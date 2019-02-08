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
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937958"
---
# <a name="nosplash-devenvexe"></a>/ NoSplash (devenv.exe)

Zapobiega są wyświetlane na ekranie powitalnym.

## <a name="syntax"></a>Składnia

```shell
devenv /NoSplash [File1[ FileN]...]
```

## <a name="arguments"></a>Argumenty

- *File1*

  Opcjonalna. Plik można otworzyć w istniejącego wystąpienia programu Visual Studio. Jeśli nie ma wystąpień programu Visual Studio, jest tworzone nowe wystąpienie o uproszczonym układzie okna i otwarciu narzędzia *plik1* w nowym wystąpieniu.

- *FileN*

  Opcjonalna. Jeden lub więcej dodatkowych plików do otwierania w istniejącym wystąpieniu programu Visual Studio.

## <a name="remarks"></a>Uwagi

Ten przełącznik powoduje ukrycie opcji na ekranie powitalnym. Pomijając ten przełącznik powoduje, że ekran powitalny do wyświetlenia. Aby sprawdzić na ekranie powitalnym dalsze (na przykład, aby sprawdzić, ikona produktu pakietu VSPackage), należy użyć [/powitalny](../../extensibility/devenv-command-line-switches-for-vspackage-development.md) przełącznika.

`/NoSplash` Przełącznika może być łączone z innymi przełącznikami, takich jak [/Run](run-devenv-exe.md) lub [/DebugExe](debugexe-devenv-exe.md).

## <a name="example"></a>Przykład

Wszystkie trzy przykłady Otwórz IDE bez wyświetlania na ekranie powitalnym. Drugi przykład również określone rozwiązanie kompiluje i uruchamia wbudowanych pliku wykonywalnego. Trzeci przykład otwiera określony plik wykonywalny do debugowania w środowisku IDE.

```shell
devenv /nosplash

devenv /nosplash /run MySolution.sln

devenv /nosplash /debugexe MySolution.exe
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Przełączniki wiersza polecenia Devenv dla programowania pakietu VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
