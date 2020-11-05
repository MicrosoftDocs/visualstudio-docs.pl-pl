---
title: Plik konfiguracji devinit
description: Dokumentacja .devinit.jsw pliku manifestu dla devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2b6cc27d2614f71c85988457ab9bb64228bbaebb
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399967"
---
# <a name="devinit-configuration-file"></a>plik konfiguracji devinit

## <a name="file-location"></a>Lokalizacja pliku

`devinit.exe init`Polecenie jest realizowane za pośrednictwem _.devinit.js_ pliku. Domyślnie program `devinit.exe` szuka pliku w następujących lokalizacjach:

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

_.devinit.jsw_ pliku można również jawnie określić za pomocą `--file` / `-f` opcji.

### <a name="directories-and-relative-paths"></a>Katalogi i ścieżki względne

Ścieżki są względne dla lokalizacji, w której działa devinit. Jest to zazwyczaj bieżący katalog roboczy, z którego `devinit` wykonano.

## <a name="file-format"></a>Format pliku

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
