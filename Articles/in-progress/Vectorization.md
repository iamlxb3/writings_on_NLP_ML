### Why vectorization is faster

https://stackoverflow.com/questions/35091979/why-is-vectorization-faster-in-general-than-loops

Answer1: 

>Vectorization (as the term is normally used) refers to SIMD (single instruction, multiple data) operation.
>
>That means, in essence, that one instruction carries out the same operation on a number of operands in parallel. For example, to multiply a vector of size N by a scalar, let's call M the number of operands that size that it can operate on simultaneously. If so, then the number of instructions it needs to execute is approximately N/M, where (with purely scalar operations) it would have to carry out N operations.
>
>For example, Intel's current AVX 2 instruction set uses 256-bit registers. These can be used to hold (and operate on) a set of 4 operands of 64-bits apiece, or 8 operands of 32 bits apiece.
>
>So, assuming you're dealing with 32-bit, single-precision real numbers, that means a single instruction can do 8 operations (multiplications, in your case) at once, so (at least in theory) you can finish N multiplications using only N/8 multiplication instructions. At least, in theory, this should allow the operation to finish about 8 times as fast as executing one instruction at a time would allow.
>
>Of course, the exact benefit depends on how many operands you support per instruction. Intel's first attempts only supported 64-bit registers, so to operate on 8 items at once, those items could only be 8 bits apiece. They currently support 256-bit registers, and they've announced support for 512-bit (and they may have even shipped that in a few high-end processors, but not in normal consumer processors, at least yet). Making good use of this capability can also be non-trivial, to put it mildly. Scheduling instructions so you actually have N operands available and in the right places at the right times isn't necessarily an easy task (at all).
>
>To put things in perspective, the (now ancient) Cray 1 gained a lot of its speed exactly this way. Its vector unit operated on sets of 64 registers of 64 bits apiece, so it could do 64 double-precision operations per clock cycle. On optimally vectorized code, it was much closer to the speed of a current CPU than you might expect based solely on its (much lower) clock speed. Taking full advantage of that wasn't always easy though (and still isn't).
>
>Keep in mind, however, that vectorization is not the only way in which a CPU can carry out operations in parallel. There's also the possibility of instruction-level parallelism, which allows a single CPU (or the single core of a CPU) to execute more than one instruction at a time. Most modern CPUs include hardware to (theoretically) execute up to around 4 instructions per clock cycle1 if the instructions are a mix of loads, stores, and ALU. They can fairly routinely execute close to 2 instructions per clock on average, or more in well-tuned loops when memory isn't a bottleneck.
>
>Then, of course, there's multi-threading--running multiple streams of instructions on (at least logically) separate processors/cores.
>
>So, a modern CPU might have, say, 4 cores, each of which can execute 2 vector multiplies per clock, and each of those instructions can operate on 8 operands. So, at least in theory, it can be carrying out 4 * 2 * 8 = 64 operations per clock.
>
>Some instructions have better or worse throughput. For example, FP adds throughput is lower than FMA or multiply on Intel before Skylake (1 vector per clock instead of 2). But boolean logic like AND or XOR has 3 vectors per clock throughput; it doesn't take many transistors to build an AND/XOR/OR execution unit, so CPUs replicate them. Bottlenecks on the total pipeline width (the front-end that decodes and issues into the out-of-order part of the core) are common when using high-throughput instructions, rather than bottlenecks on a specific execution unit.

 Answer2:

> Vectorization has two main benefits.
>
> The primary benefit is that hardware designed to support vector instructions generally has hardware that is capable of performing multiple ALU operations in parallel when vector instructions are used. For example, if you ask it to perform 16 additions with a 16-element vector instruction, it may have 16 adders that can do all the additions at once, in parallel. The only way to access all those adders is through vectorization. With scalar instructions you just get the 1 lonely adder.
> There is usually some overhead saved by using vector instructions. You load and store data in big chunks (up to 512 bits at a time on some recent Intel CPUs) and each loop iteration does more work so the loop overhead is generally lower in a relative sense, and you need fewer instructions to do the same work so the CPU front-end overhead is lower, etc.
> Finally, your dichotomy between loops and vectorization is odd. When you take non-vector code and vectorize it, you are generally going to end up with a loop if there was a loop there before, or not if there wasn't. The comparison is really between scalar (non-vector) instructions and vector instructions.

