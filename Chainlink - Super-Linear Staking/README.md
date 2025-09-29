
# Chainlink 2.0 Super-Linear Staking: Tổng quan

## Giới thiệu

Whitepaper Chainlink 2.0 vừa được công bố đã giới thiệu hàng loạt đổi mới nhằm cải thiện đáng kể năng lực của Decentralized Oracle Networks (DONs), trong đó nổi bật nhất là việc cho phép DONs thực hiện các phép tính bảo mật ngoài chuỗi (off-chain computations). Với khả năng cung cấp cho smart contract quyền truy cập vào nhiều dịch vụ phi tập trung hơn ngoài việc chỉ truyền dữ liệu, DONs mở ra một hạ tầng lai rộng lớn hơn, cho phép các nhà phát triển kết hợp mã on-chain với tài nguyên off-chain để xây dựng những smart contract ngày càng tiên tiến.  

Một khía cạnh quan trọng trong việc triển khai thế hệ hybrid smart contracts tiếp theo là xây dựng mô hình bảo mật cryptoeconomic vững chắc cho DONs, nhằm tối đa hóa chi phí tấn công. Đây là yếu tố then chốt để mở rộng bảo mật cho DONs khi chúng ngày càng tham gia nhiều hơn vào việc bảo vệ các chức năng trọng yếu trong smart contracts giá trị cao, liên quan trực tiếp đến tài sản người dùng.  

Để đạt mức độ chống giả mạo cao hơn, whitepaper giới thiệu **Explicit Staking**—một hệ thống cryptoeconomic tiên tiến đang được phát triển, trong đó các node Chainlink khóa LINK làm tài sản thế chấp và có thể bị slashed nếu có hành vi độc hại hay không mong muốn.  

Mô hình staking của Chainlink mang tính độc đáo vì được thiết kế để bảo vệ chống lại một tập hợp rộng lớn các đối thủ có tiềm lực tài chính mạnh, đồng thời đạt được hiệu ứng **super-linear staking**—một cơ chế trong đó kẻ tấn công phải có ngân sách lớn hơn đáng kể so với tổng số stake của toàn bộ node trong một DON, từ đó tạo ra mức bảo mật ngày càng lớn cho các ứng dụng smart contract giá trị cao, trong khi vẫn tiết kiệm chi phí.  

---

## Vai trò của Explicit Staking trong Decentralized Oracle Networks  

Cơ chế explicit staking của Chainlink theo đuổi một mục tiêu hoàn toàn khác với staking trong các blockchain. Nếu như các blockchain Proof-of-Stake dùng staking để đạt đồng thuận toàn cầu về các giao dịch được sắp xếp thành block, thì explicit staking trong Chainlink 2.0 nhằm tạo ra các báo cáo oracle đáng tin cậy, chống giả mạo, phản ánh chính xác các sự kiện thực ngoài chuỗi.  

Mục tiêu cuối cùng là tăng cường bảo mật cryptoeconomic cho DONs, giúp người dùng có được sự đảm bảo lớn hơn về tính xác thực và kịp thời của dữ liệu bên ngoài và các tính toán off-chain mà hybrid smart contracts giá trị cao phụ thuộc vào. Các cơ chế staking oracle trước đây chỉ bảo vệ được một số ít kiểu tấn công, chưa tính tới khả năng của kẻ tấn công thực tế. Ngược lại, cơ chế explicit staking của Chainlink được thiết kế để chống lại một loạt chiến lược tấn công tinh vi, bao gồm cả **prospective bribery**, khi node bị nhắm mục tiêu theo vai trò của nó trong mạng (ví dụ node được chọn để phân xử báo cáo).  

---

## Nền tảng của Explicit Staking trong Chainlink  

Whitepaper Chainlink 2.0 mô tả cách explicit staking sẽ bảo vệ các DON chịu trách nhiệm cung cấp dữ liệu thị trường tài chính on-chain—một nguồn dữ liệu ngoài chuỗi thiết yếu cho nhiều ứng dụng DeFi. Cơ chế explicit staking được đề xuất bao gồm nhiều thành phần độc lập, kết hợp để tạo ra mức bảo mật kinh tế đáng kể.  

### Service Agreements  

Mỗi DON có một **service agreement** xác định số lượng LINK mà mỗi node phải stake và các yêu cầu hiệu suất chính, chẳng hạn như mức sai lệch tối đa giữa phản hồi của node và giá trị tổng hợp, hoặc mức sai lệch giữa giá trị tổng hợp và giá trị thực mà nó cần phản ánh. Service agreement cũng có thể định nghĩa nguồn dữ liệu sử dụng, tần suất cập nhật, mức thanh toán cho từng node, cùng nhiều tham số khác.  

Các kết quả từ DON được tổ chức thành các **reporting rounds**, trong đó mỗi vòng tạo ra một báo cáo oracle mới chứa phản hồi riêng của từng node cho cùng một dữ liệu (ví dụ giá ETH/USD), sau đó tất cả phản hồi được tổng hợp thành một giá trị duy nhất (ví dụ median). Service agreement định nghĩa cách tạo báo cáo và các điều kiện để stake của node có thể bị slashed.  

Việc lựa chọn node tham gia DON có thể bao gồm các nhà vận hành node uy tín đã bảo vệ hàng chục tỷ đô la trong hệ DeFi. Các node này có thể được lọc và lựa chọn thông qua các framework danh tiếng như **Chainlink Market**, nơi cung cấp marketplace phi tập trung hiển thị hiệu suất lịch sử của node như uptime, độ trễ, sai lệch phản hồi, mạng hỗ trợ, nguồn dữ liệu, v.v.  

### Mạng Oracle Hai Tầng  

Để đảm bảo service agreement được thực hiện đúng, Chainlink áp dụng thiết kế mạng oracle hai tầng:  

- **Tầng thứ nhất**: DON hiệu suất cao và chi phí thấp, gồm các node stake LINK và liên tục tạo báo cáo oracle tổng hợp.  
- **Tầng thứ hai**: DON bảo mật tối đa và chi phí cao hơn, dùng để phân xử mọi tranh chấp về tính hợp lệ của báo cáo do tầng đầu tạo ra.  

Thiết kế này giúp tối ưu hiệu quả trong điều kiện bình thường, đồng thời ưu tiên khả năng chống giả mạo và độ chính xác khi xảy ra phân xử, bảo đảm các node tầng đầu phải chịu trách nhiệm nếu có hành vi xấu hoặc hiệu suất kém.  

Mạng Chainlink hiện tại đã hoạt động hơn hai năm, tạo ra hàng triệu giao dịch on-chain và bảo vệ hàng chục tỷ đô la trong DeFi. Đến nay chưa từng cần một lớp phân xử riêng, bởi các khích lệ cryptoeconomic đã đảm bảo các node uy tín luôn xuất bản báo cáo chính xác. Tuy nhiên, để thận trọng, Chainlink 2.0 tích hợp sẵn tầng phân xử thứ hai, đem lại lớp bảo mật cao hơn.  

---

## Bảo mật cryptoeconomic của tầng hai qua User Voting  

Trong trường hợp hiếm hoi phát sinh tranh chấp về báo cáo từ tầng một (được kích hoạt bởi cơ chế watchdog/alerter), tranh chấp sẽ được giải quyết bởi một ủy ban tầng hai chậm hơn, gồm hàng trăm rồi hàng nghìn người dùng độc lập của Chainlink như Aave, Synthetix, Compound, v.v.  

Những người dùng này sẽ bỏ phiếu về tính chính xác của báo cáo dựa trên bằng chứng TLS mật mã do **DECO** tạo ra, cung cấp **zero-knowledge proof** từ một hoặc nhiều nhà cung cấp dữ liệu. DECO cho phép phân xử hiệu quả, chi phí thấp, chống giả mạo, ngay cả khi người bỏ phiếu không truy cập được dữ liệu gốc.  

Vì bảo mật của ứng dụng smart contract và tài sản người dùng phụ thuộc vào báo cáo oracle chính xác, nên mỗi người bỏ phiếu tầng hai có động lực kinh tế mạnh mẽ để giải quyết đúng tranh chấp, nhằm không gây tổn hại đến bảo mật, danh tiếng hoặc giá trị token ứng dụng của họ. Dù hiếm khi có thiểu số bỏ phiếu sai, đại đa số những người tham gia tầng hai đều có lợi ích lớn để bỏ phiếu đúng. Khi có thêm mỗi người dùng trả phí mới, ngân sách bảo mật của mạng oracle Chainlink không chỉ tăng, mà còn tăng cả số lượng người tham gia bỏ phiếu hợp lý.  

Người tham gia tầng hai có thể là đội phát triển ứng dụng, hoặc các **DAO** dùng token quản trị để bỏ phiếu. Khi DAO bỏ phiếu bằng token quản trị, bảo mật tầng hai tỷ lệ thuận với tổng giá trị token tham gia. Nếu ai đó bỏ phiếu ngược lại bằng chứng DECO, họ sẽ bị áp đảo bởi đa số, và bị ghi lại on-chain như đã bỏ phiếu sai, gây ảnh hưởng tới danh tiếng ứng dụng.  

---

## Cơ chế Watchdog Ưu Tiên (prioritized watchdog reports)

Để tầng hai được kích hoạt đúng lúc khi cần, bất kỳ node tầng một nào cũng có thể đóng vai trò watchdog, phát cảnh báo nếu nghi ngờ báo cáo tổng hợp sai.  

Trong mỗi reporting round, node tầng một được gán một **số ưu tiên công khai** ngẫu nhiên (dùng Chainlink VRF), xác định thứ tự xử lý cảnh báo của node. Ví dụ, trong mạng 100 node, mỗi node sẽ có một số từ 1–100.  

Nếu watchdog phát cảnh báo và tầng hai xác nhận báo cáo tổng hợp tầng một là sai, toàn bộ LINK stake của nhóm node gian lận sẽ bị slashed và trao cho node watchdog có số ưu tiên cao nhất. Cơ chế này tạo động lực kinh tế mạnh mẽ cho node tầng một hành động hợp lý, bởi watchdog có thể kiếm được phần stake rất lớn từ hành vi sai trái.  

---

## Phần thưởng Tập Trung và Hiệu ứng Super-Linear  

Hệ thống watchdog ưu tiên tạo ra **phần thưởng tập trung**, dẫn đến tác động staking super-linear—ngân sách kẻ tấn công cần để giả mạo DON tăng theo cấp số nhân khi số lượng node tăng.  

Để ngăn chặn bất kỳ cảnh báo nào được gửi lên tầng hai, kẻ tấn công phải hối lộ mỗi node tầng một bằng số tiền lớn hơn phần thưởng cảnh báo mà node có thể nhận. Điều này khiến chi phí hối lộ khả thi tăng đáng kể.  

Việc tập trung phần thưởng cảnh báo vào một node thay vì chia đều cho tất cả tạo ra mức bảo mật cryptoeconomic cho toàn DON cao hơn.  

---

## Định Lượng Bảo Mật của Explicit Staking  

Giả sử DON tầng một có **n node**, mỗi node stake **d**, tổng stake toàn mạng là **dn**. Để tạo báo cáo sai, kẻ tấn công cần kiểm soát đa số node, nghĩa là stake gian lận ít nhất bằng **dn/2**. Nếu watchdog cảnh báo và tầng hai xác nhận, watchdog ưu tiên cao nhất sẽ nhận phần thưởng ít nhất **dn/2**. Vì bất kỳ node nào cũng có thể là watchdog, mỗi node cần được hối lộ ít nhất số tiền đó để im lặng. Do đó, ngân sách kẻ tấn công cần có để giả mạo DON tầng một ít nhất là **dn²/2**, tức tăng theo hàm bậc hai của số node.  

---

## Các Kịch Bản Sau Khi Báo Cáo Được Công Bố  

Sau khi DON tầng một xuất bản báo cáo:  

1. **Đồng thuận hoàn toàn**: Tất cả node hoạt động đúng, báo cáo hợp lệ, mỗi node nhận phí cố định.  
2. **Đồng thuận một phần**: Một số node offline hoặc sai, nhưng đa số vẫn đúng, báo cáo hợp lệ không cần cảnh báo. Node đúng nhận phí, node sai bị slashed nhẹ.  
3. **Cảnh báo**: Một hoặc nhiều node cho rằng báo cáo sai và phát cảnh báo. Tầng hai sẽ phân xử:  
   - **Cảnh báo đúng**: Báo cáo sai, toàn bộ stake node gian lận bị slashed, trao cho watchdog ưu tiên cao nhất.  
   - **Cảnh báo sai**: Báo cáo đúng, node phát cảnh báo bị slashed nhẹ.  

---

## Bảo Hiểm Sai Báo Cáo (Misreporting Insurance)  

Người dùng có thể chọn chấp nhận báo cáo từ tầng một một cách lạc quan hoặc chờ kết quả phân xử từ tầng hai. Để phòng rủi ro, có thể mua **misreporting insurance**, được cung cấp bởi các underwriter thông qua smart contract on-chain. Nếu báo cáo tầng một và tầng hai khác nhau, bảo hiểm sẽ tự động chi trả. Nhờ dữ liệu hiệu suất lịch sử của node và DON, chi phí bảo hiểm có thể giữ ở mức thấp mà vẫn bền vững.  

---

## Kết luận  

Thông qua cơ chế explicit staking super-linear, mạng Chainlink có thể mở rộng để hỗ trợ thế hệ hybrid smart contracts tiếp theo, bảo vệ ngày càng nhiều giá trị tài sản. Nếu smart contracts trở thành hình thức thỏa thuận số chủ đạo, thì mức bảo mật cryptoeconomic cao hơn này là rất quan trọng để đảm bảo tính chính xác, kịp thời và chống giả mạo trong việc thực thi các ứng dụng phi tập trung dựa vào báo cáo oracle và tính toán off-chain.  

Whitepaper Chainlink 2.0 cung cấp phân tích sâu hơn về explicit staking, gồm chi tiết thiết kế, cân nhắc và giải thích từng thành phần. Để tìm hiểu thêm, hãy tham khảo phần 9 của whitepaper.  

