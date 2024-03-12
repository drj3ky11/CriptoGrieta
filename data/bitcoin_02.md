# Transacciones

En este primer enfoque sobre las transacciones, nos quedaremos en una capa de abstracción bastante elevada, únicamente para tener una idea general. Más adelante, profundizaremos en aspectos más técnicos sobre las mismas

## Pensando en Outputs

Para entender correctamente el funcionamiento de una transacción, es más sencillo hacerlo mediante el uso del concepto *Output*, que no suena muy intuitivo, pero al final del artículo le habrás encontrado el sentido.

Imaginemos la blockchain como un almacén de cajas cerradas con llave, estas cajas las denominaremos Outputs. Estas cajas contienen una cantidad concreta de Bitcoin.

![Output](/images/outpu1.png)

En el proceso de una transacción, se desbloquea uno de estos outputs, y se bloquea una nueva *caja* de forma que solo el destinatario puede abrirla. Si, esto suena raro, y difícil, pero no lo es tanto. Imaginemos que quiero enviar 20btc. Primeramente tomare un Output que tenga tal cantidad, dentro de los que tengo disponibles y lo *abriré*. Pero no quiero enviar los 20, solo 5btc; entonces se crearán dos outputs nuevos, dos nuevas cajas, una contendrá 10btc, y estará cerrada (solo yo la puedo abrir) y la otra contendrá 5btc y estará cerrada para todos, salvo para el destinatario.

![Transacción](/images/outpu2.png)

## Si hay cajas cerradas tendrá que haber llaves...

Abrir... Cerrar... no carece de sentido la comparación. Como ya se ha mencionado previamente, bitcoin sienta sus bases sobre la criptografía y en concreto sobre denominada ["Criptografía de Clave Pública"](https://en.wikipedia.org/wiki/Public-key_cryptography) o asimétrica. La base de esta criptografía, consiste en que al contrario que en los sistemas clásicos, existen dos claves. En un sistema clásico se cifra con la misma clave que se descifra, en uno de clave pública, se cifra con una clave y se descifra con otra. Esto aporta numerosas ventajas y está tan implantado en el día a día que lo usamos sin darnos cuenta, con los certificados digitales, la navegación https... Si quieres aprender más sobre criptografía [este es un buen recurso](https://www.cryptool.org/en/jct/)

Como en todo sistema de clave pública, existe una clave privada y una pública (la denominación no puede ser más explicita, seguramente ya sepas cual de ellas hay que custodiar en secreto) y ambas guardan una relación aritmética, bastante compleja, en la que en teoría es imposible desde la clave pública obtener la privada, en cambio, la clave pública procede de la clave privada. Este par de claves nos permite, principalmente dos operaciones, **firmar** y **cifrar**:

```php
#Firmar:
 Se emplea la clave privada, "se cierra con la clave privada" y cualquiera que
 tenga mi clave pública, puede contrastar que el que ha firmado (cerrado) he sido yo.

#Cifrar: 
Se emplea la clave pública del destinatario, "se cierra con la clave pública de otro"
 esto hace que una vez cifrado algo, solo el destinatario (con su clave privada) 
 será el único capaz de descifrar.
```

==¿Y esto que tiene que ver con Bitcoin?==

Púes muy sencillo, para tener bitcoin u operar con bitcoin es necesario tener un par de claves, como las que hemos presentado anteriormente. Y su uso es fundamental:

Para desbloquear los "Outputs" necesito abrir con mi llave privada (firmando digitalmente, de forma que todos puedan ver que los fondos son míos), para enviar los fondos, la nueva caja que quiero cerrar para el destinatario, lo haré con su clave pública, y el resto, que volverá a mí, lo cerraré con mi clave pública.

La dirección de bitcoin, que estamos acostumbrados a ver, es una permutación de la clave pública (esto tiene bastantes matices, pero de momento sirva esta simplificación), que hace más fácil la memorización de la dirección. La clave pública y privada tiene un aspecto bastante agreste, una dirección de btc no tanto... o eso dicen.

Lo anterior está explicado muy por encima, pero hay un par de cosas fundamentales que hay que comprender:

> **La clave privada determina la posesión de fondos**, quién tiene la privada puede enviar fondos. ¿A dónde? A una clave pública, que a su vez tiene asociada una privada distinta, que permite reenviar esos fondos recibidos. 

> **Bitcoin, en parte, se trata como bloques indivisibles**, como cajas hemos dicho. Esto se puede aproximar también a billetes, si tengo un billete de 5€ no puedo pagar 2€ rompiendo el billete y entregando el trozo proporcional. Tengo que pagar con todo el billete y recibiré un cambio. En bitcoin, cada vez que recibimos una cantidad, se comporta como un bloque, una caja que hemos recibido. Si queremos mandar parte, tenemos que abrir la caja entera y lo sobrante lo guardaremos en otra caja más pequeña. De la forma contraria, para hacer una transacción de mayor valor quizás necesitemos juntar varias "cajas".

Seguramente, te suene también que existe un conjunto de palabras, denominadas comúnmente **"frase semilla"**. Consiste entre 12 y 24 palabras en ingles, carentes de sentido. Esta semilla, por ahora, nos quedaremos que sirve para "generar" un par de claves. Humanamente, es más sencillo apuntar o memorizar la semilla que la clave privada, de ahí que la semilla se emplee como copia de las claves, o de qué directamente un usuario no vea nunca su clave privada, únicamente esta semilla. Esto es crucial, el que posee la semilla, tiene el control sobre los fondos, dado que de la semilla (simplificando) derivan las claves.

![Llaves y semilla](/images/beginners-wallets-seed-addresses.png)
[Fuente](https://learnmeabitcoin.com/beginners/wallets/)

[**SIGUIENTE**](/data/bitcoin_03.md)