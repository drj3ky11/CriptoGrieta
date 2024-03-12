# Bitcoin

## Introducción

Bitcoin es una forma de dinero digital descentralizado, que permite a los usuarios realizar transacciones de persona a persona (peer-to-peer) sin necesidad de intermediarios como bancos o gobiernos. Es la primera y más conocida criptomoneda, creada en 2009 por una persona o grupo de personas bajo el seudónimo de Satoshi Nakamoto.

Aspectos Clave de Bitcoin:

**Descentralización**: A diferencia de las monedas tradicionales, Bitcoin no está controlado por ninguna autoridad central, como un banco central o un gobierno. En cambio, funciona en una red descentralizada de computadoras llamadas nodos, que validan y registran las transacciones en una cadena de bloques pública y transparente.

**Tecnología Blockchain**: La cadena de bloques (blockchain) es el sistema subyacente que permite que Bitcoin funcione. Es un libro de contabilidad digital público y descentralizado que registra todas las transacciones de Bitcoin de manera cronológica y segura. Cada bloque en la cadena está vinculado al anterior mediante criptografía, lo que garantiza la integridad y la inmutabilidad de los datos.

**Criptografía**: Bitcoin utiliza principios de criptografía para garantizar la seguridad y la privacidad de las transacciones. Las direcciones de Bitcoin, que se utilizan para enviar y recibir fondos, son cadenas de caracteres alfanuméricos generadas de forma aleatoria. Además, las transacciones se firman digitalmente para verificar la identidad del remitente y garantizar que no se puedan modificar una vez registradas en la cadena de bloques.

![bitcoinnetwork](/images/dos.png)

## Fundamentos

### ¿Que es Bitcoin?

La forma más simple de explicarlo es decir que es un programa de ordenador, que te puedes descargar [aquí](https://bitcoin.org/en/download)

Si te descargases el programa y lo ejecutases, lo que pasaría es que tu ordenador se conectaría con otros ordenadores que ejecutan el mismo programa, y compartirían un fichero con una lista enorme de transacciones, esto es la blockchain.

![Red de bitcoin](/images/1_2_network.png)
*[Fuente Imagen](https://learnmeabitcoin.com/)*

Básicamente, cuando una transacción se inserta en la red, se difunde entre todos los ordenadores de la red hasta que uno de ellos (nodo) la inserta en la blockchain y comparte la actualización con el resto. Esta inserción en en la blockchain se denomina **minar**. 

Llegados a este punto, te habrás dado cuenta, de que bitcoin proporciona un modelo de pago descentralizado. No hay una entidad central que gobierne la red, es un consenso de red. Y esto evita uno de los problemas mayores a los que se podría enfrentar la red, a un doble gasto. Esto sería incluir una transacción falsa, pero en resumen, el consenso hace que *mentir* de esa forma salga tan caro y sea tan costoso que la red no lo permite. Puedes leer más sobre esto [aquí](https://river.com/learn/how-bitcoin-solves-the-double-spend-problem/)


El minado, no deja de ser una operación aritmética bastante similar al cálculo de un [hash](https://learnmeabitcoin.com/technical/cryptography/hash-function/) y mediante el minado se consiguen recompensas, en bitcoin. Este es el incentivo que tiene la red para minar, es decir, para mantener todo en marcha. Hemos simplificado mucho esta parte, en verdad hay por medio una técnica denominada "[Proof of work](https://academy.bit2me.com/que-es-proof-of-work-pow/)" que viene a resolver uno de los mayores problemas, la confianza. Es interesante leer el dilema de los [generales bizantinos](https://www.microsoft.com/en-us/research/uploads/prod/2016/12/The-Byzantine-Generals-Problem.pdf) para entender el origen de esto, [en este artículo](https://academy.binance.com/es/articles/byzantine-fault-tolerance-explained) lo detallan.

> **Resumen**: bitcoin es un software, que se ejecuta en una red distribuida, que permite un mecanismo de consenso por el cuál todas las partes están de acuerdo en las transacciones que se incluyen en el "libro de cuentas". Para ello existen unas figuras que se denominan "miners" que son los encargados de escribir la blockchain, y que reciben recompensas por ello en forma de bitcoin.

## Algunos componentes

Aunque aún no se han explicado algunos conceptos en detalle, seguramente los ejemplos que presentamos a continuación sean familiares para el lector, sin saber del todo que significan:

Una dirección pública (wallet address) puede ser algo así: 169EcbWYvkao99Uy9AdqUtVhori3pS9Pih
Un hash de una transacción puede parecerse a esto:  76151be37920f19d08cefaa0464a9ad6c18e869460811bd33da7a745ced7181e 
Una frase semilla puede ser algo parecido a: master resist draft spray pill pelican scissors donkey devote release mask produce


[**SIGUIENTE**](/data/bitcoin_02.md)

