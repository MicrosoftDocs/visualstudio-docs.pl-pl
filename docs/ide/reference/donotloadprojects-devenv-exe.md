---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a414fde4dee401016e997fa5d6890da2ae8d9d53
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083932"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Nowość w Visual Studio 2019 wersji 16.1**

Otwiera określone rozwiązanie bez ładowania jakiegokolwiek projektu. Aby uzyskać więcej informacji, zobacz [filtrowane rozwiązań w programie Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Składnia

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumenty

*SolutionName*

Wymagana. Pełną ścieżkę i nazwę rozwiązania, które ma zostać otwarty.

## <a name="example"></a>Przykład

Przykład otwiera rozwiązanie MySln.sln bez ładowania jakiegokolwiek projektu.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Zobacz także

- [Filtrowane rozwiązań w programie Visual Studio](../filtered-solutions.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
