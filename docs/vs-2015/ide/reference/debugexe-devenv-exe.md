---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f472add6b821693d1d48397e878db19e707e2868
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660804"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otwiera określony plik wykonywalny do debugowania.

## <a name="syntax"></a>Składnia

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argumenty
 `ExecutableFile` Wymagane. Ścieżka i nazwa pliku. exe.

 Jeśli plik exe nie zostanie znaleziony lub nie istnieje, ostrzeżenie lub błąd nie jest wyświetlany i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uruchamiany normalnie.

## <a name="remarks"></a>Uwagi
 Wszystkie ciągi po `ExecutableFile` parametrze są przekazane do tego pliku jako argumenty.

## <a name="example"></a>Przykład
 Poniższy przykład otwiera plik `MyApplication.exe` do debugowania.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Zobacz też
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
