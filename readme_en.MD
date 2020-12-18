prog_cpld : very simple USB CPLD programmer  
Copyright (C) 2009  Koichi Nishida  

This program is free software; you can redistribute it and/or  
modify it under the terms of the GNU General Public License  
as published by the Free Software Foundation; either version 2  
of the License, or (at your option) any later version.  

This program is distributed in the hope that it will be useful,  
but WITHOUT ANY WARRANTY; without even the implied warranty of  
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the  
GNU General Public License for more details.  
  
You should have received a copy of the GNU General Public License  
along with this program; if not, write to the Free Software  
Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.  
  
----------  
  
This is a software to write configuration data to Xilinx CPLD with USB.  
FTDI's USB controller FT232R / FT245R is assumed.  
  
How To USE  
  
<Hardware>  

Make a download cable with FT232R / FT245R chip in normal manner.

  configuration:
    D0/TXD -> TDI
    D1/RXD -> TMS
    D2/RTS# -> TCK
    D3/CTS# -> TDO
 
Don't forget to wire VCCIO according to the supply voltage for the device.

<Software>

1 Download D2XX direct driver from FTDI's home page (www.ftdichip.com) and install it.

2 Run PROG_CPLD with an argument which specifies SVF file in command prompt.

> prog_cpld test.svf

3 If you want to watch the progress, specify -v option.

> prog_cpld -v test.svf

4 If you want to compare TDO values to the expected values, specify -c option.

>prog_cpld -c test.svf

If you succeed the programming, the following message is printed.

 <<< All TDO outputs matched to the expected values! >>>
 
<Notice>

1 Device chain is not supported..
2 State transition is not complete.
3 Tested with just one example on XC9572XL. 
    Created for very limited specification of SVF.
