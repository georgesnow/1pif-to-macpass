# 1PIF to MacPass

A fork of Mike Green's original 1pif-to-keepass, a Node module that converts a 1Password `*.1pif` archive to an XML file importable by MacPass (compatible with 0.7.3)

## Installation

```bash
git clone https://github.com/simonguest/1pif-to-macpass.git
cd 1pif-to-macpass
npm install
```

## Usage

You can convert files by running `bin/1p2mp.js` script.

```
1PIF to MacPass Converter

Usage: 1p2mp INPUT [-o OUTPUT]

Options:
  -o, --output   Output file ('-' for stdout)  [default: "-"]
  -h, --help     Show help  [boolean]
  -v, --version  Display version information  [boolean]

Examples:
  1p2mp input.1pif -o output.xml
  1p2mp input.1pif -o - # STDOUT

Forked from original 1pif-to-keepass, (C) 2015, Mike Green
```

The original KeyPass code can still also be used as a library, if required:

```js
var OPC = require('1pif-to-keepass');

// If you don't specify an output option, it will default to STDOUT.
var converter = new OPC('data.1pif', { output: 'file.xml' });

// OPC is an EventEmitter, so it will notify you about various stages of the conversion
// process:

converter.on('data', function(data) {
  console.log('Parsed entry: %O', data);
});

converter.on('end', function() {
  console.log('Conversion is all finished!');
});

converter.start();
```


