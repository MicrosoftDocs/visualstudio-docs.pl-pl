---
title: OpenCV
description: Przykładowe dostosowanie przy użyciu devinit dla repozytorium OpenCV/OpenCV.
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
ms.openlocfilehash: dd8a17635b70d0f9f49852d09d8f1b9a6864e26e
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809098"
---
# <a name="opencv"></a>OpenCV

Ten przykład ilustruje modyfikacje, które muszą być obsługiwane przez program [OpenCV](https://github.com/opencv/opencv) w celu automatycznego aprowizacji z [GitHub Codespaces] https://github.com/features/codespaces) .

## <a name="devinitjson"></a>.devinit.jsna

Zawartość [_.devinit.js_](devinit-json.md) pliku. Ten plik musi znajdować się w tym samym folderze co _.devcontainer.js_.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

## <a name="devcontainerjson"></a>.devcontainer.jsna

Zawartość _.devcontainer.jsw_ pliku w katalogu głównym repozytorium.

```json
{
  "postCreateCommand": "devinit init"
}
```