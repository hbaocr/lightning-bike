lightning payable e-bike

The lightning-bike is an e-bike (pedelec) whose electrical support can be booked for a certain period of time. 
It uses lightning as a payment system to activate this feature. You select on the display how long you want to drive, 
get a qr-code that you scan and pay for with your lightning mobile APP, after that the power for the selected period is turned on. The special about this system, it's mobile, the communication is realized via the mobile network and the power comes from the 
battery of the e-bike.

The heart of the system is a Raspberry Pi Zero WH, which controls both the connection to the mobile network and the switching 
of the power supply via a relay. An e-paper display is used as a monitor, which practically also provides 4 switches for the 
control of the programm. I mainly used the e-paper display because it consumes very little power, actually only when the screen 
changes, the contrast and good readability even on sunny days. The image composition is quite long with about 6 seconds, but it 
will be require only 2 steps/images to complete the payment process.

The bike:

A normal 28 inches men's bike with derailleur system, what I converted into a e-bike with a conversion kit from the company 
YOSE Power (Ebay). The conversion kit includes a 250W front engine witch complies with the legal requirements, so it can be used
in normal road traffic. The conversion, that's a story for itself!

The system consists of two parts:

On the server side there is a Raspberrypi 3 there runs a lightning node based on c-lightning https://github.com/ElementsProject/lightning This installation differs only in that there is no Bitcoin fullnode installed. I use the pseudonode sPRUNED https://github.com/gdassori/spruned/ which has the advantage that I only need about 300MB for the bitcoin blockchain. This step is optional and not required, but I wanted to learn more about the stability of sPRUNED. If you do not already run a bitcoin fullnode, you should start with it, it will run a bit more stable and strengthen bitcoin network at the same time! For the lightning node control i use the lightning-charge API https://github.com/ElementsProject/lightning-charge. That was the main reason for me to choose the c-lightning implementation. With lightning-charge it was very easy to programm the payment processes.

On the client side, i choice a raspberry Pi Zero WH with an e-paper display, mainly to keep power consumption as low as possible. More problematic in power consumption is certainly the USB modem/network card, there is perhaps a better way. The relay 
for switching the power for the system is controlled via GPIO and also the 4 switches of the e-paper queried via GPIO.




