# 01 — Individual Problem Scan

**Học viên:** Trương Công Thái Đức — 2A202601581

> Ghi chú đọc file: chỗ nào đánh dấu `[?]` là số liệu tôi **chưa đo được**, không phải số bịa. Toàn bộ `[?]` được gom lại ở mục [Giả định cần validate](#giả-định-cần-validate-phase-4) để mang sang Phase 4 kiểm chứng.

---

## Phase 1 — Bảng scan

Bối cảnh scan: công việc kỹ thuật tại công ty, khóa học VIN AI, dự án nhóm.

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại | Setup lại môi trường dev / chạy lại pipeline mỗi khi có người mới hoặc đổi máy | Dev mới join, người hướng dẫn | Lặp lại mỗi lần onboard; tần suất `[?]` lần/tháng |
| 2 | Tốn thời gian | Debug bug production: phải **tự tái hiện lại kịch bản** từ mô tả của tester rồi mới lần được log | Dev xử lý bug, tester chờ kết quả | Khâu tái hiện + ghép log là phần lâu nhất; `[?]` phút/lần |
| 3 | Tốn thời gian | **Chỉ người cầm server mới xem được log** — dev khác muốn xem phải đi nhờ | Cả team dev; người cầm server bị làm nút cổ chai | Mọi bug cần log đều phải qua 1 người |
| 4 | Tốn thời gian | Đọc tài liệu / spec dài chỉ để tìm đúng 1-2 đoạn mình cần | Dev, BA | `[?]` lần/tuần |
| 5 | Pain từ người khác | **Nội dung lỗi mô tả bằng ảnh trên Telegram, còn trạng thái lại kéo thả trên Jira** — card ghi "Cần xem lại" nhưng không nói sai cái gì, dev phải scroll Telegram tìm lại | Dev, tester | **3-4 bug/ngày ≈ 15-20 bug/tuần**; ảnh không search được, tin nhắn không kèm mã card |
| 6 | Pain từ người khác | **Không có ai chịu trách nhiệm phân loại bug khách báo** — không biết thuộc module của ai, route cho ai (team chưa có bảng ownership module) | Cả team; bug khách báo dễ bị treo | Thường xuyên không biết giao cho ai |
| 7 | AI có thể tốt hơn | Tóm tắt thread thảo luận dài thành "chốt cái gì, ai làm gì" | Cả team | `[?]` lần/tuần |
| 8 | Pain từ người khác | Tìm hướng dẫn / quy định chung trong Discord khóa VIN AI — nhiều channel, không biết nội dung nằm ở đâu | ~500+ học viên, TA, giảng viên | Lớp 500+ người; mỗi lần tìm mất `[?]` phút |
| 9 | Lặp lại | Nhiều lỗi khác nhau trên cùng một chức năng bị gộp vào **một card Jira duy nhất** → không đo được chức năng nào hay lỗi, vòng test trung bình mấy lượt | Lead, QA, dev | Không có số liệu chất lượng nào để nhìn |

9 problems, vượt mức tối thiểu 5.

**Cách các problem liên hệ với nhau:**

```text
NHÓM A — vòng đời một bug report (#2, #3, #5, #6, #9)
  Tester/khách phát hiện lỗi
    → mô tả bằng ảnh trên Telegram               (#5)
    → trạng thái kéo thả trên Jira, KHÔNG kèm nội dung (#5) ← nghẽn 1
    → nhiều lỗi gộp vào 1 card, không đếm được   (#9)       ← nghẽn 2
    → (bug khách báo) không ai phân loại, không biết route ai (#6) ← nghẽn 3
    → dev hỏi lại tester, chờ, rồi tự tái hiện   (#2)       ← nghẽn 4
    → xin log từ người cầm server                (#3)       ← nghẽn 5
    → tìm ra nguyên nhân → fix

  Nhận xét quan trọng: team ĐÃ CÓ Jira và kéo thả trạng thái bình thường
  (Ready for test → Cần xem lại). Vấn đề KHÔNG phải thiếu tool, mà là
  TRẠNG THÁI nằm ở Jira còn NỘI DUNG nằm ở Telegram, hai bên không liên kết.
  Đây là lý do phần lớn nghẽn ở nhóm này giải được bằng process fix,
  không cần AI.

NHÓM B — thông tin nằm rải rác, phải tự nối lại (#4, #7, #8)
  Nội dung đã tồn tại ở đâu đó, nhưng chi phí tìm lại quá cao

NHÓM C — automation thuần (#1)
  Không cần AI, chỉ cần script / container hóa
```

---

## Phase 2 — Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | **#5 + #6 + #9 — Nội dung lỗi ở Telegram, trạng thái ở Jira, hai bên không liên kết** | Chạm vào mọi vòng test của mọi chức năng, tần suất cao nhất trong ba card. Tách được rất rõ ba mức Process fix / Rule / AI nên so sánh phương án thay thế rất sạch | Nếu chỉ cần bắt tester comment thẳng vào Jira là xong thì phần AI còn lại rất nhỏ — chưa biết tester có chịu đổi thói quen không |
| 2 | **#2 + #3 — Điều tra bug prod: hỏi lại tester + log bị khóa sau một người** | Pain rõ, ai trong team cũng công nhận. Đặc biệt: đã xác nhận bottleneck lớn nhất **chưa fix chỉ vì chưa ai làm**, không có rào cản kỹ thuật → ca mẫu để chứng minh "không cần AI vẫn là kết luận đúng" | Chưa biết log nằm ở mấy nơi, chưa đo thời gian mỗi lần điều tra |
| 3 | **#8 — Tìm hướng dẫn/quy định trong Discord VIN AI 500+ người** | Actor rộng (500+ học viên), **cả nhóm lab đều là actor** → validate được ngay trong lớp. Nội dung câu trả lời đã tồn tại, chỉ là khó tìm | Chưa rõ tần suất; chưa rõ có được phép truy cập/index dữ liệu Discord không |

---

## Problem Card #1 — Nội dung lỗi ở Telegram, trạng thái ở Jira, hai bên không liên kết

**Problem 1 câu:**
Tester và khách hàng mô tả lỗi bằng ảnh chụp màn hình trên Telegram, còn tiến độ lại được kéo thả trên Jira, nên card Jira chỉ cho biết "cần xem lại" mà không cho biết sai cái gì — dev phải quay sang Telegram tự tìm lại nội dung tương ứng.

**Actor:**
Dev trong team (`[?]` người) nhận card bị kéo về `Cần xem lại`, và người đầu tiên đọc tin nhắn lỗi của khách trong group Telegram.

**Thời điểm / bối cảnh:**
Trong vòng test của mỗi chức năng, và bất kỳ lúc nào khách phát hiện lỗi trên môi trường thật.

**Current workflow — có 2 luồng khác nhau:**

```text
LUỒNG A — tester test chức năng đang làm (Jira có sẵn card)
1. Dev code xong → kéo card sang cột "Ready for test"
2. Tester test, phát hiện sai
3. Tester chụp màn hình gửi Telegram + kéo card về "Cần xem lại"
4. Card Jira chỉ mang TRẠNG THÁI, không chứa NỘI DUNG lỗi   <-- BOTTLENECK 1
5. Dev quay sang Telegram, scroll tìm ảnh tương ứng với card
6. Nhiều lỗi trên cùng một chức năng → gộp hết vào 1 card,
   không đếm được thực sự có bao nhiêu lỗi

LUỒNG B — khách hàng báo lỗi (Jira KHÔNG có card sẵn)
1. Khách chụp màn hình gửi Telegram
2. Không có card nào tương ứng, phải tạo mới
3. Không ai được giao việc phân loại → không biết thuộc
   module của ai, route cho ai                              <-- BOTTLENECK 2
4. Ai đó nhớ thì tạo card; không thì tin nhắn trôi
```

**Ví dụ bug report thật** *(trích nguyên văn một tin nhắn của tester trong group Telegram; ảnh chụp gốc không đính kèm vào repo vì chứa dữ liệu sản phẩm và tên người dùng thật)*

```text
Tester gửi:  [1 ảnh chụp toàn màn hình sản phẩm]
             "Hiện tại e test thấy hôm nay nó trả kết quả lâu hơn ạ"

Những gì tin nhắn KHÔNG có:
  ✗ mã card Jira               → bot không biết đính vào đâu
  ✗ thời điểm thực hiện request → dev không lọc được log đúng cửa sổ
  ✗ tài khoản test              → không tái hiện được
  ✗ "lâu hơn" là bao nhiêu giây, so với mốc nào → không biết đã fix xong chưa
  ✗ phân định rõ: đây là lỗi CHẬM, hay lỗi "Hệ thống đang gặp sự cố khi lấy
    dữ liệu" hiện trong ảnh? Hai lỗi khác nhau, gộp trong một tin nhắn
```

Đây là hình dạng input mà mọi phương án phải xử lý được. Nó giải thích vì sao dev phải hỏi lại tester (Card #2) và vì sao rule thuần không đủ.

**Bottleneck:**

- **Luồng A, bước 4-5** — trạng thái và nội dung nằm ở hai nơi không liên kết. Card nói *"cần xem lại"* nhưng không nói *"sai cái gì"*. Mỗi lần dev nhận card là một lần phải đi tìm lại thông tin vốn đã tồn tại.
- **Luồng A, bước 6** — nhiều lỗi gộp vào một card nên không đo được: chức năng nào hay lỗi nhất, một chức năng phải quay lại bao nhiêu vòng.
- **Luồng B, bước 3** — không có owner triage, và team chưa có bảng ownership module nên không ai chắc bug thuộc phần của ai.

**Impact:**
- Mỗi card `Cần xem lại` kéo theo một lần scroll Telegram để tìm lại nội dung
- Ảnh là ảnh: không search được, không copy được text lỗi, không tra lại được sau vài tuần
- Nhiều lỗi gộp một card → **không có số liệu về chất lượng**: không biết chức năng nào hay lỗi, không biết vòng test trung bình mấy lượt
- Luồng B: bug khách báo có nguy cơ trôi mất vì không ai nhận
- **Định lượng: 3-4 bug/ngày ≈ 15-20 bug/tuần ≈ 60-80 bug/tháng.** Với khối lượng này, mỗi phút lãng phí trên một bug đều được nhân lên đáng kể

**Success metric:**

| Chỉ số | Hiện trạng | Mục tiêu | Cách đo |
|---|---|---|---|
Khối lượng nền: **3-4 bug/ngày ≈ 15-20 bug/tuần**.

| Chỉ số | Hiện trạng | Mục tiêu | Cách đo |
|---|---|---|---|
| **Tỉ lệ bug report có đủ 4 field tối thiểu** (thời điểm, tài khoản, bước tái hiện, kỳ vọng vs thực tế) | Gần 0% — ví dụ thật không có field nào | Trên 80% | Chấm 20 bug report liên tiếp |
| **Số lượt dev phải hỏi lại tester trước khi tái hiện được** | `[?]` lượt/bug | Dưới 0.3 lượt/bug | Đếm trên 20 bug liên tiếp |
| Thời gian dev tìm lại nội dung lỗi ứng với một card `Cần xem lại` | `[?]` phút × 15-20 bug/tuần | 0 — nội dung nằm ngay trong card | Bấm giờ 10 card gần nhất |
| Tỉ lệ bug tra lại được sau 1 tháng bằng tìm kiếm văn bản | 0% (chỉ có ảnh) | 100% | Thử tra 10 bug cũ |
| Số vòng test trung bình của một chức năng | Không đo được hiện nay | Đo được | Đếm số lần card quay về `Cần xem lại` |

**Non-AI alternative:**

| Phương án | Có giải được không? | Vướng ở đâu |
|---|---|---|
| **Process fix** — quy định tester comment thẳng vào card Jira thay vì Telegram | Về lý thuyết giải gần hết Luồng A | ❌ **Đã kiểm chứng là không thực tế.** Tester vẫn đang và sẽ tiếp tục comment trên Telegram vì nhanh hơn. Đây là thói quen đang chạy, không đổi được bằng một quy định |
| **Rule** — bot đính ảnh vào card theo mã card trong tin nhắn | Sẽ rất gọn nếu tin nhắn có mã | ❌ **Tin nhắn thật không hề có mã card** (xem ví dụ ở trên). Rule này gần như không bao giờ khớp |
| **Rule** — bot tạo card `Chưa phân loại` cho mọi tin có ảnh | ✅ Có, cho Luồng B | ⚠️ Sinh rác: 15-20 card/tuần toàn tiêu đề trống, vẫn phải có người mở từng cái ra đọc ảnh |
| **Process fix** — cử người trực triage luân phiên theo tuần | ✅ Có | ⚠️ Không tiết kiệm công, chỉ chuyển gánh nặng sang một người cố định. Với 15-20 bug/tuần thì đây là việc thật, không nhỏ |

Kết luận phần này: **các phương án non-AI đều xử lý được phần "không để trôi", nhưng không phương án nào xử lý được phần "biến ảnh + câu nói mơ hồ thành thông tin dùng được".** Đó chính là chỗ chi phí thật nằm.

**AI hypothesis:**
AI làm đúng phần mà cả process fix lẫn rule đều bó tay:
- Đọc ảnh + câu tiếng Việt tự do → **chuyển thành mô tả text search được**
- **Đoán card/chức năng liên quan** khi tin nhắn không có mã card (đây là ca phổ biến, không phải ngoại lệ)
- **Phát hiện thiếu field** và hỏi ngược tester ngay tại Telegram: *"lúc mấy giờ? tài khoản nào? chậm bao nhiêu giây?"* — cắt vòng hỏi-chờ của Card #2 ngay từ đầu nguồn
- Tách một tin nhắn báo nhiều lỗi thành nhiều mục riêng

Con người xác nhận rồi mới ghi vào Jira.

⚠️ Điều kiện tiên quyết: muốn AI gợi ý **người phụ trách** thì phải có **bảng ownership module** trước. Hiện chưa có. Nếu người thật còn không biết bug thuộc về ai, AI không có căn cứ nào để đoán — phần này phải tắt cho tới khi có bảng.

**Quick gut:**
- [ ] No AI / process fix — *đã thử nghĩ, nhưng tester sẽ không rời Telegram*
- [ ] Rule — *không đủ: tin nhắn thật không có mã card để bám vào*
- [x] **Workflow** — *rule bắt tin nhắn (không để trôi) + AI đọc ảnh/text và hỏi ngược field thiếu + người xác nhận trước khi ghi Jira*
- [ ] Agent — *không cần AI tự lập kế hoạch hay đổi bước*
- [ ] Chưa biết

### Draft workflow — Card #1

```text
CURRENT STATE

LUỒNG A — tester test chức năng đang làm
JIRA     [Dev kéo card → "Ready for test"]
              ↓
TELEGRAM [Tester test sai → chụp ảnh gửi Telegram: nội dung lỗi ở ĐÂY]
              ↓
JIRA     [Tester kéo card về "Cần xem lại": chỉ có TRẠNG THÁI]
              ↓
         ✂ HAI NƠI KHÔNG LIÊN KẾT        <-- BOTTLENECK 1
              ↓
TELEGRAM [Dev scroll ngược tìm ảnh ứng với card: [?]']
         [Nhiều lỗi gộp 1 card → không đếm được lỗi nào là lỗi nào]

LUỒNG B — khách báo lỗi
TELEGRAM [Khách chụp ảnh gửi Telegram]
              ↓
         [Không có card sẵn, không ai được giao phân loại]  <-- BOTTLENECK 2
              ↓
         [Ai đó nhớ thì tạo card — không thì trôi]

FUTURE STATE — giữ nguyên Telegram làm cửa vào, thêm cầu nối 2 lớp

Nguyên tắc: KHÔNG bắt tester hay khách đổi thói quen. Họ vẫn gửi ảnh
lên Telegram y như hôm nay. Toàn bộ thay đổi nằm ở phía sau.

── LỚP 1: RULE — không để trôi (không AI) ──
[Tester/khách gửi ảnh + text lên Telegram]
→ [BOT bắt mọi tin có ảnh trong group bug
   → ghi nhận: timestamp, người gửi, ảnh, link tin nhắn gốc]
   ⇒ dù AI hỏng hoàn toàn, KHÔNG tin nhắn nào biến mất

── LỚP 2: AI — biến ảnh thành thông tin dùng được ──
→ [AI đọc ảnh + text tiếng Việt tự do:
     · chuyển ảnh thành mô tả text (search được, tra lại được)
     · đoán chức năng/card liên quan  (vì tin nhắn KHÔNG có mã card)
     · tách 1 tin báo nhiều lỗi thành nhiều mục
     · phát hiện field còn thiếu]
→ [AI HỎI NGƯỢC ngay tại Telegram, đúng lúc tester còn nhớ:
     "Anh/chị thực hiện lúc mấy giờ? Tài khoản test nào?
      Chậm khoảng bao nhiêu giây?"]
   ⇒ cắt vòng hỏi-chờ của Card #2 ngay tại đầu nguồn
→ [NGƯỜI: dev/lead xác nhận hoặc sửa — 1 thao tác]   <-- HUMAN BOUNDARY
→ [Ghi vào Jira: comment vào card có sẵn (Luồng A)
                 hoặc tạo card mới (Luồng B)]

Boundary:
- AI CHỈ soạn nháp, KHÔNG tự gán việc, KHÔNG tự chuyển trạng thái card
- AI KHÔNG tự đặt mức nghiêm trọng cao nhất (tránh báo động giả với khách)
- Với tin nhắn của KHÁCH: AI chỉ hỏi ngược khi thật cần, giọng lịch sự,
  không hỏi dồn như với tester nội bộ
- Mọi card giữ link về tin nhắn Telegram gốc để truy ngược
- Gợi ý người phụ trách chỉ bật SAU KHI có bảng ownership module

Fallback: AI đoán sai card, hoặc lỗi hoàn toàn
          → tin nhắn vẫn được LỚP 1 ghi nhận, không mất
          → vào hàng đợi "Chưa phân loại", người triage tay như hôm nay
```

---

## Problem Card #2 — Điều tra bug production: tái hiện kịch bản + log bị khóa sau một người

**Problem 1 câu:**
Khi tester báo bug, dev phải tự tái hiện lại kịch bản từ mô tả rồi đi nhờ người cầm server lấy log, khiến việc tìm nguyên nhân kéo dài và phụ thuộc vào một người duy nhất.

**Actor:**
Dev được giao xử lý bug production, và người giữ quyền truy cập server (nút cổ chai).

**Thời điểm / bối cảnh:**
Sau khi tester báo bug, trước khi bắt tay sửa code.

**Current workflow:**

```text
1. Tester báo bug (thường kèm ảnh chụp màn hình, mô tả ngắn)
2. Dev đọc mô tả, cố suy ra kịch bản đã dẫn tới lỗi
3. Thiếu thông tin (tài khoản nào? lúc mấy giờ? bước nào?)
   → nhắn hỏi lại tester → chờ tester rảnh trả lời      <-- BOTTLENECK 1
4. Dev tự dựng lại kịch bản trên môi trường test, thử nhiều lần
5. Nếu cần log server: phải nhờ người cầm server         <-- BOTTLENECK 2
6. Người cầm server lọc log quanh thời điểm lỗi, copy đoạn liên quan gửi lại
7. Dev ghép log với hành vi quan sát được → suy ra nguyên nhân
8. Fix + verify với tester
```

**Bottleneck:**
- **Bước 3-4** — tái hiện kịch bản: mô tả từ tester thiếu thông tin nên dev phải hỏi lại rồi chờ, hoặc tự đoán và thử nhiều lần. Đây là **vòng lặp hỏi-chờ**, không phải một bước tuyến tính.
- **Bước 5** — quyền xem log tập trung vào một người: mọi việc phải chờ người đó rảnh. Chưa có công cụ log tập trung nào (không Sentry, không Grafana, không ELK).

**Impact:**
- Thời gian tìm nguyên nhân bị kéo dài, phần lớn là **thời gian chờ và thời gian đoán**, không phải thời gian suy nghĩ kỹ thuật
- Người cầm server bị cắt ngang công việc liên tục
- Bug khó tái hiện có nguy cơ bị đóng kiểu "không tái hiện được"
- Định lượng: `[?]` bug/tuần cần log, `[?]` phút mỗi lần, riêng khâu tái hiện + xin log chiếm `[?]` %

**Success metric:**

| Chỉ số | Hiện trạng | Mục tiêu | Cách đo |
|---|---|---|---|
| Thời gian từ lúc nhận bug → xác định được nguyên nhân | `[?]` phút | Giảm `[?]` % | Bấm giờ 10 bug liên tiếp |
| Số lần phải đi nhờ người khác để xem log | Gần như 100% số bug cần log | 0 | Đếm số lượt nhờ |
| Tỉ lệ bug tái hiện được ngay lần đầu | `[?]` % | Tăng lên `[?]` % | Đếm số lần thử tái hiện |

**Non-AI alternative:** ⭐ *gần như chắc chắn là đáp án đúng*

Đã xác nhận: **chưa cấp quyền đọc log cho dev chỉ vì chưa ai làm** — không có rào cản bảo mật hay ràng buộc hợp đồng nào. Nghĩa là bottleneck lớn nhất của card này gỡ được với **chi phí gần bằng 0 và không cần một dòng AI nào**:

- Cấp quyền đọc log read-only cho toàn bộ dev, hoặc
- Đẩy log lên một chỗ tập trung có giao diện tìm kiếm (Grafana Loki / Sentry / ELK)

Bottleneck còn lại (hỏi lại tester) giảm được bằng **process fix**: bắt buộc bug report kèm timestamp + tài khoản test + các bước tái hiện — liên hệ trực tiếp tới Card #1.

Nói cách khác: **giải Card #1 + mở quyền log là đã xử lý được phần lớn Card #2, không cần AI.** Nếu vẫn chọn AI cho card này thì phải trả lời được: vì sao không làm việc rẻ hơn và chắc chắn hơn trước?

**AI hypothesis:**
Chỉ *sau khi* đã có log tập trung, AI mới thêm giá trị: đọc đoạn log quanh thời điểm lỗi → tóm tắt chuyện gì đã xảy ra và đưa 2-3 giả thuyết nguyên nhân, mỗi giả thuyết kèm dòng log dẫn chứng. Dev vẫn là người kết luận.

**Quick gut:**
- [x] No AI / process fix — *cho bottleneck chính: mở quyền log + chuẩn hóa bug report*
- [ ] Rule
- [x] Workflow — *chỉ cho bước tóm tắt log, sau khi đã fix quyền truy cập*
- [ ] Agent
- [ ] Chưa biết

### Draft workflow — Card #2

```text
CURRENT STATE — [?] phút/bug

[Tester báo bug: ảnh + mô tả ngắn]
→ [Dev đọc, thiếu thông tin]
   ↺ [Hỏi lại tester → chờ trả lời: [?]']     <-- BOTTLENECK 1 (vòng lặp)
→ [Dev tự tái hiện, thử nhiều lần: [?]']
→ [Nhắn nhờ người cầm server: chờ [?]']       <-- BOTTLENECK 2 (một người duy nhất)
→ [Người cầm server lọc log, copy gửi lại: [?]']
→ [Ghép log + hành vi → tìm nguyên nhân: [?]']
→ [Fix + verify]

FUTURE STATE — làm theo 2 lớp, KHÔNG cần AI ở lớp 1

── LỚP 1: process/infra fix (không AI, làm trước) ──
[Ticket Jira có sẵn timestamp + tài khoản + bước tái hiện]  (đến từ Card #1)
   ⇒ cắt hẳn vòng lặp hỏi-chờ tester                        <-- xóa BOTTLENECK 1
→ [Dev tự truy cập log read-only, tự lọc theo thời điểm]    <-- xóa BOTTLENECK 2
→ [Tái hiện ngay được vì đã đủ thông tin]
→ [Tìm nguyên nhân]

── LỚP 2: thêm AI, chỉ khi lớp 1 đã xong ──
→ [AI: tóm tắt log quanh thời điểm lỗi
   + đưa 2-3 giả thuyết nguyên nhân, mỗi giả thuyết kèm dòng log dẫn chứng]
→ [NGƯỜI: dev kiểm dẫn chứng và kết luận]     <-- HUMAN BOUNDARY

Boundary:
- AI KHÔNG được kết luận nguyên nhân, chỉ đưa giả thuyết CÓ DẪN CHỨNG
- AI KHÔNG được tự sửa code
- Mọi giả thuyết phải trỏ về dòng log thật để dev kiểm được

Fallback: AI tóm tắt sai hoặc không tìm thấy gì
          → dev đọc log thô như hiện tại (vẫn nhanh hơn hôm nay
            vì đã tự truy cập được log)
```

---

## Problem Card #3 — Tìm hướng dẫn / quy định trong Discord khóa VIN AI

**Problem 1 câu:**
Học viên khóa VIN AI (~500+ người) mất thời gian tìm lại các hướng dẫn và quy định chung vì nội dung nằm rải rác qua nhiều channel Discord và bị chat thường nhật đẩy trôi.

**Actor:**
Học viên khóa VIN AI cần tra một quy định hoặc hướng dẫn (format nộp bài, cấu trúc repo, deadline, quy trình chung). Người bị ảnh hưởng kèm theo: TA và giảng viên phải trả lời lặp lại.

**Thời điểm / bối cảnh:**
Trước khi làm bài hoặc trước khi nộp — thường là lúc gấp deadline.

**Current workflow:**

```text
1. Học viên cần tra một quy định/hướng dẫn
2. Không nhớ nội dung đó được đăng ở channel nào
3. Đoán từ khóa, dùng search của Discord                <-- BOTTLENECK
   → kết quả lẫn lộn giữa thông báo chính thức và chat tán gẫu
4. Scroll ngược từng channel khả nghi
5. Không thấy → hỏi lại trong channel hỏi đáp
6. Chờ TA/giảng viên trả lời — dù câu này đã từng được trả lời
```

**Bottleneck:**
Bước 3-4. Nội dung câu trả lời **đã tồn tại**, vấn đề thuần túy là chi phí tìm lại: không phân biệt được đâu là nguồn chính thức, không có mục lục.

**Impact:**
- Mỗi lần tìm mất `[?]` phút, nhân với 500+ học viên
- TA/giảng viên trả lời lặp cùng một câu hỏi
- Nguy cơ làm sai format / thiếu field vì không tìm ra quy định, phải làm lại

**Success metric:**

| Chỉ số | Hiện trạng | Mục tiêu | Cách đo |
|---|---|---|---|
| Thời gian tìm ra một quy định | `[?]` phút | Dưới 2 phút | Bấm giờ 5 câu hỏi mẫu, so trước/sau |
| Tỉ lệ tự tìm được mà không phải hỏi lại | `[?]` % | Trên `[?]` % | Poll nhanh trong lớp |
| Số câu hỏi trùng lặp TA phải trả lời/tuần | `[?]` | Giảm `[?]` % | Đếm trong channel hỏi đáp |

**Non-AI alternative:** ⭐ *có thể đã đủ*

Một trang index duy nhất được pin: "Quy định & hướng dẫn — mục lục", liệt kê từng mục kèm link thẳng tới message gốc. Cộng thêm một channel `#thông-báo-chính-thức` chỉ chứa nội dung chính thức, cấm chat.
Cách này rẻ, không rủi ro, và **nhiều khả năng giải được phần lớn case** — cần kiểm chứng ở Phase 4 trước khi nghĩ tới AI.

**AI hypothesis:**
Bot Q&A đánh index nội dung các channel thông báo, trả lời câu hỏi bằng tiếng Việt tự nhiên và **luôn kèm link tới message gốc** để học viên tự kiểm.
Giá trị thêm so với trang index: xử lý được câu hỏi diễn đạt tự do, không cần biết trước từ khóa đúng.

**Quick gut:**
- [x] No AI / process fix — *nên thử trang index trước*
- [ ] Rule
- [x] Workflow — *nếu index thủ công không đủ: bot Q&A trả lời kèm link nguồn*
- [ ] Agent
- [ ] Chưa biết

### Draft workflow — Card #3

```text
CURRENT STATE — [?] phút/lần tra cứu

[Cần tra một quy định]
→ [Đoán channel: [?]']
→ [Search Discord bằng từ khóa đoán: [?]']     <-- BOTTLENECK
   (kết quả lẫn thông báo chính thức với chat thường)
→ [Scroll ngược từng channel: [?]']
→ [Không thấy → hỏi lại trong channel hỏi đáp]
→ [Chờ TA trả lời: [?]']

FUTURE STATE — mục tiêu dưới 2 phút

── LỚP 1: process fix (không AI, thử trước) ──
[Cần tra một quy định]
→ [Mở trang index được pin: "Quy định & hướng dẫn"]
→ [Bấm link thẳng tới message gốc]
   Ước tính giải được phần lớn case — CẦN VALIDATE ở Phase 4

── LỚP 2: thêm AI, chỉ khi lớp 1 không đủ ──
→ [Hỏi bot bằng câu tự nhiên]
→ [AI trả lời NGẮN + BẮT BUỘC kèm link message gốc]
→ [NGƯỜI: học viên tự mở link kiểm lại]        <-- HUMAN BOUNDARY
→ [Câu hỏi bot không trả lời được → tự chuyển cho TA]

Boundary:
- Bot CHỈ trả lời từ nội dung đã đăng chính thức, KHÔNG tự chế quy định
- Bot LUÔN kèm link nguồn; không có nguồn thì phải nói "không tìm thấy"
- Bot KHÔNG trả lời câu hỏi về điểm số hoặc trường hợp cá nhân
- Cần xác nhận: có được phép đọc/index dữ liệu Discord của khóa không

Fallback: bot không chắc → chuyển câu hỏi cho TA như quy trình hiện tại
```

---

## Card tôi muốn pitch nhất

```text
Card #1 — Nội dung lỗi ở Telegram, trạng thái ở Jira, hai bên không liên kết
```

**Vì sao:**

```text
1. Tần suất cao nhất trong ba card. Nó không xảy ra "khi có sự cố" mà
   xảy ra ở MỌI vòng test của MỌI chức năng. Team đã có Jira chạy ổn
   (Ready for test → Cần xem lại), nên đây không phải bài "thiếu tool"
   mà là bài "hai nửa thông tin nằm ở hai nơi".

2. Giải Card #1 kéo theo Card #2: nếu nội dung lỗi nằm ngay trong card
   kèm tài khoản và thời điểm, dev không còn phải hỏi lại tester rồi chờ.
   Một bài giải được hai nghẽn.

3. Tôi đã LOẠI hai phương án non-AI bằng bằng chứng, không phải bằng
   cảm tính — đây là phần tôi tự tin nhất khi pitch:
   - PROCESS FIX (tester comment thẳng vào Jira) → loại: tester vẫn sẽ
     dùng Telegram, đây là thói quen đang chạy
   - RULE (bot đính ảnh theo mã card)            → loại: tin nhắn thật
     KHÔNG hề có mã card
   - AGENT                                        → thừa, không cần AI
     tự lập kế hoạch hay tự đổi bước
   Còn lại đúng một mức hợp lý: WORKFLOW.

4. Có bằng chứng thật: ảnh chụp một bug report nguyên bản, cộng khối
   lượng 3-4 bug/ngày. Không phải con số ước lượng trong đầu.

5. Metric đo được bằng dữ liệu CÓ SẴN, không cần dựng gì mới: chấm
   20 bug report xem đủ field không, đếm số lượt hỏi lại tester.
```

**Câu hỏi tôi muốn nhóm challenge:**

```text
1. Câu tôi muốn bị đánh mạnh nhất: tôi đã loại process fix vì "tester
   sẽ không đổi thói quen". Nhưng đó là kết luận hay là sự đầu hàng?
   Nếu lead ra quy định cứng thì có đổi được không? Tôi có đang dùng AI
   để né một vấn đề KỶ LUẬT QUY TRÌNH không?

2. AI hỏi ngược tester ngay trên Telegram ("mấy giờ? tài khoản nào?")
   nghe hay, nhưng liệu tester có thấy phiền và bắt đầu phớt lờ bot
   không? Nếu bot bị lơ thì cả thiết kế sụp.

3. Team chưa có bảng ownership module. Nếu ngay cả người thật cũng không
   biết bug thuộc về ai, AI dựa vào đâu để gợi ý đúng người? Có phải vấn
   đề gốc là THIẾU BẢNG PHÂN CÔNG chứ không phải thiếu AI?

4. Với 15-20 bug/tuần, một người trực triage mất bao lâu mỗi ngày? Nếu
   chỉ 20 phút/ngày thì có đáng xây hệ thống không, hay cứ cử người?
```

---

## Giả định cần validate (Phase 4)

Danh sách toàn bộ `[?]` — mang sang Phase 4 để đo hoặc hỏi, không dùng số ước lượng thay số thật.

| # | Giả định / số liệu chưa có | Cách kiểm chứng dự kiến |
|---|---|---|
| 1 | ~~Bao nhiêu bug/tuần?~~ **ĐÃ TRẢ LỜI: 3-4 bug/ngày ≈ 15-20 bug/tuần** | ✅ Đã xác nhận (ước lượng của người trong team) |
| 2 | ~~Tester có chịu comment thẳng vào Jira không?~~ **ĐÃ TRẢ LỜI: không — tester vẫn sẽ comment trên Telegram.** Có ảnh chụp tin nhắn thật làm bằng chứng | ✅ Đã xác nhận — phương án process fix bị loại |
| 3 | Thời gian dev phải bỏ ra để tìm nội dung lỗi ứng với một card `Cần xem lại` | Bấm giờ 10 card gần nhất |
| 3b | Trung bình mỗi bug phải hỏi lại tester mấy lượt trước khi tái hiện được | Đếm trên 20 bug liên tiếp |
| 4 | Một chức năng trung bình quay về `Cần xem lại` mấy lần | Đếm lịch sử chuyển trạng thái trên Jira |
| 5 | Tỉ lệ bug **khách hàng** báo trên Telegram được tạo thành card Jira | Đối chiếu tin nhắn có ảnh 2 tuần với card Jira cùng kỳ |
| 6 | Bug khách báo bị treo bao lâu trước khi có người nhận | Rà lịch sử chat + Jira |
| 7 | Thời gian trung bình điều tra một bug prod; bao nhiêu % là chờ hỏi lại tester + chờ xin log | Tự bấm giờ 5 bug tiếp theo |
| 8 | Bao nhiêu % bug phải hỏi lại tester mới tái hiện được | Đếm trên 10 bug gần nhất |
| 9 | Log hiện nằm ở mấy nơi (server nào, file nào) | Hỏi người cầm server |
| 10 | ~~Có rào cản gì khiến chưa cấp quyền đọc log cho dev?~~ **ĐÃ TRẢ LỜI: chưa ai làm, không có rào cản kỹ thuật hay bảo mật** | ✅ Đã xác nhận |
| 11 | Team dev bao nhiêu người; đã có bảng ownership module chưa (hiện *hình như* chưa) | Hỏi lead |
| 12 | Thời gian trung bình tìm một quy định trong Discord; tỉ lệ tìm được | Poll nhanh trong nhóm lab + lớp |
| 13 | Số câu hỏi trùng lặp TA phải trả lời mỗi tuần | Rà channel hỏi đáp 1 tuần |
| 14 | Có được phép đọc / index dữ liệu Discord của khóa không | Hỏi TA/giảng viên |

---

## Ghi chú dùng AI ở Phase 1-2 *(để dành cho reflection Phase 7)*

| Việc | Tôi tự làm gì | AI hỗ trợ gì | Tôi bác bỏ / sửa gì |
|---|---|---|---|
| Scan problem | Chọn ra các problem thật đã trải qua từ danh sách gợi ý, bỏ những cái không đúng với mình | Đưa danh sách gợi ý theo 4 lăng kính khi tôi chưa nghĩ ra được gì | *(điền sau)* |
| Số liệu | Từ chối điền số tôi chưa đo được | Đánh dấu `[?]` và gom thành danh sách giả định | AI không được điền số thay tôi |
| Phân tích liên hệ | Xác nhận đúng với thực tế công ty | Chỉ ra vấn đề "báo bug qua Telegram" và "điều tra bug" là hai khúc của cùng một dòng chảy | *(điền sau)* |
| Phản biện | Kiểm lại xem có đúng là quyền truy cập không | Chỉ ra bottleneck của Card #2 là vấn đề quyền truy cập, không phải bài toán AI | *(điền sau)* |
| Sửa giả định sai lần 1 | **Tôi bác bỏ giả định "team chưa dùng Jira"** — thực tế team có Jira và kéo thả trạng thái bình thường | AI suy đoán sai vì tôi mới chỉ kể "không ai phân loại" | Bài toán đổi hẳn: không phải *thiếu tool tracking* mà là *khoảng trống giữa Telegram và Jira* |
| Sửa giả định sai lần 2 | **Tôi bác bỏ tiếp giả định "bug biến mất khỏi Jira"** — tôi mô tả luồng thật: dev kéo card sang `Ready for test`, tester test sai thì kéo về `Cần xem lại` | AI đã kết luận quá mạnh dựa trên một câu nói ngắn của tôi | Bài toán đổi lần nữa và lần này mới đúng: card **đã tồn tại**, cái thiếu là **nội dung lỗi** — trạng thái ở Jira còn mô tả lỗi ở Telegram. Card #1 phải tách thành 2 luồng: tester test chức năng (có card sẵn) và khách báo lỗi (không có card) |
| Hệ quả lên kết luận | Xác nhận "chưa cấp quyền log chỉ vì chưa ai làm" | AI dùng thông tin này để hạ mức đề xuất của Card #2 xuống No AI | Vì không có rào cản kỹ thuật nào, kết luận "fix bằng process, không cần AI" trở nên chắc chắn thay vì chỉ là suy đoán |
| Đưa bằng chứng thật | **Tôi đưa ảnh chụp một bug report nguyên bản trên Telegram** thay vì mô tả lại bằng lời | AI đọc ảnh và chỉ ra tin nhắn thiếu 5 loại thông tin, trong đó có mã card | Ảnh này **loại bỏ hai phương án** mà AI đã đề xuất ở vòng trước: rule bám theo mã card (vì tin nhắn không có mã) và process fix bắt tester dùng Jira (vì tester vẫn sẽ dùng Telegram). Bài học: một ảnh chụp thật có giá trị hơn nhiều vòng suy luận |
