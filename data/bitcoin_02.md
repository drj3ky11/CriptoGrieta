# Transacciones

En este primer enfoque sobre las transacciones, nos quedaremos en una capa de abstracción bastante elevada, únicamente para tener una idea general. Más adelante, profundizaremos en aspectos más técnicos sobre las mismas

## Pensando en Outputs

Para entender correctamente el funcionamiento de una transacción, es más sencillo hacerlo mediante el uso del concepto *Output*, que no suena muy intuitivo, pero al final del artículo le habrás encontrado el sentido.

Imaginemos la blockchain como un almacén de cajas cerradas con llave, estas cajas las denominaremos Outputs. Estas cajas contienen una cantidad concreta de Bitcoin.

![Output](/images/outpu1.png)

En el proceso de una transacción, se desbloquea uno de estos outputs, y se bloquea una nueva *caja* de forma que solo el destinatario puede abrirla. Si, esto suena raro, y difícil, pero no lo es tanto. Imaginemos que quiero enviar 20btc. Primeramente tomare un Output que tenga tal cantidad, dentro de los que tengo disponibles y lo *abriré*. Pero no quiero enviar los 20, solo 5btc; entonces se crearán dos outputs nuevos, dos nuevas cajas, una contendrá 10btc, y estará cerrada (solo yo la puedo abrir) y la otra contendrá 5btc y estará cerrada para todos, salvo para el destinatario.

![Transaccion](/images/outpu2.png)

## Si hay cajas cerradas tendrá que haber llaves...

Abrir... Cerrar... no carece de sentido la comparación. Como ya se ha mencionado previamente, bitcoin sienta sus bases sobre la criptografía y en concreto sobre denominada ["Criptografía de Clave Pública"](https://en.wikipedia.org/wiki/Public-key_cryptography) o asimétrica. La base de esta criptografía, consiste en que al contrario que en los sistemas clásicos, existen dos claves. En un sistema clásico se cifra con la misma clave que se descifra, en uno de clave pública, se cifra con una clave y se descifra con otra. Esto aporta numerosas ventajas y está tan implantado en el día a día que lo usamos sin darnos cuenta, con los certificados digitales, la navegación https... Si quieres aprender más sobre criptografía [este es un buen recurso](https://www.cryptool.org/en/jct/)

Como en todo sistema de clave pública, existe una clave privada y una pública (la denominación no puede ser más explicita, seguramente ya sepas cual de ellas hay que custodiar en secreto) y ambas guardan una relación aritmética, bastante compleja, en la que en teoría es imposible desde la clave pública obtener la privada. Este par de claves nos permite, principalmente dos operaciones, **firmar** y **cifrar**:
````
Firmar: Se emplea la clave privada, "se cierra con la clave privada" y cualquiera que tenga mi clave pública, puede contrastar que el que ha firmado (cerrado) he sido yo.

Cifrar: Se emplea la clave pública del destinatario, esto hace que una vez cifrado algo, solo el destinatario (con su clave privada) será el único capaz de descifrar.
````

