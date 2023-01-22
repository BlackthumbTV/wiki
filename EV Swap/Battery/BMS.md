# BMS
The options out there for BMSs are lookin quite slim. There are some "dumb" BMSs out there, but I need something that I can activly query/command from a microcontroller. Any of those that you can do that with are quite expensive.

Current options:
 - (ENNOID BMS)[https://www.ennoid.me/bms/gen-1]
   - [Semi-open source](https://github.com/EnnoidMe/ENNOID-BMS) (no PCB files shared 😟)
   - Looks to be using VESC BMS stuff, at least for configuration
   - Master seems to do a lot of things, but only supports 500a
     - Uses the LTC6811/LTC6813, so could just get slave boards and make a custom master.
     - The LTC chips are in very short supply right now (2023/01) so might be tough to get
   - Expensive materials, expensive to buy
     - For this project I'd need either (Assuming I went with 142 LTO cells for a ~400v pack):
        {{ for slave in ENNOID.Slaves }}

        - {{slave.Count}} x {{slave.Name}} board at ${{slave.Price}}: ${{slave.Price * slave.Count}}
        {{ end }}
 - [Orion BMS 2](https://www.orionbms.com/products/orion-bms-standard/)
   - Mature product, but seems to be a bit of a walled garden
     - Their software (Orion BMS 2 Control Application) has a menu to "Enter a Service Code". Not sure what this is, but if I spend $2500 on a BMS I better have access to literally everything it has to offer.
   - Has a lot of bells and whistles that I quite like
     - Can monitor cell resistance which is nice
     - Monitors battery current. Again, very nice