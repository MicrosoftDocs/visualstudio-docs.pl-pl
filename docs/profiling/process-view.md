---
title: Widok procesu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: da3097c276557238e6f5b521f6f7d3231434cd10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772179"
---
# <a name="process-view"></a>Widok procesu
W widoku Proces są wyświetlane dane profilowania dla procesów i wątków, które zostały wykonane podczas przebiegu profilowania.

 Procesy są wyświetlane według nazwy. Wątki są wyświetlane jako węzły podrzędne procesu, który je utworzył. Wątki są nazwane przez funkcję, która rozpoczęła wątek lub przez etykietę **[ntdll.dll],** jeśli nie są dostępne żadne symbole.

 Aby dodać lub usunąć kolumny, kliknij prawym przyciskiem myszy widok, a następnie wybierz polecenie **Dodaj/Usuń kolumny**. Ponadto można sortować dane, klikając nazwę kolumny. Aby uzyskać więcej informacji, zobacz [Jak: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).

 Kolumny process widoku są takie same dla danych, które są generowane przy użyciu metody próbkowania i instrumentacji i danych, które zawiera dane pamięci .NET. W poniższej tabeli opisano wartości kolumn.

|Kolumna|Opis|
|------------|-----------------|
|**Unikatowy identyfikator**|Identyfikator generowany przez profiler, który jest unikatowy dla procesu lub wątku.|
|**ID**|Wygenerowany przez system identyfikator procesu lub wątku.|
|**Nazwa**|Nazwa procesu lub wątku.|
|**Godzina rozpoczęcia**|Liczba milisekund lub cykli procesora od początku profilowania do początku procesu lub wątku.|
|**Godzina zakończenia**|Liczba milisekund lub cykli procesora od początku profilowania do końca procesu lub wątku.|

## <a name="see-also"></a>Zobacz też
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
