# -Project-Marketing-Power-BI-_Nguy-n-Qu-nh-Anh
 Star Schema Data Model

Hình trên mô tả mô hình dữ liệu dạng **Star Schema** (Sao) được sử dụng xuyên suốt toàn bộ báo cáo Power BI.

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
<img width="1098" height="711" alt="image" src="https://github.com/user-attachments/assets/744d36f2-542e-47c6-94b3-c0febd1e1b70" />

<img width="1858" height="811" alt="image" src="https://github.com/user-attachments/assets/3a166559-26f9-4afe-899f-5bc8e7d5b575" />

<img width="1764" height="802" alt="image" src="https://github.com/user-attachments/assets/44f1903c-19c4-4ef0-aa0d-3cd5bc9ec0ff" />
