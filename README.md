# Free Adversarial Training 
This is a PyTorch implementation of the [Adversarial Training for Free!](https://arxiv.org/abs/1904.12843 "Free Adversarial Training") paper.
The official TensorFlow implementation can be found [here](https://github.com/ashafahi/free_adv_train).

Using the Free Adversarial Training (Free-m) algorithm, we can train robust models at no additional cost compared to natural training. This allows us to train robust ImageNet models using only a few GPUs in a couple of days! Below is the performance of various Free-trained ImageNet models where we vary the replay parameter (m).
<p align="center">
<img src="https://mahyarnajibi.github.io/github_readme_data/free_adv.png"/>
</p>

This repository provides codes for training and evaluating the models on the ImageNet dataset.
The implementation is adapted from the [official PyTorch repository](https://github.com/pytorch/examples/blob/master/imagenet).

## Installation
1. Install [PyTorch](https://github.com/pytorch/examples/blob/master/imagenet).
2. Install the required python packages. All packages can be installed by running the following command:
```bash
pip install -r requirements.txt
```
3. Download and prepare the ImageNet dataset. You can use [this script](https://raw.githubusercontent.com/soumith/imagenetloader.torch/master/valprep.sh), 
provided by the PyTorch repository, to move the validation subset to the labeled subfolders.

## Training a model
To train a robust model run the following command:

```bash
python main_free.py [PATH_TO_IMAGENET_ROOT]
```
This trains a robust model with the default parameters. The training parameters can be set by changing the ```configs.yml``` config file.
Please run ```python main_free.py --help``` to see the list of possible arguments. 
The script saves the trained models into the ```trained_models``` folder and the logs into the ```output``` folder.


## Evaluating a trained model
You can evaluate a trained model by running the following command:
```bash
python main_free.py [PATH_TO_IMAGENET_ROOT] -e --resume [PATH_TO_THE_MODEL_CHECKPOINT]
```
The script evaluates the model on clean examples as well as examples generated by PGD attacks with different parameters.
The attack parameters can be set by changing the ```configs.yml``` file.

## Citing
If you find the paper or the code useful for your study, please consider citing the free training paper:
```bash
@article{2019arXiv190412843S,
   author = {{Shafahi}, A. and {Najibi}, M. and {Ghiasi}, A. and {Xu}, Z. and 
	{Dickerson}, J. and {Studer}, C. and {Davis}, L. and {Taylor}, G. and {Goldstein}, T.},
    title = "{Adversarial Training for Free!}",
    journal = {ArXiv e-prints},
    year = 2019
}
```
