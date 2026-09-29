# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| adasind_062370.jpg — các đối tượng reference chưa ghép | local_quality ghi 2 missing_annotation: R5 ThreeWheeler và R8 Truck. | Cần xác định đây có phải hai vật riêng thuộc phạm vi H≥40 hay không trước khi thêm nhãn. Với R5, soát quan hệ với L6/R7 để tránh thêm trùng; với R8, kiểm tra ảnh gốc và ignore. | Ảnh gốc/crop R5 và R8, overlay L/R/M, dòng conflicts và finding tương ứng, quyết định theo R01–R04 và R09. |
| adasind_117120.jpg — phân loại phương tiện | local_quality ghi 1 extra_annotation ở L3 Bus. Chọn thêm 2 cụm bất đồng class trong findings: L7/R2 Car ↔ M1 Truck và L5/R4 ThreeWheeler ↔ M7 Truck. Hai cụm này là ca cần review, không tự cộng thành 4 lỗi độc lập. | Có thể thay đổi cách diễn giải thiếu/thừa và quyết định bên nào cần sửa. L3 Bus là xe xa cần xem rõ bằng chứng; hai cụm còn lại cần phân biệt class và hình học. | Ảnh gốc/crop rõ vật, model_compare.html, conflicts, cặp dòng LR_noM/M_only liên quan, rule R04 và kết quả phân xử. |

**Giới hạn:** Ba frame không đại diện cho toàn bộ camera hoặc bốn camera SVM. Frame và đối tượng có thể phụ thuộc nhau; nhiều dòng findings có thể mô tả cùng một vật qua các vòng hoặc qua các cell. Teaching reference chưa phải gold set đã phê duyệt. Vì vậy kế hoạch này chỉ ưu tiên công việc review, không ước lượng tỷ lệ lỗi triển khai. Frame adasind_086220.jpg vẫn cần xử lý riêng khác biệt truncated L2/R1 và hai box bị báo thừa theo báo cáo hiện có.

## Chuyển sang kế hoạch bốn camera giả lập

45_sampling_plan.csv phân bổ mỗi camera front, rear, left, right gồm 20 frame normal và 30 frame hard: 50 frame/camera, tổng 200; trong đó normal là 80 và hard là 120. Khi có dữ liệu thật, kiểm tra đủ tám ô camera × normal/hard, không trùng camera/frame ID và giữ camera ID, timestamp, phiên ghi cùng lý do chọn từng mẫu.

Trong từng ô, chọn từ nhiều phiên và cảnh khác nhau, tránh lấy hàng loạt frame liên tiếp của cùng một tình huống rồi coi là những ca độc lập. Ghi nhóm cảnh/sự kiện để nhận biết phụ thuộc; khi cần khảo sát seam, giữ các cặp đồng bộ và ghi rõ quan hệ giữa chúng. Soát độ phủ ánh sáng, che khuất, mép ảnh, loại phương tiện và thân xe ego theo dữ liệu thực sự có, không khẳng định đã thu đủ tình huống khi mới lập kế hoạch.

Phân bổ ưu tiên hard case giúp tìm vấn đề cần soi nhưng làm mẫu khác phân bố vận hành. Chưa có dữ liệu nguồn, thiết kế lấy mẫu đại diện và xác suất chọn mẫu nên không dùng tỷ lệ lỗi trong 200 frame này làm tỷ lệ lỗi của 50.000 frame. Muốn đo tỷ lệ chung cần một kế hoạch đánh giá phù hợp và reference đã được review, phân xử theo 46_gold_set_plan.md.