# TensorFlow Lite Python object detection example
This example uses [TensorFlow Lite](https://tensorflow.org/lite) to perform real-time object detection using images
in a directory. It draws a bounding box around each detected
object in a the image (when the object score is above a given threshold). This image is then saved in a separate folder.
This example was modified from the [TensorFlow Lite Raspberry Pi Object Detection Example](https://github.com/tensorflow/examples/lite/examples/object_detection/raspberry_pi):


## Install the TensorFlow Lite runtime

In this project, all you need from the TensorFlow Lite API is the `Interpreter`
class. So instead of installing the large `tensorflow` package, we're using the
much smaller `tflite_runtime` package.

To install this  follow the instructions in the
[Python quickstart](https://www.tensorflow.org/lite/guide/python).
Return here after you perform the `pip install` command.


## Download the example files

First, clone this Git repo onto your Raspberry Pi like this:

```
git clone https://github.com/bkatona/detect_person --depth 1
```

Then use our script to install a couple Python packages, and
download the MobileNet model and labels file:

```
cd detect_person

# The script takes an argument specifying where you want to save the model files
bash download.sh /tmp
```
Add the location of the detect_person.py script to your python environment, for example
```
export PATH=$PATH:/path
```
where "/path" is the path to the detect_person.py. You can also add this to your .bashrc.

## Run the example
Go to the directory containing the images you wish to analyze. Then type:

```
python3 detect_person.py \
  --model /tmp/detect.tflite \
  --labels /tmp/coco_labels.txt
```

You should see a printout of the results, and a sub-directory will be created with images in which a person or people were positively identified.

For more information about executing inferences with TensorFlow Lite, read
[TensorFlow Lite inference](https://www.tensorflow.org/lite/guide/inference).

