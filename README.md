# AUTO PK — ThanLongItemConsolidator v1.7

Windows x64 build sửa riêng phép thử bán một vật phẩm trong cửa sổ **LỌC ĐỒ**.

## v1.7 nested stock RequestSellItem

- Sửa đúng root cause runtime v1.6: `NPCShop_SellItemTab` là script của component con `SellItemTab`, không phải tên top-level cho `GUI.FindUI`.
- T1 tìm script root qua `MonoBehaviourExecutor.FindScriptUIRoots("NPCShop_SellItemTab")`; chỉ nhận đúng một root active thuộc cây `NPCShop` hiện hành.
- Gọi đúng overload stock `ExecuteScriptFunction(UIObject,string,object[])` → `RequestSellItem(liveItem)`.
- Không direct packet `200036`, không đọc/hard-code ShopID, không click chuột; vẫn re-scan đúng live `InstanceID` và fail-closed khi root thiếu/mơ hồ/sai shop.
- Protected-function audit giữ nguyên `SellBagItem`, AUTO SELL, lọc/vứt đồ, Auto PK, trade, route và Telegram.
- CI tái dựng từ source v1.6 đúng SHA-256, áp patch v1.7 đúng SHA-256, ép các `assert` luôn hoạt động trong MSVC Release, rồi chạy 13 logic tests + 2 verifier tests trước khi publish.
- Trạng thái runtime: **RUNTIME UNTESTED** cho tới live-client test đúng cặp EXE/DLL v1.7.

## v1.6 stock RequestSellItem

- Re-scan đúng live `InstanceID` và giữ guard bán/quest-family.
- Gọi trực tiếp semantic nội bộ `NPCShop_SellItemTab.RequestSellItem(item)` qua bridge.
- Không dùng click tọa độ màn hình và không chiếm chuột người dùng.
- Chỉ báo PASS khi đúng instance đã chọn biến mất khỏi fresh bag scan.
- Verifier cấm đường mouse/direct packet, khóa đúng một stock dispatch và tự thử đột biến từng protected function definition.
- AUTO SELL, lọc đồ production, Auto PK, trade, route, Telegram và các primitive khác không đổi.

Windows CI dựng từ source v1.5 đúng SHA-256, áp patch v1.6 đúng SHA-256, chạy 13 logic tests + verifier + verifier self-test qua CTest trước khi publish EXE/DLL/source ZIP vào `dist/`.
