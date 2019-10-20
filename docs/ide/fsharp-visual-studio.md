---
title: Narzędzia języka F#
description: Dowiedz się, które funkcje programu Visual Studio F#są obsługiwane w programie.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 176504ceb7c80a36028e7d5f1806aa598cdf708e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645366"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Programowanie za pomocą F# wizualizacji w Visual Studio

Ten artykuł zawiera informacje o funkcjach programu Visual F# Studio na potrzeby programowania.

## <a name="install-f-support"></a>Zainstaluj F# obsługę

Aby rozpocząć tworzenie F# w programie Visual Studio, najpierw zainstaluj obciążenie **Programowanie aplikacji klasycznych platformy .NET** , jeśli nie zostało to jeszcze zrobione. Możesz zainstalować obciążenia programu Visual Studio za pomocą Instalator programu Visual Studio, które można otworzyć, wybierając pozycję **narzędzia**  > **Pobierz narzędzia i funkcje**.

![Obciążenie Programowanie aplikacji klasycznych dla platformy .NET w programie Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>F#funkcje projektu

Różne szablony projektów i elementów są dostępne dla F# programu Visual Studio. Na poniższej ilustracji przedstawiono niektóre szablony F# projektów dla platformy .NET Core i .NET standard:

![F#Szablony projektów w programie Visual Studio](media/fsharp-project-templates.png)

Na poniższej ilustracji przedstawiono niektóre szablony F# elementów:

![F#szablony elementów w programie Visual Studio](media/fsharp-item-templates.png)

Aby uzyskać więcej informacji na temat szablonów elementów na potrzeby dostępu do danych, zobacz [ F# dostawcy typów](/dotnet/fsharp/tutorials/type-providers/index).

Poniższa tabela zawiera podsumowanie funkcji właściwości projektu dla F#:

|Ustawienie projektu|Obsługiwane w F#?|Uwagi|
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

**Projektant projektu** składa się z kilku stron właściwości projektu pogrupowanych według pokrewnych funkcji. Strony dostępne dla F# projektów są głównie podzbiorem tych dostępnych dla innych języków i są opisane w poniższej tabeli. Linki są dostarczane do odpowiedniej C# strony **projektanta projektu** .

|Strona projektanta projektu|Linki pokrewne|Opis|
| - |-------------|-----------|
|Aplikacja|[Strona aplikacji, Projektant projektu](reference/application-page-project-designer-csharp.md)|Umożliwia określenie ustawień i właściwości na poziomie aplikacji, takich jak to, czy tworzysz bibliotekę lub plik wykonywalny, która wersja programu .NET jest przeznaczona dla aplikacji, oraz informacje o tym, gdzie są przechowywane pliki zasobów używane przez aplikację.|
|Kompilacja|[Strona kompilacja, Projektant projektu](reference/build-page-project-designer-csharp.md)|Umożliwia sterowanie sposobem kompilowania kodu.|
|Zdarzenia kompilacji|[Strona zdarzenia kompilacji, Projektant projektu](reference/build-events-page-project-designer-csharp.md)|Umożliwia określenie poleceń do uruchomienia przed kompilacją lub po niej.|
|Debugowanie|[Strona debugowania, Projektant projektu](reference/debug-page-project-designer.md)|Umożliwia sterowanie sposobem uruchamiania aplikacji podczas debugowania. Dotyczy to również poleceń, które mają być używane, i zawartości katalogu początkowego aplikacji oraz wszelkich specjalnych trybów debugowania, które mają być włączone, takich jak kod natywny i SQL.|
|Pakiet (tylko .NET SDK)|Brak|Umożliwia definiowanie metadanych pakietu NuGet podczas publikowania jako pakiet NuGet.|
|Ścieżki odwołań|[Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md)|Pozwala określić, gdzie mają być wyszukiwane zestawy, od których zależy kod.|
|Zasoby (tylko zestaw SDK platformy .NET)|Brak|Umożliwia generowanie domyślnego pliku zasobów i zarządzanie nim.|

### <a name="f-specific-settings"></a>F#Ustawienia specyficzne dla

Poniższa tabela zawiera podsumowanie ustawień, które są specyficzne F#dla:

|Strona projektanta projektu|Ustawienie|Opis|
| - |-------|-----------|
|Kompilacja|Generuj wywołania tail|W przypadku wybrania tej wartości program umożliwia korzystanie z instrukcji języka pośredniego (MSIL) firmy Microsoft. Powoduje to, że ramka stosu zostanie ponownie użyta na potrzeby funkcji cyklicznych. Odpowiednik opcji kompilatora `--tailcalls`.|
|Kompilacja|Inne flagi|Umożliwia określenie dodatkowych opcji wiersza polecenia kompilatora.|

## <a name="code-and-text-editor-features"></a>Funkcje edytora kodu i tekstu

Następujące funkcje programu Visual Studio Code i edytorów tekstu są obsługiwane w programie F#:

|Funkcja|Opis|Obsługiwane w F#?|
|-------|-----------|----------------|
|Automatycznie komentarz|Umożliwia komentowanie lub usuwanie komentarzy do sekcji kodu.|Tak|
|Automatycznie Formatuj|Formatuje kod ze standardowym wcięciem i stylem.|Nie|
|Zakładki|Umożliwia zapisywanie miejsc w edytorze.|Tak|
|Zmień wcięcie|Zwiększa wcięcie wybranych wierszy lub usuwa z nich wcięcia.|Tak|
|Inteligentne wcięcia|Automatycznie zwiększa wcięcie i cofa wcięcie kursora zgodnie z F# regułami określania zakresu.|Tak|
|[Znajdowanie i zastępowanie tekstu](finding-and-replacing-text.md)|Umożliwia wyszukiwanie w pliku, projekcie lub rozwiązaniu, a także może spowodować zmianę tekstu.|Tak|
|Przejdź do definicji interfejsu API platformy .NET|Po umieszczeniu kursora w interfejsie API platformy .NET program wyświetla kod generowany na podstawie metadanych platformy .NET.|Nie|
|Przejdź do definicji dla interfejsu API zdefiniowanego przez użytkownika|Gdy kursor znajduje się w zdefiniowanej jednostce programu, przenosi kursor do lokalizacji w kodzie, w którym zdefiniowano jednostkę.|Tak|
|Przejdź do wiersza|Umożliwia przejście do określonego wiersza w pliku według numeru wiersza.|Tak|
|Paski nawigacyjne w górnej części pliku|Umożliwia przechodzenie do lokalizacji w kodzie, przez, na przykład, nazwa funkcji.|Tak|
|Wskazówki dotyczące struktury bloków|Pokazuje wskazówki wskazujące F# zakresy, które mogą być przesuwane w wersji zapoznawczej.|Tak|
|[Obramowanie](outlining.md)|Umożliwia zwinięcie sekcji kodu w celu utworzenia bardziej kompaktowego widoku.|Tak|
|Na tabulatory|Konwertuje spacje na tabulatory.|Tak|
|Kolorowanie typów|Pokazuje zdefiniowane nazwy typów w specjalnym kolorze.|Tak|
|Szybkie znajdowanie. Zobacz szybkie znajdowanie, Znajdowanie i zamienianie okna.|Umożliwia wyszukiwanie w pliku lub projekcie.|Tak|
|**Naciśnij klawisz Ctrl** , +**kliknij** , aby przejść do definicji|Umożliwia zatrzymanie klawisza **Ctrl** i kliknięcie F# symbolu do wywołania przejdź do definicji.|Tak|
|Przejdź do definicji z sekcji szybkich informacji|Symbole, które można klikać w obrębie etykietek narzędzi, które wywołują przejdź do definicji.|Tak|
|Przejdź do wszystkiego|Włącza globalną nawigację dopasowania dla wszystkich F# konstrukcji za pośrednictwem **kombinacji klawiszy CTRL** +**t**.|Tak|
|Nazwa wbudowana|Zmienia nazwę wszystkich wystąpień symbolu w tekście.|Tak|
|Znajdź wszystkie odwołania|Znajduje wszystkie wystąpienia symbolu w bazie kodu.|Tak|
|Uprość poprawkę kodu nazw|Usuwa zbędne kwalifikatory F# dla symboli.|Tak|
|Usuń nieużywaną poprawkę kodu instrukcji `open`|Usuwa wszystkie zbędne instrukcje `open` w dokumencie.|Tak|
|Poprawka nieużywanego kodu wartości|Sugeruje zmianę nazwy nieużywanego identyfikatora na podkreślenie.|Tak|

Aby uzyskać ogólne informacje na temat edytowania kodu w programie Visual Studio i funkcji edytora tekstów, zobacz [pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>Funkcje IntelliSense

W poniższej tabeli zestawiono funkcje IntelliSense obsługiwane i nieobsługiwane w F#programie:

|Funkcja|Opis|Obsługiwane w F#?|
|-------|-----------|----------------|
|Automatycznie Implementuj interfejsy|Generuje fragmenty kodu dla metod interfejsu.|Tak|
|Fragmenty kodu|Wprowadza kod z biblioteki wspólnych konstrukcji kodowania do tematów.|Nie|
|Dokończ wyraz|Zapisuje tekst, wykonując słowa i nazwy podczas wpisywania.|Tak|
|Automatyczne uzupełnianie|Po włączeniu powoduje, że uzupełnianie wyrazów wybiera pierwsze dopasowanie podczas pisania, zamiast czekać na wybranie jednego lub naciśnięcie klawisza **Ctrl** +**miejsce**.|Tak|
|Ukończenie oferty dla symboli w nieotwartych przestrzeniach nazw|W przypadku automatycznego uzupełniania sugerowany symbol, który znajduje się w nieotwartym obszarze nazw, jest proponowany, a oferta została wykonana z odpowiadającą jej instrukcją `open` po zaznaczeniu.|Tak|
|Generuj elementy kodu|Umożliwia generowanie kodu szczątkowego dla różnych konstrukcji.|Nie|
|Lista składników|Po wpisaniu operatora dostępu do elementu członkowskiego (.), pokazuje elementy członkowskie dla danego typu.|Tak|
|Organizuj przy użyciu/Otwórz|Organizuje przestrzenie nazw, do których C# odwołują się instrukcje F# **using** w lub **otwierają** dyrektywy w.|Nie|
|Informacje o parametrach|Wyświetla przydatne informacje dotyczące parametrów podczas wpisywania wywołania funkcji.|Tak|
|Szybkie informacje|Wyświetla kompletną deklarację dla dowolnego identyfikatora w kodzie.|Tak|
|Automatyczne uzupełnianie nawiasów klamrowych|Automatycznie uzupełnia F# w sposób transakcyjny konstrukcje składniowe w nawiasach klamrowych.|Tak|

Aby uzyskać ogólne informacje na temat technologii IntelliSense, zobacz [Korzystanie z funkcji IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Funkcje debugowania

Poniższa tabela zawiera podsumowanie funkcji dostępnych podczas debugowania F# kodu:

|Funkcja|Opis|Obsługiwane w F#?|
|-------|-----------|----------------|
|okno zmiennych automatycznych|Wyświetla zmienne automatyczne lub tymczasowe.|Nie|
|Punkty przerwania|Umożliwia wstrzymanie wykonywania kodu w określonych punktach podczas debugowania.|Tak|
|Warunkowe punkty przerwania|Włącza punkty przerwania, które testują warunek określający, czy wykonywanie powinno zostać wstrzymane.|Tak|
|Edytuj i kontynuuj|Umożliwia modyfikowanie i kompilowanie kodu w trakcie debugowania działającego programu bez zatrzymywania i ponownego uruchamiania debugera.|Nie|
|Ewaluatora wyrażeń|Oblicza i wykonuje kod w czasie wykonywania.|Nie, ale można C# używać ewaluatora wyrażeń, chociaż należy użyć C# składni.|
|Debugowanie historyczne|Umożliwia wkroczenie do wykonanego wcześniej kodu.|Tak|
|okno zmiennych lokalnych|Pokazuje zdefiniowane lokalnie wartości i zmienne.|Tak|
|Uruchom do kursora|Umożliwia wykonywanie kodu do momentu, aż wiersz zawierający kursor zostanie osiągnięty.|Tak|
|Wkrocz do|Umożliwia wykonywanie i przechodzenie do dowolnego wywołania funkcji.|Tak|
|Przekrocz nad|Umożliwia wykonywanie z wyprzedzeniem bieżącej ramki stosu i przechodzenie do poprzedniego wywołania funkcji.|Tak|

Aby uzyskać ogólne informacje na temat debugera programu Visual Studio, zobacz [debugowanie w programie Visual Studio](../debugger/index.yml).

## <a name="additional-tools"></a>Dodatkowe narzędzia

Poniższa tabela zawiera podsumowanie obsługi programu F# w narzędziach Visual Studio.

|Narzędzie|Opis|Obsługiwane w F#?|
|----|-----------|----------------|
|Hierarchia wywołań|Wyświetla zagnieżdżoną strukturę wywołań funkcji w kodzie.|Nie|
|Metryki kodów|Zbiera informacje o kodzie, takie jak liczby wierszy.|Nie|
|Widok klas|Przedstawia widok kodu w projekcie oparty na typie.|Nie|
|[Okno Lista błędów](reference/error-list-window.md)|Pokazuje listę błędów w kodzie.|Tak|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Umożliwia wpisywanie (lub kopiowanie i wklejanie) F# kodu i natychmiastowe uruchamianie go niezależnie od kompilowania projektu. Okno F# interaktywne to odczytana, oszacowana i drukowana pętla (REPL).|Tak|
|Przeglądarka obiektów|Umożliwia wyświetlanie typów w zestawie.|F#typy, które pojawiają się w skompilowanych zestawach, nie są wyświetlane dokładnie podczas ich tworzenia. Można przeglądać skompilowaną reprezentację F# typów, ale nie można wyświetlić typów, z F#których się pojawiają.|
|[Okno danych wyjściowych](reference/output-window.md)|Wyświetla dane wyjściowe kompilacji.|Tak|
|Analiza wydajności|Oferuje narzędzia do mierzenia wydajności kodu.|Tak|
|Okno właściwości|Wyświetla i umożliwia edytowanie właściwości obiektu w środowisku programistycznym, które ma fokus.|Tak|
|Server Explorer|Zapewnia sposoby współpracy z różnymi zasobami serwera.|Tak|
|Eksplorator rozwiązań|Umożliwia wyświetlanie projektów i plików oraz zarządzanie nimi.|Tak|
|Lista zadań|Umożliwia zarządzanie elementami roboczymi związanymi z kodem.|Nie|
|Projekty testowe|Oferuje funkcje, które ułatwiają testowanie kodu.|Nie|
|Przybornik|Wyświetla karty zawierające przeciągane obiekty, takie jak kontrolki i sekcje tekstu lub kodu.|Tak|

## <a name="see-also"></a>Zobacz także

- [F#Przewodnik (.NET Framework)](/dotnet/fsharp/)
- [Wprowadzenie F# do programu Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)