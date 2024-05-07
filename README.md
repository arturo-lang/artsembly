<h1 align="center">
    ArtSembly
</h1>

<p align="center">
     <i>Arturo VM Bytecode assembler for Arturo</i> 
     <br><br>
     <img src="https://img.shields.io/github/license/arturo-lang/grafito?style=for-the-badge">
    <img src="https://img.shields.io/badge/language-Arturo-orange.svg?style=for-the-badge">
</p>

--- 

### What does this package do?

This package features a bytecode "assembler" for the Arturo programming language. In a few words, it allows to write bytecode for the Arturo VM directly, only in a friendly, Assembly-style fashion.

> [!WARNING]
> This package is to be considered mostly an - adventurous - experiment, highlighting what is possible and is not meant to be neither a replacement of Arturo nor a 100% functional bytecode assembler that aims to cover everything!

### How do I use it?

All you have to do is `import` it and then pass a block (or text) of valid ArtSembly code. The returned value is always a Bytecode object, which means that you can either run it directly (via [`do`](https://arturo-lang.io/documentation/library/core/do/)) or manipulate it further, if you wish.

#### Example 

```arturo
import "artsembly"!

do assemble {
    push 0                 ; x: 0
    store 'x

    theLoop:
        load 'x            ; print x
        call 'print

        load 'x
        push 1
        call 'add
        store 'x           ; x: 1 + x

        load 'x
        push 5
        call 'equal?       ; x = 5

        jmpIf 'finished    ; if x = 10 -> go to finished

        goto 'theLoop      ; else -> go back up

    finished:
        push "finished!"
        call 'print        ; print "finished!"
}
```

**Output:**

```bash
0
1
2
3
4
finished!
```

### Available commands

| Name | Arguments | Description |
|---|---|---|
| `push` | :any | push a value onto the stack |
| `store` | :literal, :string | store topmost stack item to given symbol |
| `load` | :literal, :string | push given symbol value to stack |
| `call` | :literal, :string | call given function by name |
| `goto` | :literal, :string | go to given label |
| `jmpIf` | :literal, :string | jump forward to given label if topmost stack value is true |
| `jmpIfNot` | :literal, :string | jump forward to given label if topmost stack value is not true |

> [!TIP]
> As highlighted in the example above, all commands listed here are to be used solely *within* an `assemble` call.

<hr/>

### License

MIT License

Copyright (c) 2024 Yanis Zafirópulos

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
