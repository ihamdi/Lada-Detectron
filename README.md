# Lada Detectron
### Using MaskRCNN on Custom Dataset with Detectron2 on a Jupyter Notebook

<a href="https://www.python.org/"><img src="https://img.shields.io/badge/python-v3.9.7-blue.svg?logo=python&style=for-the-badge" /></a>
<a href="https://www.anaconda.org/"><img src="https://img.shields.io/badge/conda-v4.10.3-blue.svg?logo=conda&style=for-the-badge" /></a>
<a href="https://pytorch.org/"><img src="https://img.shields.io/badge/PyTorch-v1.10.0-red.svg?logo=PyTorch&style=for-the-badge" /></a>
<a href="https://jupyter.org/try"><img src="https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter" /><a>


<p align="center">
  <img width="1000" src="https://user-images.githubusercontent.com/93069949/144974647-89acc184-a541-499b-a5eb-3370533639c1.png">
</p>

1. Create conda environment
```
conda create --name env-name ipykernel gitpython
```

2. Clone Github
```
from git import Repo
Repo.clone_from("https://github.com/ihamdi/Lada-Detectron.git","/your/directory/")
```
or [download](https://github.com/ihamdi/Lada-Detection/archive/refs/heads/main.zip) and extract a copy of the files.
  

3. Install [PyTorch](https://pytorch.org/get-started/locally/) according to your machine. For example:
```
conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
```

4. Install Detectron2:
Visit the [official website](https://detectron2.readthedocs.io/en/latest/tutorials/install.html) to install Detectron2 according to your operating system and Pytorch/Cudatoolkit version.

For example, I had to run the following line on my Linux machine with Pytorch 1.10.0 and Cudatoolkit 10.2:
```
python -m pip install detectron2 -f   https://dl.fbaipublicfiles.com/detectron2/wheels/cu102/torch1.10/index.html
```

5. Install dependencies from [`requirements.txt`](https://github.com/ihamdi/Detectron2/blob/main/requirements.txt) file:
```
pip install -r requirements.txt
```

## Dataset:
[Custom dataset](https://github.com/ihamdi/Detectron2/tree/main/lada_dataset/lada) is included on the [Github page](https://github.com/ihamdi/Detectron2) with the code. Images for the custom dataset were obtained from Google Images, and the annotations were created and exported to json using [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/via.html). The dataset has a total of 41 images: 29 for training and 12 for validation.

## How to Use:
Press Run All on the Jupyter Notebook to load the data and then train and validate a model on the dataset.

If you'd like to create and use your own custom dataset, all you have to do is follow the same directory structure and place the json files produced by [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/via.html) in the corresponding folder. The Notebook is specifically designed to handle the json files produced by that program.

## Results:
As seen in the validation section of the Notebook, the model generally does very well at segmenting Ladas even when the it is partly covered by an object. However, it seems to get a little confused when there are more than one in the image.  
![2](https://user-images.githubusercontent.com/93069949/144981337-5f62f469-2369-41d8-a5a9-6da51c6b3f7f.png)
![3](https://user-images.githubusercontent.com/93069949/144981325-245e279b-9499-4099-b159-ff19226606a8.png)
![4](https://user-images.githubusercontent.com/93069949/144981734-98a12164-7633-4ff6-8647-635047e63c67.png)
![6](https://user-images.githubusercontent.com/93069949/144981835-8c6cc22c-3e6e-4b68-a112-e9d962f6fa64.png)

Ideally, the training data would contain images where there are more than one car in them. 

---
  
## Changes made to [Installation Tutorial](https://colab.research.google.com/drive/16jcaJoc6bCFAQ96jDe2HwtXj7BMD_-m5#scrollTo=PIbAM2pv-urF)
1. Inside the get_xxxx_dicts function, 
  ```
  for _, anno in annos.items():
            assert not anno["region_attributes"]
            anno = anno["shape_attributes"]
  ```
  was replaced with 
  ```
  annos = annos[0]["shape_attributes"]
  ```
  since the json file obtained from [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/) returns a list instead of a dictionary.

---
  
### Background:
This was done purely for learning purposes (and fun) and to get more familiar with Detectron2. Detectron2 is already quite powerful in detecting people, cars, umbrellas, ... etc, but I was curious to see how to train it on a new object. The car model Lada was used simply because it was the easiest to annotate due to its straight-line shape.

For future work, I would like to see how good it can be at differentiating car models. Another thing I would like to try is detecting and reading number plates as some sort of rudimentary algorithm for photo-radar.

---

### Contact:
For any questions or feedback, please feel free to post comments or contact me at ibraheem.hamdi@mbzuai.ac.ae

---

### References:

[Getting Started as Detectron2](https://detectron2.readthedocs.io/en/latest/tutorials/getting_started.html) was used as base for this code.
  
[VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/) by Visual Geometry Group at University of Oxford.

[Detectron2](https://github.com/facebookresearch/detectron2)'s Github page by Facebook Research.
