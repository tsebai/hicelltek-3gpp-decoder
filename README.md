# HiCellTek Online 3GPP RRC & NAS Decoder

[Open the HiCellTek 3GPP decoder](https://hicelltek.com/en/decoder/)

HiCellTek is a browser-based decoder for isolated Layer 3 protocol data units from GSM, UMTS, LTE and 5G NR networks. It covers supported RRC and NAS structures from earlier 3GPP releases through Release 18.

The decoding engine is proprietary. This repository contains public documentation and examples only.

## What the online decoder provides

- GSM, UMTS, LTE and 5G NR workflows
- RRC and NAS decoding
- Supported structures through 3GPP Release 18
- Free single-frame RRC and NAS decoding in the browser, without signup or a daily product quota
- Programmatic API access and batch decoding in the Pro plan at EUR 29 per month
- Custom enterprise plans for higher-volume or organization-specific requirements
- Tree view, raw view and text export
- Supported-channel detection and assisted selection where enough context is available
- Expansion of supported LTE containers carrying nested NR configuration
- In-memory processing without retention of submitted frames

RRC UPER data is not self-describing. Accurate decoding depends on the technology, direction, release family and logical channel supplied with the PDU. When automatic detection is not possible, use the channel recorded by the capture source.

## Quick start

1. Paste the hexadecimal PDU.
2. Select GSM, UMTS, LTE or NR.
3. Select RRC or NAS.
4. Select the logical channel when required.
5. Decode and inspect the result.

Try it at [hicelltek.com/en/decoder/](https://hicelltek.com/en/decoder/).

## Access model

The browser interface is intended for interactive, single-frame RRC and NAS decoding. It has no daily product quota, while remaining protected by server-side abuse, concurrency, request-size and resource controls.

Automated or programmatic use must use the paid API. The Pro plan is EUR 29 per month and includes API and batch workflows; enterprise access is available on a custom basis. The free browser workflow is not an API licence and must not be automated or used to bypass the paid API controls.

## Minimal 5G NAS example

```text
7e004411
```

In the expected plain 5GMM context, the bytes represent:

- `7e`: 5G mobility management extended protocol discriminator
- `00`: plain NAS security header context
- `44`: Registration Reject message type
- `11`: 5GMM cause 17, `Network failure`

A decoded reject cause identifies what the network signalled. One message alone is not enough to establish a complete root cause. Correlate it with the registration procedure, radio conditions, preceding NAS exchanges and network-side evidence.

More examples and context are available in [examples/README.md](examples/README.md).

## HiCellTek or Wireshark?

Use [Wireshark](https://www.wireshark.org/docs/wsug_html_chunked/ChIOOpenSection) when you need to open a complete PCAP, preserve packet timing and correlate several protocols in one trace.

Use HiCellTek when you need to inspect an isolated RRC or NAS PDU quickly, with a structured tree and raw output, without first building a complete capture workflow.

The approaches are complementary. Wireshark provides capture-wide context; HiCellTek provides a focused single-PDU workflow.

## Supported protocol references

The public compatibility scope is documented in [docs/supported-protocols.md](docs/supported-protocols.md). Relevant official specifications include:

- [3GPP TS 38.331: NR Radio Resource Control](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3197)
- [3GPP TS 36.331: E-UTRA Radio Resource Control](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=2440)
- [3GPP TS 24.501: 5GS NAS](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3370)
- [3GPP TS 24.301: EPS NAS](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=1072)

## Validation boundary

A bounded validation corpus contains 63,375 cases:

- 36,904 expected decodes
- 26,471 expected safe rejections
- Zero oracle or transport failures within that bounded scope

These results describe the cited corpus. They do not guarantee universal decoding of every frame, optional extension, vendor-specific structure, malformed input or message lacking its required channel and release context. See [docs/privacy-and-validation.md](docs/privacy-and-validation.md).

## Related resources

- [HiCellTek online 3GPP decoder](https://hicelltek.com/en/decoder/)
- [How to decode 5G NR RRC messages online](https://dev.to/hicelltek/how-to-decode-5g-nr-rrc-messages-online-2oo9)
- [TelecomHall: 3GPP Messages Decoder discussion](https://www.telecomhall.net/t/3gpp-messages-decoder/12258/15)

## Repository scope

This repository does not contain the decoding engine, ASN.1 implementation, production configuration, binaries, API credentials, private captures or validation corpus. It is not an open-source release of the HiCellTek decoder.
