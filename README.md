# Задание 6 — Unity WebXR

Проект расположен в C:\Users\user\Documents\Task6_Unity_WebXR.
Редактор: Unity 6000.3.7f1.

## Открытие и демонстрация
Запустить Open_Project.cmd или добавить эту папку через Unity Hub → Projects → Add project from disk.
Открыть Assets/Scenes/ViewerSpace.unity и нажать Play. Куб должен находиться перед активной камерой на расстоянии 1.2 м и оставаться в центре взгляда при её перемещении.
В Hierarchy есть оригинальный BiRP WebXRCameraSet пакета De-Panther, камеры AR/VR и контроллеры. Viewer-space Cube содержит ViewerObject.

## Настройки
WebXR Export / WebXR Interactions 0.25.0 включены локальными пакетами (лицензия Apache-2.0 в UPSTREAM-LICENSE).
XR Plug-in Management → WebGL: WebXRLoader.
WebXR Settings: Disable XR Display Subsystem = true (Built-in Render Pipeline), AR reference space = local.
WebGL: шаблон WebXR2020; compression Disabled; decompression fallback false; threads false.
Сцена добавлена в Build Settings. Команда WebAR → Configure Project повторно сохраняет настройки.
WebAR → Build WebGL создаёт сборку в docs; размер записывается в BUILD_SIZE.txt.

## Структура
Assets/Scripts/ViewerObject.cs — привязка объекта к активной камере.
Assets/Editor/BuildProject.cs — создание сцены, настройка WebXR, сборка.
Assets/Scenes/ViewerSpace.unity — готовая сцена.
Assets/WebGLTemplates — оригинальные шаблоны De-Panther.
Packages/com.de-panther.webxr* — исходные пакеты.

## Проверка
Скрипты и настройка сцены проверены запуском Unity в batchmode.
Мобильный AR требует HTTPS и браузера с WebXR immersive-ar. Физическое мобильное тестирование пока не выполнено. Зафиксировать устройство, ОС, браузер, загрузку, вход и выход из AR, положение куба, размер передачи и ошибки.

Источник: https://github.com/De-Panther/unity-webxr-export

WebGL Build Support установлен для Unity 6000.3.7f1. Проверка сцены: 5 камер, 2 контроллера, отсутствующих скриптов 0. Результат в VALIDATION.txt.


Open_Project.cmd ограничивает BEE_BUILD_THREADS до 8, чтобы сборка не запускала сотни компиляторов и не исчерпывала память компьютера.


WebGL-сборка успешно завершена (Unity exit 0). Готовые файлы находятся в docs. BUILD_SIZE.txt содержит отчёт Unity. Для запуска в браузере нужна раздача docs через HTTP localhost или HTTPS; двойной щелчок index.html не подходит.

