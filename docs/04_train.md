Train
=====

!!! warning "Disclaimer"
    This page is not up-to-date. It will be updated soon with the latest procedure. Stay tuned!

1. Open four terminal windows. For each, navigate to the CyberRunner workspace and source the workspace.

        cd cyberrunner_ws
        source install/setup.bash

2. In terminal 1 run

        ros2 run cyberrunner_camera cam_publisher.py

3. In terminal 2 run

        ros2 run cyberrunner_state_estimation estimator_sub

4. In terminal 3 run 

        ros2 run cyberrunner_dynamixel cyberrunner_dynamixel

5. In terminal 4 run

        ros2 run cyberrunner_dreamer train
        
   and wait until you see the first logs for step 0.

6. Place the ball at the starting location on the labyrinth, and press `ENTER` in terminal 4. CyberRunner will start playing the game.

7. Once the ball falls down a hole or the pre-defined time limit of 1 minute per episode has passed, CyberRunner will automatically stop playing. Go back to step 6 to start the next episode.