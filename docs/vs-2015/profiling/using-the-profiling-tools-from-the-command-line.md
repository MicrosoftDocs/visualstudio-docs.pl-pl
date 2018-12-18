---
title: Za pomocą profilowania narzędzia z wiersza polecenia | Dokumentacja firmy Microsoft
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
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9cb3fafa78d49904c346212e8fd4062c966a63f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775150"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Korzystanie z narzędzi do profilowania z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć narzędzia wiersza poleceń dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools do profilu aplikacji w wierszu polecenia i zautomatyzować profilowania przy użyciu plików wsadowych i skryptów. Można również wygenerować pliki raportu w wierszu polecenia. Uproszczone autonomicznego profilera można użyć do zbierania danych na komputerach, które nie mają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowane.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Ustaw lokalizację symboli:** do wyświetlania nazw funkcji i parametrów, program profilujący musi mieć dostęp do plików symboli (.pdb) profilowanych danych binarnych. Pliki te powinny obejmować pliki symboli dla Microsoft systemu operacyjnego i aplikacji, które mają być wyświetlane w analizy. Upewnij się, że pliki .pdb poprawne dla danych binarnych firmy Microsoft, można użyć serwera publicznego symboli firmy Microsoft.|-   [Porady: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profiluj aplikację:** narzędzi wiersza polecenia i opcje używane do profilu aplikacji docelowej są zależne od typu aplikacji, metody profilowania i tego, czy element docelowy jest aplikacją zarządzane lub natywne.|-   [Za pomocą metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|  
|**Tworzenie raportów XML i CSV:** profilowania w wierszu polecenia tworzy pliki danych, które mogą być wyświetlane w interfejsie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Można również wygenerować XML lub pliki wartości rozdzielanych przecinkami (CSV) w danych za pomocą narzędzia wiersza polecenia VSPerfReport.|-   [Tworzenie raportów Profiler w wierszu polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profiluj kod na komputerach bez programu Visual Studio:** autonomicznego profilera Profiling Tools umożliwiają zbieranie danych dla aplikacji na komputerach, które nie mają [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowane.|-   [Porady: Instalowanie autonomiczny Profiler](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Tematy pomocy  
 [Narzędzia profilowania wiersza polecenia — dokumentacja](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)



