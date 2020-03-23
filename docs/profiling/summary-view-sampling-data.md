---
title: Widok podsumowania - Dane próbkowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 649d0e9e5b32c124cfa962f45e4d128e4a32210f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778209"
---
# <a name="summary-view---sampling-data"></a>Widok podsumowania — dane próbkowania
W widoku Podsumowanie są wyświetlane informacje o najbardziej kosztownych z wydajnością funkcjach w przebiegu profilowania. Aby uzyskać więcej informacji, w tym opis łączy powiadomień i list raportów, zobacz [Widok podsumowania](../profiling/summary-view.md).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="timeline-graph"></a>Wykres osi czasu
 Wykres osi czasu w widoku Podsumowanie pokazuje procent wykorzystania procesora (CPU) profilowane aplikacji w czasie, który wystąpił profilowanie. Za pomocą wykresu osi czasu można filtrować widok do wybranego przedziału czasu. Aby uzyskać więcej informacji, zobacz [Jak: Filtrowanie widoków raportu z osi czasu podsumowania](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

## <a name="hot-path"></a>Gorąca ścieżka
 **Ścieżka gorąca** wyświetla ścieżkę wykonywania, w której większość próbek zostały zebrane. Można kliknąć funkcję, aby wyświetlić widok Szczegóły funkcji dla tej funkcji. Aby wyświetlić inne widoki funkcji, kliknij tę funkcję prawym przyciskiem myszy, a następnie kliknij widok z listy.

 **Ścieżka gorąca** zawiera następujące dane dla każdej funkcji:

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**Próbki włącznie %**|Procent wszystkich próbek, które wystąpiły podczas wykonywania tej funkcji lub funkcji wywoływanej przez tę funkcję.|
|**Próbki na wyłączność %**|Procent wszystkich próbek, które wystąpiły podczas wykonywania kodu przez funkcję w treści funkcji. Próbki zebrane w funkcjach wywoływanych przez tę funkcję nie są uwzględniane.|

## <a name="functions-doing-most-individual-work"></a>Funkcje wykonujące większość pracy indywidualnej
 Na liście **Funkcje wykonujące większość pracy indywidualnej** są wyświetlane funkcje, które mają największą liczbę próbek wyłącznych w przebiegu profilowania. Próbka wyłączności jest przypisana do funkcji, jeśli funkcja wykonuje swój własny kod podczas pobierania próbki. Próbka wyłączności nie jest przypisana do funkcji, jeśli funkcja wywołuje inną funkcję podczas pobierania próbki. Duża liczba próbek wyłącznych wskazuje, że znaczny czas spędzono w samej funkcji.

 Można kliknąć funkcję, aby wyświetlić widok Szczegóły funkcji dla tej funkcji. Aby wyświetlić inne widoki funkcji, kliknij tę funkcję, a następnie kliknij widok z listy.

 **Funkcje wykonujące większość pracy indywidualnej** obejmują następujące dane dla każdej funkcji:

|Kolumna|Opis|
|------------|-----------------|
|**Nazwa**|Nazwa funkcji.|
|**Próbki na wyłączność %**|Procent wszystkich próbek w przebiegu profilowania, które zostały zebrane podczas wykonywania kodu przez funkcję w treści funkcji. Wartość procentowa nie obejmuje próbek, które zostały zebrane podczas wykonywania funkcji, które ta funkcja była wykonywana.|

## <a name="see-also"></a>Zobacz też
- [Widok podsumowania — dane pamięci platformy .NET](../profiling/summary-view-dotnet-memory-data.md)
- [Widok podsumowania - dane instrumentacji](../profiling/summary-view-instrumentation-data.md)
