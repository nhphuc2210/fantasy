Dưới đây là những gì Ari Juels (và Chainlink / Chainlink 2.0) đã nói / đề xuất liên quan đến việc staking để bảo vệ mạng DONs (Decentralized Oracle Networks, mạng oracle phân quyền của Chainlink)


Bối cảnh: DONs & động lực staking trong Chainlink 2.0
 • Trong whitepaper Chainlink 2.0, các DON được định nghĩa là các mạng oracle phân quyền, mỗi DON là một ủy ban (committee) của các node Chainlink, chịu trách nhiệm thực thi các chức năng oracle và (một phần) thực hiện tính toán off-chain, sau đó đồng thuận và gửi kết quả lên blockchain.  
 • Khi mạng oracle phân quyền chịu trách nhiệm nhiều hơn (không chỉ truyền dữ liệu mà còn thực thi tính toán off-chain, hỗ trợ hợp đồng lai, định tuyến, bảo mật, v.v.), thì yêu cầu về bảo mật kinh tế (cryptoeconomic security) tăng lên — tức là, cần cơ chế để đảm bảo node “chơi đẹp” (honest) và chống lại các kẻ tấn công hoặc lạm dụng.  
 • Một trong những công cụ chính được đề xuất để tăng cường bảo mật kinh tế cho DONs đó là staking — các node (hoặc người tham gia có liên quan) đặt cọc (deposit) token để chịu trách nhiệm, chịu phạt nếu hành vi sai, và hưởng phần thưởng nếu thực hiện đúng.

 “Super-linear staking” (staking siêu tuyến tính, hoặc staking siêu tỷ lệ/mở rộng)

Ý tưởng là trong mô hình super-linear, một kẻ tấn công muốn kiểm soát hoặc làm sai lệch hệ thống phải bỏ ra chi phí vốn rất lớn, lớn hơn rất nhiều so với số token mà các node đặt cọc gộp lại. Điều này làm tăng rào cản tấn công và làm cho mạng an toàn hơn.

Khuyến khích hành vi trung thực / chống hối lộ / chống thỏa thuận xấu: Bằng cách staking, các node bị ràng buộc: Nếu một node làm sai (cung cấp dữ liệu sai, âm mưu tấn công), nó có thể bị phạt (slashing hoặc mất phần đặt cọc). Điều này làm giảm động cơ để nhận hối lộ hoặc tham gia vào hành vi sai.

Tỷ lệ chi phí tấn công tăng theo số lượng node và tổng đặt cọc
 • Mô hình staking (đặc biệt là super-linear) mang lại chi phí vốn tấn công tăng nhanh khi mạng mở rộng. Khi có nhiều node tham gia đặt cọc, chi phí để tấn công tất cả hoặc kiểm soát mạng trở nên cực kỳ cao — nghĩa là nếu chỉ một node vẫn giữ trung thực, toàn bộ âm mưu tấn công có thể bị phá vỡ, vì các node gian lận sẽ bị trừng phạt.

Mối liên hệ giữa staking, sự phát triển & bảo mật kinh tế ngày càng cao, flywheel : mạng an toàn hơn → người dùng tin tưởng hơn → có nhiều giá trị được giao dịch / sử dụng → cần bảo mật cao hơn → nhiều người sẽ đặt cọc / tham gia để bảo vệ mạng.


⸻



 “super-linear staking” của Ari Juels làm cho chi phí để làm sai lệch một DON tăng nhanh hơn tuyến tính theo số node. 


