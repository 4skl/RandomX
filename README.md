See https://github.com/tevador/RandomX for installation

# Introduction
I'm trying to solve problems occured while trying to run on RPi3B (and RPi4B in the future)
And by this way I'm trying to learn more about the RandomX algorithm (I don't fully understand the algorithm yet)

# RPi errors
ERROR: Cannot create VM with the selected options. Try using --softAes with call :  
: ./randomx-benchmark --verify
> problems without --softAes option can came from the 
 fact that Cortex-A53 desnt implement AES (in hardware) ?:
 
ERROR: Dataset allocation failed
> Verify if this error cannot came from --softAes but from --mine (and what can raise this type of exception)

: ./randomx-benchmark --mine  
: ./randomx-benchmark --mine --softAes

this error seem to be raised by full memory mode
an is raised by this code with a std::bad_alloc exception: 
call used : ./randomx-benchmark --mine --softAes --nonces 10

```cpp
dataset = new randomx_dataset();
if (flags & RANDOMX_FLAG_LARGE_PAGES) {
    dataset->dealloc = &randomx::deallocDataset<randomx::LargePageAllocator>;
    dataset->memory = (uint8_t*)randomx::LargePageAllocator::allocMemory(randomx::DatasetSize);
}
else {
    dataset->dealloc = &randomx::deallocDataset<randomx::DefaultAllocator>;
    dataset->memory = (uint8_t*)randomx::DefaultAllocator::allocMemory(randomx::DatasetSize); //Error came from here
}
```
(uint8_t*) aligned_alloc(count,64); // count > 2^29 cause return (nil) pointer

This line call an aligned_alloc(count, alignment), with count = 2^31+24287*64 and alignement = 64

we try to allocate a dataset of size 2^31+24287*64 bytes

There is more errors but not yet all listed