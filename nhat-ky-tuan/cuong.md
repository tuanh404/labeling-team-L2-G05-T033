# Nhật ký tuần 01 · 15/09 – 21/09/2026

**Lead tuần này:** Nguyễn Tú Anh - 2A202602059
**Dữ liệu / task CVAT:** [task 152](https://cvat.note.transformerlabs.ai/tasks/152)

## Thành viên và phân công

| Thành viên | Vị trí | Phân công tuần này |
|---|---|---|
|Nguyễn Tú Anh| Lead, Annotator, Reviewer | Segmentation job 1674 |
|Hoàng Mạnh Cường| Annotator, Reviewer | Segmentation job 1676, BBox/Polygon/Polyline job 1460|
|Hoàng Văn Long| Annotator, Reviewer | Segmentation ..., BBox, Polygon job 1462 |
|Lê Hữu Sơn| Annotator, Reviewer | Segmentation ..., BBox, Polygon job 1459 |
|Nguyễn Minh Quân| Annotator, Reviewer | Segmentation ..., BBox, Polygon job 1458 |

## Công việc

| # | Nội dung công việc | Annotator | Reviewer | Hoàn thành | Ghi chú |
|---|---|---|---|---|---|
| 1 | Segmentation 25 frame | Nguyễn Tú Anh | Hoàng Mạnh Cường | 20% | Vẽ được 5/25 frame, chưa review |
| 2 | BBox, Polygon, Polyline 25 frame ([job 1460](https://cvat.note.transformerlabs.ai/tasks/152/jobs/1460)) | Hoàng Mạnh Cường | Hoàng Văn Long | ✅ 100% | Đã hoàn thành 25/25 frame, cập nhật lên CVAT-online và xử lý xong 17/17 issue. |
| 3 | BBox, Polygon 50 frame | Hoàng Văn Long | Lê Hữu Sơn | ...% | Vẽ được .../50 frame, chưa review |
| 4 | BBox, Polygon 50 frame | Lê Hữu Sơn | Nguyễn Minh Quân | ...% | Vẽ được .../50 frame, chưa review |
| 5 | BBox, Polygon 50 frame | Nguyễn Minh Quân | Nguyễn Tú Anh | ...% | Vẽ được .../50 frame, chưa review |
| 6 | Segmentation 25 frame ([job 1676](https://cvat.note.transformerlabs.ai/tasks/206/jobs/1676)) | Hoàng Mạnh Cường | *(chưa phân công)* | ✅ 100% | Đã hoàn thành 25/25 frame và cập nhật lên CVAT-online. Job này chưa có trong bảng phân công gốc, nhờ Lead bổ sung reviewer. |

Mức hoàn thành: ✅ xong **và đã qua review** · 🟡 đang làm (ghi %) · ⛔ bị chặn (ghi lý do) · ⬜ chưa bắt đầu

## Tổng kết
- Đã gán (phần của Hoàng Mạnh Cường): 25/25 ảnh job 1460 + 25/25 ảnh job 1676 = 50/50 ảnh.
- Qua review lần đầu: chưa có reviewer nhận job, chưa review.
- Edge case mới: [P-004](../problem-backlog.md#p-004), [P-005](../problem-backlog.md#p-005)

## Bảng issue — 19/09/2026

| # | Job | Frame | Loại | Nội dung | Trạng thái |
|---|---|---|---|---|---|
| 1 | 1460 | 0 | ATTRIBUTE_CHECK | Đèn giao thông tại (472,298), (786,285) và các xe phía trái bị loá — cần kiểm tra lại nhãn/biên, không lấy quầng sáng làm biên box | ✅ Resolved |
| 2 | 1460 | 1 | UNCERTAIN_SCOPE | Rà các xe tối hoặc ở xa dọc hai bên đường; kiểm tra lại màu vạch vàng/trắng và nhãn lane tương ứng | ✅ Resolved |
| 3 | 1460 | 2 | UNCERTAIN_BOUNDARY | Kiểm tra các polyline crosswalk gần nhau có bị trùng, thống nhất cách vẽ tim/biên vạch; rà người bị che/quá nhỏ trên vỉa hè trái | ✅ Resolved |
| 4 | 1460 | 3 | UNCERTAIN_BOUNDARY | Tuyết và bóng tối làm biên đường, biên xe phía xa không rõ — kiểm tra lại extent của box và polygon | ✅ Resolved |
| 5 | 1460 | 4 | UNCERTAIN_BOUNDARY | Polygon drivable còn đè lên xe phía trước; biên alternative chưa bám rõ vùng đường | ✅ Resolved |
| 6 | 1460 | 5 | ATTRIBUTE_CHECK | Rà xe ở xa và biển báo nhỏ bị nhoè; kiểm tra nhãn `single yellow` vì màu vạch chưa rõ | ✅ Resolved |
| 7 | 1460 | 6 | UNCERTAIN_BOUNDARY | Xe phía xa và biên đường bên phải bị tối — cần xác nhận biên nhìn thấy trước khi sửa | ✅ Resolved |
| 8 | 1460 | 7 | UNCERTAIN_SCOPE | Rà các xe bị che phía sau dải phân cách, đặc biệt xe nhỏ ở xa; thống nhất box theo phần nhìn thấy hay toàn bộ đối tượng | ✅ Resolved |
| 9 | 1460 | 9 | UNCERTAIN_SCOPE | Rà người và xe phía xa, phía phải bị gương/xe/tủ báo che; bổ sung đối tượng còn đủ bằng chứng | ✅ Resolved |
| 10 | 1460 | 10 | UNCERTAIN_BOUNDARY | Polyline lệch vạch đường, có đoạn nằm trên nắp capo; đèn tại (320,211) bị loá | ✅ Resolved |
| 11 | 1460 | 11 | UNCERTAIN_CLASS | Polyline nằm trên táp-lô, cần vẽ lại theo vạch thật; kiểm tra nhãn `double yellow` | ✅ Resolved |
| 12 | 1460 | 12 | UNCERTAIN_SCOPE | Hai polygon `area/drivable` đã được gộp lại thành một; xác nhận cách phân chia drivable/alternative | ✅ Resolved |
| 13 | 1460 | 13 | UNCERTAIN_BOUNDARY | Polyline crosswalk lệch xuống nắp capo, 1 line nằm ở mép dưới ảnh | ✅ Resolved |
| 14 | 1460 | 14 | UNCERTAIN_BOUNDARY | Crosswalk nằm trên nắp capo, cần vẽ lại theo vạch nhìn thấy | ⚠️ Resolved trên hệ thống nhưng **thực tế polyline chưa sửa**, cần làm lại |
| 15 | 1460 | 15 | UNCERTAIN_BOUNDARY | Lane tràn xuống nắp capo; polygon thiếu vùng đường phía trước; người bị bus che | ✅ Resolved |
| 16 | 1460 | 23 | UNCERTAIN_BOUNDARY | Rà road curb theo biên lề thật; polygon đặt thấp, bỏ sót phần đường phía trước | ✅ Resolved |
| 17 | 1460 | 24 | UNCERTAIN_BOUNDARY | Ánh nắng và kính bẩn che khuất đường, xe phía trước; polygon mới bao vùng đáy ảnh | ✅ Resolved |
| 18 | 1676 | S057 | UNCERTAIN_BOUNDARY | Road/sidewalk ngược sáng qua kính chắn gió, không xác định rõ ranh giới | 🔴 Mở — chưa đẩy lên job 1676 online |
| 19 | 1676 | S063 | UNCERTAIN_BOUNDARY | Ảnh qua kính mờ/phản chiếu nặng, không đủ tin cậy để xác định fence/building/road/vegetation | 🔴 Mở — chưa đẩy lên job 1676 online |
| 20 | 1676 | S071 | UNCERTAIN_BOUNDARY | Vùng nhà xa bị sương mù che, không phân biệt được building hay vegetation | 🔴 Mở — chưa đẩy lên job 1676 online |

## Kế hoạch tuần sau

- Sửa nốt 8 polyline sai vị trí ở job 1460 (frame 14, 16) — [P-005](../problem-backlog.md#p-005).
- Bổ sung traffic sign còn thiếu cho các ảnh còn lại của job 1460.
- Theo dõi Lead xác nhận [QĐ-003](../so-quyet-dinh.md#qđ-003) để áp dụng chung cho cả team.
- Xin Lead bổ sung reviewer cho job 1676.
