See https://github.com/tevador/RandomX for installation

# Introduction
I'm trying to solve problems occured while trying to run on RPi3B (and RPi4 in the future)
And by this way I'm trying to learn more about the RandomX algorithm (I don't fully understand the algorithm yet)

# RPi errors
ERROR: Cannot create VM with the selected options. Try using --softAes with call :
: ./randomx-benchmark --verify
> problems without --softAes option can came from the  fact that Cortex-A53 desnt implement AES (in hardware) ?:
 
ERROR: Dataset allocation failed
> Verify if this error cannot came from --softAes but from --mine (and what can raise this type of exception)
: ./randomx-benchmark --mine
: ./randomx-benchmark --mine --softAes

There is more errors but not yet all listed
