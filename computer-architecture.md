# Principles of Computer Architecture

## CPU Caching

* small pool of memory that stores info the CPU is most likely to need next
* if the CPU finds the data, called “cache hit"
* if the CPU can’t find the data, called “cache miss"
* L1 —> L2 —> L3 —> L4 —> main memory (DRAM)
* there’s diminishing marginal return for larger caches
    * slower
    * more expensive
    * after a certain point, better to spend CPU resources on additional cores, etc
* rule of thumb —> add one level of cache every 10 years
* caching, from fastest to slowest
    * L1
        * first level CPU cache
        * .5ns read
        * very small in comparison to other caches
        * most modern hit rates are >=95%
    * L2
        * second level CPU cache
        * 7ns read
        * larger than L1 and therefore more latency
    * L3 and L4
        * third and fourth level CPU caches
        * not all processors will have this
    * main memory (DRAM)
        * 100 ns