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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570144"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Otwiera określony plik wykonywalny do debugowania.

## <a name="syntax"></a>Składnia

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumenty

- *ExecutableFile*

  Wymagany. Ścieżka i nazwa pliku `.exe` . Jeśli `.exe` plik nie zostanie znaleziony lub nie istnieje, wyświetlane jest ostrzeżenie lub błąd, a program Visual Studio jest uruchamiany normalnie.

## <a name="remarks"></a>Uwagi

Wszystkie ciągi po parametrze *executablefile* są przekazane do tego pliku jako argumenty.

## <a name="example"></a>Przykład

Poniższy przykład otwiera plik `MyApplication.exe` do debugowania.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
