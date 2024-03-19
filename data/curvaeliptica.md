# Elliptic Curve Digital Signature

La criptografía de curva elíptica (ECC), es la base criptográfica sobre la que se fundamenta Bitcoin; comprenderla, al menos en parte, es un paso para llegar a entender Bitcoin.

El ECC se emplea en otras muchas cosas, por ejemplo TLS, PGP y SSH. Previo al ECC, la criptografía se basaba (y lo sigue haciendo en parte) en la aritmética modular de sistemas como el [RSA](https://es.wikipedia.org/wiki/RSA), [DSA](https://es.wikipedia.org/wiki/DSA) y otros derivados de [Diffie-Hellman](/resources/New%20directions%20in%20cryptography.pdf).

![ecc1](/images/ecc1.png)

### Explicación para todos

Imaginemos un equipo, en el que los componentes del mismo solo saben multiplicar; son minioms que solo multiplican. El jefe del equipo es el único que sabe dividir y multiplicar, y les tiene explicado a los minioms que su número favorito es el 5.

Un día, los minioms se encuentran un mensaje `Hoy no puedo ir a trabajar vuelvo mañana` y firmado `El jefe, 8`. Los minioms, para asegurarse que el mensaje es de su jefe, cuentan los caracteres del mensaje (40) y multiplican el número favorito del jefe (5) por el que consta en la firma (8); y al comprobar que 5x8=40 y que 40 son los caracteres tienen la seguridad de que lo ha escrito el jefe.

Pero además, como no saben dividir, no podrían modificar el mensaje de ninguna forma y firmar... Esto, más o menos, es parte del a criptografía de clave pública y la firma digital.

La clave para entender las bases de ECC es entender que una curva elíptica no es más que `Punto = Multiplicador * Punto Generador Público`.

De ahí se deriva, que la clave privada es el **Multiplicador** y la clave pública es el **Punto**. Dado el Punto, es imposible averiguar el multiplicador. Con el Multiplicador se puede sumar, restar, multiplicar y dividir; pero con el Punto solo se puede sumar y multiplicar. **Crear una firma requiere dividir, pero comprobarla solo requiere multiplicar**

La realidad no dista tanto del ejemplo del jefe y los minioms.

## Explicación técnica

Secp256k1 es la curva que usa bitcoin.

En construcción..........
