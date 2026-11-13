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

**Quy ước thiết kế của nhóm:** các mốc dưới đây là dữ liệu dựng để kiểm thử, không phải cam kết hay chính sách thật của Shopee. Khi chuyển hồ sơ, mục tiêu là nhân viên phản hồi lần đầu trong 24 giờ, không hứa giải quyết xong trong 24 giờ. Mốc phản hồi của shop được hiện bằng ngày giờ cụ thể trong fixture; không lấy mốc này thay cho hạn gửi yêu cầu của người mua. Chuyển người không đồng nghĩa đã gửi yêu cầu trả hàng hoặc được gia hạn. Nếu chưa có dữ liệu hạn, giao diện ghi “Chưa xác định hạn — cần nhân viên kiểm tra”, không tự đoán.

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

| Nguyên tắc | Chỗ cụ thể ở K04 | Chỗ cụ thể ở K07 |
| --- | --- | --- |
| **G10 — Thu hẹp phạm vi khi nghi ngờ** | Câu “Mô tả hiện tại không chứng minh nội dung lúc mua”; dừng kết luận và chuyển người khi thiếu bản lúc đặt | Nhãn “Tem khớp; màu hàng thực tế chưa xác minh”; chưa hoàn hay từ chối khi bằng chứng còn mâu thuẫn |
| **G11 — Giải thích vì sao** | Thẻ tách lời người mua, mô tả hiện tại và bản lúc đặt còn thiếu, kèm nguồn/thời điểm nếu có | Hiện màu đặt, tem và ảnh cạnh nhau; giải thích giới hạn của ảnh và lý do chờ phản hồi shop |
| **G9 — Sửa dễ dàng** | Nút “Sửa thông tin”, cho bổ sung bản lưu; đính chính kết luận cũ và gửi cho người xử lý | Nút “Sửa thông tin / ảnh gửi nhầm”; đánh dấu ảnh cũ không dùng và cập nhật hồ sơ thay vì bắt khách làm lại |

### Lỗi câu chữ không cứu được và cơ chế thiết kế

- **K04:** AI nói “chưa chắc” nhưng vẫn gọi `tu_choi_khieu_nai` thì người mua vẫn có thể mất tiền. Cần chặn quyết định dựa riêng vào mô tả hiện tại khi thiếu căn cứ lúc mua; tách rõ nguồn/thời điểm và chuyển người kiểm tra. Câu xin lỗi không đảo được tiền đã chuyển.
- **K07:** AI nói “đang chờ shop” nhưng gọi `soan_hoan_tien` hoặc `tu_choi_khieu_nai` trước khi đủ căn cứ thì một bên vẫn chịu thiệt. Cần chặn quyết định khi còn tranh chấp chưa xác minh hoặc shop vẫn còn hạn phản hồi; hết hạn không tự coi im lặng là thừa nhận. Đây là ràng buộc cần cụ thể hóa ở §4 và thể hiện trạng thái bị chặn trên prototype.
- **Đối chiếu bốn đường trải nghiệm:** bình thường — đủ căn cứ, hai bên thống nhất thì đi tới bước xử lý theo mức duyệt ở §4; thiếu chắc chắn — K07 xin đúng phần thiếu và chờ phản hồi; thiếu căn cứ — K04 chuyển người; người dùng sửa AI — cả hai ca đều có nút sửa, lưu đính chính và cập nhật người tiếp nhận. Việc hai bên thống nhất không tự cấp quyền để AI chuyển tiền.

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
