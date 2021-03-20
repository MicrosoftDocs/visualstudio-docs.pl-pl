---
title: devinit i GitHub Codespaces
description: Dowiedz się, jak dostosować codespace dla programu Visual Studio przy użyciu devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c98c00e0b62d3a2a755790b07621d717abcb41c1
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672222"
---
# <a name="devinit-and-github-codespaces"></a>devinit i GitHub Codespaces

> [!IMPORTANT]
> Od 12 kwietnia 2021 połączenie z usługą GitHub Codespaces z programu Visual Studio 2019 nie będzie już obsługiwane i zostanie zawarta prywatna wersja zapoznawcza. Firma Microsoft koncentruje się na rozwojem środowisk dla chmurowych i opartych na chmurze rozwiązań infrastruktury VDI zoptymalizowanych pod kątem szerokiego zestawu obciążeń programu Visual Studio. W ramach tego `devinit` i skojarzonych narzędzi nie będą już dostępne. Zachęcamy do pracy na naszym forum społeczności deweloperów dla programu Visual Studio, aby uzyskać informacje na temat przyszłych informacji o zaplanowanych i związanych z planami.

devinit to doskonały uzupełnienie usługi [GitHub Codespaces](https://github.com/features/codespaces) i devinit może służyć do uzyskania konfiguracji codespace, aby Współautorzy mogli kompilować, uruchamiać i debugować od razu.

> [!IMPORTANT]
> Przed integracją devinit z codespace należy najpierw upewnić się, `.devinit.json` że masz plik, który definiuje zależności. Aby uzyskać więcej informacji na temat tworzenia `.devinit.json` , Przeczytaj [dokumentację wprowadzenie](getting-started-with-devinit.md).

W witrynie GitHub Codespace aplikacja została skompilowana i uruchomiona w chmurze. W chmurze oznacza, że aplikacja nie ma dostępu do zasobów lokalnych na Twoich komputerach. Dotyczy to również narzędzi lub programów zainstalowanych lokalnie. Jeśli aplikacja wymaga zainstalowania lub skonfigurowania zależności w całym systemie, należy je wykonać na każdym codespace. Najprostszym sposobem osiągnięcia tego jest użycie `.devinit.json` pliku.

Aby upewnić się, że codespace jest tworzona z zależnościami wymaganymi przez aplikację, należy `devinit` uruchomić ją podczas tworzenia codespace. Można to zrobić przez wywołanie `devinit init` z poziomu `postCreateCommand` zdefiniowanego w `.devcontainer.json` pliku umieszczonym w katalogu głównym repozytorium. Ciąg (s) w programie `postCreateCommand` są wykonywane w domyślnej powłoce, po sklonowaniu repozytorium w codespace. Więcej informacji można znaleźć `postCreateCommand` w [dokumentacji dostosowania](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)Codespaces usługi GitHub. Aby dodać `devinit` polecenie, możesz dodać do polecenia, `devinit init` `postCreateCommand` jak pokazano w poniższych przykładach.

Możesz również wykonać `devinit init -f <path to .devinit.json>` z poziomu zintegrowanego terminalu programu Visual Studio po nawiązaniu połączenia z codespace.

## <a name="examples"></a>Przykłady

W obu przykładach `.devinit.json` znajduje się w katalogu głównym repozytorium wraz z `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>Z .devcontainer.jsw pliku

W tym przykładzie `.devcontainer.json` Poniższy plik znajduje się w katalogu głównym repozytorium obok `.devinit.json` pliku. Pliki można również umieścić w `.devcontainer` katalogu.

```json
{
  "postCreateCommand": "devinit init"
}
```

Gdy `.devinit.json` znajduje się w innym katalogu, można użyć flagi-f.

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

Więcej przykładów użycia devinit można znaleźć w naszej [dokumentacji](sample-all-tool.md) i w witrynie GitHub na przykład na [platformie .NET Core](https://github.com/microsoft/devinit-example-dotnet-core) , a [Node.js przykładowe](https://github.com/microsoft/devinit-example-nodejs) repozytoria.

### <a name="as-commands"></a>Jako polecenia

W tym przykładzie `.devcontainer.json` Poniższy plik znajduje się w katalogu głównym repozytorium i `devinit run` jest wywoływany bezpośrednio z wiersza polecenia w celu uruchomienia indywidualnego narzędzia.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Z poziomu wiersza terminalu

Gdy bieżący katalog roboczy zawiera `.devinit.json` plik.

```console
devinit init
```

Gdy `.devinit.json` znajduje się w innym katalogu.

```console
devinit init -f path/to/.devinit.json
```
