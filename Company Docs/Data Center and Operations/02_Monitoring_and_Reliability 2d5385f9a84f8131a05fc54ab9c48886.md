# 02_Monitoring_and_Reliability

# 5.2 Monitoring, Reliability & Shepherd

At FarmGPU, we view monitoring not as a set of dashboards, but as the operational backbone of the AI data path. Our reliability model is built specifically to exceed the **ClusterMax™ Evaluation Criteria**, ensuring that "random" hardware events never dictate the success of your training run.

## 1. Shepherd: The "Autonomous SRE"

Shepherd is FarmGPU’s proprietary reliability engine. It continuously audits the state of the cluster against the **ClusterMax™ Evaluation Criteria**, automating the transition from detection to remediation.

### The Unified Telemetry Fabric

- **GPU Failure Detection:** Real-time capture of **NVIDIA XID/SXID** events, SM occupancy, memory pressure, and **PCIe AER rates**.
- **Interconnect (RoCEv2):** Monitoring of link flaps, retry counters, and fabric-wide **NCCL collective timing**.
- **Data Plane:** BlueField-3 telemetry for NVMe queue depths, IOPS/throughput histograms, and DPU-offload health.
- **Physical:** PDU-level power draw, fan speeds, and multi-sensor thermal mapping (CPU, GPU, RAM, NIC, and Transceivers).

## 2. Passive Health Checks (The Safety Net)

Aligned with **ClusterMax™ Monitoring Standards**, Shepherd runs continuous passive checks to identify "failing" nodes before they become "failed" nodes.

- **GPU/Memory ECC Monitoring:** Real-time tracking of single-bit and double-bit ECC errors (via DCGM and EDAC) with automated node-cordoning upon crossing threshold.
- **Link Flap Detection:** Sub-millisecond monitoring of fabric stability; Shepherd automatically drains nodes exhibiting link degradation to prevent NCCL collective timeouts.
- **Thermal Drift Alerts:** Proactive detection of thermal anomalies in transceivers or GPUs, triggering automated power-capping or workload migration before throttling occurs.
- **"GPU Off the Bus" Detection:** Immediate capture of `NVML_ERROR_GPU_IS_LOST` or XID 79 events, with automated node isolation.

## 3. Active Health Checks

Idle nodes in the Farm undergoes regular "Active Diagnostic" suite:

- **Compute Validation:** NVIDIA DCGM Diag level 3 and 4
- **Stress Testing:** In house developed **GPU-Burn** validate thermal stability under maximum synthetic load.
- **Interconnect Validation:** Pairwise `ib_write_bw` and multi-node **NCCL All-Reduce** tests to verify that every node achieves >90% of theoretical fabric bandwidth.
- **Storage Throughput:** Validating Sustained GB/s-per-GPU from the Silo storage tiers to the GPU memory.

## 4. Managed Observability (Grafana)

FarmGPU bare metal customers will get a dedicated monitoring stack and a custom URL.

- **Cluster-Level:** Node availability, pending pod counts, and fabric-wide goodput.
- **Node-Level:** Granular GPU SM utilization, power draw, and temperature heatmaps.
- **Job-Level:** Integration with **Slurm (sacct)** and **Kubernetes** to correlate infrastructure metrics directly with training loss curves.