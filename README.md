# efx-jtag-spi-flash-loader
Efinix JTAG SPI Flash loader proxy bitstream.

## Supported devices packages
* BGA49, BGA81 (T4, T8)

---

### Build proxy bitstream
Open the project in efinity and build.

### Load the proxy bitstream
Assuming your are using a FT4232 with JTAG on bus A.
```
source /opt/efinity/2022.2/bin/setup.sh

/opt/efinity/2022.2/bin/python3 /opt/efinity/2022.2/pgm/bin/efx_pgm/ftdi_program.py -m jtag -a "ftdi://0x0403:0x6011/1" outflow/efx_jtag_spi_flash_loader.hex
```
```
Programming 'outflow/efx_jtag_spi_flash_loader.hex' via JTAG at freq 6.0 MHz
Using CRESET, SS control pins as part of T8/T4 JTAG programming...
... finished with JTAG programming
```

### Flash your application bitstream
```
/opt/efinity/2022.2/bin/python3 /opt/efinity/2022.2/pgm/bin/efx_pgm/ftdi_program.py -m jtag_bridge -a "ftdi://0x0403:0x6011/1" path_to_my_bitstream.hex
```
```
Connecting to JTAG_TAP: efx
Manufacturing ID read from Flash Controller (via JTAG): 0xEF
[WARNING ] (get_flashdb) Found 0 matching JEDEC in JSON file
[WARNING ] (get_flashdb) Something not right. Returning empty dict
Unrecognized Flash device. Will use Generic Flash profile. Please contact support if you face any problem.
Flash Controller (via JTAG) at freq 6.0 MHz
Flash device: Generic Flash Profile. JEDEC id: 0xEF7018
Will perform mode 'all' on 176128 bytes starting at address 0x00000000 ...
Erasing 169 KiB from flash @ 0x00000000 (may take a while...)
Finished erase in 1 seconds
Writing 169 KiB to flash @ 0x00000000 (may take a while...)
...10%
...20%
...30%
...40%
...50%
...60%
...70%
...80%
...90%
...100%
Finished write in 6 seconds
Reading 169 KiB from flash @ 0x00000000 (may take a while...)
...10%
...20%
...30%
...40%
...50%
...60%
...70%
...80%
...90%
...100%
Finished read in 10 seconds
Flash verify successful
... finished with Flash Controller (via JTAG)
```
