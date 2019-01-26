---
title: -NoSplash (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f11b44833ae54c6982cc4df9e2dbd6cb03e7fcd1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927896"
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
