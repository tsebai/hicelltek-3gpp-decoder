# Supported protocol scope

HiCellTek provides browser-based decoding for supported RRC and NAS structures across several mobile-network generations. The current public scope extends from earlier 3GPP releases through Release 18.

## Compatibility overview

| Generation | RRC scope | NAS scope | Primary public reference |
| --- | --- | --- | --- |
| GSM / GERAN | Supported structures | MM, GMM and SM supported structures | Applicable 3GPP GERAN specifications |
| UMTS / UTRA | Supported structures | MM, GMM and SM supported structures | Applicable 3GPP UTRA specifications |
| LTE / E-UTRA | Supported structures | EPS EMM and ESM supported structures | TS 36.331 and TS 24.301 |
| 5G NR / NG-RAN | Supported structures | 5GMM and 5GSM supported structures | TS 38.331 and TS 24.501 |

## Official specifications

- [3GPP TS 38.331: NR Radio Resource Control](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3197)
- [3GPP TS 36.331: E-UTRA Radio Resource Control](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=2440)
- [3GPP TS 24.501: NAS protocol for 5GS](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3370)
- [3GPP TS 24.301: NAS protocol for EPS](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=1072)

## Required decoding context

RRC payloads encoded with UPER are not self-describing. A useful decoding request includes:

1. The hexadecimal PDU without the capture-file or DIAG header.
2. The radio technology.
3. RRC or NAS protocol selection.
4. The exact logical channel for RRC when required.
5. The direction and release context when the capture source provides them.

Supported-channel detection can assist when the input contains enough context. It must not replace authoritative metadata from the capture when several grammars could accept the same bit sequence.

## Nested LTE to NR structures

For supported EN-DC messages, HiCellTek can detect and expand an NR configuration container nested in an LTE RRC message. This is useful when an LTE `RRCConnectionReconfiguration` carries an NR `CellGroupConfig` such as `nr-SecondaryCellGroupConfig-r15`.

## Boundaries

- Ciphered NAS contents require the relevant deciphering context before their protected payload can be interpreted.
- A capture header is not part of the RRC or NAS PDU and should be removed before decoding.
- Malformed, truncated, metadata-incoherent or unsupported frames may be rejected deliberately.
- Support through Release 18 does not imply that every optional extension or vendor-specific structure is implemented.

The proprietary engine is not distributed through this repository.
