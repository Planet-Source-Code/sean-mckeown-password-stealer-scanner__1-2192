<div align="center">

## Password Stealer Scanner


</div>

### Description

Now you can scan for Password Stealers, Deltrees, and Even Virii! With this simple, quick FEW lines of coding and a little know how you can build a file scanner. The example below scans for Deltree strings which damage data and destroy files on your computer. There are tons of them floating around on AOL so better build your own before you get Tree'd.
 
### More Info
 
This code returns the percent of strings (damaging deltree strings) found in a file, and if it is safe enough to use.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[sean mckeown](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/sean-mckeown.md)
**Level**          |Unknown
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0
**Category**       |[Files/ File Controls/ Input/ Output](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files-file-controls-input-output__1-3.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/sean-mckeown-password-stealer-scanner__1-2192/archive/master.zip)





### Source Code

```
Const buf_size = 4096		'we scan it in 4096 byte chunks
Dim filename As String
Dim buffer As String
Dim resultsMSG as string
Dim strScan1 as boolean
Dim strScan2 as boolean
Dim strScan3 as boolean
Dim strScan4 as boolean
Dim strScan5 as boolean
Dim corrupt as integer	       		'percent of strings found
corrupt = 0: filename = "C:\Windows\win.ini" 'i use win.ini as an example
  Open filename For Binary As 1		'the open file command
    Do While Not EOF(1)
    buffer = Space(buf_size)     'this buffer is the 4096
    Get 1, , buffer			'gets that size from file
    DoEvents
      If InStr(1, buffer, "kill") Then strScan1 = true	'you can replace these strings with anything
      If InStr(1, buffer, "kill c:\") Then strScan2 = true  ' even make yourself a neat little file finder
      If InStr(1, buffer, "deltree") Then strScan3 = true
      If InStr(1, buffer, "shell =") Then strScan4 = true
      If InStr(1, buffer, "hard drive") Then strScan5 = true
    Loop
  Close 1
if strScan1 = true then corrupt = corrupt + 20: resultsMSG =resultsMSG & "kill, "  'this is my useless garble
if strScan2 = true then corrupt = corrupt + 20: resultsMSG =resultsMSG & "kill c:\, " 'to tell the results of a
if strScan3 = true then corrupt = corrupt + 20: resultsMSG =resultsMSG & "deltree, "  'scan
if strScan4 = true then corrupt = corrupt + 20: resultsMSG =resultsMSG & "shell=, "
if strScan5 = true then corrupt = corrupt + 20: resultsMSG =resultsMSG & "hard drive, "
MsgBox "-file scanned for strings - " & Chr(10) & corrupt & "% of strings found." & chr(10) & resultsMSG
```

