---
title: -DebugExe (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia DebugExe devenv otworzyć określony plik wykonywalny do debugowania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5cdf770446b78b1a1bb4b55d61f4c3e9f50c4035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894611"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Otwiera określony plik wykonywalny do debugowania.

## <a name="syntax"></a>Składnia

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumenty

- *ExecutableFile*

  Wymagane. Ścieżka i nazwa pliku `.exe` . Jeśli `.exe` plik nie zostanie znaleziony lub nie istnieje, wyświetlane jest ostrzeżenie lub błąd, a program Visual Studio jest uruchamiany normalnie.

## <a name="remarks"></a>Uwagi

Wszystkie ciągi po parametrze *executablefile* są przekazane do tego pliku jako argumenty.

## <a name="example"></a>Przykład

Poniższy przykład otwiera plik `MyApplication.exe` do debugowania.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
