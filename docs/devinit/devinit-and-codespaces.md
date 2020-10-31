---
title: devinit i GitHub Codespaces
description: Dowiedz się, jak dostosować codespace dla programu Visual Studio przy użyciu devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: a9731469f6725c0a4b9118c4e41235974a19c473
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134386"
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

```console
devinit init
```

Gdy _.devinit.json_ znajduje się w innym katalogu.

```console
devinit init -f path/to/.devinit.json
```
