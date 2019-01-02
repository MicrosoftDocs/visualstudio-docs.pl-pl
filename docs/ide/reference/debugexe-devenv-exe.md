---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 99f256b47125f4e07ca5dc148c4351871389a94b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889413"
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