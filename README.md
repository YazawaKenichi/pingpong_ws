# CIT-Advanced-Robotics-Project-2025E

# 概要
卓球ボールを射出するロボットのソフトウェアリポジトリをまとめるリポジトリ

# インストール
```
sudo apt update
sudo apt install python3-vcstool
cd $HOME
git clone https://github.com/yazawakenichi/pingpong_ws
```

仮想環境の作成と有効化
```
cd pingpong_ws
python3 -m venv venv
source venv/bin/activate
source /opt/ros/$ROS_DISTRO/setup.bash
```

インポート
```
cd ~/pingpong_ws
mkdir src
vcs import src < main.repos
```

Python 仮想環境の作成
```
cd ~/pingpong_ws
python3 -m venv venv
```

Python パッケージのインストール
```
cd ~/pingpong_ws
~/pingpong_ws/venv/bin/pip install -r requirements.txt
```

# ビルド
```
cd ~/pingpong_ws
rosdep update
rosdep install -y --from-paths src --ignore-src --rosdistro $ROS_DISTRO
~/pingpong_ws/venv/bin/colcon build --symlink-install
source $HOME/pingpong_ws/install/setup.bash
```

## micro-ROS Agent のビルド（必須）
```
cd ~/pingpong_ws
ros2 run micro_ros_setup create_firmware_ws.sh host
ros2 run micro_ros_setup build_firmware.sh
source $HOME/pingpong_ws/install/local_setup.bash
ros2 run micro_ros_setup create_agent_ws.sh
ros2 run micro_ros_setup build_agent.sh
source $HOME/pingpong_ws/install/local_setup.bash
```

## 動作確認（任意）
### micro-ROS Agent
```
ros2 run micro_ros_agent micro_ros_agent serial -b 115200 --dev /dev/ttyACM0 -v6
```

上記を起動してから [yazawakenichi/pico-pwm](https://github.com/yazawakenichi/pico-pwm) が組み込まれた Raspberry Pi Pico を接続 USB 経由で接続

# 
(C) 2025 年度 千葉工業大学 大学院 先進工学研究科 未来ロボティクス専攻 ロボット設計製作特論 E グループ

