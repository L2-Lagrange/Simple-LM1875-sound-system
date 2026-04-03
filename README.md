# Simple-LM1875-sound-system
This is my design for a simple LM1875 bridge-tied-load sound system. I wanted to design a practical analog amplifier system that is easy to build, has great performance, and makes for good educatoinal material. I have tested this design for several weeks and I am very happy with it. This document is about designing an analog amplifier system that will work with any signal source input. In this case my signal source is a [$3 bluetooth reciever module from Amazon.](https://www.amazon.com/hiBCTR-Wireless-Bluetooth-Audio-Receiver/dp/B0FDLGMMYC/ref=sr_1_8?crid=350EUMJXBN4NV&dib=eyJ2IjoiMSJ9.Hz_ZgfGwXoIZV5nocs7b126nDdCcdYSbgK9A1z3RJKLhT1cz--GEa3WTc_r3OOHGRY9FarT_VZx-J5lBDyLFj8vOGiySonwBIZ1kvVUOeB1Q8dR2eUkfJ7Q_jlzzyOuEYd0lVI_-uhTDe1ct_fYaA3AArWnHJAKOYzXvK3QndtL3qvyXXTN7THovINOcq88VqpU_mcGi9XMeYuAU9Y2iQcgw7ReGjUXgMcREKI2Z7GU.sa2W5zidMW-tkHYAYGa7TfbJ-GyrVTsSYmgwTngp6ZE&dib_tag=se&keywords=bluetooth+module&qid=1775198601&sprefix=bluetooth+modu%2Caps%2C182&sr=8-8)


<p align="center">
  <img src="Images/Amplifier_With_Speaker.jpg" width="300"><br>
</p>


The LM1875 power stage has a bridge-tied-load output. This means the output is taken across a pair of amplifiers that have opposite outputs. BTL increases power output by roughly 4 times, making it more practical to build loud analog amplifiers at low voltage rails.

<p align="center">
  <img src="Images/LM1875_Single_Supply_BTL.png" width="800"><br>
  <em>Schematic:  LM1875 Single Supply Bridge-Tied-Load Schematic</em>
</p>

To make this work, we use a phase splitter. The phase splitter takes in one signal, and outputs the same signal as well as its inverted version. The plase splitter complementary outputs drive the LM1875 power amplifier stage. This design runs from a single DC rail instead of positive and negative rails, so the phase splitter and power stage require a virtual ground. This design uses a buffered voltage divider to generate and distribute the virtual ground to the TL074 and LM1875 amplifiers. The virtual ground at half the supply voltage is what allows us to run the system with a single +24V rail. 

The power rails include bulk electrolitic capacitors and small ceramic capacitors. It is important to have at least a few thousand uF of capacitance on the power rails for the LM1875 board. It is also important to keep 0.1uf ceramic capacitors immediately near each chip's power pins. I also tend to add a 0.1uf capacitor in parallel next to each bulk cap, and then a few extras around the board for good measure. There is a lot of wiggle room for capacitance on the rails. For the capacitor voltage rating, use a value that is around 50% higher than your power rail. For a 24V rail you want to use at least 35V rated capacitors. I used 50V rated capacitors in my build.





<p align="center">
  <img src="Images/Bluetooth_Rx_Analog_Filter_Single_Supply.png" width="800"><br>
  <em>Schematic:  Bluetooth Receiver Analog Filter Board With Gain</em>
</p>




The system is powered by a single DC voltage source between 18-30V, and performs great with [cheap 24V wall power supply bricks](https://www.amazon.com/100V-240V-Terminal-Connector-Adapter-5-5x2-1mm/dp/B0CW598HV8/ref=sr_1_2_sspa?crid=SO4U9JPWYUSR&dib=eyJ2IjoiMSJ9.Wj2MH52ngXubGGHn_jR5-tq3j1g8CH6NQ8uUdveCFZiM2RgN0ZBpEiFOTj8VnqWan0aAO3ANwrCY0JCexMZ2bsMjlpHWn8h4nfXn2Z3OHU4LRMzv8ZXsNwfGOxvwVAQx-4uxml4SoSLu7E3XRWt--kh5I8faRnT2te4GcDbC0yMmAZibx5akN4-dxBs6_6iZVO-5CSu8_1-fQMGQsTG-56A2ATmhaNWGmlust4Jhq9M.yrbyAWJkabPssMtkYnAYnOK17R7ZLXuvFp0E1h8N3uQ&dib_tag=se&keywords=24v+power+supply&qid=1775199681&sprefix=24v+power+supply%2Caps%2C168&sr=8-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1). This means you do not need to build a power supply to design a similar system.

The speaker below the amplifier is 3D printed, but this system should work with any speaker rated at least 30W. This particular build uses a single [PRV Audio 4 inch midrange 30W RMS speaker](https://www.amazon.com/PRV-4MR60-4-Midrange-Woofer-Speaker/dp/B00RC3Z9H2/ref=sr_1_3_pp?crid=1KCQM80K1PAQ5&dib=eyJ2IjoiMSJ9.x3e2p23kjf49gjaOcO_Ginvh5fZAL4RJupKdT0HOsPY2IyrSVZsr_lAZDN7yt-1VV6PE8BlDJDUVkZxbkw7uh2w71MyDrd3TqlnQbStcCKdQm9OpM0VgmFTw19aUo9BUUvu2CqzZcZzMKE7OF60JZGnQrp6TJ6GPyvxGsvEhPAU0sSh2_lbeOkQgoihgaUo2EBoLWyqMaLDjNgtfGIgXMiGLnHADxxvJDaDK5QvGixg.dlc8fJVgHgVgwpuQZBXRm12JyQiUWVWKJPb0BeQVfCQ&dib_tag=se&keywords=4+ohm+speaker&qid=1775198332&sprefix=4+ohm+speak%2Caps%2C161&sr=8-3), but I have tested it with many other 4 and 8 ohm speakers. This document focuses on the power amplifier and bluetooth reciever boards.

The bluetooth reciever used in this particular build [costs roughly $3 on Amazon.](https://www.amazon.com/hiBCTR-Wireless-Bluetooth-Audio-Receiver/dp/B0FDLGMMYC/ref=sr_1_8?crid=350EUMJXBN4NV&dib=eyJ2IjoiMSJ9.Hz_ZgfGwXoIZV5nocs7b126nDdCcdYSbgK9A1z3RJKLhT1cz--GEa3WTc_r3OOHGRY9FarT_VZx-J5lBDyLFj8vOGiySonwBIZ1kvVUOeB1Q8dR2eUkfJ7Q_jlzzyOuEYd0lVI_-uhTDe1ct_fYaA3AArWnHJAKOYzXvK3QndtL3qvyXXTN7THovINOcq88VqpU_mcGi9XMeYuAU9Y2iQcgw7ReGjUXgMcREKI2Z7GU.sa2W5zidMW-tkHYAYGa7TfbJ-GyrVTsSYmgwTngp6ZE&dib_tag=se&keywords=bluetooth+module&qid=1775198601&sprefix=bluetooth+modu%2Caps%2C182&sr=8-8) This reciever works great and uses incredibly low power, but there are more hifi options. There are also no offical datasheets avalible for the chip, but it is still easy to work with. The analog filter after the bluetooth reciever significanly improves the signal quality and makes it usable in a system like this.
