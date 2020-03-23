---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /NoSplash switch
- /NoSplash Devenv switch
- NoSplash Devenv switch
author: DennisLee-DennisLee
ms.author: v-dele
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a1e8118faa743398271fb282a2603aab5fcd76b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950658"
---
# <a name="nosplash-devenvexe"></a>/NoSplash (devenv.exe)

Zapobiega pokazywaniu ekranu powitalnego.

## <a name="syntax"></a>Składnia

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *Plik1*

  Element opcjonalny. Plik do otwarcia w istniejącym wystąpieniu programu Visual Studio. Jeśli nie istnieje żadne wystąpienie programu Visual Studio, zostanie utworzone nowe wystąpienie z uproszczonym układem okna, a narzędzie otworzy *plik1* w nowym wystąpieniu.

- *Plik*

  Element opcjonalny. Jeden lub więcej dodatkowych plików do otwarcia w istniejącym wystąpieniu programu Visual Studio.

## <a name="remarks"></a>Uwagi

Ten przełącznik ukrywa ekran powitalny. Pozostawienie tego przełącznika powoduje wyświetlenie ekranu powitalnego. Jeśli chcesz zbadać ekran powitalny dalej (na przykład, aby sprawdzić ikonę produktu VSPackage), użyj przełącznika [/Splash.](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)

Przełącznik `/NoSplash` może być łączony z innymi przełącznikami, takimi jak [/Run](run-devenv-exe.md) lub [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Przykład

Wszystkie trzy przykłady otwierają IDE bez wyświetlania ekranu powitalnego. Drugi przykład kompiluje również określone rozwiązanie i uruchamia wbudowany plik wykonywalny. Trzeci przykład otwiera określony plik wykonywalny do debugowania w IDE.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Przełączniki wiersza polecenia Devenv dla rozwoju VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
