# artsembly-module
Arturo VM Bytecode assembler - as an Arturo module

## Example 

```red
do.import module 'artsembly

do [
    do assemble {
        push "What is your name? "
        call 'input
        store 'name
        push "!"
        load 'name
        call 'append
        push "Hello "
        call 'append
        call 'print
        push "Now, let's play a bit with some numbers..."
        call 'print
        push 2
        push 1
        iadd
        call 'print
        push 2
        push 1
        isub
        call 'print
    }
]
```

**Output:**

```bash
What is your name? John
Hello John!
Now, let's play a bit with some numbers...
3
-1
```
