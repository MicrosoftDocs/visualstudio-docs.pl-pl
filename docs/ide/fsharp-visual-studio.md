---
title: Narzędzia języka F#
description: 'Dowiedz się, które funkcje programu Visual Studio są obsługiwane w języku F #.'
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
f1_keywords:
- fs.ProjectPropertiesDebug
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c0ce6e68fa36f3b13474306ddd1d8304d640c0ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87507979"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Programowanie przy użyciu Visual F# w programie Visual Studio

Ten artykuł zawiera informacje o funkcjach programu Visual Studio na potrzeby programowania w języku F #.

## <a name="install-f-support"></a>Zainstaluj obsługę języka F #

Aby opracowywać przy użyciu języka F # w programie Visual Studio, najpierw zainstaluj obciążenie **Programowanie aplikacji klasycznych platformy .NET** , jeśli jeszcze tego nie zrobiono. Możesz zainstalować obciążenia programu Visual Studio za pomocą Instalator programu Visual Studio, które można otworzyć, wybierając pozycję **Narzędzia**  >  **Pobierz narzędzia i funkcje**.

![Obciążenie Programowanie aplikacji klasycznych dla platformy .NET w programie Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Funkcje projektu języka F #

Różne szablony projektów i elementów są dostępne dla języka F # w programie Visual Studio. Na poniższej ilustracji przedstawiono niektóre szablony projektów F # dla platformy .NET Core i .NET Standard:

![Szablony projektów języka F # w programie Visual Studio](media/fsharp-project-templates.png)

Na poniższej ilustracji przedstawiono niektóre szablony elementów F #:

![Szablony elementów języka F # w programie Visual Studio](media/fsharp-item-templates.png)

Aby uzyskać więcej informacji na temat szablonów elementów na potrzeby dostępu do danych, zobacz [dostawcy typów języka F #](/dotnet/fsharp/tutorials/type-providers/index).

Poniższa tabela zawiera podsumowanie funkcji we właściwościach projektu dla języka F #:

|Ustawienie projektu|Obsługiwane w języku F #?|Uwagi|
|---------------|----------------|-----|
|Pliki zasobów|Tak||
|Ustawienia kompilacji, debugowania i odwołania|Tak||
|Wielowersyjność kodu|Tak||
|Ikona i manifest|Nie|Dostępne za poorednictwem opcji wiersza poleceń kompilatora.|
|ASP.NET usługi klienta|Nie||
|ClickOnce|Nie|Użyj projektu klienta w innym języku .NET, jeśli ma to zastosowanie.|
|Silne nazewnictwo|Nie|Dostępne za poorednictwem opcji wiersza poleceń kompilatora.|
|Publikowanie zestawów i przechowywanie wersji|Nie||
|Analiza kodu|Nie|Narzędzia do analizy kodu można uruchamiać ręcznie lub jako część polecenia po kompilacji.|
|Zabezpieczenia (Zmień poziomy zaufania)|Nie||

## <a name="project-designer"></a>Projektant projektu

**Projektant projektu** składa się z kilku stron właściwości projektu pogrupowanych według pokrewnych funkcji. Strony dostępne dla projektów języka F # są głównie podzbiorem tych dostępnych dla innych języków i są opisane w poniższej tabeli. Linki są dostarczane do odpowiedniej strony **projektanta projektu** C#.

|Strona projektanta projektu|Linki pokrewne|Opis|
| - |-------------|-----------|
|Aplikacja|[Strona aplikacji, Projektant projektu](reference/application-page-project-designer-csharp.md)|Umożliwia określenie ustawień i właściwości na poziomie aplikacji, takich jak to, czy tworzysz bibliotekę lub plik wykonywalny, która wersja programu .NET jest przeznaczona dla aplikacji, oraz informacje o tym, gdzie są przechowywane pliki zasobów używane przez aplikację.|
|Kompilacja|[Strona kompilacja, Projektant projektu](reference/build-page-project-designer-csharp.md)|Umożliwia sterowanie sposobem kompilowania kodu.|
|Zdarzenia kompilacji|[Strona zdarzenia kompilacji, Projektant projektu](reference/build-events-page-project-designer-csharp.md)|Umożliwia określenie poleceń do uruchomienia przed kompilacją lub po niej.|
|Debugowanie|[Strona debugowania, Projektant projektu](reference/debug-page-project-designer.md)|Umożliwia sterowanie sposobem uruchamiania aplikacji podczas debugowania. Dotyczy to również poleceń, które mają być używane, i zawartości katalogu początkowego aplikacji oraz wszelkich specjalnych trybów debugowania, które mają być włączone, takich jak kod natywny i SQL.|
|Pakiet (tylko .NET SDK)|Brak|Umożliwia definiowanie metadanych pakietu NuGet podczas publikowania jako pakiet NuGet.|
|Ścieżki odwołań|[Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md)|Pozwala określić, gdzie mają być wyszukiwane zestawy, od których zależy kod.|
|Zasoby (tylko zestaw SDK platformy .NET)|Brak|Umożliwia generowanie domyślnego pliku zasobów i zarządzanie nim.|

### <a name="f-specific-settings"></a>Ustawienia specyficzne dla języka F #

Poniższa tabela zawiera podsumowanie ustawień specyficznych dla języka F #:

|Strona projektanta projektu|Ustawienie|Opis|
| - |-------|-----------|
|Kompilacja|Generuj wywołania tail|W przypadku wybrania tej wartości program umożliwia korzystanie z instrukcji języka pośredniego (MSIL) firmy Microsoft. Powoduje to, że ramka stosu zostanie ponownie użyta na potrzeby funkcji cyklicznych. Odpowiednik `--tailcalls` opcji kompilatora.|
|Kompilacja|Inne flagi|Umożliwia określenie dodatkowych opcji wiersza polecenia kompilatora.|

## <a name="code-and-text-editor-features"></a>Funkcje edytora kodu i tekstu

Następujące funkcje programu Visual Studio Code i edytorów tekstu są obsługiwane w języku F #:

|Cechy|Opis|Obsługiwane w języku F #?|
|-------|-----------|----------------|
|Automatycznie komentarz|Umożliwia komentowanie lub usuwanie komentarzy do sekcji kodu.|Tak|
|Automatycznie Formatuj|Formatuje kod ze standardowym wcięciem i stylem.|Nie|
|Zakładki|Umożliwia zapisywanie miejsc w edytorze.|Tak|
|Zmień wcięcie|Zwiększa wcięcie wybranych wierszy lub usuwa z nich wcięcia.|Tak|
|Inteligentne wcięcia|Automatycznie zwiększa wcięcie i cofa wcięcie kursora zgodnie z regułami określania zakresu języka F #.|Tak|
|[Znajdowanie i zastępowanie tekstu](finding-and-replacing-text.md)|Umożliwia wyszukiwanie w pliku, projekcie lub rozwiązaniu, a także może spowodować zmianę tekstu.|Tak|
|Przejdź do definicji interfejsu API platformy .NET|Po umieszczeniu kursora w interfejsie API platformy .NET program wyświetla kod generowany na podstawie metadanych platformy .NET.|Nie|
|Przejdź do definicji dla interfejsu API zdefiniowanego przez użytkownika|Gdy kursor znajduje się w zdefiniowanej jednostce programu, przenosi kursor do lokalizacji w kodzie, w którym zdefiniowano jednostkę.|Tak|
|Przejdź do wiersza|Umożliwia przejście do określonego wiersza w pliku według numeru wiersza.|Tak|
|Paski nawigacyjne w górnej części pliku|Umożliwia przechodzenie do lokalizacji w kodzie, przez, na przykład, nazwa funkcji.|Tak|
|Wskazówki dotyczące struktury bloków|Pokazuje wskazówki wskazujące zakresy języka F #, które można umieścić na początku dla wersji zapoznawczej.|Tak|
|[Tworzenie konspektu](outlining.md)|Umożliwia zwinięcie sekcji kodu w celu utworzenia bardziej kompaktowego widoku.|Tak|
|Na tabulatory|Konwertuje spacje na tabulatory.|Tak|
|Kolorowanie typów|Pokazuje zdefiniowane nazwy typów w specjalnym kolorze.|Tak|
|Szybkie znajdowanie. Zobacz szybkie znajdowanie, Znajdowanie i zamienianie okna.|Umożliwia wyszukiwanie w pliku lub projekcie.|Tak|
|**Ctrl** + **kliknij** , aby przejść do definicji|Umożliwia zatrzymanie klawisza **Ctrl** i kliknięcie symbolu F # w celu wywołania przejdź do definicji.|Tak|
|Przejdź do definicji z sekcji szybkich informacji|Symbole, które można klikać w obrębie etykietek narzędzi, które wywołują przejdź do definicji.|Tak|
|Przejdź do wszystkiego|Włącza globalną nawigację dopasowania dla wszystkich konstrukcji F # za pośrednictwem **Ctrl** + **T**.|Tak|
|Nazwa wbudowana|Zmienia nazwę wszystkich wystąpień symbolu w tekście.|Tak|
|Znajdź wszystkie odwołania|Znajduje wszystkie wystąpienia symbolu w bazie kodu.|Tak|
|Uprość poprawkę kodu nazw|Usuwa zbędne kwalifikatory dla symboli języka F #.|Tak|
|Usuń nieużywaną `open` poprawkę kodu instrukcji|Usuwa wszystkie zbędne `open` instrukcje w dokumencie.|Tak|
|Poprawka nieużywanego kodu wartości|Sugeruje zmianę nazwy nieużywanego identyfikatora na podkreślenie.|Tak|

Aby uzyskać ogólne informacje na temat edytowania kodu w programie Visual Studio i funkcji edytora tekstów, zobacz [pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>Funkcje IntelliSense

W poniższej tabeli zestawiono funkcje IntelliSense obsługiwane i nieobsługiwane w języku F #:

|Cechy|Opis|Obsługiwane w języku F #?|
|-------|-----------|----------------|
|Automatycznie Implementuj interfejsy|Generuje fragmenty kodu dla metod interfejsu.|Tak|
|Fragmenty kodu|Wprowadza kod z biblioteki wspólnych konstrukcji kodowania do tematów.|Nie|
|Dokończ wyraz|Zapisuje tekst, wykonując słowa i nazwy podczas wpisywania.|Tak|
|Automatyczne uzupełnianie|Po włączeniu powoduje, że uzupełnianie wyrazów wybiera pierwsze dopasowanie podczas pisania, zamiast czekać na wybranie jednego lub naciśnięcie klawisza **Ctrl** + **Space**.|Tak|
|Ukończenie oferty dla symboli w nieotwartych przestrzeniach nazw|W przypadku automatycznego uzupełniania sugerowany symbol, który znajduje się w nieotwartym obszarze nazw, jest proponowany, a oferta została zakończona z odpowiednią `open` instrukcją w przypadku wybrania.|Tak|
|Generuj elementy kodu|Umożliwia generowanie kodu szczątkowego dla różnych konstrukcji.|Nie|
|Lista składników|Po wpisaniu operatora dostępu do elementu członkowskiego (.), pokazuje elementy członkowskie dla danego typu.|Tak|
|Organizuj przy użyciu/Otwórz|Organizuje przestrzenie nazw, do których odwołują się instrukcje **using** w języku C# lub **otwierają** dyrektywy w języku F #.|Nie|
|Informacje o parametrach|Wyświetla przydatne informacje dotyczące parametrów podczas wpisywania wywołania funkcji.|Tak|
|Szybkie informacje|Wyświetla kompletną deklarację dla dowolnego identyfikatora w kodzie.|Tak|
|Automatyczne uzupełnianie nawiasów klamrowych|Automatycznie wykonuje konstrukcje składniowe w postaci nawiasów klamrowych F # w sposób transakcyjny.|Tak|

Aby uzyskać ogólne informacje na temat technologii IntelliSense, zobacz [Korzystanie z funkcji IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Funkcje debugowania

Poniższa tabela zawiera podsumowanie funkcji dostępnych podczas debugowania kodu F #:

|Cechy|Opis|Obsługiwane w języku F #?|
|-------|-----------|----------------|
|okno zmiennych automatycznych|Wyświetla zmienne automatyczne lub tymczasowe.|Nie|
|Punkty przerwania|Umożliwia wstrzymanie wykonywania kodu w określonych punktach podczas debugowania.|Tak|
|Warunkowe punkty przerwania|Włącza punkty przerwania, które testują warunek określający, czy wykonywanie powinno zostać wstrzymane.|Tak|
|Edytuj i kontynuuj|Umożliwia modyfikowanie i kompilowanie kodu w trakcie debugowania działającego programu bez zatrzymywania i ponownego uruchamiania debugera.|Nie|
|Ewaluatora wyrażeń|Oblicza i wykonuje kod w czasie wykonywania.|Nie, ale można używać ewaluatora wyrażeń języka C#, chociaż należy użyć składni języka C#.|
|Debugowanie historyczne|Umożliwia wkroczenie do wykonanego wcześniej kodu.|Tak|
|okno zmiennych lokalnych|Pokazuje zdefiniowane lokalnie wartości i zmienne.|Tak|
|Uruchom do kursora|Umożliwia wykonywanie kodu do momentu, aż wiersz zawierający kursor zostanie osiągnięty.|Tak|
|Wkrocz do|Umożliwia wykonywanie i przechodzenie do dowolnego wywołania funkcji.|Tak|
|Przekrocz nad|Umożliwia wykonywanie z wyprzedzeniem bieżącej ramki stosu i przechodzenie do poprzedniego wywołania funkcji.|Tak|

Aby uzyskać ogólne informacje na temat debugera programu Visual Studio, zobacz [debugowanie w programie Visual Studio](../debugger/index.yml).

## <a name="additional-tools"></a>Dodatkowe narzędzia

Poniższa tabela zawiera podsumowanie obsługi języka F # w narzędziach Visual Studio.

|Narzędzie|Opis|Obsługiwane w języku F #?|
|----|-----------|----------------|
|Hierarchia wywołań|Wyświetla zagnieżdżoną strukturę wywołań funkcji w kodzie.|Nie|
|Metryki kodów|Zbiera informacje o kodzie, takie jak liczby wierszy.|Nie|
|Widok klas|Przedstawia widok kodu w projekcie oparty na typie.|Nie|
|[Okno listy błędów](reference/error-list-window.md)|Pokazuje listę błędów w kodzie.|Tak|
|[Interaktywny F#](/dotnet/fsharp/tutorials/fsharp-interactive/)|Umożliwia wpisywanie (lub kopiowanie i wklejanie) kodu F # i natychmiastowe uruchamianie go niezależnie od kompilowania projektu. Okno F# Interactive to odczytana, oszacowana i drukowana pętla (REPL).|Tak|
|Przeglądarka obiektów|Umożliwia wyświetlanie typów w zestawie.|Typy języka F #, które pojawiają się w skompilowanych zestawach, nie są wyświetlane dokładnie podczas ich tworzenia. Można przeglądać skompilowaną reprezentację typów języka F #, ale nie można wyświetlać typów, które są wyświetlane w języku F #.|
|[Okno wyniku](reference/output-window.md)|Wyświetla dane wyjściowe kompilacji.|Tak|
|Analiza wydajności|Oferuje narzędzia do mierzenia wydajności kodu.|Tak|
|Okno właściwości|Wyświetla i umożliwia edytowanie właściwości obiektu w środowisku programistycznym, które ma fokus.|Tak|
|Eksplorator serwera|Zapewnia sposoby współpracy z różnymi zasobami serwera.|Tak|
|Eksplorator rozwiązań|Umożliwia wyświetlanie projektów i plików oraz zarządzanie nimi.|Tak|
|Lista zadań|Umożliwia zarządzanie elementami roboczymi związanymi z kodem.|Nie|
|Projekty testowe|Oferuje funkcje, które ułatwiają testowanie kodu.|Nie|
|Przybornik|Wyświetla karty zawierające przeciągane obiekty, takie jak kontrolki i sekcje tekstu lub kodu.|Tak|

## <a name="see-also"></a>Zobacz też

- [Przewodnik po języku F # (.NET Framework)](/dotnet/fsharp/)
- [Wprowadzenie do języka F # w programie Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)
