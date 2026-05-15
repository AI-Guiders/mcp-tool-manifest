# mcp-tool-manifest

Общая библиотека **`McpToolManifest`** / NuGet **`AIGuiders.McpToolManifest`**: формат `mcp-tools.manifest.json`, чтение, валидация, сравнение имён с рантайм-каталогом.

У каждого MCP свой манифест в корне проекта; общий «протокол на все сервисы» не задаётся — только формат файла и эти хелперы.

## Установка

```bash
dotnet add package AIGuiders.McpToolManifest
```

Исходники и CI: этот репозиторий. В монорепо `financial-open` копия раньше лежала в `tools/McpToolManifest/` — канон теперь здесь.

## Формат

- `schema_version` — `1`
- `mcp_id` — id сервера
- `tools[]` — `name` (обяз.), `description` (опц.)

Пилот потребителей: [agent-notes-mcp](https://github.com/AI-Guiders/agent-notes-mcp), roslyn-mcp, git-mcp, dotnet-debug-mcp и др. (тесты `McpToolManifestTests` в каждом MCP).

## Сборка и NuGet (maintainers)

```bash
dotnet pack McpToolManifest.csproj -c Release -o nupkg
```

Публикация на **nuget.org**: workflow [`.github/workflows/nuget-publish.yml`](.github/workflows/nuget-publish.yml) (Trusted Publishing, аккаунт **LonelySoul** — настроить репозиторий `KarataevDmitry/mcp-tool-manifest` на nuget.org, как у `git-mcp-core`).

Тег `v1.0.0` или `workflow_dispatch` с версией SemVer.

## Лицензия

MIT — см. [LICENSE](LICENSE).
