# Holset HE300VG Notes

## Various Sizes
- Oil feed: M12x1.5
- Oil return: uses the flang-looking ones for sale, holes are 50mm apart.
- Coolant lines: M16x1.5
- Uses a T4i flange, whatever that is...
  - See Flanges in this section, I have a DXF that can be used for cutting.

## CAN BUS
The actuator CAN BUS speed is 250kbps. Below is the code I use to both set the vane position, and read it. Note that I use an ESP32 so the code you see here is for their TAWI lib.

### Setting the position

```
void sendPosition(int16_t vgtReq)
{
    vgtReq = constrain(vgtReq, 0, 1000);

    twai_message_t xmit = {0};
    xmit.identifier = 0x0CFFC600;
    xmit.data_length_code = 8;
    xmit.flags = TWAI_MSG_FLAG_EXTD;
    xmit.data[0] = vgtReq;
    xmit.data[1] = vgtReq >> 8;
    xmit.data[2] = 0x01;
    xmit.data[3] = 0xff;
    xmit.data[4] = 0xff;
    xmit.data[5] = 0xff;
    xmit.data[6] = 0xff;
    xmit.data[7] = 0xff;
    twai_transmit(&xmit, pdMS_TO_TICKS(10));
}

```

### Getting the position

```
  void processIncoming()
  {
      twai_message_t message;
      int count = 0;
      while (twai_receive(&message, pdMS_TO_TICKS(10)) == ESP_OK)
      {
          if (message.identifier == 0x18ffc502)
          {
              vgtPos = ((uint16_t)message.data[2] << 8) | message.data[1];
          }
      }
  }
```

### References
The info I used comes from [this](https://www.cumminsforum.com/threads/he351ve-control.1072194/page-3) and [this](https://mopar1973man.com/topic/9632-he351ve-stand-alone-arduino-controller-code-for-2nd-gen-cummins/?page=18).