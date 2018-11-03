Sipeed M1 Guide
=================================================

Sipeed M1, an embedded AI development platform.

Lichee Dan is an excellent open source AI development kit in China. It aims to promote AI-related development and education, and integrates Micropython to make development no longer difficult.

.. figure:: http://pgeza64pd.bkt.clouddn.com/dan-board.jpg
  :width: 500px
  :align: center
  
  Sipeed M1
 
Sipeed M1 uses the AI chip k210 of Kendryte as the core unit.Dual core with independent FPU,64-bit CPU bit width,8M on-chip SRAM,adjustable nominal CPU frequency of 400M,FPU supports multiplication, division and square root double precision operations

In the AI processing, k210 can perform convolution, batch normalization, activation, pooling, etc.At the same time, the pre-processing of voice direction scanning and voice data output can also be performed.

Sipeed has the following abilities

- Camera Interface (DVP)
- Universal Asynchronous Receiver/Transmitter (UART)
- Direct Memory Access Controler (DMAC)
- Inter－Integrated Circuit (I²C)
- Serial Peripheral Interface (SPI)
- Inter—IC Sound (I²S)
- Joint Test Action Group (JTAG)
- Field Programmable IO array(FPIOA/IOMUX)

What’s amazing is that Sipeed M1 also has

- Neural network processor (KPU)
- Audio processor (APU)
- Fast Fourier transform accelerator (FFT Accelerater)
- Advanced Encryption Standard Accelerater (AES Accelerater) 
- Secure Hash Algorithm Accelerater (SHA256 Accelerater)  

|  
.. figure:: http://pgeza64pd.bkt.clouddn.com/dan-core-borad.jpg
  :width: 500px
  :align: center
  
  Sipeed M1 core board

Characteristics of Sipeed M1

- Machine vision
- Machine hearing 
- Better low power vision processing speed and accuracy
- KPU can excute high performance convolutional neural network operations
- Support firmware encryption, it is difficult to crack using common methods
- Unique programmable IO array make product design more flexible
- 3.3V/1.8V dual voltage support
|

Sipeed M1's onboard peripherals

- 72 pins lead-out fully, which can be mapped function freely
- FPC24 can be connected to DVP camera
- FPC24 can be connected to 8bit MCU LCD
- Onboard power amplifier IC for use with speakers
- Onboard Type C interface
- Onboard TF card slot
- Onboard microphone
- Onboard wifi
- Onboard high speed DAC
- Can be used with microphone array expansion board for speech recognition, beamforming, sound field imaging

.. figure:: http://pgeza64pd.bkt.clouddn.com/dan-pin.png
  :width: 500px
  :align: center
  
  Sipeed M1 pin picture

You may need these to know more about Sipeed M1.： `kendryte210_datasheet  <http://pgeza64pd.bkt.clouddn.com/kendryte_datasheet_20180919020633.pdf>`_ | `Sipeed M1 schematic <http://pgeza64pd.bkt.clouddn.com/K210_dock.pdf>`_

Sipeed M1 is still growing. For the appearance, circuit design, document content and even the development direction of Sipeed M1, we welcome you to give your valuable advice to `Sipeed M1 bbs <http://bbs.lichee.pro/t/dan>`_.
 
At the same time, we welcome you to join the `Lichee Telegram group <https://t.me/sipeed>`_ and communicate with many developers and enthusiasts.

.. toctree::
    :maxdepth: 2
    :caption: Get started
	 
    prepare <before_experience/uartCH340_src>
    standalone development <experience/standalone_src>
    FreeRTOS <experience/freeRTOS_src>
