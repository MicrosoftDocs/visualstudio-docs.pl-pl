---
title: Wyświetlanie struktury kodu za pomocą okien narzędzi
description: Dowiedz się, jak używać okien narzędzi Widok klasy, hierarchii wywołań, przeglądarki obiektów i definicji kodu (tylko język C++) do badania klas i ich składowych w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window
- Visual Studio, object browser
- call hierarchy
- Visual Studio, document outline window
- code definition window [Visual Studio]
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41c11025e22c1288387862fa138b35efbbca8557
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924958"
---
# <a name="view-the-structure-of-code-by-using-different-tool-windows"></a>Wyświetlanie struktury kodu przy użyciu różnych okien narzędzi

Klasy i ich składowe można badać w programie Visual Studio różnych oknach narzędzi, w tym **Widok klasy,** hierarchii wywołań, przeglądarki obiektów i definicji kodu **(tylko** język C++). Te okna narzędzi mogą sprawdzać kod w projektach Visual Studio, składnikach .NET, składnikach COM, bibliotekach łączy dynamicznych (DLL) i bibliotekach typów (TLB).

Za pomocą programu **Eksplorator rozwiązań** można również przeglądać typy i elementy członkowskie w projektach, wyszukiwać symbole, wyświetlać hierarchię wywołań metody, wyszukiwać odwołania do symboli i nie tylko, bez konieczności przełączania się między wieloma oknami narzędzi.

Jeśli masz już Visual Studio Enterprise, możesz  użyć map kodu, aby zwizualizować strukturę kodu i jego zależności w całym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Map dependencies with code maps (Mapowanie zależności za pomocą map kodu).](../modeling/map-dependencies-across-your-solutions.md)

## <a name="class-view-visual-basic-c-c"></a>Widok klasy (Visual Basic, C#, C++)

**Widok klasy** jest wyświetlana jako **część Eksplorator rozwiązań** w osobnym oknie. **Widok klasy** wyświetla elementy aplikacji. W górnym okienku są wyświetlane przestrzenie nazw, typy, interfejsy, wyliczenia i klasy, a w dolnym okienku są wyświetlane składowe należące do typu wybranego w górnym okienku. Za pomocą tego okna można przejść do definicji elementów członkowskich  w kodzie źródłowym (lub w przeglądarce obiektów, jeśli element jest zdefiniowany poza rozwiązaniem).

Nie trzeba kompilować projektu, aby wyświetlić jego elementy w **Widok klasy**. Okno jest odświeżane podczas modyfikowania kodu w projekcie.

Możesz dodać kod do projektu, wybierając węzeł projektu i wybierając przycisk **Dodaj,** aby otworzyć **okno dialogowe** Dodawanie nowego elementu. Kod jest dodawany w oddzielnym pliku.

Jeśli projekt jest zaewidencjonowany do kontroli kodu źródłowego, Widok klasy **element** wyświetla ikonę wskazującą stan kodu źródłowego pliku. Typowe polecenia kontroli kodu **źródłowego,** takie jak Wyewidencjonaj, Zaewidencjuj i  **Pobierz** najnowszą wersję, są również dostępne w menu skrótów elementu .

### <a name="class-view-toolbar"></a>Widok klasy narzędzi

Pasek **Widok klasy** narzędzi zawiera następujące polecenia:

|Nazwa|Opis|
|-|-|
|**Nowy folder**|Tworzy wirtualny folder lub podfolder, w którym można organizować często używane elementy. Są one zapisywane w aktywnym pliku rozwiązania *(.suo).* Po zmianie nazwy lub usunięciu elementu w kodzie może on pojawić się w folderze wirtualnym jako węzeł błędu. Aby rozwiązać ten problem, usuń węzeł błędu. Jeśli zmieniono nazwę elementu, można ponownie przenieść go z hierarchii projektu do folderu .|
|**Wstecz**|Przechodzi do wcześniej wybranego elementu.|
|**do przodu**|Przechodzi do następnego wybranego elementu.|
|**Wyświetlanie diagramu klas** (tylko projekty kodu zarządzanego)|Staje się dostępne po wybraniu przestrzeni nazw lub typu w **Widok klasy**. Po wybraniu przestrzeni nazw diagram klas pokazuje wszystkie typy w tej przestrzeni nazw. Po wybraniu typu diagram klas pokazuje tylko ten typ.|

### <a name="class-view-settings"></a>Widok klasy ustawień

Przycisk **Widok klasy ustawienia na** pasku narzędzi ma następujące ustawienia:

|Nazwa|Opis|
|-|-|
|**Pokaż typy podstawowe**|Zostaną wyświetlone typy podstawowe.|
|**Pokaż odwołania do projektu**|Zostaną wyświetlone odwołania do projektu.|
|**Pokaż ukryte typy i elementy członkowskie**|Ukryte typy i elementy członkowskie (nie są przeznaczone do użytku przez klientów) są wyświetlane w jasnoszarym tekście.|
|**Pokaż publiczne elementy członkowskie**|Zostaną wyświetlone publiczne elementy członkowskie.|
|**Pokaż chronione elementy członkowskie**|Chronione elementy członkowskie są wyświetlane.|
|**Pokaż prywatne elementy członkowskie**|Zostaną wyświetlone prywatne elementy członkowskie.|
|**Pokaż inne elementy członkowskie**|Wyświetlane są inne rodzaje elementów członkowskich, w tym wewnętrzne (lub znajomy w Visual Basic).|
|**Pokaż dziedziczone elementy członkowskie**|Zostaną wyświetlone dziedziczone elementy członkowskie.|

### <a name="class-view-shortcut-menu"></a>Widok klasy menu skrótów

Menu skrótu (lub kliknięcie prawym przyciskiem myszy) w Widok klasy **może** zawierać następujące polecenia, w zależności od wybranego rodzaju projektu:

|Nazwa|Opis|
|-|-|
|**Przejdź do definicji**|Znajduje definicję elementu w kodzie źródłowym lub w przeglądarce obiektów **,** jeśli element nie jest zdefiniowany w otwartym projekcie.|
|**Przeglądaj definicję**|Wyświetla wybrany element w przeglądarce **obiektów**.|
|**Znajdź wszystkie odwołania**|Znajduje aktualnie zaznaczony element obiektu i wyświetla wyniki w **oknie Znajdź** wyniki.|
|**Filtruj do typu** (tylko kod zarządzany)|Wyświetla tylko wybrany typ lub przestrzeń nazw. Możesz usunąć filtr, wybierając przycisk **Wyczyść** wyszukiwanie (**X**) obok **pola** Znajdź.|
|**Kopiuj**|Kopiuje w pełni kwalifikowaną nazwę elementu.|
|**Sortowanie alfabetyczne**|Wyświetla listę typów i elementów członkowskich alfabetycznie według nazwy.|
|**Sortuj według typu członka**|Wyświetla listę typów i składowych w kolejności według typu (tak, aby klasy poprzedzały interfejsy, interfejsy poprzedzały delegatów i metody poprzedzały właściwości).|
|**Sortuj według dostępu do członków**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, na przykład publiczne lub prywatne.|
|**Grupuj według typu członka**|Sortuje typy i elementy członkowskie w grupy według typu obiektu.|
|**Przejdź do deklaracji** (tylko kod C++)|Wyświetla deklarację typu lub członka w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do definicji**|Wyświetla definicję typu lub członka w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub członka w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetlanie hierarchii wywołań**|Wyświetla wybraną metodę w **oknie Hierarchia** wywołań.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Okno Hierarchia wywołań (Visual Basic, C#, C++)

Okno **Hierarchia wywołań** pokazuje, gdzie jest wywoływana danej metody lub właściwości. Zawiera również listę metod, które są wywoływane z tej metody. Można wyświetlić wiele poziomów wykresu wywołań, który pokazuje relacje wywołujące-wywołujące między metodami w określonym zakresie.

Okno Hierarchia **wywołań** można wyświetlić, wybierając metodę (lub właściwość lub konstruktor) w edytorze, a następnie wybierając pozycję **Wyświetl** hierarchię wywołań w menu skrótów. Ekran powinien wyglądać następująco:

![Okno Hierarchia wywołań w Visual Studio](../ide/media/multiplenodes.png)

Korzystając z listy rozwijanej na pasku narzędzi, można określić zakres hierarchii: rozwiązanie, bieżący projekt lub bieżący dokument.

W okienku głównym są wyświetlane wywołania metody i , a w okienku **Witryny** wywołań jest wyświetlana lokalizacja wybranego wywołania. W przypadku elementów członkowskich, które są wirtualne lub abstrakcyjne, zostanie wyświetlony węzeł **Nazwa metody przesłonięcia.** W przypadku elementów członkowskich interfejsu zostanie wyświetlony węzeł **Nazwa metody** Implements.

Okno **Hierarchia wywołań** nie znajduje odwołań do grupy metod, które obejmują miejsca, w których metoda jest dodawana jako procedura obsługi zdarzeń lub przypisana do delegata. Aby znaleźć te odwołania, użyj **polecenia Znajdź wszystkie odwołania.**

Menu skrótów w **oknie Hierarchia wywołań** zawiera następujące polecenia:

|Nazwa|Opis|
|-|-|
|**Dodaj jako nowy katalog główny**|Dodaje wybrany węzeł jako nowy węzeł główny.|
|**Usuń katalog główny**|Usuwa wybrany węzeł główny z okienka widoku drzewa.|
|**Przejdź do definicji**|Przechodzi do oryginalnej definicji metody.|
|**Znajdź wszystkie odwołania**|Znajduje w projekcie wszystkie odwołania do wybranej metody.|
|**Kopiuj**|Kopiuje wybrany węzeł (ale nie jego podwęzłe).|
|**Odświeżanie**|Odświeża informacje.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a> Przeglądarka obiektów

W **oknie Przeglądarka** obiektów są wyświetlane opisy kodu w projektach.

Składniki, które chcesz wyświetlić, można filtrować przy użyciu listy rozwijanej w górnej części okna. Składniki niestandardowe mogą obejmować pliki wykonywalne kodu zarządzanego, zestawy bibliotek, biblioteki typów i *pliki ocx.* Nie można dodawać składników niestandardowych języka C++.

::: moniker range="vs-2017"

Ustawienia niestandardowe są zapisywane w Visual Studio aplikacji użytkownika *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat.*

::: moniker-end

::: moniker range=">=vs-2019"

Ustawienia niestandardowe są zapisywane w Visual Studio aplikacji użytkownika *%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat.*

::: moniker-end

W okienku po **lewej stronie przeglądarki obiektów** są pokazuje zestawy. Można rozwinąć zestawy, aby wyświetlić przestrzenie nazw, które zawierają, a następnie rozwinąć przestrzenie nazw, aby wyświetlić zawarte w nich typy. Po wybraniu typu jego elementy członkowskie (takie jak właściwości i metody) są wyświetlane w okienku po prawej stronie. W prawym dolnym okienku wyświetlane są szczegółowe informacje o wybranym elementie.

Możesz wyszukać określony element, używając **pola** Wyszukaj w górnej części okna. W wyszukiwaniu nie jest uwzględniania ich litera. Wyniki wyszukiwania są wyświetlane w okienku po lewej stronie. Aby wyczyścić wyszukiwanie, wybierz przycisk **Wyczyść wyszukiwanie** (**X**) obok **pola** Wyszukiwania.

Przeglądarka **obiektów** śledzi dokonane wybory i umożliwia przechodzenie między wyborami przy  użyciu  przycisków Do przodu i Wstecz na pasku narzędzi.

Za pomocą przeglądarki **obiektów** można dodać odwołanie do zestawu do otwartego rozwiązania, wybierając element  (zestaw, przestrzeń nazw, typ lub element członkowski) i wybierając przycisk Dodaj odwołanie na pasku narzędzi.

### <a name="object-browser-settings"></a>Ustawienia przeglądarki obiektów

Za pomocą **przycisku Ustawienia przeglądarki** obiektów na pasku narzędzi można określić jeden z następujących widoków:

|Nazwa|Opis|
|-|-|
|**Wyświetlanie przestrzeni nazw**|Wyświetla przestrzenie nazw, a nie kontenery fizyczne, w okienku po lewej stronie. Przestrzenie nazw przechowywane w wielu kontenerach fizycznych są scalane.|
|**Wyświetlanie kontenerów**|Wyświetla kontenery fizyczne zamiast przestrzeni nazw w okienku po lewej stronie. **Ustawienia Wyświetl przestrzenie nazw** **i Wyświetl kontenery** wzajemnie się wykluczają.|
|**Pokaż typy podstawowe**|Wyświetla typy podstawowe.|
|**Pokaż ukryte typy i elementy członkowskie**|Wyświetla ukryte typy i elementy członkowskie (nie są przeznaczone do użytku przez klientów) w jasnoszarym tekście.|
|**Pokaż publiczne elementy członkowskie**|Wyświetla publiczne elementy członkowskie.|
|**Pokaż chronione elementy członkowskie**|Wyświetla chronione elementy członkowskie.|
|**Pokaż prywatne elementy członkowskie**|Wyświetla prywatne elementy członkowskie.|
|**Pokaż inne elementy członkowskie**|Wyświetla inne typy elementów członkowskich, w tym wewnętrzne (lub znajomy w Visual Basic) członków.|
|**Pokaż dziedziczone elementy członkowskie**|Wyświetla dziedziczone elementy członkowskie.|
|**Pokazywanie metod rozszerzeń**|Wyświetla metody rozszerzenia.|

### <a name="object-browser-shortcut-menu-commands"></a>Polecenia menu skrótów przeglądarki obiektów

Menu skrótu (lub kliknięcie prawym przyciskiem myszy) w przeglądarce **obiektów** może zawierać następujące polecenia, w zależności od wybranego rodzaju elementu:

|Nazwa|Opis|
|-|-|
|**Przeglądaj definicję**|Przedstawia węzeł podstawowy dla wybranego elementu.|
|**Znajdź wszystkie odwołania**|Znajduje aktualnie zaznaczony element obiektu i wyświetla wyniki w **oknie Znajdź** wyniki.|
|**Filtruj do typu**|Wyświetla tylko wybrany typ lub przestrzeń nazw. Możesz usunąć filtr, wybierając przycisk **Wyczyść** wyszukiwanie.|
|**Kopiuj**|Kopiuje w pełni kwalifikowaną nazwę elementu.|
|**Usuń**|Jeśli zakres jest niestandardowym zestawem składników, program usuwa wybrany składnik z zakresu.|
|**Sortowanie alfabetyczne**|Wyświetla listę typów i elementów członkowskich alfabetycznie według nazwy.|
|**Sortuj według typu obiektu**|Wyświetla listę typów i składowych w kolejności według typu (tak, aby klasy poprzedzały interfejsy, interfejsy poprzedzały delegatów i metody poprzedzały właściwości).|
|**Sortuj według dostępu do obiektu**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, na przykład publiczne lub prywatne.|
|**Grupowanie według typu obiektu**|Sortuje typy i elementy członkowskie w grupy według typu obiektu.|
|**Deklaracja Przejdź do** (tylko projekty C++)|Wyświetla deklarację typu lub członka w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do definicji**|Wyświetla definicję typu lub członka w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub członka w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetlanie hierarchii wywołań**|Wyświetla wybraną metodę w **oknie Hierarchia** wywołań.|

## <a name="code-definition-window-c"></a>okno Definicja kodu (C++)

W **oknie** Definicja kodu jest wyświetlana definicja wybranego typu lub członka języka C++ w aktywnym projekcie. Typ lub element członkowski można wybrać w edytorze kodu lub w oknie widoku kodu.

Chociaż to okno jest tylko do odczytu, można ustawić w nim punkty przerwania lub zakładki. Aby zmodyfikować wyświetloną definicję, wybierz **pozycję Edytuj definicję** w menu skrótów. Spowoduje to otwarcie pliku źródłowego w edytorze kodu i przeniesienie punktu wstawiania do wiersza, w którym rozpoczyna się definicja.

> [!NOTE]
> Począwszy od Visual Studio 2015  r., okno Definicja kodu może być używane tylko z kodem C++.

### <a name="code-definition-shortcut-menu"></a>Menu skrótów definicji kodu

Menu skrótu (lub kliknięcie prawym przyciskiem myszy) w **oknie Definicja** kodu może zawierać następujące polecenia:

|Nazwa|Opis|
|-|-|
|**Szybkie akcje i operacje refaktoryzacji**||
|**Zmień nazwę**||
|**Generowanie grafu plików dołączanych**||
|**Podejrzyj definicję**||
|**Przejdź do definicji**|Znajduje definicję (lub definicje dla klas częściowych) i wyświetla je w **oknie Znajdź** wyniki.|
|**Przejdź do deklaracji**||
|**Znajdź wszystkie odwołania**|Znajduje odwołania do typu lub członka w rozwiązaniu.|
|**Wyświetlanie hierarchii wywołań**|Wyświetla metodę w oknie **Hierarchia** wywołań.|
|**Przełączanie nagłówka/pliku kodu**||
|**Uruchamianie testów**|Jeśli w projekcie istnieją testy jednostkowe, program uruchamia testy dla wybranego kodu.|
|**Debugowanie testów**||
|**Punkt przerwania**|Wstawia punkt przerwania (lub punkt śledzenia).|
|**Uruchom do kursora**|Uruchamia program w trybie debugowania do lokalizacji kursora.|
|**Fragment kodu**||
|**Wycinanie,** **kopiowanie,** **wklejanie**||
|**Adnotacja**||
|**Tworzenie konspektu**|Standardowe polecenia wytłaszczania.|
|**Skanuj ponownie**||
|**Edytuj definicję**|Przenosi punkt wstawiania do definicji w oknie kodu.|
|**Wybieranie kodowania**|Otwiera okno **Kodowanie,** aby można było ustawić kodowanie pliku.|

## <a name="document-outline-window"></a>Okno Konspekt dokumentu

Okna Konspekt **dokumentu można** używać w połączeniu z widokami projektanta, takimi jak projektant strony XAML, projektant formularzy systemu Windows lub strony HTML. To okno wyświetla elementy w widoku drzewa, dzięki czemu można wyświetlić strukturę logiczną formularza lub strony i znaleźć kontrolki, które są głęboko osadzone lub ukryte.

## <a name="see-also"></a>Zobacz też

- [Widok klasy i Przeglądarka obiektów, ikony](../ide/class-view-and-object-browser-icons.md)
