# Filesystem

## Prefetch
The filesystem workload often loads a large amount of file data sequentially. This file read too large to fit in the cache, or it is often read only once, so the cache is not efficientively used.
Prefetching is used to solve this problem. Filesystem detects sequencial read from currently, and previously I/O offset. After that, the filesystem predicts the continuation of the sequential read and executes the reading of the disk before the request of the application. The data acquired here is held in the cache, and the read request from the application is processed by a cache hit.
If prefetching works well, the application performance will be greatly improved. However, unless it works well, unnecessary I/O is issued, and the cache area becomes dirty, which degreades the application performance. Normally, the filesystem provide the tuning methods for prefetch as needed.
