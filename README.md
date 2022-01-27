# arduino_hssp
Cypress PSoC® 1 Device hacking using an Arduino

This is a fork of trou's fork of miracoli's port of the code found at
<http://www.cypress.com/?rID=2906> (AN44168, Revision 2.30) to the Arduino
platform by Dirk Petrautzki.

It also includes the python interfacing code, originally from 
[cypress_psoc_tools](https://github.com/trou/cypress_psoc_tools).

It adds support for multiple banks when reading memory, and (very very
partially) adds Python3 support.

Thanks my test subject not enabling protection bits, a normal flash dump
works fine.
## Usage

Clone the code into a folder called 'arduino_hssp', run `make && make_upload` or
just use the Arduino IDE.

Connect your PSoC 1 device as follows
(can be changed in issp_defs.h):

* `SDATA_PIN` -> 9
* `SCLK_PIN` -> 8
* `XRES_PIN` -> 4
* `TARGET_VDD` -> 11

Install requirements (`pip install tqdm pyserial`).  
Run the code and check serial output. The flash will be saved to `flash.bin`.

I didn't have much luck with automatic power toggling - if you get failure to
init, try power cycling the arduino and your target board, then quickly (within
~15 seconds) perform the dump.

If the protection debugging shows banks as being protected, the resulting dump
will be invalid. You should try using the original project's CRC attack.

## Project status
Tested and working with Arduino Leonardo and CY8C22345.

## Previous writeup
<https://syscall.eu/blog/2018/03/12/aigo_part2/>
