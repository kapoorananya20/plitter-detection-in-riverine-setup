# plitter-detection-in-riverine-setup
The primary goal of pLitter detection in rivers is to automatically identify and classify plastic litter within riverine environments through the use of deep learning and computer vision technologies. With an alarming **11 million metric tons** of plastic entering our oceans each year, and rivers accounting for up to 80% of this pollution, it is imperative that we implement efficient monitoring and cleanup strategies.

By delivering real-time data on pollution levels, pinpointing high-risk areas, and bolstering cleanup initiatives, pLitter seeks to significantly reduce plastic waste in rivers and safeguard aquatic ecosystems. This innovative system serves as a valuable resource for governments, non-governmental organizations (NGOs), and researchers, enabling them to devise targeted solutions to address the escalating plastic crisis. Through collaboration and informed action, we can work towards a cleaner, healthier environment for both our rivers and the diverse life they support.

# Dataset Creation 
The dataset for pLitter detection was created by collecting images from two primary sources:  
1. YouTube Playlist 
Images and video frames were extracted from a curated YouTube playlist containing riverine environments with visible plastic litter. The playlist can be accessed here: [YouTube Link](https://youtube.com/playlist?list=PLKdGIbtBVuW2Wao2kko7wqdhbGdN7mzEK&feature=shared). Frames were extracted from videos at different time intervals to ensure diversity.  
2. Web Scraping Tools
Additional images were gathered from various online sources using **automated web scraping tools** to enhance dataset diversity and model robustness.  

# Data Annotation  
The extracted frames were manually labeled into **4 classes** using the **Makesense.ai annotation tool**. The annotated data was then converted into the **YOLOv5 annotation format** for model training.  
Dataset Statistics 
Total Dataset Size: 989 MB
Train Split Size: 2,890 images  
Validation Split Size: 250 images  
Number of Classes: 4 
Class Names: Plastic Bag , Plastic Bottle, Plastic Waste, Not Plastic Waste**  

# Dataset Directory Structure 
The dataset follows the standard **YOLOv5 directory structure** for easy integration with object detection models.  

```
pLitter_Dataset/
│── train/
│   ├── images/            
│   ├── labels/              
│── val/
│   ├── images/            
│   ├── labels/              
│── data.yaml             
```

# Annotation Format (YOLOv5)
Each image has a corresponding `.txt` file in the `labels/` directory, following the YOLOv5 annotation format:  
```
<class_id> <x_center> <y_center> <width> <height>
```
- `class_id`: Index of the class (0 for Plastic Bag, 1 for Plastic Bottle, etc.).  
- `x_center, y_center`: Center coordinates of the bounding box (normalized between 0 and 1).  
- `width, height`: Width and height of the bounding box (normalized between 0 and 1).  

Example Annotation for an Image (`image1.txt`)  
```
0 0.45 0.55 0.30 0.40  # Plastic Bag
2 0.60 0.70 0.20 0.30  # Plastic Waste
```
This means:  
A Plastic Bag (class 0) is located at `(0.45, 0.55)`, with a width of `0.30` and height of `0.40`.  
A Plastic Waste (class 2) is located at `(0.60, 0.70)`, with a width of `0.20` and height of `0.30`.  

