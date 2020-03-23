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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775917"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Jak: Wykluczyć lub uwzględnić krótkie funkcje z oprzyrządowania
Domyślnie narzędzia profilowania wykluczają *małe funkcje* z instrumentacji. Małe funkcje to krótkie funkcje, które nie wywołują żadnych wywołań funkcji. Wyłączenie tych małych funkcji zapewnia mniejsze obciążenie oprzyrządowania, a tym samym lepszą szybkość oprzyrządowania. Wykluczenie małych funkcji zmniejsza również wydajność profilowania pliku danych (.* vsp*) i czas wymagany do analizy. Jeśli małe funkcje są wykluczone, czas spędzony w małych funkcji liczy się z wyłącznym i włącznie czasu ich funkcji nadrzędnych. Małe funkcje można wykluczyć lub uwzględnić w oprzyrządowanie, jak opisano w poniższej procedurze.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Aby wykluczyć lub uwzględnić krótkie funkcje z oprzyrządowania

1. W **Eksploratorze wydajności**wybierz pozycję **Sesja wydajności,** a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Właściwości**.

     Wyświetli się okno dialogowe **Strony właściwości**.

2. Na **stronach właściwości**kliknij właściwości **Instrumentacja.**

3. Aby wykluczyć krótkie funkcje z oprzyrządowania, wybierz **opcję Wyklucz krótkie funkcje z instrumentacji**. Jest to ustawienie domyślne.

     — lub —

     Aby uwzględnić krótkie funkcje w oprzyrządowanie, jasne **Wyklucz krótkie funkcje z instrumentacji**.

4. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)
- [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
