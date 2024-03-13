# Versión
La versión no es algo que suela preocupar al usuario medio de bitcoin, pero si se pretende un conocimiento más hondo sobre el tema es necesario detenerse un poco para entenderlas y como se representan en los [bloques](/data/bloque.md), así como su evolución. Actualmente existen las siguientes versiones:

0x00000001 = The original software Height Activated: 0

0x00000002 = [BIP 34](https://github.com/bitcoin/bips/blob/master/bip-0034.mediawiki):  Coinbase

0x00000003 = [BIP 66](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki): firmas Strict DER

0x00000004 = [BIP 65](https://github.com/bitcoin/bips/blob/master/bip-0065.mediawiki): OP_CHECKLOCKTIMEVERIFY

Las actualizaciones, se hacen permanentes entre los 950 y 1000 bloques siguientes minados con la versión nueva.

![Btc actualizandose](/images/btc_gym.png)

En 2015, la versión cambió empezando a usar un campo de bit, que permite añadir hasta 29 características a los mineros. Esto se traduce en que en los 4 bytes que representan la versión, se pueden activar (a nivel bit, es decir 32 campos) bits de forma que representen alguna característica. Veamos un ejemplo:

El bloque `00000000003fba93cce03e40bfe90a9dbf376cb9f2437c09b967c429fdfa2d76`

A nivel bit sería `00000000000000000000000000000001` y en Hex `0x00000001` que no tiene el campo bit activado.

Por contra, el bloque ` 0000000000000000002dd37b33c414b829918ed2ef710965952069212b0e3449` con bits `00100000000000000000000000000000` y en Hex `0x20000000`

Otro ejemplo, el bloque ` 00000000000000000003a1f6d39e2b5ae317a85561d51bcae7b0ed9b2131f545` a nivel bit `00100000110000000000000000000000` y en Hex `0x20c00000`

Los campos que se han usado para mejoras han sido los siguientes:

- Bit 0: [BIP 112](https://github.com/bitcoin/bips/blob/master/bip-0112.mediawiki) CHECKSEQUENCEVERIFY Ejemplo: `0b00100000000000000000000000000001` 
- Bit 1: [BIP 141](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki) Segwit Ejemplo: `0b00100000000000000000000000000010`
- Bit 2: [BIP 341](https://github.com/bitcoin/bips/blob/master/bip-0341.mediawiki) Taproot Ejemplo: `0b00100000000000000000000000000100`

Como te habrás dado cuenta ya, para emplear los "bits de versión" para marcar hay que comenzar por poner `0b001` tal como indica el [BIP 9](https://github.com/bitcoin/bips/blob/master/bip-0009.mediawiki). Evidentemente, haciendo cuentas, nos quedan 29 bits para marcar.

El campo de versión, aumentó más sobre el bloque 411000 al incluir el 0b001, veamos unos ejemplos:

-  **0x20000000** - Se emplea la marca de bit, pero no señala nada.
    Version Bits: 0b00100000000000000000000000000000
    Example: 000000000000000005025d88492c54a51ac3bccaaa15c12a05aee16a28d6b294 (Height 410,370)

- **0x20000001** - Version bits señalando la mejora CSV.
    Version Bits: 0b00100000000000000000000000000001
    Example: 000000000000000004983f04183f2a6ae7f1cdf6ddb8f4b3f79e39e14392db4c (Height 416,498)

- **0x20000002** - Version bits Segwit
    Version Bits: 0b00100000000000000000000000000010
    Example: 0000000000000000001094a0145695e4228c21cbbc6be40507f728c6b7d6f16a (Height 471,329)

- **0x20000003** - Version bits Taproot.
    Version Bits: 0b00100000000000000000000000000100
    Example: 0000000000000000004f065fae967b93540f321076684fe926d4e7bfbcd77ab (Height 703,353)






