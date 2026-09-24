
# 14/10/2025 - Redesign

The entire arm has been redesigned for a simpler layout and to allow easy mounting of ArUco markers. 

<img width="774" height="439" alt="image" src="./media/cad1.png" />

<img width="846" height="572" alt="image" src="./media/cad2.png" />

<img width="3000" height="4000" alt="1" src="./media/cad3.jpg" />

<img width="4000" height="3000" alt="2" src="./media/cad4.jpg" />

<img width="4000" height="3000" alt="3" src="./media/cad5.jpg" />

<img width="4000" height="3000" alt="4" src="./media/cad6.jpg" />

# 20/09/2025 - YOLO card detection

The card detection is complete. 

- The dataset contains 828 images of the four cards, with differing orientation, position, lighting and card count. There are also negative images to prevent false positives during deployment of the model. 
- The images were labelled using [Label Studio](https://labelstud.io/), shown below:
<img width="1262" height="709" alt="image" src="./media/cards1.png" />

- The images were randomly split into 80% training and 20% validation. 
- I chose to use YOLO11n to optimise frame rate for use on a raspberry pi; a comparison of the different YOLO11 sub-models is shown below:
<img width="950" height="490" alt="yolo11 performance" src="./media/performance-table.png" />

- I trained the model locally on an Nvidia RTX 3060Ti GPU, with 40 epochs, which is shown below:
<img width="2400" height="1200" alt="results" src="./media/results.png" />

- I wrote a python program to detect the cards in real time, and also combined the Aruco marker detection; a demo is shown below:

https://github.com/user-attachments/assets/7dcee5a4-68bd-4ffd-b935-b0bce6134944

# 19/09/2025 - Suction pipeline

The suction pipeline contains:
- Arduino uno with a sensor shield
- Solenoid valve
- DC vacuum pump
- Suction cup
- Silicone tubing

The pump and valve are controlled using the Servo arduino library. The suction cup will be used as the end effector for the robotic arm, to pick up the playing cards.

![suction pipeline](./media/suction-pipeline.jpg)

# 26/08/2025 - Raspberry Pi & Arduino Communication

I set up communication between the raspberry pi & arduino, using a serial connection.
I also incorporated the inverse kinematics script, so that the joint angles are calculated on the pi, then sent to the arduino.

<img width="1026" height="416" alt="image" src="./media/comms.png" />

# 03/08/2025 - Image dataset

In order to train a YOLO model to detect playing cards (and which suit it is), I must gather many example images:
- The arm will sort playing cards by suit, so use the 10s because they have the most identifiable objects (e.g. hearts).
- Must be in the same conditions as the task will be carried out in to maximise performance, same lighting, same background, etc
- I aim to gather around 400 images, since the arm will be working in a controlled environment - the background will not change during detection
  
Then the next steps are:
- The images must be labelled, I'm using [Label Studio](https://labelstud.io/)
 to achieve this
- Images must be split into training and validation sets
- Then I will train the model using an anaconda virtual environment, using a local GPU

<img width="769" height="1025" alt="image" src="./media/cards2.png" />

# 02/08/2025 - Base completion

The base has been completed apart from the lid. The motors are mounted outside the turret, as an improvement on the previous version of the arm. It allows any NEMA 17 motor to be mounted without changing the design, and also allows easier access to the cables.

It features:
- Rotating turret to accommodate a counterweight
- Centering mechanism
- Timing belt driven rotation
- Belt tensioner
- NEMA 17 motors
- Limit switch for motor homing

<img width="1063" height="530" alt="image" src="./media/cad7.png" />

<img width="565" height="577" alt="image" src="./media/cad8.png" />

<img width="781" height="649" alt="image" src="./media/cad9.png" />
