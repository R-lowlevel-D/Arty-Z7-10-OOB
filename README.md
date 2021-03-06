Arty Z7-10 Out of Box Demo
==========================

Description
-----------
This repository contains the Out-of-Box Demo for the Arty Z7-10. It similar to the demo that comes preprogrammed on the board when shipped to customers. The demo uses a wide range of the board's peripherals, including the HDMI video inputs and outputs, audio output, LEDs, buttons, and USB-UART bridge.
The demo forwards signals from the HDMI input port to the HDMI output port. To use this feature of the demo, an HDMI capable computer and an HDMI capable monitor are required, as well as two HDMI cables.
When any button is pressed, an audio sample is generated by the Zynq processor and is streamed out over the audio output jack for approximately 4.5 seconds. The sample generated is a 261 Hz sine wave, also known as the musical note C4.
As long as the demo is running, the two RGB LEDs alternate cycling through the colors red, green, blue, and white.
The user LEDs are continuously set to the state of user buttons. When only one of the user switches is switched on, the LEDs are inverted.
Status messages are printed out over UART to a connected Serial Terminal. . See the Requirements section below for instructions on how to install and use an application to view these messages.

Requirements
------------
* **Arty Z7-10**: To purchase a Arty Z7-10, see the [Digilent Store](https://store.digilentinc.com/arty-z7-apsoc-zynq-7000-development-board-for-makers-and-hobbyists/).
* **Vivado 2018.2 Installation with Xilinx SDK**: To set up Vivado, see the [Installing Vivado and Digilent Board Files Tutorial](https://reference.digilentinc.com/vivado/installing-vivado/start).
* **Serial Terminal Emulator Application**: For more information see the [Installing and Using a Terminal Emulator Tutorial](https://reference.digilentinc.com/learn/programmable-logic/tutorials/tera-term).
* **MicroUSB Cable**
* **Headphones or Speaker with 3.5 mm Audio Jack**
* **HDMI Cable**
* **HDMI capable Monitor/TV**

Demo Setup
----------
1. Download the most recent release ZIP archive ("Arty-Z7-10-OOB-2018.2-*.zip") from the repo's [releases page](https://github.com/Digilent/Arty-Z7-10-OOB/releases).
2. Extract the downloaded ZIP.
3. Open the XPR project file, found at \<archive extracted location\>/vivado_proj/Arty-Z7-10-OOB.xpr, included in the extracted release archive in Vivado 2018.2.
4. In the toolbar at the top of the Vivado window, select **File -> Export -> Export Hardware**. Select **\<Local to Project\>** as the Exported Location and make sure that the **Include bitstream** box is checked, then click **OK**.
5. In the toolbar at the top of the Vivado window, select **File -> Launch SDK**. Select **\<Local to Project\>** as both the workspace location and exported location, then click **OK**.
6. With Vivado SDK opened, wait for the hardware platform exported by Vivado to be imported.
7. In the toolbar at the top of the SDK window, select **File -> New -> Application Project**.
8. Fill out the fields in the first page of the New Application Project Wizard as in the table below. Most of the listed values will be the wizard's defaults, but are included in the table for completeness.

| Setting                                 | Value                            |
| --------------------------------------- | -------------------------------- |
| Project Name                            | arty_z7_10_oob                   |
| Use default location                    | Checked box                      |
| OS Platform                             | standalone                       |
| Target Hardware: Hardware Platform      | design_1_wrapper_hw_platform_0   |
| Target Hardware: Processor              | ps7_cortexa9_0                   |
| Target Software: Language               | C                                |
| Target Software: Board Support Package  | Create New (arty_z7_10_oob_bsp)  |

9. Click **Next**.
10. From the list of template applications, select "Empty Application", then click **Finish**.

**Note**: Steps 11-16 describe how to add math library support to an application project, for more information see (Xilinx Answer Record 52971)[https://www.xilinx.com/support/answers/52971.html].

11. In the project explorer, right click on the new application project (arty_z7_10_oob) and select **Properties**.
12. In the properties window that pops up, under **C/C++ Build**, click **Settings**.
13. In the Tool Settings tab, under **ARM v7 gcc linker**, click **Libraries**.
14. To the right of the Libraries pane, click the **Add...** button - the button looks like a sheet of paper with a green plus over it.
15. In the Enter Value popup, type **-m** into the text field. Then click **OK**.
16. Back in the properties window, click **OK**.

17. In the Project Explorer pane to the left of the SDK window, expand the application project (named "arty_z7_10_oob").
18. Right click on the "src" subdirectory of the application project and select **Import**.
19. In the "Select an import wizard" pane of the window that pops up, expand **General** and select **File System**. Then click **Next**.
20. Fill out the fields of the "File system" screen as in the table below. Most of the listed values will be the defaults, but are included in the table for completeness.

| Setting                                                | Value                                      |
| -                                                      | -                                          |
| From directory                                         | \<archive extracted location\>/sdk_appsrc  |
| Files to import pane: sdk_appsrc                       | Checked box                                |
| Into folder                                            | arty_z7_10_oob/src                    |
| Options: Overwrite existing resources without warning  | Checked box                                |
| Options: Create top-level folder                       | Unchecked box                              |

21. Click **Finish**.
22. Plug in the HDMI IN/OUT cables as well as the HDMI capable Monitor/TV. Plug in the headphones or speaker.
23. Open a serial terminal application (such as [TeraTerm](https://ttssh2.osdn.jp/index.html.en) and connect it to the Arty Z7-10's serial port, using a baud rate of 115200.
24. In the toolbar at the top of the SDK window, select **Xilinx -> Program FPGA**. Leave all fields as their defaults and click "Program".
25. In the Project Explorer pane, right click on the "arty_z7_10_oob" application project and select "Run As -> Launch on Hardware (System Debugger)".
26. The application will now be running on the Arty Z7-10. It can be interacted with as described in the first section of this README.

Next Steps
----------
This demo can be used as a basis for other projects by modifying the hardware platform in the Vivado project's block design or by modifying the SDK application project.
Check out the Arty Z7-10's [Resource Center](https://reference.digilentinc.com/reference/programmable-logic/arty-z7/start) to find more documentation, demos, and tutorials.
For technical support or questions, please post on the [Digilent Forum](forum.digilentinc.com).

Known Issues
------------
* Parts of the HDMI passthrough do not meet timing.
* The audio sample can be "static-ey" at higher volumes/amplitudes.

Additional Notes
----------------
For more information on how this project is version controlled, refer to the digilent-vivado-scripts submodule's [readme](https://github.com/digilent/digilent-vivado-scripts).