---
title: Śledzenie plików | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8d999d65b207f72542b732842f6eb984df40764
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156459"
---
# <a name="file-tracking"></a>Śledzenie plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Śledzenie pliku rejestruje wywołania do Windows systemu plików dla procesu i jego procesów podrzędnych. Przez wywołanie funkcji wymienionych poniżej, programy kontrolują kiedy należy włączyć rejestrowanie i wyłączyć i określ plik dziennika do użycia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Zatrzymaj śledzenie bieżącego kontekstu.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Wznów śledzenie po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Ustaw liczbę wątków używanych na potrzeby śledzenia.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Rozpocznij nowy kontekst śledzenia.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Rozpocznij nowy kontekst śledzenia z określonym katalogiem głównym.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Zakończenia śledzenia i zwolnienia zasobów używane.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Czasowo zawieszają śledzenie.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Zapisać dziennik śledzenia dla wszystkich kontekstów.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Zapisać dziennik śledzenia dla bieżącego kontekstu.
