---
title: -DoNotLoadProjects (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia DoNotLoadProjects devenv otworzyć określone rozwiązanie bez ładowania żadnych projektów.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef3502a2180f7ae7ed5963deb14844b46f3dbff9
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040631"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Nowość dla programu Visual Studio 2019 w wersji 16,1**

Otwiera określone rozwiązanie bez ładowania żadnych projektów. Aby uzyskać więcej informacji, zobacz [przefiltrowane rozwiązania w programie Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Składnia

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumenty

*SolutionName*

Wymagane. Pełna ścieżka i nazwa rozwiązania, które ma zostać otwarte.

## <a name="example"></a>Przykład

Przykład otwiera rozwiązanie MySln. sln bez ładowania żadnych projektów.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Zobacz też

- [Rozwiązania filtrowane w programie Visual Studio](../filtered-solutions.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
