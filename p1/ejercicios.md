## Ejercicio 1 
```py
def foo(A: list[int], B: list[int]) -> int:
    r: int = 0
    i: int = 0
    while i < len(A):
        r += A[i] * B[i]
        i += 1
    return r
```
La pre condición más débil que impide que se produzcan excepciones es $A \neq null \land B \neq null \land \text{len}(B) \geq \text{len}(A)$. 

## Ejercicio 2 
Con el test:
```py
class TestFoo(unittest.TestCase):
    def test1(self):
        rv = foo(1, 0)
        self.assertEqual(rv, 0)
```
Como $1 > 0$ cómo no se cumple el if se pasa al else. Por lo que el nuevo test tiene que cumplirse que $x \leq y$.
```py 
class TestFoo(unittest.TestCase):
    def test1(self):
        rv = foo(1, 0)
        self.assertEqual(rv, 0)
    def test2(self):
        rv = foo(0,1)
        self.assertEqual(rv, 0)
```

## Ejercicio 3 
El test que mata al mutante es el tercero. 
```py
class TestFoo(unittest.TestCase):
    def test1(self):
        rv = foo(1, 0)
        self.assertEqual(rv, 0)
    def test2(self):
        rv = foo(0,1)
        self.assertEqual(rv, 0)
    def test3(self): 
        rv = foo(5,3)
        self.assertEqual(rv, 3)
```

## Ejercicio 4 
Programa:
```py
def triangle(a: int, b: int, c: int) -> int:
    if a <= 0 or b <= 0 or c <= 0:
        return 4  # invalid
    if not (a + b > c and a + c > b and b + c > a):
        return 4  # invalid
    if a == b and b == c:
        return 1  # equilateral
    if a == b or b == c or a == c:
        return 2  # isosceles
    return 3  # scalene
```
Mutante: 
```py
def triangle(a: int, b: int, c: int) -> int:
    if a > 0 or b <= 0 or c <= 0:
        return 4  # invalid
    if not (a + b > c and a + c > b and b + c > a):
        return 4  # invalid
    if a == b and b == c:
        return 1  # equilateral
    if a == b or b == c or a == c:
        return 2  # isosceles
    return 3  # scalene
```
Test case capaz de matar al mutante: 
```py
class TestTriangle(unittest.TestCase):
    def test1(self):
        rv = triangle(1, 1, 1)
        self.assertEqual(rv, 1)
```

## Ejercicio 5
Original:
```py
def testme(n: int) -> int:
    r: int = 0
    if n >= 0:
        i: int = 0
        while i < n:
            if i % 2 == 1:
                r = r + i
            i = i + 1
    return r
```

Un mutante ROR no equivalente puede ser: 
```py
def testme(n: int) -> int:
    r: int = 0
    if n >= 0:
        i: int = 0
        while i > n:
            if i % 2 == 1:
                r = r + i
            i = i + 1
    return r
```

Un test que lo detecte puede ser: 
```py
class TestTestMe(unittest.TestCase):
    def test1(self):
        rv = testme(5)
        self.assertEqual(rv, 4)
```

Un mutante ROR equivalente tal que no existe test que lo detecte es: 

```py
def testme(n: int) -> int:
    r: int = 0
    if n >= 0:
        i: int = 0
        while i < n:
            if i % 2 != 0:
                r = r + i
            i = i + 1
    return r
```

## Ejercicio 6
Original:
```py
def testme(x: int, y: int) -> bool:
    result: bool = False
    z: int = 2 * y
    if z == x:
        if x > y + 10:
            result = True
    return result
```

Un mutante AOR no equivalente puede ser: 
```py
def testme(x: int, y: int) -> bool:
    result: bool = False
    z: int = 2 + y
    if z == x:
        if x > y + 10:
            result = True
    return result
```

Un test que lo detecta puede ser: 

```py
class TestTestMe(unittest.TestCase):
    def test1(self):
        rv = testme(22,11)
        self.assertEqual(rv, True)
```

Usando el operador de mutación AOR no hay mutantes equivalentes porque las unicas cosas que podemos cambiar son los operadores en: `z : int = 2∗y` y `if x > y+10` son la multiplicacion y la suma, y al trabajar con esas expresiones cambiar cualquiera de los dos operadores aritmeticos nos da a números distintos. 

## Ejercicio 7
Original:
```py
def testme(k: int, j: int) -> int:
    i: int = 0
    r: int = 0
    while i < 2:  # C1
        if k == j:  # C2
            r = r + 1
        i = i + 1
    return r
```

Un mutante ABS no equivalente puede ser: 

```py
def testme(k: int, j: int) -> int:
    i: int = 0
    r: int = 0
    while i < 2:  # C1
        if k == j:  # C2
            r = -abs(r) + 1
        i = i + 1
    return r
```

Un test que lo detecta puede ser: 
```py
class TestTestMe(unittest.TestCase):
    def test1(self):
        rv = testme(5,5)
        self.assertEqual(rv, 2)
```

Un mutante ABS equivalente tal que no exista ningún test que lo detecte puede ser: 
```py
def testme(k: int, j: int) -> int:
    i: int = 0
    r: int = 0
    while i < 2:  # C1
        if k == j:  # C2
            r = abs(r) + 1
        i = i + 1
    return r
```

## Ejercicio 8
Original:
```py
def testme(k: int, j: int) -> int:
    r: int = 1
    if k != 0 and k > 0:  # C1
        c: int = k % 3  # k modulo 3
        i: int = 0
        while i < c:  # C2
            r = r * j
            i = i + 1
    return r
```
Un mutante ROR no equivalente puede ser: 

```py
def testme(k: int, j: int) -> int:
    r: int = 1
    if k != 0 and k == 0:  # C1
        c: int = k % 3  # k modulo 3
        i: int = 0
        while i < c:  # C2
            r = r * j
            i = i + 1
    return r
```

Un test que lo detecta puede ser: 
```py
class TestTestMe(unittest.TestCase):
    def test1(self):
        rv = testme(1,2)
        self.assertEqual(rv, 2)
```

Un mutante equivalente tal que no exista test case que lo detecte puede ser: 

```py
def testme(k: int, j: int) -> int:
    r: int = 1
    if k != 0 and k >= 0:  # C1
        c: int = k % 3  # k modulo 3
        i: int = 0
        while i < c:  # C2
            r = r * j
            i = i + 1
    return r
```

## Ejercicio 9
Original:
```py
def testme(k: int, j: int) -> int:
    r: int = 1
    if k > 0 and k < 3:  # C1
        i: int = 0
        while i < k:  # C2
            r = r * j
            i = i + 1
    return r
```

Un mutante ABS no equivalente puede ser: 

```py
def testme(k: int, j: int) -> int:
    r: int = 1
    if k > 0 and k < 3:  # C1
        i: int = 0
        while i < k:  # C2
            r = 0 * j
            i = i + 1
    return r
```

Un test que lo detecta puede ser: 
```py
class TestTestMe(unittest.TestCase):
    def test1(self):
        rv = testme(1, 1)
        self.assertEqual(rv, 1)
```

Un mutante ABS equivalente tal que no exista ningún test que lo detecte puede ser: 
```py
def testme(k: int, j: int) -> int:
    r: int = 1
    if k > 0 and k < 3:  # C1
        i: int = 0
        while i < k:  # C2
            r = abs(r) * j
            i = i + 1
    return r
```