# Voice Service Monitoring Dashboard

**Time Range**: Last 60 minutes | **Refresh Rate**: 30 seconds

---

## 1. Overall Service Health

| Metric                       | Current Value | Target   | Status |
| ---------------------------- | ------------- | -------- | ------ |
| **Mean Opinion Score (MOS)** | `4.31`        | `> 4.2`  | ✅ OK  |
| **Active Voice Sessions**    | `152`         | N/A      | -      |
| **WebSocket Error Rate**     | `0.05%`       | `< 0.1%` | ✅ OK  |

---

## 2. Real-Time Network Quality (Time Series)

This section visualizes the core metrics affecting user-perceived audio quality over the last hour.

### MOS & Jitter

```mermaid
Mean Opinion Score (MOS)
5.0 ┤
4.5 ┤             ╭╮
4.0 ┤      ╭╮     ││
3.5 ┤ ╭────╯╰╮____╯╰──
3.0 ┤─╯      ╰╮
    └──────────────────
      -60m  -45m  -30m

Jitter (ms)
 40 ┤
 30 ┤      ╭╮
 20 ┤   ╭──╯╰╮
 10 ┤ ╭─╯    ╰───────
  0 ┤─╯
    └──────────────────
      -60m  -45m  -30m
```

### Packet Loss & Round-Trip Time (RTT)

```
Packet Loss (%)
1.5 ┤
1.0 ┤
0.5 ┤         ╭─╮
0.0 ┤─┬───┬───╯ ╰───
    └──────────────────
      -60m  -45m  -30m

Round-Trip Time (ms)
200 ┤
150 ┤       ╭╮
100 ┤   ╭───╯╰╮
 50 ┤ ╭─╯     ╰─────
  0 ┤─╯
    └──────────────────
      -60m  -45m  -30m
```

---

## 3. Backend & Dependency Performance

### External API Latencies (p95)

| Service                     | Current Latency | Target    | Status |
| --------------------------- | --------------- | --------- | ------ |
| Google Speech-to-Text (STT) | `480ms`         | `< 500ms` | ✅ OK  |
| Amazon Polly (TTS)          | `455ms`         | `< 500ms` | ✅ OK  |
