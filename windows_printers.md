```python
#
# Simple example to give me the list of printers that are available to the Windows User.
# Helpful to be able to create a copy of the print menu options so that in other examples
# I can have the user pick the printer that they want a file printed to.
#
# Uses the module win32print, see the documentation at the following link:
# http://timgolden.me.uk/pywin32-docs/win32print.html
#

import win32print

printers = win32print.EnumPrinters(2) 
# The number can be 1,2,4 or 5 based on the level of type of printer info structure.
# Please see the documentation to understand more.

printer_list = []
for x in range(len(printers)):
    printer_list.append(printers[x][2])
    
print(printer_list)                   
# This list should give you the names of the printers available to you as they would look
# in your print menu.
                                      
```
