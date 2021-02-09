# artsembly-module
Arturo VM Bytecode assembler - as an Arturo module

## Example 

```red
do.import module 'artsembly

do [
    do assemble [
        ; print header
        push "This is a number game written in ArtSembly"
        call 'print
        push "Let's go!"
        call 'print

        ; get random number
        push 9
        push 1
        call 'random
        store 'rnd

        ; start the loop
        guessNumber:
            ; get user's guess
            push "Guess the number: "
            call 'input
            push :integer
            call 'to

            ; compare with the secret number
            load 'rnd
            cmpeq 

            ; if not found jump back
            jmpifnot guessNumber

        ; that was it!
        push "Yes! You got it right!"
        call 'print
    ]
]
```

**Output:**

```bash
This is a number game written in ArtSembly
Let's go!
Guess the number: 1
Guess the number: 2
Guess the number: 3
Guess the number: 4
Guess the number: 5
Yes! You got it right!
```
