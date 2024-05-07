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

### Example 

```red
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
        push 10
        call 'equal?       ; x = 10

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
5
6
7
8
9
finished!
```

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