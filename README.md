# Khái Quát Kết Quả So Sánh Thuật Toán Phân Cụm: FINCH vs. Baseline Algorithms

Dự án này thực hiện đánh giá và so sánh thực nghiệm hiệu năng của thuật toán **FINCH** (First Integer Neighbor Clustering Hierarchy) [cite: 187] với các phương pháp phân cụm phổ biến như **DBSCAN, K-Means, Spectral Clustering, HAC** và **Affinity Propagation (AP)**.

Thông qua các chỉ số về NMI (Normalized Mutual Information) và thời gian thực thi, kết quả thử nghiệm làm nổi bật các đặc tính ưu việt của FINCH so với các thuật toán truyền thống:

## Các điểm nhấn & Kết quả đạt được

- **Giải quyết triệt để rào cản siêu tham số (Hyperparameters):** Trong khi các thuật toán như K-Means, Spectral và HAC bắt buộc người dùng phải cung cấp trước số lượng cụm, hay DBSCAN đòi hỏi tinh chỉnh thủ công các tham số phức tạp (như `eps`), FINCH chứng minh khả năng vận hành hoàn toàn tự động. Thuật toán không cần bất kỳ siêu tham số, ngưỡng khoảng cách hay số lượng cụm định trước nào từ người dùng[cite: 10, 30].

- **Độ ổn định cao & Loại bỏ lỗi "Không hội tụ":** Thực nghiệm cho thấy thuật toán AP thường xuyên gặp tình trạng không hội tụ (`ConvergenceWarning`) khi xử lý dữ liệu. Ngược lại, việc FINCH chỉ sử dụng thông tin láng giềng đầu tiên (First Neighbor) [cite: 9] giúp thuật toán hội tụ rất nhanh qua vài bước và luôn cung cấp một phân vùng hợp lệ tại mỗi bước[cite: 392, 394].

- [cite_start]**Chất lượng phân cụm (NMI) & tốc độ tối ưu:** Dù hoàn toàn không có thông tin tiên nghiệm về phân phối dữ liệu hay số lượng cụm mục tiêu, FINCH vẫn tự động khám phá và đạt được điểm số NMI rất cao, duy trì hiệu năng ổn định trên các tập dữ liệu[cite: 303]. [cite_start]Về mặt tính toán, thời gian thực thi thực tế của FINCH cực kỳ nhanh và bộ nhớ được tối ưu nhờ việc không cần tính toán và lưu trữ toàn bộ ma trận khoảng cách[cite: 79, 348].

- [cite_start]**Khám phá dữ liệu đa cấp độ (Hierarchy):** Thay vì chỉ xuất ra một mảng nhãn duy nhất (phân vùng phẳng) như DBSCAN hay K-Means, điểm sáng của FINCH là trả về một hệ thống phân cấp tự nhiên, cung cấp góc nhìn từ chi tiết (fine) đến tổng quát (coarse) đối với các nhóm dữ liệu[cite: 213]. Điều này cho phép người dùng linh hoạt phân tích sâu hơn vào cấu trúc tiềm ẩn của dữ liệu ở nhiều mức độ khác nhau.
