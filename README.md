# Обновления VORDA Launcher

Публичный канал Windows x64 для подписанных установщиков VORDA на Tauri 2. Файлы выпусков хранятся в разделе [Releases](https://github.com/V0RDA/VORDA-update/releases).

## Публикация новой версии

В закрытом репозитории лаунчера откройте `launcher-tauri`. С установленными зависимостями, Rust/MSVC и заданным в окружении `TAURI_SIGNING_PRIVATE_KEY` выполните:

```powershell
. ..	ools\Enter-NativeEnvironment.ps1
.	ools\Build-GitHubRelease.ps1 -Version <версия> -PublicKeyFile <путь-к-публичному-ключу>
```

Скрипт создаст подписанный NSIS-установщик, его `.sig` и `latest.json` в `launcher-tauri/artifacts/release-v<версия>/`. Загрузите все три файла в черновик GitHub Release с тегом `v<версия>`. Сверьте версию и протестируйте обновление на Windows. После публикации как Latest установленный Tauri-лаунчер сможет получить обновление из GitHub.

Ключ подписи хранится в закрытом окружении сборки. Публичный ключ должен совпадать с ключом, который встроен в установленные версии. Первый установщик и обновления подписываются соответствующим приватным ключом. Формат обновления описан в [документации Tauri](https://v2.tauri.app/plugin/updater/).
