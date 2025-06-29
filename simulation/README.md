# Интеграция с симулятором
Конфигурация Gazebo и мост между ROS2 и RLlib.

## gazebo/worlds/
- [WIP] `empty.world`: Пустой мир для базового обучения
- [WIP] `obstacles.world`: Шаблон мира с препятствиями

## gazebo/models/iris_rl/
- [WIP] SDF-файлы кастомизированной модели дрона Iris

## gazebo/launch/
- [WIP] `training.launch.py`: ROS2 launch-файл для обучения
- [WIP] `eval.launch.py`: Launch-файл для тестирования моделей

## ros2_bridge/
- [WIP] `env_node.py`: Главный узел связи среды с RLlib
- [WIP] `data_adapter.py`: Конвертер ROS2 сообщений ↔ тензоры PyTorch