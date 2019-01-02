---
title: -Run (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f46afb431b998b5fd937d24178a602f6aea81eb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921747"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
Kompiluje i uruchamia określony projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty
 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 `ProjectName`

 Wymagana. Pełna ścieżka i nazwa pliku projektu.

## <a name="remarks"></a>Uwagi
 Kompiluje i uruchamia określony projekt lub rozwiązanie, zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik uruchamia zintegrowanego środowiska programistycznego (IDE) i pozostawia aktywne po projekt lub rozwiązanie zakończy działanie.

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie uruchamia rozwiązanie `MySolution` przy użyciu konfiguracji aktywnego wdrożenia.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)