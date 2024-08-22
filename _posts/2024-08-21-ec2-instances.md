---
layout: post
title: AWS EC2 Instance Types
---

"Amazon EC2 provides a wide selection of instance types optimized to fit different use cases. **Instance types comprise varying combinations of CPU, memory, storage, and networking capacity** and give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes, allowing you to scale your resources to the requirements of your target workload." -- AWS EC2

AWS EC2 instances form the backbone of cloud computing within AWS, providing the essential compute power that drives a wide range of AWS services, such as RDS (Relational Database Service), EMR (Elastic MapReduce), SageMaker, ECS (Elastic Container Service), and etc.

With hundreds of instance types available, it's challenging to memorize them all. This post provides a mental model for understanding the naming conventions, allowing you to quickly identify the general characteristics of an instance type at a glance. This knowledge will enable you to swiftly and confidently select an appropriate instance for a typical use case.

Example: fast launch choices of notebook instance in SageMaker Studio

| Instance Type | Instance Category | vCPU | GPU | Memory | Fast Launch |
|---------------|-------------------|------|-----|--------|-------------|
| ml.t3.medium | General purpose | 2 | 0 | 4 GiB | √ |
| ml.g4dn.xlarge | Accelerated computing | 4 | 1 | 16 GiB | √ |
| ml.m5.large  | General purpose | 2 | 0 | 8 GiB | √ |
| ml.c5.large  | Compute optimized | 2 | 0 | 4 GiB | √ |

The nomenclature for EC2 instance types follows the pattern `[family][generation][additional].[size]`, where each component represents instance family, instance generation, additional capabilities, and instance size, respectively. Other AWS services that use EC2 instance have their own specific prefixes, such as `ml` for SageMaker as shown in the example above, and `db` for RDS.

The following sections break down each component of an instance type.

## Instance Family

* General Purpose
  * a balance of compute, memory and networking resources, ideal for applications that use resources in equal proportions
  * use cases: web services, code repositories, etc.
  * examples: m (mnemonic: **m**edium), t (burstable - overall the instance has OK CPU performance; when the machine needs to process something unexpected, it can burst, and CPU can be very good. If the machine bursts, it utilizes "burst credits"; if all credits are gone, the CPU becomes back; if the machine stops bursting, credits are accumulated over time)

* Compute Optimized
  * ideal for compute bound applications that benefit from high performance processors
  * use cases: batch processing, media transcoding, high performance web servers, high performance computing (HPC), scientific modeling, dedicated gaming servers, ad server engines, machine learning inference, etc.
  * examples: c (mnemonic: **C**PU)

* Memory Optimized
  * deliver fast performance for workloads that process large data sets in memory
  * use cases: enterprise-class databases, in-memory cache, etc.
  * examples: r (mnemonic: **R**AM), u, x, z

* Storage Optimized
  * designed for workloads that require high, sequential read and write access to very large data sets on local storage; optimized to deliver tens of thousands of low latency, random I/O operations per second to applications
  * use cases: databases, shared file systems, high I/O computing
  * examples: i (mnemonic: **I**O), d, h

* Accelerated computing
  * use hardware accelerators, or co-processors, to perform functions (such as floating point number calculations, graphics processing, or data pattern matching) more efficiently than is possible in software running on CPUs
  * use cases: video rendering, remote visualization, streaming games, high performance computing (HPC), machine learning, deep learning
  * examples: g (mnemonic: **G**PU), p, trn, inf, dl, f, vt

  | instance types | GPU model |
  |----------------|-----------|
  | g2 | NVIDIA GRID K520 |
  | p2 | NVIDIA Tesla K80 (GPUDirect for peer-to-peer GPU communication) |
  | g3 | NVIDIA M60 |
  | p3 | NVIDIA Tesla V100 (NVLink for peer-to-peer GPU communication) |
  | g4ad | AMD Radeon Pro V520 |
  | g4dn | NVIDIA T4 |
  | trn1 | AWS Trainium |
  | inf1/2 | AWS Inferentia/Inferentia2 |
  | p4 | NVIDIA A100 (600GB/s peer-to-peer GPU communication with NVIDIA NVSwitch) |
  | g5 | NVIDIA A10G |
  | g5g | NVIDIA T4G |
  | p5 | NVIDIA H100 (900GB/s peer-to-peer GPU communication with NVIDIA NVSwitch) | 
  | g6 | NVIDIA L4 |

* HPC optimized
  * purpose built to offer the best price performance for running HPC workloads at scale
  * use cases: large, complex simulations, deep learning
  * examples: hpc

## Additional Info

* processors and architectures

  * Intel processors: generations of Sandy Bridge, Ivy Bridge, Skylake, Cascade Lake, Ice Lake, etc. Instance types have optional suffix of `i`.
    * m5: 3.1 GHz Intel Xeon Scalable processors (Skylake 8175M or Cascade Lake 8259CL)
    * m6i: 3.5 GHz 3rd Generation Intel Xeon Scalable processors (Ice Lake 8375C)
    * m7i: 3.2 GHz 4th Generation Intel Xeon Scalable processors (Sapphire Rapids 8488C)
    
  * AMD EPYC processors: since 2018, lower cost. Instance types have suffix of `a`.
    * m6a: 3.6 GHz 3rd generation AMD EPYC processors (AMD EPYC 7R13)
    * m7a: 3.7 GHz 4th generation AMD EPYC processors (AMD EPYC 9R14)
    
  * AWS Graviton processors: Arm architecture. Instance types have suffix of `g`.
    * m6g: Graviton2
    * m7g: Graviton3

* memory: DDR4, DDR5

* storage

  * EBS: Amazon Elastic Block Store, an easy-to-use, scalable, high-performance block-storage service designed for Amazon Elastic Compute Cloud. up to 40 Gbps of bandwidth

  * NVMe SSD: instance types have suffix of `d`, e.g. m6g.medium vs. m6gd.medium

* networking bandwidth

  * default

  * enhanced: instance types have suffix of `n`, ideal for network-intensive workloads such as backend servers, enterprise, gaming servers, and caching fleets applications, for example, up to 200Gbps of network bandwidth and up to 80 Gbps Amazon EBS bandwidth

## Instance Size

Instance sizes are calculated by different multiples of the corresponding instance type baseline. The number of multiples is indicated by micro, small, medium, large, and #xlarge.

Example:

| instance | vCPU | Memory (GiB) |
|----------|------|--------------|
| c5.large | 2 | 4 |
| c5.xlarge | 4 | 8 |
| c5.2xlarge | 8 | 16 |
| c5.4xlarge | 16 | 32 |
| c5.9xlarge | 36 | 72 |
| c5.18xlarge | 48 | 96 |
| c5.24xlarge | 96 | 192 |
| c5.metal | 96 | 192 |

| instance | vCPUs | GPUs | GPU memory |
|----------|-------|------|------------|
| p3.2xlarge | 8 | 1 | 16 |
| p3.8xlarge | 32 | 4 | 64 |
| p3.16xlarge | 64 | 8 | 128 |
| p3dn.24xlarge | 96 | 8 | 256 |

## References
- https://aws.amazon.com/ec2/instance-types/
- https://instances.vantage.sh