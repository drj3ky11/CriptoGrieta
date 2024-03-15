# Transacción, técnicamente hablando

## Advertencia previa
En este apartado, se bajará a un nivel bastante técnico sobre el como funcionan las transacciones en la cadena. Previo a ello, el lector no experimentado tendrá que ir leyendo otras entradas que se van a ir referenciando a lo largo del artículo. Si la lectura del contenido de este curso es más bien generalista, quizás la lectura de este artículo pueda saltarse para ir directamente a ejemplos prácticos.

Hemos considerado adecuado comenzar por las transacciones, porque en parte es la base. Más adelante se cubrirán los nodos, carteras y otros elementos relevantes. Pero por ahora, estos conceptos se tomarán de forma generalista, para cubrir la teoría explicada.

## ¿Qué es una transacción?

Una transacción de bitcoin es solo un conjunto de datos que desbloquea y bloquea lotes de bitcoins.
Para ser más precisos, una transacción selecciona lotes existentes de bitcoins (inputs) y los desbloquea (o descifra); a continuación crea nuevos lotes de bitcoins (outputs) y los bloquea (cifra) de una nueva forma (por ejemplo con la clave pública del destinatario).

El cifrado de un output contiene la clave pública, esto quiere decir que es necesaria la clave privada asociada a esa pública para descifrar y para firmar.

Una transacción puede agrupar múltiples inputs y generar múltiples outpus. Además, una transacción al ser parte de una cadena, implica que los inputs de una operación serán los outputs de otra operación futura.

Atendiendo a las palabras del creador de Bitcoin:

> Una moneda digital contiene la clave pública de su propietario. Para transferirla, el propietario firma la moneda junto con la clave pública del siguiente propietario. Cualquiera puede comprobar las firmas para verificar el cambio de titularidad.

**Un básico de las transacciones, si yo he recibido por una parte 5btc y por otra 2btc; pero yo quiero enviar 6btc, tengo que enviar los dos lotes (5btc y 2btc) como inputs, y generar dos outputs, uno de 6 btc para el destinatario y otro de 1 btc para mí.**

En resumen, las transacciones Bitcoin se componen de 2 listas:

    una lista de "outputs", cada output dice:
        cuánto bitcoin se transfiere
        quién recibe la transferencia de bitcoin
    una lista de "inputs", cada input incluye:
        una referencia a un output anterior
        una "firma" que pruebe que el creador de la transacción está autorizado a gastar ese output


![Transaccion](/images/bitcoin-transaction.jpg)

## Estructura

Veamos un ejemplo de una transacción, tomemos el hash ` b460aefaca8026569b9d432fa20d6fca82514489479c25ce79b52593b5d76633`
Los datos de la transacción, son conjunto de números tal que así:

```
02000000000102078259717fe999ad3c7005d6b1a30c7b59897f78f6e2fe29b8
ad92279cfb5c860000000000fdffffff90e7b7f15bf9befa81ce468ef2c15894
7b65ec69a22859b683e2d10f785cd4a70000000000fdffffff02f82401000000
00001600140738c93dd800e9c492d43eed777fd68b7fd92371a0860100000000
0017a9140796cc225d45ae0b497972994cc0a163cb9a764d8702473044022011
b2440e1d26fd72b243d0f4f1d768e2808ac46eea7a610dc50f7767ca15ba0902
2030f683e07dcf6b2252beca755b0fa6e9b476e012ae4f96bb59ffc63a2e1d0c
a001210376a2954a0c1eb9d47763dfeae74eafd065ed9fa6aab3534c8d91104b
3bd4c57302473044022041a92bc25071e99ed8d25f0e1930c5ec89e858029786
7194a617dd6af37d6e50022064803d49d585a2258fbbe4fc3afc4409674d7833
fbb33b3f183ac379550118b7012103ab7df281310b558f0095acb94ce642fbd3
cf1dfb46c36661bed11024b983d3382d8e0a00
```
Para continuar con esta aproximación a las transacciones, sería bueno tener claro que son los [bit y bytes](https://es.wikipedia.org/wiki/Unidades_de_informaci%C3%B3n) algo de [hexadecimal](https://es.wikipedia.org/wiki/Sistema_hexadecimal) y un poco de (¿por qué no?) [little-endian o big-endian](https://es.wikipedia.org/wiki/Endianness)

Y una forma un poco más amigable de ver la cadena anterior es esta:

```json
{
  "version": "02000000",
  "marker": "00",
  "flag": "01",
  "inputcount": "02",
  "inputs": [
    {
      "txid": "078259717fe999ad3c7005d6b1a30c7b59897f78f6e2fe29b8ad92279cfb5c86",
      "vout": "00000000",
      "scriptsigsize": "00",
      "scriptsig": "",
      "sequence": "fdffffff"
    },
    {
      "txid": "90e7b7f15bf9befa81ce468ef2c158947b65ec69a22859b683e2d10f785cd4a7",
      "vout": "00000000",
      "scriptsigsize": "00",
      "scriptsig": "",
      "sequence": "fdffffff"
    }
  ],
  "outputcount": "02",
  "outputs": [
    {
      "amount": "f824010000000000",
      "scriptpubkeysize": "16",
      "scriptpubkey": "00140738c93dd800e9c492d43eed777fd68b7fd92371"
    },
    {
      "amount": "a086010000000000",
      "scriptpubkeysize": "17",
      "scriptpubkey": "a9140796cc225d45ae0b497972994cc0a163cb9a764d87"
    }
  ],
  "witness": [
    {
      "stackitems": "02",
      "0": {
        "size": "47",
        "item": "3044022011b2440e1d26fd72b243d0f4f1d768e2808ac46eea7a610dc50f7767ca15ba09022030f683e07dcf6b2252beca755b0fa6e9b476e012ae4f96bb59ffc63a2e1d0ca001"
      },
      "1": {
        "size": "21",
        "item": "0376a2954a0c1eb9d47763dfeae74eafd065ed9fa6aab3534c8d91104b3bd4c573"
      }
    },
    {
      "stackitems": "02",
      "0": {
        "size": "47",
        "item": "3044022041a92bc25071e99ed8d25f0e1930c5ec89e8580297867194a617dd6af37d6e50022064803d49d585a2258fbbe4fc3afc4409674d7833fbb33b3f183ac379550118b701"
      },
      "1": {
        "size": "21",
        "item": "03ab7df281310b558f0095acb94ce642fbd3cf1dfb46c36661bed11024b983d338"
      }
    }
  ],
  "locktime": "2d8e0a00"
}
```

Ahora, iremos desgranando lo que significa cada parte, es aquí cuando el itinerario de este contenido se convierte en una auténtica madrigera... Lo recomendable es que vayas visitando cada enlace según necesites profundizar en ello. En los liks se cubren partes muy técnicas y en algunas ocasiones, para el lector no experimentado en las bases de informática puede ser un terreno bastante agreste... Pero con paciencia e interés todo se llega a entender.

[**Versión**](/data/bitcoin_version.md) en nuestro ejemplo corresponde a `02000000`, son 4 bytes en Little-Endian. Representa el número de la versión empleada en la transacción. Las versiones 1 se ven desde el 2009, y las versiones 2 [BIP 68](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki) desde el 2015. La V2 introduce el [RLT]() o tiempo de bloqueo relativo; el RLT permite especificar una cantidad de tiempo o número de bloques desde que se extrajo un output antes de que una transacción que lo gaste sea válida.


**Marker y flag** ocupan 2 bytes y sirven para indicar si la transacción es [Segregated Witness](/data/SegregatedWitness.md) o SegWit. Únicamente son necesarios para aquellos outputs cifrados con P2WPKH, P2WSH o P2TR. Todos ellos los veremos más adelante en la parte [Script](/data/scriptbtc.md).

El Marker es el primer byte, para indicar SegWit se pondrá en 00.

La flag, es el siguiente byte, y en el caso de SegWit irá a 01.

**Input Count** muy fácil, indica el número de inputs que hay en la transacción



**Input** son los "output" que se seleccionan para enviar en la transacción. **Hay que tener presente, que en una transacción se seleccionan outputs que hemos recibido, que pasarán a ser inputs de la nueva transacción**. Este campo lo componen, por cada input los siguientes apartados:

```json
  "inputs": [
    {
      "txid": "078259717fe999ad3c7005d6b1a30c7b59897f78f6e2fe29b8ad92279cfb5c86",
      "vout": "00000000",
      "scriptsigsize": "00",
      "scriptsig": "",
      "sequence": "fdffffff"
    },
```

- TXID  32 bytes 	Natural Byte Order 	el txid de la transacción del output que se quiere gastar.
- VOUT 	00000000 	4 bytes 	Little-Endian 	Una transacción puede tener distintos outputs, el VOUT hace referencia a cual de ellos. 
- ScriptSig Size 	00 	variable 	Compact Size 	el tamaño que ocupara, a continuación el  ScriptSig.
- ScriptSig 	[script] 	variable 	Script 	el script que se ha de emplear para desbloquear, en el caso de legacy consta aquí (P2PK P2PKH P2MS P2SH), en segwit se verá un 00 porque están contenidos (P2WPKH o P2WSH) en el campo witness.
- Sequence 	fdffffff 	4 bytes 	Little-Endian Este campo permite indicar:

-> Locktime. Al establecer al menos una de las secuencias en 0xFFFFFFFE o inferior, se habilita el campo de tiempo de bloqueo próximo para toda la transacción.

-> Replace-by-Fee. Al establecer un valor de secuencia de 0xFFFFFFFD o inferior, se habilita esta entrada para que se gaste en una transacción diferente con una tarifa más alta (si esta transacción actual todavía está en la reserva de memoria en ese momento).

-> Relative Locktime. Estableciendo un valor de secuencia inferior a 0x80000000 puede establecer un tiempo de bloqueo relativo en esta entrada. Esto significa que la transacción no puede ser minada hasta un punto específico en el tiempo. Esto puede ser un número de segundos o un número de bloques desde que la salida a la que has hecho referencia fue minada originalmente.

Un valor bastante común el es `0xFFFFFFFD` que permite locktime y RbF.



**Output Count** lo mismo que el input count, indica el número de outputs de la transacción

**Output** forman la parte de la transacción que se envía, tiene unos campos específicos que veremos a continuación:

```json
  "outputs": [
    {
      "amount": "f824010000000000",
      "scriptpubkeysize": "16",
      "scriptpubkey": "00140738c93dd800e9c492d43eed777fd68b7fd92371"
    },
```
**Amount** 8 bytes, integer, Little-Endian establece la cantidad de satoshi que se quiere enviar (1 satoshi = 0.00000001 BTC). Hay que afinar con los cálculos al crear la transacción, todo lo restante que no se asigne correctamente lo reclamará el minero como fee.

**scriptpubkeysize** igual que los inputs

**scriptpubkey** es el código con el que se está bloqueando el output:

P2PKH (legacy) - Bloquea la salida al hash de una clave pública. Para desbloquear es necesario proporcionar la clave pública original y una firma válida. Ejemplo: 76a914{publickeyhash}88ac

P2SH (legacy) - Bloquea la salida con el hash de un script personalizado. Para desbloquear es necesario proporcionar el script original junto con el script que lo satisface. Ejemplo: a914{scripthash}87

P2WPKH - Bloquear la salida al hash de una clave pública. Funciona igual que un P2PKH, pero el código de desbloqueo va en el campo witness en lugar del campo scriptsig. Ejemplo: 0014{publickeyhash}

P2WSH - Bloquea la salida al hash de un script personalizado. Funciona igual que un P2SH, pero el código de desbloqueo va en el campo witness en lugar del campo scriptsig. Ejemplo: 0020{scripthash}


**Witness**

Como ya hemos dicho, este campo solo aplica a las tx de segwit. Contiene un campo witness por cada input:

```json
"witness": [
    {
      "stackitems": "02",
      "0": {
        "size": "47",
        "item": "3044022011b2440e1d26fd72b243d0f4f1d768e2808ac46eea7a610dc50f7767ca15ba09022030f683e07dcf6b2252beca755b0fa6e9b476e012ae4f96bb59ffc63a2e1d0ca001"
      },
      "1": {
        "size": "21",
        "item": "0376a2954a0c1eb9d47763dfeae74eafd065ed9fa6aab3534c8d91104b3bd4c573"
      }
    },
    {
      "stackitems": "02",
      "0": {
        "size": "47",
        "item": "3044022041a92bc25071e99ed8d25f0e1930c5ec89e8580297867194a617dd6af37d6e50022064803d49d585a2258fbbe4fc3afc4409674d7833fbb33b3f183ac379550118b701"
      },
      "1": {
        "size": "21",
        "item": "03ab7df281310b558f0095acb94ce642fbd3cf1dfb46c36661bed11024b983d338"
      }
    }
  ],
```
El campo **stackitems** indica cuantos componentes han de sumarse a la pila (stack). El siguiente campo es el **size** que indica el tamaño del siguiente campo y finalmente el **item**, que será la firma (bytes) y luego la clave pública.

En el ejemplo de arriba es un P2WPKH que suele tener la estructura 0247FIRMA21CLAVEPUBLICA, se aprecia que en los dos casos tiene la misma firma y la misma clave pública (ojo, en formato comprimido); eso se debe a que ambos provienen de la misma cartera!! Firma la misma clave privada.

**Locktime** lo componen 4 bytes en Little-Endian. Permite especificar una altura de bloque o tiempo en el que esta transacción puede ser minada.

Inferior o igual a 500000 = Altura de bloque

Más de 500000 = Hora Unix


¿Quieres más detalles al respecto? Consulta [Bitcoindeveloper](https://developer.bitcoin.org/devguide/transactions.html)