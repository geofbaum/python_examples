```python
# This is an example to print a file.
# Uses the win32api and win32print modules.
# 
# Please see the examples from Tim Golden and the documentation
# that he has regarding them.
#
# I'd also recommend this link to see some examples of other 
# printer related things you could do with the data available 
# from win32print. It might be old but it still helpful.
# https://www.blog.pythonlibrary.org/2010/02/14/python-windows-and-printers/
#

import win32api
import win32print

file = 'test_text_file.txt'

# Gives me information on the printers available to me
printers = win32print.EnumPrinters(2)

# This gives you the systems default printer
printer_name = win32print.GetDefaultPrinter()

printer_list = []
for x in range(len(printers)):
    printer_list.append(printers[x][2])

# printer_list should look something like the example below
# ['Send To OneNote 2016', 'Microsoft XPS Document Writer', 
#  'Microsoft Print to PDF', 'Fax', 'Brother DCP-7065DN', 'Canon MAXIFY iB4120']
# 
# Let's say I want to print my text file to pdf just for fun.
#

my_printer = printer_list[2]

# This will print to the Microsoft Print to PDF printer option
win32api.ShellExecute (0, "print", file, my_printer, ".", 0)
# This would print it to my default printer due to the None arg
# win32api.ShellExecute (0, "print", file, None, ".", 0) 
```
