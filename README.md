# FT245-RC2014
An add-on board for the RC2014 bus using the FT245 as an ACIA/UART replacement

The FT245 is a USB-FIFO IC. That is, it appears to be a COM port at the PC, but it has a bidirectional tristate data bus, read and write enables, and a couple of status lines. With minimal logic it can be interfaced to an 8 bit micro to provide power and a serial connection that requires no configuration at either end. Fed up of trying to work out what serial port settings to use? This doesn't care. Use any baud rate you like, the chip will still transfer at 12Mbps. Sick of trying to get weird UARTs to work in assembly language? Fear not, simply check the status "register" at BASE+0x00, and then write to, or read from BASE+0x01. It doesn't get easier!

This version is compatible with the RC2014 standard (and enhanced) bus, and appears as a MC6850. Sort of. SCM and BASIC do not use interrupts, so seem to work fine. CP/M needs an interrupt on receive, but the FT245 doesn't provide an interrupt, so the logic fakes one. It's enough to get CP/M up and running, but because there is no flow control logic, transmit delays may still be needed for some applications. With a 1ms character delay, using download to transfer packages was still faster than the SIO provided as part of the RC2014 Pro kit.

This is provided as-is, use at your own risk, I do not accept any responsibility for damages however caused.
