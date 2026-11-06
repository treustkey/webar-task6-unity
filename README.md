# Задание 6 — Unity WebXR

## Фактический статус
Подготовлены исходные файлы и автоматизация создания сцены/сборки. Это заготовка проекта, не законченная работа: WebGL Build Support не установлен; сборка и тест на мобильном устройстве не выполнены. Размер сборки не измерен. docs/index.html — честная страница статуса, не имитация Unity.

## Подготовка
1. Unity Hub: установить WebGL Build Support для 6000.3.7f1. Открыть эту папку как проект.
2. Дождаться установки пакетов OpenUPM. В Package Manager импортировать BiRP Sample пакета WebXR Interactions (версию interactions при необходимости выбрать доступную в реестре).
3. Window > WebXR > Copy WebGLTemplates. Project Settings > XR Plug-in Management > WebGL: включить WebXR Export; в WebXR Settings отключить Display Submodule для Built-in Render Pipeline.
4. Выбрать WebGL. Выполнить WebAR > Create Scene: используется оригинальный prefab WebXRCameraSet со встроенными WebXRController. Если prefab не найден, команда явно завершится ошибкой.
5. Проверить имя шаблона в Assets/WebGLTemplates. BuildProject.cs использует PROJECT:WebXR; изменить его при другом имени установленного шаблона. WebAR > Build WebGL. Compression Disabled, Decompression Fallback false, threadsSupport false.
6. Выгрузить docs на GitHub Pages. Размер после успешной сборки записывается в BUILD_SIZE.txt. Не коммитить Library, Temp и логи.

## Сценарий
ViewerObject.LateUpdate привязывает куб на расстоянии 1.2 м к активной Camera.main. Он остаётся в центре поля зрения (viewer-space), а не прикрепляется к поверхности.

## Протокол тестирования (не выполнен)
Записать модель телефона, ОС, браузер, наличие ARCore/WebXR, дату, время загрузки, размер передачи, вход/выход AR, видимость куба и поведение при движении головы. Проверить обычный браузер. На несовместимых браузерах AR не считать пройденным. Репозиторий upstream предупреждает об ограниченной мобильной поддержке.

## Источники
https://github.com/De-Panther/unity-webxr-export
https://github.com/De-Panther/unity-webxr-export/blob/master/Documentation/Getting-Started.md

Пакеты WebXR 0.25.0 и WebGLTemplates включены локально с лицензией Apache-2.0. Шаблон сборки: WebXR2020. Папка Assets содержит BiRP WebXRCameraSet. Редактор пока не завершил повторный импорт пакетов; готовая сцена не подтверждена.


Обновление проверки: Unity batchmode завершился с кодом 0; Assets/Scenes/ViewerSpace.unity успешно создана. Скрипты компилируются. WebGL-сборка и мобильный тест по-прежнему не выполнены. Архив содержит runtime/editor части пакетов; примеры с текстурами исключены для уменьшения размера.

