# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B2 | MISSING | 9 |
| center | B2 | SPURIOUS | 15 |
| center | B3 | BOX_GEOMETRY | 1 |
| center | C0 | SPURIOUS | 1 |
| center | C0 | WRONG_CLASS | 1 |
| edge | B2 | SPURIOUS | 1 |
| edge | B3 | WRONG_CLASS | 1 |
| edge | C0 | WRONG_CLASS | 1 |
| mid | B2 | ATTRIBUTE | 2 |
| mid | B2 | MISSING | 3 |
| mid | B2 | SPURIOUS | 5 |
| mid | B3 | BOX_GEOMETRY | 1 |
| mid | B3 | WRONG_CLASS | 1 |
| mid | C0 | MISSING | 1 |
| mid | C0 | SPURIOUS | 1 |

## Top defects
- SPURIOUS: 23 (ví dụ frame adasind_019560.jpg)
- MISSING: 13 (ví dụ frame adasind_019560.jpg)
- WRONG_CLASS: 4 (ví dụ frame adasind_019560.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- **Nguyên nhân khả dĩ (why) và cơ sở:** SPURIOUS là nhóm xuất hiện nhiều nhất trong bảng hiện tại, nhưng đây là số dòng hiện tượng trong findings, chưa phải số lỗi độc lập đã xác nhận. Tại adasind_117120.jpg, M1 Truck cùng vùng với L7/R2 Car được ghi ở hai cell M_only và LR_noM. Trường hợp này cần kiểm tra bất đồng class theo R04 thay vì kết luận model tạo một xe giả. Tương tự, M6 Pedestrian nằm cùng vùng với L6/R5 Bike là ca cần soát quy tắc gộp rider theo R03. Chưa có đủ bằng chứng để quy mọi trường hợp cho domain shift hoặc khẳng định reference sai; các ca chưa phân xử tiếp tục giữ E5_unresolved.
- **Cách sửa và người nhận việc:** QA đối chiếu ảnh gốc, overlay và rule cho từng cụm box cùng vị trí, xác định chênh lệch nằm ở class, hình học, rider hay reference. Annotator chỉ sửa nhãn của mình khi đã xác nhận vi phạm luật; ca quyết định giữ cần giải thích rõ. Nếu vấn đề thuộc model thì đề nghị ai_team xem xét đầu ra và ánh xạ nhãn; nếu luật chưa đủ rõ thì chuyển guideline. Với adasind_086220.jpg L2/R1, báo cáo local_quality ghi mismatching_attributes và finding đã xác định cần sửa truncated theo R05; thao tác sửa và kết quả sau sửa vẫn phải được ghi nhận bằng export rework.
- **Bằng chứng:** Dẫn các dòng adasind_117120.jpg L7+R2, M1 và M6 trong submission/findings.csv; đối chiếu submission/r3_diag/model_compare.html, model_compare.md và local_quality_conflicts.csv. Áp dụng R03 cho rider và R04 cho phương tiện. Cần bổ sung ảnh chụp vùng L7/R2/M1 vào submission/screenshots/117120_L7_R2_M1_class.png; đây là đường dẫn dự kiến, ảnh chưa được xác nhận có trong repo.

