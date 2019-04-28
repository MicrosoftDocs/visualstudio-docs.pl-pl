---
title: Konfigurowanie sesji wydajności | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434326"
---
# <a name="configuring-performance-sessions"></a>Konfigurowanie sesji wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools można zbierać szeroką gamę danych wydajności dla wielu typów aplikacji. W tej sekcji dowiesz się, jak za pomocą właściwości Wizardand wydajność sesji wydajności i docelowy plik binarny Konfigurowanie narzędzi profilowania do zbierania danych, który Cię interesuje. Właściwości konfiguracji narzędzia profilowania można również do kontrolowania ilości danych zbieranych podczas uruchomienia profilowania. Aby uzyskać więcej informacji, zobacz [kontrolowanie zbierania danych](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
> W wielu przypadkach przy użyciu właściwości domyślne kreatora wydajności jest skutecznym sposobem zbierania danych profilowania. Aby uzyskać więcej informacji, zobacz [profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md) i [wprowadzenie](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Ustawianie podstawowych opcji profilowania:** Należy skonfigurować [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] do korzystania z serwera symboli firmy Microsoft. Będzie to upewnij się, że masz dostęp do symboli, takich jak nazwy funkcji i parametrów, aby uzyskać bieżącą wersję Windows i innych aplikacji firmy Microsoft. Można również określić inne opcje ogólne, przed uruchomieniem sesji profilowania, takich jak system uprawnień do narzędzi profilowania i nazwy pliku danych profilowania.|-   [Jak: Odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Jak: Serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)<br />-   [Jak: Ustawianie bieżącej sesji](../profiling/how-to-set-the-current-session.md)<br />-   [Jak: Ustawianie uprawnień](../profiling/how-to-set-permissions.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Określ dane, które mają być zbierane:** Procedury, które są używane do konfigurowania sesji profilowania zależą od tego, typ aplikacji docelowej, który chcesz przeprowadzić profilowanie i typ danych wydajności, które mają być zbierane.|-   [Jak: Wybieranie metod zbierania](../profiling/how-to-choose-collection-methods.md)<br />-   [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Jak: Profilowanie kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Zbieranie danych współbieżności procesu i wątku](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Zbieranie dodatkowych danych o wydajności](../profiling/collecting-additional-performance-data.md)|  
|**Ustawianie opcji zaawansowanej konfiguracji:** Podczas profilowania aplikacji .NET Framework, które załadować wiele wersji wspólnego języka środowiska wykonawczego języka wspólnego (CLR) można określić, którą wersję profilu. Jeśli masz wiele plików .exe w sesji wydajności, można ustawić kolejność rozruchu plików binarnych.|-   [Jak: Określanie środowiska uruchomieniowego programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Jak: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)
