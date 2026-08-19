# Public examples

The examples in this directory are small, non-customer inputs intended to demonstrate the expected decoder context. They are not extracted from private HiCellTek repositories, production logs or customer captures.

## 5GMM Registration Reject

Hexadecimal PDU:

```text
7e004411
```

Expected context:

| Field | Value |
| --- | --- |
| Technology | 5G NR / 5GS |
| Protocol | NAS |
| Security context | Plain 5GMM message |
| Message | Registration Reject |
| 5GMM cause | 17, Network failure |

Byte outline:

| Byte | Meaning |
| --- | --- |
| `7e` | 5G mobility management extended protocol discriminator |
| `00` | Plain NAS security header context |
| `44` | Registration Reject message type |
| `11` | Cause value 17, Network failure |

Open the [HiCellTek online decoder](https://hicelltek.com/en/decoder/), select the 5G NAS workflow and paste the PDU.

## Interpretation boundary

The message confirms the reject cause carried by this PDU. It does not, by itself, identify the full operational root cause. A complete investigation should correlate the result with the preceding registration exchange, serving-cell conditions, subscriber context and core-network evidence.

Do not publish customer payloads, subscriber identifiers, security material or proprietary captures as examples.
