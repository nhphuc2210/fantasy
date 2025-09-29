# Chainlink FAQ

## Vì sao cơ chế “prioritized watchdog reports” lại tạo ra hiệu ứng super-linear, và điều này làm tăng chi phí tấn công DON như thế nào?

## Tại sao chi phí hối lộ tối thiểu tăng theo hàm bậc hai của số node (\(\frac{d n^2}{2}\))?

## Vì sao Staker được nhận reward?

Trong mô hình Chainlink thì thường có 2 vai trò tách biệt:

### 1. Node operator (người vận hành node)

- Chạy hạ tầng, ký dữ liệu, báo cáo on-chain, duy trì uptime.
- Đặt cọc (stake) của chính mình → thể hiện “skin in the game”.
- Nếu sai phạm (báo cáo sai, gian lận, downtime…) thì stake của họ có thể bị slashing (cắt mất).

### 2. Staker bên ngoài (delegator / community staker)

- Đây là những người không trực tiếp vận hành node, nhưng đặt cọc token LINK vào pool staking.
- Đóng góp của họ là gia tăng “bảo mật kinh tế” (cryptoeconomic security) cho mạng lưới.
- Khi có thêm nhiều token bị khóa trong staking pool, chi phí để kẻ tấn công mua quyền kiểm soát / hối lộ node sẽ cao hơn nhiều.
- Staker không chạy node, nhưng họ ủy thác vốn để củng cố sức mạnh bảo mật cho mạng.
- Đổi lại, họ nhận phần thưởng staking (reward), thường đến từ phí dịch vụ mà người dùng Chainlink trả cho DONs.

### Cách mà staker “đóng góp”

1. Tăng chi phí tấn công:
   - Nếu chỉ có token của node operator đặt cọc, tổng lượng vốn “at risk” khá nhỏ → attacker dễ dàng gom vốn lớn hơn.
   - Khi có cộng đồng cùng stake thêm, tổng lượng vốn “at risk” tăng rất nhiều → attacker phải bỏ ra vốn gấp bội (theo mô hình super-linear staking mà Ari Juels đề xuất).

2. Củng cố uy tín mạng:
   - Người dùng dApp / DeFi sẽ tin tưởng hơn khi thấy DON được “hậu thuẫn” bởi lượng stake lớn → rủi ro bị tấn công thấp hơn.

3. Phân quyền trách nhiệm:
   - Thay vì phụ thuộc chỉ vào vốn của vài node operator, cơ chế staking cho phép cả cộng đồng cùng tham gia, tránh tình trạng tập trung vốn.

### Tóm lại

- Staker hỗ trợ bảo mật cho mạng – tăng chi phí tấn công: Khi có nhiều LINK bị khóa trong staking pool, kẻ tấn công cần có lượng vốn lớn hơn nhiều lần để hối lộ hoặc chiếm quyền kiểm soát mạng. Điều này làm tăng tính an toàn cho toàn bộ hệ thống.
- Mối liên hệ giữa staking, sự phát triển và bảo mật kinh tế ngày càng cao (flywheel): mạng an toàn hơn → người dùng tin tưởng hơn → có nhiều giá trị được giao dịch/sử dụng → cần bảo mật cao hơn → nhiều người sẽ đặt cọc/tham gia để bảo vệ mạng.

## “Super-linear staking” (staking siêu tuyến tính, hoặc staking siêu tỷ lệ/mở rộng)

Ý tưởng: trong mô hình super-linear, một kẻ tấn công muốn kiểm soát hoặc làm sai lệch hệ thống phải bỏ ra chi phí vốn rất lớn, lớn hơn đáng kể so với số token mà các node staking gộp lại. Điều này nâng rào cản tấn công và làm cho mạng an toàn hơn.

Khuyến khích hành vi trung thực / chống hối lộ / chống thỏa thuận xấu: Bằng cách staking, các node bị ràng buộc. Nếu một node làm sai (cung cấp dữ liệu sai, âm mưu tấn công), nó có thể bị phạt (slashing hoặc mất phần staking). Điều này làm giảm động cơ nhận hối lộ hoặc tham gia vào hành vi sai.

Tỷ lệ chi phí tấn công tăng theo số lượng node và tổng lượng LINK staking:

- Khi số node tham gia staking tăng, chi phí để tấn công hoặc kiểm soát mạng trở nên cực kỳ cao — chỉ cần một node còn trung thực là âm mưu bị phá vỡ vì các node gian lận sẽ bị trừng phạt.

## Tại sao “super-linear staking” của Ari Juels làm cho chi phí để làm sai lệch một DON tăng nhanh hơn tuyến tính theo số node?

Cụ thể, nếu mỗi node đặt cọc d và có n node, thì kẻ tấn công phải chuẩn bị ngân sách lớn hơn \( \frac{d n^2}{2} \) — tức là bậc hai theo n, chứ không chỉ xấp xỉ tổng cọc \( d n \).

### Cơ chế hoạt động (tóm tắt)

- Hai tầng: Tầng 1 (rẻ, hiệu quả) tạo báo cáo oracle liên tục; nếu có tranh chấp, Tầng 2 (an toàn tối đa) xét xử để quyết định đúng sai.
- Watchdog priority & bounty tập trung: Mỗi vòng báo cáo, mọi node có thể làm “watchdog”. Nếu báo cáo sai, watchdog có ưu tiên cao nhất được thưởng hơn \( \frac{d n}{2} \) lấy từ phần stake bị slashing của đa số node làm sai. Toàn bộ thưởng dồn cho 1 watchdog, nên chỉ cần một node trung thực báo động là đủ “đánh sập” âm mưu.

### Tại sao chi phí tấn công tăng thành bậc hai?

1. Để báo cáo sai lọt qua Tầng 1, kẻ tấn công phải khiến đa số node hành xử sai → lượng stake bị slashing cỡ > \( \frac{d n}{2} \).
2. Vì một watchdog có thể “ăn trọn” phần thưởng > \( \frac{d n}{2} \), mỗi node đều có động lực không nhận hối lộ mà tố cáo để nhận thưởng.
3. Muốn bịt miệng tất cả watchdog, kẻ tấn công phải hối lộ từng node một khoản lớn hơn \( \frac{d n}{2} \). Có n node → tổng hối lộ > \( \frac{d n^2}{2} \) (siêu tuyến tính/quadratic).

Ví dụ nhanh:

\[ n = 25,\; d = 10{,}000\;\text{LINK} \Rightarrow d n = 250{,}000\;\text{LINK},\; \frac{d n^2}{2} = \frac{10{,}000 \times 25^2}{2} = 3{,}125{,}000\;\text{LINK} \]

Lớn gấp 12,5 lần tổng cọc (minh họa từ whitepaper/blog).

## Tại sao lại là mũ 2 mà không thiết kế là mũ 10 hay mũ 20?

- Trong thiết kế:
  - Chi phí tấn công của mỗi node tăng tuyến tính theo số node (\( \sim d n \)).
  - Và bạn cần “bao phủ” tất cả node (số lượng n) → nhân thêm một lần nữa.
  - Tuyến tính × tuyến tính = bậc hai.

Nói cách khác, quadratic xuất hiện tự nhiên từ:

- (a) chi phí hối lộ mỗi node tỉ lệ với số node, và
- (b) phải hối lộ n node.

### Sao không chọn công thức kiểu \( n^{20} \)?

Để có mũ 20, bạn phải thiết kế thưởng/phạt phi thực tế: ví dụ, chỉ cần 1 node tố cáo thì nó lấy toàn bộ stake của cả mạng, rồi nhân lên theo nhiều vòng. Khi đó:

- Node nhỏ stake ít nhưng lại có quyền ăn cả núi phần thưởng.
- Node sẽ không thật sự có gì để mất hay để được ngoài số stake nhỏ của mình.
- Dù công thức bảo mật có “to” đến đâu, nó không phản ánh hành vi kinh tế thực tế.

### 1) Động lực phải khả thi để trả

- Nếu một node chỉ stake 1 LINK mà khi tố cáo lại được “thưởng” \( n^{20} \) LINK, thì số thưởng đó lấy ở đâu ra?
- Trong mô hình super-linear (mũ 2), bounty lấy từ stake bị cắt của đa số node gian lận → có nguồn thực tế.
- Với mũ 20, số tiền thưởng vượt xa tổng stake của cả mạng → không có nguồn vốn nào để chi trả.

### 2) Động lực phải cân bằng với rủi ro

- Một node honest phải cân nhắc: “Nếu mình tố cáo, mình có thể nhận thưởng; nếu sai hoặc bị kiện ngược, mình mất stake”.
- Khi thưởng quá khổng lồ, cán cân này mất cân bằng: node honest có thể dàn dựng gian lận giả để tự tố cáo và hốt bounty.
- Hệ thống sẽ biến thành “ai cũng muốn farm bounty” thay vì vận hành oracle đúng nghĩa.