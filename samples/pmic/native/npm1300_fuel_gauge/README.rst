.. _npm1300_fuel_gauge:

nPM1300: Fuel gauge
###################

.. contents::
   :local:
   :depth: 2

The Fuel gauge sample demonstrates how to calculate the battery state of charge using the :ref:`nrfxlib:nrf_fuel_gauge`.

Requirements
************

The sample supports the following development kit:

.. table-from-sample-yaml::

The sample also requires an nPM1300 EK.

Overview
********

This sample allows to calculate the state of charge, time to empty and time to full information from a battery connected to the nPM1300 PMIC.

Wiring
******

#. Connect the TWI interface between the chosen DK and the nPM1300 EK as in the following table:

   .. list-table:: nPM1300 EK connections.
      :widths: 25 25
      :header-rows: 1

      * - nPM1300 EK pins
        - nRF52 DK pins
      * - SDA
        - P0.26
      * - SCL
        - P0.27
      * - GND
        - GND

#. Make the following connections on the nPM1300 EK:

   * Connect a USB power supply to the **J3** connector.
   * Connect a suitable battery to the **J2** connector.
   * On the **P18** pin header, connect **VOUT2** and **VDDIO** pins with a jumper.
   * On the **P2** pin header, connect **VBAT** and **VBATIN** pins with a jumper.
   * On the **P17** pin header, connect all LEDs with jumpers.
   * On the **P13** pin header, connect **RSET1** and **VSET1** pins with a jumper.
   * On the **P14** pin header, connect **RSET2** and **VSET2** pins with a jumper.

Building and running
********************

.. |sample path| replace:: :file:`samples/npm1300_fuel_gauge`

.. include:: /includes/build_and_run.txt

Testing
*******

|test_sample|

#. |connect_kit|
#. |connect_terminal|

If the initialization was successful, the terminal displays the following message with status information:

.. code-block:: console

   PMIC device ok
   V: 4.101, I: 0.000, T: 23.06, SoC: 93.09, TTE: nan, TTF: nan

.. _table::
   :widths: auto

   ======  ===============  ==================================================
   Symbol  Description      Units
   ======  ===============  ==================================================
   V       Battery voltage  Volts
   I       Current          Amps (negative for charge, positive for discharge)
   T       Temperature      Degrees C
   SoC     State of Charge  Percent
   TTE     Time to Empty    Seconds (may be NaN)
   TTF     Time to Full     Seconds (may be NaN)
   ======  ===============  ==================================================

Dependencies
************

The sample uses the following `sdk-nrfxlib`_ library:

* :ref:`nrfxlib:nrf_fuel_gauge`

In addition, it uses the following Zephyr libraries:

* :ref:`zephyr:logging_api`
* :ref:`zephyr:shell_api`
