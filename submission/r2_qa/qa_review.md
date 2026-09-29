# QA review · B3-center

Mã khóa: D96E-623D

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_167700.jpg | L6 | R03 | Theo finding QA đã ghi, box Bike gộp người ở mép phải đang dắt xe đạp với xe. Đề nghị tách một box Pedestrian và một box Bike, bám phần nhìn thấy. Quy tắc gộp rider chỉ áp dụng khi người ngồi trên xe. Chưa sửa bản đã khóa. |
| adasind_167700.jpg | L7 | R03 | Theo finding QA đã ghi, box Bike gộp người áo sọc đi bộ cạnh xe đạp chở hàng. Đề nghị tách người và xe thành Pedestrian và Bike theo R03, đồng thời kiểm tra lại ranh giới từng đối tượng trên ảnh gốc. |
| adasind_167700.jpg | L5 | R03, R04 | Finding hiện ghi nhãn ThreeWheeler trên vùng người áo xanh nhạt và xe đạp, chưa thấy phương tiện ba bánh tương ứng. Đề nghị annotator kiểm tra lại hình ảnh và quan hệ người–xe; nếu xác nhận người đang dắt xe thì dùng Pedestrian và Bike tách riêng. |
| adasind_212280.jpg | L3 | R04 | Nhãn Car bao phương tiện chở khách lớn bị cắt ở mép trái. Cần phân xử van chở người hay minibus trước khi đổi sang Bus; phần xe nhìn thấy chưa đủ để chốt chỉ từ kích thước box. Giữ trạng thái chưa xác nhận và đề nghị QA xem ảnh gốc. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
