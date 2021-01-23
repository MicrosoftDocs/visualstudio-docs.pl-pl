---
title: Widok procesu | Microsoft Docs
description: Dowiedz się, w jaki sposób widok procesu wyświetla dane profilowania dla procesów i wątków, które zostały wykonane podczas przebiegu profilowania.
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
ms.openlocfilehash: bd4dfd4657d6ca2f42c234f576e362ffacb9e693
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719469"
---
# <a name="process-view"></a>Widok procesu
Widok procesu przedstawia dane profilowania procesów i wątków, które zostały wykonane podczas przebiegu profilowania.

 Procesy są wyświetlane według nazwy. Wątki są wyświetlane jako węzły podrzędne procesu, który je utworzył. Wątki są nazwane przez funkcję, która uruchomiła wątek lub przez etykietę **[ntdll.dll]** , jeśli nie są dostępne żadne symbole.

 Aby dodać lub usunąć kolumny, kliknij prawym przyciskiem myszy w widoku, a następnie wybierz polecenie **Dodaj/Usuń kolumny**. Ponadto można sortować dane, klikając nazwę kolumny. Aby uzyskać więcej informacji, zobacz [How to: dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md).

 Kolumny widoku procesu są takie same dla danych, które są generowane przy użyciu metody próbkowania i Instrumentacji oraz dla danych, które zawierają dane pamięci platformy .NET. W poniższej tabeli opisano wartości kolumn.

|Kolumna|Opis|
|------------|-----------------|
|**Unikatowy identyfikator**|Wygenerowany przez profiler identyfikator, który jest unikatowy dla procesu lub wątku.|
|**ID (Identyfikator)**|Wygenerowany przez system identyfikator procesu lub wątku.|
|**Nazwa**|Nazwa procesu lub wątku.|
|**Godzina rozpoczęcia**|Liczba milisekund lub cykli procesora od początku profilowania do początku procesu lub wątku.|
|**Czas zakończenia**|Liczba milisekund lub cykli procesora od początku profilowania do końca procesu lub wątku.|

## <a name="see-also"></a>Zobacz także
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
- [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
- [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)
