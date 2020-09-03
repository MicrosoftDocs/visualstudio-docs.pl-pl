---
title: -DoNotLoadProjects (devenv.exe)
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
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75569858"
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

Wymagany. Pełna ścieżka i nazwa rozwiązania, które ma zostać otwarte.

## <a name="example"></a>Przykład

Przykład otwiera rozwiązanie MySln. sln bez ładowania żadnych projektów.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Zobacz też

- [Rozwiązania filtrowane w programie Visual Studio](../filtered-solutions.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
