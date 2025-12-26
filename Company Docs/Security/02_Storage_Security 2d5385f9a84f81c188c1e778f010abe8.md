# 02_Storage_Security

## 4.2.1 Advanced Encryption Architecture

FarmGPU implements encryption **by default**, with no performance penalty and no dependency on application-level controls.

### Data at Rest — Self-Encrypting Drives (SEDs, TCG OPAL)

- **Hardware-Based Encryption:** All Solidigm NVMe SSDs deployed in FarmGPU infrastructure support **TCG OPAL 2.0** compliant self-encrypting drives (SEDs).
- **Always-On Encryption:** Data is encrypted transparently at the controller level and does not rely on OS or application configuration.
- **Zero Performance Impact:** Encryption is handled entirely within the drive controller, ensuring **no reduction in GPU, CPU, or I/O throughput**.
- **Strong Key Isolation:** Encryption keys never leave the device, preventing exposure through host compromise.

This approach ensures that data remains protected even in the event of physical access to drives.

### Data in Transit — DPU-Accelerated Encryption

FarmGPU secures inter-node and storage traffic using **hardware-offloaded encryption**.

- **DPU-Accelerated IPsec / TLS 1.3:**
    
    NVIDIA **BlueField-3 DPUs** offload encryption and decryption from host CPUs, protecting data in flight across the storage and AI fabric.
    
- **Line-Rate Security:**
    
    Encryption is performed at hardware speed, preserving full utilization of **400 Gbps and 800 Gbps** network fabrics.
    
- **Reduced Attack Surface:**
    
    By removing cryptographic processing from the host OS, DPUs reduce exposure to kernel-level attacks and misconfiguration.
    

This ensures secure communication between GPUs, storage systems, and cluster services without introducing latency or bottlenecks.

## 4.2.2 Media Sanitization & Data Destruction (IEEE 2883)

FarmGPU follows **standards-based media sanitization**, ensuring that data is irreversibly destroyed when no longer required.

- **IEEE 2883-2022 Alignment:**
    
    FarmGPU adheres to IEEE 2883 guidance for secure sanitization of solid-state storage devices.
    
- **Cryptographic Erase (CE):**
    
    Upon tenant offboarding, drive reassignment, or hardware retirement, FarmGPU performs **cryptographic erase** by destroying the media encryption keys on SEDs.
    
- **Instant and Verifiable:**
    
    CE renders all data permanently unrecoverable within seconds, without the wear or uncertainty associated with overwrite-based methods.
    

This approach enables:

- Secure multi-tenant reuse of hardware
- Compliance with enterprise and regulatory data-handling expectations
- Environmentally responsible lifecycle management of SSDs

## 4.2.3 Storage ISV Partner Security

FarmGPU works with **enterprise-grade storage ISVs** that implement security as a core design principle. Storage platforms are deployed using **vendor-recommended hardening and encryption configurations**, and validated through FarmGPU’s internal benchmarking and qualification process.

### VAST Data (Example)

VAST Data provides a unified storage platform designed for large-scale AI workloads, with security features embedded at the architecture level.

Key security characteristics include:

- **End-to-End Encryption:**
    
    Data is encrypted at rest and in transit using industry-standard cryptographic algorithms.
    
- **Key Management Integration:**
    
    Support for centralized key management and separation of duties.
    
- **Multi-Tenant Isolation:**
    
    Logical isolation mechanisms ensure separation between tenants, datasets, and workloads.
    
- **Secure Metadata Handling:**
    
    Metadata services are protected with the same security controls as data paths.
    
- **Operational Hardening:**
    
    Role-based access control (RBAC), audit logging, and secure administrative interfaces.
    

FarmGPU deploys VAST Data in accordance with documented best practices, ensuring encryption, access control, and isolation are consistently enforced.