## EFS Scale
- 1000s of concurrent NFS clients, 10GB+ /s throughput;
- Grow to Petabyte-scale network file system, automatically;

## Performance Mode (set at EFS creation time)
- **General Purpose (default)**: Latency-sensitive use cases (web servers, CMS, etc...)
- **Max I/O**: higher latency, throughput, highly parallel (big data, media processing);

## Throughput Mode
- **Bursting**: 1TB = 50MiB/s + burst of up to 100MiB/s;
- **Provisioned**: set your throughput regardless of storage size, ex:
	- 1GiB/s for 1TB storage;
- **Elastic**: Automatically scales throughput up or down based on your workloads;
	- Up to 3GiB/s for reads and 1GiB/s for writes;
	- Used for unpredictable workloads.