# MSP430-BIP39
This project will consist of using the MSP430F5529 as a BIP39 seed word generator, deriving entropy from various sources.

## BIP39
In the Bitcoin protocol, [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki) defines a method of generating a seed phrase from derived entropy.
A seed phrase is basically a human-readable encoding of a private key. There is a set of 2048 possible words for the seed phrase, and it can have a lenght of 12, 15, 18, 21 or 24 words;
the most common are 12 and 24 words. I go on more detail about this process on [this blog post](https://luisschwab.net/blog/from-dice-to-address/).

## Entropy
For safe seed generation, it's essential to derive entropy from a random source, such as a hardware based PRNG, or from random physical events, such as dice throws.
It's interesting to source at least 256 bits of entropy for good key generation. There are known attacks on low entropy seed generation, which has the real risk of loss
of funds.

On this project, I'll make the folowing sources availabe to the user:
- Dice thows, via a keypad or something similar,
- Accelerometer (shake to make entropy),
- Microphone,

## Software
BIP39 seed phrase generation is pretty straight forward: only basic math operations are necessary, and the most complex function will be the SHA-256 
hashing function, which I have previously implemented [here](https://github.com/luisschwab/sha256.c).

## Hardware
I estimate that the hardware needed will be:
- MSP430F5529LP
- I2C display
- Keypad or some medium to enter dice throw values (1-6 + enter + delete)
- Accelerometer
- Microphone
