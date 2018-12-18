---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1badcaba6f6461f6a2c6b73580d8d12c50481c2b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948780"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Otwiera określony plik wykonywalny do zdebugowania.

## <a name="syntax"></a>Składnia

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argumenty
 `ExecutableFile`

 Wymagana. Ścieżka i nazwa pliku .exe.

 Jeśli plik .exe nie zostanie znaleziony lub nie istnieje, jest wyświetlana nie ostrzeżenia lub błędu i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uruchamia się normalnie.

## <a name="remarks"></a>Uwagi
 Wszystkie ciągi zgodnie z `ExecutableFile` parametru są przekazywane do tego pliku jako argumenty.

## <a name="example"></a>Przykład
 W poniższym przykładzie otwierany plik `MyApplication.exe` do debugowania.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)