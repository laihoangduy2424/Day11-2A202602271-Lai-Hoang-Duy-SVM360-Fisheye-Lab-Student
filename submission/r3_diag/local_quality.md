# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `18653f605eba9f18e2378ca818779faa33963b5e9f411dde20014121e8625842`; slice `B2-center`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_062370.jpg, adasind_086220.jpg, adasind_117120.jpg. Frame thiếu trong export: không.
TP=18; FP=3; FN=2; số lần đối chiếu=23; mean IoU của TP=0.862.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.783 | 0.964 | 0.957 |
| precision | 0.857 | 0.612 | 0.000 |
| recall | 0.900 | 0.643 | 0.000 |
| jaccard | 0.783 | 0.589 | 0.000 |
| dice | 0.878 | 0.624 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 7 | 1 | 0 | 0.957 | 0.875 | 1.000 | 0.875 | 0.933 |
| Bus | 0 | 1 | 0 | 0.957 | 0.000 | 0.000 | 0.000 | 0.000 |
| Car | 4 | 1 | 0 | 0.957 | 0.800 | 1.000 | 0.800 | 0.889 |
| Pedestrian | 1 | 0 | 0 | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| ThreeWheeler | 6 | 0 | 1 | 0.957 | 1.000 | 0.857 | 0.857 | 0.923 |
| Truck | 0 | 0 | 1 | 0.957 | 0.000 | 0.000 | 0.000 | 0.000 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_062370.jpg | 7 | 0 | 2 | 0.778 | 1.000 | 0.778 |
| adasind_086220.jpg | 5 | 2 | 0 | 0.714 | 0.714 | 1.000 |
| adasind_117120.jpg | 6 | 1 | 0 | 0.857 | 0.857 | 1.000 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Bus | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 7 | 0 | 0 | 0 | 0 | 0 | 0 |
| Bus | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Car | 0 | 0 | 4 | 0 | 0 | 0 | 0 |
| Pedestrian | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| ThreeWheeler | 0 | 0 | 0 | 0 | 6 | 0 | 1 |
| Truck | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| <extra> | 1 | 1 | 1 | 0 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
