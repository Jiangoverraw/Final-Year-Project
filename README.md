# Game Kinh Dị Hợp Tác (Lấy Cảm Hứng từ MIMESIS)

## Tổng Quan Dự Án

Dự án này là một **trò chơi kinh dị co-op nhiều người chơi** được phát triển bằng **Unity Engine**.  
Gameplay tập trung vào việc **hợp tác giữa người chơi, khám phá môi trường nguy hiểm và thu thập vật phẩm có giá trị**, đồng thời phải tránh các sinh vật nguy hiểm.

Thiết kế gameplay lấy cảm hứng từ **MIMESIS**, một trò chơi kinh dị tâm lý nơi người chơi không thể hoàn toàn tin tưởng đồng đội của mình.

Một cơ chế quan trọng của trò chơi là **quái vật có thể giả dạng người chơi và bắt chước giọng nói mà người chơi đã nói trước đó**, tạo nên yếu tố kinh dị tâm lý và sự nghi ngờ giữa các thành viên trong nhóm.

---

# Nền Tảng

PC (Windows)

---

# Game Engine

Unity LTS  
Rendering Pipeline: **Universal Render Pipeline (URP)**

URP được sử dụng để:

- Tối ưu hiệu năng
- Cải thiện hệ thống ánh sáng cho môi trường kinh dị
- Áp dụng các hiệu ứng hậu kỳ như:
  - Film Grain
  - Chromatic Aberration
  - Fog
  - Color Grading

---

# Gameplay Loop

Gameplay Loop mô tả chu trình trải nghiệm chính của người chơi trong game.

Start Game
→
Join Lobby
→
Spawn in Mission Area
→
Explore the Map
→
Find Valuable Items
→
Cooperate to Carry Heavy Objects
→
Avoid or Escape Monsters
→
Deliver Loot to Extraction Zone
→
Receive Money / Rewards
→
Start Next Mission

---


---

# Các Tính Năng Gameplay

## Khám Phá (Exploration)

Người chơi sẽ khám phá những môi trường nguy hiểm như:

- Nhà máy bỏ hoang  
- Phòng thí nghiệm  
- Kho công nghiệp  

Các bản đồ sẽ được **tạo ngẫu nhiên (procedural generation)** để tăng tính chơi lại.

---

## Hệ Thống Loot

Mỗi vật phẩm có **trọng lượng và giá trị khác nhau**.

| Vật phẩm | Trọng lượng | Giá trị |
|---------|-------------|--------|
Laptop | Trung bình | 100 |
Máy phát điện | Nặng | 300 |
Ổ dữ liệu | Nhẹ | 50 |

Một số vật phẩm cần **2 người khiêng cùng lúc**.

---

## Gameplay Hợp Tác

Người chơi cần giao tiếp và phối hợp để:

- Khiêng vật nặng
- Khám phá khu vực nguy hiểm
- Trốn khỏi quái vật
- Hoàn thành nhiệm vụ

Tinh thần **teamwork** là yếu tố quan trọng để sống sót.

---

# Hệ Thống Quái Vật Giả Dạng (Mimic Monster)

Một cơ chế kinh dị quan trọng của game là **quái vật có khả năng giả dạng người chơi**.

Quái vật có thể:

- Sao chép ngoại hình người chơi
- Bắt chước chuyển động
- Phát lại giọng nói người chơi đã nói trước đó

Cơ chế này tạo nên **sự căng thẳng và nghi ngờ trong nhóm người chơi**.

---

## Các Giai Đoạn Hoạt Động Của Quái Vật

### Quan Sát (Observation)

Quái vật theo dõi người chơi và ghi lại voice chat.

---

### Giả Dạng (Mimic)

Quái vật chọn một người chơi và sao chép:

- Model nhân vật
- Animation
- Tên người chơi

Sau đó nó **trộn vào nhóm người chơi**.

---

### Bắt Chước Giọng Nói (Voice Mimic)

Quái vật có thể phát lại voice chat trước đó.

Ví dụ:

Người chơi đã nói:

> "Lại đây, tôi tìm thấy vật gì đó."

Sau đó quái vật có thể lặp lại câu này để dụ người chơi khác.

---

### Tấn Công (Attack)

Khi người chơi tiến lại gần:

- Quái vật lộ diện
- Tấn công bất ngờ

---

# Công Nghệ Sử Dụng

## Game Engine

Unity LTS với URP.

---

## Multiplayer

Sử dụng **Photon Fusion 2**.

Tính năng:

- Multiplayer real-time
- Lobby system
- Đồng bộ người chơi
- Đồng bộ vật thể

---

## Hệ Thống Vật Lý

Sử dụng **Unity Rigidbody Physics**.

Ứng dụng cho:

- Tương tác vật thể
- Khiêng vật phẩm
- Va chạm môi trường

Cơ chế nhặt vật sử dụng:

- Rigidbody
- Configurable Joint

---

## AI

AI sử dụng **Unity NavMesh System**.

Chức năng:

- Pathfinding
- Phát hiện người chơi
- Tấn công
- Hành vi giả dạng

---

## Voice Chat

Sử dụng **Photon Voice 2**.

Hỗ trợ:

- Voice chat theo khoảng cách (proximity voice)
- Spatial audio
- Ghi âm voice

---

# Hệ Thống Voice Mimic

Quái vật có thể phát lại giọng nói người chơi.

## Ghi Âm Voice

Voice chat được lưu vào buffer.

Player1
clip1
clip2
clip3

---


---

## Phát Lại Voice

Quái vật:

1. Lấy clip từ buffer  
2. Phát lại bằng Audio Source  
3. Áp dụng 3D spatial audio  

Âm thanh sẽ giống như phát ra từ vị trí của quái vật.

---

# Game Architecture
Player Client
│
Input System
│
Player Controller
│
Gameplay Systems
│
├── Physics System
├── AI System
├── Loot System
│
Networking Layer (Photon Fusion)
│
Game Host

---

# System Architecture
Player Client
│
Networking Layer
│
├── Physics System
├── AI System
├── Voice Chat System
│
Game Manager


---

# Procedural Map Generation

Game sử dụng **procedural generation** để tạo bản đồ ngẫu nhiên.

Các module phòng:

- Corridor (Hành lang)
- Storage Room (Kho)
- Control Room (Phòng điều khiển)
- Laboratory (Phòng thí nghiệm)

---

## Quy Trình Tạo Bản Đồ
Start Game
→
Create Map Grid
→
Spawn Starting Room
→
Attach Random Rooms
→
Validate Room Connections
→
Spawn Loot Points
→
Spawn Enemy Locations
→
Spawn Exit Point


---


---

# Phân Chia Công Việc

Dự án được thực hiện bởi **2 thành viên**, mỗi người phụ trách khoảng **50% hệ thống game**.

---

## Thành viên 1 – Gameplay & Physics

Nhiệm vụ:

- Player Controller
- Camera System
- Object Interaction
- Loot System
- Cooperative Carry System
- Gameplay UI
- Mission Logic

Công nghệ:

- Unity Physics
- Animation Rigging
- Unity UI

---

## Thành viên 2 – Multiplayer & AI

Nhiệm vụ:

- Photon Fusion Networking
- Lobby System
- Player Synchronization
- Object Network Sync
- Enemy AI
- Mimic Monster System
- Voice Mimic System
- Procedural Map Generation

Công nghệ:

- Photon Fusion
- Photon Voice
- NavMesh AI

---

# Timeline Phát Triển (10 Tuần)

## Tuần 1–2
- Setup project
- Player controller
- Physics interaction

---

## Tuần 3–4
- Multiplayer lobby
- Player synchronization

---

## Tuần 5–6
- Loot system
- Cooperative carry mechanics

---

## Tuần 7–8
- Enemy AI
- Mimic monster system

---

## Tuần 9–10
- Voice mimic system
- Bug fixing
- Optimization
- Final build
