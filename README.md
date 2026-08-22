# AUTO PK — ThanLongItemConsolidator v1.6

Windows x64 build sửa riêng phép thử bán một vật phẩm trong cửa sổ **LỌC ĐỒ**.

## v1.6 stock RequestSellItem

- Re-scan đúng live `InstanceID` và giữ guard bán/quest-family.
- Gọi trực tiếp semantic nội bộ `NPCShop_SellItemTab.RequestSellItem(item)` qua bridge.
- Không dùng click tọa độ màn hình và không chiếm chuột người dùng.
- Chỉ báo PASS khi đúng instance đã chọn biến mất khỏi fresh bag scan.
- Verifier cấm đường mouse/direct packet, khóa đúng một stock dispatch và tự thử đột biến từng protected function definition.
- AUTO SELL, lọc đồ production, Auto PK, trade, route, Telegram và các primitive khác không đổi.

Windows CI dựng từ source v1.5 đúng SHA-256, áp patch v1.6 đúng SHA-256, chạy 13 logic tests + verifier + verifier self-test qua CTest trước khi publish EXE/DLL/source ZIP vào `dist/`.
