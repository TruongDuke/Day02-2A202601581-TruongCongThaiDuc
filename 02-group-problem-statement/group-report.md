# Group Report — Day 02


## Thành viên nhóm


| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|-----|-----------|-------------|--------------------|
| 1   | Phạm Quốc Tuấn          |      01983       |          Thư kí          |
| 2   |     Trần Văn Hiếu      |         02030    |         Thành viên           |
| 3   |     Trần Trung Hiếu      |         02002    |        Thành viên            |
| 4   |         Trương Công Thái Đức  |      01581       |       Thành viên             |
| 5   |    Hoàng Mạnh Dũng       |        01213     |            Thành viên        |


---


# 02 — Group Problem Statement


## Group convergence


Nhóm 5 người, mỗi người share top 3. Tổng cộng 15 candidates.


### Bước 3.1 — Trình bày top 2-3 của từng người


> Cột `Người đưa ra` đã đủ 15 dòng. Ba cột bên phải hiện mới điền cho các candidate vào shortlist — thành viên nào muốn bổ sung chi tiết candidate của mình thì điền thêm.


| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---|---|---|---|---|---|
| 1 | Trần Văn Hiếu | Tư vấn quán ăn / tour | | | |
| 2 | Trần Văn Hiếu | Trả lời câu hỏi lặp lại | | | |
| 3 | Trương Công Thái Đức | Tra cứu hướng dẫn/thông báo của khóa học | Học viên (500+), TA/giảng viên | Search trả kết quả lẫn thông báo chính thức với chat thường; không tìm thấy thì hỏi lại câu đã có người hỏi | No AI trước — trang mục lục ghim; AI diễn giải chỉ khi cần |
| 4 | Phạm Quốc Tuấn | Tra cứu quy chế học vụ | | | |
| 5 | Trần Trung Hiếu | Tìm tài liệu domain AI project | | | |
| 6 | Trần Trung Hiếu | Tóm tắt PDF | | | |
| 7 | Trần Văn Hiếu | Bàn giao ca | | | |
| 8 | Trương Công Thái Đức | Nội dung lỗi tách rời Telegram/Jira | Dev, tester | Card Jira ghi "Cần xem lại" nhưng không nói sai cái gì; nội dung lỗi nằm ở Telegram dạng ảnh | Workflow — rule bắt tin nhắn + AI đọc ảnh + người xác nhận |
| 9 | Hoàng Mạnh Dũng | Theo dõi chỉ số sức khỏe | | | |
| 10 | Trần Trung Hiếu | Quản lý deadline | | | |
| 11 | Trương Công Thái Đức | Điều tra lỗi môi trường qua log | Dev, người giữ quyền truy cập server | Phải hỏi lại tester mới đủ thông tin tái hiện; log chỉ một người xem được | No AI — cấp quyền đọc log + chuẩn hóa bug report |
| 12 | Phạm Quốc Tuấn | Phân tích lỗi sai TOEIC | | | |
| 13 | Phạm Quốc Tuấn | Phân tích log lỗi AI nhúng | | | |
| 14 | Hoàng Mạnh Dũng | Lịch tập + dinh dưỡng | | | |
| 15 | Hoàng Mạnh Dũng | Hướng dẫn quy trình khám bệnh | | | |


Phân bố: mỗi thành viên đóng góp đúng 3 candidate — Trần Văn Hiếu (1, 2, 7) · Phạm Quốc Tuấn (4, 12, 13) · Trần Trung Hiếu (5, 6, 10) · Trương Công Thái Đức (3, 8, 11) · Hoàng Mạnh Dũng (9, 14, 15).


### Bước 3.2 — Gom trùng / cluster


| Cluster | Candidate examples | Pattern chung |
|---|---|---|
| Tra cứu & tổng hợp thông tin phân tán | Tư vấn quán ăn/tour, trả lời câu hỏi lặp lại, tra cứu hướng dẫn/thông báo của khóa học, tra cứu quy chế học vụ, tìm tài liệu domain AI project, tóm tắt PDF | Thông tin nằm rải rác nhiều nguồn/kênh, người dùng phải tự tìm và tổng hợp thủ công |
| Trạng thái/bàn giao thông tin giữa nhiều người | Bàn giao ca, nội dung lỗi tách rời Telegram/Jira, theo dõi chỉ số sức khỏe, quản lý deadline | Thông tin về 1 sự việc nằm rải rác giữa nhiều người/hệ thống, cần tổng hợp & bàn giao chính xác |
| Phân tích lỗi/log để tìm nguyên nhân | Điều tra lỗi môi trường qua log, phân tích lỗi sai TOEIC, phân tích log lỗi AI nhúng | Đọc dữ liệu lỗi để chẩn đoán nguyên nhân và đề xuất hướng sửa |
| Điều phối/hướng dẫn theo thời gian thực | Lịch tập + dinh dưỡng, hướng dẫn quy trình khám bệnh | Cá nhân hóa lộ trình hoặc điều hướng người dùng theo tình huống đang diễn ra |


## Shortlist và score


### Bước 3.3 — Shortlist


| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| Tra cứu hướng dẫn/thông báo của khóa học | Cả 5 thành viên đều là actor và dùng chung một hệ thống kênh nên validate ngay được; không cần quyền truy cập dữ liệu đặc biệt | 5 người đau vì 5 lý do khác nhau; mẫu 5 người có thể không đại diện cho 500+ học viên |
| Nội dung lỗi Telegram/Jira | Evidence sâu nhất, có ảnh chụp bug report thật; so sánh Rule/Workflow/Agent rất rõ | Chỉ 1/5 hiểu domain dev/QA; giải pháp 3 lớp quá lớn so với thời gian lab |
| Bàn giao ca | Workflow rõ, so sánh Rule/Workflow/Agent tốt | Chỉ 1 người có trải nghiệm thật để cả nhóm khai thác sâu |
| Phân tích lỗi sai TOEIC | Impact đo được, scope gọn | Evidence còn mỏng |
| Lịch tập + dinh dưỡng | Workflow rõ | Cá nhân hóa cao, khó làm gọn trong lab |
| Tra cứu quy chế học vụ | Actor rõ | Quy chế khác nhau giữa các trường; cần PDF chính thức chưa chắc lấy được trong buổi lab |


### Bước 3.4 — Score để đồng thuận


| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Tra cứu hướng dẫn/thông báo của khóa học | 5 | 4 | 3 | 3 | 5 | 4 | 5 | 29 |
| Nội dung lỗi Telegram/Jira | 5 | 5 | 5 | 5 | 3 | 5 | 2 | 30 |
| Bàn giao ca | 4 | 5 | 4 | 3 | 4 | 5 | 2 | 27 |
| Phân tích lỗi sai TOEIC | 4 | 4 | 3 | 4 | 4 | 4 | 3 | 26 |
| Lịch tập + dinh dưỡng | 4 | 5 | 3 | 4 | 3 | 4 | 3 | 26 |
| Tra cứu quy chế học vụ | 5 | 4 | 3 | 3 | 3 | 3 | 4 | 25 |


Nhóm chọn: **Tra cứu hướng dẫn/quy định/thông báo trong kênh trao đổi của khóa học**.


Vì sao chọn:


- Actor là chính 5 thành viên trong nhóm (đều đang học khóa này, **cùng dùng chung một hệ thống kênh thông báo**) nên validate được ngay lập tức, không cần khảo sát bên ngoài.
- Vì cả 5 dùng chung một kênh nên pilot chạy chung được và đo chung được — khác với candidate "quy chế học vụ" vốn phụ thuộc từng trường riêng.
- Không phụ thuộc nguồn dữ liệu khó tiếp cận (không cần quyền truy cập hệ thống nội bộ công ty, chỉ cần các kênh thông báo công khai của khóa học).
- Scope vừa sức để đi hết các bước còn lại trong thời gian lab.
- Điểm tổng gần với candidate cao nhất (29 so với 30) nhưng rủi ro thấp hơn nhiều.


Vì sao không chọn các bài khác:


- Nội dung lỗi Telegram/Jira: điểm cao nhất và evidence/research sâu nhất, nhưng chỉ 1/5 thành viên thực sự hiểu domain dev/QA; giải pháp đề xuất có 3 lớp (Rule + AI + Human) khá lớn so với thời gian lab còn lại.
- Bàn giao ca: workflow và so sánh Rule/Workflow/Agent rất tốt, nhưng chỉ 1 người có trải nghiệm thật để cả nhóm khai thác sâu thêm.
- Tra cứu quy chế học vụ: actor rõ nhưng quy chế khác nhau giữa các trường — nếu thành viên không cùng trường, domain không dùng chung được; cần dữ liệu PDF chính thức chưa chắc lấy được trong buổi lab.


Nếu có disagreement, nhóm xử lý thế nào:


```text
Có tranh luận, nhưng nhóm thống nhất được nhanh.

Điểm gây tranh luận:
Bài "Nội dung lỗi Telegram/Jira" chấm được 30 điểm, cao nhất bảng và hơn bài
được chọn 1 điểm. Nếu chỉ nhìn tổng điểm thì lẽ ra phải chọn bài này.

Cách nhóm xử lý:
Thay vì so tổng điểm, nhóm tách riêng hai tiêu chí quyết định được kết quả:
- "Nhóm hiểu domain": bài Telegram/Jira được 2/5, bài tra cứu được 5/5
- "Làm trong lab": bài Telegram/Jira được 3/5, bài tra cứu được 5/5
Nhóm thống nhất rằng với một buổi lab 4 tiếng, hai tiêu chí này quan trọng
hơn độ sâu evidence. Một bài mà phần lớn thành viên không hiểu domain thì cả
nhóm không cùng đào sâu được, và phần deep-dive dễ biến thành một người làm.

Kết quả:
Thành viên đề xuất bài Telegram/Jira đồng ý với lý do loại. Bài đó cần bảng
ownership module và quyền truy cập hệ thống nội bộ công ty — những thứ cả
nhóm không kiểm chứng được trong buổi lab. Chọn bài mà cả 5 người đều là
actor giúp validate ngay tại chỗ, đúng tinh thần "kiểm chứng trước khi viết
Problem Statement".

Bài Telegram/Jira được giữ lại trong báo cáo cá nhân, có thể quay lại nếu
có thời gian dài hơn.
```


## Quick validation


Vì actor chính là 5 thành viên trong nhóm, cách nhanh nhất là mỗi người tự trả lời 5 câu hỏi dưới đây từ trải nghiệm thật của mình (không cần khảo sát ngoài):


### Câu trả lời từng người (5/5 — đủ)


| # | Q1: Lần gần nhất | Q2: Cách tìm | Q3: Bước khó chịu nhất | Q4: Thời gian mất | Q5: Muốn thay đổi gì |
|---|---|---|---|---|---|
| 1 | Hôm qua | Lướt tay qua các kênh thông báo | Không có search hiệu quả, phải tự lướt tìm | ~15-20 phút | Muốn có "trợ lý tìm kiếm" hướng dẫn/thông báo |
| 2 | Sáng nay | Tìm kiếm từ khoá | Tìm ra thông báo nhưng nội dung quy định vẫn chưa rõ ràng | *(chưa nêu cụ thể)* | Muốn có hướng dẫn cụ thể hơn, không chỉ link mà giải thích rõ |
| 3 | Tuần trước | Lướt tay, tìm quy định/lịch/phòng học | Phải tự lướt tìm rải rác nhiều loại thông tin khác nhau | 15 phút | Muốn có lập lịch/timeline tổng hợp |
| 4 | Hôm kìa | Hỏi lại nhóm | Giao diện (kênh/công cụ hiện tại) khó tương tác | *(chưa nêu)* | *(chưa nêu)* |
| 5 | Vừa xong (ngay lúc trả lời) | Hỏi trực tiếp giảng viên | Thời gian chờ trả lời không cố định, tuỳ lúc | Biến động, không cố định | Muốn hướng dẫn theo cá nhân |


| Nguồn | Số người | Tín hiệu xác nhận | Tín hiệu phản bác / mở rộng | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Tự phỏng vấn thành viên | 5/5 | Cả 5 đều có trải nghiệm thật và gần đây (từ "tuần trước" đến "vừa xong") → pain xảy ra thường xuyên, không phải hiếm gặp; baseline ~15-20 phút/lần ở các trường hợp có nêu số (người 1, 3) | Không phải ai cũng đau vì cùng 1 lý do — 5 người mô tả 5 kiểu khó chịu và 5 kiểu mong muốn khác nhau | Cần thu hẹp Boundary: giữ lại phần chung (tra cứu lại thông tin/quy định đã có, đang phải tự xoay xở qua nhiều cách khác nhau); tách "lập lịch timeline" (người 3) và "hướng dẫn cá nhân hoá" (người 5) ra làm candidate khác, không đưa vào bài này |


Câu hỏi dùng để tự phỏng vấn:


```text
1. Lần gần nhất bạn tìm lại một thông báo/hướng dẫn/quy định cũ trong kênh của khóa học là khi nào?
2. Bạn tìm bằng cách nào (search từ khóa, hỏi lại nhóm, lướt tay)?
3. Bước nào mất thời gian hoặc khó chịu nhất?
4. Bạn mất khoảng bao lâu để tìm ra (hoặc bỏ cuộc và hỏi lại)?
5. Nếu tốt hơn, bạn muốn thay đổi điều gì?
```


## Research giải pháp


| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Wallu — AI Discord Support Bot | https://wallubot.com/ | Trả lời câu hỏi hỗ trợ tự động trong Discord dựa trên knowledge base được nạp sẵn, hoạt động 24/7 | Không cần đội ngũ trực, học từ dữ liệu có sẵn của server | Không rõ có bắt buộc trích dẫn nguồn hay không → rủi ro hallucinate nếu không kiểm soát | Cần ràng buộc bắt buộc kèm link nguồn cho mọi câu trả lời, không để bot tự bịa khi thiếu dữ liệu |
| FAQ Bot (Discord App Directory) | https://discord.com/discovery/applications/1351844496253386854 | Khớp câu hỏi thành viên với các cặp Q&A định nghĩa sẵn, trả lời câu tương tự | Đơn giản, không cần AI phức tạp — gần mức Rule/Workflow nhẹ | Chỉ trả lời tốt câu hỏi khớp mẫu có sẵn; không xử lý được câu hỏi diễn đạt khác hoặc câu hỏi mới | Xác nhận mức Rule (Q&A cố định) đã giải quyết được phần lớn nhu cầu cơ bản mà không cần AI phức tạp |
| Chat Data — Telegram AI Chatbot | https://www.chat-data.com/telegram-chatbot | Tạo chatbot Telegram huấn luyện từ knowledge base/FAQ tải lên, trả lời ngay trong group | Triển khai nhanh, không cần dev, hoạt động ngay trong kênh hiện có (không cần thành viên chuyển sang app khác) | Cần duy trì cập nhật knowledge base khi có thông báo mới; công cụ thương mại có thể tốn phí | Gợi ý dùng tin nhắn ghim làm nguồn ngữ cảnh cho bot — khớp với ý tưởng "mục lục ghim" ở mức Rule |


Research takeaway:


```text
Cả 3 case đều xác nhận: mức Rule (mục lục ghim, FAQ tĩnh) đã giải quyết được phần lớn nhu cầu cơ bản mà không cần AI phức tạp. AI chỉ thực sự cần khi câu hỏi diễn đạt khác với mẫu có sẵn, hoặc khi nội dung quá nhiều để duy trì thủ công. Nên bắt đầu từ Rule, chỉ nâng lên Workflow (AI + bắt buộc trích nguồn) nếu Rule không đủ.
```


Tham khảo thêm về thực hành human-centered AI: [PAIR Guidebook — Google](https://pair.withgoogle.com/guidebook/). Phần kiểm tra ranh giới người–máy theo khung này nằm ở mục [Rule / Workflow / Agent](#rule--workflow--agent).


## Bằng chứng đã chắc và giả định còn mở


Tách rõ phần đã có bằng chứng khỏi phần còn là giả định, trước khi viết Problem Statement.


### Đã có bằng chứng


| Nội dung | Bằng chứng | Nguồn |
|---|---|---|
| Pain có thật và xảy ra thường xuyên | 5/5 thành viên đều gặp; lần gần nhất trải dài từ "tuần trước" đến "ngay lúc trả lời" | Tự phỏng vấn nội bộ nhóm |
| Không có nguồn tra cứu chung | 5/5 người dùng 4 cách xoay xở khác nhau, không ai dùng chung một nguồn | Tự phỏng vấn nội bộ nhóm |
| Đã tồn tại công cụ giải bài tương tự | 3 sản phẩm đang chạy thật, đã kiểm link | wallubot.com · Discord App Directory · chat-data.com |
| Mức Rule là cách tiếp cận phổ biến và đủ dùng cho phần lớn case | FAQ Bot hoạt động thuần khớp mẫu Q&A cố định, không dùng AI | Discord App Directory |


### Giả định còn mở


| # | Giả định | Vì sao chưa chắc | Cách kiểm chứng |
|---|---|---|---|
| 1 | Baseline 15-20 phút/lần đại diện cho cả nhóm | Chỉ 2/5 người nêu số; 3/5 không đưa con số nào | Hỏi lại 3 người còn lại, hoặc bấm giờ 5 lần tra cứu tiếp theo |
| 2 | Chỉ 1/5 người vướng dạng "tìm ra nhưng không hiểu rõ" | Mẫu 5 người quá nhỏ để kết luận tỷ lệ, mà đây lại là căn cứ chính để hoãn phần AI | Khảo sát rộng hơn trước khi chốt bỏ phần AI |
| 3 | Trang mục lục ghim giải quyết được phần lớn nhu cầu | Suy ra từ mô tả sản phẩm của 3 tool, chưa có số liệu và nhóm chưa tự thử | Chính là mục tiêu của pilot 1-2 tuần |
| 4 | Sẽ có người duy trì cập nhật trang mục lục | Chưa xác định ai là owner — đây là rủi ro lớn nhất của pilot | Chốt tên người phụ trách trước khi bắt đầu pilot |
| 5 | Học viên sẽ biết tới và thực sự dùng trang mục lục | Công cụ tốt nhưng không ai biết thì không giảm được câu hỏi lặp | Sau pilot hỏi "bạn có biết trang này không" trước, rồi mới hỏi "có dùng không" |
| 6 | Mẫu 5 thành viên đại diện được cho 500+ học viên | 5 người cùng một nhóm lab, có thể có thói quen giống nhau và không phản ánh hết cách xoay xở của cả khóa | Poll nhanh 20-30 học viên ngoài nhóm trên kênh chung |
| 7 | 500+ học viên đều gặp vấn đề này ở mức đáng kể | Con số 500+ là quy mô lớp, chưa phải số người thực sự gặp pain mỗi tuần | Poll: "tuần này bạn có phải tìm lại một thông báo cũ không?" |
| 8 | Nhóm được phép tạo và ghim trang trong kênh chính | Chưa hỏi người quản trị kênh | Hỏi giảng viên hoặc quản trị viên kênh |
| 9 | Hiện mỗi tuần có bao nhiêu câu hỏi lặp | Metric "giảm số lần hỏi lại" chưa có số gốc nên chưa đo được | Đếm câu hỏi trùng trong kênh 1 tuần |


## Workflow before/after


Current workflow (dựng từ câu trả lời thật của 5/5 thành viên — mỗi người một cách xoay xở khác nhau, đây chính là bằng chứng cho thấy thiếu 1 điểm tra cứu chung):


```text
CURRENT STATE — 4 nhánh tùy người, không có nguồn chung


[Có câu hỏi/cần tra cứu thông tin/quy định/lịch của khóa học]
→ Nhánh A (người 1, 3): [Lướt tay qua các kênh thông báo] <-- bottleneck, 15-20 phút
→ Nhánh B (người 2): [Search từ khoá] → [Tìm ra nhưng quy định đọc vẫn chưa rõ ràng] <-- bottleneck khác: hiểu, không phải tìm
→ Nhánh C (người 4): [Hỏi lại trong nhóm] <-- bottleneck: giao diện/kênh khó tương tác
→ Nhánh D (người 5): [Hỏi trực tiếp giảng viên] <-- bottleneck: thời gian chờ trả lời không cố định


→ Không ai dùng chung 1 nguồn tra cứu chính thức — mỗi người tự chọn cách khác nhau
```


Future workflow (draft — dựa trên AI hypothesis + research, cần nhóm review lại):


```text
FUTURE STATE


[Học viên nhập câu hỏi vào công cụ tìm kiếm/hỏi đáp]
→ [Rule: đối chiếu với mục lục ghim (thông báo chính thức của khóa học)]
→ [Nếu khớp: trả lời kèm link nguồn gốc]
→ [Nếu không khớp mẫu có sẵn: AI tóm tắt/giải thích từ nội dung đã ghim, bắt buộc kèm trích dẫn nguồn]
→ [Học viên đọc & tự xác nhận]  <-- human boundary
→ [Nếu vẫn không rõ: liên hệ TA/giảng viên]  -- fallback


Fallback: Nếu không có nguồn phù hợp → công cụ trả lời "không biết", không tự suy diễn.
```


Before/after impact:


| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Tổng thời gian | ~15-20 phút/lần | Dưới 3 phút | Baseline từ 2/5 người nêu số cụ thể |
| Số cách xoay xở | 4 cách khác nhau (lướt tay, từ khoá, hỏi nhóm, hỏi GV) | 1 nguồn tra cứu chung | Mục tiêu chính: hội tụ về 1 điểm tra cứu |
| Bước thủ công | Toàn bộ thủ công | Chỉ còn bước đọc & tự xác nhận | Human boundary giữ nguyên |
| Bottleneck chính | Không có nguồn chung + đôi khi tìm ra vẫn không hiểu rõ | Rule trả lời câu khớp mẫu; AI diễn giải câu chưa khớp (nếu cần) | Tùy vào tỷ lệ 2 dạng đau sau pilot |
| Risk mới | Không có AI hallucination | Có rủi ro nếu sau này thêm AI mà thiếu kiểm soát nguồn | Ràng buộc bắt buộc trích dẫn nguồn |


## Problem Statement v0


| Field | Nội dung |
|---|---|
| **Actor** | Học viên khóa VIN AI (**hơn 500 người**) cần tra lại thông báo/quy định/lịch; TA và giảng viên phải trả lời lặp lại cùng một câu hỏi |
| **Workflow** | Học viên tra cứu lại thông báo/quy định/lịch cũ bằng nhiều cách khác nhau (lướt tay, tìm từ khoá, hỏi lại nhóm, hỏi trực tiếp giảng viên) vì không có 1 nguồn tra cứu chính thức, dễ tìm |
| **Bottleneck** | Không có điểm tra cứu tập trung, đáng tin cậy: thông báo chính thức lẫn với tin nhắn trao đổi thường ngày, khiến mỗi người phải tự chọn cách xoay xở riêng (5/5 người dùng 5 cách khác nhau) |
| **Impact** | Baseline ~15-20 phút/lần với các trường hợp có nêu số (2/5); 5/5 xác nhận pain xảy ra thường xuyên (gần nhất trải dài từ "tuần trước" đến "ngay lúc trả lời") |
| **Success Metric** | Giảm thời gian tự tra cứu từ ~15-20 phút xuống dưới 3 phút; giảm số lần phải hỏi lại nhóm/giảng viên cho câu hỏi đã có câu trả lời sẵn |
| **Boundary** | Chỉ trả lời dựa trên nội dung đã ghim/xác thực chính thức, không tự suy diễn khi thiếu nguồn; không thay thế vai trò TA/giảng viên với câu hỏi ngoài phạm vi thông báo. **Không bao gồm**: lập lịch/timeline cá nhân (nhu cầu người 3) và hướng dẫn cá nhân hoá theo từng học viên (nhu cầu người 5) — đây là 2 vấn đề khác, để làm candidate riêng sau |


## Độ phù hợp với AI


Bài toán của nhóm nằm ở ô nào trong ma trận độ mơ hồ × độ phức tạp?


```text
Độ phức tạp THẤP  ×  Độ mơ hồ THẤP  →  Rule hoặc workflow đơn giản thường đủ
```


Vì sao:


```text
- Độ mơ hồ THẤP: câu hỏi tra cứu có đáp án đúng/sai rõ ràng. Một thông báo
  hoặc quy định chỉ có một nội dung đúng, không phải loại câu hỏi mà nhiều
  cách trả lời đều chấp nhận được.
- Độ phức tạp THẤP: chỉ 1-2 bước (nhận câu hỏi → trả về đúng thông báo kèm
  link nguồn), một nguồn dữ liệu duy nhất là các thông báo đã ghim.
- AI KHÔNG cần tự quyết định bước tiếp theo: cả 5/5 người chỉ cần tra cứu
  bị động, không ai cần AI chủ động làm gì thêm.

Ngoại lệ đã ghi nhận: nhu cầu của người 2 ("tìm ra nhưng vẫn không hiểu rõ
quy định") rơi vào ô độ mơ hồ CAO — diễn giải một quy định thì nhiều cách
viết vẫn chấp nhận được. Đây chính là lý do phần AI diễn giải được giữ lại
như bước nâng cấp CÓ ĐIỀU KIỆN, không làm ngay từ đầu.
```


## Rule / Workflow / Agent


| Mức | Phương án | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | Trang mục lục ghim, liệt kê từng nội dung kèm link trực tiếp tới thông báo gốc | Đủ nếu phần lớn câu hỏi lặp chỉ cần tìm đúng link | Không xử lý được câu hỏi diễn đạt khác từ ngữ so với thông báo gốc | ✅ **CHỌN** — làm pilot đầu tiên |
| **Workflow** | Công cụ tìm kiếm/hỏi đáp có AI tóm tắt, bắt buộc kèm link nguồn cho mọi câu trả lời | Hợp nếu mục lục ghim vẫn không đủ, cần hiểu ý câu hỏi tự nhiên | Trả lời sai/hallucinate nếu không kiểm soát tốt nguồn dữ liệu | ⏸ **CÓ ĐIỀU KIỆN** — chỉ nâng lên sau khi đo kết quả pilot |
| **Agent** | Agent tự tổng hợp, tự cập nhật kho tri thức, tự trả lời đa kênh | Chỉ cần nếu phải tự động theo dõi nhiều kênh và tự quyết định khi nào cập nhật | Rủi ro cao, khó kiểm soát, chưa chắc cần thiết ở quy mô này | ❌ **KHÔNG CHỌN** |


Mức chọn:


```text
Bắt đầu bằng Rule (mục lục ghim); có thể cần nâng lên Workflow nhẹ nếu Rule không giải quyết được vấn đề "tìm ra nhưng vẫn không hiểu rõ".
```


Vì sao:


```text
- Cả 3 tool research được đều xác nhận: mục lục/FAQ tĩnh (Rule) giải quyết phần lớn nhu cầu tìm kiếm cơ bản mà không cần AI.
- Trong 5/5 câu trả lời validation, 3/5 người (1, 3, 4) đau vì KHÔNG CÓ nguồn chung để tra cứu/hỏi — đây là vấn đề Rule (mục lục ghim) giải quyết trực tiếp được.
- Chỉ 1/5 người (2) đau vì "tìm ra rồi vẫn không hiểu rõ" — đây mới là phần cần AI diễn giải. Vì chỉ chiếm thiểu số trong mẫu, ưu tiên làm Rule trước, đo lại xem còn bao nhiêu người vẫn vướng dạng này sau khi có mục lục.
- Người 5 (hỏi thẳng giảng viên) và người 3 (muốn lập lịch timeline) không thuộc phạm vi Rule/Workflow này — đã đưa vào Boundary loại trừ.
- Chưa cần Agent: không có nhu cầu tự động theo dõi nhiều kênh hay tự quyết định hành động tiếp theo; toàn bộ 5 người chỉ cần tra cứu bị động, không cần AI chủ động làm gì thêm.
```


Vì sao không chọn mức đơn giản hơn:


```text
Rule đã là mức thấp nhất trong ba mức so sánh. Phương án duy nhất đơn giản
hơn là giữ nguyên hiện trạng — mà hiện trạng chính là vấn đề (5 người tự
xoay xở theo 5 cách khác nhau). Nhóm cố ý chọn mức thấp nhất vẫn giải được
điểm nghẽn, và giữ phần AI như bước nâng cấp có điều kiện.
```


### Kiểm tra ranh giới người–máy


Đối chiếu theo khung human-centered AI của [PAIR Guidebook](https://pair.withgoogle.com/guidebook/):


| Khía cạnh | Nhóm xử lý thế nào |
|---|---|
| Nhu cầu người dùng & định nghĩa thành công | Nhu cầu lấy từ 5/5 câu trả lời thật, không suy đoán. Thành công định nghĩa bằng thời gian tra cứu và số lần hỏi lại — không phải bằng "có dùng AI hay không" |
| Giải thích & niềm tin | Mọi câu trả lời bắt buộc kèm link tới thông báo gốc để người đọc tự đối chiếu. Không có link thì không trả lời |
| Phản hồi & quyền kiểm soát | Người dùng luôn tự đọc và tự xác nhận. Công cụ không thay mặt ai đưa quyết định |
| Lỗi & thất bại có kiểm soát | Không tìm thấy nguồn phù hợp thì trả lời "không biết" thay vì suy diễn. Fallback: chuyển sang hỏi TA/giảng viên như quy trình hiện tại |


## Problem Statement v1


| Field | Nội dung |
|---|---|
| **Actor** | Học viên khóa VIN AI (**hơn 500 người**) cần tra lại thông báo/quy định/lịch; TA và giảng viên phải trả lời lặp lại cùng một câu hỏi |
| **Workflow** | Học viên cần tra cứu lại thông báo/quy định/lịch cũ → không có nguồn chung → tự chọn 1 trong 4 cách (lướt tay, từ khoá, hỏi nhóm, hỏi giảng viên) → tốn thời gian hoặc phải chờ người khác trả lời |
| **Bottleneck** | Không có điểm tra cứu tập trung đáng tin cậy (3/5 người); thiểu số (1/5) còn vướng thêm ở việc quy định đọc không rõ ràng dù đã tìm ra |
| **Impact** | ~15-20 phút/lần ở các trường hợp có nêu số; pain xảy ra thường xuyên với cả 5/5 người trong tuần gần nhất |
| **Success Metric** | Giảm thời gian tự tra cứu từ ~15-20 phút xuống dưới 3 phút; giảm số lần hỏi lại nhóm/giảng viên cho câu đã có câu trả lời sẵn — đo lại sau 1-2 tuần pilot mục lục ghim |
| **Boundary** | Chỉ trả lời dựa trên nội dung đã ghim/xác thực; không tự suy diễn khi thiếu nguồn; không thay vai trò TA/giảng viên. Không bao gồm lập lịch/timeline cá nhân và hướng dẫn cá nhân hoá (để làm candidate riêng) |
| **AI intervention point** | Chưa kích hoạt AI ở pilot đầu tiên (chỉ Rule). Chỉ thêm AI diễn giải (kèm trích dẫn nguồn bắt buộc) nếu sau pilot vẫn còn nhiều người vướng dạng "tìm ra nhưng không hiểu rõ" |
| **Mức chọn** | Rule (mục lục ghim) trước — pilot nhỏ, đo lại rồi mới quyết có cần thêm Workflow/AI hay không |
| **Rủi ro & người thật kiểm tra** | Rủi ro: mục lục ghim không được duy trì cập nhật; nếu sau này thêm AI thì rủi ro diễn giải sai quy định. Người thật kiểm tra: TA/giảng viên xác nhận và cập nhật nội dung ghim; học viên tự đối chiếu link nguồn trước khi tin |


### Success Metric chi tiết


| Chỉ số | Hiện trạng | Mục tiêu | Cách đo |
|---|---|---|---|
| Thời gian tự tra cứu một thông báo/quy định | ~15-20 phút/lần *(từ 2/5 người có nêu số)* | Dưới 3 phút | Bấm giờ 5 câu hỏi mẫu, so trước và sau khi có mục lục ghim |
| Số câu hỏi trùng lặp mỗi tuần | **Chưa đếm** — đo trong tuần đầu pilot làm mốc | Giảm 50% sau 2 tuần | Đếm câu hỏi trùng trong kênh hỏi đáp, so tuần trước và sau khi ghim mục lục |
| Số cách xoay xở khác nhau trong nhóm | 4 cách (lướt tay, từ khóa, hỏi nhóm, hỏi giảng viên) | 1 nguồn tra cứu chung | Hỏi lại 5 thành viên sau pilot: lần gần nhất bạn tra bằng cách nào |


Để hiện trạng của chỉ số thứ hai là "chưa đếm" thay vì điền số ước lượng — đúng nguyên tắc không dùng số liệu chưa kiểm được nguồn.


## Final decision


Tự kiểm trước khi chốt:


| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | **Yes** | Actor là học viên; workflow dựng từ câu trả lời thật của 5/5 thành viên, có 4 nhánh xoay xở khác nhau |
| Baseline và success metric đã đo được chưa? | **Not Yet** | Baseline 15-20 phút chỉ đến từ 2/5 người; metric "giảm số lần hỏi lại" chưa có số gốc — sẽ đo trong tuần đầu pilot |
| Có data/input đủ dùng chưa? | **Yes** | Pilot chỉ dùng thông báo công khai đã đăng, không cần quyền truy cập đặc biệt |
| Nếu AI sai, hậu quả có chấp nhận được không? | **Yes** | Pilot chưa có AI nên chưa phát sinh rủi ro. Khi thêm AI, ràng buộc bắt buộc trích nguồn giúp người đọc tự kiểm |
| Có người review/owner vận hành không? | **Not Yet** | Chưa xác định ai duy trì cập nhật trang mục lục — đây là rủi ro lớn nhất của pilot, cần chốt tên trước khi bắt đầu |
| Có cách non-AI đơn giản hơn không? | **Yes** | Chính pilot đã là phương án non-AI. Nhóm cố ý chọn mức đơn giản nhất trước |


Hai ô `Not Yet` không làm đổi quyết định Go, vì cả hai đều nằm trong phạm vi pilot 1-2 tuần sẽ giải quyết. Ghi thật thay vì tick Yes toàn bộ.


Decision:


```text
Go — scope nhỏ: pilot Rule (mục lục ghim) trước, chưa build AI ngay
```


Lý do:


```text
- Đủ 5/5 xác nhận: pain có thật, xảy ra thường xuyên (trải dài từ "tuần trước" đến "ngay lúc trả lời"), và rõ ràng đến từ việc THIẾU 1 nguồn tra cứu chung — mỗi người đang tự xoay xở bằng 4 cách khác nhau.
- Non-AI alternative (Rule) đã được cả research (3 tool) và đa số validation (3/5 người) xác nhận là đủ để giải quyết phần lớn — nên bắt đầu từ đây thay vì nhảy thẳng vào AI.
- Rủi ro thấp: pilot chỉ là 1 trang mục lục ghim, không có AI nên không có rủi ro hallucination ngay từ đầu.
- Việc có cần AI hay không (cho nhóm thiểu số 1/5 vướng "tìm ra nhưng không hiểu rõ") sẽ được quyết định SAU khi đo lại kết quả pilot — không quyết định trước khi có bằng chứng.
```


Pilot nhỏ nhất:


```text
- Tạo 1 trang/mục lục ghim liệt kê thông báo, quy định, lịch, phòng học chính thức, mỗi mục kèm link tới nguồn gốc.
- Ghim trang này ở vị trí dễ thấy nhất trong kênh chính của khóa học.
- Theo dõi 1-2 tuần: hỏi lại 5 thành viên (và vài học viên khác nếu được) xem số lần phải hỏi lại nhóm/giảng viên có giảm không, thời gian tự tìm có giảm không.
```


Exit / điều kiện nâng lên Workflow (thêm AI):


```text
- Nếu sau pilot, số câu hỏi dạng "tìm ra nhưng không hiểu rõ quy định" (như người 2) vẫn còn nhiều → cân nhắc thêm lớp AI diễn giải, bắt buộc trích dẫn nguồn.
- Nếu số câu hỏi lặp không giảm dù đã có mục lục ghim → trước khi đổ lỗi cho thiếu AI, kiểm tra lại xem học viên có biết trang mục lục tồn tại hay không (vấn đề truyền thông, không phải vấn đề công cụ).
```




