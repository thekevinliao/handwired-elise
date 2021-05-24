# handwired-elise

<h2> Handwired Keyboard Project: 40% Acrylic Alice Layout </h2>
<br />

 ![Finished Keyboard](https://github.com/thekevinliao/handwired-elise/blob/main/images/finished_board.jpeg)

 <ul>
    <li>Case: <a href="https://www.etsy.com/listing/689561858/prime-e-acrylic-case?ref=shop_home_active_12&crt=1&variation0=1080073886&variation1=1553392155">Prime E Acrylic Case (Great service, highly reccomend)</a></li>
    <li>Switches: Lubed and Filmed Holy Chickies (Halo Stem in Cherry Mx Blue housing</li>
    <li>Stabilizers: <a href="https://flashquark.com/product/genuine-cherry-plate-mounted-stabilizers/">Genuine Cherry Plate-Mounted Stabilizers</a>
    <li>Keycaps: <a href = "https://www.originativeco.com/products/pbt-valentine">ePBT Valentine</a></li>
 </ul>

 <br />


<h3>Software Resources Used</h3>
<ul>
    <li><a href = "http://www.keyboard-layout-editor.com/">keyboard-layout-editor</a></li>
    <li><a href = "https://kbfirmware.com/">kbfirmware</a></li>
    <li><a href = "https://github.com/qmk/qmk_toolbox">QMK Toolbox</a></li>
</ul>

<br />

<h3>Parts needed for build<h3>
<ul>
    <li><a href = "https://flashquark.com/product/1n4148-diodes/">1N4148 Diodes</a></li>
    <li><a href = "https://keeb.io/products/elite-c-low-profile-version-usb-c-pro-micro-replacement-atmega32u4">Elite C v4 Microcontroller</a></li>
    <li>Soldering Iron</li>
    <li>Solder</li>
    <li>Some plan for insulation (Insulated wire, electrical tape, etc)</li>
    <li>A USB-C to USB wire</li>
</ul>

<br />

<h3>Creating the software</h3>
<h4>Create your desired layout on keyboard-layout-editor and upload the JSON file to kbfirmware</h4>

 ![Key Layout](https://github.com/thekevinliao/handwired-elise/blob/main/images/kbfirmware_key_editor.JPG)

<p>This will let you map the symbols you want to correspond to each key on the keyboard. This can be edited later on. Because of the compact nature of this keyboard,
I will be using multiple layers of function keys. In the image, MO(1) is the key to change to the first layer and MO(2) is the key to the second layer, with the default layer
being MO(0). Now that you have a keymap you are satisfied with, it's time to get to planning your handwire. </p>

![Wiring Layout](https://github.com/thekevinliao/handwired-elise/blob/main/images/kbfirmware_wiring.jpg)

<p>This section is just used to draw out your rows and columns to know where you want to solder your connections. This will make it much easier to connect rows and columns to the correct
position on your microcontroller.</p>

<h4>Find the pinout of your microcontroller and determine which pins you want your rows and columns to connect to</h4>

![Pinout](https://github.com/thekevinliao/handwired-elise/blob/main/images/pinout.png)

<p>In this case, refer to the pins by the labels marked in blue. In my keyboard, the pins used for my rows were F7, F6, F5 and F4, and my columns were 
D1, D0, D4, C6, D7, E6, B4, B5, D5, C7, F1, F0, B6. Make sure to only use the Digital I/O pins and none of the voltage ones, such as GND or RST. Try and print this out, as you will need this when you being building</p>
<p>Finally, download the JSON and HEX file of this firmware and save it somewhere. You'll need the HEX file to flash your keyboard with the firmware and the JSON file to make changes later</p>

<br />

<h3>Building the keyboard</h3>

![Empty Case](https://github.com/thekevinliao/handwired-elise/blob/main/images/empty_case.jpg)

<p>This is the case of this keyboard. The first step is to insert the switches into the plate, making sure that they are inserted in the correct orientation (luckily with handwired builds, we can have south facing switches without any problems). This case actually uses PCB mount stabilizers, so I had to superglue the stabilizers to the side of plate. It is important to make sure that it is straight and not misaligned, or your stabilizers are not going to feel nice at all. Once you inserted all the switches, you should probably superglue them down. Although this is optional, it allows you to change keycaps without ripping out the wiring and potentially ruining your board.</p>

![Inserted Switches](https://github.com/thekevinliao/handwired-elise/blob/main/images/inserted_switches.jpg)

<p>Next, its time to turn it around and start soldering. Using your 1N4148 Diodes. You want to solder the orange side of the diode onto the first pin of the switch. It is best to wrap the diode around the pin, solder it on, and cut off the excess with wire cutters.</p>

![Diode Example](https://github.com/thekevinliao/handwired-elise/blob/main/images/diode_example.png)

<p>With the bottom leg, bend it towards the switch to the right of its row. On the last switch, you can just snip this leg off. For the gap in the middle, I had to use a small bit of wire to maintain a connection as the diodes were not long enough. Once you solder each diode on each switch, you can solder the rows together. The easiest way to do this is to apply a little bit of solder onto the leg of the first diode, have the two diodes touch, and then melt the solder so there is a connection. At the end, it should look something like this (I took this picture before I finished soldering the bottom row, you need wiring to cover those gaps)</p>

![Finished Rows](https://github.com/thekevinliao/handwired-elise/blob/main/images/soldered_horizontal_diodes.jpg)

<p>Next, its time to move onto the columns. This time, you will need to use some form of wire. In my case, I used insulated wire to make sure nothing could short, but there are multiple ways to achieve this. I stripped my wire like this: (image creditted to QMK)</p>

![Stripped Wire](https://github.com/thekevinliao/handwired-elise/blob/main/images/stripped_wire.jpeg)

<p>These gaps will be connected to the second pin of the switch, like so: </p>

![Finished Columns](https://github.com/thekevinliao/handwired-elise/blob/main/images/soldered_vertical_diodes.jpg)

<p>Once that is done, it is finally time to connect the rows and columns on to the microcontroller. Attach a piece of wire from a row of column onto the pin you assigned it to and solder it on. Make sure that the metal parts of the wire are not touching each other or it will short and not reach the correct key properly. This can be tedious and requires careful hands, so take your time.</p>

![Finished Micro](https://github.com/thekevinliao/handwired-elise/blob/main/images/soldered_to_microcontroller.jpeg)

<p>And just like that, if nothing went wrong, your keyboard should be good to flask</p>

<h3>Flashing your keyboard</h3>
<p>Open up QMK and plug your keyboard in. This will put your keyboard in bootloader mode, which is a state your keyboard needs to be to flask your keyboard. Find the HEX file you saved earlier in the local files section and make sure the MCU is in atmega32u4. From there, you should be able to flash. You should see a message like this in the terminal.</p>

![Flash](https://github.com/thekevinliao/handwired-elise/blob/main/images/qmk_flash.png)

</p>Open up a text file and try testing if all of your keys work. You should do this before you put your keycaps on, so if there are any problems, you don't have to take off all of your keycaps. If there are any issues, turn the keyboard around and check the connections. Are any wires touching each other? Is the solder on the microcontroller touching? Did any solder fall off of the switches themselves? Did you make your firmware correctly? For troubleshooting purposes, please refer to this <a href="https://beta.docs.qmk.fm/using-qmk/guides/keyboard-building/hand_wire">Handwiring guide by QMK</a></p>
