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

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: TODO
- Cách sửa và ai nhận việc (`owner`): TODO
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): TODO
