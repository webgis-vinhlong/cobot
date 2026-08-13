# 🦾 Cobot Lab 3D

Trang tài liệu học tập mở về **cobot (collaborative robot)** và **mô phỏng 3D cánh tay robot**, thiết kế cho người mới bắt đầu nhưng có lộ trình đi đến ROS 2, MoveIt 2, MuJoCo, robosuite, imitation learning và reinforcement learning.

> Trọng tâm của repository: **mô phỏng và hiểu bản chất cánh tay cobot**, với `ARISE-Initiative/robosuite` là framework thực hành chính cho robot manipulation / robot learning.

## 🌐 Trang học tương tác

Sau khi GitHub Pages được bật cho nhánh `main` / thư mục root, trang sẽ có địa chỉ:

**https://webgis-vinhlong.github.io/cobot/**

File web chính: [`index.html`](./index.html)

## ✨ Nội dung chính

- 🦾 Cobot là gì, khác robot công nghiệp truyền thống ở đâu.
- 🧩 Link, joint, frame, DoF, end-effector và kiến trúc cánh tay robot.
- 🎮 **Mô phỏng 3D cánh tay 6 khớp ngay trên trình duyệt** bằng Three.js.
- 🎚️ Teach pendant: kéo từng joint và xem vị trí TCP/end-effector.
- 🎯 Bộ giải **Inverse Kinematics (IK)** minh họa bằng numerical Jacobian + damped least squares.
- 📐 Forward kinematics, inverse kinematics, Jacobian, joint-space và task-space.
- ⚙️ Phân biệt mô phỏng động học với mô phỏng động lực học/contact.
- 🧪 Hướng dẫn bắt đầu với **robosuite + MuJoCo**.
- 🧠 Reinforcement learning, imitation learning, domain randomization và sim-to-real.
- 🤖 So sánh robosuite, MuJoCo Menagerie, PyBullet, CoppeliaSim, Webots, Isaac Lab và Robotics Toolbox for Python.
- 🛰️ ROS 2, MoveIt 2, `ros2_control`, Gazebo và driver robot thật.
- 🛡️ An toàn cobot theo ISO 10218-1:2025, ISO 10218-2:2025 và trạng thái hiện hành của ISO/TS 15066:2016.
- 🧭 Lộ trình 8 bài thực hành và các đề tài đồ án.

## 🎮 Mô phỏng 3D trong trang này là gì?

Mô hình 3D nhúng trong `index.html` là **mô phỏng động học giáo dục**. Nó giúp người học nhìn trực tiếp chuỗi biến đổi của 6 khớp và hiểu quan hệ giữa joint-space với vị trí TCP.

Mô hình web **không mô phỏng đầy đủ**:

- khối lượng và tensor quán tính;
- động lực học mô-men;
- ma sát;
- contact constraint;
- compliance;
- force/torque sensing;
- actuator dynamics;
- safety functions của robot thật.

Khi bài toán chuyển sang grasping, contact-rich manipulation hoặc robot learning, repository hướng người học sang **MuJoCo + robosuite**.

## ⭐ Trọng tâm: robosuite

Repository chính:

- https://github.com/ARISE-Initiative/robosuite

robosuite là framework modular cho robot manipulation / robot learning chạy trên MuJoCo. Framework cung cấp các abstraction cho environment, robot, arena, object, controller, sensor/observation, teleoperation và demonstration collection.

### Cài đặt cơ bản

```bash
python -m venv .venv
source .venv/bin/activate

pip install --upgrade pip
pip install robosuite

python -m robosuite.demos.demo_random_action
```

> Tài liệu robosuite chính thức nêu macOS và Linux là các nền tảng được hỗ trợ chính thức; phần installation của dự án có ghi chú riêng nếu thử chạy trên Windows.

## 🧰 Hệ sinh thái repository nên học

### Manipulation / Robot Learning

- **robosuite** — https://github.com/ARISE-Initiative/robosuite
- **robomimic** — https://github.com/ARISE-Initiative/robomimic
- **Isaac Lab** — https://github.com/isaac-sim/IsaacLab

### MuJoCo models

- **MuJoCo Menagerie** — https://github.com/google-deepmind/mujoco_menagerie

Menagerie hiện có nhiều model cánh tay hữu ích cho học cobot/robot manipulation như Franka Panda, KUKA iiwa14, Kinova Gen3, UR5e, UR10e và các model khác. Luôn đọc `README` và `LICENSE` trong từng thư mục model vì license có thể khác nhau.

### Python / physics simulation

- **Bullet / PyBullet** — https://github.com/bulletphysics/bullet3
- **Robotics Toolbox for Python** — https://github.com/petercorke/robotics-toolbox-python

### General-purpose robot simulator

- **CoppeliaSim** — https://github.com/CoppeliaRobotics/CoppeliaSim
- **Webots** — https://github.com/cyberbotics/webots

### ROS 2 / Motion planning

- **Universal Robots ROS 2 Driver** — https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver
- **Franka ROS 2** — https://github.com/frankarobotics/franka_ros2
- **MoveIt 2** — https://github.com/moveit/moveit2
- **gz_ros2_control** — https://github.com/ros-controls/gz_ros2_control

Các repository ROS 1 vẫn có giá trị tham khảo cho hệ thống cũ, nhưng dự án mới nên ưu tiên stack ROS 2 và kiểm tra đúng distro/branch tương thích.

## 🧭 Lộ trình học đề xuất

1. **Link – joint – frame – DoF**: thao tác trực tiếp mô hình 3D.
2. **Forward kinematics**: hiểu chuỗi homogeneous transformations.
3. **Inverse kinematics**: dùng target XYZ và quan sát hiện tượng khó hội tụ / workspace boundary.
4. **Jacobian & control**: joint-space, differential IK, operational space control.
5. **MuJoCo model**: mở và đọc MJCF từ MuJoCo Menagerie.
6. **robosuite**: chạy Lift, Stack, PickPlace; đổi robot và controller.
7. **ROS 2 + MoveIt 2**: robot description, planning scene, collision checking và trajectory execution.
8. **Robot Learning**: demonstration, behavior cloning/RL, evaluation và domain randomization.

## 🧪 Gợi ý đồ án

- Gắp và phân loại nông sản.
- Pick-and-place trong phòng thí nghiệm.
- Peg-in-hole / nut assembly.
- Human–robot handover.
- Lau bề mặt với điều khiển lực.
- Teleoperation → thu demonstration → imitation learning.
- So sánh cùng một nhiệm vụ giữa Panda, UR và Kinova.
- Sim-to-real với domain randomization và safety gate.

## 🛡️ Ghi chú về an toàn

Trang này phục vụ **giáo dục và nghiên cứu mô phỏng**, không phải tài liệu chứng nhận an toàn.

Nguồn ISO hiện hành cần lưu ý tại thời điểm cập nhật (13/08/2026):

- **ISO 10218-1:2025** — Robotics — Safety requirements — Part 1: Industrial robots.
- **ISO 10218-2:2025** — Robotics — Safety requirements — Part 2: Industrial robot applications and robot cells.
- **ISO/TS 15066:2016** — Collaborative robots; ISO vẫn liệt kê bản này là published/current nhưng đang trong tiến trình sửa đổi và dự án ISO/AWI 15066-1 được lên kế hoạch thay thế.

Simulation không thay thế risk assessment, validation, kiểm tra stop time/distance, đo lực/áp suất, guarding hay yêu cầu pháp lý tại nơi triển khai.

## 📚 Nguồn chính

- Zhu, Y., Wong, J., Mandlekar, A., Martín-Martín, R., Joshi, A., Nasiriany, S., Zhu, Y., & Lin, K. (2020). *robosuite: A Modular Simulation Framework and Benchmark for Robot Learning*. arXiv:2009.12293.
- ARISE Initiative. *robosuite*. https://github.com/ARISE-Initiative/robosuite
- Zakka, K., Tassa, Y., & MuJoCo Menagerie Contributors. *MuJoCo Menagerie*. https://github.com/google-deepmind/mujoco_menagerie
- Isaac Lab Project Developers. *Isaac Lab Documentation*. https://isaac-sim.github.io/IsaacLab/
- ISO. *ISO 10218-1:2025*.
- ISO. *ISO 10218-2:2025*.
- ISO. *ISO/TS 15066:2016*.

## 🚀 Bật GitHub Pages

Nếu Pages chưa được bật:

1. Mở repository **Settings**.
2. Chọn **Pages**.
3. Ở **Build and deployment → Source**, chọn **Deploy from a branch**.
4. Chọn branch **main** và thư mục **/(root)**.
5. Save.

Trang dùng HTML/CSS/JavaScript thuần, không cần build step.

## 🧱 Kiến trúc repository

```text
cobot/
├── index.html    # Trang học + mô phỏng 3D tương tác
└── README.md     # Giới thiệu, lộ trình và hướng dẫn Pages
```

## ℹ️ Ghi chú kỹ thuật

- 3D rendering: Three.js tải từ jsDelivr CDN.
- Không cần npm, bundler hay framework frontend.
- IK trên web chỉ giải **vị trí XYZ**, không ép orientation đầy đủ 6D.
- Bộ giải IK được thiết kế để minh họa Jacobian số và damped least squares, không thay thế solver công nghiệp.

---

**Mục tiêu của Cobot Lab 3D:** học bằng cách thay đổi tham số, quan sát hệ thống và nối từng khái niệm toán học với một hành vi robot nhìn thấy được.