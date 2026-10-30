# Practical Investigation — Nmap Host and Service Assessment

## 1. Objective

Assess the network visibility of explicitly assigned lab hosts using Nmap, then interpret the results without treating service exposure as proof of a vulnerability.

## 2. Authorization and scope

- **Environment:** Assigned Ubuntu and Windows lab virtual machines.
- **Target scope:** Use only the IP addresses and ranges specified by the lab instructions.
- **Safety boundary:** Do not scan public, third-party or unrelated networks. Confirm the target list before each run.
- **Execution record:** Record the operator, date/time, host running Nmap and Nmap version.

## 3. Methodology

### Phase A — Host discovery

Use host discovery to determine which in-scope systems respond to the selected discovery probes:

```bash
nmap -sn <authorized-target-or-range>
```

Record the exact target expression and discovery result. A host that does not respond may still be active if a firewall or network policy blocks discovery probes.

### Phase B — Port-state assessment

Choose the scan type permitted by the lab and the privileges available:

```bash
nmap -sS <authorized-target>
nmap -sT <authorized-target>
```

- `-sS` performs a TCP SYN scan and generally requires suitable privileges.
- `-sT` uses the operating system's TCP connect call.

Do not run both automatically; select the method required by the exercise and record the reason.

### Phase C — Service identification

Where authorized, use service/version detection:

```bash
nmap -sV <authorized-target>
```

Record the exact service and version strings returned. Nmap's identification is a probe-based estimate and may be incomplete or ambiguous.

### Phase D — Output preservation

```bash
nmap <same-authorized-options> -oN scan-results.txt -oX scan-results.xml <authorized-target>
```

Use the actual command and filenames from the run. Do not replace the command record with a generic example when documenting an executed scan.

## 4. Results record

Complete this table from the original output. Leave a field out rather than guessing.

| Field | Recorded value |
|---|---|
| Lab target | Actual assigned host/IP |
| Date and time | Actual execution timestamp |
| Scanner / Nmap version | Recorded version |
| Exact command | Copied from command history |
| Host discovery result | Actual output |
| Port and state | Actual output |
| Service / version | Actual output |
| Output artifacts | Actual filenames |
| Constraints | Firewall, privileges, routing or scan limitations |

## 5. Technical interpretation

Interpret port states carefully:

- **open:** An application is accepting connections on that port at the time of the scan.
- **closed:** The host responded, but no application was listening on that port.
- **filtered:** Nmap could not determine whether the port was open because packet filtering or another network condition prevented a clear response.
- **open|filtered:** The probe received no response that could distinguish an open service from filtering; this is common in some UDP scan conditions.

An open port is an exposure observation, not a vulnerability finding. A defensible vulnerability assessment needs additional evidence, such as validated software/version details, configuration context and a relevant security advisory or test result.

## 6. Correlation and limitations

If a packet capture is available, correlate its timestamp and target with the Nmap run. Identify the probes and responses actually visible in the capture. Note that capture location, offloading, packet loss, firewall behaviour and timing can affect what is observed.

## 7. Evidence checklist

- Original command or terminal capture
- Normal output file, if generated
- XML output file, if generated
- Target and time-window record
- Related packet capture, if collected
- Short interpretation tied to the observed output

## 8. Conclusion

Write the conclusion only after reviewing the original scan output. State what hosts, ports and services were observed, what could not be determined, and what further authorized validation would be required. Do not invent results, counts, versions or vulnerabilities.
