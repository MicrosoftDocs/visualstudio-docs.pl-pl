---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34fe7dfed2774eace7d32b1c9041355b566d4e76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654493"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv. exe)

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

## <a name="see-also"></a>Zobacz także

- [Rozwiązania filtrowane w programie Visual Studio](../filtered-solutions.md)
- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
