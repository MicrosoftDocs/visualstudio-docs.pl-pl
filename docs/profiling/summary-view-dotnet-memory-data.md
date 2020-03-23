---
title: Widok podsumowania — dane pamięci .NET | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a67902af99eaee6c75f92f86c2481dfc2afd744e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771559"
---
# <a name="summary-view---net-memory-data"></a>Widok podsumowania — dane pamięci .NET
W widoku Podsumowanie są wyświetlane informacje o funkcjach i typach platformy .NET, które przydzieliły najwięcej pamięci, oraz o typach, które zostały utworzone najczęściej w przebiegu profilowania. Aby uzyskać więcej informacji, w tym opis łączy powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).

## <a name="timeline-graph"></a>Wykres osi czasu
 Wykres osi czasu w widoku Podsumowanie pokazuje wykorzystanie procesora (CPU) przez profilowane aplikacji w czasie, który wystąpił profilowania. Za pomocą wykresu osi czasu można filtrować widok do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [Jak: Filtrowanie widoków raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="functions-allocating-most-memory"></a>Funkcje przydzielające większość pamięci
 Wyświetla listę funkcji, które przydzielono największą liczbę bajtów pamięci w przebiegu profilowania.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**Bajty %**|Procent wszystkich przydzielonych bajtów w przebiegu profilowania, które zostały przydzielone przez tę funkcję lub przez funkcję podrzędną, która została wywołana przez tę funkcję.|

## <a name="types-with-most-memory-allocated"></a>Typy z największą liczną pamięcią
 Wyświetla listę typów, dla których największa liczba bajtów pamięci zostały przydzielone w przebiegu profilowania.

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa typu.|
|**Bajty %**|Procent wszystkich przydzielonych bajtów w przebiegu profilowania, które zostały przydzielone dla tego typu.|

## <a name="types-with-most-instances"></a>Typy z większością wystąpień
 Wyświetla listę typów, które zostały utworzone najwięcej razy podczas wykonywania profilowania. Hda

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa typu.|
|**Wystąpienia %**|Procent całkowitej liczby obiektów of.NET, które zostały utworzone w przebiegu profilowania, które były wystąpieniami tego typu.|

## <a name="see-also"></a>Zobacz też
- [Widok podsumowania — dane próbkowania](../profiling/summary-view-sampling-data.md)
- [Widok podsumowania - dane oprzyrządowania](../profiling/summary-view-instrumentation-data.md)
