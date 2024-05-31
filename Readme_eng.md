tty_uart is a universal application of serial port under the linux system, 
and various common serial port functions have been encapsulated into API interface functions for developers to use 
Function: Serial port general parameter setting (baud rate/data bit/stop bit/check bit) 
Serial port hardware flow control Receive real-time data echoes Serial port to send files or receive serial port data to save to files
The serial port is basically read and written MODEM signal reading and setting 
Support to obtain serial port related counts (modem change times/serial port frame error/verification error/overflow error)
Support obtaining/setting serial port serial_struct Support synchronous waiting for the change of the MODEM input signal 
Usage: Use gcc to compile tty_test.c source files, 
for example, gcc tty_uart.c -o test, generate an executable file, and run the serial port with root privileges.
Run Command Options: -D --device tty device to use (serial port name for specified operation, default operation if not specified: /dev/ttyUSB0) -S --speed uart speed (set serial baud rate) -v --verbose Verbose (show rx buffer) (whether to display the received serial port data in real time) -f --hardflow open hardware flowcontrol 
The serial port setting of the source program is 8N1 by default, if you need to set it to other serial port formats, you can directly modify the code. 
After the serial port is successfully opened, enter the corresponding characters to perform the corresponding operations: 
s - Set RTS and DTR to work z - Invalid RTS and DTR set g - Obtain MODEM input pin status (CTS, DSR, RING, DCD) h - Synchronously wait for the MODEM signal to change (the corresponding operation will block the execution until the signal changes or the serial port exits abnormally) b - Send a break signal w - Send a string r—Read the data once f - Choose to send files through the serial port or receive serial data to save to a file 
Example: sudo./test -D /dev/ttyS1 -S 57600 -v (indicates that the /dev/ttyS1 serial port is operated at 57600 baud rate and the received data is displayed in real time) 
Concentrate: This application uses the IOCTL method to set the serial port baud rate, and the purpose is to support the setting of non-standard baud rate. 
However, individual systems or drivers may not support this baud rate setting method, if you have any questions, please send an email to:
