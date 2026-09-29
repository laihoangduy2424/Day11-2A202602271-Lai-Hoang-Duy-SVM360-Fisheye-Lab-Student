# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

## 1. Một vật xuất hiện ở seam của hai camera

Một vật xuất hiện đồng thời trên hai camera không mặc nhiên là lỗi DUPLICATE. Nếu đầu ra là detection trên từng ảnh raw, mỗi camera có hệ tọa độ và phần nhìn thấy riêng nên hai box có thể cùng hợp lệ. Cần policy riêng quy định giữ các quan sát theo camera hay hợp nhất thành một đối tượng ở tầng sau. Không xóa một box hoặc gộp identity chỉ vì cùng class và cùng xuất hiện ở rìa ảnh. Nếu yêu cầu đầu ra hợp nhất, cần kiểm tra đồng bộ thời gian, calibration và bằng chứng đối chiếu trước khi quyết định.

## 2. Track ID, keyframe và Outside

Trên cùng một camera, giữ track ID khi có đủ bằng chứng đó vẫn là cùng một vật qua các frame. Thêm keyframe tại các thời điểm hình học, hướng di chuyển hoặc mức che khuất thay đổi khiến nội suy không bám đúng phần nhìn thấy; kiểm tra cả các frame giữa hai keyframe. Đánh dấu Outside khi vật ra khỏi trường nhìn theo quy định task; không đồng nhất việc bị vật khác che với việc ra ngoài khung hình. Ca mất dấu hoặc tái xuất hiện cần xử lý theo policy, không nối chỉ vì đối tượng mới có ngoại hình tương tự.

Trước khi nối track qua hai camera, cần timestamp đã kiểm chứng đồng bộ, camera ID, calibration nội/ngoại camera, vùng chồng tương ứng, bằng chứng hình ảnh/chuyển động và quy định identity đầu ra. Nếu thiếu bằng chứng, giữ các quan sát riêng và chuyển phân xử. Bài ADASIND hiện tại chỉ dùng một camera, nên nội dung này là nguyên tắc thiết kế, chưa phải kết quả thực nghiệm tracking bốn camera.

## 3. Nhìn lại một ca bất đồng

Ca tôi chọn xem lại là adasind_117120.jpg L3 Bus. Báo cáo local_quality đánh dấu đây là extra_annotation, trong khi findings ghi M8 Car và M10 Truck nằm cùng vùng. Việc reference không có box tương ứng chưa đủ để kết luận L3 phải bị xóa, và việc model có hai class khác nhau cũng không xác nhận Bus là đúng. Tôi chưa có đủ cơ sở khẳng định nhãn của mình đúng trong ca này; đây là bất đồng cần kiểm tra ảnh gốc, ngưỡng kích thước và R04.

Hiện findings giữ E5_unresolved với hướng xử lý escalate; chưa có bằng chứng phân xử hoặc sửa nhãn nên tôi giữ nguyên bản đã khóa. Nếu làm lại, tôi sẽ chụp crop rõ phương tiện và ghi căn cứ chọn class ngay khi gán nhãn, đối chiếu rule trước khi mở reference và gom các box cùng vị trí để review chung. Cách này giúp phân biệt chênh lệch do class với thiếu/thừa thực sự, đồng thời tránh sửa theo reference hoặc model khi chưa xác minh ảnh.

## 10. Phần còn cần thao tác thật

1. Bổ sung ít nhất hai screenshot thật vào submission/screenshots/. Tên 117120_L7_R2_M1_class.png trong bản này là tên đề xuất, không phải ảnh đã tạo. Ảnh thứ hai có thể minh họa truncated của 086220 L2 hoặc vùng ego_body đã kiểm tra trên CVAT.
2. Chuyển ticket cho người phụ trách và cập nhật D08 thành escalated theo thực tế. Hoàn thiện dẫn chứng trong ticket và error card sau khi đã có ảnh.
3. Kiểm tra, sửa nhãn B2-center trên CVAT, lưu và export ZIP mới. Không lấy bản QA B3-center làm rework của mình.
4. Chạy make lock ROUND=rework FILE=exports/rework.zip rồi make rework, thay đường dẫn bằng export thật. Ba file annotations-v2.xml, lock2.txt, delta.md phải được tạo từ thao tác này; không tự viết số trước/sau.
5. Chốt findings, chạy make card trước khi thay mục phân tích của file 10, rồi make triage và make check. Bản nội dung hiện tại chưa làm tất cả gate đạt vì các thao tác trên còn cần thực hiện.

Lưu ý đối chiếu phiên bản: finding mới cho 062370 L1/R1 ghi compare cũ báo ATTRIBUTE nhưng local_quality_conflicts không còn dòng đó. Không dựa riêng selfqc/compare cũ để khẳng định truncated vẫn sai. Kiểm tra export hiện tại trước khi sửa.

