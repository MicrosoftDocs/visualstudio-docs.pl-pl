---
title: Konfigurowanie sesji wydajności | Dokumentacja firmy Microsoft
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
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 280d9023167b4d83dfb8b0137301219a518521b9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790399"
---
# <a name="configuring-performance-sessions"></a>Konfigurowanie sesji wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools można zbierać szeroką gamę danych wydajności dla wielu typów aplikacji. W tej sekcji dowiesz się, jak za pomocą właściwości Wizardand wydajność sesji wydajności i docelowy plik binarny Konfigurowanie narzędzi profilowania do zbierania danych, który Cię interesuje. Właściwości konfiguracji narzędzia profilowania można również do kontrolowania ilości danych zbieranych podczas uruchomienia profilowania. Aby uzyskać więcej informacji, zobacz [kontrolowanie zbierania danych](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  W wielu przypadkach przy użyciu właściwości domyślne kreatora wydajności jest skutecznym sposobem zbierania danych profilowania. Aby uzyskać więcej informacji, zobacz [profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md) i [wprowadzenie](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Ustawianie podstawowych opcji profilowania:** należy skonfigurować [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] do korzystania z serwera symboli firmy Microsoft. Będzie to upewnij się, że masz dostęp do symboli, takich jak nazwy funkcji i parametrów, aby uzyskać bieżącą wersję Windows i innych aplikacji firmy Microsoft. Można również określić inne opcje ogólne, przed uruchomieniem sesji profilowania, takich jak system uprawnień do narzędzi profilowania i nazwy pliku danych profilowania.|-   [Porady: odwoływać się do informacji o symbolach Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Instrukcje: serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)<br />-   [Porady: Ustawianie bieżącej sesji](../profiling/how-to-set-the-current-session.md)<br />-   [Porady: Ustawianie uprawnień](../profiling/how-to-set-permissions.md)<br />-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Określ dane, które mają być zbierane:** procedur, które służą do konfigurowania sesji profilowania są zależne od typ aplikacji docelowej, który chcesz przeprowadzić profilowanie i typ danych wydajności, które mają być zbierane.|-   [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)<br />-   [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Porady: profilowanie kodu JavaScript na stronach sieci Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Zbieranie danych współbieżności procesu i wątku](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Zbieranie dodatkowych danych o wydajności](../profiling/collecting-additional-performance-data.md)|  
|**Ustawianie opcji konfiguracji zaawansowanej:** podczas profilowania aplikacji .NET Framework, które załadować wiele wersji wspólnego języka środowiska wykonawczego języka wspólnego (CLR) można określić, którą wersję profilu. Jeśli masz wiele plików .exe w sesji wydajności, można ustawić kolejność rozruchu plików binarnych.|-   [Porady: Określanie środowiska wykonawczego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Porady: Określanie plików binarnych do ekranu startowego](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)



