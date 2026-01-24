# dVRK Description
![banner](images/banner.png)

This repository contains **unofficial** URDF description files and meshes for the [da Vinci Research Kit (dVRK)](https://github.com/jhu-dvrk) surgical robots. 

**Gallery**
| | Endoscopic Camera Manipulator (ECM) | Patient Side Manipulator (PSM) | Setup Joints (SUJ) | Master Tele Manipulator (MTM) |
|-|-|-|-|-|
| Classic | ![ecm_classic](images/ecm_classic.png)| ![psm_classic](images/psm_classic.png)| ![suj_classic](images/suj_classic.png)| ![mtm_classic](images/mtm_classic.png)|
| Si | ![ecm_si](images/ecm_si.png) | ![psm_si](images/psm_si.png) | ![suj_si](images/suj_si.png) |  |

| 8mm Small Clip Applier - Classic | 8mm Cadiere Forceps - Classic | 5mm Round Tip Scissors - Classic | 8mm Large Needle Driver - Si |
|------------------------|---------------------|------------------------|------------------------|
|![sca](images/tool_sca_classic.png)|![cadiere](images/tool_cadiere_classic.png)|![rts](images/tool_rts_classic.png)|![lnd](images/tool_lnd_si.png)|

<img src="images/REP-103.png" width=60%>


## Getting Started

1. Compose your dVRK robot description [xacro](https://wiki.ros.org/xacro) file using the provided macros defined in the `urdf/include` directory. Examples can be found in the `urdf/examples` directory.
2. Compile your xacro file to plain URDF using the `xacro` command-line tool (if using ROS) or any other xacro processor, such as [xacrodoc](https://github.com/adamheins/xacrodoc):
   ```bash
   xacrodoc your_robot_description.xacro -o your_robot_description.urdf
   ```
3. Use the generated URDF file for your applications.