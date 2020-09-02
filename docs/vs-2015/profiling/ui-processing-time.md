---
title: Czas przetwarzania interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bbed9d8c4725b6bd497377d4a9dee22f2f8573d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145485"
---
# <a name="ui-processing-time"></a>Czas przetwarzania interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Te segmenty na osi czasu są skojarzone z czasem blokowania, które są klasyfikowane jako przetwarzanie interfejsu użytkownika. Oznacza to, że wątek jest pompą komunikatów systemu Windows lub wykonywania innych czynności interfejsu użytkownika. W tym czasie wątek został zablokowany w interfejsie API, który jest obliczany przez Wizualizator współbieżności jako przetwarzanie interfejsu użytkownika. Interfejsy API, takie jak `GetMessage()` i `MsgWaitForMultipleObjects()` mieszczą się w tej grupie.  
  
 Jeśli nie określono wstępnie zdefiniowanego interfejsu API blokowania, przejrzyj stosy wywołań i raporty profilu, aby określić podstawowe przyczyny opóźnienia.  
  
 Kategoria przetwarzania interfejsu użytkownika jest ważna dla poznania czasu reakcji aplikacji GUI i jest pożądana w aplikacjach, które są zależne od czasu odpowiedzi interfejsu użytkownika. Na przykład jeśli wątek interfejsu użytkownika w aplikacji uzyskuje 100% czasu w czasie przetwarzania interfejsu użytkownika, prawdopodobnie bardzo odpowiada. Jeśli jednak wątek interfejsu użytkownika spędza znaczący czas w innych kategoriach, należy poszukać głównych przyczyn i rozważyć Opcje zmniejszenia kategorii innych niż interfejs użytkownika w tym wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Widok wątków](../profiling/threads-view-parallel-performance.md)
