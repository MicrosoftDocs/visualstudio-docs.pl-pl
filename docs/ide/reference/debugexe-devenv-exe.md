---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4eb1eb49cd6b29740fb6d365a98a51cc28387e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661678"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Otwiera określony plik wykonywalny do debugowania.

## <a name="syntax"></a>Składnia

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumenty

- *ExecutableFile*

  Wymagany. Ścieżka i nazwa pliku `.exe`. Jeśli plik `.exe` nie zostanie znaleziony lub nie istnieje, nie jest wyświetlane ostrzeżenie ani błąd, a program Visual Studio jest uruchamiany normalnie.

## <a name="remarks"></a>Uwagi

Wszystkie ciągi po parametrze *executablefile* są przekazane do tego pliku jako argumenty.

## <a name="example"></a>Przykład

Poniższy przykład otwiera plik `MyApplication.exe` na potrzeby debugowania.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)