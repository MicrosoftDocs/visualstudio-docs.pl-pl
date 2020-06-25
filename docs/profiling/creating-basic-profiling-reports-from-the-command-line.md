---
title: Tworzenie podstawowych raportów profilowania z wiersza polecenia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bca944b67b19fdbb4138c479acf5693994d1c717
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329050"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Tworzenie podstawowych raportów profilowania z poziomu wiersza polecenia
W tym artykule opisano podstawowe polecenia VSPerfReport, które generują wartości rozdzielane przecinkami (.* CSV*) raportów z programu. *VSP* lub. plik danych profilowania *vsps* . Aby uzyskać opis wszystkich opcji raportów, zobacz [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Polecenia raportów
 Użyj jednego z poniższych poleceń, aby utworzyć raport dla określonego pliku danych profilowania.

 **VSPerfReport** `VSPFile` **/Summary: wszystkie** Generuje wszystkie raporty dostępne dla programu. *VSP* lub. plik *vsps* .

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...] Generuje określone typy raportów.

 **VSPerfReport** `VSPFile` **/CallTrace** Generuje raport, który zawiera listę wszystkich zdarzeń zbierania danych. Tylko Instrumentacja.

## <a name="summary-report-type-parameters"></a>Parametry typu raportu podsumowania
 W poniższej tabeli opisano raporty, które są generowane przez określoną opcję typu raportu. Kolumny raportu zależą od metody profilowania, która została użyta do zbierania danych.

|Parametr podsumowania|Opis raportu|Odwołanie do raportu|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|Reprezentuje relacje nadrzędny/podrzędny między funkcjami.|-   [Próbkowanie danych](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dane instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/caller-callee-view-contention-data.md)|
|**Funkcja**|Wyświetla listę danych profilowania według funkcji.|-   [Próbkowanie danych](../profiling/functions-view-sampling-data.md)<br />-   [Dane instrumentacji](../profiling/functions-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci platformy .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/functions-view-contention-data.md)|
|**Widokach drzewa wywołań**|Reprezentuje ścieżki wykonywania i dane profilowania funkcji w przebiegu profilowania.|-   [Dane instrumentacji](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Próbkowanie danych](../profiling/call-tree-view-sampling-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci platformy .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/call-tree-view-contention-data.md)|
|**Licznik**|Wyświetla listę znaczników profilowania i wartości liczników wydajności systemu Windows, które zostały zebrane podczas przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|
|**Przegląd**|Wyświetla listę danych profilowania według instrukcji.|-   [Próbkowanie danych](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dane rywalizacji](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Życia**|Wyświetla listę okresów istnienia przyznanych obiektów.|-   [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md)|
|**Wiersz**|Wyświetla listę danych profilowania według wiersza kodu źródłowego.|-   [Próbkowanie danych](../profiling/lines-view-sampling-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dane rywalizacji](../profiling/lines-view-contention-data.md)|
|**Nagłówki**|Profilowanie informacji nagłówka pliku danych.|Specyficzne dla pliku.|
|**Znacznik**|Znaczniki profilowania zebrane w przebiegu profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|
|**Moduł**|Wyświetla listę danych profilowania dla modułów.|-   [Próbkowanie danych](../profiling/modules-view-sampling-data.md)<br />-   [Dane instrumentacji](../profiling/modules-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dane instrumentacji pamięci platformy .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/modules-view-contention-data.md)|
|**Proces**|Wyświetla listę danych profilowania dla procesów.|-   [Widok procesu](../profiling/process-view.md)<br />-   [Dane rywalizacji](../profiling/process-view-contention-data.md)|
|**Nici**|Wyświetla listę danych profilowania dla wątków.|-   [Widok procesu](../profiling/process-view.md)|
|**Typ**|Wyświetla listę alokacji danych profilowania według typu.|-   [Widok przydziałów](../profiling/dotnet-memory-allocations-view.md)|
|**Rywalizacji**|Rywalizacje o zasoby.|-   [Rywalizacje o zasoby](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Wyświetla listę problemów z regułami wydajności.|-Wyświetla listę CheckId, opis i lokalizację kodu źródłowego problemu z regułą.|
|**ETW**|Wyświetla listę zdarzeń śledzenia zdarzeń systemu Windows (ETW) zebranych w przebiegu profilowania.|-   [Raport ETW](../profiling/event-tracing-for-windows-etw-report.md)|
