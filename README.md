## Demo
![Chạy thử chương trình](./demo.gif)

## Các thuật toán tìm kiếm được tích hợp

### 1. Uninformed Search Algorithm (Tìm kiếm mù)
Đây là nhóm thuật toán duyệt qua không gian trạng thái một cách hệ thống mà không có bất kỳ thông tin gợi ý nào về vị trí của trạng thái đích (Goal State).

**Breadth-First Search (BFS - Tìm kiếm theo chiều rộng):** Về cách hoạt động, thuật toán duyệt qua tất cả các trạng thái ở độ sâu hiện tại trước khi chuyển sang các trạng thái ở độ sâu tiếp theo, tức là duyệt dàn trải theo từng tầng. Đặc điểm của thuật toán này là đảm bảo luôn tìm ra đường đi ngắn nhất với ít số bước nhất. Tuy nhiên, nhược điểm lớn của BFS là tốn rất nhiều bộ nhớ do phải lưu trữ toàn bộ các trạng thái cùng một tầng vào danh sách chờ.

**Depth-First Search (DFS - Tìm kiếm theo chiều sâu):** Thuật toán sẽ đi theo một nhánh của cây tìm kiếm đến trạng thái sâu nhất có thể cho đến khi chạm đáy. Nếu nhánh đó không chứa đích, nó sẽ quay lui để tiếp tục duyệt các nhánh khác. Đặc điểm của DFS là tiết kiệm bộ nhớ hơn so với BFS vì chỉ cần lưu lại lộ trình đang duyệt. Nhược điểm là không đảm bảo tìm được nghiệm tối ưu, có thể ra đường đi rất dài, và dễ bị kẹt ở những nhánh vô hạn.

**Iterative Deepening Search (IDS - Tìm kiếm sâu dần):** Đây là sự kết hợp hoàn hảo giữa ưu điểm của BFS và DFS. Thuật toán sẽ chạy DFS nhiều vòng lặp, mỗi vòng giới hạn độ sâu (depth limit) tăng dần lên 1 đơn vị, cho đến khi tìm thấy đích. Đặc điểm nổi bật là tối ưu về mặt bộ nhớ giống như DFS và đảm bảo tìm được đường đi ngắn nhất giống như BFS.

**Uniform Cost Search (UCS - Tìm kiếm chi phí đồng nhất):** Trong mỗi bước, thuật toán sẽ ưu tiên mở rộng trạng thái có tổng chi phí (cost) tính từ vạch xuất phát là nhỏ nhất. Thuật toán này luôn đảm bảo tìm được lời giải có tổng chi phí thấp nhất, tuy nhiên thời gian xử lý có thể lâu nếu cây tìm kiếm có quá nhiều nhánh chi phí thấp phân nhánh liên tục.

### 2. Informed Search Algorithm (Tìm kiếm có thông tin)
Nhóm thuật toán này sử dụng thêm hàm đánh giá (Heuristic function) để ước lượng khoảng cách từ trạng thái hiện tại đến đích, giúp thuật toán dự đoán được hướng đi nào là tiềm năng nhất và ưu tiên duyệt trước.

**Greedy Search Algorithm (GSA - Tìm kiếm tham lam):** Thuật toán luôn ưu tiên mở rộng trạng thái có giá trị Heuristic nhỏ nhất, tức là trạng thái có vẻ gần với đích nhất. Tốc độ tìm kiếm thường rất nhanh vì nó đi thẳng tới mục tiêu dựa trên gợi ý. Tuy nhiên, GSA đôi lúc có thể đưa ra lời giải không phải là tối ưu nhất với số bước đi không phải ngắn nhất, hoặc đi vào ngõ cụt nếu hàm Heuristic đánh giá không chuẩn xác.

**A\* Search Algorithm (Tìm kiếm A\*):** Thuật toán này kết hợp một cách hoàn hảo giữa chi phí thực tế từ điểm xuất phát và chi phí ước lượng bằng hàm Heuristic đến điểm đích để tạo ra hàm đánh giá tổng thể f(n) = g(n) + h(n). Ở mỗi bước duyệt, thuật toán sẽ chọn mở rộng trạng thái có tổng chi phí f(n) thấp nhất. Điểm mạnh vượt trội của A\* là luôn đảm bảo tìm ra đường đi ngắn nhất và tối ưu nhất nếu hàm Heuristic được thiết kế hợp lệ và nhất quán.


**Iterative Deepening A\* (IDA\* - Tìm kiếm A\* sâu dần):** Thay vì giới hạn theo độ sâu của cây, IDA\* thiết lập một ngưỡng giới hạn dựa trên tổng chi phí f(n) và thực hiện tìm kiếm theo chiều sâu DFS trong phạm vi ngưỡng đó. Nếu không tìm thấy đích, thuật toán sẽ tăng ngưỡng giới hạn lên bằng giá trị chi phí nhỏ nhất của các trạng thái đã bị cắt nhánh ở vòng trước và lặp lại quá trình. Nhờ vậy, IDA\* vừa tiết kiệm bộ nhớ tối đa giống như DFS, vừa giữ nguyên được khả năng tìm ra lời giải tối ưu của A\*.

## Hướng dẫn chạy chương trình

**Bước 1:** Tải source code về máy và mở file chứa hàm main. Cập nhật biến initial thành trạng thái ban đầu của trò chơi mà bạn muốn giải, sau đó bấm Run All.

**Bước 2:** Sau khi chạy, cửa sổ chương trình sẽ xuất hiện. Chọn thuật toán bạn muốn sử dụng ở thanh menu, sau đó bấm "PLAY" để thuật toán bắt đầu phân tích. Cửa sổ sẽ trực quan hóa từng step giải bài toán. Đồng thời, danh sách các hành động tương ứng để đi từ trạng thái bắt đầu đến trạng thái hiển thị trên màn hình cũng sẽ được cập nhật.

**Bước 3:** Bấm nút "Reset" để xóa các thiết lập hiện tại và đưa ma trận về lại trạng thái khởi tạo ban đầu.

### Lưu ý quan trọng
Sau khi bấm nút "PLAY", thời gian để thuật toán tìm ra lời giải nhanh hay chậm sẽ phụ thuộc rất lớn vào thuật toán bạn lựa chọn và độ khó của trạng thái ban đầu. Hãy chờ đợi nếu chương trình đang xử lý những test case khó.