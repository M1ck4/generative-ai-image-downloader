# Muse

Muse is a powerful dataset creation and management tool designed to organize, label, and optimize preprocessed images for AI model training. It seamlessly integrates with the Chisel preprocessing tool and is an essential part of the image-to-AI pipeline, leading to the creation of high-quality, structured datasets ready for training on models like MichaelAngelo.

## Features

### Enhanced Image Processing & Augmentation

- **Advanced Augmentation Techniques**: Implements MixUp and CutMix to diversify training data and prevent overfitting.
- **Data Augmentation**: Supports rotations, flips, cropping, and more to enhance dataset variety.

### Quality Control Features

- **Image Quality Verification**: Ensures images meet minimum size and format requirements.
- **Metadata Integration**: Incorporates Creative Commons data to maintain licensing compliance.
- **Error Logging**: Records issues with images to prevent corrupted data from entering the dataset.

### Performance Optimization

- **Multiprocessing**: Leverages multiple CPU cores to accelerate data processing and augmentation.
- **Efficient Resource Utilization**: Optimizes processing time for large datasets.

### Dataset Management

- **Balanced Splits**: Ensures training, validation, and test sets are representative and balanced.
- **Stratified Splitting**: Maintains class distribution across dataset splits.
- **Incremental Updates**: Facilitates easy maintenance and updates to datasets.

### Analytics & Monitoring

- **Dataset Analytics**: Provides insights into dataset composition and label distribution.
- **Progress Tracking**: Monitors processing steps and augmentation progress.
- **Logging**: Detailed logs for auditing and troubleshooting.

## AI Pipeline Overview

Muse is part of a comprehensive AI pipeline for creating ethical and high-quality datasets using Creative Commons images. The pipeline includes:

#### Curator: The Image Collector

   Curator downloads Creative Commons images from trusted APIs, collecting legally usable media.
   It manages metadata from the start, ensuring proper licensing and documentation are attached to every image.

#### FilmFrame: Frame Extraction for Creative Use

   FilmFrame extracts frames from Creative Commons-licensed movies, providing a rich resource for creative projects.
   It emphasizes proper attribution with automated metadata tagging, making it perfect for educational and non-profit projects.

#### Chisel: Image Preprocessing with Precision

   Chisel refines your dataset by resizing images, removing blurriness, and ensuring all files meet quality standards.
   It standardizes images, so they’re ready for use without compromising ethical and legal standards.

#### Muse: The Dataset Creator & Manager

   Muse organizes, labels, and augments images, preparing them for AI training while preserving Creative Commons licenses.
   Every image’s metadata including attribution, author information, and license details are securely saved and traceable.
   Muse validates the dataset's legal compliance, automatically tagging images and creating structured databases for transparency.

#### MichaelAngelo: Creating with a Conscience

   Muse's dataset becomes the foundation for MichaelAngelo, our AI model that generates new images. This ensures that AI creations are built upon ethically sourced data, keeping legal and creative integrity    intact.

### Alternate Workflow
For quick dataset creation, Muse can be used directly after Curator to organize and manage images instantly. However, to ensure the highest data quality, running Chisel first is always recommended.

## Installation

### Prerequisites

- **Python 3.8 - 3.10**: TensorFlow and other dependencies require Python versions 3.8 to 3.10.
- **pip**: Ensure `pip` is up to date.

### Steps

1. **Clone the Repository**

       git clone https://github.com/M1ck4/muse.git
   
        cd muse
   
### Usage

Muse is designed to be used after Chisel has preprocessed the images. Follow these steps to create and manage your dataset:
Command-Line Arguments

    python muse.py \
    --input_folder path/to/preprocessed_images \
    --output_folder path/to/output_dataset \
    --split_ratios 0.7 0.2 0.1 \
    --augment \
    --augmentation_types rotate flip_horizontal mixup cutmix \
    --augmentation_multiplier 2 \
    --min_size 256 \
    --allowed_formats JPEG PNG \
    --stratify

### Parameters

    --input_folder: Path to the folder containing preprocessed images and their metadata from Chisel.
    --output_folder: Destination folder where the organized dataset will be saved.
    --split_ratios: Ratios for splitting the dataset into training, validation, and test sets. Must sum to 1.0. Default is 0.8 0.1 0.1.
    --augment: Enable data augmentation.
    --augmentation_types: Types of augmentations to apply. Options include rotate, flip_horizontal, flip_vertical, crop, mixup, cutmix.
    --augmentation_multiplier: Number of times to apply augmentation per image. Default is 1.
    --min_size: Minimum image size (in pixels) for quality control. Images smaller than this will be excluded. Default is 128.
    --allowed_formats: List of allowed image formats. Default is JPEG PNG.
    --stratify: Enable stratified splitting based on labels to maintain class distribution.

### Examples

    python muse.py \
    --input_folder ./preprocessed_images \
    --output_folder ./dataset \
    --split_ratios 0.7 0.2 0.1 \
    --augment \
    --augmentation_types rotate flip_horizontal mixup cutmix \
    --augmentation_multiplier 2 \
    --min_size 256 \
    --allowed_formats JPEG PNG \
    --stratify

### Steps

      Load Metadata: Muse loads metadata from JSON files generated by Curator, Chisel, and FilmFrame.
      Quality Control: Filters out images that do not meet the minimum size or are in unsupported formats.
      Apply Labels: Labels images based on metadata categories.
      Split Dataset: Divides the dataset into training, validation, and test sets according to specified ratios.
      Data Augmentation: Applies specified augmentation techniques to diversify the training data.
      Analyze Dataset: Generates analytics on dataset composition.
      Export Dataset: Saves the organized dataset into designated folders with updated metadata.

Configuration
Label Mapping

The label_mapping dictionary in the script maps category names to numerical labels. Modify this dictionary in the script to match your dataset's categories.

    label_mapping = {
    'Category1': 0,
    'Category2': 1,
    'Unknown': -1
    }

### Augmentation Types

Available augmentation types:

    rotate: Rotates images by 90, 180, and 270 degrees.
    flip_horizontal: Flips images horizontally.
    flip_vertical: Flips images vertically.
    crop: Crops the central portion of the image.
    mixup: Blends two images together.
    cutmix: Combines parts of two images.

### Quality Control

Muse ensures data quality by performing the following checks:

    Format Verification: Ensures images are in allowed formats (e.g., JPEG, PNG).
    Size Verification: Excludes images below the minimum size threshold.
    Metadata Integrity: Validates that metadata files are correctly linked and include necessary information like Creative Commons attribution.

### Performance Optimization

To handle large datasets efficiently, Muse utilizes:

    Multiprocessing: Accelerates data augmentation by processing multiple images in parallel.
    Progress Indicators: Uses tqdm to display progress bars during processing steps.
    Resource Management: Optimizes memory and CPU usage to handle extensive datasets without significant slowdowns.

### Dataset Management

Muse ensures your dataset is well-organized and balanced:

      Balanced Splits: Maintains representative distributions across training, validation, and test sets.
      Stratified Splitting: Preserves label distributions to prevent biases in model training.
      Incremental Updates: Facilitates easy updates and maintenance of the dataset as new images are added.

### Analytics & Monitoring

Muse provides valuable insights into your dataset:

      Dataset Analytics: Logs total images and label distributions for each split.
      Processing Logs: Detailed logs (muse_log.txt) record processing steps, errors, and augmentation details.
      Transparency: Records processing steps applied to each image for auditing and compliance.

<div align="center">

---

[![View MichaelAngel.io on GitHub](https://img.shields.io/badge/GitHub-View%20MichaelAngel.io-blue?logo=github)](https://github.com/M1ck4/MichaelAngel.io)

[![Ethical AI](https://img.shields.io/badge/Ethical%20AI-Priority-orange.svg)](https://github.com/M1ck4/MichaelAngel.io/blob/main/docs/the_codex/AI_Artisians_FAQ.md) 

---

![Creative Commons License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey?style=for-the-badge&logo=creative-commons&logoColor=white)
</div>
