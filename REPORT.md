# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602263
- Ngày / CVAT local: 17/09/2026 / http://localhost:8080 (CVAT v2.74.1)
- Công cụ đã dùng: Brush, Polygon, Intelligent Scissors; Google Colab để tự kiểm cấu trúc ZIP

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: `000000373353.jpg`, người đi bộ ở phía phải trước dòng xe.
- Class và quy tắc tôi dùng để chọn biên: `person`; dùng Brush 2 px ôm theo đầu, vai, áo và chân, dừng tại phần giày nhìn thấy, không tô bóng đổ trên mặt đường.
- Nếu dùng gợi ý sau đó: gợi ý gộp bóng đổ dưới chân vào người; tôi dùng Erase Brush xóa phần bóng và giữ phần cơ thể nhìn thấy.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `cp2_slice`, `000000017627.jpg`, hai xe `car` đỗ sát nhau bên lề đường.
- Lỗi thuộc loại: gộp-tách.
- Bằng chứng tôi nhìn thấy: hai xe có khe phân tách nhưng ban đầu nằm trong cùng một mask.
- Quy tắc và hành động sửa: hai xe cùng class vẫn là hai instance; tôi phóng to, dùng Polygon theo khe giữa hai xe và tách thành hai object `car`.
- Sau sửa đã Save và export lại chưa? Đã Save, kiểm danh sách Objects và export lại `cp2_slice.zip`.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): Colab tự kiểm: 9/9 ZIP OK, 0 lỗi hợp đồng, 0 task thiếu ZIP; chưa có điểm reference. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `hard_panoptic`, `000000460147.jpg`, sân lát gạch trước sảnh | `road` hoặc `sidewalk` | Bề mặt lát gạch tiếp giáp công trình dành cho người đi bộ; phần xe chạy là lòng đường nhựa. | Chọn `sidewalk` cho sân lát gạch, giữ phần đường nhựa là `road`. |
| `cp2_slice`, `000000017627.jpg`, khe giữa hai xe sát nhau | Một mask `car` hoặc hai instance `car` | Hai xe có ranh phân tách và quy tắc instance yêu cầu tách các vật cùng class. | Tách thành hai mask `car`. |
| `cp6_coverage`, `7daa6479-67988f3f.jpg`, vùng tối dưới tán cây | Gán `building` hoặc tách `vegetation` và `building` | Lớp tiền cảnh nhìn thấy quyết định nhãn; lá cây che tường vẫn là `vegetation`. | Tô phần lá là `vegetation`, phần tường lộ ra là `building`, không để khe trống. |
