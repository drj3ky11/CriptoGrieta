# Segregated Witness

Ha sido uno de los mayores avances en Bitcoin y se introdujo en el 2017 mediante los [BIP 141](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki), [BIP 143](https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki) y [BIP 144](https://github.com/bitcoin/bips/blob/master/bip-0144.mediawiki)

Básicamente, se aumentó el tamaño de bloque, se cambió el formato de las direcciones y se creo una nueva estructura de transacciones.

La razón para esta actualización, se basó en el cambio de como se obtiene el [hash o txid](/data/txid.md) de la transacción. En la versión anterior **Legacy** se creaba el hash con todos los datos de la transacción, con SegWit se evita crear un hahs  que contenga las firmas. Esto se debe a una remota posibilidad de manipulación del txid una vez enviada la transacción a la red

En una transacción quedan sin formar parte del [HASH256](/data/hash256.md) el marker, flag y los campos de witness.

## Nueva estructura

SegWit introduce una nueva estructura de las transacciones, introduciendo el campo witness, que almacena el código de desbloqueo (firmas) para los nuevos protocolos de bloqueo introducidos [P2WPKH](/data/scriptbtc.md) y [P2WSH](/data/scriptbtc.md); los scripts empleados en Legacy eran  [P2PKH](/data/scriptbtc.md), [P2SH](/data/scriptbtc.md).



Otro cambio introducido, fue la modificación sobre como se calcula el tamaño de la transacción, de hecho, segwit provoca que se deje de hablar de tamaño (size) y se hable de peso (weigth). Anteriormente se calculaba en función del número de bytes; con segwit, se asignan unos multiplicadores a distintas partes de la transacción, por ejemplo la parte del marker, flag y witness será un x1 mientras que el resto x4. 

Esto proporciona un peso menor en las transacciones y por ello, se aumenta el número de transacciones que entran en un bloque. Se pasó de un tamaño máximo de bloque de 1,000,000 bytes a 4,000,000 bytes.

Al introducir nuevos scripts, también cambió el formato de las direcciones a un Bech32 (las bc1q) que permite una detección de errores mejor y un formato más sencillo de transcribir. 

Otro cambio que introducen los scripts nuevos, es un proceso distinto de firmado para desbloquear y bloquear pese a que se sigue empelando [ECDSA](/data/curvaeliptica.md) la diferencia reside en como se preparan los datos para la firma.

### wTXID

Dado que SegWit introduce una nueva forma de calcular el TXID, hay campos que se quedan fuera del hash; estos se introducen en le wTXID. Y estos datos, han de añadirse de alguna forma al bloque. El constructor del bloque ahora calculará el [merkle root](/data/merkleroot.md) de todos los wTXID y lo incluirá en la transacción [coinbase](/data/coinbasetx.md). Esto, evita que se puedan modificar los datos witness en las transacciones ya incluidas en el bloque.

El wTXID se calcula con los campos  HASH256 [version] [marker] [flag] [inputs] [outputs] [locktime] [witness]
