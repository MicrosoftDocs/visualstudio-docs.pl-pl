---
title: Czas przetwarzania interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecf2c33b2af2e57c964e145a334f6dd0d7161a92
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738436"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z zablokowania prób są klasyfikowane jako przetwarzania interfejsu użytkownika. Oznacza to, że wątek jest przekazywanie komunikatów Windows lub wykonywania innych zadań interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który zlicza Concurrency Visualizer jako przetwarzania interfejsu użytkownika. Interfejsy API, takie jak `GetMessage()` i `MsgWaitForMultipleObjects()` należą do tej grupy.  
  
 Jeśli zostanie zidentyfikowana żadnych wstępnie zdefiniowanych interfejsów API do blokowania, zapoznaj się z stosów wywołań i raportów profilu, aby ustalić podstawowe przyczyny opóźnienia.  
  
 Kategoria przetwarzania interfejsu użytkownika jest istotne dla zrozumienia szybkość reakcji aplikacji GUI i jest pożądane w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji realizuje 100% czasu przetwarzania interfejsu użytkownika, jest prawdopodobnie bardzo elastyczny. Jednak jeśli wątek interfejsu użytkownika zużywa znaczną ilość czasu w innych kategoriach, poszukaj głównych przyczyn i należy rozważyć opcje redukcji kategorii bez interfejsu użytkownika dla tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)



