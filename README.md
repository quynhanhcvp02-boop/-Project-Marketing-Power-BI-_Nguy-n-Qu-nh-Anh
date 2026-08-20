# -Project-Marketing-Power-BI-_Nguy-n-Qu-nh-Anh
 Star Schema Data Model

Hình sau mô tả mô hình dữ liệu dạng **Star Schema**  được sử dụng xuyên suốt toàn bộ báo cáo Power BI.

### Bảng Fact (Trung tâm)
- **`Fact_Marketing`**: Đây là bảng fact chính, lưu trữ các chỉ số hiệu suất marketing ở mức độ chi tiết theo chiến dịch, kênh, sản phẩm và thời gian. Các metric quan trọng bao gồm:
  - `Clicks`, `Impressions`, `Leads`, `Conversions`, `Revenue`.

### Các bảng Dimension (Xung quanh)
- **`Dim_Campaign`**: Chứa thông tin về chiến dịch (mã, tên, mục tiêu, người phụ trách, ngày bắt đầu/kết thúc).
- **`Dim_Channel`**: Phân loại kênh truyền thông (Channel) và nhánh con (Subchannel).
- **`Dim_Product`**: Danh mục và tên sản phẩm.
- **`Dim_Date`**: Bảng ngày tháng, hỗ trợ phân tích theo các mốc thời gian như `Month`, `Quarter`.

### Bảng Measures (Hỗ trợ tính toán)
- **`0.Dim_measure`**: Đây là bảng metadata dùng để lưu trữ các **KPI động** hoặc tham số đầu vào cho báo cáo (ví dụ: `Active Campaign`, `Average Campaign ROAS`, `Average Daily Spend`). Bảng này giúp việc tính toán các chỉ số tùy chỉnh trở nên linh hoạt và dễ bảo trì hơn.

### Mối quan hệ
Các bảng `Dim_*` kết nối với `Fact_Marketing` qua các khóa ngoại tương ứng (`CampaignKey`, `ChannelKey`, `ProductKey`, `DateKey`), tạo thành cấu trúc hình sao đặc trưng, tối ưu cho việc cắt lọc (filter) và tính toán tổng hợp (aggregation) trong DAX.
<img width="1124" height="640" alt="image" src="https://github.com/user-attachments/assets/02eac014-470a-4ce3-ba85-95662d86fdbd" />
Page 1: Marketing Performance Dashboard – Overview
Đây là trang **tổng quan (Overview)** của báo cáo, cung cấp cái nhìn toàn diện và nhanh nhất về hiệu suất hoạt động Marketing trên tất cả các chiến dịch và kênh.

###  Các chỉ số KPI hàng đầu (Top Metrics)
Dashboard hiển thị 4 chỉ số quan trọng nhất ngay tại đầu trang:
- **Total Revenue**: `$19,952M` – Tổng doanh thu đạt được.
- **Total Spending**: `$8,428M` – Tổng chi phí đã bỏ ra cho các chiến dịch.
- **CTR (Click-Through Rate)**: `6.75%` – Tỷ lệ nhấp chuột, đo lường mức độ thu hút của nội dung quảng cáo.
- **ROAS (Return on Ad Spend)**: `2.37` – Tỷ suất hoàn vốn trên chi phí quảng cáo (Trung bình cứ 1$ chi ra thu về 2.37$), phản ánh hiệu quả đầu tư tổng thể.

###  Bộ lọc tương tác (Slicers)
Tương tác để lọc dữ liệu theo:
- **Time**: Chọn năm (2024, 2025) để so sánh hiệu suất theo từng giai đoạn.
- **Channel**: Lọc theo từng kênh riêng lẻ (Email, Facebook Ads, Google Ads, Offline, TikTok Ads).
- **Campaign**: Lọc chi tiết theo từng chiến dịch cụ thể (ví dụ: Giáng sinh 2024, Hè 2025, Baseline...).

###  Trực quan hóa chính: Revenue and Spending Trend
- Biểu đồ đường kết hợp (Combo Chart) thể hiện xu hướng **Doanh thu (Total Revenue)** và **Chi phí (Total Spending)** theo từng tháng.
- Trục **Y bên trái** thể hiện Doanh thu (màu xanh dương), trục **Y bên phải** thể hiện Chi phí (màu cam), giúp người xem dễ dàng đánh giá mối tương quan giữa mức đầu tư và kết quả thu về qua từng thời điểm.

###  Điều hướng nâng cao
Ngoài ra, giao diện còn cung cấp các nút chuyển trang (hoặc bookmark) để đi sâu vào phân tích chi tiết hơn ở các trang:
- **Campaign Deep Dive** – Phân tích chuyên sâu theo từng chiến dịch.
- **Product Analysis** – Phân tích hiệu quả theo từng sản phẩm.
<img width="1127" height="637" alt="image" src="https://github.com/user-attachments/assets/bf9290b1-5767-4a8f-89df-ac1a67d88c57" />
##  Page 2: Marketing Performance Dashboard – Spending & Budget Allocation

Đây là trang **phân tích chi phí (Spending)** chuyên sâu, đóng vai trò như "trung tâm kiểm soát ngân sách" của toàn bộ báo cáo. Trang này giúp nhà quản lý hiểu rõ **tiền đang được chi ở đâu, cho kênh nào và hiệu quả ra sao** thông qua các chỉ số chi phí và tỷ lệ chuyển đổi.

###  Các chỉ số KPI trọng tâm
- **Total Spending**: `$8,428M` – Tổng chi phí đã giải ngân.
- **Average Daily Spend**: `$105,349K` – Chi phí trung bình mỗi ngày, chỉ số quan trọng để kiểm soát dòng tiền chiến dịch.
- **Cost Per Lead (CPL)**: `$8.931K` – Chi phí cho mỗi khách hàng tiềm năng, đo lường hiệu quả thu hút đối tượng mục tiêu.
- **CPA (Cost Per Acquisition)**: `$92.044K` – Chi phí cho mỗi khách hàng chuyển đổi thành công, phản ánh chi phí thực tế để có được một đơn hàng.
- **Active Campaign**: `7` – Số lượng chiến dịch đang hoạt động trong kỳ phân tích.

###  Bộ lọc (Slicers)
Tương tự các trang khác, người dùng có thể lọc theo:
- **Time**: 2024 / 2025
- **Channel**: Email, Facebook Ads, Google Ads, Offline, TikTok Ads
- **Campaign**: Các chiến dịch cụ thể (Baseline, Giáng sinh, Hè...)

###  Các trực quan hóa chính

**1. Phân bổ ngân sách theo kênh (Budget Allocation by Channel)**
- Biểu đồ tròn (Donut Chart) thể hiện tỷ lệ % chi phí cho từng kênh.
- **Google Ads** chiếm tỷ trọng lớn nhất (`28.41%`), tiếp theo là **TikTok Ads** (`22.74%`) và **Offline** (`18.61%`). Đây là cơ sở để đánh giá lại chiến lược phân bổ ngân sách.

**2. Top 3 chiến dịch chi tiêu nhiều nhất (Top 3 Spending Campaign)**
- Danh sách các chiến dịch có mức chi tiêu cao nhất: **Hè 2024**, **Tết 2025**, và **Baseline Campaign**.
- Cho thấy các chiến dịch trọng điểm vào dịp lễ/Tết thường có ngân sách lớn, cần được theo dõi sát sao về ROAS.

**3. Phân bổ ngân sách theo danh mục (Budget Allocation by Categories)**
- Bảng/thanh thể hiện chi phí theo nhóm sản phẩm/dịch vụ:
  - **Dịch vụ bổ sung**: `$3,371M`
  - **Google Ads**: `$1,570M` *(Lưu ý: nếu đây là hạng mục sản phẩm, đây là chi phí dành riêng cho nhóm này)*
  - **Vận tải**: `$1,167M`
- Góc nhìn này giúp xác định danh mục sản phẩm nào đang "ngốn" ngân sách quảng cáo nhiều nhất.

**4. Chi phí theo từng kênh (Bar Chart)**
- Biểu đồ cột so sánh trực quan mức chi tiêu tuyệt đối giữa các kênh (TikTok Ads, Email, Offline, Facebook Ads...), giúp dễ dàng nhận diện kênh dẫn đầu về chi phí tuyệt đối so với các kênh còn lại.
<img width="1764" height="802" alt="image" src="https://github.com/user-attachments/assets/44f1903c-19c4-4ef0-aa0d-3cd5bc9ec0ff" />
##  Page 3: Marketing Performance Dashboard – Revenue

Đây là trang **phân tích doanh thu (Revenue)** chuyên sâu, cho phép nhà quản lý nhìn nhận rõ ràng **doanh thu đến từ đâu, kênh nào đóng góp nhiều nhất và sản phẩm/dịch vụ nào đang tạo ra giá trị** qua các giai đoạn.

###  Các chỉ số KPI đầu trang
- **Total Revenue**: `$19,952M` – Tổng doanh thu đạt được (trùng khớp với trang Overview, đảm bảo tính nhất quán).

###  Bộ lọc (Slicers)
Người dùng có thể tùy chỉnh dữ liệu theo:
- **Time**: Chọn năm (2024, 2025) để so sánh tăng trưởng doanh thu giữa các năm.
- **Channel**: Lọc doanh thu theo từng kênh riêng lẻ hoặc tổ hợp kênh.
- **Campaign**: Lọc theo các chiến dịch cụ thể (Baseline, Giáng sinh, Hè, Tết...).

###  Các trực quan hóa chính

**1. Biểu đồ xu hướng doanh thu (Revenue Trend)**
- Biểu đồ kết hợp hiển thị **Total Revenue** (cột) và **Revenue YoY %** (đường/điểm) theo từng tháng.
- Trục X hiển thị các tháng từ tháng 1/2024 đến tháng 10/2025, giúp đánh giá tính mùa vụ và tốc độ tăng trưởng qua từng thời kỳ.
- Đường YoY% cho thấy mức thay đổi doanh thu so với cùng kỳ năm trước, là chỉ số quan trọng để đánh giá chiến lược marketing có đang cải thiện hiệu quả theo thời gian hay không.

**2. Top 3 chiến dịch doanh thu cao nhất (Top 3 Revenue Campaign)**
- Danh sách các chiến dịch có tổng doanh thu lớn nhất: **Baseline Campaign**, **Hè 2024**, và **Tết 2025**.
- Điều này cho thấy các chiến dịch vào dịp lễ (Tết, Hè) và chiến dịch cơ bản (Baseline) là những động lực chính thúc đẩy doanh thu tổng thể.

**3. Phân bổ doanh thu theo kênh (Revenue Allocation by Channel)**
- Biểu đồ tròn (pie chart) thể hiện tỷ lệ đóng góp doanh thu của từng kênh:
  - **Offline**: `34.05%` – Kênh ngoại tuyến đóng góp lớn nhất, có thể là cửa hàng vật lý hoặc đối tác chiến lược.
  - **Google Ads**: `23.11%` – Kênh tìm kiếm trả tiền mang lại lượng doanh thu đáng kể.
  - **Facebook Ads**: `16.6%`, **TikTok Ads**: `14.52%`, **Email**: `11.72%` – Các kênh digital còn lại có tỷ trọng vừa phải.
- Góc nhìn này giúp đánh giá đâu là kênh "đẻ trứng vàng" để tập trung đầu tư.

**4. Phân bổ doanh thu theo danh mục (Revenue Allocation by Categories)**
- Biểu đồ thanh hiển thị doanh thu theo nhóm sản phẩm/dịch vụ:
  - **Vận tải**: `$8,668M` – Nhóm đóng góp lớn nhất.
  - **Dịch vụ bổ sung**: `$7,202M` – Nhóm dịch vụ gia tăng có doanh thu cao thứ hai.
  - **Logistics**: `$4,062M` – Nhóm còn lại.
- Kết hợp với trang **Spending** để tính **ROAS theo danh mục**, từ đó quyết định cần đẩy mạnh hay cắt giảm ngân sách cho từng nhóm sản phẩm.
<img width="1122" height="641" alt="image" src="https://github.com/user-attachments/assets/fed8ce27-fa8d-4d38-8a15-7ee75eb4abdd" />
##  Page 4: Marketing Performance Dashboard – Channel Performance

Đây là trang **phân tích hiệu quả theo kênh (Channel Performance)** – nơi cung cấp cái nhìn chi tiết và so sánh trực tiếp hiệu suất giữa các kênh marketing dựa trên bộ chỉ số đa chiều (Revenue, ROAS, CTR, CVR). Trang này giúp nhà quản lý **xác định kênh mạnh, kênh yếu và tối ưu hóa phân bổ ngân sách**.

---

###  Các chỉ số KPI tổng quan (hàng đầu)
- **Total Revenue**: `$19,952M` – Doanh thu tổng thể, nhất quán với các trang trước.
- **ROAS**: `2.37` – Tỷ suất hoàn vốn trung bình toàn cục.
- **CTR**: `6.75%` – Tỷ lệ nhấp chuột trung bình.
- **CVR**: `2.69%` – Tỷ lệ chuyển đổi trung bình (Conversion Rate).
- **Active Channel**: Số lượng kênh đang hoạt động trong kỳ phân tích.

###  Bộ lọc (Slicers)
- **Time**: Lọc theo năm (2024 / 2025).
- **Campaign**: Lọc theo từng chiến dịch (Baseline, Giáng sinh, Hè 2024...).

###  Các trực quan hóa chính

**1. Biểu đồ hiệu quả kênh (Effective Channel Performance)**
- Biểu đồ cột nhóm thể hiện **Total Revenue** và **ROAS** của từng kênh (Email, Facebook Ads, Google Ads, Offline, TikTok Ads).
- Cho phép so sánh nhanh: kênh nào có doanh thu cao nhưng ROAS thấp (ví dụ Offline) cần xem xét lại hiệu quả; kênh nào có ROAS vượt trội như Email (3.54) thì nên duy trì hoặc tăng ngân sách.

**2. Hành trình khách hàng theo kênh (Customer Journey by Channel)**
- Biểu đồ dạng funnel hoặc thanh ngang thể hiện quá trình chuyển đổi của từng kênh qua các giai đoạn: **Impression → Clicks → Leads → Conversions**.
- Hình ảnh này giúp xác định kênh nào có tỷ lệ rò rỉ cao nhất ở từng bước trong hành trình, từ đó có chiến lược tối ưu hóa cụ thể (ví dụ: TikTok Ads có thể nhiều Impression nhưng tỷ lệ chuyển đổi thấp).

**3. Xu hướng Budget và Revenue theo kênh (Budget and Revenue Trend by Channel)**
- Biểu đồ đường/cột thể hiện **Total Spending** và **Total Revenue** theo các tháng (1–12), so sánh mức đầu tư và doanh thu đạt được của từng kênh theo thời gian.
- Hữu ích để phát hiện các kênh có chi phí tăng đột biến nhưng doanh thu không theo kịp, hoặc kênh có hiệu quả vượt trội vào các tháng cụ thể.

**4. Bảng chi tiết (Detail Information)**
- Bảng dữ liệu chi tiết hiển thị đầy đủ các chỉ số cho từng kênh:
  - **Email**: Revenue `$6,794M`, ROAS `3.54` (cao nhất), CTR `7.30%` (cao nhất), CVR `6.43%` (cao vượt trội) → Kênh này cực kỳ hiệu quả.
  - **TikTok Ads**: Revenue `$4,611M`, ROAS `1.93` – doanh thu tốt nhưng hiệu quả đầu tư thấp hơn trung bình.
  - **Offline**: ROAS `1.49` – thấp nhất, cần đánh giá lại chiến lược hoặc loại bỏ nếu không cải thiện.
- Bảng này cũng hiển thị tổng ở dòng cuối cùng để đối chiếu với KPI đầu trang.

<img width="1128" height="634" alt="image" src="https://github.com/user-attachments/assets/69a24a24-fde6-43fe-818e-37c17cc97798" />
##  Page 5: Marketing Performance Dashboard – Campaign Deep Dive

Đây là trang **phân tích chuyên sâu theo chiến dịch (Campaign Deep Dive)** – cung cấp cái nhìn chi tiết nhất về hiệu suất của từng chiến dịch marketing, từ doanh thu, chi phí, ROAS đến phân bổ theo người phụ trách. Trang này là "trái tim" của báo cáo, giúp nhà quản lý **ra quyết định về chiến dịch nào nên duy trì, mở rộng hay dừng lại**.


###  Các chỉ số KPI tổng quan (Top Metrics)
- **Total Revenue**: `$19,952M` – Tổng doanh thu (nhất quán với các trang khác).
- **Total Spend**: `$8,428M` – Tổng chi phí đã giải ngân.
- **Average Campaign ROAS**: `2.38` – ROAS trung bình trên tất cả các chiến dịch.
- **Active Campaigns**: `7` – Số lượng chiến dịch đang hoạt động.
- **ROI**: `1.37` – Tỷ suất hoàn vốn đầu tư (Return on Investment), đo lường lợi nhuận thu được so với chi phí bỏ ra.

> *ROI = 1.37 có nghĩa là cứ 1$ chi phí, chiến dịch tạo ra 1.37$ lợi nhuận (sau khi trừ chi phí).*


###  Bộ lọc (Slicers)
- **Time**: Lọc theo năm (2024 / 2025).
- **Channel**: Lọc theo từng kênh để xem hiệu suất của chiến dịch trên từng nền tảng cụ thể.
- **Campaign**: Lọc theo từng chiến dịch cụ thể (Baseline, Giáng sinh, Hè 2024, Hè 2025...).

---

###  Các trực quan hóa chính

**1. Tổng quan hiệu quả chiến dịch (Effective Campaign Overview)**
- Biểu đồ cột nhóm thể hiện **Total Revenue** và **ROAS** của từng chiến dịch.
- Các chiến dịch được liệt kê bao gồm:
  - **Baseline Campaign** – Chiến dịch cơ bản, có doanh thu ổn định.
  - **Hè 2024** và **Hè 2025** – Chiến dịch mùa hè, cho thấy sự tăng trưởng qua các năm.
  - **Tết 2024** và **Tết 2025** – Chiến dịch Tết Nguyên Đán, có thể là chiến dịch lớn nhất trong năm.
  - **Khai giảng 9/24** – Chiến dịch back-to-school.
  - **Giáng sinh 2024** và **Giáng sinh 9/24** – Chiến dịch lễ Giáng sinh.
- Biểu đồ này giúp nhanh chóng xác định chiến dịch nào có ROAS cao nhất (hiệu quả nhất) và chiến dịch nào có doanh thu thấp (cần xem xét).

**2. Doanh thu chiến dịch theo người phụ trách (Campaign Revenue by Owner)**
- Biểu đồ cột xếp chồng thể hiện doanh thu của từng chiến dịch được phân bổ theo nhóm/phòng ban phụ trách (**Team A, Team B, Team C**).
- Góc nhìn này rất hữu ích để:
  - Đánh giá hiệu suất làm việc của từng team.
  - Xác định team nào đang đóng góp nhiều nhất cho thành công của chiến dịch.
  - Làm cơ sở để khen thưởng hoặc điều chỉnh nhân sự cho các chiến dịch tương lai.

**3. Phân bổ ngân sách cho chiến dịch đặc biệt (Budget Allocation for Special Campaign)**
- Phần này hiển thị so sánh **doanh thu (Total Revenue)** và **chi phí (Total Spending)** cho từng chiến dịch lớn.
- Các thanh ngang/trục đều có cùng thang đo giúp so sánh trực quan:
  - **Tết 2024** vs **Tết 2025**: So sánh hiệu quả của chiến dịch Tết qua 2 năm.
  - **Hè 2024** vs **Hè 2025**: Đo lường sự cải thiện của chiến dịch mùa hè.
  - **Hàm 9/24** – Chiến dịch có thể là một đợt khuyến mãi đặc biệt khác.
- Điều này giúp đánh giá xem mức đầu tư đã hợp lý chưa và doanh thu có tương xứng với chi phí không.

**4. Campaign Duration (Góc nhìn thời gian)**
- Biểu đồ đường/cột (có thể ở phía dưới) thể hiện **doanh thu** và **chi phí** theo thời gian diễn ra chiến dịch.
- Giúp phát hiện điểm rơi (peak) của chiến dịch – thời điểm nào đem lại doanh thu cao nhất để tái sử dụng cho các năm tiếp theo.
<img width="1128" height="645" alt="image" src="https://github.com/user-attachments/assets/59745318-ef47-401c-9705-e9a8b90315d2" />
##  Page 6: Marketing Performance Dashboard – Product Analysis

Đây là trang **phân tích hiệu suất theo sản phẩm (Product Analysis)** – cung cấp cái nhìn chi tiết về **sản phẩm/dịch vụ nào đang mang lại doanh thu và chuyển đổi tốt nhất**, từ đó giúp định hướng chiến lược sản phẩm, tập trung nguồn lực vào những sản phẩm chủ lực và cải thiện những sản phẩm kém hiệu quả.

###  Các chỉ số KPI tổng quan
- **Total Revenue**: `$19,952M` – Tổng doanh thu (nhất quán xuyên suốt các trang).
- Các nút điều hướng ở đầu trang cho phép chuyển nhanh giữa các phần: **Overview**, **Budget Analysis**, **Revenue Analysis**, **Channel Performance**, **Campaign Deep Dive**, và **Product Analysis** (trang hiện tại).


###  Bộ lọc (Slicers)
- **Time**: Lọc theo năm (2024 / 2025).
- **Channel**: Lọc theo từng kênh để xem hiệu quả sản phẩm trên từng nền tảng.
- **Campaign**: Lọc theo từng chiến dịch cụ thể để phân tích sản phẩm trong từng chiến dịch riêng biệt.


###  Các trực quan hóa chính

**1. Phân bổ doanh thu theo tháng và sản phẩm (Revenue Allocation by Month)**
- Biểu đồ thanh ngang xếp chồng (100% stacked bar) thể hiện tỷ lệ đóng góp doanh thu của từng sản phẩm qua các tháng (1–12).
- Các sản phẩm chính bao gồm:
  - **Gói VIP** – Dịch vụ cao cấp.
  - **Gửi hàng** – Dịch vụ vận chuyển hàng hóa.
  - **Vé liên tỉnh** – Dịch vụ vận tải hành khách liên tỉnh.
- Biểu đồ này giúp phát hiện tính mùa vụ của từng sản phẩm: ví dụ, **Vé liên tỉnh** có thể chiếm tỷ trọng cao vào các tháng cao điểm du lịch (hè, Tết), trong khi **Gói VIP** có thể ổn định hơn quanh năm.

**2. Hiệu quả sản phẩm (Effective Product)**
- Biểu đồ cột nhóm thể hiện **Total Revenue** (cột xanh) và **Conversions** (đường/điểm màu cam) của từng sản phẩm.
- Các chỉ số cụ thể:
  - **Vé liên tỉnh**: Doanh thu cao nhất (~$8.5B) và số lượng chuyển đổi cao nhất (~35K) → Sản phẩm chủ lực.
  - **Gói VIP**: Doanh thu khoảng ~$7B, conversions ~25K.
  - **Gửi hàng**: Doanh thu khoảng ~$4B, conversions ~15K.
- Biểu đồ này giúp so sánh trực tiếp mức doanh thu và số lượng giao dịch của từng sản phẩm, từ đó đánh giá giá trị trung bình mỗi giao dịch (Average Order Value) một cách gián tiếp.

**3. Phân bổ doanh thu theo danh mục (Revenue Allocation by Categories)**
- Biểu đồ tròn (Donut Chart) thể hiện tỷ lệ đóng góp doanh thu của các nhóm danh mục:
  - **Vận tải**: `43.44%` – Đóng góp lớn nhất, phù hợp với sản phẩm Vé liên tỉnh và Gửi hàng.
  - **Dịch vụ bổ sung**: `36.10%` – Nhóm dịch vụ gia tăng (có thể bao gồm Gói VIP và các dịch vụ khác).
  - **Logistics**: `20.46%` – Nhóm dịch vụ hậu cần/logistics.
- Góc nhìn này giúp xác định nhóm ngành hàng chiến lược để tập trung phát triển sản phẩm mới hoặc tối ưu hóa nhóm hiện có.
<img width="1123" height="629" alt="image" src="https://github.com/user-attachments/assets/c5b1e961-e2f7-4f56-a3a4-dd46023b09ce" />
