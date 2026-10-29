# Sushant Mishra

Electrical engineering student at DTU, working toward the semiconductor industry. The reason is simple: everything else gets built on top of silicon.

Most of what I build sits on one question, asked from both ends: what does ML need from the hardware, and what can the hardware do for ML? Digital design and computer architecture on one side, models that have to run somewhere real on the other. They are not a pivot from one to the other. They run in parallel, and each keeps making the other make more sense.

## Pinned

**[e-hvgp](https://github.com/sushant-mishra-dtu/e-hvgp)** — A RISC-V Vector (RVV 1.0) core in plain Verilog-2001. Vector units are where ML-shaped arithmetic actually runs, and quantized inference is full of widening and narrowing ops that produce register groups of different sizes from the same instruction stream. The question the core was built to test: if vector-register-file bank placement is chosen per group from EMUL/LMUL/SEW at rename time, do those mixed-width bank conflicts go down? Two builds differ in exactly one module, produce byte-identical architectural results, and are compared by counters. v1 does not beat the baseline. The result is negative, reproducible, and the cause is isolated to a design constraint. Xcelium for simulation, Vivado for synthesis.

**[NVIDIA-NeMo/labs-OO-Agents](https://github.com/NVIDIA-NeMo/labs-OO-Agents)** — Upstream contributor to NVIDIA's object-oriented agent framework ([merged and open PRs](https://github.com/NVIDIA-NeMo/labs-OO-Agents/pulls?q=is%3Apr+author%3Asushant-mishra-dtu)). The first fix we landed was a cross-platform encoding bug: skill instruction files were read with the platform default encoding, which is UTF-8 on Linux and cp1252 on Windows, so the same file gave the model different instructions depending on the OS. Since then: closing storage connections when a commit fails, tolerating a malformed MCP token cache, decoding subprocess output safely, and writing trajectory JSON as UTF-8. Each one lands with a regression test.

**[coworkAI](https://github.com/sushant-mishra-dtu/coworkAI)** — An enterprise AI platform split into two services: a Core Platform for document-grounded team chat, agent-to-agent calls and MCP tools, and an LLM Configurator that routes models through LiteLLM and enforces rate limits and PII guardrails. Built end to end with Sampoorn Nagpal — both FastAPI services, ChromaDB retrieval, model routing, JWT auth and the React + Vite frontend.

**[Real-Time-Conversational-AI-Commentator](https://github.com/sushant-mishra-dtu/Real-Time-Conversational-AI-Commentator)** — The systems end of edge inference: a 7B speech model (PersonaPlex, Q4_K) running full-duplex on a consumer AMD GPU through Vulkan/ROCm, behind a FastAPI orchestrator with a server-authoritative state machine, VAD, an AudioMux that arbitrates two voices into one stream, and lean RAG over SQLite + FAISS for tool-augmented stats retrieval. React front end that acts as a dumb mirror.

**[ADAS](https://github.com/sushant-mishra-dtu/ADAS)** — Uses the accelerator already in everyone's pocket. Driver assistance for India's chaotic, unstructured traffic that runs entirely on the phone's NPU/GPU through TFLite, with CameraX feeding frames in Kotlin. No cloud, because the road doesn't wait for a round trip.

**[FPGA-Accelerated-Edge-Intelligence-System](https://github.com/sushant-mishra-dtu/FPGA-Accelerated-Edge-Intelligence-System)** — Inference moved into logic. A VHDL pipeline on a PYNQ-Z2 (Zynq-7020) with an ESP32-S3 host: UART frame parser, threshold detector, FSM classifier, 8-sample pattern matcher. The classifier is deliberately simple; the point was a deterministic pipeline and finding where the time actually goes. Four GHDL testbenches, ~57 µs per frame end to end in simulation, of which the FPGA takes three clock cycles. The rest is UART. SemiXthon 2026, Digital Design & VLSI track.

## Also on the bench

**[ARUNA](https://github.com/sushant-mishra-dtu/ARUNA---Aerial-Real-time-Unsupervised-Neural-Anomaly-detector)** — An LSTM autoencoder that watches a UAV's MAVLink telemetry and flags GPS spoofing, packet injection, and replay. Trained on normal flight only, so it catches attacks it has never seen, and it says which channel was hit. Quantized to int8 and benchmarked through ONNX.

**SIH-26168** (private team repo) — One continuously running Invariant EKF on SE₂(3) for GNSS-denied dead reckoning, with a learned speed head exactly where the physics runs out, NHC/ZUPT/ZARU constraints, and HMM map matching over an offline OSM graph. All on a phone IMU at 125 Hz in an Android operator app. Smart India Hackathon 2026.

## Currently

Building [NoSlack Labs](https://noslacklabs.com) with Sampoorn Nagpal: an independent engineering lab for FPGAs, embedded hardware and robotics.

Working on the state-augmented fix for E-HVGP v2, keeping PRs flowing into NeMo, and looking for RTL, digital design, or FPGA internships.

[NoSlack Labs](https://noslacklabs.com) · [Portfolio](https://sushant-mishra-dtu.github.io/Portfolio/) · [LinkedIn](https://www.linkedin.com/in/sushant-mishra-dtu)
