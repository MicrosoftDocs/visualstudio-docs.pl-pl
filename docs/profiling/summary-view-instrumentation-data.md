---
title: Widok podsumowania — dane Instrumentacji | Microsoft Docs
description: Dowiedz się, w jaki sposób widok podsumowania Wyświetla informacje o najbardziej wydajnych funkcjach i opisie łączy powiadomień oraz list raportów.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a9431f6f7a2adfee06f4fa007eafc109d3c32d0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722662"
---
# <a name="summary-view---instrumentation-data"></a>Widok podsumowania — dane Instrumentacji
Widok podsumowania zawiera informacje o najbardziej wydajnych funkcjach w przebiegu profilowania. Aby uzyskać więcej informacji, w tym opis linków powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Wykres osi czasu
 Wykres osi czasu w widoku Podsumowanie przedstawia wykorzystanie procesora (CPU) przez profilowaną aplikację w czasie, w którym nastąpiło profilowanie. Możesz użyć wykresu osi czasu do filtrowania widoku do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [How to: Filter viewss Reports from a Summary oś czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Ścieżka gorąca
 **Ścieżka gorąca** wyświetla ścieżkę wykonywania, która była używana przez najwięcej czasu. Możesz kliknąć funkcję, aby wyświetlić widok szczegółów funkcji dla funkcji. Aby wyświetlić inne widoki dla funkcji, kliknij ją prawym przyciskiem myszy, a następnie kliknij Widok z listy.

 **Ścieżka gorąca** zawiera następujące dane dla każdej funkcji:

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**% Czasu włącznego, który upłynął**|Wartość procentowa całego czasu w danych profilowania, jaką funkcja poświęca na wykonywanie kodu w jego treści funkcji i w funkcjach, które wywołuje.|
|**% Czasu wyłącznego, który upłynął**|Wartość procentowa całego czasu w danych profilowania, jaką funkcja poświęca na wykonywanie kodu w jego treści funkcji. Czas spędzony w funkcjach wywoływanych przez funkcję nie jest uwzględniony.|

## <a name="functions-with-most-individual-work"></a>Funkcje z największą liczbą zadań indywidualnych
 Lista funkcji, które zużywają najwięcej czasu wykonywania kodu w treści funkcji, a nie w funkcjach, które wywołuje.

 Funkcja **z największą** ilością pracy obejmuje następujące dane dla każdej funkcji:

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**% Czasu wyłącznego**|Wartość procentowa całego czasu w danych profilowania, jaką funkcja poświęca na wykonywanie kodu w jego treści funkcji. Czas spędzony w funkcjach wywoływanych przez funkcję nie jest uwzględniony.|

## <a name="see-also"></a>Zobacz także
- [Widok podsumowania — dane próbkowania](../profiling/summary-view-sampling-data.md)
- [Widok podsumowania — dane pamięci platformy .NET](../profiling/summary-view-dotnet-memory-data.md)
