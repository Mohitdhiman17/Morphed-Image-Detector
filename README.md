# Image Tampering Detection Using ELA and Metadata Analysis

Image forensics has witnessed significant growth in recent years, driven by advancements in computer vision and the surge of digital data. Ensuring the authenticity of images has become a top priority, as sophisticated manipulation techniques continue to emerge. We propose a multi-modal approach to gain insight into the image's authenticity.

#### Step 1
Choose the image
#### Step 2
Select if weather metadata is available
#### Step 3
Analyze the results


### Running Locally
Clone the repo


to install all dependencies, create a new virtualenv, and install all required packages as:<br>
```bash
pip install -r requirements
```

Usage:<br>
Keep the model in <i>ELA_Training</i> Folder<br>
run <code>streamlit run app.py</code> for local inference<br>

### A Short Summary
We are using ELA and Metadata Analysis to achieve insight into the authenticity of an image<br>
#### 1. ELA
when a lossy algorithm like JPEG compresses an image, the compression process introduces artifacts or discrepancies in it. these can appear as blocks or regions within an image, exhibiting pixel values that differ from those of the surrounding areas. when an image goes under manipulation, compression artifacts are disrupted for the tampered region.<br>

#### 2. Weather Validation using Metadata Analysis
image contains a lot of metadata with it, say, camera model, date, time, location, etc. By 'weather validation' to gain insight into the authenticity of an image, we mean precisely validating the depicted weather. A trained Weather CNN detects weather depicted in an image(preferably outdoor), and this result of Weather CNN is validated using Historical weather data. for fetching weather data all you need is a good open-source weather database, place, date, and time. Using metadata analysis, we could extract longitude and latitude, as well as the date and time. then parsing this metadata, we can send a request to weather-API to get the original weather on that place on a given date and time and validate our weather-CNN's result.
<br>The dataset for training weather-CNN was collected from various sources. We have collected a total of 1,804 training images and 451 validation images, and the categories we narrowed down for the classification are the following:
<ul>
<li> Lighting
<li> rainy
<li> cloudy
<li> sunny
</ul>

### Training
In case you want to retrain the ELA models, download the CASIA2.0 Dataset and put it inside ELA_Training and run <code>main.ipynb</code>. If you want to access the weather dataset, you can contact me.

### Results
For ELA with DenseNet, using standard practices for training and optimizing the model, the accuracies model achieved were:
| Metric                | Accuracy  |
|-----------------------|----------:|
| Train Accuracy        |   98.34%  |
| Validation Accuracy   |   93.78%  |
| Test Accuracy         |   87.24%  |

For Weather CNN:<br>
| Metric                | Accuracy  |
|-----------------------|----------:|
| Train Accuracy        |   91.2%   |
| Validation Accuracy   |   81.6%   |
| Test Accuracy         |   73.4%   |

### To-Dos
- [ ] Use scene classification model to remove user dependency for checking whether the image is outdoor or not. (In progress)
- [ ] Integration of Web-Traces and more modalities to Improve upon the Results.

## Cite
If you use our study in your research, please consider citing us, Thanks:
author={Mohit , Shobhit},

