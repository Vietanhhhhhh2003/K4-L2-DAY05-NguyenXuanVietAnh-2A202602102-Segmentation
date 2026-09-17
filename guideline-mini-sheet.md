# Phiếu quy tắc gán nhãn Day 5

## Chọn đúng loại trước khi vẽ

| Loại     | Câu hỏi                                      | Trong bài                                                             |
| -------- | -------------------------------------------- | --------------------------------------------------------------------- |
| Semantic | Pixel này thuộc **loại vùng** nào?           | Easy (OK), `cp3_thin` (OK), `cp4_curb` (OK), `cp6_coverage` (OK)      |
| Instance | Pixel này thuộc **vật nào**?                 | Medium (OK), `cp1_holes` (OK), `cp2_slice` (OK), `cp5_occlusion` (OK) |
| Panoptic | Vùng thuộc loại nào **và** vật đếm được nào? | Hard (OK)                                                             |

Tên lớp phải giống từng chữ trong `classes.json` của task. `traffic sign` khác `traffic_sign`. Không dùng chung một danh sách lớp cho mọi task.

## Quy tắc hình học chung

- Vẽ sát **phần nhìn thấy**, không tự đoán phần bị che.
- Hai vật cùng lớp sát nhau vẫn là **hai instance**.
- Một vật bị cột hay vật khác che có thể có các vùng nhìn thấy rời nhau nhưng vẫn là **một instance**.
- Kính/chi tiết trên xe không tự động là lỗ phải khoét khỏi mask; theo quy tắc task.
- Ranh `road`–`sidewalk` xác định theo chức năng và bó vỉa, không chỉ theo màu.
- Phóng to kiểm nét mảnh và khe hở; Save rồi xem lại danh sách Objects.

## Tự kiểm trước export

1. Đúng ảnh và đúng loại semantic/instance/panoptic chưa?
2. Mọi tên lớp có khớp `classes.json` không?
3. Có vật thiếu, vật thừa, gộp hai vật hoặc tách sai một vật không?
4. Mask có tràn sang nền/bóng hoặc bỏ sót vùng rõ ràng không?
5. Đã Save và export đúng format của task chưa?

Khi không chắc, ghi ảnh/vị trí, dấu hiệu nhìn thấy, quy tắc đã dùng và điều cần hỏi trong `REPORT.md`. Không ép đoán cho đủ coverage.
