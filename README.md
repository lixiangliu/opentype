## An OpenType font parser in JavaScript

This is a pure JavaScript parser for OpenType font files. It supports fonts with CFF and TrueType outlines, and can read fonts wrapped as WOFF.

The following OpenType tables are currently supported:

* CMAP (only format 0, 4, 12, and 13)
* head
* hhea
* maxp
* hmtx
* name
* OS/2
* post
* GSUB (excluding LookupType 5, 6, 7, and 8)
* GDEF (only the Glyph Class Definitions)
* gasp

This roughly corresponds to all the metadata available in most fonts.

## Usage

This fork is already compiled with Grunt. Please check the `build` folder for the compiled `opentype.js` file. 

Then include `build/opentype.js` into your page and pass the `opentype.parse` method an `ArrayBuffer` instance:

    var buffer = new ArrayBuffer(...);

    var font = opentype.parse(buffer);

The `font` variable will now contain a JSON representation of all supported OpenType tables. Later versions of this library will support parsing only select OpenType tables.

You can also use `glyphArray` and `glyphData` to quickly understand which glyphs are supported in the parsed font. `glyphArray` returns a array and `glyphData` returns an object. 

## Browser Support

This library extensively uses `ArrayBuffer`'s, and `DataView`'s so you will need a browser that supports those. Any recent version of Safari or Firefox will do. Tested on Safari 9.

## Copyright and License

This library is licensed under the three-clause BSD license.

Original source code of opentype.js can be found from [here](https://github.com/bramstein/opentype "Bram Stein’s original source code"). 

Copyright (c) 2013 - 2015, Bram Stein, Lixiang Chris Liu
All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

- Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

- Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

- Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.