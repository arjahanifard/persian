# Lubeck

کتابخانه جبر خطی سطح بالا بر اساس الگوریتم CBLAS، LAPACK و Mir.

## Dependencies
Lubeck به CBLAS و LAPACK API نیاز دارد. ممکن است لازم باشد آنها را نصب کرده و «dub.sdl» را به روز کنید
CBLAS و LAPACK از قبل روی MacOS نصب شده اند.
[OpenBLAS](http://www.openblas.net) یا [Intel MKL](https://software.intel.com/en-us/mkl)
backends پیشنهاد میشه برای ویندوز و لینوکس.

## Links

 - [GitHub](https://github.com/kaleidicassociates/lubeck)
 - [Mir Algorithm API](http://mir-algorithm.libmir.org)
 - [Mir Random API](http://mir-random.libmir.org)
 - [Mir API](http://mir.libmir.org)

## {SourceCode:incomplete}

```d
/+dub.sdl:
dependency "lubeck" version="~>1.1"
+/
import kaleidic.lubeck: mtimes;
import mir.algorithm.iteration: each;
import mir.ndslice: magic, repeat, as,
    slice, byDim;
import std.stdio: writeln;

void main()
{
    auto n = 5;
    // Magic Square
    auto matrix = n.magic.as!double.slice;
    // [1 1 1 1 1]
    auto vec = 1.repeat(n).as!double.slice;
    // Uses CBLAS for multiplication
    matrix.mtimes(vec).writeln;
    "-----".writeln;
    matrix.mtimes(matrix).byDim!0.each!writeln;
}
```
