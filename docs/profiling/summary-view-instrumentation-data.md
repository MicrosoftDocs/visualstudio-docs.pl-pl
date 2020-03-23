---
title: Widok podsumowania - Dane oprzyrządowania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2f52f80cad4ce7678a832a7b76a75d8f2fd4460e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778222"
---
# <a name="summary-view---instrumentation-data"></a>Widok podsumowania - dane oprzyrządowania
W widoku Podsumowanie są wyświetlane informacje o najbardziej kosztownych z wydajnością funkcjach w przebiegu profilowania. Aby uzyskać więcej informacji, w tym opis łączy powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Wykres osi czasu
 Wykres osi czasu w widoku Podsumowanie pokazuje wykorzystanie procesora (CPU) przez profilowane aplikacji w czasie, który wystąpił profilowania. Za pomocą wykresu osi czasu można filtrować widok do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [Jak: Filtrowanie widoków raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Gorąca ścieżka
 **Ścieżka gorąca** wyświetla ścieżkę wykonywania, która pochłonęła najwięcej czasu. Można kliknąć funkcję, aby wyświetlić widok Szczegóły funkcji dla tej funkcji. Aby wyświetlić inne widoki funkcji, kliknij tę funkcję, a następnie kliknij widok z listy.

 **Ścieżka gorąca** zawiera następujące dane dla każdej funkcji:

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**Czas włącznie, który upłynął %**|Procent całego czasu w danych profilowania, które funkcja spędził wykonywania kodu w treści funkcji i funkcji, które wywoływała.|
|**Czas wyłączny, który upłynął %**|Procent całego czasu w danych profilowania, które funkcja spędził wykonywania kodu w treści funkcji. Czas spędzony w funkcjach, które wywoływana funkcja nie jest uwzględniony.|

## <a name="functions-with-most-individual-work"></a>Funkcje z większością pracy indywidualnej
 Lista funkcji, które zużywały najwięcej czasu wykonywania kodu w treści funkcji, a nie w funkcjach, które wywoływała.

 **Funkcje z większością pracy indywidualnej** obejmują następujące dane dla każdej funkcji:

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**Czas wyłączny %**|Procent całego czasu w danych profilowania, które funkcja spędził wykonywania kodu w treści funkcji. Czas spędzony w funkcjach, które wywoływana funkcja nie jest uwzględniony.|

## <a name="see-also"></a>Zobacz też
- [Widok podsumowania — dane próbkowania](../profiling/summary-view-sampling-data.md)
- [Widok podsumowania — dane pamięci .NET](../profiling/summary-view-dotnet-memory-data.md)
