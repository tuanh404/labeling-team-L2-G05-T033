

  # Problem backlog

  Những chỗ gặp trong lúc gán nhãn mà guideline chưa trả lời được,
  cộng các pain point về công cụ.

  Ghi ngay khi gặp, kể cả lúc chưa biết xử lý thế nào. Một edge case
  không được ghi lại thì
  mỗi người sẽ tự xử lý theo một kiểu — và đó là nguồn lớn nhất của
  nhãn không nhất quán.

  > Các mục dưới đây là vấn đề thực tế nhóm đã ghi nhận trong quá
  > trình gán nhãn.

 
## Danh sách

| Mã | Tóm tắt | Loại | Mục guideline | Trạng thái | Kết quả |
|---|---|---|---|---|---|
| [P-001](#p-001) | Vật thể ở xa, bị nhòe hoặc che khuất đến mức nào thì không cần gán nhãn | Guideline chưa nói tới| Chưa xác định | 🔴 Mở  | [QĐ-001](so-quyet-dinh.md#qđ-001) |
| [P-002](#p-002) | Phân biệt đèn giao thông với bóng đèn hoặc nguồn sáng khác | Guideline mơ hồ | Chưa xác định| 🔴 Mở  | — |
| [P-003](#p-003) | Phân biệt vạch kẻ đường đơn và đôi khi bị mờ hoặc khuất bóng| Guideline chưa nói tới | Chưa xác định| 🔴 Mở  | — |
| [P-004](#p-004) | Cách vẽ mask sky khi có dây điện hoặc dây cáp chạy ngang| Guideline chưa nói tới | Chưa xác định| 🔴 Mở  | — |
| [P-005](#p-005) | Xe chiếm gần toàn bộ frame, boundary và area/drivable không rõ| Guideline mơ hồ | § Occluded & Truncated/ § Quy tắc Bbox| 🔴 Mở  | — |
| [P-006](#p-006) | area/drivable bị chia cắt thành nhiều mảng rời trong 1 frame | Guideline chưa nói tới |Chưa xác định| 🔴 Mở  | — |
| [P-007](#p-007) | Object vừa occluded vừa truncated, vẽ box đến đâu?| Guideline mơ hồ | § Occluded & Truncated | 🔴 Mở  | — |

**Loại**

| Loại | Nghĩa là |
|---|---|
| Guideline chưa nói tới | Tình huống không có trong guideline |
| Guideline mơ hồ | Đọc guideline ra được hai cách hiểu trở lên |
| Guideline mâu thuẫn | Hai mục trong guideline nói ngược nhau |
| Pain point công cụ | Guideline rõ, nhưng làm trên CVAT chậm hoặc dễ sai |

**Trạng thái:** 🔴 Mở · 🗣️ Đang bàn · ↗️ Hỏi BTC · ✅ Đã chốt (trỏ sang QĐ) · 🛠️ Làm tool (trỏ sang `source-tool/`) · ⚪ Bỏ (ghi lý do)

---

  ## P-001

  **Ngưỡng bỏ qua vật thể ở xa, bị nhòe hoặc che khuất**

  - **Loại:** Guideline chưa nói tới
  - **Mục guideline:** Chưa xác định
  - **Người phát hiện:**
      - Nguyễn Tú Anh · 16/09/2026
      - Hoàng Mạnh Cường · 17/09/2026

  - **Link CVAT:**
      - Job 1674 — frame 1
        — vật thể ở xa, kích thước nhỏ và khó xác định class.

      - Job 1460 — ảnh b502
        — vật thể ở xa phía bên trái, hình dáng giống ô tô hoặc phương
        tiện nhưng chưa xác định chắc chắn class.

      - Job 1460 — ảnh b066
        — đối tượng ID 189 bị nhòe hoặc che khuất, chưa xác định được
        loại phương tiện.

  - **Mô tả:** Chưa rõ vật thể ở xa, bị nhòe hoặc che khuất đến mức nào
    thì không cần gán nhãn. Guideline chưa quy định ngưỡng kích thước,
    tỷ lệ nhìn thấy hoặc mức độ chắc chắn cần thiết để xác định class.

  - **Các cách hiểu:**
      1. Vẫn gán nếu còn nhận diện chắc chắn được class, không phụ
         thuộc khoảng cách.

      2. Không gán nếu không thể xác định chắc chắn class.
      3. Gán một class tổng quát nếu biết đây là phương tiện nhưng
         không xác định được loại cụ thể.

      4. Không gán nếu bbox hoặc polygon nhỏ hơn một ngưỡng pixel do
         BTC quy định.

  - **Xử lý tạm trong lúc chờ:** Gán các vật thể vẫn nhận diện chắc chắn
    được class. Với vật thể quá mờ hoặc không xác định chắc chắn, ghi
    lại frame và tạm chờ BTC/Coach chốt; không tự đặt ngưỡng khoảng
    cách hoặc kích thước.

  - **Câu hỏi cần chốt:** Tiêu chí nào quyết định một vật thể ở xa, bị
    nhòe hoặc che khuất có cần gán nhãn: khả năng nhận diện class, tỷ
    lệ nhìn thấy hay kích thước pixel?

  - **Kết quả:** 🔴 Mở


  ## P-002

  **Phân biệt đèn giao thông với bóng đèn hoặc nguồn sáng khác**

  - **Loại:** Guideline mơ hồ
  - **Mục guideline:** Chưa xác định
  - **Người phát hiện:** Hoàng Mạnh Cường · 17/09/2026
  - **Link CVAT:**
      - Job 1460 — ảnh b051
        — xuất hiện các đốm sáng hoặc bóng đèn màu xanh, chưa rõ có
        phải đèn giao thông hay không.

  - **Mô tả:** Một số nguồn sáng màu xanh có hình dạng hoặc màu sắc gần
    giống đèn giao thông nhưng không nhìn rõ cấu trúc, vị trí hay cột
    đèn để xác định.

  - **Các cách hiểu:**
      1. Gán là đèn giao thông dựa trên màu sắc và vị trí tương đối.
      2. Chỉ gán khi nhìn thấy đủ đặc điểm để xác nhận chắc chắn là
         đèn giao thông.

      3. Không gán nếu chỉ nhìn thấy đốm sáng mà không xác định được
         vật thể.

  - **Xử lý tạm trong lúc chờ:** Không gán class đèn giao thông nếu chỉ
    dựa vào màu của nguồn sáng; ghi lại frame và chờ BTC/Coach xác
    nhận.

  - **Câu hỏi cần chốt:** Cần những đặc điểm tối thiểu nào để một nguồn
    sáng được gán nhãn là đèn giao thông?

  - **Kết quả:** 🔴 Mở


  ## P-003

  **Phân biệt vạch kẻ đường đơn và đôi khi bị mờ hoặc khuất bóng**

  - **Loại:** Guideline chưa nói tới
  - **Mục guideline:** Chưa xác định
  - **Người phát hiện:** Hoàng Mạnh Cường · 17/09/2026
  - **Link CVAT:**
      - Job 1460 — ảnh b059
        — vạch kẻ đường bị mờ hoặc khuất bóng, chưa phân biệt được
        vạch đơn hay vạch đôi.

  - **Mô tả:** Một phần vạch kẻ đường không nhìn thấy rõ do bị mờ hoặc
    khuất bóng, khiến annotator không đủ căn cứ xác định loại vạch.

  - **Các cách hiểu:**
      1. Suy luận loại vạch dựa trên phần còn nhìn thấy.
      2. Chỉ gán khi nhìn rõ và xác định chắc chắn loại vạch.
      3. Dùng một nhãn tổng quát nếu bộ nhãn có class phù hợp.

  - **Xử lý tạm trong lúc chờ:** Không tự suy đoán loại vạch từ phần bị
    che khuất; ghi lại frame và chờ BTC/Coach chốt.

  - **Câu hỏi cần chốt:** Khi không đủ căn cứ phân biệt vạch đơn và vạch
    đôi, nhóm nên bỏ qua, dùng nhãn tổng quát hay suy luận từ phần còn
    nhìn thấy?

  - **Kết quả:** 🔴 Mở


  ## P-004

  **Cách vẽ mask sky khi có dây điện hoặc dây cáp chạy ngang**

  - **Loại:** Guideline chưa nói tới
  - **Mục guideline:** Chưa xác định
  - **Người phát hiện:** Hoàng Mạnh Cường · 17/09/2026
  - **Link CVAT:**
      - Job 1460 — ảnh s051
        — vùng trời có mật độ dây điện hoặc dây cáp dày đặc.

  - **Mô tả:** Chưa rõ mask sky có được phủ qua các dây điện nhỏ chạy
    ngang bầu trời hay phải loại trừ chính xác từng phần dây khỏi vùng
    trời.

  - **Các cách hiểu:**
      1. Mask sky phủ qua các dây điện nhỏ vì dây quá mảnh.
      2. Mask sky phải loại trừ toàn bộ dây điện nhìn thấy.
      3. Chỉ loại trừ dây điện khi kích thước của dây vượt một ngưỡng
         nhất định.

  - **Xử lý tạm trong lúc chờ:** Ghi lại frame và không áp dụng một quy
    tắc mới cho toàn bộ batch cho đến khi BTC/Coach chốt.

  - **Câu hỏi cần chốt:** Khi segmentation sky, mask có được phủ qua dây
    điện hoặc dây cáp không? Nếu phụ thuộc kích thước dây, ngưỡng áp
    dụng là gì?

  - **Kết quả:** 🔴 Mở


  ## P-005

  **Xe chiếm gần toàn bộ frame — boundary và area/drivable không rõ**

  - **Loại:** Guideline mơ hồ
  - **Mục guideline:** § Occluded & Truncated / § Quy tắc BBox
  - **Người phát hiện:** Lê Hữu Sơn · 19/09/2026
  - **Link CVAT:**
    - Job 1459 — frame G05_B027.jpg
      — truck chiếm ~91% chiều rộng và ~96% chiều cao ảnh, occluded=true,
      truncated=true; không rõ boundary thực sự của xe ở đâu.
    - Job 1459 — frame G05_B030.jpg
      — truck chiếm ~96% chiều rộng và ~89% chiều cao ảnh, cùng tình huống.
    - Job 1459 — frame G05_B039.jpg
      — truck chiếm ~73% chiều rộng và ~100% chiều cao ảnh (bị cắt cả trên lẫn dưới).
  - **Mô tả:** Khi một xe lớn (thường là truck) lấp gần toàn bộ khung hình,
    guideline yêu cầu vẽ box bao sát object và bật truncated/occluded, nhưng
    không quy định rõ: (1) box nên bao đến mép ảnh hay dừng tại phần nhìn thấy;
    (2) có cần vẽ polygon area/drivable cho phần đường nhỏ còn lộ ra hai bên
    hay bên dưới xe không; (3) nếu không thể xác định boundary vì xe che hết,
    có nên bỏ qua object này không.
  - **Các cách hiểu:**
    1. Vẽ box đến mép ảnh (tức truncated), chấp nhận box bao cả phần nền bị che.
    2. Chỉ bao phần xe thực sự nhìn thấy, không ước lượng phần bị cắt.
    3. Bỏ qua object nếu không thể xác định boundary do che khuất quá nhiều.
    4. Vẽ box toàn bộ ước lượng (kể cả phần khuất) theo hình dạng loại xe đã biết.
  - **Xử lý tạm trong lúc chờ:** Vẽ box bao phần nhìn thấy đến mép ảnh, bật
    truncated=true và occluded=true. Vẽ area/drivable cho phần đường còn lộ ra
    nếu đủ lớn (>2000 px²). Ghi review log UNCERTAIN_BOUNDARY cho các frame này.
  - **Câu hỏi cần chốt:** Khi xe chiếm >70% frame, box nên vẽ đến đâu?
    Có bắt buộc vẽ area/drivable cho phần đường còn lộ không?
  - **Kết quả:** 🔴 Mở


  ## P-006

  **Vùng area/drivable bị chia cắt thành nhiều mảnh rời trong 1 frame**

  - **Loại:** Guideline chưa nói tới
  - **Mục guideline:** Chưa xác định
  - **Người phát hiện:** Lê Hữu Sơn · 19/09/2026
  - **Link CVAT:**
    - Job 1459 — frame G05_B044.jpg
      — 3 polygon area/drivable riêng biệt; đường bị chia cắt bởi xe và
      dải phân cách.
    - Job 1459 — frame G05_B048.jpg
      — 3 polygon area/drivable riêng biệt; các vùng đường không liên thông
      nhau trên cùng frame.
    - Job 1459 — frame G05_B026.jpg, B029.jpg, B033.jpg, B039.jpg, B047.jpg,
      B049.jpg, B050.jpg
      — mỗi frame có 2 polygon area/drivable tách rời.
  - **Mô tả:** Khi xe lớn hoặc dải phân cách chia mặt đường thành các vùng
    không liên thông, annotator cần quyết định: vẽ một polygon duy nhất bao
    toàn bộ (kể cả phần bị che/chia cắt) hay vẽ nhiều polygon riêng biệt cho
    từng vùng nhìn thấy. Guideline chỉ mô tả area/drivable là "vùng đường có
    thể đi được" mà không đề cập trường hợp đường bị chia cắt về mặt thị giác.
  - **Các cách hiểu:**
    1. Vẽ 1 polygon duy nhất bao toàn bộ vùng drivable (kể cả phần bị xe che),
       chấp nhận polygon bao qua object khác.
    2. Vẽ nhiều polygon riêng biệt, mỗi polygon cho một vùng đường liên thông
       nhìn thấy được.
    3. Chỉ vẽ polygon cho vùng drivable lớn nhất, bỏ qua các mảnh nhỏ.
  - **Xử lý tạm trong lúc chờ:** Vẽ nhiều polygon riêng biệt cho từng vùng
    đường liên thông nhìn thấy (cách 2), lọc bỏ mảnh nhỏ hơn 2000 px².
    Ghi review log để reviewer xác nhận.
  - **Câu hỏi cần chốt:** Khi area/drivable bị chia cắt thành nhiều mảnh
    không liên thông, vẽ 1 polygon hay nhiều polygon? Ngưỡng diện tích tối
    thiểu để bỏ qua mảnh nhỏ là bao nhiêu?
  - **Kết quả:** 🔴 Mở

  ## P-007

  **Object vừa occluded vừa truncated cùng lúc — vẽ box đến đâu?**

  - **Loại:** Guideline mơ hồ
  - **Mục guideline:** § Occluded & Truncated
  - **Người phát hiện:** Lê Hữu Sơn · 19/09/2026
  - **Link CVAT:**
    - Job 1459 — frame G05_B027.jpg
      — truck: occluded=true (bị xe khác che một phần) + truncated=true
      (bị cắt bởi mép trái và mép trên ảnh) cùng lúc.
    - Job 1459 — frame G05_B029.jpg
      — pedestrian: occluded=true + truncated=true tại mép phải ảnh,
      bbox xtl=1209 xbr=1279 ytl=281 ybr=334.
    - Job 1459 — frame G05_B040.jpg
      — pedestrian: occluded=true + truncated=true tại mép phải ảnh,
      bbox rất nhỏ (31×31 px), khó xác định có đủ bằng chứng thị giác không.
  - **Mô tả:** Guideline định nghĩa occluded (bị vật khác trong scene che) và
    truncated (bị cắt bởi mép frame) là hai attribute độc lập, nhưng không nói
    rõ cách xử lý khi cả hai xảy ra đồng thời. Cụ thể: phần object bị mép ảnh
    cắt đi lại nằm sau vật thể khác — annotator không biết nên vẽ box ước lượng
    phần bị cắt (như truncated) hay chỉ bao phần nhìn thấy (như occluded nặng).
  - **Các cách hiểu:**
    1. Ưu tiên quy tắc truncated: ước lượng toàn bộ object và kéo box đến mép
       ảnh, bất kể phần bị che.
    2. Ưu tiên quy tắc occluded: chỉ bao phần thực sự nhìn thấy, không ước
       lượng phần khuất sau vật khác, dù box chạm mép ảnh.
    3. Bỏ qua object nếu phần nhìn thấy quá nhỏ (< ngưỡng px) do hai yếu tố
       cộng dồn.
  - **Xử lý tạm trong lúc chờ:** Bật cả occluded=true và truncated=true, vẽ
    box bao phần nhìn thấy rõ nhất và kéo đến mép ảnh nếu object bị cắt.
    Ghi review log ATTRIBUTE_CHECK để reviewer xác nhận.
  - **Câu hỏi cần chốt:** Khi object vừa bị vật khác che vừa bị mép ảnh cắt,
    box nên bao đến đâu? Có ngưỡng diện tích nhìn thấy tối thiểu để quyết định
    bỏ qua object không?
  - **Kết quả:** 🔴 Mở


  ## Mẫu để thêm vấn đề mới

  ## P-NNN

  **Tóm tắt vấn đề trong một dòng**

  - **Loại:** Guideline chưa nói tới | Guideline mơ hồ | Guideline mâu
  thuẫn | Pain point công cụ
  - **Mục guideline:** §... | Chưa xác định
  - **Người phát hiện:** Tên thành viên · dd/mm/yyyy
  - **Link CVAT:**
    - https://cvat.note.transformerlabs.ai/tasks/<task-id>/jobs/<job-id>?frame=<frame>
      — mô tả ngắn vấn đề tại frame.
  - **Mô tả:**
  - **Các cách hiểu:**
    1.
    2.
  - **Xử lý tạm trong lúc chờ:**
  - **Câu hỏi cần chốt:**
  - **Kết quả:** 🔴 Mở
