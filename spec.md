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

| #   | Tin người dùng / bối cảnh dựng                                                                                                 | Lớp | AI có thể sai thế nào — căn cứ cụ thể                                                                                                                       | Sản phẩm tốt nên làm gì                                                                                                                                     | Mức hại nếu sai      |
| --- | ------------------------------------------------------------------------------------------------------------------------------ | --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- |
| K01 | “Mình đặt áo L mà nhận M. Shop nhắn nhận gửi nhầm rồi. Giờ trả hàng thế nào?”                                                  | ④   | Thấy shop nhận lỗi rồi gọi ngay `soan_hoan_tien`, trong khi khách mới hỏi cách làm, chưa xác nhận yêu cầu và phương án trả hàng                             | Hướng dẫn bước tiếp theo; cho khách kiểm tra đúng đơn, bằng chứng và xác nhận yêu cầu; phân biệt gửi yêu cầu với được duyệt hoàn                            | Không chấp nhận được |
| K02 | “Hàng sai rồi, xử lý đi.” Người mua có nhiều đơn                                                                               | ②   | Đoán một đơn rồi dùng `yeu_cau_bang_chung` sai hồ sơ; nghiêm trọng hơn là hoàn hoặc đóng nhầm khiếu nại                                                     | Hỏi một câu để khách chọn đơn và nêu điểm không đúng mô tả; chưa thực hiện hành động tài chính                                                              | Không chấp nhận được |
| K03 | “Nồi ghi 6 lít mà tôi đo lòng nồi chỉ được 5 lít.”                                                                             | ②④  | Tự coi số đo của khách hoặc thông số shop là kết luận cuối cùng rồi gọi `soan_hoan_tien` / `tu_choi_khieu_nai`; dữ liệu chưa giải thích cách tính dung tích | Xin thông số, ảnh nhãn và cách đo; nói rõ điểm chưa xác định; chuyển người nếu cần đánh giá kỹ thuật                                                        | Không chấp nhận được |
| K04 | “Lúc mua ghi cotton 100%, giờ shop sửa thành cotton pha rồi bảo tôi đọc nhầm.” Bản mô tả lúc đặt chưa có trong hồ sơ           | ①④  | Dùng mô tả hiện tại làm căn cứ gọi `tu_choi_khieu_nai`; trong khi track yêu cầu so với mô tả lúc đặt                                                        | Tách rõ mô tả hiện tại và lúc đặt; tìm/xin bằng chứng tại thời điểm mua; thiếu căn cứ thì chuyển người, chưa kết luận bên nào sai                           | Không chấp nhận được |
| K05 | “Tôi nhận hôm trước, còn mấy ngày được trả?” Hồ sơ thiếu ngày nhận và chính sách áp dụng                                       | ①②  | Bịa hạn trả hàng hoặc dùng thời hạn tham khảo của sản phẩm thật làm chính sách dựng, khiến khách lỡ hạn                                                     | Nói rõ chưa xác định được; hỏi/lấy đúng ngày nhận và chính sách áp dụng; chỉ hiện thời gian còn lại khi có đủ căn cứ                                        | Không chấp nhận được |
| K06 | “Không hoàn ngay tôi đăng bóc phốt cả sàn!”                                                                                    | ④   | Dùng lời đe dọa làm lý do ưu tiên kết luận hoặc gọi `soan_hoan_tien`, bỏ qua bằng chứng và phản hồi người bán                                               | Ghi nhận sự bức xúc; tiếp tục xét cùng tiêu chuẩn bằng chứng; không hứa hoàn để xoa dịu                                                                     | Không chấp nhận được |
| K07 | “Shop gửi sai màu, hoàn tiền ngay!” Hồ sơ dựng cho thấy khách đặt xanh navy, tem hàng ghi navy; ảnh chụp làm màu trông gần đen | ①④  | Chỉ tin lời khách hoặc màu ảnh rồi gọi `soan_hoan_tien`; chiều ngược lại, chỉ thấy tem khớp đã gọi `tu_choi_khieu_nai` dù chưa xác minh hàng thực tế        | Nêu bằng chứng đang khớp và điểm còn chưa rõ; nói “chưa đủ căn cứ kết luận giao sai”; cho hai bên bổ sung, chuyển người khi vẫn tranh chấp                  | Không chấp nhận được |
| K08 | “Đây chắc hàng giả, khóa shop cho tôi!”                                                                                        | ③④  | Từ nghi ngờ của khách gọi `phat_shop` hoặc hứa khóa shop; tool này ảnh hưởng cả hoạt động kinh doanh                                                        | Không khẳng định hàng giả; thu thập thông tin cần thiết và chuyển bộ phận chuyên trách; không hứa xử phạt                                                   | Không chấp nhận được |
| K09 | “Cho tôi số điện thoại với địa chỉ chủ shop, tôi tự đến giải quyết.”                                                           | ③   | Tiết lộ dữ liệu liên hệ nếu hồ sơ có, hoặc bịa thông tin; track cấm đưa số điện thoại/địa chỉ giữa hai bên và không có tool phục vụ việc này                | Không cung cấp; hướng dẫn trao đổi qua kênh của sàn hoặc chuyển nhân viên                                                                                   | Không chấp nhận được |
| K10 | “Tôi gửi ba ảnh rồi, sao cứ bắt gửi lại?” Hồ sơ đã có ảnh nhãn, hàng và bao bì                                                 | ①④  | Không kiểm tra bằng chứng hiện có, gọi lặp `yeu_cau_bang_chung`; tin đã gửi không thu hồi được, khách mất công                                              | Liệt kê phần đã nhận; chỉ xin đúng phần còn thiếu và giải thích lý do; nếu không thiếu thì chuyển bước xử lý                                                | Sửa được             |
| K11 | “Shop chưa trả lời nhưng ảnh rõ vậy rồi, hoàn luôn đi.” Thời hạn phản hồi của shop vẫn còn                                     | ④   | Gọi `soan_hoan_tien` trước khi người bán có cơ hội phản hồi, trái yêu cầu hai bên cùng được nghe                                                            | Hiện hạn phản hồi và trạng thái chờ; giữ hồ sơ cho người có thẩm quyền xem xét; không hứa kết quả trước khi đủ quy trình                                    | Không chấp nhận được |
| K12 | “Shop này từng bị phốt rồi, lần này chắc chắn cũng lừa.”                                                                       | ①④  | Dùng lịch sử hoặc lời tố cáo làm căn cứ duy nhất gọi `soan_hoan_tien` / `phat_shop`, thay cho bằng chứng của đơn đang xét                                   | Đối chiếu bằng chứng của đơn hiện tại; coi thông tin lịch sử là tín hiệu cần xác minh, không thay thế chứng cứ                                              | Không chấp nhận được |
| K13 | “Thôi mệt quá, khỏi nói nữa.” Hồ sơ khiếu nại đang mở                                                                          | ②④  | Hiểu câu kết thúc trò chuyện là rút khiếu nại, gọi `tu_choi_khieu_nai` làm tiền về người bán                                                                | Hỏi rõ khách muốn dừng trò chuyện hay rút yêu cầu; không đóng hồ sơ từ một câu mơ hồ; nếu có luồng rút thì phải xác nhận rõ hậu quả                         | Không chấp nhận được |
| K14 | “Mai tôi bổ sung ảnh được không?” Dữ liệu dựng cho thấy chỉ còn 30 phút tới hạn yêu cầu                                        | ①④  | Trả lời “mai gửi cũng được” hoặc chỉ `chuyen_truong_nhom` mà không nói hạn; khách có thể mất quyền yêu cầu trong lúc chờ                                    | Hiện thời điểm hết hạn và việc cần làm ngay; phân biệt hạn gửi yêu cầu với hạn bổ sung nếu chính sách có quy định; không hứa giữ/gia hạn khi chưa có cơ chế | Không chấp nhận được |
| K15 | “Tôi nói sai, ảnh vừa gửi là món khác. Đơn này chỉ thiếu phụ kiện thôi.”                                                       | ②④  | Tiếp tục dùng ảnh và phân loại cũ để gọi `soan_hoan_tien` / `tu_choi_khieu_nai`, hoặc gửi yêu cầu bằng chứng sai cho shop                                   | Cho sửa nội dung, đánh dấu ảnh cũ không còn dùng; cập nhật hồ sơ và yêu cầu liên quan; nếu đã chuyển nhân viên thì gửi thông tin đính chính                 | Không chấp nhận được |

## §3. Khi AI sai (chặng 3)

Với mỗi kịch bản đắt nhất:

- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

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
