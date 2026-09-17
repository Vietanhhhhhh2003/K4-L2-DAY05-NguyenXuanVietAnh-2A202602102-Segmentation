# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602102
- Ngày / CVAT local: 17/09/2026
- Công cụ đã dùng: CVAT

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task            | File ZIP đúng tên     | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --------------- | --------------------- | -----------------: | ---------------------------: |
| easy_semantic   | `easy_semantic.zip`   |              3 / 3 |                           20 |
| medium_instance | `medium_instance.zip` |              3 / 3 |                           32 |
| hard_panoptic   | `hard_panoptic.zip`   |              2 / 2 |                           30 |
| cp1_holes       | `cp1_holes.zip`       |              1 / 1 |                            3 |
| cp2_slice       | `cp2_slice.zip`       |              1 / 1 |                            3 |
| cp5_occlusion   | `cp5_occlusion.zip`   |              1 / 1 |                            3 |
| cp3_thin        | `cp3_thin.zip`        |              1 / 1 |                            3 |
| cp4_curb        | `cp4_curb.zip`        |              1 / 1 |                            3 |
| cp6_coverage    | `cp6_coverage.zip`    |              1 / 1 |                            3 |
| **Tổng tối đa** |                       |                    |                      **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Ảnh, vị trí và object Medium đầu tiên tự vẽ: 000000181542.jpg, person gần mép phải ảnh; annotation đầu tiên trong ZIP có id=1, bbox (611.25, 123.05, 23.75, 41.6). ZIP không lưu thứ tự thao tác nên không thể dùng ZIP để xác nhận đây là object đầu tiên tự vẽ.
Class và quy tắc tôi dùng để chọn biên: person; chỉ giữ phần người nhìn thấy và dừng ở biên người/nền, không đoán phần bị che.
Nếu dùng gợi ý sau đó: chưa có dữ liệu trong ZIP để xác nhận vùng gợi ý sai/đúng hoặc hành động sửa/giữ.
Nếu không dùng gợi ý: chưa có dữ liệu để xác nhận.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `cp2_slice` / `000000017627.jpg` / export
- Lỗi thuộc loại: khác — thiếu ZIP đúng tên
- Bằng chứng tôi nhìn thấy: trước đó chưa có ZIP; hiện có 16 annotation, kiểu mask `RLE: 16`
- Quy tắc và hành động sửa: xuất lại đúng ZIP COCO 1.0 với tên `cp2_slice.zip`
- Sau sửa đã Save và export lại.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí                                                | Hai cách hiểu có thể                  | Quy tắc/chứng cứ                                                                                                            | Quyết định hoặc câu hỏi cho coach                                                           |
| --------------------------------------------------------- | ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `easy_semantic` / `7ee6d192-89e2408b.jpg` / mép mặt đường | road hay sidewalk?                    | Ảnh hiển thị mặt đường cao tốc và phần rìa đường; ranh `road`–`sidewalk` phải theo chức năng và bó vỉa, không chỉ theo màu. | Chưa xác nhận mask; cần kiểm lại trực tiếp trong CVAT.                                      |
| `cp4_curb` / `7d83710e-4697c3b2.jpg` / ranh bó vỉa        | road hay sidewalk?                    | Dùng ranh chức năng và bó vỉa theo quy tắc semantic.                                                                        | Chưa có bằng chứng vùng cụ thể trong dữ liệu hiện có; cần coach xác nhận nếu ranh không rõ. |
| `cp5_occlusion` / `000000336232.jpg` / phần vật bị che    | một instance bị che hay hai instance? | Vật bị che có thể có các vùng nhìn thấy rời nhau nhưng vẫn là một instance.                                                 | Chưa có ảnh/mask chi tiết để xác nhận quyết định đã gán.                                    |
