# Bản tóm tắt để pitch với nhóm — Phase 3

**Trương Công Thái Đức — 2A202601581**

> Đây là bản tra cứu dữ kiện của chính tôi khi trình bày, **không phải kịch bản đọc**. Lời pitch và phần phản biện tôi tự nói theo hiểu biết của mình — đúng quy ước [01-worksheet.md](../01-worksheet.md) mục "Quy ước dùng AI trong lab".
>
> Chi tiết đầy đủ nằm ở [individual-report.md](individual-report.md).

---

## Tóm tắt 1 dòng — 3 candidates

| # | Candidate | Ai đau | Nghẽn ở đâu | Số liệu |
|---|---|---|---|---|
| **1** | Nội dung lỗi ở Telegram, trạng thái ở Jira, hai bên không liên kết | Dev + tester | Card ghi "Cần xem lại" nhưng không nói sai cái gì | **3-4 bug/ngày ≈ 15-20/tuần** |
| **2** | Điều tra bug prod: hỏi lại tester + log khóa sau một người | Dev + người cầm server | Phải chờ hỏi tester, rồi chờ xin log | Mọi bug cần log đều qua **1 người** |
| **3** | Tìm hướng dẫn/quy định trong Discord VIN AI | Học viên + TA | Nhiều channel, search lẫn thông báo với chat | Lớp **500+ người** |

---

## Candidate #1 — *(đây là bài tôi muốn pitch nhất)*

**Problem:**
Tester và khách báo lỗi bằng ảnh chụp màn hình trên Telegram. Tiến độ thì kéo thả trên Jira. Hai nửa thông tin nằm ở hai nơi không nối với nhau.

**Ai đau:** dev nhận card bị kéo về `Cần xem lại`; và người đầu tiên đọc tin nhắn lỗi của khách.

**Workflow nghẽn ở đâu — có 2 luồng:**

```text
LUỒNG A — tester test chức năng đang làm (card ĐÃ CÓ SẴN)
  Dev kéo card → "Ready for test"
  → Tester test sai → chụp ảnh gửi Telegram + kéo card về "Cần xem lại"
  → Card chỉ mang TRẠNG THÁI, không mang NỘI DUNG        ← NGHẼN
  → Dev phải scroll ngược Telegram tìm ảnh ứng với card
  → Nhiều lỗi trên 1 chức năng gộp hết vào 1 card, không đếm được

LUỒNG B — khách hàng báo lỗi (KHÔNG có card sẵn)
  Khách chụp ảnh gửi Telegram
  → Không ai được giao phân loại, không biết thuộc module ai  ← NGHẼN
  → Ai đó nhớ thì tạo card, không thì trôi
```

**Bằng chứng thật — một bug report nguyên bản:**

```text
"Hiện tại e test thấy hôm nay nó trả kết quả lâu hơn ạ"  +  1 ảnh màn hình

Thiếu:  mã card · thời điểm request · tài khoản test
        · "lâu hơn" bao nhiêu giây · là lỗi CHẬM hay lỗi "Hệ thống gặp sự cố"?
```

**Future workflow đổi gì:**

```text
Nguyên tắc: KHÔNG bắt tester/khách đổi thói quen. Vẫn gửi Telegram như cũ.

LỚP 1 — RULE (không AI): bot bắt mọi tin có ảnh, ghi nhận timestamp
        + người gửi + link tin gốc  ⇒ không tin nhắn nào trôi mất
LỚP 2 — AI: đọc ảnh + text → mô tả text search được, đoán card liên quan,
        và HỎI NGƯỢC ngay tại Telegram: "mấy giờ? tài khoản nào? chậm bao nhiêu giây?"
NGƯỜI — dev/lead xác nhận 1 thao tác trước khi ghi vào Jira
Fallback — AI hỏng thì tin nhắn vẫn được LỚP 1 giữ, triage tay như hôm nay
```

**Vì sao đáng làm:**
- Tần suất cao nhất: không phải "khi có sự cố" mà là **mọi vòng test của mọi chức năng**
- Giải bài này kéo theo Candidate #2 — nếu ticket đủ thông tin, dev không còn phải hỏi lại tester
- Metric đo được bằng dữ liệu có sẵn: chấm 20 bug report xem đủ field không

**Đã loại được phương án nào — và vì sao:**

| Phương án | Vì sao loại |
|---|---|
| Process fix: bắt tester comment thẳng vào Jira | Tester vẫn sẽ dùng Telegram. Thói quen đang chạy, không đổi bằng quy định |
| Rule: bot đính ảnh theo mã card | **Tin nhắn thật không có mã card** — rule không bao giờ khớp |
| Agent | Không cần AI tự lập kế hoạch hay tự đổi bước |

→ Mức còn lại hợp lý: **Workflow**

---

## Candidate #2

**Problem:** Dev phải hỏi lại tester để đủ thông tin tái hiện, rồi phải đi nhờ người cầm server lấy log.

**Ai đau:** dev xử lý bug; người cầm server bị cắt ngang liên tục.

**Nghẽn:**
1. Vòng lặp hỏi-chờ tester (mô tả thiếu timestamp, tài khoản, bước tái hiện)
2. **Chỉ một người xem được log.** Chưa có Sentry/Grafana/ELK

**Điểm đáng nói nhất khi pitch:**
Đã xác nhận: chưa cấp quyền đọc log cho dev **chỉ vì chưa ai làm** — không có rào cản bảo mật hay hợp đồng. Nghĩa là nghẽn lớn nhất gỡ được với chi phí gần bằng 0 và **không cần một dòng AI nào**.

→ Gut: **No AI / process fix** cho nghẽn chính. AI chỉ thêm giá trị *sau khi* đã có log tập trung (tóm tắt log → 2-3 giả thuyết kèm dòng log dẫn chứng).

---

## Candidate #3

**Problem:** Học viên mất thời gian tìm lại hướng dẫn/quy định vì nội dung rải rác nhiều channel và bị chat đẩy trôi.

**Ai đau:** ~500+ học viên; TA/giảng viên phải trả lời lặp.

**Nghẽn:** search Discord trả kết quả lẫn lộn thông báo chính thức với chat tán gẫu → phải scroll từng channel → không thấy thì hỏi lại.

**Lợi thế riêng của bài này:** **cả nhóm lab đều là actor** → validate được ngay trong buổi, không cần đi hỏi ai ngoài.

**Rủi ro:** một trang index được pin có thể đã đủ. Chưa chắc cần AI. Và chưa rõ có được phép index dữ liệu Discord không.

→ Gut: **No AI / process fix trước**, AI chỉ khi index thủ công không đủ.

---

## Số liệu chốt — để khỏi lật lại lúc họp

| Dữ kiện | Giá trị | Độ chắc |
|---|---|---|
| Bug/ngày | 3-4 (≈ 15-20/tuần, 60-80/tháng) | Ước lượng của người trong team |
| Bug report có đủ field | Gần 0% | Trích nguyên văn tin nhắn tester |
| Tin nhắn có mã card Jira | Không có | Trích nguyên văn tin nhắn tester |
| Tester đổi sang comment trên Jira | Không — vẫn dùng Telegram | Đã xác nhận |
| Rào cản cấp quyền log | Không có, chỉ là chưa ai làm | Đã xác nhận |
| Công cụ log tập trung | Chưa có | Đã xác nhận |
| Bảng ownership module | Hình như chưa có | **Cần xác nhận lại** |
| Team dev bao nhiêu người | Chưa rõ | **Cần xác nhận lại** |
| Lớp VIN AI | 500+ học viên | Đã biết |

---

## Điểm yếu tôi tự biết — nên chủ động nói ra

1. Số 3-4 bug/ngày là **ước lượng**, tôi chưa đếm thật trên Telegram
2. Chưa biết **team bao nhiêu người** → chưa biết 15-20 bug/tuần là nặng hay nhẹ
3. **Chưa có bảng ownership module** → phần AI gợi ý người phụ trách hiện chưa có căn cứ để chạy
4. Candidate #2 và #3 tôi đều tự kết luận là **không cần AI** — nếu nhóm muốn một bài "làm được AI" thì chỉ Candidate #1 hợp

---

## Câu tôi muốn nhóm challenge

1. Tôi loại process fix vì "tester sẽ không đổi thói quen". Đó là kết luận hay là sự đầu hàng? Nếu lead ra quy định cứng thì có đổi được không?
2. AI hỏi ngược tester ngay trên Telegram — liệu tester có thấy phiền rồi phớt lờ bot không? Bot bị lơ thì cả thiết kế sụp.
3. Nếu người thật còn không biết bug thuộc về ai, AI dựa vào đâu để đoán? Vấn đề gốc có phải là **thiếu bảng phân công** chứ không phải thiếu AI?
4. Với 15-20 bug/tuần, cử một người trực triage mất bao lâu mỗi ngày? Nếu chỉ 20 phút thì có đáng xây gì không?

---

## Checklist để challenge bài của bạn khác

Dựa trên tiêu chí shortlist của [01-worksheet.md](../01-worksheet.md) Bước 3.3:

- **Actor** — "ai" đó là một người cụ thể hay một nhóm chung chung?
- **Workflow** — bạn vẽ được 3-7 bước không? Bạn có thật sự làm bước đó bao giờ chưa?
- **Bottleneck** — nghẽn là *một bước cụ thể*, hay chỉ là "nói chung là chậm"?
- **Dấu hiệu thật** — có số không? Số đó bạn đo hay đoán?
- **Metric** — đo bằng gì? Baseline hiện tại là bao nhiêu?
- **Non-AI** — nếu chỉ sửa quy trình hoặc viết một script thì đã giải được bao nhiêu %?
- **Nếu AI sai** — ai phát hiện? Hậu quả tới đâu?
- **Scope** — có làm gọn trong một buổi lab không?
- **Data** — có dữ liệu thật để dùng không, có được phép truy cập không?
