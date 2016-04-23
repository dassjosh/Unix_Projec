===========================
RC Car with Vision Tracking
===========================

The RC Car with Vision Tracking is a custom built RC Car with a raspberry pi as the main computer.
This car uses an arduino and H-drive to control the motor and what speed they run at.
The way the RC car with Vision Tracking moves is by utilizing  a camera to track a ball of a predetermined color.
As a secondary control system we have a bluetooth Playstation 4 control for manual control.

The software used to run the RC 

* GitHub: https://github.com/du-linux/Team1/

Features
--------

- Manually able to control Remote Control Car with Playstation 4 Controller
- Remote Control Car follows a color ball
- Implemented Changing License Plate -- using Arduino
- Implemented Object avoidance, using Ultra Sonic Sensors, with automatic reverse
- Features an Dual H-Bridge that controls all four wheels
- Controlling all 4-wheels with python w/out Arduino
- Reverse Support with the Playstation 4 Controller.


Installation Guide
==================

Dependencies
------------

- `Python <http://python.org/>`_ 2.7 or 3.3+ (for Debian/Ubuntu you need to
  install the *python2.7-dev* or *python3.3-dev* package)
- `python-setuptools <https://pythonhosted.org/setuptools/>`_
- hcitool (usually available in the *bluez-utils* or equivalent package)

These packages will normally be installed automatically by the setup script,
but you may want to use your distro's packages if available:

- `pyudev <http://pyudev.readthedocs.org/>`_ 0.16 or higher
- `python-evdev <http://pythonhosted.org/evdev/>`_ 0.3.0 or higher


Stable release
^^^^^^^^^^^^^^

Installing the latest release is simple by using `pip <http://www.pip-installer.org/>`_:

.. code-block:: bash

    $ sudo pip install ds4drv

Development version
^^^^^^^^^^^^^^^^^^^

If you want to try out latest development code check out the source from
Github and install it with:

.. code-block:: bash

    $ git clone https://github.com/chrippa/ds4drv.git
    $ cd ds4drv
    $ sudo python setup.py install


Using
-----

ds4drv has two different modes to find DS4 devices, decide which one to use
depending on your use case. 

Raw bluetooth mode
^^^^^^^^^^^^^^^^^^

Supported protocols: **Bluetooth**

Unless your system is using BlueZ 5.14 (which was released recently) or higher
it is not possible to pair with the DS4. Therefore this workaround exists,
which connects directly to the DS4 when it has been started in pairing mode
(by holding **Share + the PS button** until the LED starts blinking rapidly).

This is the default mode when running without any options:

.. code-block:: bash

   $ ds4drv


Hidraw mode
^^^^^^^^^^^

Supported protocols: **Bluetooth** and **USB**

This mode uses the Linux kernel feature *hidraw* to talk to already existing
devices on the system.

.. code-block:: bash

   $ ds4drv --hidraw


To use the DS4 via bluetooth in this mode you must pair it first. This requires
**BlueZ 5.14+** as there was a bug preventing pairing in earlier verions. How you
actually pair the DS4 with your computer depends on how your system is setup,
suggested googling: *<distro name> bluetooth pairing*

To use the DS4 via USB in this mode, simply connect your DS4 to your computer via
a micro USB cable.

**Note:** Unfortunately due to a kernel bug it is currently not possible to use
any LED functionality when using bluetooth devices in this mode.


Permissions
^^^^^^^^^^^

If you want to use ds4drv as a normal user, you need to make sure ds4drv has
permissions to use certain features on your system.

ds4drv uses the kernel module *uinput* to create input devices in user land and
the module *hidraw* to communicate with DualShock 4 controllers (when using
``--hidraw``), but this usually requires root permissions. You can change the
permissions by copying the `udev rules file <udev/50-ds4drv.rules>`_ to
``/etc/udev/rules.d/``.

You may have to reload your udev rules after this with:

.. code-block:: bash

    $ sudo udevadm control --reload-rules
    $ sudo udevadm trigger


Configuring
-----------

Configuration file
^^^^^^^^^^^^^^^^^^

The preferred way of configuring ds4drv is via a config file.
Take a look at `ds4drv.conf <ds4drv.conf>`_ for example usage.

ds4drv will look for the config file in the following paths:

- ``~/.config/ds4drv.conf``
- ``/etc/ds4drv.conf``

... or you can specify your own location with ``--config``.


Command line options
^^^^^^^^^^^^^^^^^^^^
You can also configure using command line options, this will set the LED
to a bright red:

.. code-block:: bash

   $ ds4drv --led ff0000

See ``ds4drv --help`` for a list of all the options.


Multiple controllers
^^^^^^^^^^^^^^^^^^^^

ds4drv does in theory support multiple controllers (I only have one
controller myself, so this is untested). You can give each controller
different options like this:

.. code-block:: bash

   $ ds4drv --led ff0000 --next-controller --led 00ff00

This will set the LED color to red on the first controller connected and
green on the second.


Known issues/limitations
------------------------

- `Bluetooth 2.0 dongles are known to have issues, 2.1+ is recommended. <https://github.com/chrippa/ds4drv/wiki/Bluetooth%20dongle%20compatibility>`_
- The controller will never be shut off, you need to do this manually by
  holding the PS button until the controller shuts off
- No rumble support


References
----------

The DualShock 4 report format is not open and had to be reverse engineered.
These resources have been very helpful when creating ds4drv:

- http://www.psdevwiki.com/ps4/DualShock_4
- http://eleccelerator.com/wiki/index.php?title=DualShock_4
- https://gist.github.com/johndrinkwater/7708901
- https://github.com/ehd/node-ds4
- http://forums.pcsx2.net/Thread-DS4-To-XInput-Wrapper


----

.. |dogecoin| image:: http://targetmoon.com/img/dogecoin.png
  :alt: Dogecoin
  :target: http://dogecoin.com/

|dogecoin| DCbQgDa4aEbm9QNm4ix6zYV9vMirUDQLNj



RC Car with Vision Tracking

The RC Car with Vision Tracking is a custom built RC Car with a raspberry pi as the main computer.
This car uses an arduino and H-drive to control the motor and what speed they run at.
The way the RC car with Vision Tracking moves is by utilizing  a camera to track a ball of a predetermined color.
As a secondary control system we have a bluetooth Playstation 4 control for manual control.

The software used to run the RC 






