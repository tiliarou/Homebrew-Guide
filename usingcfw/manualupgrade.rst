.. Homebrew Guide documentation master file, created by
   sphinx-quickstart on Sun Jan 13 23:22:33 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Updating/Downgrading Manually
=============================

When you update your system firmware version, your Nintendo Switch burns a microscopic fuse to prevent your Switch from being able to downgrade. Essentially, if a firmware tries to boot but too many fuses are burnt for that specific firmware version, the system will simply power off, preventing you from booting.

Hekate, ReiNX and SXOS bypass these fuse checks and the fuse burns. By enabling AutoRCM and then manually updating using ChoiDujourNX, you can keep your Switch in a state where it can be downgraded again the future.

You can also use this guide as a way to upgrade your Switch if your Switch does not have access to the internet or is superbanned, and to downgrade your Switch to any firmware version.

.. note:: 
   If something goes wrong or you need help, check `troubleshooting </troubleshooting.html>`_.

.. raw:: html

    <div class="admonition danger" style="color:#C42525" align="center">
		<h1 style="margin-bottom:0.5rem;margin-top:0.5rem;font-size:2.5rem">WARNING</h1>
        <h2>Never enable AutoRCM on an IPATCHED Switch</h2>
        <p>This is only intended to be used on consoles with a vulnerable RCM. Enabling AutoRCM on an IPATCHED Switch will <b>literally BRICK your Switch.</b>
        <h2 style="margin-bottom:0.5rem">If you cannot run payloads from RCM with fusee-gelee, <b>DO NOT ENABLE AUTORCM.</b></h2>
        <h2>Failure to heed this warning <b>will</b> result in a bricked Switch.</h2>
	</div>

.. danger::
    **A later step will give you the option to enable or disable AutoRCM.** AutoRCM is a software method of forcing your Switch to go into RCM on every launch, without the need of a jig or hardmod. Essentially, you are purposefully bricking your Switch in a controlled matter that forces it to launch into recovery. This might sound scary but is not actually dangerous on unpatched Switches, and can be undone at any time.

    * **NEVER EVER EVER ENABLE AUTORCM ON AN IPATCHED SWITCH. THIS IS EQUIVALENT TO BRICKING YOUR SWITCH.**

    AutoRCM has the following benefits:

    * The Switch will not burn any fuses, meaning you can downgrade your Switch to a lower firmware version in the future should the need arise.
    * You will never accidentally boot stock firmware, meaning you can avoid having telemetry data accidentally sent to Nintendo.
    
    AutoRCM has the following disadvantages:

    * You will not be able to boot your Switch at all without a payload sender.
    
    It is **highly recommended that you enable AutoRCM** as if you ever boot your Switch without Hekate, your fuses will burn and you will not be able to cleanly downgrade again in the future.
    
    .. tip::
        If you just want to manually update your system firmware and do not care about burning fuses, you can leave AutoRCM disabled.
        
    .. warning::
        If you are downgrading to a firmware expecting less fuses burnt than you have, AutoRCM is required to boot your Switch until you upgrade again.
   
........
   
Step 1: Preparing Files
-----------------------

1. You need to locate the firmware binaries for the firmware version you want to downgrade to. These cannot be shared here as they are copyrighted (hint: darthsternie)
2. Make sure your SD card includes a basic Hekate/Atmosphere setup (such as the one installed when following this guide)
3. Insert your SD card into your PC
4. Create a new folder on the root of your SD card named **"firmware"**
5. Extract **the contents** of your firmware archive file into the new **/firmware** folder on your SD card
6. Go to switchtools.sshnuke.net
7. Download the latest version of ChoiDujourNX by rajkosto
8. Extract the **ChoiDujourNX.nro** file within the downloaded .ZIP file into the /switch folder on your SD card

........

Step 2: Allow ChoiDujourNX to write to BIS
------------------------------------------

.. note:: 
   If you are not using Atmosphere or Kosmos, skip to step 3.

A new security feature in Atmosphere requires you to explicitly allow applications to write to BIS, something ChoiDujourNX needs to do to upgrade the firmware.
   
1. If you are on Windows, in File Explorer, make sure File Extensions are set to be shown

.. image:: https://i.imgur.com/REKpKTi.png

2. Navigate to **/atmosphere** on your SD card.
3. Create a folder named **flags**
4. Create a blank txt file named **hbl_bis_write.flag**.

    * The file extension must be changed from **.txt** to **.flag**. The filename **hbl_bis_write.flag.txt** is **WRONG**.
    * On Windows, you will be asked to confirm to change the file extension. This means you have done it correctly, choose **OK**.

Step 3: Installing the New Firmware Version
-------------------------------------------

1. Insert your SD card into your Switch
2. Launch Atmosphere CFW
    
3. **IMPORTANT: Plug your Switch in to prevent the Switch from dying midway through the install process**
4. Enter the Homebrew Menu through Album while holding the R button
5. Select **ChoiDujourNX**
6. In ChoiDujourNX, enter the **/firmware** you created earlier and select Choose
7. After processing, select **[x.x.x] (exFAT)** where [x.x.x] is the firmware version you chose
8. After verification, choose **Select Firmware**
9. Choose whether you want to enable or disable AutoRCM (see above for more information). **This will override an existing AutoRCM settings you have, so make sure to pick which you want.**

    * If you are on an IPATCHED Switch and are given the option to enable AutoRCM, **DISABLE IT**. Enabling AutoRCM is equivalent to bricking your Switch.

10. Choose **Start installation**
11. Wait for the firmware update to finish

    * This can be take little time or a long time depending on the situation. Be patient, and don't worry if it finishes very quickly.

12. After installation, select **Reboot** and then **Shutdown Now!**

You can now delete the **/firmware** folder on your SD card.

.. toctree::
   :maxdepth: 2
   :caption: Contents:
