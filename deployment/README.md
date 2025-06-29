# Развертывание на реальном дроне
Оптимизация и запуск модели в реальном времени.

## ros2_nodes/
- [WIP] `inference_engine.py`: Узел инференса (>100Hz)
- [WIP] `diagnostics.py`: Мониторинг производительности и ресурсов

## model_compression/
- [WIP] `quantize_model.py`: Квантование модели (FP32 → INT8)
- [WIP] `torchscript_export.py`: Экспорт в TorchScript

## real_time_configs/
- [WIP] `priority_settings.yaml`: Настройки приоритетов процессов
- [WIP] `latency_optimization.yaml`: Параметры оптимизации задержек