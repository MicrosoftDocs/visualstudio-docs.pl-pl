---
title: Ustawianie ogólnych opcji sesji wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3bb57e2c8c5dd156fd5c96994eeb843569954af
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544953"
---
# <a name="setting-general-performance-session-options"></a>Ustawianie opcji sesji wydajności ogólnej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można ustawić metodę kolekcji i konwencje nazewnictwa danych dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sesji wydajności narzędzia profilowania na stronie **Ogólne** okna dialogowego właściwości dla sesji wydajności. Aby otworzyć to okno dialogowe z **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="choosing-data-collection-methods"></a>Wybieranie metod zbierania danych  
 Metodę kolekcji bazowej ustawia się, wybierając jedną z opcji w obszarze **Kolekcja profilowania**. Opcje są opisane w poniższej tabeli:  
  
|Opcja|Opis|  
|-|-|  
|**Próbkowanie**. Metoda próbkowania zbiera informacje profilowania w regularnych odstępach czasu. Ta metoda jest przydatna do znajdowania problemów z użyciem procesora i jest sugerowaną metodą uruchamiania większości badań wydajności.|-   [Zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentacja**. Metoda Instrumentacji wprowadza do kopii kodu profilowania modułu, który rejestruje każde wejście, wyjście i wywołanie funkcji funkcji w module podczas przebiegu profilowania. Ta metoda jest przydatna do zbierania szczegółowych informacji o chronometrażu w sekcji kodu oraz do poznania wpływu operacji wejścia i wyjścia na wydajność aplikacji.|-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Współbieżność**. Metoda współbieżności zbiera dane dla każdego zdarzenia, które blokuje wykonywanie kodu, na przykład gdy wątek oczekuje na zwolnienie zablokowanego dostępu do zasobu aplikacji. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.|-   [Zbieranie danych współbieżności dla wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 Dane pamięci platformy .NET można zbierać przy użyciu metody próbkowania lub Instrumentacji. Wybierasz typ danych w obszarze **profilowania pamięci platformy .NET**.  
  
|Opcje|Artykuł|  
|-|-|  
|**Zbierz informacje o alokacji obiektu .NET**. Domyślnie dane obejmują liczbę i rozmiar przydzielonego obiektu. Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć zbieranie danych pamięci platformy .NET.<br /><br /> **Zbierz również informacje o okresie istnienia obiektu .NET**. Zaznacz to pole wyboru, aby uwzględnić dane dotyczące generacji wyrzucania elementów bezużytecznych, które były używane do odzyskiwania obiektów pamięci.|-   [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Po rozpoczęciu profilowania aplikacji zostanie wyświetlona strona sesji profilowania, w której można wstrzymywać, wznawiać i zatrzymywać profilowanie.  
  
 ![Strona sesji profilowania](../profiling/media/prof-profilingsessionpage.png "PROF_ProfilingSessionPage")  
  
## <a name="setting-profiling-data-file-options"></a>Ustawianie opcji pliku danych profilowania  
  
|Opcja|Artykuł|  
|-|-|  
|**Raport**. Domyślnie plik danych profilowania (. vsp) otrzymuje nazwę profilowanej aplikacji i znajduje się w folderze rozwiązanie lub projekt. Ciąg daty jest również dołączany do nazwy, a przyrostowy numer jest dodawany do plików danych, które w przeciwnym razie byłyby zduplikowane nazwy. Można zmienić te opcje.|-   [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
