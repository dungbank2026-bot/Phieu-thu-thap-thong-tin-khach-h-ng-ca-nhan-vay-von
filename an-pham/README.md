# Ấn phẩm in mã QR – Phiếu thông tin vay vốn

Thư mục này chứa các ấn phẩm in (standee, backdrop, biển để bàn) có mã QR lớn để khách hàng quét và mở **Phiếu thông tin vay vốn** trên điện thoại.

## Các tệp

| Tệp | Nội dung |
|---|---|
| `index.html` | Trang tạo ấn phẩm: chọn khổ, nhập số Zalo cán bộ, xem trước, **In / Lưu PDF**, **Tải SVG mã QR** |
| `pdf/standee-60x160.pdf` | Standee cuốn 60 × 160 cm, bản chung (không gắn số cán bộ) |
| `pdf/standee-80x200.pdf` | Standee cuốn 80 × 200 cm, bản chung |
| `pdf/backdrop-300x200.pdf` | Backdrop sự kiện 300 × 200 cm, bản chung |
| `pdf/bien-qr-A5.pdf` | Biển QR để bàn tại quầy, A5 đứng (14,8 × 21 cm), bản chung |
| `xem-truoc/*.png` | Ảnh xem nhanh của 4 tệp PDF trên (không dùng để in) |
| `vendor/qrcode.js` | Thư viện tạo mã QR `qrcode-generator` 1.4.4 (giấy phép MIT, Kazuhiko Arase) |
| `fonts/*.woff2` | Phông Montserrat và Open Sans (bản biến thiên, bộ ký tự tiếng Việt + Latin) |
| `fonts/OFL-Montserrat.txt`, `fonts/OFL-OpenSans.txt` | Giấy phép SIL Open Font License 1.1 của hai phông |

Mọi thứ đã nằm sẵn trong thư mục, trang không cần tải gì từ Internet nên mở trực tiếp từ máy vẫn chạy.

Cả 4 tệp PDF đều có **lề xén (bleed) 3 mm** mỗi cạnh. Khổ trang PDF bằng thành phẩm cộng 6 mm, ví dụ standee 60 × 160 cm có trang PDF 60,6 × 160,6 cm.

## Mã QR dẫn tới đâu

Mã QR mở link phiếu vay, kèm thêm tham số cho biết khách đến từ kênh nào:

- Standee: `…/?nguon=standee`
- Backdrop: `…/?nguon=backdrop`
- Biển để bàn: `…/?nguon=ban-qr`

Phiếu (từ phiên bản v14) đọc tham số này và ghi thêm dòng **Kênh tiếp cận** vào tin nhắn hồ sơ, ví dụ *Kênh tiếp cận: Quét QR standee tại PGD*.

Khi nhập số Zalo cán bộ, link có thêm đuôi `#09xxxxxxxx`. Hồ sơ khách gửi khi đó đi về cả lãnh đạo PGD (0904 532 088) và cán bộ đó.

## Làm standee riêng cho từng cán bộ

1. Mở `an-pham/index.html`, hoặc `https://dungbank2026-bot.github.io/Phieu-thu-thap-thong-tin-khach-h-ng-ca-nhan-vay-von/an-pham/` khi đã bật GitHub Pages.
2. Chọn **Khổ ấn phẩm**, rồi nhập **Tên cán bộ** và **Số Zalo cán bộ** (10 số, bắt đầu bằng 0). Chân ấn phẩm hiện thêm dòng *Cán bộ tư vấn: … – số Zalo*.
3. Kiểm tra ô **Mã QR mở link**: phải có `#số Zalo` ở cuối.
4. Bấm **In / Lưu PDF**. Trong hộp thoại in của Chrome hoặc Edge:
   - **Máy in:** Lưu dưới dạng PDF
   - **Lề:** Không
   - **Tỷ lệ:** 100 %
   - Bật **Đồ họa nền** (Background graphics)

   Khổ giấy tự đặt theo ấn phẩm.
5. Đặt tên tệp theo cán bộ, ví dụ `standee-60x160-NguyenThiLan.pdf`.

Có thể lưu sẵn thiết lập bằng nút **Sao chép link thiết lập này**. Link có dạng:

```
an-pham/?kho=standee60&ten=Nguyễn Thị Lan&sdt=0912345678
```

Các tham số nhận được:

| Tham số | Ý nghĩa |
|---|---|
| `kho` | Khổ ấn phẩm: `standee60`, `standee80`, `backdrop`, `a5` |
| `sdt` | Số Zalo cán bộ |
| `ten` | Tên cán bộ |
| `pgd` | Tên phòng giao dịch |
| `diachi` | Địa chỉ |
| `hotline` | Số hotline |
| `link` | Link phiếu vay khác (nếu đổi) |
| `bleed=0` | Bỏ lề xén |
| `khung=0` | Ẩn đường xén và vùng an toàn trên bản xem trước |

Mặc định PGD là *Phòng giao dịch Yên Hòa* và hotline là 0904 532 088; cả hai sửa được. Địa chỉ để trống, anh/chị tự điền. Trang không tự ghi một địa chỉ nào.

Nếu địa chỉ hoặc tên dài, trang tự thu nhỏ mã QR nhưng không nhỏ hơn mức tối thiểu: standee 25 cm, backdrop 50 cm, biển A5 9 cm. Khi đã chạm mức tối thiểu, trang báo đỏ để anh/chị rút gọn nội dung.

## Gửi nhà in

- **Gửi tệp PDF** (không gửi ảnh PNG xem trước). PDF là dạng vector: mã QR, chữ và mảng màu nét ở mọi kích thước, không có ảnh bitmap nào. Chữ được nhúng dưới dạng đường nét (Type 3), nhà in không cần cài phông.
- Báo nhà in: **thành phẩm** (ví dụ 60 × 160 cm) và **đã có bleed 3 mm mỗi cạnh**. Nhà in xén đúng thành phẩm.
- **Độ phân giải:** tệp vector không phụ thuộc độ phân giải. Nếu nhà in đòi chuyển sang ảnh, dùng tối thiểu:
  - 300 dpi cho biển A5;
  - 100–150 dpi theo kích thước thật cho standee và backdrop (nhìn từ xa trên 1 m).
- **Màu:** tệp dùng hệ màu RGB. Đề nghị nhà in chuyển sang CMYK theo quy trình của họ và **in thử một bản**, đặc biệt màu đỏ đô và vàng lúa.
- **Quét thử mã QR trên bản in thử** bằng Zalo và camera điện thoại trước khi in số lượng.
- **Standee cuốn:** khoảng 5–8 cm dưới đáy có thể bị khuất trong hộp chân. Bố cục đã chừa khoảng này, nhưng nên hỏi lại nhà in loại chân standee.
- **Biển A5:** bản in nên cán màng mờ (không bóng) để mã QR không bị lóa đèn khi quét.

## Logo

Thư mục chưa có logo Agribank gốc, và trang **không tự vẽ hay mô phỏng logo**. Ở góc trên mỗi ấn phẩm có một ô viền đứt, ghi *Dán logo Agribank gốc (logo.png)*. Cách gắn logo:

1. Lấy file logo chính thức từ chi nhánh hoặc bộ phận truyền thông. Nên dùng bản nền trong suốt, độ phân giải cao, hoặc bản vector SVG.
2. Đặt file vào thư mục `an-pham/`, tên `logo.png` (hoặc `logo.svg`).
3. Mở lại `index.html`: logo tự hiện trong ô, đúng tỷ lệ, trên nền trắng.
4. Xuất lại PDF. Các tệp PDF trong `pdf/` hiện **chưa có logo**, cần xuất lại sau khi có logo.

Không kéo méo, không đổi màu logo.

## Bật GitHub Pages (bắt buộc để mã QR mở được phiếu)

Mã QR trỏ tới `https://dungbank2026-bot.github.io/Phieu-thu-thap-thong-tin-khach-h-ng-ca-nhan-vay-von/`. Link này chỉ hoạt động khi kho đã bật GitHub Pages:

1. Mở kho trên GitHub, vào **Settings → Pages**.
2. Mục **Build and deployment**:
   - **Source:** Deploy from a branch
   - **Branch:** `main`, thư mục `/ (root)`
3. Bấm **Save**, đợi vài phút.
4. Mở link trên điện thoại để kiểm tra trước khi in.

## Khi đổi link phiếu

Mã QR in ra là cố định. Nếu đổi tên kho, đổi tài khoản GitHub hoặc chuyển phiếu sang địa chỉ khác thì **mọi ấn phẩm đã in sẽ mở sai trang**. Khi đó:

1. Nhập link mới vào ô **Link phiếu vay**.
2. Xuất lại PDF.
3. **In lại** toàn bộ standee, backdrop, biển để bàn.

Vì vậy nên giữ nguyên link phiếu sau khi đã in ấn phẩm.

## Nội dung trên ấn phẩm

Ấn phẩm chỉ giới thiệu cách gửi thông tin vay vốn: 3 bước, các nhu cầu vay mà phiếu hỗ trợ, hotline, tên và địa chỉ PGD. Ấn phẩm **không** ghi lãi suất, khuyến mại, cam kết hay số liệu. Muốn thêm các nội dung đó, cần lấy từ văn bản chính thức còn hiệu lực và được duyệt theo quy định trước khi in.

Màu theo bảng màu tạm của bộ nhận diện (đỏ đô `#8C1D28`, vàng lúa `#E8B32C`), chưa đối chiếu cẩm nang chính thức của Agribank. Khi có cẩm nang, sửa các biến màu trong khối `.sheet { … }` của `index.html`.
