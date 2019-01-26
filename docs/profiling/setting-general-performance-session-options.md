---
title: Opcje sesji wydajności ogólnej ustawienie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4cc99869276588da43a897e7b087f6e1251651b7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026778"
---
# <a name="set-general-performance-session-options"></a>Ustawianie opcji sesji wydajności ogólnej

Można ustawić metod zbierania i profilowanie danych konwencje nazewnictwa dla sesji wydajności programu Visual Studio Profiling Tools **ogólne** strony okna dialogowego właściwości sesji wydajności. Aby otworzyć to okno dialogowe z **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.

## <a name="choosing-data-collection-methods"></a>Wybieranie metody zbierania danych

Ustawianie metody podstawowej kolekcji, wybierając jedną z opcji w obszarze **kolekcja profilowania**. Opcje te są opisane, zgodnie z poniższą tabelą:

|||
|-|-|
|**Próbkowanie**. Metoda pobierania próbek zbiera informacje dotyczące profilowania w regularnych odstępach czasu. Ta metoda jest przydatna do znajdowania problemy dotyczące użycia procesora i jest metodą sugerowane na uruchamianie większości badania wydajności.|- [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentacja**. Metoda Instrumentacja wprowadza do kopii modułu profilowania kodu, który rejestruje każdego wpisu, zakończenia i wywołanie funkcji funkcje w module podczas uruchomienia profilowania. Ta metoda jest przydatne do zbierania informacji chronometrażu o sekcji kodu i zrozumienie wpływu na operacje wejścia i wyjścia na wydajność aplikacji.|- [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Współbieżność**. Metody współbieżności zbiera dane dla każdego zdarzenia, że bloki wykonywania kodu, takie jak kiedy wątek czeka na zablokowany dostęp do zasobu aplikacji ma zostać zwolniony. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.|- [Zbieranie danych współbieżności procesu i wątku](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Może zbierać dane pamięci platformy .NET przy użyciu metody próbkowania i instrumentacji. Wybierz typ danych w ramach **profilowania pamięci środowiska .NET**.

|||
|-|-|
|**Zbierz informacje dotyczące alokacji obiektów platformy .NET**. Domyślnie dane obejmują liczbę i rozmiar istnienia przydzielonych obiektów. Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć zbieranie danych pamięci .NET. |- [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET**. Zaznacz to pole wyboru, aby dołączyć dane dotyczące generacje kolekcji wyrzucania elementów, które zostały użyte do odzyskania obiektów pamięci.|- [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Stroną sesji profilowania pojawia się po uruchomieniu profil aplikacji, którym można wstrzymać, wznowić i zatrzymanie profilowania.

 ![Stronie sesji profilowania](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Ustawianie opcji pliku danych profilowania

|||
|-|-|
|**Raport**. Domyślnie plik profilowania (.vsp) danych o nazwie profilowanej aplikacji i znajduje się w folderze rozwiązania lub projektu. Ciąg daty jest również dołączana do nazwy, a zwiększona liczba jest dodawany do plików danych, które w przeciwnym razie byłyby takich samych nazwach. Te opcje można zmienić.|- [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|