
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

   Mã          Tóm tắt         Loại         Mục          Trạng    Kết
                                            guideline    thái     quả
  ━━━━━━━━━━  ━━━━━━━━━━━━━━  ━━━━━━━━━━━  ━━━━━━━━━━━  ━━━━━━━  ━━━━━
   P-001       Vật thể ở       Guideline    Chưa xác     🔴 Mở    —
   (#p-001)    xa, bị nhòe     chưa nói     định
               hoặc che        tới
               khuất đến
               mức nào thì
               không cần
               gán nhãn?
  ──────────  ──────────────  ───────────  ───────────  ───────  ─────
   P-002       Phân biệt       Guideline    Chưa xác     🔴 Mở    —
   (#p-002)    đèn giao        mơ hồ        định
               thông với
               bóng đèn
               hoặc nguồn
               sáng khác
  ──────────  ──────────────  ───────────  ───────────  ───────  ─────
   P-003       Phân biệt       Guideline    Chưa xác     🔴 Mở    —
   (#p-003)    vạch kẻ         chưa nói     định
               đường đơn và    tới
               đôi khi bị
               mờ hoặc
               khuất bóng
  ──────────  ──────────────  ───────────  ───────────  ───────  ─────
   P-004       Cách vẽ mask    Guideline    Chưa xác     🔴 Mở    —
   (#p-004)    sky khi có      chưa nói     định
               dây điện        tới
               hoặc dây cáp
               chạy ngang

  ## Loại vấn đề

   Loại                      Nghĩa là
  ━━━━━━━━━━━━━━━━━━━━━━━━  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
   Guideline chưa nói tới    Tình huống không có trong guideline
  ────────────────────────  ──────────────────────────────────────────
   Guideline mơ hồ           Đọc guideline có thể hiểu theo hai cách
                             trở lên
  ────────────────────────  ──────────────────────────────────────────
   Guideline mâu thuẫn       Hai mục trong guideline đưa ra hướng dẫn
                             trái ngược nhau
  ────────────────────────  ──────────────────────────────────────────
   Pain point công cụ        Guideline đã rõ nhưng thao tác trên CVAT
                             chậm hoặc dễ sai

  Trạng thái: 🔴 Mở · 🗣️ Đang bàn · ↗️ Hỏi BTC · ✅ Đã chốt (trỏ sang
  quyết định) · 🛠️ Làm tool (trỏ sang source-tool/) · ⚪ Bỏ (ghi rõ lý
  do)

  ———

  ## P-001

  Ngưỡng bỏ qua vật thể ở xa, bị nhòe hoặc che khuất

  - Loại: Guideline chưa nói tới
  - Mục guideline: Chưa xác định
  - Người phát hiện:
      - Nguyễn Tú Anh · 16/09/2026
      - Hoàng Mạnh Cường · 17/09/2026

  - Link CVAT:
      - Job 1674 — frame 1
        — vật thể ở xa, kích thước nhỏ và khó xác định class.

      - Job 1460 — ảnh b502
        — vật thể ở xa phía bên trái, hình dáng giống ô tô hoặc phương
        tiện nhưng chưa xác định chắc chắn class.

      - Job 1460 — ảnh b066
        — đối tượng ID 189 bị nhòe hoặc che khuất, chưa xác định được
        loại phương tiện.

  - Mô tả: Chưa rõ vật thể ở xa, bị nhòe hoặc che khuất đến mức nào
    thì không cần gán nhãn. Guideline chưa quy định ngưỡng kích thước,
    tỷ lệ nhìn thấy hoặc mức độ chắc chắn cần thiết để xác định class.

  - Các cách hiểu:
      1. Vẫn gán nếu còn nhận diện chắc chắn được class, không phụ
         thuộc khoảng cách.

      2. Không gán nếu không thể xác định chắc chắn class.
      3. Gán một class tổng quát nếu biết đây là phương tiện nhưng
         không xác định được loại cụ thể.

      4. Không gán nếu bbox hoặc polygon nhỏ hơn một ngưỡng pixel do
         BTC quy định.

  - Xử lý tạm trong lúc chờ: Gán các vật thể vẫn nhận diện chắc chắn
    được class. Với vật thể quá mờ hoặc không xác định chắc chắn, ghi
    lại frame và tạm chờ BTC/Coach chốt; không tự đặt ngưỡng khoảng
    cách hoặc kích thước.

  - Câu hỏi cần chốt: Tiêu chí nào quyết định một vật thể ở xa, bị
    nhòe hoặc che khuất có cần gán nhãn: khả năng nhận diện class, tỷ
    lệ nhìn thấy hay kích thước pixel?

  - Kết quả: 🔴 Mở

  ———

  ## P-002

  Phân biệt đèn giao thông với bóng đèn hoặc nguồn sáng khác

  - Loại: Guideline mơ hồ
  - Mục guideline: Chưa xác định
  - Người phát hiện: Hoàng Mạnh Cường · 17/09/2026
  - Link CVAT:
      - Job 1460 — ảnh b051
        — xuất hiện các đốm sáng hoặc bóng đèn màu xanh, chưa rõ có
        phải đèn giao thông hay không.

  - Mô tả: Một số nguồn sáng màu xanh có hình dạng hoặc màu sắc gần
    giống đèn giao thông nhưng không nhìn rõ cấu trúc, vị trí hay cột
    đèn để xác định.

  - Các cách hiểu:
      1. Gán là đèn giao thông dựa trên màu sắc và vị trí tương đối.
      2. Chỉ gán khi nhìn thấy đủ đặc điểm để xác nhận chắc chắn là
         đèn giao thông.

      3. Không gán nếu chỉ nhìn thấy đốm sáng mà không xác định được
         vật thể.

  - Xử lý tạm trong lúc chờ: Không gán class đèn giao thông nếu chỉ
    dựa vào màu của nguồn sáng; ghi lại frame và chờ BTC/Coach xác
    nhận.

  - Câu hỏi cần chốt: Cần những đặc điểm tối thiểu nào để một nguồn
    sáng được gán nhãn là đèn giao thông?

  - Kết quả: 🔴 Mở

  ———

  ## P-003

  Phân biệt vạch kẻ đường đơn và đôi khi bị mờ hoặc khuất bóng

  - Loại: Guideline chưa nói tới
  - Mục guideline: Chưa xác định
  - Người phát hiện: Hoàng Mạnh Cường · 17/09/2026
  - Link CVAT:
      - Job 1460 — ảnh b059
        — vạch kẻ đường bị mờ hoặc khuất bóng, chưa phân biệt được
        vạch đơn hay vạch đôi.

  - Mô tả: Một phần vạch kẻ đường không nhìn thấy rõ do bị mờ hoặc
    khuất bóng, khiến annotator không đủ căn cứ xác định loại vạch.

  - Các cách hiểu:
      1. Suy luận loại vạch dựa trên phần còn nhìn thấy.
      2. Chỉ gán khi nhìn rõ và xác định chắc chắn loại vạch.
      3. Dùng một nhãn tổng quát nếu bộ nhãn có class phù hợp.

  - Xử lý tạm trong lúc chờ: Không tự suy đoán loại vạch từ phần bị
    che khuất; ghi lại frame và chờ BTC/Coach chốt.

  - Câu hỏi cần chốt: Khi không đủ căn cứ phân biệt vạch đơn và vạch
    đôi, nhóm nên bỏ qua, dùng nhãn tổng quát hay suy luận từ phần còn
    nhìn thấy?

  - Kết quả: 🔴 Mở

  ———

  ## P-004

  Cách vẽ mask sky khi có dây điện hoặc dây cáp chạy ngang

  - Loại: Guideline chưa nói tới
  - Mục guideline: Chưa xác định
  - Người phát hiện: Hoàng Mạnh Cường · 17/09/2026
  - Link CVAT:
      - Job 1460 — ảnh s051
        — vùng trời có mật độ dây điện hoặc dây cáp dày đặc.

  - Mô tả: Chưa rõ mask sky có được phủ qua các dây điện nhỏ chạy
    ngang bầu trời hay phải loại trừ chính xác từng phần dây khỏi vùng
    trời.

  - Các cách hiểu:
      1. Mask sky phủ qua các dây điện nhỏ vì dây quá mảnh.
      2. Mask sky phải loại trừ toàn bộ dây điện nhìn thấy.
      3. Chỉ loại trừ dây điện khi kích thước của dây vượt một ngưỡng
         nhất định.

  - Xử lý tạm trong lúc chờ: Ghi lại frame và không áp dụng một quy
    tắc mới cho toàn bộ batch cho đến khi BTC/Coach chốt.

  - Câu hỏi cần chốt: Khi segmentation sky, mask có được phủ qua dây
    điện hoặc dây cáp không? Nếu phụ thuộc kích thước dây, ngưỡng áp
    dụng là gì?

  - Kết quả: 🔴 Mở

  ———

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
