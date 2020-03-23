---
title: Narzędzia języka F#
description: Dowiedz się, które funkcje programu Visual Studio są obsługiwane w języku F#.
ms.date: 07/11/2018
ms.topic: reference
helpviewer_keywords:
- F# features [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 75ebee68bf76a4dd5419942f79a3207c29673134
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565243"
---
# <a name="develop-with-visual-f-in-visual-studio"></a>Tworzenie za pomocą języka Visual F# w programie Visual Studio

Ten artykuł zawiera informacje o funkcjach programu Visual Studio dla rozwoju języka F#.

## <a name="install-f-support"></a>Obsługa instalacji języka F#

Aby opracować za pomocą języka F# w programie Visual Studio, najpierw zainstaluj obciążenie **programistyczne pulpitu .NET,** jeśli jeszcze tego nie zrobiłeś. Obciążenia programu Visual Studio są instalowane za pośrednictwem instalatora programu Visual Studio, który można otworzyć, wybierając **pozycję Narzędzia** > **Pobierz narzędzia i funkcje**.

![Obciążenie programistyczne pulpitu platformy .NET w programie Visual Studio](media/dotnet-desktop-development-workload.png)

## <a name="f-project-features"></a>Funkcje projektu języka F#

Różne szablony projektu i elementów są dostępne dla języka F# w programie Visual Studio. Na poniższej ilustracji przedstawiono niektóre szablony projektów języka F# dla platformy .NET Core i .NET Standard:

![Szablony projektów języka F# w programie Visual Studio](media/fsharp-project-templates.png)

Na poniższej ilustracji przedstawiono niektóre szablony elementów języka F#:

![Szablony elementów języka F# w programie Visual Studio](media/fsharp-item-templates.png)

Aby uzyskać więcej informacji na temat szablonów elementów dostępu do danych, zobacz [Dostawcy typów języka F#.](/dotnet/fsharp/tutorials/type-providers/index)

W poniższej tabeli podsumowano funkcje we właściwościach projektu dla języka F#:

|Ustawienie projektu|Obsługiwane w języku F#?|Uwagi|
|---------------|----------------|-----|
|Pliki zasobów|Tak||
|Ustawienia kompilacji, debugowania i odwołań|Tak||
|Wielowersyjność kodu|Tak||
|Ikona i manifest|Nie|Dostępne za pośrednictwem opcji wiersza polecenia kompilatora.|
|ASP.NET Usługi klienta|Nie||
|ClickOnce|Nie|Użyj projektu klienta w innym języku .NET, jeśli ma to zastosowanie.|
|Silne nazewnictwo|Nie|Dostępne za pośrednictwem opcji wiersza polecenia kompilatora.|
|Publikowanie i przechowywanie wersji zestawu|Nie||
|Analiza kodu|Nie|Narzędzia analizy kodu można uruchamiać ręcznie lub jako część polecenia po kompilacji.|
|Zabezpieczenia (zmiana poziomów zaufania)|Nie||

## <a name="project-designer"></a>Projektant projektu

**Projektant projektu** składa się z kilku stron właściwości projektu pogrupowanych według powiązanych funkcji. Strony dostępne dla projektów Języka F# są głównie podzbiór tych dostępnych dla innych języków i są opisane w poniższej tabeli. Łącza są dostarczane do odpowiedniej strony **projektanta projektu** w języku C#.

|Strona Projektanta projektu|Powiązane linki|Opis|
| - |-------------|-----------|
|Aplikacja|[Strona aplikacji, Projektant projektu](reference/application-page-project-designer-csharp.md)|Umożliwia określenie ustawień i właściwości na poziomie aplikacji, takich jak tworzenie biblioteki lub pliku wykonywalnego, jaka wersja .NET obiektów docelowych aplikacji i informacje o tym, gdzie są przechowywane pliki zasobów używane przez aplikację.|
|Kompilacja|[Strona kompilacji, Projektant projektu](reference/build-page-project-designer-csharp.md)|Umożliwia kontrolowanie sposobu kompilowania kodu.|
|Tworzenie zdarzeń|[Strona tworzenia zdarzeń, Projektant projektu](reference/build-events-page-project-designer-csharp.md)|Umożliwia określenie poleceń do uruchomienia przed lub po kompilacji.|
|Debugowanie|[Strona debugowania, Projektant projektu](reference/debug-page-project-designer.md)|Umożliwia kontrolowanie sposobu działania aplikacji podczas debugowania. Obejmuje to, jakie polecenia do użycia i co jest katalog początkowy aplikacji i wszystkie specjalne tryby debugowania, które chcesz włączyć, takich jak kod macierzysty i SQL.|
|Pakiet (tylko pakiet SDK.NET)|Nie dotyczy|Umożliwia zdefiniowanie metadanych pakietu NuGet podczas publikowania jako pakietu NuGet.|
|Ścieżki referencyjne|[Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md)|Umożliwia określenie, gdzie należy wyszukiwać zestawy, od których zależy kod.|
|Zasoby (tylko SDK.NET)|Nie dotyczy|Umożliwia generowanie domyślnego pliku zasobów i zarządzanie nim.|

### <a name="f-specific-settings"></a>Ustawienia specyficzne dla języka F#

W poniższej tabeli podsumowano ustawienia specyficzne dla języka F#:

|Strona Projektanta projektu|Ustawienie|Opis|
| - |-------|-----------|
|Kompilacja|Generowanie wywołań ogonowych|Jeśli ta opcja jest zaznaczona, umożliwia użycie instrukcji języka pośredniego firmy Microsoft (MSIL). Powoduje to, że ramka stosu ma być ponownie używana dla funkcji cyklicznych ogona. Odpowiednik opcji `--tailcalls` kompilatora.|
|Kompilacja|Inne flagi|Umożliwia określenie dodatkowych opcji wiersza polecenia kompilatora.|

## <a name="code-and-text-editor-features"></a>Funkcje edytora kodu i tekstu

Następujące funkcje kodu programu Visual Studio i edytorów tekstu są obsługiwane w języku F#:

|Funkcja|Opis|Obsługiwane w języku F#?|
|-------|-----------|----------------|
|Automatyczne komentowanie|Umożliwia komentowanie lub odkomentowywać sekcje kodu.|Tak|
|Automatyczne formatowanie|Formatuje kod ze standardowym wcięciem i stylem.|Nie|
|Zakładki|Umożliwia zapisywanie miejsc w edytorze.|Tak|
|Zmiana wcięcie|Wcięcie lub jednedyczki zaznaczone linie.|Tak|
|Inteligentne wcięcie|Automatycznie wcina i odcina kursor zgodnie z regułami zakresu F#.|Tak|
|[Znajdowanie i zastępowanie tekstu](finding-and-replacing-text.md)|Umożliwia wyszukiwanie w pliku, projekcie lub rozwiązaniu i potencjalnie zmieniać tekst.|Tak|
|Przejdź do definicji interfejsu API platformy .NET|Gdy kursor jest umieszczony w interfejsie API platformy .NET, pokazuje kod wygenerowany z metadanych platformy .NET.|Nie|
|Przejdź do definicji interfejsu API zdefiniowanego przez użytkownika|Gdy kursor znajduje się w zdefiniowanej encji programu, przenosi kursor do lokalizacji w kodzie, w której zdefiniowano encję.|Tak|
|Przejdź do wiersza|Umożliwia przejść do określonego wiersza w pliku według numeru wiersza.|Tak|
|Paski nawigacyjne u góry pliku|Umożliwia przejście do lokalizacji w kodzie, na przykład nazwa funkcji.|Tak|
|Wskazówki dotyczące struktury bloków|Pokazuje wytyczne wskazujące zakresy języka F#, które można najechać kursorem na podgląd.|Tak|
|[Tworzenie konspektu](outlining.md)|Umożliwia zwinięcie sekcji kodu w celu utworzenia widoku bardziej kompaktowego.|Tak|
|Tabify (Tabify)|Konwertuje spacje na karty.|Tak|
|Kolorowanie typów|Pokazuje zdefiniowane nazwy typów w specjalnym kolorze.|Tak|
|Szybkie znajdowanie. Zobacz Szybkie znajdowanie, znajdowanie i zamienianie okna.|Umożliwia wyszukiwanie w pliku lub projekcie.|Tak|
|**Ctrl**+**kliknij,** aby przejść do definicji|Umożliwia przytrzymanie **ctrl** i kliknij symbol F#, aby wywołać Przejdź do definicji.|Tak|
|Przejdź do definicji z QuickInfo|Symbole klikalne wewnątrz etykietek narzędzi, które wywołują Przejdź do definicji.|Tak|
|Przejdź do wszystkich|Umożliwia globalną nawigację dopasowywania rozmytego dla wszystkich konstrukcji języka F# za pośrednictwem **ctrl**+**T**.|Tak|
|Zmiana nazwy w linii|Zmienia nazwę wszystkich wystąpień symbolu w linii.|Tak|
|Znajdź wszystkie odwołania|Znajduje wszystkie wystąpienia symbolu w bazie kodu.|Tak|
|Uproszczenie poprawki kodu nazwy|Usuwa niepotrzebne kwalifikatory dla symboli Języka F#.|Tak|
|Usuń nieużywane `open` poprawki kodu instrukcji|Usuwa wszystkie `open` niepotrzebne instrukcje w dokumencie.|Tak|
|Nieużywane poprawki kodu wartości|Sugeruje zmianę nazwy nieużytego identyfikatora w celu podkreślenia.|Tak|

Aby uzyskać ogólne informacje dotyczące edytowania kodu w programie Visual Studio i funkcji edytora tekstu, zobacz [Pisanie kodu w edytorze](writing-code-in-the-code-and-text-editor.md).

## <a name="intellisense-features"></a>Funkcje IntelliSense

W poniższej tabeli podsumowano funkcje intellisense obsługiwane i nie obsługiwane w języku F#:

|Funkcja|Opis|Obsługiwane w języku F#?|
|-------|-----------|----------------|
|Automatyczne implementowanie interfejsów|Generuje wycinki kodu dla metod interfejsu.|Tak|
|Fragmenty kodu|Wstrzykuje kod z biblioteki typowych konstrukcji kodowania do tematów.|Nie|
|Dokończ wyraz|Zapisuje wpisywanie, wypełniając słowa i nazwy podczas pisania.|Tak|
|Automatyczne uzupełnianie|Gdy ta opcja jest włączona, powoduje, że zakończenie wyrazu powoduje wybranie pierwszego dopasowania podczas pisania, zamiast oczekiwania na wybranie jednego lub**naciśnięcie klawisza** **Ctrl**+Space .|Tak|
|Uzupełnianie oferty dla symboli w nieotwartych przestrzeniach nazw|W przypadku automatycznego uzupełniania zalecany jest pasujący symbol, który znajduje się w `open` nieotwartej przestrzeni nazw, oferując uzupełnienie odpowiedniej instrukcji po wybraniu.|Tak|
|Generowanie elementów kodu|Umożliwia generowanie kodu skrótowego dla różnych konstrukcji.|Nie|
|Lista składników|Po wpisaniu operatora dostępu elementu członkowskiego (.), pokazuje elementy członkowskie dla typu.|Tak|
|Organizowanie usings/Open|Organizuje przestrzenie nazw, do których odwołuje się **użycie** instrukcji w języku C# lub **otwartych** dyrektyw w języku F#.|Nie|
|Informacje o parametrach|Pokazuje przydatne informacje o parametrach podczas wpisywania wywołania funkcji.|Tak|
|Szybkie informacje|Wyświetla pełną deklarację dla dowolnego identyfikatora w kodzie.|Tak|
|Automatyczne uzupełnianie nawiasów klamrowych|Automatycznie kończy F# klamry jak konstrukcje składni w sposób transakcyjny.|Tak|

Aby uzyskać ogólne informacje na temat programu IntelliSense, zobacz [Korzystanie z programu IntelliSense](using-intellisense.md).

## <a name="debugging-features"></a>Funkcje debugowania

W poniższej tabeli podsumowano funkcje, które są dostępne podczas debugowania kodu Języka F#:

|Funkcja|Opis|Obsługiwane w języku F#?|
|-------|-----------|----------------|
|okno zmiennych automatycznych|Pokazuje zmienne automatyczne lub tymczasowe.|Nie|
|Punkty przerwania|Umożliwia wstrzymanie wykonywania kodu w określonych punktach podczas debugowania.|Tak|
|Warunkowe punkty przerwania|Włącza punkty przerwania, które testują warunek, który określa, czy wykonanie należy wstrzymać.|Tak|
|Edytuj i kontynuuj|Umożliwia modyfikację i skompilowanie kodu podczas debugowania uruchomionego programu bez zatrzymywania i ponownego uruchamiania debugera.|Nie|
|Wyrażenie|Ocenia i wykonuje kod w czasie wykonywania.|Nie, ale można użyć ewaluatora wyrażenia C#, chociaż należy użyć składni języka C#.|
|Debugowanie historyczne|Umożliwia przejście do wcześniej wykonanego kodu.|Tak|
|okno zmiennych lokalnych|Pokazuje lokalnie zdefiniowane wartości i zmienne.|Tak|
|Uruchom do kursora|Umożliwia wykonywanie kodu, dopóki nie zostanie osiągnięty wiersz zawierający kursor.|Tak|
|Wejdź do|Umożliwia wcześniejsze wykonanie i przejście do dowolnego wywołania funkcji.|Tak|
|Krok nad|Umożliwia wcześniejsze wykonanie w bieżącej ramce stosu i przejście poza dowolne wywołanie funkcji.|Tak|

Aby uzyskać ogólne informacje na temat debugera programu Visual Studio, zobacz [Debugowanie w programie Visual Studio](../debugger/index.yml).

## <a name="additional-tools"></a>Dodatkowe narzędzia

W poniższej tabeli podsumowano obsługę języka F# w narzędziach programu Visual Studio.

|Narzędzie|Opis|Obsługiwane w języku F#?|
|----|-----------|----------------|
|Hierarchia wywołań|Wyświetla zagnieżdżoną strukturę wywołań funkcji w kodzie.|Nie|
|Metryki kodów|Zbiera informacje o kodzie, takie jak liczba wierszy.|Nie|
|Widok klas|Udostępnia widok kodu w projekcie oparty na typie.|Nie|
|[Okno listy błędów](reference/error-list-window.md)|Pokazuje listę błędów w kodzie.|Tak|
|[F# Interactive](/dotnet/fsharp/tutorials/fsharp-interactive/)|Umożliwia wpisanie (lub skopiować i wkleić) kod F# i uruchomić go natychmiast, niezależnie od tworzenia projektu. Okno Interaktywne F# jest odczytem, oceną, pętlą drukowania (REPL).|Tak|
|Przeglądarka obiektów|Umożliwia wyświetlanie typów w złożeniu.|Typy F#, ponieważ pojawiają się w skompilowanych zestawach nie są wyświetlane dokładnie tak, jak je tworzysz. Można przeglądać skompilowaną reprezentację typów Języka F#, ale nie można wyświetlić typów, które pojawiają się z języka F#.|
|[Okno danych wyjściowych](reference/output-window.md)|Wyświetla dane wyjściowe kompilacji.|Tak|
|Analiza wydajności|Zawiera narzędzia do pomiaru wydajności kodu.|Tak|
|Okno właściwości|Wyświetla i umożliwia edycję właściwości obiektu w środowisku programistycznym, który ma fokus.|Tak|
|Eksplorator serwera|Udostępnia sposoby interakcji z różnymi zasobami serwera.|Tak|
|Eksplorator rozwiązań|Umożliwia wyświetlanie projektów i plików oraz zarządzanie nimi.|Tak|
|Lista zadań|Umożliwia zarządzanie elementami roboczymi odnoszącymi się do kodu.|Nie|
|Projekty testowe|Zawiera funkcje, które pomagają przetestować kod.|Nie|
|Przybornik|Wyświetla karty zawierające przeciągane obiekty, takie jak formanty i sekcje tekstu lub kodu.|Tak|

## <a name="see-also"></a>Zobacz też

- [F# przewodnik (.NET Framework)](/dotnet/fsharp/)
- [Wprowadzenie do języka F# w programie Visual Studio](/dotnet/fsharp/get-started/get-started-visual-studio)
