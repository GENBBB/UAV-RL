# Конфигурация обучения
Настройки алгоритмов RL и оптимизации под оборудование.

## rllib/
- [WIP] `ppo_config.yaml`: Параметры алгоритма PPO
- [WIP] `sac_config.yaml`: Конфиг для алгоритма SAC
- [WIP] `multi_agent_setup.py`: Настройка параллельных сред

## gpu_optimizer/
- [WIP] `memory_manager.py`: Автоматический контроль VRAM (6GB GPU)
- [WIP] `fp16_strategy.py`: Реализация mixed-precision вычислений

## curriculum/
- [WIP] `basic_waypoints.yaml`: Простые траектории для начального обучения
- [WIP] `advanced_paths.yaml`: Сложные маршруты для продвинутой стадии