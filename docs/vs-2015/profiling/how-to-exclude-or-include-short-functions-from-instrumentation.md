---
title: 'Instrukcje: Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d37984b6535e353053ba6ee71090797e4ce119d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801664"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Instrukcje: Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie, narzędzia profilowania wykluczyć *małe funkcje* z Instrumentacji. Małe funkcje są krótkich funkcji, których nie należy wprowadzać wszelkie wywołania funkcji. Te małe funkcje z wyjątkiem zapewnia mniejsze koszty Instrumentacji i w związku z tym zwiększona szybkość instrumentacji. Wyłączenie małych funkcji zmniejsza rozmiar pliku (Vsp) dane profilowania wydajności i czasu, który jest wymagany do analizy. Jeśli małe funkcje zostaną wykluczone, czasu spędzonego w małych funkcji zmniejsza wyłącznych i całkowity czas ich funkcji nadrzędnej. Małe funkcje mogą być wyłączone lub objęte instrumentacji, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji  
  
1.  W **Eksplorator wydajności**, wybierz opcję **sesji wydajności** a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
     **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  W **stron właściwości**, kliknij przycisk **Instrumentacji** właściwości.  
  
3.  Aby wykluczyć krótkich funkcji z Instrumentacji, należy wybrać **wykluczenie krótkich funkcji z Instrumentacji**. To jest ustawienie domyślne.  
  
     —lub—  
  
     Aby dołączyć krótkich funkcji instrumentacji, należy wyczyścić **wykluczenie krótkich funkcji z Instrumentacji**.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
