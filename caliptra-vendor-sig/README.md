# Caliptra FW vendor signatures

Vendor ECC key0 + LMS key0 signatures of the Caliptra FW bundle, one folder per
Caliptra RT version. They depend on the Caliptra FW version (FMC/RT TOC), not on
the platform.

Each `vendor_sig_ecc_key0_lms_key0.bin` is 1716 bytes: ECC sig (96) + LMS sig
(1620), the same layout as `ImageSignatures`. It is extracted from offset 1936 of
the signed caliptra-fw.bin, and it is valid only for an image whose vendor TBS
(header bytes 5520..5636) matches the digest below.

Use with the caliptra-sw builder: `--vendor-sig-override <file>`.

| Folder | Extracted from | FMC version | RT version | Vendor TBS SHA384 (prefix) |
|---|---|---|---|---|
| rt-1.2.1 | bmc-pb ec1e5c2 ast2700a2/caliptra-fw.bin | 0x0 | 0x0 | `73848b7ef7a28c96` |
| rt-1.2.5 | ast2700a2/caliptra-fw-ver-1p2p5.zip:caliptra-fw.bin | 0x885 | 0x1020005 | `57a6cdafa0450247` |
| rt-1.3.0 | bmc-pb 2d615ea ast2700a2/caliptra-fw.bin | 0x8c0 | 0x1030000 | `e43472605c685aa5` |

All signatures were verified with `socsec/tools/scripts/cptra_img_sig_ver.py`
against their source image.
