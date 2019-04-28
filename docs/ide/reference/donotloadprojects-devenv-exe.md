---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 03/11/2019
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
ms.openlocfilehash: de757e7022339b11f6d7c04ea7315abf685da24c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428042"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

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
