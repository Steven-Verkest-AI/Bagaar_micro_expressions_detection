## Emotion Detection: a use case ..about detecting microexpressions


### Goal
Trying to detect emotions in images & videos.

### Table of contents

* [Microexpressions](#microexpressions)
* [Technologies used](#technologies-used)
* [Approaches](#approaches)
* [Data: FER+](#data-fer)
* [MobileNetV2 CNN](#mobilenetv2-cnn])
* [To use](#to-use)

### Microexpressions

A microexpression is a very brief, involuntary facial expression humans make when experiencing
an emotion. They usually last 0.5–4.0 seconds and cannot be faked.
Dr. Paul Ekman popularized the term “microexpression” and greatly expanded the research.

A few examples:

| Happy | Fear |
|-------|------|
|Corners of the lips are drawn back and up | Eyebrows are raised and drawn together, usually in a flat line |
|Mouth may or may not be parted, teeth exposed |Wrinkles in the forehead are in the center between the eyebrows, not across |
|A wrinkle runs from outer nose to outer lip |Upper eyelid is raised, but the lower lid is tense and drawn up |
|Cheeks are raised |Eyes have the upper white showing, but not the lower white  |
|Lower eyelid may show wrinkles or be tense |Mouth is open and lips are slightly tensed or stretched and drawn back |

### Technologies used
- OpenCV for image and video handling and Haarcascades to detect faces
- DeepFace
- Tensorflow Keras
- MobileNetV2
- ...

### Approaches
- Build Keras CNN for emotion recognition with transfer learning using pretrained MobileNetV2
- Trying to detect faces and emotions with deepFace

### Data: FER+

The FER+ annotations provide a set of new labels for the standard Emotion FER dataset. In FER+, each image has been labeled by 10 crowd-sourced taggers, which provide better quality ground truth for still image emotion than the original FER labels. The image emotion labels are: hapiness, anger, fear, disgust, contempt, surprise, sadness and neutral.

Here are some examples of the FER vs FER+ labels extracted from the abovementioned paper (FER top, FER+ bottom):
<p align="center">
  <img src="https://github.com/kristof-becode/Emotion-Detection-use-case/blob/master/img/FER%2BvsFER.png" width=50% >
</p>

You can find all necessary information on FER+ and how to generate it in this repo: https://github.com/microsoft/FERPlus

The original FER data set can be found here: https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data


### MobileNetV2 CNN

A Keras model was created using the pretrained MobileNetV2 with transfer learning. The upper layers of this model were trained on FER+ with 7 emotions.

The accuracy:

<p align="center">
  <img src="https://github.com/kristof-becode/Emotion-Detection-use-case/blob/master/img/StevensAcc.png" width=45% >
</p>





### To use

```

To build a Keras CNN FER model for real-time detection use `detect_emotion_video.py`  This will open a webcam and give FER overlaid on the webcam stream.
```
python detect_emotion_video.py
```

To detect emotions from what is verbally said in a video using IBM Watson and NRCLex
```
mp4_to_emotion.py
```

To generate adversarial FER images, try the jupyter notebook `Adversarial_FER.ipynb` in the `Adversarial_FER` folder

To detect emotions in realtime
```
all the file-names that start with: realtime_emotion_recognition....

(the end of the file-name describes which dataset was used to train the model)
```


