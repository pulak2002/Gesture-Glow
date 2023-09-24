# Gesture Glow: Gesture Based Face Feature Selection
Face (facial) landmarks are fundamental features of the human face that help us recognise various faces. The nose, brow, lips, and corners of the eyes are only a few examples of prominent human facial landmarks. The landmarks in a facial image are typically their 2D positions in the image plane.In our project we are using mediapipe as a face dectection model after construction of the model Now to perform the detection on the sample image, we will have to pass the image (in RGB format) into the loaded model and we will get an object that will have an attribute detection that contains a list of a bounding box and six key points for each face in the image. The six key points are on the:

Right Eye
Left Eye
Nose Tip
Mouth Center
Right Ear Tragion
Left Ear Tragion

The library uses the BlazeFace model for detecting face landmarks. BlazeFace is a deep learning model that is already 5optimized for low spec devices like smartphones. Therefore, we can use the model in real-time.BlazeFace contains two main steps. First, the model detects one or 
more faces on an image. Second, the image detects around 468 face keypoints by using regression

## Design
Python 3.8.0's built-in modules have been used to implement the gesture-controlled face filter. We made use of well-known modules like Hand-Tracking-Module,openCV, and Mediapipe. The media pipe offers more than 400 feature coordinates, many of which are in three dimensions, making it more sophisticated than Dilip library. As previously mentioned, a face detector is used internally by Mediapipe's face landmarks detection solution to extract the necessary Regions of Interest (faces) from the image. The RGB input image that was converted using the openCV function is required by the Mediapipe. We can identify the right and left ear tragion, mouth centre, and right and left eyes using Mediapipe. Using the input frame as a starting point, the detectFacialLandmarks() function detects 
facial landmarks. It needs the face mesh function and an image.The output image in BGR format and the outcomes of the facial landmark’s detection are returned. Using a face part's landmarks, the getsize() function determines the height and width of the component. It returns the face part's calculated width, height, and an array of landmarks. To determine whether a specific face part is open or closed, use the functions isOpen() and isOpenMouth(). Its mouth and eyes will be examined. The overlay function uses the cv2 module to create a filter image mask for the face filter image. In order to create a new annotated image, this mask is added 10 to the image's region of interest. The mask function uses built-in Mediapipe library features to identify all facial landmarks and 
annotate them with a 3D mask mesh grid. The mesh grid adjusts to the movement of the facial components. We used two images for the eyes and an animation for the fire piece on the smoke filter. The animation is designed to operate in an infinite loop so that it can resume after the animation's frames are finished. The mouth 
filter makes use of an image that is placed in the mouth's centre. The user's mouth size determines how big the mouth is. All 
hand landmarks are located and detected by the Hand Tracking module. Additionally, it keeps the fingers' indexes, which are up 
and down in the provided frame. All these details are stored in the one-dimensional array for further pre-processing.

## Algorithm:

1. The webcam is initialised using the Cv2 function to record the frames and provide them for additional pre-processing.
2. The hand tracking module determines which fingers are all extended. It calls the appropriate face filter function based on the desired finger inputs.
3. The frames of the video are flipped in order to provide selfie-view.
4. To identify every face landmark, the detectFacialLandmarks() function is used. 
5. In order to provide face mask face filters, these face landmarks are built on a three-dimensional mesh grid that is annotated with the current frame.
6. If not (for the remaining filters), we call the isOpen() isOpenMouth() function to find all the face's open areas. If the distance exceeds the predetermined threshold, they are marked as open.
7. The size of the face part is also calculated if it is marked as open in order to annotate the entire face part with the filter image.
8. Next, the correct face filter image is entered into the overlay function in order to create its mask and annotate it on the currently displayed frame.
9. As the filters are applied to each frame of the video, the entire process begins in an infinite loop.
10. If the "Escape" key on the standard input output keyboard is pressed, the loop is ended or the webcam is released.The face mask is placed on the face if the thumb is raised. A scary face mask is added over the user's face if the Index and fourth fingers are raised. The smoke filters are applied using the thumb and the fourth finger. Zero indexing is used in the array.
    
## Annotations: -
Index 0 - Thumb
Index 1 – Index finger
Index 2- Middle finger
Index 3 – Ring finger

## Results

![image](https://github.com/pulak2002/Gesture-Based-Face-Feature-Selection/assets/110912267/438fbfb1-e0dd-4400-85e0-a50faed734e7)

![image](https://github.com/pulak2002/Gesture-Based-Face-Feature-Selection/assets/110912267/9afd6879-6381-4f7c-aafe-7587db683e3e)
