---
title: Ustawianie ogólnych opcji sesji wydajności | Microsoft Docs
description: Dowiedz się, jak ustawić metodę zbierania i konwencje nazewnictwa danych dla sesji wydajności narzędzia profilowania.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.general
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 78082e8937f497af915c23e6db75b4b9836591fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960185"
---
# <a name="set-general-performance-session-options"></a>Ustawianie opcji sesji wydajności ogólnej

Można ustawić metodę kolekcji i konwencje nazewnictwa danych dla sesji wydajności programu Visual Studio narzędzia profilowania na stronie **Ogólne** okna dialogowego właściwości dla sesji wydajności. Aby otworzyć to okno dialogowe z **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

## <a name="choosing-data-collection-methods"></a>Wybieranie metod zbierania danych

Metodę kolekcji bazowej ustawia się, wybierając jedną z opcji w obszarze **Kolekcja profilowania**. Opcje są opisane w poniższej tabeli:

|Opcja|Artykuł|
|-|-|
|**Próbkowanie**. Metoda próbkowania zbiera informacje profilowania w regularnych odstępach czasu. Ta metoda jest przydatna do znajdowania problemów z użyciem procesora i jest sugerowaną metodą uruchamiania większości badań wydajności.|- [Zbieranie statystyk wydajności przy użyciu próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)|
|**Instrumentacja**. Metoda Instrumentacji wprowadza do kopii kodu profilowania modułu, który rejestruje każde wejście, wyjście i wywołanie funkcji funkcji w module podczas przebiegu profilowania. Ta metoda jest przydatna do zbierania szczegółowych informacji o chronometrażu w sekcji kodu oraz do poznania wpływu operacji wejścia i wyjścia na wydajność aplikacji.|- [Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|
|**Współbieżność**. Metoda współbieżności zbiera dane dla każdego zdarzenia, które blokuje wykonywanie kodu, na przykład gdy wątek oczekuje na zwolnienie zablokowanego dostępu do zasobu aplikacji. Ta metoda jest przydatna do analizowania aplikacji wielowątkowych.|- [Zbieranie danych współbieżności dla wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)|

 Dane pamięci platformy .NET można zbierać przy użyciu metody próbkowania lub Instrumentacji. Wybierasz typ danych w obszarze **profilowania pamięci platformy .NET**.

|Opcja|Artykuł|
|-|-|
|**Zbierz informacje o alokacji obiektu .NET**. Domyślnie dane obejmują liczbę i rozmiar przydzielonego obiektu. Zaznacz lub wyczyść to pole wyboru, aby włączyć lub wyłączyć zbieranie danych pamięci platformy .NET. |- [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|
|**Zbierz również informacje o okresie istnienia obiektu .NET**. Zaznacz to pole wyboru, aby uwzględnić dane dotyczące generacji wyrzucania elementów bezużytecznych, które były używane do odzyskiwania obiektów pamięci.|- [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) |

 Po rozpoczęciu profilowania aplikacji zostanie wyświetlona strona sesji profilowania, w której można wstrzymywać, wznawiać i zatrzymywać profilowanie.

 ![Strona sesji profilowania](../profiling/media/prof_profilingsessionpage.png "PROF_ProfilingSessionPage")

## <a name="set-profiling-data-file-options"></a>Ustawianie opcji pliku danych profilowania

|Opcja|Artykuł|
|-|-|
|**Raport**. Domyślnie plik danych profilowania (. vsp) otrzymuje nazwę profilowanej aplikacji i znajduje się w folderze rozwiązanie lub projekt. Ciąg daty jest również dołączany do nazwy, a przyrostowy numer jest dodawany do plików danych, które w przeciwnym razie byłyby zduplikowane nazwy. Można zmienić te opcje.|- [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|
