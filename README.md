# Detectron2
### Using Facebook's Detectron2 with a custom dataset

<a href="https://www.anaconda.org/"><img src="https://img.shields.io/badge/conda-v4.10.3-blue.svg?logo=conda&style=for-the-badge" /></a>
<a href="https://pytorch.org/"><img src="https://img.shields.io/badge/PyTorch-v1.10.0-red.svg?logo=PyTorch&style=for-the-badge" /></a>
<a href="https://www.python.org/"><img src="https://img.shields.io/badge/python-v3.9.7-blue.svg?logo=python&style=for-the-badge" /></a>

<p align="center">
  <img width="1000" src="https://user-images.githubusercontent.com/93069949/144974647-89acc184-a541-499b-a5eb-3370533639c1.png">
</p>

1. Clone Github
```
import git
git.Git("/your/directory/to/clone").clone("git:https://github.com/ihamdi/Detectron2.git)
```
or [download](https://github.com/ihamdi/Detectron2/archive/refs/heads/main.zip) and extract a copy of the files.

2. Create conda environment
```
conda create --name env-name ipykernel
```

3. Install [PyTorch](https://pytorch.org/get-started/locally/)

4. Install Detectron2:
Visit the [Installation](https://detectron2.readthedocs.io/en/latest/tutorials/install.html) to install Detectron2 according to your operating system and Pytorch/Cudatoolkit version.

For example, I had to run the following line on my Linux machine with Pytorch 1.10.0 and Cudatoolkit 10.2:
```
python -m pip install detectron2 -f   https://dl.fbaipublicfiles.com/detectron2/wheels/cu102/torch1.10/index.html
```

5. Install dependencies:
```
pip install -r requirements.txt
```

## Dataset:
Images for custom dataset were obtained from Google, and the masks were created and exported to json using [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/via.html). The dataset has a total of 41 images: 29 for training and 12 for validation.

## How to Use:
Press Run All on the Jupyter Notebook to load the data and then train and validate a model on the dataset.

If you'd like to create and use your own custom dataset, all you have to do is follow the same directory structure and place the json files produced by [VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/via.html) in the corresponding folder. The Notebook is specifically designed to handle the json files produced by that program.

## Results:



### Background:
This was done purely for learning purposes (and fun) and to get more familiar with Detectron2. The car model Lada was used simply because it was the easiest to annotate due to its flat surfaces.

---

### Contact:
For any questions or feedback, please feel free to post comments or contact me at ibraheem.hamdi@mbzuai.ac.ae

---

### References:

[Detectron2](https://github.com/facebookresearch/detectron2)'s Github page by Facebook Research.

[VGG Image Annotator](https://www.robots.ox.ac.uk/~vgg/software/via/) by Visual Geometry Group at University of Oxford.

[AarohiSingla](https://github.com/AarohiSingla/Detectron2-Tutorial)'s code was used as base.
