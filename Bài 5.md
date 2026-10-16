
# PHẦN 1. PHÂN TÍCH HỆ THỐNG SMART FARM

1.  ## Xác định Input/Output theo mô hình IPO
    

Thành phần

Nội dung

**Input (Đầu vào)**

Dữ liệu nhiệt độ môi trường và độ ẩm đất từ cảm biến.

**Processing (Xử lý)**

ESP32 tiếp nhận dữ liệu, xử lý và so sánh độ ẩm đất với ngưỡng cài đặt.

**Output (Đầu ra)**

Điều khiển relay, máy bơm nước và van tưới; gửi dữ liệu lên hệ thống giám sát.

2.  ## Sơ đồ phối hợp phần cứng
    

### Chức năng của các thành phần

-   **Cảm biến:** Thu thập dữ liệu nhiệt độ và độ ẩm đất.

-   **ESP32 (SoC):** Tiếp nhận, xử lý dữ liệu và đưa ra lệnh điều khiển.

-   **Relay:** Đóng/ngắt mạch điều khiển máy bơm.

-   **Máy bơm và van tưới:** Cung cấp nước cho cây trồng.

-   **Wi-Fi và hệ thống giám sát:** Truyền dữ liệu để người nông dân theo dõi tình trạng trang trại.

### Nguyên lý hoạt động

Cảm biến thu thập dữ liệu → ESP32 xử lý dữ liệu → Relay điều khiển máy bơm → Nước được cung cấp cho cây trồng.

Đồng thời, ESP32 có thể gửi dữ liệu qua Wi-Fi để người nông dân theo dõi và quản lý trang trại.

### Liên hệ kiến thức đã học

-   **SoC:** ESP32 tích hợp bộ xử lý và các chức năng kết nối trên một chip.

-   **IPO:** Dữ liệu cảm biến là đầu vào, ESP32 xử lý và tạo ra tín hiệu điều khiển là đầu ra.

-   **DIKW:** Dữ liệu cảm biến được chuyển thành thông tin, tri thức và quyết định tưới cây.

1.  ## Giới thiệu dự án
    

**Smart Farm** là hệ thống nông nghiệp thông minh ứng dụng công nghệ IoT nhằm tự động hóa quá trình giám sát môi trường và tưới nước cho cây trồng tại trang trại Lan.

Hệ thống sử dụng cảm biến để thu thập dữ liệu, ESP32 để xử lý thông tin và điều khiển máy bơm dựa trên điều kiện thực tế. Qua đó, hệ thống giúp tiết kiệm nước, giảm công sức lao động và nâng cao hiệu quả sản xuất.

2.  ## Hướng dẫn cài đặt
    

### Yêu cầu phần cứng

-   ESP32 (bộ điều khiển trung tâm).

-   Cảm biến nhiệt độ.

-   Cảm biến độ ẩm đất.

-   Relay điều khiển máy bơm.

-   Máy bơm nước và hệ thống ống tưới.

-   Nguồn điện phù hợp.

### Các bước cài đặt

**Bước 1:** Kết nối cảm biến và relay với ESP32 theo sơ đồ đấu nối.

**Bước 2:** Cài đặt Arduino IDE và bổ sung gói hỗ trợ ESP32.

**Bước 3:** Kết nối ESP32 với máy tính, chọn đúng cổng và loại bo mạch.

**Bước 4:** Nạp chương trình điều khiển vào ESP32.

**Bước 5:** Cấp nguồn, kiểm tra dữ liệu cảm biến và thử nghiệm máy bơm.

Ví dụ chương trình kiểm tra cảm biến:

```

```

_Lưu ý: Đây là chương trình minh họa đọc dữ liệu cảm biến. Cần hiệu chuẩn cảm biến và bổ sung chương trình điều khiển relay trước khi vận hành thực tế._

3.  ## Tính năng hệ thống
    

-   Thu thập dữ liệu nhiệt độ và độ ẩm đất.

-   Sử dụng ESP32 để xử lý dữ liệu cảm biến.

-   Hỗ trợ điều khiển máy bơm thông qua relay.

-   Hỗ trợ theo dõi dữ liệu qua kết nối Wi-Fi khi được cấu hình.

-   Bổ sung cảnh báo khi cảm biến hoặc máy bơm gặp sự cố.

-   Bổ sung lưu trữ lịch sử dữ liệu dài hạn.

4.  ## Sơ đồ hệ thống
    

**Nguyên lý hoạt động:**

Cảm biến thu thập dữ liệu → ESP32 xử lý → Relay điều khiển máy bơm → Nước được cấp cho cây trồng. Dữ liệu cũng có thể được truyền đến hệ thống giám sát thông qua Wi-Fi.

_Lưu ý:_ Hình sơ đồ cần được thêm vào thư mục images trong repository với tên smart-farm-diagram.png. Văn bản thay thế (Alt Text) sẽ hiển thị khi hình ảnh không tải được.

5.  ## Chu kỳ Fetch – Decode – Execute
    

Khi hệ thống cần thực hiện lệnh tưới, CPU xử lý các chỉ thị trong chương trình theo chu kỳ Fetch – Decode – Execute.

> **Fetch (Lấy lệnh):** CPU lấy lệnh tiếp theo từ bộ nhớ.
> 
> **Decode (Giải mã):** CPU giải mã lệnh để xác định thao tác cần thực hiện.
> 
> **Execute (Thực thi):** CPU thực hiện thao tác theo chương trình, chẳng hạn xử lý dữ liệu độ ẩm và điều khiển chân GPIO để gửi tín hiệu đến relay.
> 
> **Kết quả:** Relay kích hoạt máy bơm nếu điều kiện tưới được thỏa mãn.

_Lưu ý: Đây là mô tả đơn giản hóa. CPU thực thi các lệnh của chương trình; quyết định tưới được thực hiện bởi logic điều khiển đã lập trình, không phải bởi một lệnh CPU riêng mang tên “tưới”._

6.  ## Mô hình DIKW – Chuyển dữ liệu thành hành động
    

DIKW gồm bốn cấp độ: Data (Dữ liệu), Information (Thông tin), Knowledge (Tri thức) và Wisdom (Sự khôn ngoan/Quyết định).

```

```

**Ví dụ tại trang trại Lan:**

1.  **Data:** Cảm biến ghi nhận độ ẩm đất là 25%.

2.  **Information:** Hệ thống xác định độ ẩm đất đang thấp hơn ngưỡng cài đặt 30%.

3.  **Knowledge:** Dựa trên ngưỡng đã thiết lập và loại cây trồng, hệ thống xác định đất cần được bổ sung nước.

4.  **Wisdom:** Hệ thống ra quyết định bật máy bơm trong khoảng thời gian phù hợp, sau đó đo lại độ ẩm để tránh tưới quá mức.

_Các ngưỡng trên chỉ là ví dụ minh họa; cần điều chỉnh theo loại cây, đất và điều kiện thực tế._

7.  ## Lưu ý an toàn và xử lý sự cố
    

-   Kiểm tra dây nối và nguồn điện trước khi vận hành.

-   Không để thiết bị điện tiếp xúc trực tiếp với nước.

-   Hiệu chuẩn cảm biến trước khi sử dụng.

-   Thiết lập giới hạn thời gian chạy máy bơm để tránh tưới liên tục.

-   Khi mất kết nối Wi-Fi, hệ thống cần có chế độ vận hành an toàn độc lập nếu chương trình hỗ trợ.

### Xử lý khi RAM bị đầy do dữ liệu nhật ký

-   Không lưu toàn bộ nhật ký liên tục trong RAM.

-   Ghi nhật ký theo từng dòng vào bộ nhớ lưu trữ phù hợp hoặc gửi đến máy chủ khi có kết nối.

-   Chỉ giữ lại các thông tin cần thiết trong RAM; giải phóng bộ nhớ tạm sau khi xử lý.

-   Giới hạn dung lượng nhật ký và luân phiên tệp log khi đạt giới hạn.

-   Không xóa dữ liệu quan trọng khi chưa xác nhận đã lưu thành công.

-   Nếu bộ nhớ gần đầy, ưu tiên duy trì chức năng giám sát và tưới an toàn; ghi nhận cảnh báo và chuyển sang chế độ an toàn khi cần.

# PHẦN 3. KIỂM THỬ HỆ THỐNG SMART FARM

1.  ## Tình huống kiểm thử
    

Giả định hệ thống ESP32 ghi nhật ký hoạt động liên tục vào RAM. Khi dữ liệu nhật ký chiếm quá nhiều bộ nhớ, RAM có thể bị đầy, khiến hệ thống hoạt động chậm, bị treo hoặc tự khởi động lại.

2.  ## Cách xử lý an toàn
    

-   Không lưu toàn bộ dữ liệu nhật ký liên tục trong RAM.

-   Ghi nhật ký theo từng dòng vào bộ nhớ lưu trữ phù hợp.

-   Giới hạn dung lượng nhật ký và thực hiện luân phiên tệp log khi đạt giới hạn.

-   Giải phóng bộ nhớ tạm sau khi xử lý dữ liệu.

-   Kiểm tra dung lượng RAM định kỳ và phát cảnh báo khi bộ nhớ gần đầy.

-   Không xóa dữ liệu quan trọng khi chưa xác nhận dữ liệu đã được lưu an toàn.

-   Ưu tiên duy trì chức năng điều khiển tưới an toàn, tránh để máy bơm hoạt

