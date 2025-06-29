# Ядро системы
Основные компоненты автопилота. Содержит реализации сред, систем восприятия и управления.

## environments/
- [WIP] `base_env.py`: Абстрактный базовый класс для всех RL-сред
- [WIP] `point_navigation.py`: Среда для следования к одиночной цели
- [WIP] `waypoint_tracking.py`: Среда для следования по цепочке точек
- [WIP] `obstacle_extension.py`: Шаблон для будущей интеграции препятствий

## perception/
- [WIP] `ground_truth.py`: Получение точных данных позиции из симуляции
- [WIP] `odometry_interface.py`: Базовый класс для реализации кастомной одометрии
- [WIP] `sensor_fusion.py`: Объединение данных от разных сенсоров

## control/
- [WIP] `rl_controller.py`: Основной RL-контроллер (политика)
- [WIP] `pid_fallback.py`: ПИД-регулятор как резервная система
- [WIP] `manual_override.py`: Система ручного управления

## utils/
- [WIP] `trajectory_logger.py`: Логирование траекторий полета
- [WIP] `config_loader.py`: Динамическая загрузка YAML-конфигов