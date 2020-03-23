---
title: Tworzenie podstawowych raportów profilowania z wiersza polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd9748d88a9398792274c386a42bdaa3ce48ba70
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777793"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Tworzenie podstawowych raportów profilowania z wiersza polecenia
W tym artykule opisano podstawowe polecenia VSPerfReport, które generują wartość oddzieloną przecinkami (.* csv)* raporty z . *vsp* lub . *vsps* profilowania pliku danych. Aby uzyskać opis wszystkich opcji raportu, zobacz [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Polecenia raportu
 Użyj jednego z następujących poleceń, aby utworzyć raport dla określonego pliku danych profilowania.

 **VSPerfReport** `VSPFile` **/Summary:Wszystkie** generuje wszystkie raporty dostępne dla . *vsp* lub . *vsps.*

 **VSPerfReport** `VSPFile` **/Podsumowanie:**`ReportType``ReportType`[, ...] Generuje określone typy raportów.

 **VSPerfReport** `VSPFile` **/CallTrace** generuje raport, który wyświetla listę każdego zdarzenia zbierania danych. Tylko oprzyrządowanie.

## <a name="summary-report-type-parameters"></a>Parametry typu raportu podsumowującego
 W poniższej tabeli opisano raporty generowane przez określoną opcję typu raportu. Kolumny raportu zależą od metody profilowania, która została użyta do zbierania danych.

|Parametr podsumowania|Opis raportu|Odwołanie do raportu|
|-----------------------|------------------------|----------------------|
|**CallerCallee (CallerCallee)**|Reprezentuje relacje nadrzędny/podrzędny między funkcjami.|-   [Dane dotyczące próbkowania](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dane oprzyrządowania](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/caller-callee-view-contention-data.md)|
|**Funkcja**|Wyświetla listę danych profilowania według funkcji.|-   [Dane dotyczące próbkowania](../profiling/functions-view-sampling-data.md)<br />-   [Dane oprzyrządowania](../profiling/functions-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/functions-view-contention-data.md)|
|**CallTree (Drzewo wywoławze)**|Reprezentuje ścieżki wykonywania i profilowanie danych funkcji w przebiegu profilowania.|-   [Dane oprzyrządowania](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Dane dotyczące próbkowania](../profiling/call-tree-view-sampling-data.md)<br />-   [Dane próbkowania pamięci .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/call-tree-view-contention-data.md)|
|**Licznik**|Wyświetla listę znaczników profilowania i wartości liczników wydajności systemu Windows, które zostały zebrane podczas przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|
|**Ip**|Wyświetla dane profilowania według instrukcji.|-   [Dane dotyczące próbkowania](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dane próbkowania pamięci .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dane rywalizacji](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Życia**|Wyświetla listę okresu istnienia przydzielonych obiektów.|-   [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md)|
|**Linii**|Wyświetla listę danych profilowania według wiersza kodu źródłowego.|-   [Dane dotyczące próbkowania](../profiling/lines-view-sampling-data.md)<br />-   [Dane próbkowania pamięci .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dane rywalizacji](../profiling/lines-view-contention-data.md)|
|**Nagłówka**|Profilowanie informacji nagłówka pliku danych.|Specyficzne dla pliku.|
|**Mark**|Znaczniki profilowania zebrane w przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|
|**Moduł**|Wyświetla listę danych profilowania dla modułów.|-   [Dane dotyczące próbkowania](../profiling/modules-view-sampling-data.md)<br />-   [Dane oprzyrządowania](../profiling/modules-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/modules-view-contention-data.md)|
|**Proces**|Wyświetla listę danych profilowania dla procesów.|-   [Widok procesu](../profiling/process-view.md)<br />-   [Dane rywalizacji](../profiling/process-view-contention-data.md)|
|**Wątku**|Wyświetla listę danych profilowania dla wątków.|-   [Widok procesu](../profiling/process-view.md)|
|**Typ**|Wyświetla listę danych profilowania alokacji według typu.|-   [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)|
|**Rywalizacji**|Rywalizacja o zasoby.|-   [Rywalizacja o zasoby](../profiling/resource-contentions-view-contention-data.md)|
|**ZasadyWarnings**|Wyświetla listę problemów z regułami wydajności.|- Wyświetla checkid, opis i lokalizację kodu źródłowego problemu reguły.|
|**ETW**|Wyświetla listę zdarzeń śledzenia zdarzeń dla systemu Windows (ETW) zebranych w przebiegu profilowania.|-   [Raport ETW](../profiling/event-tracing-for-windows-etw-report.md)|
