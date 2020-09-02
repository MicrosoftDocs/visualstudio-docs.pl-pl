---
title: Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03e27d021b8b3c5ec29a8646a1bbe7bc6ebdecc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64818353"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Zbieranie statystyk aplikacji dla aplikacji autonomicznych przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury i opcje zbierania statystyk wydajności dla aplikacji klienckiej (autonomicznej) za pomocą metody próbkowania z wiersza polecenia.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Uruchamianie aplikacji przy użyciu profilowania**|-   [Instrukcje: uruchamianie aplikacji autonomicznej i zbieranie statystyk aplikacji](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołącz profiler do uruchomionej aplikacji .NET Framework**|-   [Instrukcje: dołączanie profilera do aplikacji .NET Framework i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dołącz profiler do uruchomionej aplikacji C/C++**|-   [Instrukcje: dołączanie profilera do natywnej aplikacji i zbieranie statystyk aplikacji](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Dodawanie danych interakcji warstwy**|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Powiązane zadania  
  
### <a name="profiling-stand-alone-applications"></a>Profilowanie aplikacji autonomicznych  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Instrumentacja aplikacji**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Zbierz dane alokacji pamięci .NET i wyrzucania elementów bezużytecznych**|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie danych rywalizacji o zasoby i wykonywanie wątków**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Profilowanie przy użyciu metody próbkowania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Profilowanie aplikacji sieci Web ASP.NET**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
|**Usługi profilu**|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Opisuje sposób zbierania statystyk wydajności z usług systemu Windows przy użyciu metody próbkowania.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analizowanie widoków i raportów danych próbkowania  
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
