Introduction
============

.. image:: https://readthedocs.org/projects/adafruit-circuitpython-ds3502/badge/?version=latest
    :target: https://circuitpython.readthedocs.io/projects/ds3502/en/latest/
    :alt: Documentation Status

.. image:: https://img.shields.io/discord/327254708534116352.svg
    :target: https://adafru.it/discord
    :alt: Discord

.. image:: https://github.com/adafruit/Adafruit_CircuitPython_DS3502/workflows/Build%20CI/badge.svg
    :target: https://github.com/adafruit/Adafruit_CircuitPython_DS3502/actions/
    :alt: Build Status

CircuitPython library for the Maxim DS3502 I2C Potentiometer


Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_
* `Bus Device <https://github.com/adafruit/Adafruit_CircuitPython_BusDevice>`_
* `Register <https://github.com/adafruit/Adafruit_CircuitPython_Register>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://github.com/adafruit/Adafruit_CircuitPython_Bundle>`_.

Installing from PyPI
--------------------

On supported GNU/Linux systems like the Raspberry Pi, you can install the driver locally `from
PyPI <https://pypi.org/project/adafruit-circuitpython-ds3502/>`_. To install for current user:

.. code-block:: shell

    pip3 install adafruit-circuitpython-ds3502

To install system-wide (this may be required in some cases):

.. code-block:: shell

    sudo pip3 install adafruit-circuitpython-ds3502

To install in a virtual environment in your current project:

.. code-block:: shell

    mkdir project-name && cd project-name
    python3 -m venv .env
    source .env/bin/activate
    pip3 install adafruit-circuitpython-ds3502

Usage Example
=============

.. code-block:: python

    from time import sleep
    import board
    import adafruit_ds3502
    from analogio import AnalogIn

    ####### NOTE ################
    # this example will not work with Blinka/rasberry Pi due to the lack of analog pins.
    # Blinka and Raspberry Pi users should run the "ds3502_blinka_simpletest.py" example

    i2c = board.I2C()
    ds3502 = adafruit_ds3502.DS3502(i2c)
    wiper_output = AnalogIn(board.A0)

    while True:

        ds3502.wiper = 127
        print("Wiper set to %d"%ds3502.wiper)
        voltage = wiper_output.value
        voltage *= 3.3
        voltage /= 65535
        print("Wiper voltage: %.2f"%voltage)
        print("")
        sleep(1.0)
        
        ds3502.wiper = 0
        print("Wiper set to %d"%ds3502.wiper)
        voltage = wiper_output.value
        voltage *= 3.3
        voltage /= 65535
        print("Wiper voltage: %.2f"%voltage)
        print("")
        sleep(1.0)

        ds3502.wiper = 63
        print("Wiper set to %d"%ds3502.wiper)
        voltage = wiper_output.value
        voltage *= 3.3
        voltage /= 65535
        print("Wiper voltage: %.2f"%voltage)
        print("")
        sleep(1.0)


Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_DS3502/blob/master/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.

Documentation
=============

For information on building library documentation, please check out `this guide <https://learn.adafruit.com/creating-and-sharing-a-circuitpython-library/sharing-our-docs-on-readthedocs#sphinx-5-1>`_.
