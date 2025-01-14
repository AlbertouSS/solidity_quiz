<div align="center">
  <img height="60" src="https://img.icons8.com/?size=100&id=HOqGCOyHDbd4&format=png&color=000000">
  <h1>Preguntas de Solidity</h1>
</div>

---

<p align="center">
Preguntas de entendimiento sobre Solidity desde básicas hasta avanzadas para complementar el Grupo de Estudio de EVM y Solidity creado por <code>garosan</code> y <code>albertou</code> :heart:</p>

<h3 align="center">Únete a nosotros</h3>

<p align="center">
  <a href="https://t.me/+_fPZloVp8b8yOGIx">Telegram del Grupo de Estudio</a> || <a href="#">Website (Próximamente)</a>
</p>
<p align="center">
  <a href="https://x.com/garosan1">X Garosan</a> || <a href="https://x.com/albertou_eth">X albertou</a>
</p>

Reconocimientos:

- [Este](https://github.com/nclskfm/javascript-quiz) es el repo original creado por [nclskfm](https://github.com/nclskfm)
- Iconos cortesía de [icons8.com](https://icons8.com/)

---

###### 1. ¿Cómo se llama el entorno de desarrollo fácil de usar, accesible desde cualquier navegador que utilizaremos para dar nuestros primeros pasos en Solidity?

- A: VS Code
- B: Hardhat
- C: Remix
- D: Foundry

<details><summary><b>Answer</b></summary>
<p>

#### Answer: C

Remix será el entorno de desarrollo que utilizaremos. Recuerda asegurarte siempre que tu navegador esté en esta dirección: `remix.ethereum.org`

</p>
</details>

---

###### 2. Solidity es un lenguaje...

- A: Dinámicamente tipado
- B: Estáticamente tipado
- C: Sin tipado
- D: Requiere librerías adicionales para agregar tipos

<details><summary><b>Answer</b></summary>
<p>

#### Answer: B

Solidity es un lenguaje de programación estáticamente tipado, lo que significa que los tipos de datos de las variables deben declararse explícitamente y se verifican en tiempo de compilación. Gracias a esto, Solidity puede detectar errores de tipo en tiempo de compilación, lo que ayuda a mejorar la seguridad y la eficiencia de los contratos inteligentes.

</p>
</details>

---

###### 3. ¿Cuáles son los 3 tipos de datos más comunes que vimos en la sesión 1?

- A: `uint256`, `bool` y `address`
- B: `bool`, `array` y `string`
- C: `tuple`, `function` y `bool`
- D: `address`, `array` y `struct`

<details><summary><b>Answer</b></summary>
<p>

#### Answer: A

Los tres tipos más comunes que ya vimos en Solidity son:

- El bool que puede ser true o false.
- El uint256 que representa un número entero positivo.
- El address que representa la dirección de una wallet o un smart contract.

</p>
</details>

---

###### 4. ¿Qué representa este código?

```solidity
function getABoolean() public pure returns (bool) {
  bool y = true;
  return y;
}
```

- A: Es una función que acepta un boolean y lo devuelve.
- B: Es una función que acepta un boolean como parámetro y no devuelve nada.
- C: Es una función que no acepta parámetros y devuelve un boolean.

<details><summary><b>Answer</b></summary>
<p>

#### Answer: C

Podemos por los paréntesis vacíos al lado del nombre de la función que ésta no acepta ningún parámetro.
Luego, al lado de la palabra clave returns entre paréntesis, encontramos el tipo de dato que devuelve esta función (bool).

</p>
</details>

---

###### 5. ¿Cuantos caracteres tiene normalmente una wallet, sin contar el 0x del principio?

- A: 256
- B: 32
- C: 64
- D: 40

<details><summary><b>Answer</b></summary>
<p>

#### Answer: D

40 es la respuesta correcta! Si te sientes con ganas de contar y verificar, esta es una wallet de Vitalik Buterin: `0xd8da6bf26964af9d7eed9e03e53415d37aa96045`. Puedes checar el balance y las últimas transacciones de Vitalik [aquí](https://etherscan.io/address/0xd8da6bf26964af9d7eed9e03e53415d37aa96045) si te sientes con más curiosidad.

</p>
</details>

---

###### 6. Esta función restará 2 números que se le pasen como parámetros, que pasará si pasamos a con un valor de `2` y b con un valor de `10`?

```solidity
function restar(uint256 a, uint256 b) public pure returns (uint256) {
    return a - b;
}
```

- A: El resultado será `-8`.
- B: La transacción se revertirá.
- C: La transacción entrará en un loop infinito y se quedará sin gas.
- D: El entero se _grapará_ sobre lo máximo que puede guardar. Es decir, el resultado será 2^256-1 (lo máximo que puede guardar un `uint256` menos `8` unidades).

<details><summary><b>Answer</b></summary>
<p>

#### Answer: B

En este caso y pasando esos parámetros a esta función, ésta simplemente se revertirá. Inténtalo en Remix!

</p>
</details>

---

###### 7. ¿Cuál sería el código correcto para calcular el 12.5% de 400?

``

- A: `uint256 interest = 400 * 12 / 100;`
- B: `uint256 interest = 200 * 75 / 1000;`
- C: `uint256 interest = 400 * 625 / 5000;`
- D: `uint256 interest = 400 * 125 / 1000;`

<details><summary><b>Answer</b></summary>
<p>

#### Answer: D

Recuerda que en Solidity no tenemos flotantes, es decir no podemos simplemente multiplicar `400 * .125` así que tenemos qué recurirr a este pequeño truco de multiplicar 400 por 125 y dividir por 1000.

</p>
</details>

---

###### 8. Si estamos trabajando con Solidity 0.8.0 o mayor, ¿cómo podemos hacer `underflow` de nuestro tipo de dato? Es decir, si tenemos una variable `uint8` (cuyo valor máximo es 256) y queremos que al restar `2 - 10` nos de `248` ¿qué tenemos qué hacer?

``

- A: Grapar nuestro código en un bloque `unchecked`.
- B: Usar un bloque `validArithmetic` adentro de la función donde pongamos éste código.
- C: Usar la librería `underflow` de OpenZeppelin.
- D: No necesitamos hacer nada especial a partir de Solidity 0.8.0.

<details><summary><b>Answer</b></summary>
<p>

#### Answer: A

Antes de Solidity 0.8.0 podíamos hacer `underflow` y `overflow` de nuestros enteros sin problema pero esto creó muchos bugs y problemas de seguridad. A partir de Solidity 0.8.0, tienes qué grapar tu código en un bloque `unchecked` si quieres hacer `underflow` u `overflow` pero esto es un feature muy avanzado y sólo deberías usarlo si sabes exactamente las consecuencias de ello.

</p>
</details>

---

###### 9. En Solidity, ¿cómo iteramos exactamente 10 veces en un for loop para agregar valores de 0 a 9 a una variable `suma`?

```solidity
// Opción A
function sumar() public pure returns (uint256) {
    uint256 suma = 0;
    for (uint256 i = 1; i <= 10; i++) {
        suma += i;
    }
    return suma;
}

// Opción B
function sumar() public pure returns (uint256) {
    uint256 suma = 0;
    for (uint256 i = 0; i <= 9; i++) {
        suma += i;
    }
    return suma;
}

// Opción C
function sumar() public pure returns (uint256) {
    uint256 suma = 0;
    for (uint256 i = 0; i < 10; i++) {
        suma += i;
    }
    return suma;
}

// Opción D
function sumar() public pure returns (uint256) {
    uint256 suma = 0;
    for (uint256 i = 1; i < 10; i++) {
        suma += i;
    }
    return suma;
```

- A: Opción A
- B: Opción B
- C: Opción C
- D: Opción D

<details><summary><b>Answer</b></summary>
<p>

#### Answer: C

La opción correcta es la C. Analicémosla: Tenemos una función donde primero declaramos nuestra variable contador `suma`, luego creamos un `for loop` con sus 3 elementos: `inicialización`, `condición` y `actualización`. Entonces decimos que nuestra variable `i` vale 0 y en cada vuelta valdrá 1 más hasta antes de llegar a 10, y en cada vuelta, agregaremos el valor de `i` a `suma`, y de esa manera agregaremos los números del 0 al 9. Trata de ver si encuentras porqué los otros códigos tienen errores o no hacen exactamente esto.

</p>
</details>

---

###### 10. Este código es válido en Solidity?

```solidity
function isNotZero(uint256 x)
    public
    pure
    returns (bool) {
        if (x) {
            return true;
        } else {
            return false;
        }
}
```

- A: No.
- B: Sí.
- C: Sí pero solo en la última versión del compilador de Solidity (^0.8.0)

<details><summary><b>Answer</b></summary>
<p>

#### Answer: A

Al contrario de otros lenguajes que convierten cualquier uint a una expresión verdadera o falsa, en Solidity no puedes hacer esto nunca. Si vas a poner una expresión dentro de un bloque `if`, esta expresión tiene qué ser de tipo `bool`; no puedes poner un string, uint u otro tipo de dato similar.

</p>
</details>

---
