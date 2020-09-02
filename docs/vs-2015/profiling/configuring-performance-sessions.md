---
title: Konfigurowanie sesji wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d67801cedded1ccf66544e21257866feda828e31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779674"
---
# <a name="configuring-performance-sessions"></a>Konfigurowanie sesji wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania można zbierać szeroką gamę danych wydajności dla dużej liczby typów aplikacji. W tej sekcji przedstawiono sposób użycia właściwości Wizardand wydajności sesji wydajności i docelowego pliku binarnego w celu skonfigurowania narzędzia profilowania w celu zebrania interesujących Cię danych. Właściwości konfiguracji narzędzia profilowania mogą być również używane do kontrolowania ilości danych zbieranych w ramach uruchomienia profilowania. Aby uzyskać więcej informacji, zobacz [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
> W wielu przypadkach korzystanie z właściwości domyślnych Kreatora wydajności jest efektywnym sposobem na zbieranie danych profilowania. Aby uzyskać więcej informacji, zobacz temat [Przewodnik początkujący dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md) i [wprowadzenie](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Ustaw podstawowe opcje profilowania:** Należy skonfigurować [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] program w taki sposób, aby korzystał z serwera symboli firmy Microsoft. Dzięki temu masz dostęp do symboli, takich jak nazwy funkcji i parametrów, dla bieżącej wersji systemu Windows i innych aplikacji firmy Microsoft. Można również określić inne opcje ogólne przed rozpoczęciem sesji profilowania, takie jak uprawnienia systemowe do narzędzi profilowania i nazwy plików danych profilowania.|-   [Instrukcje: odwołania do informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Instrukcje: Serializowanie informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)<br />-   [Instrukcje: ustawienie bieżącej sesji](../profiling/how-to-set-the-current-session.md)<br />-   [Instrukcje: Ustawianie uprawnień](../profiling/how-to-set-permissions.md)<br />-   [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Określ dane, które mają być zbierane:** Procedury służące do konfigurowania sesji profilowania zależą od typu aplikacji docelowej, która ma być profilowania, oraz typu danych wydajności, które mają być zbierane.|-   [Instrukcje: wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)<br />-   [Zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Instrukcje: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Zbieranie danych współbieżności dla wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Zbieranie dodatkowych danych dotyczących wydajności](../profiling/collecting-additional-performance-data.md)|  
|**Ustaw zaawansowane opcje konfiguracji:** Podczas profilowania .NET Framework aplikacji ładujących wiele wersji środowiska uruchomieniowego języka wspólnego (CLR) można określić, która wersja ma być przeprofilowania. Jeśli masz wiele plików exe w sesji wydajności, możesz ustawić kolejność uruchamiania plików binarnych.|-   [Instrukcje: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Instrukcje: Określanie pliku binarnego do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)
