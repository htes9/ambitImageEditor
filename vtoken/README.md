# VToken
Some files have a footer of 20 bytes.
This tools allows you to remove or merge this footer for creating custom firmware.  

# TODO  
This tool is WIP  

### Info
Show vtoken info    
`./vtoken.py info -i file.original`  

### Remove  
Create a new file without vtoken  
`./vtoken.py remove -i file.original -o file.clean`  

### Merge
Create a new file (file.new) with vtoken  
using vtoken of original file (file.original) and data of custom file (file.new.clean)  
`./vtoken.py merge -i file.original -c file.new.clean -o file.new`  

## VToken structure  
| Size (byte)  | Type | Name | Description |
| :----------: | ---- | ---- | ------- |
| 4 | Unsigned LE Int 32 | File CRC | JamCRC |
| 4 | Unsigned LE Int 32 | Magic    | 0x32570000 |
| 4 | Unsigned BE Int 32 | Chip     | Eg: 6328 |
| 4 | Unsigned LE Int 32 | Flash Type | See Flash Type list below |
| 4 | Unsigned LE Int 32 | Unused | It's always 0 |

### Flash types  
|     ID     | Type |  
| :--------: | ---- |  
| 0x01000000 | NOR | 
| 0x02000000 | NAND  16 | 
| 0x03000000 | NAND 128 | 