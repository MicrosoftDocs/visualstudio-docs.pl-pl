---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fa715c97310edc447610b0c0ae61226ab5334f9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955123"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Kompiluje i uruchamia określony projekt lub rozwiązanie, a następnie zamyka zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty
 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 `ProjectName`

 Wymagana. Pełna ścieżka i nazwa pliku projektu.

## <a name="remarks"></a>Uwagi
 Kompiluje i uruchamia określony projekt lub rozwiązanie, zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik minimalizuje IDE, podczas projektu lub rozwiązania jest uruchomiona i zamknięcie IDE po projektu lub rozwiązania zakończy działanie.

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie uruchamia rozwiązanie `MySolution` w trybie zminimalizowanym IDE przy użyciu konfiguracji aktywnego wdrożenia, a następnie zamyka IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)