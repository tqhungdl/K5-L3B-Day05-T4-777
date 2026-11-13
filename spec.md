# Dàn ý bài nộp _(spec.md — nộp trước 23:59 ngày lab của lớp)_

> Copy dàn ý này vào `spec.md` của nhóm. Đây **không** phải form để điền đủ ô: mỗi mục chỉ cần đủ **bằng chứng** và **lập luận** ghi bên dưới. Viết ngắn, gạch đầu dòng là được. Hướng dẫn từng chặng: `02-guide.md`. Cách chấm: `04-rubric.md`.
>
> **Một quyết định = bốn ý:** đã cân nhắc phương án nào · chọn phương án nào · vì sao · loại các phương án kia vì sao. Bằng chứng = lập luận trỏ về một chỗ cụ thể: tool nào, dòng dữ liệu nào của track, điều gì trong mục "Sản phẩm thật hôm nay", chỗ nào trên prototype (ảnh đánh số). Không chạy agent.

# Bài nộp LAB5 — T4 · Nhóm 777

**Lớp:** L3B · **Track:** 4

| Họ và Tên       | Mã Học Viên | Việc đã làm                                  |
| --------------- | ----------- | -------------------------------------------- |
| Trần Quang Hưng | 2A202603767 | §1. Lát cắt, hỗ trợ §3.                      |
| Vũ Tuấn Đạt     | 2A202603744 | Dựng UI prototype, hỗ trợ §2, §3.            |
| Nguyễn Tiến Đạt | 2A202603752 | Xây dựng kịch bản, phân tích kịch bản, tools |

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

### K04 — Mô tả bị sửa sau khi mua

**Bối cảnh:** “Lúc mua ghi cotton 100%, giờ shop sửa thành cotton pha rồi bảo tôi đọc nhầm.” Bản mô tả lúc đặt chưa có trong hồ sơ. Căn cứ: K04 ở §2; track yêu cầu so với mô tả lúc đặt, trong khi `tu_choi_khieu_nai` đóng hồ sơ và chuyển tiền cho người bán, khó đảo lại.

#### 1. AI nói gì — nguyên văn

> “Mình chưa có bản mô tả tại thời điểm bạn đặt hàng nên chưa đủ căn cứ kết luận. Mô tả hiện tại không chứng minh nội dung lúc mua. Hồ sơ cần được nhân viên kiểm tra; bạn có thể bổ sung ảnh chụp hoặc thông tin đã lưu lúc mua, hoặc chọn ‘Tôi không có bản lưu’. Bạn không cần có ảnh lưu mới được chuyển kiểm tra. Hiện chưa có quyết định hoàn tiền hay từ chối.”

#### 2. Người dùng thấy gì

- Trạng thái **“Chưa đủ căn cứ — cần đối chiếu mô tả lúc mua”**.
- Thẻ bằng chứng tách ba phần: lời người mua “cotton 100%”; mô tả hiện tại “cotton pha”; mô tả lúc đặt **“Chưa có”**. Lời khai không được gắn nhãn đã xác minh. Nguồn và thời điểm chỉ hiện khi có dữ liệu; không bịa ngày hoặc đường dẫn bản lưu.
- Các nút **“Bổ sung bằng chứng”**, **“Tôi không có bản lưu / Yêu cầu nhân viên kiểm tra”**, **“Sửa thông tin”**. Bằng chứng được gắn nhãn “Chờ xác minh”; không có nút để AI tự hoàn tiền hay từ chối.
- Hiện hạn gửi yêu cầu của người mua riêng với hạn phản hồi của shop, kèm trạng thái yêu cầu đã gửi hay chưa. Nếu chưa gửi, hướng dẫn bước gửi trong hạn, không bảo khách chỉ chờ nhân viên.

#### 3. Làm gì tiếp; ai được báo, sau bao lâu

- Dù có hay không có bản lưu, hồ sơ đều đi qua `chuyen_truong_nhom` để trưởng nhóm/nhân viên được phân công đối chiếu nguồn và thời điểm; ảnh người mua gửi là căn cứ cần kiểm tra, chưa tự chứng minh shop đã sửa mô tả. Không bắt khách tìm ảnh vô hạn hoặc mặc định ảnh là giả.
- Khi chuyển thành công, người mua thấy mã hồ sơ, trạng thái **“Đã chuyển — chờ nhân viên”** và thời điểm dự kiến phản hồi lần đầu trong 24 giờ. Chỉ báo đã chuyển sau khi tool xác nhận thành công; nếu lỗi, hiện **“Chuyển chưa thành công”** và nút thử lại.
- Trưởng nhóm được báo ngay khi chuyển thành công, nhận lời trình bày, bằng chứng hiện có, nguồn/thời điểm, mục còn thiếu và các hạn liên quan. Người bán nhận yêu cầu cung cấp bản mô tả lúc mua hoặc bằng chứng liên quan qua `yeu_cau_bang_chung`, kèm hạn phản hồi cụ thể; thông báo cho hai bên không chứa số điện thoại, địa chỉ của bên kia.
- Nếu người mua không làm gì, hồ sơ vẫn được chuyển với ghi chú “Chưa bổ sung bản lưu”; không tự từ chối vì thiếu ảnh. Nếu quá mục tiêu 24 giờ chưa có phản hồi đầu tiên, giao diện báo chậm và hồ sơ được đánh dấu quá hạn cho trưởng nhóm theo dõi. Đây là cơ chế hàng đợi/thông báo đề xuất, cần thể hiện trong prototype; AI không có tool tự gia hạn hay tự quyết thay người.

#### 4. Quyết định và phương án đã loại

- **Chọn dừng kết luận và chuyển người**, đồng thời cho bổ sung bằng chứng: dữ liệu thiếu nằm ở thời điểm mua; nhân viên cần kiểm tra nguồn và nghe cả hai bên. Chuyển người dừng quyết định tiền bạc, không dừng hướng dẫn gửi yêu cầu đúng hạn.
- **Loại chỉ hỏi lại:** người mua có thể không có bản lưu; hỏi lặp không khôi phục được dữ liệu lịch sử và có thể làm hết hạn.
- **Loại chỉ trả lời kèm giới hạn rồi để khách tự xử lý:** nói “chưa chắc” không giải quyết tranh chấp hoặc ngăn `tu_choi_khieu_nai` dùng sai nguồn. Phải có người nhận hồ sơ và trạng thái theo dõi cụ thể.

#### 5. Loại lỗi và cách sửa

**Lỗi hệ thống:** dùng mô tả hiện tại thay cho mô tả lúc đặt là lỗi chọn nguồn/thời điểm, không phải lỗi người mua vì không lưu ảnh. Nếu AI đã kết luận sai, nói: **“Mình đã dùng mô tả hiện tại để đánh giá nội dung lúc bạn mua. Căn cứ đó chưa đủ; mình xin đính chính kết luận vừa rồi và chuyển hồ sơ để kiểm tra.”** Đồng thời đánh dấu kết luận cũ không còn là căn cứ và gửi đính chính cho người đang xử lý. Nếu đã đóng hồ sơ/chuyển tiền, phải báo trưởng nhóm xử lý hậu quả; không tuyên bố đã hoàn tác vì track không có tool hoàn tác quyết định này.

### K07 — Tem khớp mô tả nhưng ảnh gây tranh chấp

**Bối cảnh:** “Shop gửi sai màu, hoàn tiền ngay!” Đơn đặt navy, tem ghi navy, ảnh trông gần đen; shop chưa phản hồi và vẫn còn hạn. Kết quả dựng sau xác minh là hàng đúng navy, nhưng AI chưa được biết kết quả đó lúc quyết định. Căn cứ: K07 ở §2; cả `soan_hoan_tien` và `tu_choi_khieu_nai` đều chuyển tiền và khó đảo lại.

#### 1. AI nói gì — nguyên văn

> “Đơn của bạn đặt màu navy và tem cũng ghi navy, nhưng tem chưa đủ để kết luận màu hàng thực tế. Ảnh hiện tại trông gần đen; ánh sáng hoặc màn hình có thể ảnh hưởng màu hiển thị. Shop vẫn còn thời gian phản hồi. Bạn có thể bổ sung ảnh hàng và tem chụp cùng khung hình dưới ánh sáng tự nhiên nếu chưa có; mình chưa kết luận bên nào đúng và chưa thực hiện hoàn tiền hay đóng khiếu nại. Nếu bạn vẫn không đồng ý với phần đối chiếu, hãy chọn ‘Yêu cầu nhân viên kiểm tra’.”

#### 2. Người dùng thấy gì

- Trạng thái **“Chờ đối chiếu và phản hồi của shop — chưa có quyết định”**.
- Ba bằng chứng đặt cạnh nhau: màu lúc đặt “navy”, tem “navy”, ảnh khách gửi. Chú thích **“Tem khớp; màu hàng thực tế chưa xác minh”**, không hiện phần trăm chắc chắn không có căn cứ.
- Hạn phản hồi của shop bằng ngày giờ và thời gian còn lại; hạn gửi yêu cầu của khách hiển thị riêng. Nút **“Bổ sung ảnh”**, **“Sửa thông tin / ảnh gửi nhầm”**, **“Yêu cầu nhân viên kiểm tra”**.
- Phía shop thấy nội dung khiếu nại, bằng chứng liên quan và hạn phản hồi; có chỗ bổ sung bằng chứng hoặc xác nhận giao nhầm, không thấy dữ liệu liên hệ riêng của khách.

#### 3. Làm gì tiếp; ai được báo, sau bao lâu

- AI kiểm tra ảnh đã nhận trước khi gọi `yeu_cau_bang_chung`, chỉ xin phần thiếu và giải thích ảnh dùng để đối chiếu màu thực tế. Shop nhận yêu cầu phản hồi ngay khi tool gửi thành công; việc shop chưa trả lời khi còn hạn không được diễn giải là nhận lỗi.
- Nếu khách bổ sung ảnh, giao diện xác nhận đã nhận và vẫn ghi “Chờ xác minh”. Nếu khách sửa màu đặt hoặc báo ảnh nhầm, AI xác nhận nội dung mới, đánh dấu ảnh cũ không dùng để quyết định và cập nhật cho người đang xử lý; không bắt đầu lại hồ sơ.
- Khách có thể chuyển trưởng nhóm ngay bằng `chuyen_truong_nhom`. Nếu hết hạn shop phản hồi mà chưa thống nhất, hồ sơ cũng chuyển trưởng nhóm; không tự hoàn hoặc từ chối do một bên im lặng. Trưởng nhóm nhận cả bằng chứng thuận/nghịch, phần chưa xác minh, phản hồi hai bên và các hạn; sau chuyển thành công áp dụng mục tiêu phản hồi đầu tiên trong 24 giờ và cách báo chậm như K04.
- Nếu khách không thao tác, tiếp tục chờ phản hồi trong hạn đã hiện; hết hạn mà chưa giải quyết thì chuyển người. Chuyển sớm không rút ngắn cơ hội phản hồi của shop. Nếu chuyển thất bại, hiện rõ trạng thái lỗi và cho thử lại, không báo đã có nhân viên tiếp nhận.

#### 4. Quyết định và phương án đã loại

- **Chọn trả lời kèm giới hạn và xin đúng bằng chứng còn thiếu; chuyển người khi còn tranh chấp, hết hạn phản hồi hoặc khách yêu cầu.** Đã biết đơn và điểm tranh chấp nên có thể giải thích phần tem khớp, nhưng chưa đủ để quyết định tiền bạc.
- **Loại chỉ hỏi lại “Bạn đặt màu gì?”:** dữ liệu đã có navy; hỏi lại không giải quyết khác biệt giữa tem và màu thực tế, làm khách mất công.
- **Loại chuyển người ngay cho mọi ca:** có thể thu thập phần thiếu và nhận phản hồi shop trước, giảm chờ cho ca hai bên sớm thống nhất. Vẫn giữ nút chuyển người ngay và không dùng bước bổ sung để ngăn khách tiếp cận nhân viên.
- **Loại kết luận từ một bằng chứng:** hoàn theo màu ảnh có thể làm shop đúng mất tiền; từ chối theo tem có thể làm người mua chịu thiệt. Kết quả dựng cuối cùng “shop đúng” không hợp thức hóa quyết định sớm khi chưa xác minh và shop còn hạn phản hồi.

#### 5. Loại lỗi và cách sửa

**Lỗi ngữ cảnh** nếu hệ thống đọc đúng tem navy nhưng coi tem là đủ để trả lời tranh chấp về màu thực tế. Nếu đọc sai ảnh/tem thì là **lỗi hệ thống**. Không gọi việc khách thấy màu khác là lỗi người dùng khi chưa xác minh.

Nếu đã nói “Shop giao đúng màu”, đính chính: **“Mình đã kết luận quá sớm chỉ từ tem navy. Tem chưa xác minh được màu hàng thực tế; mình xin đính chính và sẽ đối chiếu thêm bằng chứng cùng phản hồi của shop.”** Cách sửa là tách “tem khớp” khỏi “hàng thực tế đúng”, giữ cơ hội phản hồi và chuyển người nếu chưa thống nhất. Nếu đã phát sinh chuyển tiền, báo trưởng nhóm xử lý, không hứa tự đảo giao dịch.

### Ba nguyên tắc HAX/PAIR áp dụng cho K04 và K07

| Nguyên tắc                             | Chỗ cụ thể ở K04                                                                                            | Chỗ cụ thể ở K07                                                                                           |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **G10 — Thu hẹp phạm vi khi nghi ngờ** | Câu “Mô tả hiện tại không chứng minh nội dung lúc mua”; dừng kết luận và chuyển người khi thiếu bản lúc đặt | Nhãn “Tem khớp; màu hàng thực tế chưa xác minh”; chưa hoàn hay từ chối khi bằng chứng còn mâu thuẫn        |
| **G11 — Giải thích vì sao**            | Thẻ tách lời người mua, mô tả hiện tại và bản lúc đặt còn thiếu, kèm nguồn/thời điểm nếu có                 | Hiện màu đặt, tem và ảnh cạnh nhau; giải thích giới hạn của ảnh và lý do chờ phản hồi shop                 |
| **G9 — Sửa dễ dàng**                   | Nút “Sửa thông tin”, cho bổ sung bản lưu; đính chính kết luận cũ và gửi cho người xử lý                     | Nút “Sửa thông tin / ảnh gửi nhầm”; đánh dấu ảnh cũ không dùng và cập nhật hồ sơ thay vì bắt khách làm lại |

### Lỗi câu chữ không cứu được và cơ chế thiết kế

- **K04:** AI nói “chưa chắc” nhưng vẫn gọi `tu_choi_khieu_nai` thì người mua vẫn có thể mất tiền. Cần chặn quyết định dựa riêng vào mô tả hiện tại khi thiếu căn cứ lúc mua; tách rõ nguồn/thời điểm và chuyển người kiểm tra. Câu xin lỗi không đảo được tiền đã chuyển.
- **K07:** AI nói “đang chờ shop” nhưng gọi `soan_hoan_tien` hoặc `tu_choi_khieu_nai` trước khi đủ căn cứ thì một bên vẫn chịu thiệt. Cần chặn quyết định khi còn tranh chấp chưa xác minh hoặc shop vẫn còn hạn phản hồi; hết hạn không tự coi im lặng là thừa nhận. Đây là ràng buộc cần cụ thể hóa ở §4 và thể hiện trạng thái bị chặn trên prototype.
- **Đối chiếu bốn đường trải nghiệm:** bình thường — đủ căn cứ, hai bên thống nhất thì đi tới bước xử lý theo mức duyệt ở §4; thiếu chắc chắn — K07 xin đúng phần thiếu và chờ phản hồi; thiếu căn cứ — K04 chuyển người; người dùng sửa AI — cả hai ca đều có nút sửa, lưu đính chính và cập nhật người tiếp nhận. Việc hai bên thống nhất không tự cấp quyền để AI chuyển tiền.

## §4. Mức tự chủ (chặng 4)

### 4.1. Mức cho từng tool

| Tool                 | Mức chọn và điều kiện                                                                                        | Cái giá khi sai, khả năng sửa và cái giá khi chờ                                                                                                                                                | Phương án loại                                                                                                                            |
| -------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `yeu_cau_bang_chung` | **Tự làm** khi đã xác định đơn, điểm tranh chấp và phần bằng chứng còn thiếu; chỉ gửi cho đúng bên           | Xin sai/lặp khiến khách hoặc shop mất công, có thể lỡ hạn (K02, K03, K10). Tin đã gửi không thu hồi được; chỉ gửi đính chính. Chờ nhân viên duyệt mọi yêu cầu làm chậm việc thu thập bằng chứng | Loại duyệt mọi tin vì thêm chờ cho thao tác thường gặp; loại tự gửi mẫu chung khi chưa rõ đơn hoặc đã đủ ảnh                              |
| `chuyen_truong_nhom` | **Tự làm** khi khách yêu cầu, thiếu căn cứ quan trọng, hoặc hết hạn phản hồi mà chưa giải quyết              | Chuyển nhầm làm nhân viên mất công, khách chờ; trưởng nhóm có thể điều phối lại. Bắt duyệt trước khi chuyển khiến K04/K07 tiếp tục mắc kẹt                                                      | Loại cần duyệt vì thêm một cửa chờ trước khi được hỗ trợ; loại cấm vì không có đường xử lý tranh chấp                                     |
| `soan_hoan_tien`     | **Cần nhân viên xử lý tranh chấp được phân quyền duyệt**; tool này thực sự chuyển tiền                       | Hoàn sai khiến shop mất tiền và có thể mất hàng (K07); tiền đã về khách nên khó thu hồi, cần nhân viên xử lý. Chờ duyệt làm khách nhận tiền chậm, vì vậy AI chuẩn bị hồ sơ trước                | Loại tự làm vì khó đảo; loại cấm hoàn toàn vì hồ sơ hợp lệ vẫn cần hoàn tiền                                                              |
| `tu_choi_khieu_nai`  | **Cần nhân viên xử lý tranh chấp được phân quyền duyệt**; chưa cho duyệt khi còn vướng điều kiện chặn ở §4.3 | Đóng sai khiến khách mất tiền, giữ hàng sai (K04/K07); tiền đã về shop nên khó đảo, cần nhân viên xử lý. Chờ duyệt kéo dài thời gian shop nhận tiền                                             | Loại tự làm vì có thể kết luận từ sai nguồn; loại cấm hoàn toàn vì khiếu nại không đủ điều kiện sau xác minh vẫn cần quyết định có căn cứ |
| `phat_shop`          | **Cấm trong luồng này**; chỉ chuyển trưởng nhóm để điều phối bộ phận chuyên trách                            | Phạt sai ảnh hưởng uy tín và hoạt động cả shop (K08), khó khôi phục đầy đủ. Chuyển chuyên trách chậm hơn nhưng tránh xử phạt từ một nghi ngờ chưa xác minh                                      | Loại tự làm và duyệt ngay trong luồng thường vì xác nhận đơn lẻ không thay thế được quy trình xác minh, thẩm quyền xử phạt                |

### 4.2. Duyệt quyết định tiền bạc

- **Người duyệt:** nhân viên xử lý tranh chấp được phân quyền; khách xác nhận mong muốn không thay cho nhân viên duyệt hoàn tiền hoặc từ chối.
- **Trước khi bấm:** thấy đúng đơn, mô tả lúc đặt và nguồn/thời điểm, bằng chứng hai bên, phần chưa xác minh, hạn phản hồi, số tiền, bên nhận tiền và lý do đề xuất. Nếu duyệt từ chối, phải thấy rõ hồ sơ sẽ đóng và tiền về shop.
- **Quá hạn:** dùng mục tiêu phản hồi đầu tiên trong 24 giờ như §3; báo chậm và đánh dấu quá hạn cho trưởng nhóm, không tự chuyển tiền hoặc đóng hồ sơ. AI vẫn hướng dẫn khách gửi yêu cầu đúng hạn; chờ duyệt không tự giữ hoặc gia hạn quyền yêu cầu.
- **Sau duyệt:** chỉ thực hiện đúng đơn, số tiền và phương án đã được duyệt; có bằng chứng mới hoặc người dùng đính chính thì quay lại xem xét trước khi thực hiện. Chỉ báo thành công khi tool xác nhận; kết quả chưa rõ thì kiểm tra trạng thái, không gọi lại mù quáng gây hoàn trùng.

### 4.3. Luật chặn và tách bước

- **K04:** thiếu mô tả lúc đặt thì không dùng riêng mô tả hiện tại để duyệt từ chối. Trưởng nhóm cần xác minh căn cứ khác; không tìm được bản lưu không tự chứng minh bên nào đúng.
- **K07:** còn tranh chấp chưa xác minh hoặc shop vẫn còn hạn phản hồi thì chặn cả hoàn và từ chối. Hết hạn không tự coi im lặng là nhận lỗi; chuyển người đánh giá bằng chứng. Hai bên đã phản hồi và thống nhất thì không cần chờ hết hạn, nhưng bước chuyển tiền vẫn phải duyệt.
- **Xin bằng chứng:** kiểm tra phần đã nhận, không xin lặp; thiếu đơn/điểm sai thì hỏi lại trước. Người dùng sửa thông tin thì cập nhật hồ sơ và đề xuất đang chờ duyệt, không tiếp tục theo dữ liệu cũ.
- **Tách bước đề xuất:** thêm bước **lập đề xuất hoàn tiền/từ chối**, AI tự chuẩn bị bản nháp; hai tool gốc chỉ thực thi sau duyệt. Đây là phần nhóm đề xuất thêm, không phải tool sẵn có của track. Nhờ đó K04/K07 có thể được phân tích ngay mà chưa phát sinh chuyển tiền.

### 4.4. Tool khó xếp nhất: `soan_hoan_tien`

| Phương án                        | Cái giá                                                                                       |
| -------------------------------- | --------------------------------------------------------------------------------------------- |
| Tự làm                           | Khách nhận tiền nhanh; K07 có thể khiến shop giao đúng vẫn mất tiền vì AI suy từ màu ảnh      |
| Cần người duyệt — phương án chọn | Có thời gian chờ; đổi lại nhân viên kiểm tra căn cứ và phản hồi hai bên trước khi tiền chuyển |
| Cấm                              | Tránh AI hoàn sai nhưng chặn cả ca hợp lệ như đặt L, nhận M và shop xác nhận giao nhầm        |

**Cách chốt trong thiết kế:** chọn cần duyệt, tách bản nháp khỏi thực thi để giảm chờ chuẩn bị hồ sơ; không lấy mục tiêu xử lý nhanh làm lý do bỏ xác minh ở K07.

| Thành viên      | Mức tự chọn ban đầu và lý do                                                                                                                                                                                                                  |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trần Quang Hưng | **`tu_choi_khieu_nai` - cần người duyệt:** cả K4 và K7 đều có khả năng gây thiệt hại khi gọi `tu_choi_khieu_nai` tự động, làm người mua mất tiền và người bán mất uy tín.                                                                     |
| Vũ Tuấn Đạt     | Chưa ghi nhận                                                                                                                                                                                                                                 |
| Nguyễn Tiến Đạt | **`yeu_cau_bang_chung` — cần người duyệt:** K10 cho thấy hỏi lặp khiến khách mất công, tin đã gửi không thu hồi được. Đổi lại, duyệt từng tin làm chậm xử lý; chấp nhận nhóm chọn tự làm nếu kiểm tra bằng chứng đã có và chỉ xin phần thiếu. |

### 4.5. Kiểm thử thiết kế trên ba kịch bản

Đây là kiểm thử bằng lập luận trên luồng thiết kế, chưa phải kết quả chạy agent hay prototype.

| Ca                                                    | AI làm gì, người dùng thấy gì                                                                                   | Chặn được sai ở §2?                                                      | Còn tự làm khi phải hỏi/duyệt?                                                     | Có chờ vô ích?                                                                                             |
| ----------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **K04 — thiếu mô tả lúc mua**                         | Tách nguồn, xin bản lưu nếu có và chuyển trưởng nhóm; hiện “Chưa đủ căn cứ”, hạn liên quan và trạng thái chuyển | Có: chặn từ chối dựa riêng vào mô tả hiện tại                            | Không: không tự xác nhận shop sửa mô tả hoặc thực thi quyết định tiền bạc          | Không bắt khách chờ tìm ảnh mới được chuyển; vẫn cần thời gian nhân viên xác minh                          |
| **K07 — tem navy, ảnh gần đen**                       | Nêu giới hạn tem/ảnh, xin đúng phần thiếu, chờ shop trong hạn; khách vẫn có nút chuyển người                    | Có: chặn hoàn theo ảnh hoặc từ chối theo tem khi chưa đủ căn cứ          | Không: bằng chứng mâu thuẫn không được chuyển thành kết luận; hết hạn chuyển người | Chờ phản hồi là cần thiết; nếu hai bên phản hồi và thống nhất sớm thì chuyển duyệt ngay, không đợi hết hạn |
| **Ca thường — đặt L, nhận M, shop xác nhận gửi nhầm** | AI hướng dẫn ngay; nếu đã đủ ảnh thì không xin lại; lập đề xuất hoàn để nhân viên duyệt, hiện “Chờ duyệt”       | Có: kiểm tra đúng đơn, bằng chứng và xác nhận shop trước khi chuyển tiền | Không: AI chuẩn bị, nhân viên duyệt thực thi                                       | Không thêm duyệt cho hướng dẫn/xin ảnh; còn một bước duyệt tiền có chủ đích vì khó đảo                     |

### 4.6. Lời hứa với người dùng

> “AI hướng dẫn, thu thập bằng chứng và chuyển hồ sơ. Quyết định hoàn tiền hoặc từ chối cần nhân viên được phân quyền duyệt; trạng thái xử lý được hiển thị trong hồ sơ.”

Mức cần duyệt của `soan_hoan_tien` khiến lời hứa phải là **“chuẩn bị đề xuất và chờ duyệt”**, không phải “AI hoàn tiền ngay”.

## §5. Prototype (chặng 5)

### 5.1. File, công cụ, phần nào mock

- **File:** [`prototype/index.html`](prototype/index.html), một file duy nhất, mở bằng trình duyệt, không cần cài đặt, đăng nhập hay backend.
- **Công cụ:** HTML/CSS/JavaScript thuần, dựng với coding agent (Claude Code), nhóm chỉnh theo §2–§4.
- **Phần mock:** toàn bộ là mock.
  - Thương hiệu **“XanhShop”** là sàn giả lập, mô phỏng luồng “Trò chuyện với Shopee” của track nhưng không dùng tên hay logo thật.
  - Đơn hàng, shop, giá, thời hạn đều là dữ liệu dựng. Đồng hồ cũng giả lập (13/11 14:00).
  - Câu trợ lý nói là kịch bản cố định, lấy **nguyên văn §3**. Các ca lạ trả lời theo luật từ khoá, mỗi luật bám một kịch bản ở §2.
  - Tool không chạy thật: mỗi lần gọi, không gọi hay bị chặn chỉ được ghi vào **nhật ký tool**.
- **Lời gọi AI thật:** không có (không nhận bonus +3).
- **Cách bấm qua ca khó (K07, ca demo bắt buộc “người bán đúng”):**
  1. Màn **Người mua**: AI nêu giới hạn, chưa quyết định.
  2. Màn **Nhân viên duyệt**: nút Duyệt bị khoá, có lý do.
  3. Màn **Người bán**: bấm “Gửi ảnh gốc / bằng chứng”. Hai bên chưa thống nhất nên AI tự chuyển trưởng nhóm.
  4. Màn **Nhân viên duyệt**: tick “đã xác minh màu thực tế”, nút mở khoá, bấm duyệt, rồi qua hộp xác nhận.
- **Ca khác và nhánh lỗi:**
  - Ô chọn ca có **K04** và **ca thường K01** (§4.5).
  - Thanh demo có các nút: _Mô phỏng lỗi tool_, _Mô phỏng AI kết luận sớm_, _Khách không thao tác_, _Hết hạn phản hồi của shop_, _+24 giờ_.
  - 7 chip **“Thử ca lạ”** (K02, K03, K05, K06, K08, K09, K10) và ô nhập tin tự do để trả lời ca lạ khi demo.
- Mở với `?sc=K07&role=buyer&annot=1` (hoặc `role=staff`, `role=seller`) để hiện sẵn các số chú thích như trong ảnh.

### 5.2. Ảnh có đánh số

| Ảnh                                                                  | Màn hình                          |
| -------------------------------------------------------------------- | --------------------------------- |
| [`prototype/1-nguoi-mua.png`](prototype/1-nguoi-mua.png)             | K07 · Người mua: số ①–⑦           |
| [`prototype/2-nhan-vien-duyet.png`](prototype/2-nhan-vien-duyet.png) | K07 · Nhân viên duyệt: số ⑦ ⑨ ⑩ ⑪ |
| [`prototype/3-nguoi-ban.png`](prototype/3-nguoi-ban.png)             | _(ảnh phụ)_ K07 · Người bán: số ⑧ |

![Người mua](prototype/1-nguoi-mua.png)
![Nhân viên duyệt](prototype/2-nhan-vien-duyet.png)

| Số  | Thể hiện gì                                                                                                                                                                                                                         | Nguyên tắc HAX/PAIR                                                         | Mức tự chủ                                                                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| ①   | Nhãn “Trợ lý AI · có thể sai · quyết định tiền do nhân viên” ở đầu khung chat                                                                                                                                                       | **G1** (Luật AI 134/2025 Điều 11: báo người dùng đang làm việc với AI) · G2 | —                                                                               |
| ②   | Câu AI nói nguyên văn §3: tem khớp nhưng chưa đủ kết luận màu thực tế; “chưa thực hiện hoàn tiền hay đóng khiếu nại”                                                                                                                | **G10** thu hẹp khi nghi ngờ · G2                                           | AI không tự quyết tiền                                                          |
| ③   | Thẻ “Căn cứ trợ lý đang dùng”: mỗi căn cứ một dòng, có nguồn và thời điểm, nhãn _Dữ liệu hệ thống / Khớp mô tả / Chờ xác minh_; ghi chú “Tem khớp; màu hàng thực tế chưa xác minh”. Ở K04 thẻ này hiện “Mô tả lúc đặt: **Chưa có**” | **G11** giải thích vì sao · PAIR _Explainability + Trust_                   | —                                                                               |
| ④   | Trạng thái “Chờ đối chiếu và phản hồi của shop — chưa có quyết định”; hạn của shop và hạn của khách hiện **riêng**                                                                                                                  | G2 · rubric riêng T4 ý 8                                                    | —                                                                               |
| ⑤   | Nút “Sửa thông tin / ảnh gửi nhầm”: ảnh cũ bị gạch, nhãn “Không dùng để quyết định”, hồ sơ cập nhật không bắt làm lại; đã chuyển thì gửi đính chính cho người xử lý                                                                 | **G9** sửa dễ dàng                                                          | Đính chính: tự làm                                                              |
| ⑥   | Nút “Yêu cầu nhân viên kiểm tra”. Chuyển lỗi thì hiện “Chuyển chưa thành công · Thử lại”, không báo đã chuyển                                                                                                                       | G10 · PAIR _Errors + Graceful failure_                                      | `chuyen_truong_nhom`: **tự làm**                                                |
| ⑦   | Nhật ký tool: mỗi lần AI gọi, không gọi hoặc bị chặn, kèm mức tự chủ                                                                                                                                                                | Minh bạch mức tự chủ (G11)                                                  | Mọi tool                                                                        |
| ⑧   | Màn người bán: hạn phản hồi đếm ngược, câu “shop chưa trả lời khi còn hạn **không** bị coi là nhận lỗi”; liên hệ người mua bị ẩn                                                                                                    | Hai bên cùng được nghe (rubric riêng ý 3, 6)                                | `yeu_cau_bang_chung`: **tự làm**                                                |
| ⑨   | Nút “Duyệt hoàn tiền / Duyệt từ chối” **bị khoá kèm lý do** (shop còn hạn; màu thực tế chưa xác minh). Mở khoá rồi vẫn phải qua hộp xác nhận nêu số tiền, bên nhận tiền, “khó đảo lại”                                              | G10 · luật chặn §4.3                                                        | `soan_hoan_tien`, `tu_choi_khieu_nai`: **cần duyệt**                            |
| ⑩   | Không có nút phạt hay khoá shop, chỉ có “Chuyển bộ phận chuyên trách”                                                                                                                                                               | §1 việc không làm                                                           | `phat_shop`: **cấm**                                                            |
| ⑪   | Đề xuất do AI soạn sẵn, ghi rõ “Bản nháp — chưa thực thi”                                                                                                                                                                           | G11 · bước tách §4.3                                                        | `lap_de_xuat_quyet_dinh` (tên nhóm đặt cho bước tách “lập đề xuất”): **tự làm** |

Ba nguyên tắc chính của §3 nằm ở: **G10** → ② ⑥ ⑨ · **G11** → ③ ⑪ · **G9** → ⑤.

### 5.3. Quyết định: cách hiện độ chắc và bằng chứng, cách điều khiển mức tự chủ

**Hiện độ chắc**

- **Chọn:** nhãn chữ trên **từng bằng chứng** (_Dữ liệu hệ thống / Khớp mô tả / Chờ xác minh / Thiếu trong hồ sơ_), cộng một ghi chú tổng nói rõ cái gì khớp, cái gì chưa xác minh (③).
- **Loại phần trăm độ tin cậy** (“chắc 72%”): không có căn cứ để ra con số, dễ tạo cảm giác chính xác giả. Người mua sẽ đọc 72% thành “sắp được hoàn”, đúng điều §3 K07 cấm (“không hiện phần trăm chắc chắn không có căn cứ”).
- **Loại một chấm màu xanh/vàng/đỏ cho cả hồ sơ:** gộp mọi thứ thành một tín hiệu, che mất chỗ mâu thuẫn chính của K07 (tem khớp nhưng màu ảnh lệch). Chỉ dựa vào màu cũng khó đọc với người mù màu.

**Hiện bằng chứng**

- **Chọn:** thẻ đặt các căn cứ **cạnh nhau, có nguồn và thời điểm**. Ở K04, mô tả lúc đặt, mô tả hiện tại và lời người mua là ba dòng riêng.
- **Loại để AI tóm tắt bằng lời trong chat:** người dùng không tự kiểm được (trái G11). Lỗi “dùng mô tả hiện tại thay mô tả lúc đặt” của K04 sẽ bị giấu trong câu chữ.

**Điều khiển mức tự chủ**

- **Chọn: tách theo vai.**
  - Người mua không có nút tiền.
  - Người duyệt có nút tiền nhưng **khoá kèm lý do**, và **luôn có hộp xác nhận**.
  - Việc tự làm hiện trong nhật ký và có đường đính chính.
  - Việc cấm không có nút.
- **Loại nút “Xác nhận hoàn tiền” cho người mua:** khách đồng ý không thay được nhân viên duyệt (§4.2). Ở K06, nút này còn thành nơi để khách gây sức ép.
- **Loại ẩn hẳn nút duyệt khi bị chặn:** người duyệt không biết vì sao bị chặn và khi nào được mở, dễ đi đường vòng. Khoá kèm lý do cho thấy luật §4.3 đang chạy.
- **Loại “tự hoàn rồi cho hoàn tác trong 5 phút”:** track không có tool đảo ngược hoàn tiền hay đóng khiếu nại, tiền đã chuyển khó thu hồi, nên nút hoàn tác sẽ là một lời hứa suông.

**Những gì nhóm thêm, không có trong mẫu của giảng viên**

- Màn **người bán** có hạn phản hồi (⑧).
- **Lý do khoá** hiện ngay trên nút duyệt (⑨).
- **Nhật ký tool** có cả dòng “bị chặn” (⑦).
- Nút **mô phỏng AI kết luận sớm**: câu sai bị gạch, hiện loại lỗi, câu đính chính nguyên văn §3, và nhật ký cho thấy `tu_choi_khieu_nai` vẫn **bị chặn**. Nhờ vậy thấy được thiết kế chặn lỗi kể cả khi model nói sai.

## §6. Tốt là gì (chặng 6)

### 6.1. Ba tiêu chí Pass/Fail

| #   | Tiêu chí                                        | Pass khi                                                                                                                                                                                                                                             | Chấm bằng cách                                                  |
| --- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| TC1 | **Không chuyển tiền khi chưa đủ điều kiện**     | `soan_hoan_tien` / `tu_choi_khieu_nai` chỉ thực thi sau khi người duyệt bấm xác nhận, **và** không còn điều kiện chặn nào ở §4.3 (shop còn hạn, chưa xác minh, thiếu mô tả lúc đặt, có đính chính chưa xem). Một lần thực thi sai điều kiện là Fail. | Xem nhật ký tool ⑦ và trạng thái nút ⑨                          |
| TC2 | **Người bán được nghe trước khi có quyết định** | Người bán nhận yêu cầu phản hồi **kèm hạn cụ thể** trước bất kỳ quyết định tiền nào, **và** im lặng trong hạn không được coi là nhận lỗi. Thiếu một trong hai là Fail.                                                                               | Xem màn người bán ⑧ và nhật ký dòng `yeu_cau_bang_chung → shop` |
| TC3 | **Không kết luận khi căn cứ chưa xác minh**     | Khi còn bằng chứng nhãn “Chờ xác minh” hoặc “Thiếu”, câu AI **không** chứa kết luận bên đúng/sai hay hứa kết quả (“shop giao đúng”, “bạn sẽ được hoàn”), **và** mỗi căn cứ có nguồn và thời điểm (hoặc ghi “Chưa có”, không bịa).                    | Đọc câu AI ② và thẻ bằng chứng ③                                |

### 6.2. Chấm thử thiết kế trên 2 kịch bản đắt nhất

| Tiêu chí | K04 · mô tả bị sửa                                                                                                                                                       | K07 · tem khớp, ảnh gây tranh chấp                                                                                                                                                            |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| TC1      | **Pass.** `tu_choi_khieu_nai` bị chặn ngay từ đầu (“không dùng riêng mô tả hiện tại”). Nút duyệt chỉ mở khi người duyệt xác minh căn cứ khác, rồi vẫn qua hộp xác nhận.  | **Pass.** Cả hai tool tiền bị chặn tới khi shop phản hồi hoặc hết hạn **và** màu thực tế được xác minh. Có hộp xác nhận. Lỗi tool thì “kiểm tra trạng thái, không gọi lại”, tránh hoàn trùng. |
| TC2      | **Pass.** `yeu_cau_bang_chung → shop` gửi ngay, hạn 15/11 14:00, liên hệ hai bên được ẩn.                                                                                | **Pass.** Hạn đếm ngược trên màn người bán. Hết hạn thì AI nói rõ “không được coi là shop nhận lỗi” và chuyển nhân viên.                                                                      |
| TC3      | **Pass ở luồng chính:** ba dòng căn cứ tách riêng, “Mô tả lúc đặt: Chưa có”. **Fail tạm thời ở nhánh “AI kết luận sớm”:** câu sai vẫn hiện ra trước khi được đính chính. | **Pass ở luồng chính.** **Fail tạm thời** ở cùng nhánh: AI nói “Shop giao đúng màu” rồi mới gạch và đính chính.                                                                               |

**Đọc kết quả:** TC1 và TC2 do **thiết kế** giữ (luật chặn, vai người duyệt), nên vẫn Pass khi model nói sai. TC3 phụ thuộc vào **câu chữ của model**: thiết kế chỉ giảm hại (đính chính, gạch câu sai, tool vẫn bị chặn) chứ không ngăn được câu sai xuất hiện.

### 6.3. Lỗi còn lại

1. **TC3 chưa được chặn trước khi câu hiện ra.** Cần thêm bước kiểm câu trước khi gửi: câu có từ kết luận trong khi còn căn cứ “Chờ xác minh” thì không gửi. Bước này chưa có trong thiết kế.
2. **Gốc của K04 chưa được sửa.** Hệ thống vẫn không lưu **bản chụp mô tả lúc đặt hàng**, nên mọi ca giống K04 đều phải chuyển người. Đề xuất cho vòng sau: lưu bản chụp mô tả theo từng đơn, kèm một tool đọc bản chụp đó.
3. **Ô “đã xác minh” của người duyệt là tự khai.** Prototype không kiểm người duyệt đã thực sự xem ảnh gốc hay lịch sử sửa. Cần ghi lại căn cứ xác minh để hậu kiểm.
4. **Mục tiêu phản hồi 24 giờ là con số dựng.** Prototype đánh dấu quá hạn nhưng chưa có đường leo thang tiếp nếu trưởng nhóm cũng không xử lý.
5. **Ca lạ được nhận theo từ khoá.** Tin viết khác các từ khoá đã định sẽ rơi vào câu hỏi lại chung (G10). Ca này an toàn nhưng chưa hữu ích bằng câu trả lời riêng.

## §7. Demo

- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
