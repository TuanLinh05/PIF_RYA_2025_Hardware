PIF_RYA_2025_Hardware


1. Tổng quan hệ thống

Hệ thống bao gồm hai module chính được thiết kế để hoạt động phối hợp:

Module MCU (HBridgeMCU): Sử dụng vi điều khiển ARM Cortex-M3 làm bộ não trung tâm.

Module Driver (HBridgeDriver): Mạch cầu H công suất lớn dùng để điều khiển trực tiếp động cơ.

2. Thông số kỹ thuật chính

Vi điều khiển chính: STM32F103RCT6 (ARM Cortex-M3, 72MHz, 256KB Flash).

Giao thức truyền thông: Hỗ trợ CAN Bus thông qua IC Transceiver TJA1050.

Điện áp hoạt động: Nguồn động cơ (VDC) từ 12V đến 16V (Cách ly).

Cơ chế bảo vệ: * Tích hợp cầu chì tự phục hồi (Resettable Fuse) bảo vệ quá dòng.

Mạch bảo vệ điện áp VDC (VDC Protect).

Cách ly tín hiệu giữa khối điều khiển và khối công suất.

