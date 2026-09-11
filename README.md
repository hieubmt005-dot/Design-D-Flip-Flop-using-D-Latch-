# Đồ án: Thiết kế D Flip-Flop dùng D-Latch

**Môn học:** Thiết kế vi mạch số 
**Công cụ sử dụng:** Galaxy Custom Designer (Synopsys)

## 📌 Giới thiệu chung
Đồ án này tập trung vào việc phân tích, thiết kế và tối ưu hóa cấu trúc của mạch D Flip-Flop kích hoạt bằng cạnh (Edge-Triggered DFF) sử dụng D-Latch. Mạch được thiết kế theo cấu trúc Master-Slave nhằm đảm bảo khả năng đồng bộ hóa dòng dữ liệu và khắc phục các trạng thái cấm của các vi mạch tiền nhiệm. 

D Flip-Flop được xây dựng và so sánh dựa trên hai phương pháp thiết kế cổng logic:
1. Sử dụng cổng **NAND2**
2. Sử dụng **Transmission Gate (TG)**

## 🛠 Phạm vi thực hiện
Quá trình thiết kế được thực hiện đồng bộ trên công cụ chuyên dụng **Galaxy Custom Designer**, bao gồm các bước:
- **Thiết kế sơ đồ nguyên lý (Schematic):** Tính toán tỉ lệ Wp/Wn cho các cổng NOT, NAND2 và TG để cân bằng dòng điện và tối ưu thời gian trễ (Rise/Fall time).
- **Vẽ bản vẽ vật lý (Layout):** Thực hiện layout cho các khối D-Latch và D Flip-Flop.
- **Kiểm chứng vật lý:** Thực hiện kiểm tra DRC (Design Rule Check), LVS (Layout Versus Schematic), và LPE (Layout Parasitic Extraction) đảm bảo không vi phạm luật thiết kế.
- **Mô phỏng sau thiết kế (Post-layout Simulation):** Kiểm chứng chức năng logic và đo đạc các thông số định thời quan trọng (Setup time, Hold time, Clock Skew, hiện tượng Race-through).

## 📊 Kết quả đánh giá và so sánh

Sau quá trình tối ưu và mô phỏng, thiết kế D Flip-Flop dùng Transmission Gate cho thấy hiệu năng vượt trội hơn so với việc sử dụng hoàn toàn cổng NAND2 cả về tốc độ, diện tích và số lượng linh kiện.

| Thông số | DFF dùng NAND2 | DFF dùng Transmission Gate (TG) |
| :--- | :---: | :---: |
| **Số lượng transistor** | 36 | 24 |
| **T_setup** | ~90 ps | ~50 ps |
| **T_hold** | ~230 ps | ~300 ps |
| **F_max (Tần số cực đại)** | 2.51 GHz | 3.247 GHz |
| **Diện tích layout** | 75.62 µm² | 70.89 µm² |

*Lưu ý: F_max được ước lượng dựa trên tổng thời gian trễ T_min = T_CQ + T_setup + T_skew.*

## 🚀 Hướng phát triển tương lai
- **Tích hợp chân điều khiển:** Thiết kế hệ thống nạp dữ liệu bất đồng bộ với chân Clear (CLR) hoặc Preset (PR) để khởi tạo trạng thái ban đầu mà không phụ thuộc xung Clock.
- **Tối ưu layout & Phân tích công suất:** Rút ngắn đường dây, giảm điện dung ký sinh để tiếp tục nâng cao tần số hoạt động, đồng thời bổ sung phân tích công suất tĩnh và công suất động của vi mạch.
