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
        push "Let's go!\n"
        call 'print

        ; get random number
        push 9
        push 1
        call 'random
        store 'rnd

        push 0
        store 'attempt

        ; start the loop
        guessNumber:
            ; check if it's the first attempt
            push 0
            load 'attempt

            ; if it is, jump right to main
            cmpeq
            jmpif main

            ; else, print error message
            push "Not correct :( Try again!\n"
            call 'print

            main:
                ; increment attempt
                push 'attempt
                push 1
                iadd
                store 'attempt

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
        push "\n*** Yes! You got it right!\n"
        call 'print
    ]
]
```

**Output:**

```bash
This is a number game written in ArtSembly
Let's go!

Guess the number: 1
Not correct :( Try again!

Guess the number: 3
Not correct :( Try again!

Guess the number: 6
Not correct :( Try again!

Guess the number: 2

*** Yes! You got it right!
```
