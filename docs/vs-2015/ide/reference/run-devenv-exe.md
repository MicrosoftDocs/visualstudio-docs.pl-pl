---
title: — Uruchamianie (devenv.exe) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 68e5dcc5ff2e78fe87bbaad639c93f5532ea74fe
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065678"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kompiluje i uruchamia określony projekt lub rozwiązanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
devenv {/run|/r} {SolutionName|ProjectName}  
```  
  
## <a name="arguments"></a>Argumenty  
 `SolutionName`  
 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.  
  
 `ProjectName`  
 Wymagana. Pełna ścieżka i nazwa pliku projektu.  
  
## <a name="remarks"></a>Uwagi  
 Kompiluje i uruchamia określony projekt lub rozwiązanie, zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik uruchamia zintegrowanego środowiska programistycznego (IDE) i pozostawia aktywne po projekt lub rozwiązanie zakończy działanie.  
  
- Należy ująć ciągi zawierające spacje w podwójny cudzysłów.  
  
- Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie uruchamia rozwiązanie `MySolution` przy użyciu konfiguracji aktywnego wdrożenia.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/ Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)   
 [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
