# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_062370.jpg
- L1+R1 mid ATTRIBUTE
- R5 center MISSING
- R8 center MISSING
## adasind_086220.jpg
- L2+R1 mid ATTRIBUTE
- L5 center SPURIOUS
- L6 center SPURIOUS
## adasind_117120.jpg
- L3 center SPURIOUS

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 13 | 11 | 2 | 3 |
| mid | 6 | 6 | 0 | 0 |
| edge | 1 | 1 | 0 | 0 |
