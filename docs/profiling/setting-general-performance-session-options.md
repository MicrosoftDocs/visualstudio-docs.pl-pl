---
title: Ustawianie ogólnych opcji sesji wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 023681b263e6e70048ec7d82d2cee741672989ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773945"
---
# <a name="set-general-performance-session-options"></a>Ustawianie opcji sesji wydajności ogólnej

Można ustawić metodę zbierania i profilowanie konwencji nazewnictwa danych dla sesji wydajności Narzędzia profilowania programu Visual Studio na stronie **Ogólne** właściwości okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe w **Eksploratorze wydajności,** kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

## <a name="choosing-data-collection-methods"></a>Wybieranie metod zbierania danych

Metodę kolekcji podstawowej można ustawić, wybierając jedną z opcji w obszarze **Kolekcja profilowania**. Opcje są opisane w poniższej tabeli:

|||
|-|-|
|**Pobieranie próbek**. Metoda pobierania próbek zbiera informacje profilowania w regularnych odstępach czasu. Ta metoda jest przydatna do znajdowania problemów z wykorzystaniem procesora i jest sugerowaną metodą uruchamiania większości badań wydajności.|- [Zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentacja**. Metoda instrumentacji wstrzykuje do kopii kodu profilowania modułu, który rejestruje każdy wpis, wyjście i wywołanie funkcji funkcji w module podczas wykonywania profilowania. Ta metoda jest przydatna do zbierania szczegółowych informacji o chronometrażu o sekcji kodu i do zrozumienia wpływu operacji wejściowych i wyjściowych na wydajność aplikacji.|- [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Współbieżność**. Metoda współbieżności zbiera dane dla każdego zdarzenia, które blokuje wykonywanie kodu, na przykład gdy wątek czeka na zablokowany dostęp do zasobu aplikacji do uwolnienia. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.|- [Zbieranie danych współbieżności wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Dane pamięci platformy .NET można zbierać przy użyciu metod próbkowania lub instrumentacji. W obszarze **profilowanie pamięci .NET**można wybrać typ danych . NET .

|||
|-|-|
|**Zbieranie informacji o alokacji obiektów .NET**. Domyślnie dane obejmują liczbę i rozmiar przydzielonych obiektów. Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć zbieranie danych pamięci .NET. |- [Zbieranie alokacji pamięci platformy .NET i danych w okresie istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Zbieraj również informacje o okresie istnienia obiektu .NET**. Zaznacz to pole wyboru, aby uwzględnić dane dotyczące pokoleń wyrzucania elementów bezużytecznych, które były używane do odzyskiwania obiektów pamięci.|- [Zbieranie alokacji pamięci platformy .NET i danych w okresie istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Strona sesji profilowania pojawia się po rozpoczęciu profilowania aplikacji, w której można wstrzymać, wznowić i zatrzymać profilowanie.

 ![Strona sesji profilowania](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Ustawianie opcji plików danych profilowania

|||
|-|-|
|**Raport**. Domyślnie plik danych profilowania (.vsp) otrzymuje nazwę profilowanej aplikacji i znajduje się w folderze rozwiązania lub projektu. Ciąg daty jest również dołączany do nazwy, a przyrostowy numer jest dodawany do plików danych, które w przeciwnym razie miałyby zduplikowane nazwy. Można zmienić te opcje.|- [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
