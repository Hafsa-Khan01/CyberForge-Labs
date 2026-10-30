# Week 01 — Evidence Register

This register identifies the source evidence package and the subset currently published in the repository. It is intended to make review traceable without implying that every source image has been uploaded.

## 1. Source package inventory

The supplied source archive was inventoried as 46 images:

| Source group | Images | Description |
|---|---:|---|
| Labs 03–08 result cards | 6 | Learner assessment result screenshots |
| Kali desktop | 1 | Kali Linux running in VirtualBox |
| VirtualBox setup archive | 7 | VM settings, adapter, shared-folder and related configuration views |
| Wireshark practical archive | 32 | Packet lists, packet details and protocol/stream analysis views |
| **Total** | **46** | |

## 2. Public repository upload status

| Evidence group | Published | Repository location |
|---|---:|---|
| VirtualBox/Kali setup | 8 screenshots | [VirtualBox-Kali-Lab/Evidence](VirtualBox-Kali-Lab/Evidence/) |
| Windows-host Wireshark practicals | 27 screenshots | [Windows-Wireshark/Evidence](Windows-Wireshark/Evidence/) |
| Lab result cards | 6 screenshots | [Wireshark-SOC-Labs/Evidence](Wireshark-SOC-Labs/Evidence/) |
| **Published image total** | **41** | |

Five images from the 46-image source package are not currently included in the public repository. The published repository is therefore a reviewed subset, not a byte-for-byte copy of the source archive.

## 3. Learner result-card record

| Lab | Exercise | Recorded score |
|---|---|---:|
| 03 | Identify the Attacker's IP | 89% |
| 04 | Follow TCP Stream | 90% |
| 05 | Follow TCP Stream — Part 2 | 100% |
| 06 | HTTP Plain-Text Credentials | 99% |
| 07 | FTP Brute-Force Detection | 100% |
| 08 | VoIP Call Analysis | 98% |
| **Arithmetic mean** | **Six result cards** | **96%** |

These percentages are transcribed from the learner's result-card screenshots. They are not a substitute for independent review of the underlying packet captures.

## 4. Evidence navigation

- [VirtualBox/Kali setup evidence](VirtualBox-Kali-Lab/Evidence/)
- [Windows-host Wireshark evidence](Windows-Wireshark/Evidence/)
- [Lab 03 result card](Wireshark-SOC-Labs/Evidence/Lab-03/)
- [Lab 04 result card](Wireshark-SOC-Labs/Evidence/Lab-04/)
- [Lab 05 result card](Wireshark-SOC-Labs/Evidence/Lab-05/)
- [Lab 06 result card](Wireshark-SOC-Labs/Evidence/Lab-06/)
- [Lab 07 result card](Wireshark-SOC-Labs/Evidence/Lab-07/)
- [Lab 08 result card](Wireshark-SOC-Labs/Evidence/Lab-08/)

## 5. Handling and privacy

- Preserve an untouched private copy of the original source archive.
- Review every image before public release; redact credentials, tokens, account identifiers, personal/payment information, host usernames, local paths and unrelated device details.
- Do not publish VM disks, saved-state files, private keys or unreviewed packet captures.
- Use only assigned training captures or explicitly authorised systems.
