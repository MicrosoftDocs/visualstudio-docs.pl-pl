---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f4b2b78f7187b7a49b78312a1105a2af884fda3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186640"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury i opcje zbierania danych wydajności dla autonomicznych aplikacji (klienta) przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania z wiersza polecenia.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Zbieranie statystyk aplikacji:** Użyj metody próbkowania, aby zebrać dane statystyczne wydajności. Dane próbkowania są przydatne do analizowania problemów z użyciem procesora CPU oraz do poznania ogólnych cech wydajności aplikacji.|-   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbieranie szczegółowych danych o chronometrażu:** Użyj metody instrumentacji, aby zbierać szczegółowe informacje o chronometrażu. Dane instrumentacji są przydatne do analizowania problemów we/wy i szczegółowych analiz scenariuszy aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Zbierz dane pamięci .NET:** Użyj próbkowania lub Instrumentacji, aby zebrać dane alokacji pamięci .NET pokazujące rozmiar i liczbę przydzielonych obiektów. Możesz również zbierać dane o okresie istnienia obiektu, pokazujące rozmiar i liczbę obiektów, które są odzyskiwane w każdej generacji wyrzucania elementów bezużytecznych.|-   [Zbieranie danych pamięci .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Zbierz dane współbieżności:** Użyj metody współbieżności, aby zbierać dane rywalizacji o zasoby i dane aktywności wątków, które pokazują wykorzystanie procesora CPU, rywalizację o wątki, migrację wątków, opóźnienia synchronizacji, obszary nakładających się operacji we/wy oraz inne zdarzenia systemowe.|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Dodaj dane interakcji warstwy:** Można dodać dane dotyczące wydajności dotyczące synchronicznych wywołań ADO.NET, które aplikacja wykonał w [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bazie danych firmy Microsoft. Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia.|-   [Zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Wypróbuj:** Procedury krok po kroku umożliwiają profilowanie przykładowej aplikacji klienckiej przy użyciu metody próbkowania lub Instrumentacji.|-   [Przewodnik: Profilowanie wiersza polecenia przy użyciu próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Przewodnik: Profilowanie wiersza polecenia przy użyciu instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>Powiązane zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profilowanie aplikacji ASP.NET**|-   [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Usługi profilu**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|
