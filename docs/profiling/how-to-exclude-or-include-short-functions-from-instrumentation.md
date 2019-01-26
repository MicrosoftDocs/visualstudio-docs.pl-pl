---
title: 'Instrukcje: Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46edc453e16fec43028876d7d590c88651229994
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965526"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Instrukcje: Wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji
Domyślnie, narzędzia profilowania wykluczyć *małe funkcje* z Instrumentacji. Małe funkcje są krótkich funkcji, których nie należy wprowadzać wszelkie wywołania funkcji. Te małe funkcje z wyjątkiem zapewnia mniejsze koszty Instrumentacji i w związku z tym zwiększona szybkość instrumentacji. Wyłączenie małych funkcji zmniejsza wydajność plik danych profilowania (. *Vsp*) rozmiar i czas, który jest wymagany do analizy. Jeśli małe funkcje zostaną wykluczone, czasu spędzonego w małych funkcji zmniejsza wyłącznych i całkowity czas ich funkcji nadrzędnej. Małe funkcje mogą być wyłączone lub objęte instrumentacji, zgodnie z opisem w poniższej procedurze.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji  
  
1.  W **Eksplorator wydajności**, wybierz opcję **sesji wydajności** a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
     **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
2.  W **stron właściwości**, kliknij przycisk **Instrumentacji** właściwości.  
  
3.  Aby wykluczyć krótkich funkcji z Instrumentacji, należy wybrać **wykluczenie krótkich funkcji z Instrumentacji**. To jest ustawienie domyślne.  
  
     —lub—  
  
     Aby dołączyć krótkich funkcji instrumentacji, należy wyczyścić **wykluczenie krótkich funkcji z Instrumentacji**.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz także  
 [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)