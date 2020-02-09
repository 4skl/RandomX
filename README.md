See https://github.com/tevador/RandomX for installation
trying to solve a problem on rpi --mine mode problems

ERROR: Cannot create VM with the selected options. Try using --softAes with call :
: ./randomx-benchmark --verify
> problems without --softAes option can came from the  fact that Cortex-A53 desnt implement AES (in hardware) ?:
 
ERROR: Dataset allocation failed
> Verify if this error cannot came from --softAes but from --mine (and what can raise this type of exception)
: ./randomx-benchmark --mine
: ./randomx-benchmark --mine --softAes

There is more errors but not yet all listed
