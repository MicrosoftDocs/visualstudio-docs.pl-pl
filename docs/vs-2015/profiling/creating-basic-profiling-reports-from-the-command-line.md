---
title: Tworzenie Basic profilowania raportów z poziomu wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30361f0f4ae147458252400a5232a657574553d4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786769"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Tworzenie podstawowych raportów dotyczących profilowania z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano podstawowe polecenia VSPerfReport generujące raporty wartości rozdzielanych przecinkami (.csv) z .vsp lub .vsps pliku danych profilowania. Aby uzyskać opis wszystkich opcji raportu, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Polecenia raportu  
 Użyj jednej z następujących poleceń, aby utworzyć raport dla określonego pliku danych profilowania.  
  
 **VSPerfReport** `VSPFile` **której**  
 Generuje wszystkie raporty dostępne dla pliku .vsp lub .vsps.  
  
 **VSPerfReport** `VSPFile` **/Summary:**`ReportType`[,`ReportType`...]  
 Generuje typy określonego raportu.  
  
 **VSPerfReport** `VSPFile`   **/calltrace**  
 Generuje raport zawierający listę zdarzeń zbierania danych. Tylko Instrumentacja.  
  
## <a name="summary-report-type-parameters"></a>Podsumowanie parametrów typu raportu  
 W poniższej tabeli opisano raporty, które są generowane przez określoną opcję typu raportu. Kolumny raportu zależą od metody profilowania, użytej do zebrania danych.  
  
|Parametr podsumowania|Opis raportu|Dokumentacja raportów|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|Reprezentuje relacje nadrzędne/podrzędne między funkcjami.|-   [Próbkowanie danych](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dane Instrumentacji](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dane Instrumentacji pamięci platformy .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Wyświetla listę danych profilowania posortowanych według funkcji.|-   [Próbkowanie danych](../profiling/functions-view-sampling-data.md)<br />-   [Dane Instrumentacji](../profiling/functions-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dane Instrumentacji pamięci platformy .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/functions-view-contention-data.md)|  
|**Alokowania**|Reprezentuje ścieżki wykonywania i dane profilowania funkcji w trakcie uruchomienia profilowania.|-   [Dane Instrumentacji](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Próbkowanie danych](../profiling/call-tree-view-sampling-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dane Instrumentacji pamięci platformy .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Wyświetla listę znaczników profilowania i wartości licznika wydajności Windows, które zostały zebrane podczas uruchomienia profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|  
|**Adresów IP**|Wyświetla listę danych profilowania posortowanych według instrukcji.|-   [Próbkowanie danych](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dane rywalizacji](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Życia**|Wyświetla listę okresów istnienia przydzielonych obiektów.|-   [Widok okresu istnienia obiektu](../profiling/object-lifetime-view.md)|  
|**Wiersz**|Wyświetla listę danych profilowania posortowanych według wiersza kodu źródłowego.|-   [Próbkowanie danych](../profiling/lines-view-sampling-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dane rywalizacji](../profiling/lines-view-contention-data.md)|  
|**Nagłówek**|Profilowanie informacja nagłówka pliku danych.|Określone dla pliku.|  
|**Mark**|Znaczniki profilowania zebrana podczas uruchomienia profilowania.|-   [Widok znaczników](../profiling/marks-view.md)|  
|**Module**|Wyświetla listę danych profilowania dla modułów.|-   [Próbkowanie danych](../profiling/modules-view-sampling-data.md)<br />-   [Dane Instrumentacji](../profiling/modules-view-instrumentation-data.md)<br />-   [Dane próbkowania pamięci platformy .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dane Instrumentacji pamięci platformy .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dane rywalizacji](../profiling/modules-view-contention-data.md)|  
|**Proces**|Wyświetla listę danych profilowania dla procesów.|-   [Widok procesu](../profiling/process-view.md)<br />-   [Dane rywalizacji](../profiling/process-view-contention-data.md)|  
|**Wątek**|Wyświetla listę danych profilowania dla wątków.|-   [Widok procesu](../profiling/process-view.md)|  
|**Typ**|Wyświetla listę alokacji danych profilowania posortowanych według typu.|-   [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)|  
|**Rywalizacji o zasoby**|Rywalizacje o zasoby.|-   [Rywalizacje o zasoby](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Wyświetla listę problemów z regułami wydajności.|— Wyświetla CheckId, opis i lokalizacji kodu źródłowego problemu z regułą.|  
|**ETW.**|Wyświetla zdarzenia śledzenia dla Windows (ETW) zebranych podczas uruchomienia profilowania.|-   [Raport ETW](../profiling/event-tracing-for-windows-etw-report.md)|



