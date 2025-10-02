Essentials of Computer Architecture — Notes

Big picture

- Knowing hardware basics (CPU, memory, disk) matters for performance and big data scale.
    
- Python code ultimately runs as machine code; one Python line can expand into many CPU instructions.
    

Core ideas

1. Machine code vs. Python
    
    - Python statements compile/interpret down to multiple machine instructions.
        
    - Lines of Python don’t map directly to runtime cost; called functions may execute lots of instructions.
        
2. CPU, registers, and data flow
    
    - CPU core executes instructions on data in registers (very small, very fast).
        
    - Data moves between registers and RAM via caches (L1/L2/L3) to hide RAM latency.
        
    - Inputs/outputs of instructions resemble function parameters/returns via registers.
        
3. Special-purpose speedups
    
    - SIMD/Vector ops: apply one operation to many elements at once (e.g., add across 8 array items).
        
    - Multicore: multiple cores run threads/programs in parallel for speedups.
        

Storage vs. working state

- Disk/SSD: persistence, files; programs don’t operate on files directly—read/write into RAM.
    
- RAM: working state for variables, arrays, data frames; volatile.
    

Clock speeds (ballpark)

- Smartwatch ~1.5 GHz → ~1.5B instructions/sec (best case).
    
- Smartphone ~2.5 GHz → ~2.5B instructions/sec.
    
- Desktop/server ~5 GHz → ~5B instructions/sec per core; multiple cores run independently.
    

Memory hierarchy (fast → slow)

- Registers: fastest; need ≤0.2 ns access at 5 GHz; very few (~16 int, 16–32 float).
    
- L1 cache: ~32 KB, ~1 ns access; holds hot, small working sets.
    
- L2 cache: ~256–512 KB, ~2–3 ns.
    
- L3 cache: megabytes, shared/slower on multicore.
    
- RAM: gigabytes (laptops 16–32 GB; servers 128–256+ GB; some machines up to TB).
    
- Disk/SSD and network: much larger, much slower; petabyte-scale data lives beyond RAM → clusters/files.
    

Why caches matter (example)

- Large array (1M ints ≈ 4 MB). RAM read ≈ 75 ns per miss.
    
- Hardware fetches contiguous blocks into cache (e.g., 4 KB at once).
    
- First access pays ~75 ns; subsequent accesses in that block cost ~1 ns each → big amortized speedup (~75×).
    
- Writes: CPU writes to cache, then cache flushes back to RAM in chunks; similar amortization.
    

Latency intuition (Dean/Norvig chart idea)

- L1: ~1 ns.
    
- L2: ~4 ns.
    
- RAM: tens of ns (~75 ns).
    
- SSD/network in datacenter: microseconds (tens).
    
- Spinning disk or cross-world network: milliseconds to hundreds of ms.
    
- Use this to judge what operations are feasible within a time budget.
    

How to leverage the hierarchy

- Filter early: drop unneeded rows/columns ASAP to fit hot data in cache.
    
- Locality: store frequently used fields together to hit contiguous blocks.
    
- Access patterns: prefer sequential passes; avoid scattered random access to help prefetching.
    
- Compact representations: smaller footprints improve cache fit (trade-offs with access predictability).
    

Jeff Dean context

- Co-created MapReduce (precursor to Spark) and early scalable deep learning at Google; led Google AI/Research.
    
- Known for legendary performance wisdom and culture around “Jeff Dean facts.”
    

Key takeaways

- Performance depends heavily on where data lives (registers/caches/RAM/disk/network).
    
- Sequential, predictable access lets hardware prefetch and cache effectively.
    
- Minimize memory footprint; group data for locality; use vectorization and multicore when possible.