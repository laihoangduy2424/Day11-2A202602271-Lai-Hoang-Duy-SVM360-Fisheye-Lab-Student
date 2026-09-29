# Escalation ticket

## Ticket 1

- **Frame:** adasind_117120.jpg, slice B2-center; L7/R2 Car và M1 Truck nằm cùng vùng phương tiện. L7 có x=479.1, y=874.2, w=153.5, h=124.8; M1 có x=478.4, y=870.9, w=154.1, h=127.6 theo findings hiện tại.
- **Ảnh chụp:** Dự kiến submission/screenshots/117120_L7_R2_M1_class.png. Cần chụp ảnh gốc kèm overlay nhìn rõ phương tiện, class và các box liên quan; ảnh chưa được bổ sung vào repo.
- **Expected impact:** Nếu không phân xử, chênh lệch cùng một phương tiện có thể bị diễn giải thành một ca model bỏ sót và một ca model tạo box giả. Điều này ảnh hưởng cách giải thích LR_noM/M_only và việc phân công sửa nhãn hay xử lý model. Chưa khẳng định model hoặc reference sai trước khi kiểm tra ảnh.
- **Owner:** qa, phối hợp người phụ trách guideline khi R04 chưa đủ để xác định loại xe từ phần nhìn thấy.
- **Recommendation:** Đối chiếu ảnh gốc theo R04 và xác nhận đây là van chở người, xe con hay xe tải. Nếu Car đúng thì giữ nhãn L/R, ghi nhận sai class model và đề nghị ai_team xem xét; nếu L/R sai thì ghi bằng chứng và quyết định sửa có kiểm soát; nếu chưa đủ thông tin thì giữ pending, không tự đổi class. Liên kết hai dòng r3_diag L7+R2 và M1 trong findings thay vì coi là hai nguyên nhân độc lập.

**Trạng thái:** Đã soạn nội dung đề nghị phân xử; chưa có bằng chứng gửi cho người nhận và chưa có kết luận. findings đã có action=escalate cho các dòng liên quan. Sau khi thực sự chuyển ticket, cập nhật entry tương ứng trong decision log thành escalated; không ghi resolved khi chưa có phản hồi.
