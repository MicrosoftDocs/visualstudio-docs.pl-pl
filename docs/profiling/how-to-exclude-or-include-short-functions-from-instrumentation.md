---
title: Wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de6d6325b1e518146768798c773754c091861aa8
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74775917"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji
Domyślnie narzędzia profilowania wykluczają *małe funkcje* z Instrumentacji. Małe funkcje są krótkimi funkcjami, które nie wykonują żadnych wywołań funkcji. Wyłączenie tych małych funkcji zapewnia mniejszą ilość przyrzutów instrumentacji, dlatego ulepszona szybkość Instrumentacji. Wyłączenie małych funkcji zmniejsza również plik danych profilowania wydajności (. *rozmiar VSP*) i czas wymagany do analizy. W przypadku wykluczenia małych funkcji czas spędzony w przypadku małych funkcji liczy się w odniesieniu do wyłącznego i włącznie czasu ich funkcji nadrzędnych. Małe funkcje mogą być wykluczone lub zawarte w instrumentacji, zgodnie z opisem w poniższej procedurze.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Aby wykluczyć lub dołączyć krótkie funkcje z Instrumentacji

1. W **Eksplorator wydajności**wybierz pozycję **sesja wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.

     Zostanie wyświetlone okno dialogowe **strony właściwości** .

2. Na **stronie właściwości**kliknij właściwości **Instrumentacji** .

3. Aby wykluczyć funkcje krótkie z instrumentacji, wybierz opcję **Wyklucz funkcje krótkie z Instrumentacji**. To jest ustawienie domyślne.

     lub

     Aby uwzględnić krótkie funkcje w instrumentacji, wyczyść pole wyboru **Wyklucz funkcje krótkie z Instrumentacji**.

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
