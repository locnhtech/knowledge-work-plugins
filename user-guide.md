# Hướng dẫn người dùng — Knowledge Work Plugins

## Tổng quan
Repository "knowledge-work-plugins" cung cấp một tập các plugin giúp biến Claude thành trợ lý chuyên môn cho các vai trò, phòng ban và quy trình của tổ chức bạn. Các plugin được thiết kế ưu tiên cho Claude Cowork và tương thích với Claude Code. Mỗi plugin đóng gói kỹ năng (skills), lệnh gạch chéo (slash commands) và kết nối (connectors) để tự động hóa hoặc hỗ trợ các công việc chuyên môn như chăm sóc khách hàng, bán hàng, phân tích dữ liệu, nghiên cứu sinh học, v.v.

## Chức năng chính
- Tạo trợ lý chuyên biệt theo vai trò: mỗi plugin cài sẵn các quy trình làm việc, best-practice và mẫu câu để Claude đưa ra kết quả chất lượng.
- Kết nối dữ liệu và công cụ: các file `.mcp.json` định nghĩa các kết nối tới CRM, kho dữ liệu, hệ thống ticket, công cụ thiết kế, v.v. để Claude truy vấn và tổng hợp thông tin thực tế.
- Lệnh rõ ràng (commands): gọi trực tiếp các hành động như chuẩn bị cuộc gọi bán hàng, soạn trả lời hỗ trợ, chạy truy vấn dữ liệu.
- Kỹ năng ngầm (skills): kiến thức miền được nạp vào để Claude tự động kích hoạt khi ngữ cảnh phù hợp.
- Dễ tùy biến: các plugin là tập hợp file markdown và JSON — không cần code, không cần build.

## Các plugin tiêu biểu
- productivity: quản lý tác vụ, lịch, thói quen làm việc cá nhân.
- sales: tìm hiểu khách hàng, chuẩn bị cuộc gọi, soạn outreach, tạo battlecards.
- customer-support: phân loại ticket, soạn phản hồi, đóng gói escalations, viết bài KB.
- product-management: viết spec, lập roadmap, tổng hợp nghiên cứu người dùng.
- marketing: lập chiến dịch, duy trì voice thương hiệu, báo cáo hiệu suất.
- legal: rà soát hợp đồng, phân loại NDA, đánh giá rủi ro.
- finance: hạch toán, đối chiếu, báo cáo tài chính.
- data: viết SQL, phân tích dữ liệu, trực quan hóa.
- enterprise-search: tìm kiếm tập trung qua nhiều nguồn nội bộ.
- bio-research: công cụ và dữ liệu cho nghiên cứu tiền lâm sàng.
- cowork-plugin-management: công cụ để tạo và tùy chỉnh plugin cho tổ chức.

## Cách cài đặt
- Cowork: cài trực tiếp từ giao diện Cowork (claude.com/plugins) nếu bạn dùng Claude Cowork.

- Claude Code (CLI) — ví dụ cài marketplace và plugin từ repo của bạn:

```bash
# Thêm marketplace từ repo của bạn
claude plugin marketplace add locnhtech/knowledge-work-plugins

# Cài một plugin cụ thể (ví dụ sales)
claude plugin install sales@knowledge-work-plugins
```

Sau khi cài, plugin sẽ kích hoạt tự động: skills được nạp ngầm khi phù hợp và slash commands sẽ sẵn sàng (ví dụ `/sales:call-prep`, `/data:write-query`).

## Cấu trúc plugin
Mỗi plugin theo cấu trúc chung:

- .claude-plugin/plugin.json — manifest mô tả plugin
- .mcp.json — định nghĩa các connector / nguồn dữ liệu
- commands/ — lệnh slash (hành động người dùng gọi rõ ràng)
- skills/ — file markdown mô tả kiến thức miền và quy trình

## Ví dụ sử dụng (mô tả ngắn)
- Triaging ticket (customer-support): `/triage` → Claude trả về phân loại, mức độ ưu tiên, đề xuất routing và bản nháp trả lời.
- Nghiên cứu nhanh (sales): `/research prospect` → tổng hợp thông tin từ CRM, ghi chú, và nguồn công khai.
- Chạy truy vấn dữ liệu (data): `/data:write-query` → yêu cầu câu SQL mẫu, Claude trả về truy vấn và giải thích.

## Tùy chỉnh cho tổ chức của bạn
- Thay connector: chỉnh `.mcp.json` để trỏ tới các công cụ của công ty (HubSpot, Notion, Snowflake, v.v.).
- Thêm ngữ cảnh công ty: bổ sung thuật ngữ, cấu trúc tổ chức, quy trình vào các file skill để Claude hiểu bối cảnh.
- Điều chỉnh workflow: sửa hướng dẫn trong skills để phản ánh cách nhóm bạn thực tế thực hiện công việc.
- Tạo plugin mới: sao chép mẫu `cowork-plugin-management` hoặc theo cấu trúc trên để xây plugin cho vai trò khác.

## Kết nối và quyền truy cập dữ liệu
Để có trải nghiệm đầy đủ, bạn cần cấp phép và cấu hình các kết nối MCP tương ứng với hệ thống của mình. Nếu không kết nối, plugin vẫn hoạt động ở mức khung công việc và mẫu, nhưng sẽ yêu cầu bạn cung cấp ngữ cảnh thủ công.

## Đóng góp
- Fork repository, chỉnh sửa hoặc thêm plugin/skills và gửi Pull Request.
- Plugins là file markdown/JSON — kiểm tra kỹ nội dung và mô tả connector trước khi gửi PR.

---

Nếu bạn muốn, tôi có thể:
- Tạo file này trực tiếp trong repository (đã sẵn sàng để commit), hoặc
- Điều chỉnh nội dung (thêm hướng dẫn cài cụ thể cho từng plugin, dịch sang tiếng Anh, v.v.).
