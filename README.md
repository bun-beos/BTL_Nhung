# BTL_Nhung
## A. Giới thiệu
Tính năng chính:
- Menu chọn trò chơi
- Lưu kỷ lục điểm

## E. Thiết kế phần mềm
### Dinosaur run
- Trạng thái nút bấm được xác định qua GPIO 23.
- Trạng thái khủng long được xác định qua 2 biến ***isJumping*** và ***isFalling***.
- Khi trạng thái nút bấm là LOW và khủng long không ở trạng thái đang nhảy (***isJumping = false***) cũng như trạng thái đang rơi (***isFalling = false***), khủng long nhảy lên cao đến mức 6 điểm ảnh trên màn hình OLED. 
- Khi nhảy đến điểm cao nhất khủng long sẽ tạm dừng ở đó 1 khoảng thời gian được khai báo trong biến ***dinoTopDelay*** (đơn vị là milisecond). Sau đó khủng long sẽ rơi xuống đến tọa độ của mặt đất.
- Tốc độ nhảy lên và rơi xuống của khủng long lần lượt là ***speedUp*** và ***speedDown***. Tốc độ này sẽ thay đổi theo từng khoảng trong quá trình nhảy lên và rơi xuống để tạo cảm giác mượt hơn. Tương ứng với từng khoảng, giá trị tốc độ được lưu trong mảng ***speedUpArray[]*** và ***speedDownArray[]***.
- Có 3 loại cây xương rồng được random hiển thị và lưu trong mảng ***cactusDisplay[3]*** - tại 1 thời điểm có tối đa 3 cây xương rồng trên màn hình. Khi một cây xương rồng ra khỏi màn chơi thì giá trị hiển thị sẽ được random lại và tọa độ X của cây xương rồng đó sẽ được dịch sang phải, tọa độ này sẽ được tính toán cách 1 khoảng thích hợp so với cây xương rồng cuối cùng đang được hiển thị.
- Cây xương rồng và mặt đất sẽ di chuyển từ phải qua trái với giá trị tốc độ được khai báo trong biến ***speed***. Mỗi khi người chơi tăng 10 điểm tốc độ này sẽ tăng lên.
- Kiểm tra va chạm: Kiểm tra xem vùng hiển thị của khủng long có chồng lên vùng hiển thị của cây xương rồng hay không. Nếu chồng lên thì trò chơi kết thúc.