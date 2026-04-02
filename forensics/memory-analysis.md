# Memory Analysis Report

**Part of Candor Labs** | Forensics Case Study

I performed memory forensics on a compromised Windows system using **Volatility 3** to investigate potential credential dumping and process injection.

## Tools Used
- Volatility 3
- Sysmon logs (for correlation)
- Flare-VM analysis environment

## Analysis Steps

1. Acquired memory dump from the target Windows 11 endpoint.
2. Identified running processes and checked for anomalies in `lsass.exe`.
3. Scanned for injected code and hollowed processes.
4. Extracted credentials and command history from memory.
5. Correlated findings with Sysmon logs for timeline reconstruction.

## Key Findings
- Detected suspicious access to LSASS process memory.
- Identified signs of credential dumping (MITRE T1003.001).
- Found evidence of process injection in legitimate system processes.

## Challenges & Solutions
- Large memory dump size → Used targeted Volatility plugins instead of full scan.
- False positives in process listing → Cross-referenced with Sysmon Event ID 10 (Process Access).

## Lessons Learned
- Memory forensics is powerful for detecting techniques that leave minimal disk artifacts.
- Combining Volatility with Sysmon provides strong context and reduces analysis time.
- Proper documentation of findings is critical for incident reporting.

**Status**: Completed lab exercise — techniques reusable for future investigations.
