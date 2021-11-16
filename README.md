
# Project Title
# Downlink-Commands-for-Adeunis-Sensors

Adeunis Downlink Commands for LoRaWAN sensors. By this commands, we can easily control devices. Devices should support OTA.

Convert payload from base64 to HEX, 
https://base64.guru/converter/decode/hex

”ElAhwAABAAEBwgA=” =  ”108021c000010001 01c200”.   
•	Frame code(bytes0) = 10: This frame is sent following the reception of a frame with code 0x01, or at the start of the product.
•	0x80(bytes1) = Status bytes.
•	0x21c0(bytes2-3) = These 4 bytes of payload for transmission period of the keep alive frame. 8640 => 8640 x 10s = 86400s = 24h.
•	0x0001(byte4-5) = 1. Transmission period of the periodic frame.
•	0x0001(byte6-7) = 1. History period.
•	0x01c2(byte8-9) = next 4 bytes of payload is sampling period. 450 => 450 x 2s = 900s = 15minutes.
•	0x00(byte10) = No redundancy. 
•	No more payload bytes. We're finished.
To set the reporting interval of Comfort2 at 20minutes, our downlink command should be like, ”41150258”  in HEX. Here, bytes0(0x41) this frame allows us to change the values of requested registers, bytes1(0x15) register 321, bytes 2 and bytes 3 (0x0258) for the sampling period.
If we convert this payload from hex to base64, we’ll get ”QRUCWA==” value for enqueued by ChirpStack. 


To set reporting interval of Adeunis Modbus LoRaWAN at 1minute, our downlink command should be like, ”41010006”  in HEX. Here, bytes0(0X41) this frame allows us to change the values of requested resisters, bytes1 (0X01) register 301, bytes 2 and bytes 3 (0X0006) for the sample period.
If we convert this payload from HEX to base64, we’ll get ”QQEABg==” value for enqueued by ChirpStack.


## Authors

- [arifulmrislam](https://github.com/arifulmrislam)

  
## 🔗 Links
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ariful-islam-arif-2987b51a3/)
[![twitter](https://img.shields.io/badge/twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/arifulislam301)

  