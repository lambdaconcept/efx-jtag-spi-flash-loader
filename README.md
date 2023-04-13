# efx-jtag-spi-flash-loader
Efinix JTAG SPI Flash loader proxy bitstream

### Build proxy bitstream
Open the project in efinity and build.

### Load the proxy bitstream
Assuming your are using a FT4232 with JTAG on bus A.
```
source /opt/efinity/2022.2/bin/setup.sh

/opt/efinity/2022.2/bin/python3 /opt/efinity/2022.2/pgm/bin/efx_pgm/ftdi_program.py -m jtag -a "ftdi://0x0403:0x6011/1" outflow/efx_jtag_spi_flash_loader.hex
```

### Flash your application bitstream
```
/opt/efinity/2022.2/bin/python3 /opt/efinity/2022.2/pgm/bin/efx_pgm/ftdi_program.py -m jtag_bridge -a "ftdi://0x0403:0x6011/1" path_to_my_bitstream.hex
```
