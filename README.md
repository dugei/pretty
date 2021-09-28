原始代码是这个： https://github.com/davecgh/go-spew，我拿过来改一下，增加了颜色，分隔线，简化了类型，长度等输出

$ go get -u github.com/dugei/pretty/spew
```

## Quick Start

Add this import line to the file you're working in:

```Go
import "github.com/dugei/go-spew/spew"
```

To dump a variable with full newlines, indentation, type, and pointer
information use Dump, Fdump, or Sdump:

```Go
spew.Dump(myVar1, myVar2, ...) // 简化输出
spew.DetailDump(myVar1, myVar2, ...) //原始的详细信息输出，带有类型，长度等信息
spew.Fdump(someWriter, myVar1, myVar2, ...)
str := spew.Sdump(myVar1, myVar2, ...)
```
