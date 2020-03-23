---
title: Widok podsumowania — widok rywalizacji o zasoby | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 185345c13134f4d2ec6086e6a66183e044c577ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771451"
---
# <a name="summary-view---resource-contention-view"></a>Widok podsumowania — widok rywalizacji o zasoby
W widoku Podsumowanie są wyświetlane informacje o zdarzeniach w aplikacji, w których wątek lub proces został zawieszony podczas oczekiwania na dostęp do zasobu.

 Aby uzyskać więcej informacji, w tym opis łączy powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Wykres osi czasu
 Wykres osi czasu w widoku Podsumowanie pokazuje liczbę zdarzeń rywalizacji profilowanych aplikacji w czasie, w którego wystąpił profilowanie. Za pomocą wykresu osi czasu można filtrować widok do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [Jak: Filtrowanie widoków raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="most-contended-resources"></a>Większość twierdzonych zasobów
 **Większość twierdził zasobów** wyświetla zasoby w aplikacji, która spowodowała najwięcej zdarzeń rywalizacji. Można kliknąć nazwę zasobu, aby wyświetlić widok Rywalizacje. Widok Rywalizacje zawiera szczegółową oś czasu rywalizacji zasobów według wątku.

 **Większość twierdził zasobów** zawiera następujące dane dla każdego zasobu.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa zasobu.|
|**Rywalizacja %**|Procent wszystkich zdarzeń rywalizacji w danych profilowania, które były rywalizacji za ten zasób.|

## <a name="most-contended-thread"></a>Najbardziej twierdził wątku
 **Większość Twierdził wątki** wyświetla wątki w aplikacji, która miała największą liczbę zdarzeń rywalizacji. Można kliknąć nazwę wątku, aby wyświetlić widok Rywalizacje, który zawiera szczegółową oś czasu rywalizacji zasobów przez wątek.

 **Większość wątków contended** zawiera następujące dane dla każdego wątku.

|Kolumna|Opis|
|------------|-----------------|
|**ID**|Identyfikator wątku.|
|**Nazwa**|Nazwa procesu, który jest właścicielem wątku.|
|**Rywalizacja %**|Procent wszystkich zdarzeń rywalizacji w danych profilowania, które były rywalizacji za ten zasób.|
