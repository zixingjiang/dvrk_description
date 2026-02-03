![banner](images/banner.png)

# dVRK Description
This repository provides **unofficial** URDF description files and meshes for the [da Vinci Research Kit (dVRK)](https://github.com/jhu-dvrk) surgical robots.

Compared with the [official dVRK description](https://github.com/jhu-dvrk/dvrk_model) package:

- It contains **URDF files only**, without ROS launch files or RViz configurations.
- It offers **more realistic visuals** (especially for the Classic generation, thanks to the high‑poly meshes from the [dvrk_env](https://github.com/WPI-AIM/dvrk_env) repository), including improved colors and simulated parallel linkages via mimic joints.
- It is **[REP‑103 compliant](#coordinate-frames)**.
- It **fixes several issues** present in the official description, including misalgned meshes and incorrect tool names.

Note that kinematics and dynamics parameters in this package are guesstimated and may not be accurate (especially inertials). Use at your own discretion.

## Contents

### Arms
This package includes different arms of the dVRK system, both Classic and Si generations:
- **ECM**: Endoscopic Camera Manipulator
- **PSM**: Patient Side Manipulator
- **SUJ**: Setup Joints
- **MTM**: Master Tele Manipulator (Classic only; Si uses the same as Classic)

Note that for the Si generation, only low-poly meshes are available for the time being.

| | ECM | PSM | SUJ | MTM |
|-|-|-|-|-|
| Classic | ![ecm_classic](images/ecm_classic.png)| ![psm_classic](images/psm_classic.png)| ![suj_classic](images/suj_classic.png)| ![mtm_classic](images/mtm_classic.png)|
| Si | ![ecm_si](images/ecm_si.png) | ![psm_si](images/psm_si.png) | ![suj_si](images/suj_si.png) |  |

### Tools

This package includes several surgical tools for mounting on the PSM. 

For the Classic generation, available tools include:
- 8mm Small Clip Applier
- 8mm Cadiere Forceps
- 5mm Round Tip Scissors

For the Si generation, only one tool is available so far:
- 8mm Large Needle Driver

| 8mm Small Clip Applier - Classic | 8mm Cadiere Forceps - Classic | 5mm Round Tip Scissors - Classic | 8mm Large Needle Driver - Si |
|------------------------|---------------------|------------------------|------------------------|
|![sca](images/tool_sca_classic.png)|![cadiere](images/tool_cadiere_classic.png)|![rts](images/tool_rts_classic.png)|![lnd](images/tool_lnd_si.png)|

## Coordinate Frames
This package follows the [REP-103](http://www.ros.org/reps/rep-0103.html)  convention. Coordinate frames are right‑handed, with the following orientations:
- Base frame: X forward, Y left, Z up
- End‑effector frame: Z forward, X right, Y down

For RCM frame, its orientation matches that of the base frame. See the reference image below:

<div align="center"><img src="images/frames.png" width="70%"></div>

All joint axes—revolute and prismatic—are aligned with the Z‑axis. The positive direction corresponds to positive rotation following the right‑hand rule or positive translation along the Z‑axis.

## File Structure
The core of this package consists of [xacro](https://wiki.ros.org/xacro) macros located in the `urdf/include` directory. These macros can be composed to generate complete robot description files.

- For the Classic generation, the macros are defined in `classic/{ecm,mtm,psm,suj,tool}.macro.xacro`.
- For the Si generation, the macros are defined in `si/{ecm,psm,suj,tool}.macro.xacro`.

The `urdf/examples` directory contains example xacro files demonstrating how to assemble the macros into full robot descriptions.

## Usage
It is recommended to browse the [examples](urdf/examples) first to understand how the macros are used. To create your custom robot description file, follow these steps: 

1. Compose your robot description xacro file using the macros provided in this package. 
2. "Compile" your xacro file into a plain URDF. This can be done using the xacro CLI from ROS:
   ```bash
   xacro your_robot.urdf.xacro > your_robot.urdf
   ```
   or with any other xacro processor, such as [xacrodoc](https://github.com/adamheins/xacrodoc):
   ```bash
   xacrodoc your_robot.urdf.xacro -o your_robot.urdf
   ```

You can then use the generated URDF file in your applications.

## Acknowledgements
This package incorporates resources from the following repositories: 
- [dvrk_model](https://github.com/jhu-dvrk/dvrk_model) by the Johns Hopkins University dVRK team.
- [dvrk_env](https://github.com/WPI-AIM/dvrk_env) by the WPI-AIM lab.

In this README, the URDF is visualized using [Viser](https://github.com/nerfstudio-project/viser).

## License
This package is released under the [MIT License](LICENSE).