# FastAI fastbook Learning for introduction chapter
> date: 2025-04-16 \
> This blog is a personal study Fastai framework tutorial fastbook focus notes, mainly for the first chapterintroduction.

Reference: [fastbook](https://github.com/fastai/fastbook/blob/master/02_production.ipynb)


## The key context for chapter 1 introduction

### 1 Introduction
This blog is an introduction to how to train deep learning classification models using Fastai's high-level APIs, and describes how to build a classification model for cats vs. dogs using Fastai.

### 2 Environment Configuration
Install the corresponding fastai toolkit
```python
# Install fastbook for notebook environment
! [ -e /content ] && pip install -Uqq fastbook
import fastbook
fastbook.setup_book()
```
### 3 Building a dataloader with image preprocessing
```python
from fastai.vision.all import *
path = untar_data(URLs.PETS)/'images'

# Define a function to label images: we assume cats have uppercase starting letters
def is_cat(x): return x[0].isupper()

# Create a data loader from the images
dls = ImageDataLoaders.from_name_func(
    path, get_image_files(path), valid_pct=0.2, seed=42,
    label_func=is_cat, item_tfms=Resize(224)
)
```

- use `untar_data` to download and extract the dataset.

- `get_image_files` fetches all image files in the dataset.

- The `label_func function` is used to label images as either cat or dog based on whether the file name starts with an uppercase letter (cats) or lowercase (dogs).

- Finally, we use Resize(224) to resize all images to 224x224 pixels for consistency.

### 4 Model Creation and Training

```python
learn = vision_learner(dls, resnet34, metrics=error_rate)
# Fine-tune the model
learn.fine_tune(1)
```
- `vision_learner(dls, resnet34, metrics=error_rate)` creates the learner with a ResNet34 backbone, which has been pre-trained on ImageNet.

- We use `fine_tune(1)` to fine-tune the model for one epoch. Fine-tuning involves adjusting the pre-trained model’s weights to better fit our specific dataset (cats and dogs).

### 5 Results and Evaluation
Once the model is trained, we can check its performance. Fastai automatically calculates the error rate on the validation set, which helps us assess how well the model is doing.

```python
# Evaluate the model's performance
learn.show_results()
```

This will display the model’s predictions alongside the true labels for a few images from the validation set. We can inspect if the model is correctly classifying cats and dogs, and observe its accuracy.

### 6. Visualization
```Python
# Display an image from the dataset
img = PILImage.create(image_cat())
img.to_thumb(192)
```

This shows a cat image resized into 192x192, allowing us to quickly see how our model is handling the input data.

### Conclusion
This blog on how to use fastai framework to build a cat and dog classifier process to record, mainly on the core of the code for the record, to facilitate the subsequent use and understanding, through the preparation of this blog, to deepen the understanding of the fastai framework and commonly used APIs.
