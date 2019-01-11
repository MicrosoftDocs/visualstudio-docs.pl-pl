---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0633c3e94a870117e1ae171903581da448b09ace
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227216"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Otwiera określony plik wykonywalny do zdebugowania.

## <a name="syntax"></a>Składnia

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumenty

- *ExecutableFile*

  Wymagana. Ścieżka i nazwa pliku z `.exe` pliku. Jeśli `.exe` pliku nie zostanie odnaleziony lub nie istnieje, jest wyświetlane żadne ostrzeżenia ani błędu i programu Visual Studio uruchamia się normalnie.

## <a name="remarks"></a>Uwagi

Wszystkie ciągi zgodnie z *ExecutableFile* parametru są przekazywane do tego pliku jako argumenty.

## <a name="example"></a>Przykład

W poniższym przykładzie otwierany plik `MyApplication.exe` do debugowania.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)