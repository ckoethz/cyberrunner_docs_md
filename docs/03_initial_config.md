Initial Configuration
=====

Before we can start using CyberRunner, we need to first **calibrate the camera** and **configure the motors**. These steps have to be taken only once. 

## Camera Calibration

In order for the position of the ball within the labyrinth to be tracked, we need to first calibrate the camera. For this purpose, we use the <a href="https://sites.google.com/site/scarabotix/ocamcalib-omnidirectional-camera-calibration-toolbox-for-matlab" target="_blank">COCamCalib MATLAB toolbox</a>.

1. Follow the steps <a href="https://sites.google.com/site/scarabotix/ocamcalib-omnidirectional-camera-calibration-toolbox-for-matlab" target="_blank">here</a> to obtain the calibration results for your camera. 

    !!! warning "Disclaimer"

        The **Find Center** step is computationally intensive and may get stuck. In this case, update `PP` in both instances of the function `lsqlin()` to `sparse(PP)`. This should speed up the process. For more details, the bug fix is idenitified in <a href="https://groups.google.com/g/ocamcalib-toolbox/c/ZgVP4LHd-6w?pli=1" target="_blank">this thread</a>.

    To take the calibration pictures, you may use the script provided by the `cyberrunner_camera` package. This ensures that the calibration pictures are taken using the correct resolution and field of view.

            ros2 run cyberrunner_camera take_pictures.py
        Example calibration pictures are shown below. TODO

3. Save the calibration results by clicking on **Export Data** in the OCamCalib GUI. This will create the file `calib_results.txt` in your MATLAB workspace.

4. Copy the `calib_results.txt` file to your ROS workspace with

        cp <path_to_matlab_workspace>/calib_results.txt <path_to_cyberrunner_ws>/src/cyberrunner/cyberrunner_state_estimation/cyberrunner_state_estimation/data
    Replace `<path_to_matlab_workspace>` and `<path_to_cyberrunner_ws>` with the path to your MATLAB workspace and your CyberRunner ROS workspace, respectively.

5. Select corners. TODO add image, and update instruction

        ros2 run cyberrunner_camera select_corners.py
        
6. (Optional) Create mask. TODO

## Motor Configuration

1. Install [Dynamixel Wizard 2.0](https://emanual.robotis.com/docs/en/software/dynamixel/dynamixel_wizard2/).
2. Temporarily disconnect the front motor. Connect the U2D2 to your host PC and ensure that the motors are turned on by pressing the power switch on the U2D2 Power Hub Board. TODO PICTURE
3. In the Dynamixel Wizard, press **Scan** until the motor is found.
4. Assign **ID 2** to the connected motor, set the baud rate to ..., and set the **temperature limit** to 100. Make sure to click **Save** after each change. TODO Picture
5. Reconnect the front motor.
6. Press **Scan** again.
7. For the motor with **ID 1**, apply the same changes, i.e., set the baud rate to ..., and set the **temperature limit** to 100.


