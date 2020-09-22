---
title: devinit i GitHub Codespaces
description: Dowiedz się, jak dostosować codespace dla programu Visual Studio przy użyciu devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: b42ce84bcb2a336e37d0ffafb2bab6c2dba9ba9d
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852210"
---
# <a name="devinit-and-github-codespaces"></a>devinit i GitHub Codespaces

devinit to świetna odnosi się do usługi [GitHub Codespaces](https://github.com/features/codespaces) i devinit może służyć do uzyskania konfiguracji codespace, aby Współautorzy mogli kompilować, uruchamiać i debugować od razu.

Aby przeprowadzić integrację z usługą GitHub Codespaces, należy `devinit` wywołać ją z poziomu `postCreateCommand` zdefiniowanego w pliku znajdującego się `.devcontainer.json` w katalogu głównym repozytorium. Ciąg (s) w programie `postCreateCommand` są wykonywane w domyślnej powłoce, po sklonowaniu repozytorium w codespace. Więcej informacji można znaleźć `postCreateCommand` w [dokumentacji dostosowania](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)Codespaces usługi GitHub. Aby dodać `devinit` polecenie, możesz dodać do polecenia, `devinit init` `postCreateCommand` jak pokazano w poniższych przykładach.

Możesz również wykonać `devinit init -f <path to .devinit.json>` z poziomu zintegrowanego terminalu programu Visual Studio po nawiązaniu połączenia z codespace.

## <a name="examples"></a>Przykłady

### <a name="with-a-devinitjson-file"></a>Z .devinit.jsw pliku
W tym przykładzie _.devcontainer.jsw_ pliku poniżej znajduje się w katalogu głównym repozytorium obok _.devinit.jsna_ pliku. Pliki można również umieścić w katalogu _. devcontainer_ .

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>Jako polecenia
W tym przykładzie _.devcontainer.jsw_ pliku poniżej znajduje się w katalogu głównym repozytorium i `devinit run` jest wywoływana programowo w celu uruchomienia narzędzia  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Z poziomu wiersza terminalu

Gdy bieżący katalog roboczy zawiera _.devinit.js_ pliku.

```batch
> devinit init
```

Gdy _.devinit.json_ znajduje się w innym katalogu.

```batch
> devinit init -f path/to/.devinit.json
```
