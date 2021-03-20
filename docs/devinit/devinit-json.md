---
title: Plik konfiguracji devinit
description: Dokumentacja .devinit.jsw pliku manifestu dla devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 4f94ee609ba4c0783a06648ed037e58d864aa2a9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672208"
---
# <a name="devinit-configuration-file"></a>plik konfiguracji devinit

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

`.devinit.json`Plik definiuje zależności systemowe, których potrzebuje aplikacja, aby można było uruchomić i skompilować. Zależności w całym systemie są takie jak Node.js, SQL Server, IIS, RabbitMQ, Docker itp. Są to sortowanie elementów, które zwykle instalujesz w polu dev, które nie są instalowane przez określone repozytorium. Nie jest to miejsce do definiowania zależności specyficznych dla aplikacji, takich jak w przypadku menedżerów pakietów, takich jak NuGet lub NPM. Istnieje jednak możliwość zdefiniowania potrzeb tych menedżerów pakietów.

## <a name="file-location"></a>Lokalizacja pliku

`devinit init`Polecenie jest realizowane za pośrednictwem `.devinit.json` pliku. Domyślnie program `devinit` szuka pliku w następujących lokalizacjach:

* {Current-Directory} \\.devinit.jsna
* {Current-Directory} \\devinit.jsna
* {Current-Directory} \\ . devinit \\.devinit.jsna
* {Current-Directory} \\ . devinit \\devinit.jsna
* {Current-Directory} \\ devinit \\.devinit.jsna
* {Current-Directory} \\ devinit \\devinit.jsna
* {Current-Directory} \\ . devcontainer \\.devinit.jsna
* {Current-Directory} \\ . devcontainer \\devinit.jsna

> [!NOTE]
> Jeśli zostanie znalezionych wiele plików domyślnych, devinit użyje pliku, który jest wyświetlany w pierwszej kolejności na powyższej liście.

`.devinit.json`Plik można również jawnie określić za pomocą `--file` / `-f` opcji.

### <a name="directories-and-relative-paths"></a>Katalogi i ścieżki względne

Ścieżki są względne dla lokalizacji, w której działa devinit. Jest to zazwyczaj bieżący katalog roboczy, z którego `devinit` wykonano.

## <a name="file-format"></a>Format pliku
W programie `.devinit.json` można określić więcej niż jedno narzędzie do uruchomienia. W `run` sekcji można umieścić dowolną liczbę obiektów. Przykład jest widoczny w naszym przykładzie [.devinit.jsna](sample-all-tool.md) wszystkich naszych narzędziach.

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Wartości właściwości

| Nazwa         | Typ   | Wymagane | Wartość                              |
|--------------|--------|----------|------------------------------------|
| **komentarz** | ciąg | Nie       | Komentarze do pliku.             |
| **wykonane**      | array  | Tak      | [Obiekt RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Uruchom obiekt narzędzia

| Nazwa                  | Typ   | Wymagane | Wartość                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **komentarz**          | ciąg | Nie       | Komentarze dotyczące wpisu narzędzia.                                                                               |
| **narzędziem**              | ciąg | Tak      | Nazwa narzędzia. Zobacz `devinit list` polecenie, aby uzyskać listę dostępnych narzędzi.                            |
| **klawiatur**             | ciąg | Nie       | Dane wejściowe narzędzia. Różni się według narzędzia. Na przykład wymagana wersja, identyfikator pakietu, nazwa pliku lub folder.|
| **additionalOptions** | ciąg | Nie       | Dodatkowe argumenty wiersza polecenia, które mają zostać przekazane do narzędzia.                                                |

## <a name="examples"></a>Przykłady

Aby uzyskać więcej przykładów użycia devinit, zobacz [sekcję Samples (przykłady](sample-readme.md)).
