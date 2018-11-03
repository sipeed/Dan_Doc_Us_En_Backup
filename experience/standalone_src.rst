Build a standalone development environment
=================================================

.. contents:: Article directory

Download sdk
-------------------------------------------------

Sipeed M1 can be developed in both Linux and Windows.

If it is in Linux system, you can download the k210 sdk by following the steps below.

1. Use the command to download k210 standalone development sdk from the network 
``wget https://s3.cn-north-1.amazonaws.com.cn/dl.kendryte.com/documents/kendryte-standalone-sdk-0.3.0.zip`` 

2. unzip sdk
``unzip kendryte-standalone-sdk-0.3.0.zip`` 

3. Enter directory，The contents of the directory are as follows
``cd kendryte-standalone-sdk-0.3.0 && ls`` 

:: 

	 CHANGELOG.md  cmake  CMakeLists.txt  lds  lib  LICENSE  README.md  src

（window to be added...）

Programming
-------------------------------------------------

If it is in Linux system, you can write the code by the following operations.

1. Take hello_world as an example,create a directory using the command in the directory *kendryte-standalone-sdk-0.2.1* 
``cd src && mkdir hello_world`` 

2. Use the command to enter the *hello_world* directory, where you can put your own main.c file and other .c or .h files and edit them.
``cd hello_world`` 

3. Create and edit the main.c file and enter the code. Taking hellow_world as an example, enter the following code in main.c and save it.
``vim main.c`` 

.. code-block:: code

		/****************test code************************/
		#include <stdio.h>
		#include "sleep.h"
		#include "encoding.h"
		int main()
		{
		    uint64_t core_id = current_coreid();
		    if (core_id == 0)
		    {
		        printf("Core 0 Hello, world!\n");
		    }
		    else
		    {
		        msleep(100);
		        printf("Core 1 Hello, world!\n");
		    }
		    while (1)
		        ;
		    return 0;
		}

（window to be added...）



Compile code
-------------------------------------------------

If it is in Linux system, you can compile by the following operations.


1. Download k210 toolchain kendryte-toolchain.tar.gz
``wget https://s3.cn-north-1.amazonaws.com.cn/dl.kendryte.com/documents/kendryte-toolchain.tar.gz`` 

2. unzip toolchain
``tar xvf kendryte-toolchain.tar.gz``

You need to configure the environment variables
``export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:your_toolchain_path/bin/``

.. note:: your_toolchain_path is the storage path of the build toolchain

3. Enter kendryte-standalone-sdk-0.2.1 directory,use commands in this directory
``mkdir build && cd build``

4. use commands in this directory *build*
``cmake .. -DPROJ=<ProjectName> -DTOOLCHAIN=YourToolchainPath/bin && make``

.. note:: 其中ProjectName is the your project name，YourToolchainPath is the path of toolchain
	
5. Take hello_world as an example，use following command to compile.After compiling ,``build`` directory will generate the hello_world.bin file, this is the binary file we want to burn
``cmake .. -DPROJ=hello_world -DTOOLCHAIN=/opt/riscv-toolchain/bin && make``

Burning program
-------------------------------------------------

If it is in Linux system, we need to download the `burning script  <http://pgeza64pd.bkt.clouddn.com/isp_auto.py>`_ 

Use command to download burning script
``wget http://pgeza64pd.bkt.clouddn.com/isp_auto.py``

Use command to burn the binary file
``python3 your_isp_auto_path -d /dev/ttyUSB0  your_bin_path -b 200000``

.. note:: your_isp_auto_path is the path of isp_auto.py,your_bin_path is the path of your binary file.

Take my hello_world project as an example, the command is as follows
``python3 /home/isptools/isp_auto.py  -d /dev/ttyUSB0  /opt/k210_sdk/build/hello_world.bin -b 200000``

If it is in windows system，you can burn the binary file by a software.We need to download `burning software  <http://pgeza64pd.bkt.clouddn.com/K-Flash.exe>`_ 

Open the software，As shown in the red circle in the figure, click and select the path where the binary file is located.

.. figure:: http://pgeza64pd.bkt.clouddn.com/bin_path.png
   :width: 250px
   :align: center
  
Select communication serial port

.. figure:: http://pgeza64pd.bkt.clouddn.com/device.png
   :width: 250px
   :align: center

Set baud rate to 2000000

.. figure:: http://pgeza64pd.bkt.clouddn.com/btr.png
   :width: 250px
   :align: center

Click flash to burn, the burning process is about tens of seconds

Run demo
-------------------------------------------------

After burning, you can run the demo after powering on.

In order to view the output of the demo, we need to use the sterminal.Select the serial port corresponding to Sipeed M1.

Because the information will be output at the moment of power-on, at this time, the serial port of Sipeed M1 has not been connected to the host computer, so we need to restart the Sipeed M1 by pressing the RST button on the board after accessing the host computer.

At this point you can see the following debugging information.

.. code-block:: debug

		Core 0 Hello, world!
		Core 1 Hello, world!

Congratulations, you have completed the standalone demo development of Sipeed M1, please continue your AI exploration tour! !

.. admonition:: Note 
	
	You can reference README.md of sdk
	
.. admonition:: Communication and Q&A
	
	For the content of this chapter, if you have any questions, we welcome you to ask questions or share experiences in `Sipeed M1 bbs <http://bbs.lichee.pro/t/sipeed-m1>`_.







