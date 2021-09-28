原始代码是这个： https://github.com/davecgh/go-spew 我拿过来改一下，增加了颜色，分隔线，简化了类型，长度等输出

$ go get -u github.com/dugei/pretty/spew

```Go
import "github.com/dugei/go-spew/spew"
```

```Go
spew.Dump(myVar1, myVar2, ...) // 简化输出
spew.DetailDump(myVar1, myVar2, ...) //原始的详细信息输出，带有类型，长度等信息
spew.Fdump(someWriter, myVar1, myVar2, ...)
str := spew.Sdump(myVar1, myVar2, ...)
```

简化输出，map,struct的key加了颜色，var1,var2之间加了分隔线，每一次打印上下加了时间线,查看示例图片： https://github.com/dugei/pretty/blob/main/dump.jpg
```
++++++++++++++++++++++++++++++++++++++++ 2021-09-28 20:02:41 ++++++++++++++++++++++++++++++++++++++++

{
    "str": "foo",
    "num": 100,
    "bool": false,
    "array": {
        "foo",
        "bar",
        "baz"
    },
    "map": {
        "foo": "bar"
    },
    "info": {
        name: "张三",
        Age: 30,
        Addr: {
            street: "长安街",
            no: "18"
        }
    },
    "null": <nil>
}

----------------------------------------------------------------------------------------------------

{
    street: "长安街",
    no: "18"
}

++++++++++++++++++++++++++++++++++++++++ 2021-09-28 20:02:41 ++++++++++++++++++++++++++++++++++++++++
```
原始的详细输出，有类型，长度等信息，无颜色，无分隔线
```
(map[string]interface {}) (len=7)) {
    (string) (len=4)) "info": (main.Student) {
        name: (string) (len=6)) "张三",
        Age: (int) 30,
        Addr: (main.address) {
            street: (string) (len=9)) "长安街",
            no: (string) (len=2)) "18"
        }
    },
    (string) (len=4)) "null": (interface {}) <nil>,
    (string) (len=3)) "str": (string) (len=3)) "foo",
    (string) (len=3)) "num": (int) 100,
    (string) (len=4)) "bool": (bool) false,
    (string) (len=5)) "array": ([]string) (len=3 cap=3) {
        (string) (len=3)) "foo",
        (string) (len=3)) "bar",
        (string) (len=3)) "baz"
    },
    (string) (len=3)) "map": (map[string]interface {}) (len=1)) {
        (string) (len=3)) "foo": (string) (len=3)) "bar"
    }
}
(main.address) {
    street: (string) (len=9)) "长安街",
    no: (string) (len=2)) "18"
}
```
