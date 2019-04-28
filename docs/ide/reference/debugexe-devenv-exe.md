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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05266a6f1b5ee0be22e2edc8df1c03b720844f4f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968083"
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