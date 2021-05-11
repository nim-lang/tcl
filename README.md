# Nim Wrapper for the TCL programming language

## Installation

```
nimble install tcl
```

## Quick Example

```nim
import std/[strformat]
import tcl

let
  interp = CreateInterp()
if interp == nil:
  quit "Cannot create Tcl interpreter"

if interp.Init() != TCL_OK:
  quit "Cannot init the Tcl interpreter"

const
  tclCmds = ["""puts "Tcl version: $tcl_version"""",
             """puts "Hello, World"
                puts "Bye, World""""]

for cmd in tclCmds:
  if interp.Eval(cmd) != TCL_OK:
    quit &"Cannot execute '{cmd}'"
```
