---
title: Widok podsumowania — Widok rywalizacji o zasoby | Microsoft Docs
description: Widok podsumowania zawiera informacje o zdarzeniach w aplikacji, w których wątek lub proces został wstrzymany podczas oczekiwania na dostęp do zasobu.
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
ms.openlocfilehash: 40d922d8728e53d0098ad67c8b8140f9045c32b0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722649"
---
# <a name="summary-view---resource-contention-view"></a>Widok podsumowania — widok rywalizacji o zasoby
Widok podsumowania zawiera informacje o zdarzeniach w aplikacji, w których wątek lub proces został wstrzymany podczas oczekiwania na dostęp do zasobu.

 Aby uzyskać więcej informacji, w tym opis linków powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Wykres osi czasu
 Wykres osi czasu w widoku Podsumowanie przedstawia liczbę zdarzeń rywalizacji profilowanej aplikacji w czasie, w którym wystąpiło profilowanie. Możesz użyć wykresu osi czasu do filtrowania widoku do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [How to: Filter viewss Reports from a Summary oś czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="most-contended-resources"></a>Zasoby z największą rywalizacją
 **Zasoby z największą** rywalizacją zawierają listę zasobów w aplikacji, które spowodowały najwięcej zdarzeń związanych ze spisem. Możesz kliknąć nazwę zasobu, aby wyświetlić widok rywalizacji. Widok rywalizacji zawiera szczegółową oś czasu rywalizacji o zasoby według wątku.

 **Zasoby z największą** ilością zasobów obejmują następujące dane dla każdego zasobu.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa zasobu.|
|**Rywalizacji**|Wartość procentowa wszystkich zdarzeń rywalizacji w danych profilowania, które były rywalizacjami za ten zasób.|

## <a name="most-contended-thread"></a>Wątek z największą rywalizacją
 **Wątki z największą** liczbą zdarzeń w programie wyświetlają wątki w aplikacji, które miały największą liczbę zdarzenia rywalizacji. Można kliknąć nazwę wątku, aby wyświetlić widok rywalizacji, który zapewnia szczegółową oś czasu rywalizacji o zasoby przez wątek.

 **Wątki z największą** ilością ofert obejmują następujące dane dla każdego wątku.

|Kolumna|Opis|
|------------|-----------------|
|**ID (Identyfikator)**|Identyfikator wątku.|
|**Nazwa**|Nazwa procesu, który jest właścicielem wątku.|
|**Rywalizacji**|Wartość procentowa wszystkich zdarzeń rywalizacji w danych profilowania, które były rywalizacjami za ten zasób.|
