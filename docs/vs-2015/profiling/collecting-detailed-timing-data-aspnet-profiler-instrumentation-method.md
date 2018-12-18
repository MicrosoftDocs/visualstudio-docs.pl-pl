---
title: Zbieranie danych o chronometrażu dla aplikacji sieci Web platformy ASP.NET przy użyciu metody Instrumentacji Profiler z wiersza polecenia | Dokumentacja firmy Microsoft
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
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 191d61fd14bef7b64f7095461df0cc83cdda7246
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726271"
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Zbieranie szczegółowych danych o chronometrażu dla aplikacji internetowej ASP.NET przy użyciu Metody instrumentacji profilera z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano procedury składowane i opcji zbierania wydajności szczegółowe dane dotyczące [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web za pomocą **VSPerfCmd** narzędzia wiersza polecenia i metody instrumentacji.  
  
> [!NOTE]
>  **VSPerfCmd** narzędzie zapewnia pełny dostęp do funkcji narzędzi profilowania, między innymi wstrzymywanie i wznawianie profilowania i zbieranie dodatkowych danych z procesora i liczniki wydajności Windows. Można również użyć **VSPerfASPNETCmd** narzędzie wiersza polecenia, jeśli nie potrzebujesz tej funkcji. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, żadne zmienne środowiskowe muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Aby uzyskać więcej informacji, zobacz [szybkie profilowanie witryny sieci Web za pomocą polecenia VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil statycznie skompilowane pliki binarne**|-   [Porady: Instrumentacja statycznie skompilowanej ASP.NET aplikacji i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
|**Profilowania dynamicznie skompilowanych plików binarnych**|-   [Porady: Instrumentacja dynamicznie skompilowanej ASP.NET aplikacji i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
### <a name="profiling-aspnet-web-applications"></a>Profilowanie aplikacji internetowej ASP.NET  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil przy użyciu metody próbkowania**|-   [Zbieranie statystyk aplikacji przy użyciu metody próbkowania](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Profil kolekcji alokacji i odzyskiwanie pamięci**|-   [Zbieranie danych pamięci](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Profil działanie zasobu rywalizacji o zasoby i wątku**|-   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Profilowanie za pomocą metody Instrumentacji  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Profil aplikacji autonomicznej (klienta)**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Usługi profilowania**|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu metody Instrumentacji](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Analizowanie danych Instrumentacji widoków i raportów  
 [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)



