# BMS
The options out there for BMSs are lookin quite slim. There are some "dumb" BMSs out there, but I need something that I can activly query/command from a microcontroller. Any of those that you can do that with are quite expensive.


 ## [ENNOID BMS](https://www.ennoid.me/bms/gen-1)
 ENNOID BMS is a master/slave setup. It has a single *master* board that controls the rest of the daisy-chained slaves. This is similar to how the Model S battery modules work. Each module has a little BMS board that monitors that specific module, that then daisy chains the to rest of the modules, and finally terminates at a controller board of some sort.
 
 ENNOID BMS is [semi-open source](https://github.com/EnnoidMe/ENNOID-BMS) (no PCB files shared 😟). It looks to be using VESC BMS stuff, at least for configuration, which is cool. ENNOID BMS uses the LTC6811/LTC6813 BMS chips for the slaves.
 
 Master seems to do a lot of things, but only supports 500a. Given a single Tesla drive unit can pull ~1000a this is already a no-go. It does use a standard STM32 microcontroller so I could write custom firmware for it, but if I'm going that far I'd probably just make my own master that works with the sensors I want, how I want.
 
The LTC chips are in very short supply right now (2023/01) so the slaves might be tough to get, and probably makes them expensive. In fact, lets do some quick math:
For this project I'd need either (Assuming I went th 142 LTO cells for a ~400v pack):{{ for slave in ENNOID.Slaves }}
  - {{slave.Count}} x {{slave.Name}} board at ${{slave.Price}}: ${{slave.Price * slave.Count}}{{ end }}

Add in the price of the master at ${{ENNOID.MasterPrice}} and you can see this starting to get expensive, especially considering it doesn't have the features the competition below does.

One major pro is that the firmware is entirely open source. So if something doesn't work the way I like, I can just change it.


## [Orion BMS 2](https://www.orionbms.com/products/orion-bms-standard/)
The Orion BMS 2 is quite a mature product, but seems to be a bit of a walled garden. I downloaded the config software and poked around at it and, while it's nice, it certainly reminds me of controller software for things like the Kelley Controllers and the Delta Q chargers, and that's not a good thing for my purposes. One of their resellers had the 144 cell unit priced at ~$2500 bucks.

Their software (Orion BMS 2 Control Application) has a menu to "Enter a Service Code". Not sure what this is, but if I spend $2500 on a BMS I better have access to literally everything it has to offer. Other softwares, like the Delta Q Charger configuration software for example, lock you out of certain things unless you have a *super secret password*. If I wanted to be locked out of software on a device I own I'd buy an actual Tesla.

It has a lot of bells and whistles that I quite like, such as monitoring battery current, cell resistance, and most importantly **fully configurable CAN messages**. 

My biggest gripe with proprietary devices in projects like this is that they don't give me enough info. I want to see *everything*, and the BMS has the most data that I'd want to access. Things like per-cell voltage, temps, current, balance state, all that. 

Not only that, I'd love to be able to configure the thing over CAN so I don't have to use their program. Ideally I'm going to write my own little UI that runs on a cheap Android headunit. Thankfully, it appears that the Orion BMS 2 supports most, if not all of this.

Here's my notes on it's CAN-ness:
 - You can configure up to 16 custom can bus messages in the OBMS2, as detailed [here](https://www.orionbms.com/downloads/misc/editing_canbus_messages.pdf).
 - You're able to query data from the BMS, using an OBD2-like format. [Details here](https://www.orionbms.com/general/retrieving-data-obd2-canbus/).
 - You can set the BMS to transmit cell stats over the CAN bus at varying intervals.
   - <details>
        <summary>BMS Cell Broadcast Message (copied from their in-software help)</summary>

      ## Battery Cell Broadcast Message

      For some applications it is necessary to see the real-time voltages from all the cells in a quick and efficient manner. This set of options allows the user to enable a constant CANBUS broadcast message that will sequentially send all the cell voltages by going through one at a time.

      **Enable Battery Cell Broadcast**: This allows the user to enable or disable the broadcast from being regularly transmitted at all and which CANBUS interface it gets transmitted on.

      **Battery Cell Broadcast Speed [ms]**: This value represents the amount of time between message transmissions for this broadcast (eg: a value of 8ms means the message is transmitted once every 8ms).

      **Battery Cell Broadcast CAN ID**: This allows the user to specify the CANBUS message ID for this transmission broadcast.

      **NOTE:** Due to the high speed of the messages, this should not typically be enabled on an already crowded CANBUS interface, or on a CANBUS interface that has critical devices on it unless is programmed for a slow transmission rate. It is possible that the increased traffic can reduce the response time of other devices on the selected interface.

      This should only be enabled on interfaces with a frequency of 250kBps or higher.**

      The format for this message is as follows:

      Byte 0: Cell ID (8 bit, starting with 0)\
      Byte 1&2: Instant Voltage (16 bit, unit: 0.1mv)\
      Byte 3&4: Internal Resistance (15 bit, unit: 0.01mOhm)\
      Byte 5&6: Open Voltage (16 bit, unit: 0.1mv)\
      Byte 7: Checksum (8 bit)

      **Bit 8 in byte #3 is whether or not the cell is shunting (1 indicates current is being shunted, 0 means it is not).**

      Checksum Calculation:

      1.  Take the broadcast ID and add 8 (the length).

      2.  Add bytes 0-6 to the value from step 1.

      3.  Chop off the least significant 8 bits (effectively turning it into an unsigned byte) and that will be the checksum value.

      4.  If the computed checksum does not equal the provided checksum, the values should be discarded.
      </details>

# Roll my own
If nothing sticks out to me, I'll look into making my own BMS solution. Probably using a more commonly available chip than the LTC6811. Maybe the LTC6803 instead? Haven't looked into it too hard though.