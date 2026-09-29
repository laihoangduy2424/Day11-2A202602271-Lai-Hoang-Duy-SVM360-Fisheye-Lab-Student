# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 13 | 2 | 3 | 7 | 10 | SPURIOUS (3) |
| mid | 6 | 0 | 0 | 3 | 5 | ATTRIBUTE (2) |
| edge | 1 | 0 | 0 | 0 | 1 | — |

## Nhận xét

Trong ba frame của slice B2-center, center có nhiều chênh lệch theo số tuyệt đối nhất: người gán nhãn thiếu 2 và thừa 3 đối tượng; model thiếu 7 và thừa 10. Ở mid, người không có chênh lệch thiếu/thừa trong bảng nhưng có 2 lỗi ATTRIBUTE; model thiếu 3 và thừa 5. Edge chỉ có 1 đối tượng reference, người không thiếu/thừa và model có 1 box thừa. Vì lượng đối tượng ở center, mid và edge lần lượt là 13, 6 và 1, không thể dùng số lỗi tuyệt đối để khẳng định center khó hơn các zone còn lại.

Một phần chênh lệch có thể liên quan đến ánh xạ class và quy tắc rider. Chẳng hạn, tại adasind_117120.jpg, model M1 Truck nằm cùng vùng với L7/R2 Car, còn M7 Truck nằm cùng vùng với L5/R4 ThreeWheeler. Vì thế một dòng LR_noM đi kèm M_only có thể là hai biểu hiện của cùng một bất đồng class, không nhất thiết là model vừa bỏ sót một vật vừa tạo một vật giả độc lập. Cần đối chiếu ảnh gốc, vị trí box và R03–R04 trước khi chốt nguyên nhân.

Biến dạng fisheye, ngưỡng kích thước, độ khít box và vùng ignore cũng là yếu tố cần kiểm tra, nhưng bảng thống kê hiện chưa chứng minh chúng là nguyên nhân. Báo cáo self-QC có cảnh báo ego_body và truncated cần đối chiếu với export hiện tại; không suy từ cảnh báo cũ rằng lỗi chắc chắn vẫn còn. Ba frame của một camera và rất ít mẫu edge không đủ để suy rộng ra toàn bộ ADASIND hoặc hệ bốn camera. Zone bán kính cũng không biểu thị trực tiếp khoảng cách tới xe.
