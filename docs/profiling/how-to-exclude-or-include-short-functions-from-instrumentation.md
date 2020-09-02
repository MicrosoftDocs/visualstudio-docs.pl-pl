---
title: Wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 4aaae07987f1d3364b064465aa6edff9a4748301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329790"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Instrukcje: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji
Domyślnie narzędzia profilowania wykluczają *małe funkcje* z Instrumentacji. Małe funkcje są krótkimi funkcjami, które nie wykonują żadnych wywołań funkcji. Wyłączenie tych małych funkcji zapewnia mniejszą ilość przyrzutów instrumentacji, dlatego ulepszona szybkość Instrumentacji. Wyłączenie małych funkcji zmniejsza również plik danych profilowania wydajności (.* rozmiar VSP*) i czas wymagany do analizy. W przypadku wykluczenia małych funkcji czas spędzony w przypadku małych funkcji liczy się w odniesieniu do wyłącznego i włącznie czasu ich funkcji nadrzędnych. Małe funkcje mogą być wykluczone lub zawarte w instrumentacji, zgodnie z opisem w poniższej procedurze.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Aby wykluczyć lub dołączyć krótkie funkcje z Instrumentacji

1. W **Eksplorator wydajności**wybierz pozycję **sesja wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.

     Wyświetli się okno dialogowe **Strony właściwości**.

2. Na **stronie właściwości**kliknij właściwości **Instrumentacji** .

3. Aby wykluczyć funkcje krótkie z instrumentacji, wybierz opcję **Wyklucz funkcje krótkie z Instrumentacji**. Jest to ustawienie domyślne.

     -lub-

     Aby uwzględnić krótkie funkcje w instrumentacji, wyczyść pole wyboru **Wyklucz funkcje krótkie z Instrumentacji**.

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
