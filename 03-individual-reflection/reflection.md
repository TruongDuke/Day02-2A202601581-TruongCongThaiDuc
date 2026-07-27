# 03 — Individual Reflection

**Học viên:** Trương Công Thái Đức — 2A202601581
**Nhóm:** Phạm Quốc Tuấn (thư ký) · Trần Văn Hiếu · Trần Trung Hiếu · Trương Công Thái Đức · Hoàng Mạnh Dũng

> Phần này tôi tự viết. AI chỉ dùng để dựng khung câu hỏi và nhắc lại dữ kiện, không viết thay câu trả lời.

---

## 1. Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| **Scan cá nhân** | Scan 9 problems theo 4 lăng kính, từ 3 bối cảnh: công việc kỹ thuật tại công ty, khóa VIN AI, dự án nhóm | 3 trong số đó vào top 3 Problem Card của tôi |
| **Pitch Problem Card** | Pitch 3 candidate: nội dung lỗi tách rời Telegram/Jira, điều tra lỗi môi trường qua log, tra cứu hướng dẫn trong kênh khóa học | Cả 3 đều vào bảng 15 candidate của nhóm; 2 trong 3 vào shortlist |
| **Challenge bài của bạn khác** | Nghe 12 candidate của 4 bạn còn lại. Tôi thấy các bài khá hợp lý nên không hỏi vặn | *(Ghi trung thực: tôi chưa đóng góp nhiều ở khâu phản biện)* |
| **Gom trùng / cluster** | Cùng nhóm gom 15 candidate thành 4 cluster | Nhìn ra được 3 bài của tôi rơi vào 3 cluster khác nhau |
| **Chọn candidate problem** | Đồng ý bỏ bài Telegram/Jira dù nó chấm điểm cao hơn, vì tiêu chí nhóm hiểu domain chỉ được 2/5 | Bài tra cứu hướng dẫn trong kênh khóa học được nhóm chọn làm Problem Statement |
| **Validation / research** | Là 1 trong 5 người tự trả lời bộ 5 câu phỏng vấn kiểm chứng | Góp 1/5 mẫu validation của nhóm |
| **Workflow nhóm** | Góp ý cho phần workflow hiện tại, nhất là chỗ mỗi người đang xoay xở một kiểu khác nhau | Bản workflow cuối tách thành 4 nhánh theo 4 cách tìm |
| **Problem Statement** | Rà lại các field, tập trung vào bottleneck và boundary | Boundary được viết rõ cả phần loại trừ: không làm lập lịch cá nhân, không làm hướng dẫn cá nhân hóa |
| **Rule / Workflow / Agent** | Đồng tình với hướng làm Rule trước, chưa làm AI ngay | Nhóm chốt Rule, giữ AI như bước nâng cấp có điều kiện |
| **Decision** | Đồng ý Go với scope nhỏ, và đồng ý ghi rõ những chỗ còn chưa đo được thay vì điền số cho đẹp | Bảng tự kiểm có 2 ô Not Yet được ghi trung thực |

---

## 2. Tôi đã dùng AI thế nào?

Nhận xét chung của tôi: **AI hữu ích ở những khâu lặp đi lặp lại và không cần nhiều tư duy.** Còn những chỗ cần hiểu đúng bối cảnh thật thì AI hay suy đoán sai, và tôi phải là người sửa.

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai / hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| **Scan** | Gợi ý thêm problem theo 4 lăng kính khi tôi chưa nghĩ ra | Đưa danh sách rộng để tôi chọn | Nhiều gợi ý không đúng với trải nghiệm của tôi | Tự chọn lại, chỉ giữ những problem tôi thực sự đã gặp |
| **Problem Card** | Chuẩn hóa card theo template, nhờ AI phản biện | Sắp xếp thông tin, đặt câu hỏi phản biện | Tự suy ra bối cảnh công ty tôi từ vài câu ngắn, và suy sai | Bác bỏ 2 giả định sai — xem 3 trường hợp bên dưới |
| **Workflow** | Vẽ lại workflow trước/sau dạng sơ đồ | Trình bày lại cho dễ đọc | Vẽ theo bản mô tả sai nên workflow đầu tiên cũng sai theo | Mô tả lại luồng thật của team, AI vẽ lại từ đầu |
| **Research** | Tìm công cụ đã giải bài tương tự | Tìm được 3 tool có link kiểm được | Có lúc đưa thông tin mà không kèm nguồn kiểm được | Chỉ giữ lại những gì mở link ra xem được |
| **Problem Statement** | Rà field nào còn mơ hồ | Chỉ ra chỗ metric chưa đo được | Có xu hướng điền số cho đủ ô | Để trống chỗ chưa đo và ghi rõ là chưa đếm, thay vì đoán một con số |
| **Rule / Workflow / Agent** | Hỏi phản biện về mức can thiệp | Ép tôi trả lời câu "vì sao không dùng cách đơn giản hơn" | | Giữ hướng làm Rule trước |
| **Decision** | Rà lại lý do Go | Nhắc những giả định còn chưa kiểm | | Chấp nhận để 2 ô Not Yet thay vì tick Yes hết |

### Ba lần AI đoán sai mà tôi phải sửa

Ghi lại đúng những gì đã xảy ra trong quá trình làm bài:

**Lần 1 — AI đoán sai rằng team chưa dùng Jira.**
Tôi kể "không ai phân loại bug", AI suy ra team không có công cụ theo dõi công việc nào. Thực tế team có Jira và vẫn kéo thả trạng thái bình thường. Sau khi tôi sửa, bài toán đổi hẳn: không phải *thiếu công cụ* mà là *khoảng trống giữa Telegram và Jira*.

**Lần 2 — AI kết luận quá mạnh rằng bug bị biến mất.**
AI viết cả một Problem Card quanh ý "bug trôi mất khỏi Jira". Tôi mô tả lại luồng thật — dev kéo card sang `Ready for test`, tester test sai thì kéo về `Cần xem lại` — thì mới lộ ra card **vẫn tồn tại**. Cái thiếu là nội dung lỗi, không phải cái thẻ. Bài toán phải viết lại lần thứ hai.

**Lần 3 — một tin nhắn thật loại bỏ hai phương án AI đề xuất.**
AI đề xuất (a) rule đính ảnh vào card theo mã card trong tin nhắn, và (b) quy định tester ghi thẳng vào Jira. Khi tôi đưa một bug report nguyên bản thì thấy tin nhắn **không hề có mã card**, và tester thì vẫn sẽ dùng Telegram vì nhanh hơn. Cả hai phương án bị loại.

**Bài học tôi rút ra từ ba lần này:**

```text
AI suy đoán rất nhanh từ một câu mô tả ngắn, và nghe khá thuyết phục nên
dễ tin theo. Nhưng cả ba lần sai đều là do nó tự lấp vào chỗ tôi chưa kể
rõ, chứ không phải nó tính sai.

Cách sửa hiệu quả nhất không phải là giải thích thêm bằng lời, mà là đưa
dữ liệu thật. Lần đưa ảnh chụp một tin nhắn bug report nguyên bản đã loại
luôn hai phương án mà trước đó tôi và AI bàn khá lâu.

Nên từ giờ tôi sẽ đưa dữ liệu thật trước, để AI suy đoán sau.
```

---

## 3. Reflection câu hỏi mở

**Tôi học được gì khi nghe top 3 problems của các bạn khác?**

```text
Ba bài của tôi đều xuất phát từ công việc kỹ thuật và từ khóa học, nên khi
nghe các bạn nói về sức khỏe, học vụ, TOEIC, bàn giao ca thì tôi thấy cùng
một kiểu vấn đề có thể xuất hiện ở rất nhiều lĩnh vực khác nhau.

Điều tôi để ý nhất là mấy bài khác nhau về bề ngoài nhưng lại chung một
pattern: thông tin nằm rải rác nên người dùng phải tự tổng hợp. Lúc gom
cluster mới thấy rõ điều đó.
```

**Nhóm có lúc nào bị solution-first không?**

```text
Có. Trong lúc thảo luận đã có lúc nhóm nói tới giải pháp trước khi làm rõ
vấn đề. Nhưng cả nhóm đã nghe ý kiến của nhau và thấy hướng đó không hợp lý
nên đã quay lại làm rõ vấn đề trước.
```

**Tôi có thay đổi ý kiến sau khi bị challenge không?**

```text
Có. Ban đầu tôi nghĩ bài Telegram/Jira là bài đáng làm nhất vì tôi hiểu rõ
nó nhất và có dữ liệu thật. Nó cũng chấm được điểm cao hơn.

Nhưng khi nhóm tách riêng tiêu chí "nhóm hiểu domain" thì bài đó chỉ được
2/5. Tôi thấy lập luận đó đúng: nếu chỉ mình tôi hiểu bài thì phần đào sâu
sẽ thành một người làm, cả nhóm không học được gì. Nên tôi đồng ý bỏ.

Điểm tôi nhận ra: hiểu rõ một bài toán không có nghĩa đó là bài toán phù hợp
để cả nhóm cùng làm.
```

**Tôi đóng góp gì thật sự vào artifact cuối?**

```text
Tôi đóng góp phần vấn đề được nhóm chọn, và góp vào phần workflow hiện tại
cùng phần rà lại Problem Statement.

Chỗ tôi nghĩ mình có ích nhất là giữ cho nhóm không điền số cho đẹp. Có mấy
metric nhóm chưa đo được, tôi đề nghị ghi rõ là chưa đếm thay vì đoán một
con số, và để 2 ô Not Yet trong bảng tự kiểm.
```

**Điều khó nhất khi viết Problem Statement là gì?**

```text
Bottleneck. Xác định đúng một bước cụ thể đang nghẽn là phần khó nhất, vì
dễ viết chung chung kiểu "tìm thông tin chậm" thay vì chỉ ra đúng bước nào
trong quy trình đang làm mất thời gian.
```

**Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?**

```text
Tôi sẽ bàn kĩ hơn về giải pháp và tập trung vào hiệu quả thực tế của giải
pháp, thay vì dừng lại ở mức thấy hợp lý là đồng ý.
```

---

## 4. Reflection tổng

```text
Điều đọng lại nhất với tôi sau buổi lab là thứ tự làm việc: phải hiểu vấn đề
trước rồi mới nói tới giải pháp. Lúc đầu tôi vẫn hay nghĩ ngay tới việc làm
cái gì, chứ chưa nghĩ kỹ ai đang đau và đau ở bước nào.

Phần khó nhất với tôi là xác định bottleneck. Viết chung chung kiểu "tìm
thông tin chậm" thì dễ, nhưng chỉ ra đúng một bước cụ thể đang nghẽn thì
khó hơn nhiều.

Về AI, tôi thấy nó hợp với những việc lặp đi lặp lại và không cần nhiều tư
duy. Còn chỗ cần hiểu đúng bối cảnh thật thì nó suy đoán và suy sai. Ba lần
tôi phải sửa lại đều là như vậy. Đưa dữ liệu thật vào có tác dụng hơn là
giải thích thêm bằng lời.

Tôi cũng học được rằng chọn bài mình hiểu nhất chưa chắc là chọn đúng. Bài
tôi hiểu rõ nhất lại là bài cả nhóm không cùng làm được.

Nếu làm lại, tôi sẽ bàn kỹ hơn về giải pháp và tập trung vào hiệu quả thực
tế, thay vì thấy hợp lý là đồng ý. Ở phần nghe các bạn pitch tôi cũng chưa
đặt được câu hỏi nào đáng kể, đây là chỗ tôi cần chủ động hơn.
```

---

## 5. Tự kiểm cuối bài

- [x] [12đ cá nhân] Cá nhân có 5+ problems và top 3 Problem Cards — *9 problems, 3 card*
- [ ] [12đ cá nhân] Tôi đã pitch rõ và challenge nhóm đúng trọng tâm — *pitch đủ 3 card, nhưng phần challenge tôi chưa làm tốt*
- [x] Nhóm có nhật ký hội tụ từ candidates về 1 bài
- [x] [15đ nhóm] Nhóm có workflow trước/sau
- [x] [20đ nhóm] Nhóm có Problem Statement v0/v1 với metric và boundary rõ
- [x] [15đ nhóm] Nhóm có so sánh No AI / Rule / Workflow / Agent
- [x] [10đ nhóm] Nhóm có Go / Not Yet / No-Go và lý do rõ
- [x] [10đ cá nhân] Reflection cá nhân nói rõ vai trò trong nhóm, cách dùng AI, điều học được, nếu làm lại sẽ đổi gì
- [x] [6đ cá nhân] Tôi tự giải thích được mạch problem → workflow → metric → boundary → độ phù hợp với AI

### Tự kiểm hiểu bài

**Mạch của bài nhóm: problem → workflow → metric → boundary → độ phù hợp với AI**

```text
Problem: học viên khóa VIN AI cần tra lại thông báo, quy định, lịch đã đăng
nhưng không tìm được, vì nội dung nằm rải rác nhiều kênh và bị chat thường
ngày đẩy trôi.

Workflow: 5 người trong nhóm dùng 4 cách khác nhau — lướt tay, search từ
khóa, hỏi nhóm, hỏi thẳng giảng viên. Không ai dùng chung một nguồn.

Bottleneck: không có điểm tra cứu tập trung. Thông báo chính thức lẫn với
chat nên search không dùng được.

Metric: 15-20 phút mỗi lần tra cứu, mục tiêu dưới 3 phút. Đo bằng cách bấm
giờ 5 câu hỏi mẫu trước và sau khi có mục lục ghim.

Boundary: chỉ trả lời từ nội dung đã ghim chính thức, luôn kèm link nguồn,
không có nguồn thì trả lời không biết. Không thay vai trò TA/giảng viên.
Không làm lập lịch cá nhân và không làm hướng dẫn cá nhân hóa.

Độ phù hợp AI: độ mơ hồ thấp, độ phức tạp thấp, nên Rule là đủ.
```

**Vì sao nhóm chọn Rule chứ không phải Workflow hay Agent?**

```text
Vì 3 trong 5 người đau do không có nguồn chung để tra — một trang mục lục
ghim giải trực tiếp được. Chỉ 1 người đau vì tìm ra rồi vẫn không hiểu rõ,
đó mới là phần cần AI diễn giải, nhưng chỉ là thiểu số nên chưa làm ngay.

Không cần Agent vì cả 5 người chỉ tra cứu bị động, không ai cần AI tự quyết
định làm gì tiếp theo.

Research 3 công cụ cũng xác nhận FAQ tĩnh đã giải được phần lớn nhu cầu cơ
bản mà không cần AI.
```

**Vì sao Go chứ không phải Not Yet?**

```text
Vì pilot rất nhỏ và gần như không có rủi ro: chỉ là một trang mục lục ghim,
không có AI nên không có chuyện trả lời bịa.

Những chỗ còn chưa chắc — baseline mới có từ 2/5 người, chưa xác định ai duy
trì cập nhật — đều nằm trong phạm vi pilot 1-2 tuần sẽ trả lời được. Chờ đo
xong mới bắt đầu thì mất thời gian mà không thu được gì thêm.
```
