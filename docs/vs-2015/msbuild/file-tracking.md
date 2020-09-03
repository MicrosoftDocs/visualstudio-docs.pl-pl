---
title: Śledzenie plików | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156459"
---
# <a name="file-tracking"></a>Śledzenie plików
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dzienniki śledzenia plików są wywołaniami systemu plików Windows dla procesu i jego procesów podrzędnych. Wywołując funkcje wymienione poniżej, programy kontrolują, kiedy należy włączyć i wyłączyć rejestrowanie i określić plik dziennika, który ma być używany.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Zatrzymaj śledzenie bieżącego kontekstu.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Wznów śledzenie po wywołaniu [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Ustaw liczbę wątków do użycia na potrzeby śledzenia.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Rozpocznij nowy kontekst śledzenia.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Rozpocznij nowy kontekst śledzenia z określonym katalogiem głównym.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Zasoby końcowe śledzenia i wydania są używane.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Tymczasowe Wstrzymywanie śledzenia.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Zapisz dzienniki śledzenia dla wszystkich kontekstów.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Zapisz dziennik śledzenia dla bieżącego kontekstu.
