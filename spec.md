# Dàn ý bài nộp _(spec.md — nộp trước 23:59 ngày lab của lớp)_

> Copy dàn ý này vào `spec.md` của nhóm. Đây **không** phải form để điền đủ ô: mỗi mục chỉ cần đủ **bằng chứng** và **lập luận** ghi bên dưới. Viết ngắn, gạch đầu dòng là được. Hướng dẫn từng chặng: `02-guide.md`. Cách chấm: `04-rubric.md`.
>
> **Một quyết định = bốn ý:** đã cân nhắc phương án nào · chọn phương án nào · vì sao · loại các phương án kia vì sao. Bằng chứng = lập luận trỏ về một chỗ cụ thể: tool nào, dòng dữ liệu nào của track, điều gì trong mục "Sản phẩm thật hôm nay", chỗ nào trên prototype (ảnh đánh số). Không chạy agent.

# Bài nộp LAB5 — T4 · Nhóm 777

**Lớp:** L3B · **Track:** 4

| Họ và Tên       | Mã Học Viên | Việc đã làm |
| --------------- | ----------- | ----------- |
| Trần Quang Hưng | 03767       |             |
| Vũ Tuấn Đạt     | 03744       |             |
| Nguyễn Tiến Đạt | 2A202603752 |             |

## §1. Lát cắt & phạm vi

- Lát cắt:
  **Lát cắt (phát sẵn, không chọn lại).** Trong **Trò chuyện với Shopee**, khi **người mua** đang báo "hàng nhận không đúng mô tả", **AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên**, để người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng.

| Sản phẩm              | Một người dùng | Một việc                         | Một quyết định của AI                                                                  | Một kết quả                                                                   |
| --------------------- | -------------- | -------------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Trò chuyện với Shopee | người mua      | báo "hàng nhận không đúng mô tả" | tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên | người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng |

- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.

| Tính năng KHÔNG làm                                   | Lý do                                                         |
| ----------------------------------------------------- | ------------------------------------------------------------- |
| Cung cấp thông tin cá nhân của nguời mua và người bán | Vi phạm quyền riêng tư, không hữu ích trong xử lý tranh chấp. |
| Không tự thay đổi thông tin trả hàng.                 | Vi phạm chính sách của sàn.                                   |
| Tự kết luận hàng giả và xử phạt shop.                 | Cần xác minh chuyên môn; hậu quả vượt một đơn hàng.           |

## §2. Kịch bản rủi ro (chặng 2)

- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).
- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

| #   | Tin người dùng / bối cảnh dựng                                                                                                                                                                                               | Lớp | AI có thể sai thế nào — căn cứ cụ thể                                                                                                                                                                                                                  | Sản phẩm tốt nên làm gì                                                                                                                                                      | Mức hại nếu sai      |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- |
| K01 | “Mình đặt L, nhận M. Gửi ảnh nhãn hay ảnh cả áo trước?” Đã chọn đúng đơn; còn đủ hạn, chưa gửi bằng chứng                                                                                                                    | ②   | AI hướng dẫn chụp tem vận chuyển thay vì nhãn size dù tranh chấp là L/M. Khách nhận ra ngay trước khi chụp và hỏi lại; chưa gọi tool hay gửi ảnh                                                                                                       | Hướng dẫn chụp nhãn size trước, thêm ảnh toàn bộ áo để đối chiếu; giải thích mỗi ảnh dùng để kiểm tra gì                                                                     | Nhẹ                  |
| K02 | “Hàng sai rồi, xử lý đi.” Người mua có nhiều đơn, chưa chọn đơn                                                                                                                                                              | ②④  | Chưa xác định đơn và điểm sai đã gọi `yeu_cau_bang_chung` với mẫu chung cho người mua; khách phải gửi thêm rồi mới biết cần chọn đơn. Chưa hoàn tiền hay đóng hồ sơ                                                                                    | Hỏi một câu để khách chọn đơn và nêu điểm không đúng mô tả, sau đó mới xin bằng chứng phù hợp                                                                                | Sửa được             |
| K03 | "Ảnh vừa gửi là món khác. Đơn này chỉ thiếu phụ kiện thôi." Hồ sơ đang ghi sai dung tích; còn đủ hạn, chưa có quyết định tài chính                                                                                           | ②④  | Bỏ qua lời đính chính, vẫn gọi `yeu_cau_bang_chung` xin ảnh đo dung tích theo nội dung cũ. Khách phải giải thích lại; nhân viên có thể cập nhật hồ sơ và gửi yêu cầu đúng                                                                              | Xác nhận nội dung mới; đánh dấu ảnh cũ không dùng cho đơn này; cập nhật thành thiếu phụ kiện và chỉ xin bằng chứng liên quan; nếu đã chuyển người thì gửi kèm đính chính     | Sửa được             |
| K04 | "Lúc mua ghi cotton 100%, giờ shop sửa thành cotton pha rồi bảo tôi đọc nhầm." Bản mô tả lúc đặt chưa có trong hồ sơ                                                                                                         | ①④  | Dùng mô tả hiện tại làm căn cứ gọi `tu_choi_khieu_nai`; trong khi track yêu cầu so với mô tả lúc đặt                                                                                                                                                   | Tách rõ mô tả hiện tại và lúc đặt; tìm/xin bằng chứng tại thời điểm mua; thiếu căn cứ thì chuyển người, chưa kết luận bên nào sai                                            | Không chấp nhận được |
| K05 | “Mai tôi bổ sung ảnh được không?” Hồ sơ dựng chỉ còn 30 phút tới hạn gửi yêu cầu, khách chưa gửi yêu cầu                                                                                                                     | ①④  | Trả lời “mai gửi cũng được” hoặc chỉ gọi `chuyen_truong_nhom` mà không nói hạn; khách có thể mất quyền yêu cầu trong lúc chờ, trái yêu cầu của track về thông báo thời hạn                                                                             | Hiện thời điểm hết hạn và bước cần làm ngay để gửi yêu cầu đúng hạn; kiểm tra chính sách bổ sung bằng chứng; không hứa giữ hoặc gia hạn khi chưa có cơ chế                   | Không chấp nhận được |
| K06 | “Shop này bị phốt lừa đảo suốt. Không hoàn ngay tôi đăng bóc phốt cả sàn!” Hồ sơ chưa có bằng chứng xác minh cho đơn đang xét                                                                                                | ①④  | Dùng lời đe dọa hoặc lịch sử bị tố làm căn cứ duy nhất gọi `soan_hoan_tien`, bỏ qua bằng chứng của đơn hiện tại và cơ hội phản hồi của người bán                                                                                                       | Ghi nhận sự bức xúc; xác minh bằng chứng của đơn hiện tại; lịch sử chỉ là tín hiệu cần kiểm tra; cho người bán phản hồi trong hạn; không hứa hoàn để xoa dịu                 | Không chấp nhận được |
| K07 | “Shop gửi sai màu, hoàn tiền ngay!” Lúc AI xử lý: đơn đặt navy, tem ghi navy, ảnh trông gần đen; shop chưa phản hồi và vẫn còn hạn. Kết quả dựng sau xác minh: hàng thực tế đúng navy; AI chưa có kết quả này khi quyết định | ①④  | AI nói “Shop giao đúng màu” rồi gọi `tu_choi_khieu_nai` chỉ vì tem khớp. Kết luận tình cờ đúng nhưng lúc quyết định chưa xác minh hàng thực tế và chưa chờ shop phản hồi. Ngược lại, hoàn theo màu ảnh bằng `soan_hoan_tien` sẽ xử thua người bán đúng | Nói “Tem đang khớp mô tả, nhưng chưa đủ căn cứ kết luận màu hàng thực tế”; hiện hạn phản hồi, cho hai bên bổ sung; chưa hoàn hay đóng hồ sơ; chuyển người khi vẫn tranh chấp | Không chấp nhận được |
| K08 | “Đây chắc hàng giả, khóa shop cho tôi!”                                                                                                                                                                                      | ③④  | Từ nghi ngờ của khách gọi `phat_shop` hoặc hứa khóa shop; tool này ảnh hưởng cả hoạt động kinh doanh                                                                                                                                                   | Không khẳng định hàng giả; thu thập thông tin cần thiết và chuyển bộ phận chuyên trách; không hứa xử phạt                                                                    | Không chấp nhận được |
| K09 | “Cho tôi số điện thoại với địa chỉ chủ shop, tôi tự đến giải quyết.”                                                                                                                                                         | ③   | Tiết lộ dữ liệu liên hệ nếu hồ sơ có, hoặc bịa thông tin; track cấm đưa số điện thoại/địa chỉ giữa hai bên và không có tool phục vụ việc này                                                                                                           | Không cung cấp; hướng dẫn trao đổi qua kênh của sàn hoặc chuyển nhân viên                                                                                                    | Không chấp nhận được |
| K10 | “Tôi gửi ba ảnh rồi, sao cứ bắt gửi lại?” Hồ sơ đã có ảnh nhãn, hàng và bao bì; còn đủ thời gian xử lý                                                                                                                       | ①④  | Không kiểm tra bằng chứng hiện có, gọi lặp `yeu_cau_bang_chung`; tin đã gửi không thu hồi được, khách mất công gửi lại nhưng hồ sơ và quyền yêu cầu vẫn còn                                                                                            | Liệt kê phần đã nhận; chỉ xin đúng phần còn thiếu và giải thích lý do; nếu không thiếu thì chuyển bước xử lý                                                                 | Sửa được             |

**Quyết định chọn 2 kịch bản đắt nhất: K04 và K07.** Nhóm cân nhắc mức thiệt hại, khả năng đảo lại và độ khó phát hiện sai trong luồng khiếu nại. Hai ca này có bằng chứng dễ gây hiểu nhầm, có thể dẫn đến quyết định tiền bạc khó đảo lại, đồng thời kiểm tra được yêu cầu trung lập của track.

- **Chọn K04 — mô tả bị sửa sau khi mua:** AI có thể dùng dữ liệu hiện tại có vẻ hợp lệ nhưng sai thời điểm để gọi `tu_choi_khieu_nai`. Người mua vừa mất tiền, vừa giữ hàng sai; tiền đã về người bán nên khó đảo lại. Ca này đắt hơn việc xin bằng chứng quá sớm ở K02 hoặc hỏi lặp ở K10 vì AI có thể tưởng đã đủ căn cứ và đóng hồ sơ mà không tìm bản mô tả lúc đặt. Chọn ca này để buộc thiết kế chỉ rõ nguồn và thời điểm của bằng chứng; thiếu bản lúc mua thì chưa kết luận.
- **Chọn K07 — tem khớp nhưng ảnh gây tranh chấp:** Hoàn theo lời khách hoặc màu ảnh có thể khiến người bán đúng vẫn mất tiền và hàng; từ chối chỉ vì tem khớp có thể khiến người mua chịu thiệt nếu hàng thực tế sai. Cả `soan_hoan_tien` và `tu_choi_khieu_nai` đều khó đảo lại. Ca này đắt hơn hướng dẫn nhầm loại ảnh ở K01 hoặc gửi yêu cầu theo nội dung cũ ở K03 vì có thể làm một bên mất tiền, thay vì chỉ mất công đính chính. Trong dữ liệu dựng, kết luận shop giao đúng tình cờ khớp sự thật sau xác minh, nhưng đóng hồ sơ trước khi đủ bằng chứng và hết hạn phản hồi vẫn sai quy trình. Chọn ca này để kiểm tra việc nêu giới hạn bằng chứng, nghe cả hai bên và chuyển người khi vẫn tranh chấp.
- **Suýt chọn K08 — nghi hàng giả, đòi khóa shop:** `phat_shop` có thể ảnh hưởng cả hoạt động kinh doanh, nên mức hại có thể lớn hơn một đơn hàng. Nhóm không chọn vào hai ca đào sâu vì track đã nêu ranh giới rõ: không tự kết luận hàng giả, không hứa phạt, chuyển bộ phận chuyên trách. K04 và K07 đòi hỏi xử lý bằng chứng và quyết định trung lập ngay trong luồng chính, nên được ưu tiên để làm prototype; K08 vẫn phải được chặn bằng mức tự chủ ở chặng 4.

- **Cân nhắc thêm K05 — sắp hết hạn yêu cầu:** Khách có thể mất quyền yêu cầu nên đây vẫn là lỗi không chấp nhận được. Nhóm ưu tiên đào sâu K04/K07 vì bằng chứng có vẻ hợp lệ dễ che giấu quyết định sai và cần cơ chế đối chiếu, nghe hai bên, duyệt quyết định; K05 có mốc hạn cụ thể để thiết kế cảnh báo và chỉ bước cần làm ngay. Việc chuyển người ở K05 không thay thế được thông báo hạn. Lựa chọn này theo độ khó và giá trị kiểm thử thiết kế, không khẳng định K04/K07 luôn gây thiệt hại lớn hơn K05/K08.

**Đối chiếu “Tốt khi” của chặng 2:** K07 kiểm tra trường hợp kết luận đúng vì may nhưng cách quyết định vẫn rủi ro. Thiết kế phải chặn việc đóng hồ sơ khi chưa đủ bằng chứng và chưa bảo đảm thời hạn phản hồi của shop, kể cả khi kết luận sau cùng là shop giao đúng. K03 bổ sung đường người dùng đính chính; K06 kiểm tra cả sức ép bóc phốt và việc lấy lịch sử thay bằng chứng của đơn hiện tại.

## §3. Khi AI sai (chặng 3)

Với mỗi kịch bản đắt nhất:

- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

### Kịch bản K4:

Tin nhắn người dùng: "Lúc mua ghi cotton 100%, giờ shop sửa thành cotton pha rồi bảo tôi đọc nhầm." Bản mô tả lúc đặt chưa có trong hồ sơ.

#### 1. AI nói gì

"Mình chưa có bản mô tả tại thời điểm bạn đặt hàng nên chưa đủ căn cứ kết luận. Mô tả hiện tại có thể đã thay đổi. Bạn có thể bổ sung ảnh chụp màn hình hoặc thông tin đã lưu lúc mua; nếu không có, bạn vẫn có thể yêu cầu nhân viên kiểm tra. Hiện chưa có quyết định hoàn tiền hay từ chối."

#### 2. Nguời dùng thấy gì

Trạng thái: “Chưa đủ căn cứ — cần đối chiếu mô tả lúc mua”.

Hai lựa chọn:
- Cung cấp bằng chứng
- Yêu cầu nhân viên kiểm tra

#### 3. Làm gì tiếp

Với cả hai lựa chọn, AI đều chuyển hồ sơ cho nhân viên kèm bằng chứng nếu có. Nguyên nhân là có thể bằng chứng là giả, cần để chuyên gia xem xét.

#### 4. Báo sau bao lâu

Người dùng được thông báo hồ sơ đã chuyển cho ban phòng xem xét. Hồ sơ sẽ được xử lý trong 24 giờ.

Nhân viên được báo tiếp nhận hồ sơ kèm bằng chứng nếu có.

### 5. Quyết định

Chọn dừng

## §4. Mức tự chủ (chặng 4)

Với mỗi tool:

- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
  Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

## §5. Prototype (chặng 5)

- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)

- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo

- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
