# 2017-MRI 
#usr/bin/env python3

import wpilib
import wpilib.buttons

class MyRobot(wpilib.IterativeRobot):

    def robotInit(self):

        self.drive_motor1 = wpilib.Talon(0)
        self.drive_motor2 = wpilib.Talon(1)

        self.robot_drive = wpilib.RobotDrive(self.drive_motor1, self.drive_motor2)

        self.xboxController = wpilib.Joystick(0)


        self.fire_single_piston = wpilib.buttons.JoystickButton(self.xboxController, 1) #A
        self.fire_double_piston_forward = wpilib.buttons.JoystickButton(self.xboxController, 2) #B
        self.fire_double_piston_backward = wpilib.buttons.JoystickButton(self.xboxController, 3) #X
        self.winch_forward = wpilib.buttons.JoystickButton(self.xboxController, 

    def teleopInit(self):


        pass

    def teleopPeriodic(self):

        self.robot_drive.arcadeDrive(self.xboxController.getY(), self.xboxController.getX(), True)

if __name__ == "__main__":
    wpilib.run(MyRobot)
