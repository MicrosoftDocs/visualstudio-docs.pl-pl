---
title: Używanie narzędzia profilowania z wiersza polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: ebd0fbabb73d4c77d1d888b207882e7403f46aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822683"
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Korzystanie z narzędzi do profilowania z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia wiersza polecenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania umożliwiają Profilowanie aplikacji w wierszu polecenia i automatyzowanie profilowania przy użyciu plików wsadowych i skryptów. Pliki raportów można również generować w wierszu polecenia. Możesz użyć prostego profilera autonomicznego do zbierania danych na komputerach, na których nie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowano programu.  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Ustaw lokalizację symboli:** Aby wyświetlić nazwy funkcji i parametrów, profiler musi mieć dostęp do plików symboli (. pdb) profilowanych plików binarnych. Pliki te powinny zawierać pliki symboli dla systemu operacyjnego firmy Microsoft i aplikacji, które mają być wyświetlane w analizie. Możesz użyć publicznego serwera symboli firmy Microsoft, aby upewnić się, że masz poprawne pliki. pdb dla plików binarnych firmy Microsoft.|-   [Instrukcje: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profiluj aplikację:** Narzędzia wiersza polecenia i opcje używane do profilowania aplikacji docelowej zależą od typu aplikacji, metody profilowania i od tego, czy obiektem docelowym jest aplikacja zarządzana lub natywna.|-   [Korzystanie z metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|  
|**Tworzenie raportów XML i CSV:** Profilowanie w wierszu polecenia tworzy pliki danych, które mogą być wyświetlane w interfejsie dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Możesz również generować pliki z wartościami rozdzielanymi przecinkami (. csv) danych za pomocą narzędzia wiersza polecenia VSPerfReport.|-   [Tworzenie raportów profilera z wiersza polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Kod profilu na komputerach bez programu Visual Studio:** Za pomocą autonomicznego profilera narzędzia profilowania można zbierać dane dla aplikacji na komputerach, na których nie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowano programu.|-   [Instrukcje: Instalowanie autonomicznego profilera](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Tematy pomocy  
 [Informacje narzędzia profilowania wiersza polecenia](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)
