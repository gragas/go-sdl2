SDL2 binding for Go [![Build Status](https://travis-ci.org/veandco/go-sdl2.svg?branch=master)](https://travis-ci.org/veandco/go-sdl2)
===================
This is my specially-tailored fork of [veandco's SDL2 binding for Go](https://github.com/veandco/go-sdl2).

Differences?
============
I fixed some `#include`s so the bindings would actually install on my machine.

Installation
============
`go get -v github.com/gragas/go-sdl2/sdl{,_mixer,_image,_ttf}`

Example
=======
```go
package main

import "github.com/gragas/go-sdl2/sdl"

func main() {
	sdl.Init(sdl.INIT_EVERYTHING)

	window, err := sdl.CreateWindow("test", sdl.WINDOWPOS_UNDEFINED, sdl.WINDOWPOS_UNDEFINED,
		800, 600, sdl.WINDOW_SHOWN)
	if err != nil {
		panic(err)
	}
	defer window.Destroy()

	surface, err := window.GetSurface()
	if err != nil {
		panic(err)
	}

	rect := sdl.Rect{0, 0, 200, 200}
	surface.FillRect(&rect, 0xffff0000)
	window.UpdateSurface()

	sdl.Delay(1000)
	sdl.Quit()
}
```

License
=======
Go-SDL2 is BSD 3-clause licensed.
