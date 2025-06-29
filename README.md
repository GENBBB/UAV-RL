# UAV-RL
# Автономный автопилот БПЛА с использованием RLlib, ROS2 и Gazebo

Робототехническая система для обучения автопилотов квадрокоптеров с глубоким обучением с подкреплением. Поддерживает навигацию к цели, следование по точкам и спроектирована для будущего расширения с обходом препятствий.

## Ключевые особенности
- 🎯 Навигация к целям (одиночная цель и цепочки точек)
- 🧠 Обучение с RL оптимизировано для GPU 6 ГБ (RTX 4050)
- 🔧 Расширяемая архитектура для препятствий/кастомной одометрии
- 🔄 Бесшовная интеграция ROS2-Gazebo-RLlib
- ⚡ Возможности развертывания в реальном времени
- 🛡️ Трехконтурная система управления (RL/ПИД/Ручной)

## Структура проекта
```
UAV-RL/
├── core/                           # Основные компоненты системы
│   ├── environments/               # Реализации RL-сред
│   ├── perception/                 # Интерфейсы обработки сенсоров
│   ├── control/                    # Системы управления
│   └── utils/                      # Вспомогательные инструменты
├── simulation/                     # Интеграция с Gazebo
│   ├── gazebo/                     
│   └── ros2_bridge/                # Мост ROS2-RLlib
├── training/                       # Конфигурация обучения
│   ├── rllib/                      # Настройки алгоритмов RL
│   ├── gpu_optimizer/              # Оптимизации для GPU
│   └── curriculum/                 # Планы поэтапного обучения
├── deployment/                     # Развертывание на дроне
│   ├── ros2_nodes/                 # ROS2 узлы
│   ├── model_compression/          # Оптимизация моделей
│   └── real_time_configs/          # Настройки реального времени
├── configs/                        # Централизованные конфигурации
│   ├── env/                        # Параметры сред
│   └── hardware/                   # Аппаратные настройки
├── tests/                          # Тесты системы
│   ├── unit/                       # Юнит-тесты
│   └── integration/                # Интеграционные тесты
├── scripts/                        # Управляющие скрипты
├── requirements.txt                # Python зависимости
├── ros2_dependencies.txt           # ROS2 пакеты
└── Dockerfile                      # Конфигурация контейнера
```

## Начало работы

### Предварительные требования
- Ubuntu 22.04
- ROS2 Jazzy
- NVIDIA драйверы >= 525
- Python 3.8+

### Установка
```bash
# Клонирование репозитория
git clone https://github.com/GEN_BBB/drone-autopilot-rl.git
cd UAV-RL

# Установка зависимостей
pip install -r requirements.txt
sudo apt install $(cat ros2_dependencies.txt)

# Сборка ROS2 рабочего пространства
colcon build --symlink-install
source install/setup.bash
```

### Обучение модели
```bash
# Запуск симуляции
ros2 launch simulation/gazebo/launch/training.launch.py

# Старт обучения (в отдельном терминале)
./scripts/start_training.sh --config configs/env/single_target.yaml
```

### Развертывание на дроне
```bash
./scripts/deploy_real.sh --model path/to/optimized_model.trt
```

## Ключевые компоненты

### Системы навигации
- **point_navigation.py**: Следование к одиночной цели
- **waypoint_tracking.py**: Последовательное достижение точек маршрута
- **obstacle_extension.py**: Шаблон для будущей реализации препятствий

### Адаптеры восприятия
- **ground_truth.py**: Точные данные позиции (симуляция)
- **odometry_interface.py**: Базовый класс для кастомной одометрии
- **sensor_fusion.py**: Объединение данных сенсоров

### Оптимизации для RTX 4050
- Автоподбор размера батча под 6 ГБ VRAM
- Mixed-precision вычисления (FP16)
- Оффлоад данных на CPU при переполнении

## Расширение функционала

### Добавление препятствий
1. Реализовать логику в `obstacle_extension.py`
2. Создать мир с препятствиями в `simulation/gazebo/worlds/`
3. Обновить конфигурацию сенсоров

### Интеграция кастомной одометрии
1. Наследовать класс от `odometry_interface.py`
2. Зарегистрировать адаптер в `sensor_fusion.py`
3. Протестировать через `tests/unit/test_odometry.py`

## Тестирование
```bash
# Запуск всех тестов
pytest tests/

# Интеграционное тестирование
pytest tests/integration/test_control_switch.py
```

## Поддержка оборудования
- Оптимизировано для NVIDIA RTX 4050 (6 ГБ)

## Лицензия
Apache 2.0 License
