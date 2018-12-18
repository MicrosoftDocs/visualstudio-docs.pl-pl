---
title: Zbieranie danych pamięci z aplikacji internetowej ASP.NET przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 260676ee54a9410bb7bfc8d90bd3d044c403169d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788306"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Zbieranie danych pamięci z aplikacji internetowej ASP.NET przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury składowane i opcji zbierania danych pamięci alokacji i obiekt okresu istnienia dla aplikacji sieci Web platformy ASP.NET za pomocą **VSPerfCmd** narzędzie wiersza polecenia.  
  
> [!NOTE]
>  **VSPerfCmd** narzędzie zapewnia pełny dostęp do funkcji narzędzi profilowania, między innymi wstrzymywanie i wznawianie profilowania i zbieranie dodatkowych danych z procesora i liczniki wydajności Windows. Można również użyć **VSPerfASPNETCmd** narzędzie wiersza polecenia, jeśli nie potrzebujesz tej funkcji. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, żadne zmienne środowiskowe, które należy skonfigurować i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Dołącz profiler do działającej aplikacji platformy ASP.NET**|-   [Porady: dołączyć Profiler do aplikacji internetowej ASP.NET w celu zbierania danych pamięci](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrument statycznie skompilowane pliki binarne**|-   [Porady: Instrumentacja statycznie skompilowanej ASP.NET aplikacji i zbieranie danych pamięci](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrument dynamicznie skompilowanych plików binarnych**|-   [Porady: Instrumentacja dynamicznie skompilowanej ASP.NET aplikacji i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
### <a name="profiling-aspnet-web-applications"></a>Profilowanie aplikacji internetowej ASP.NET  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profil przy użyciu metody Instrumentacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Profil działanie zasobu rywalizacji o zasoby i wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Profilowanie danych pamięci .NET Framework  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klienta)**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Usługi profilowania**|-   [Zbieranie danych pamięci .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analizowanie danych pamięci .NET widoków i raportów  
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Tematy pomocy  
 [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)



