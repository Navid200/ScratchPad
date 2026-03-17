---
title: "Dexcom G7 vs G6: key differences when using xDrip"
description: "Learn the key differences between Dexcom G6 and G7 when using xDrip, including sensor behavior, connection order, session handling, and data transmission."
---

# Dexcom G7 vs G6: key differences when using xDrip  
[xDrip](../../) >> [Features](../Features_page.md) >> [xDrip & Dexcom](../Dexcom_page.md) >> Dexcom G7 vs G6: key differences when using xDrip  
  
Many Dexcom G6 users are now preparing to switch to G7. This page outlines the key differences you can expect when using G7 with xDrip.  
  
1- There are more fluctuations in readings, especially during the first day of a sensor. This is not related to xDrip.  
If you use AAPS, you can use one of the existing smoothing options in AAPS to address this.   
  
2- A G6 session needs to be started from an app, receiver, or pump. A G7 session starts automatically when you insert the sensor.  
Therefore, there is no start sensor option for G7 in xDrip.  
Since you do not need to start a G7 session, there is also no need to stop one. That is why there is no stop option for G7 in xDrip.  
  
3- You can use xDrip to connect to a G6 transmitter by entering its serial number (transmitter ID), even if another G6 transmitter is in range.  
If you have a G7 that is active but not connected to xDrip, the app, or a receiver, and you want to connect to another G7, you may have difficulty.  You can address this by following the guides.  
  
4- You are advised to connect a pump before connecting xDrip to G6.  
If your pump can connect directly to G7, you should connect xDrip to G7 first before connecting the pump.  Similarly, if you have a G7 receiver, connect xDrip first before connecting the receiver.  
  
5- G6 has only one mode of operation, transmitting once every 5 minutes.  
G7 also transmits every 5 minutes but includes a "rapid reconnect" mode in which it transmits once per minute. It transitions to this mode if it has no connectivity for 15 consecutive minutes.  
  
6- A G6 sensor runs for 10 days, and the Dexcom app reports this clearly. xDrip also reports 10 days.  
A G7 runs for 10.5 days, but the Dexcom app reports it as 10 days with a 12-hour grace period. xDrip reports the full 10.5-day duration.  
  
---  

[How to start a G7](./G7.md)  
[How to start a subsequent G7](./SubsequentG7.md)  
[G7 grace period](./G7_Grace.md)  
