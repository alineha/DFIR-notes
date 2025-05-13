uses ✨plugins✨
{plugin}list -> cursory view
{plugin}scan -> indepth view
### BASICS

> [!Code] **imageinfo ->** best guess for memory profile to parse the memory; looks for a kdbg (kernel debugger block), analysis of it tells you which OS it originated from
```volatility -f memdump.mem imageinfo```
> 
![[Pasted image 20250511164844.png]]

> [!Code] **imagecopy ->** copies an existing .mem or .dmp file to disk (so you can run volatily against it again)

> [!Code] **timeliner ->** creates a timeline of things that happened on disk/memory

> [!Code] **pslist ->** allows the device to locate an eprocess datablock, i.e. lists the RUNNING processes and EXITED processes
```volatility -f memdump.mem --profile=Win10x64_14393 pslist```
> 
![[Pasted image 20250511165424.png]]

> [!Code] **psscan ->** more indepth version of pslist, may find more processes
> ```volatility -f memdump.mem --profile=Win10x64_14393 psscan```

> [!Code] **pstree ->** shows a hierarchy of parent and child processes
> ```volatility -f memdump.mem --profile=Win10x64_14393 pstree```
> 
> ![[Pasted image 20250511170517.png]]
> PPid is the parent ID

> [!Code] **cmdscan ->** gathers and prints commands typed on the cmd
> ```volatility -f memdump.mem --profile=Win10x64_14393 cmdscan```

> [!Code] **consoles ->** gathers and prints commands typed on the cmd AND output
> ```volatility -f memdump.mem --profile=Win10x64_14393 consoles```

> [!Code] **procdump ->** dumps the executable of the process
> ```volatility -f memdump.mem --profile=Win10x64_14393 procdump -p 3960 --dump-dir=./```
> 
> ![[Pasted image 20250511170945.png]]
> 
> ```file executable.3960.exe``` gives us information on the file generated

> [!Code] **memdump ->** dumps the memory of the process
> ```volatility -f memdump.mem --profile=Win10x64_14393 memdump -p 3960 --dump-dir=./```
> 
> ![[Pasted image 20250511171430.png]]

> [!Code] **dumpfiles ->** dumps all cached files
> ```volatility -f memdump.mem --profile=Win10x64_14393 dumpfiles --dump-dir=./```

> [!Code] **modscan ->** shows kernel modules/drivers
> ```volatility -f memdump.mem --profile=Win10x64_14393 dumpfiles --dump-dir=./```
> 
> unloaded drivers can be a sign of EVIL

> [!Code] **netscan ->** shows connections
> ```volatility -f memdump.mem --profile=Win10x64_14393 netscan```
> 
> ![[Pasted image 20250511175159.png]]