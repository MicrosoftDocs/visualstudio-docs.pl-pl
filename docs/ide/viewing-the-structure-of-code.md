---
title: Widok klasy, hierarchia wywołań, Przeglądarka obiektów, okno definicji kodu
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
- vs.objectbrowser
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73a4660c9e0dad66ceb73c04852601765174264
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409987"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Wyświetlanie struktury kodu przy użyciu różnych okien narzędzi

Można badanie klas i ich członków w programie Visual Studio przy użyciu różnych okien narzędzi, w tym **Widok klasy**, **hierarchii wywołań**, **Przeglądarka obiektów**i **definicji kodu** (C++ tylko). Te okna narzędzi mogą przeglądać kod w projektach programu Visual Studio, składnikach .NET, składnikach COM, bibliotekach dołączanych dynamicznie (DLL) i bibliotekach typów (TLB).

Możesz również użyć **Eksplorator rozwiązań** do przeglądania typów i członków w projektach, wyszukiwania symboli, wyświetlania hierarchii wywołań metod, znajdowania odwołań do symboli i innych, bez konieczności przełączania się między wieloma oknami narzędzi.

Jeśli masz wersję Visual Studio Enterprise, możesz użyć *map kodu* do wizualizacji struktury kodu i jego zależności w całym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Mapowanie zależności za pomocą map kodu](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Widok klasy (Visual Basic, C#, C++)

**Widok klasy** jest pokazywany jako część **Eksplorator rozwiązań** i jako oddzielne okno. **Widok klasy** wyświetla elementy aplikacji. W górnym okienku są wyświetlane przestrzenie nazw, typy, interfejsy, wyliczenia i klasy, a w dolnym okienku są wyświetlane elementy członkowskie należące do typu wybranego w górnym okienku. Za pomocą tego okna można przenieść do definicji elementów członkowskich w kodzie źródłowym (lub w **Przeglądarka obiektów** , jeśli element jest zdefiniowany poza rozwiązaniem).

Nie trzeba kompilować projektu, aby wyświetlić jego elementy **Widok klasy**. Okno jest odświeżane w miarę modyfikowania kodu w projekcie.

Możesz dodać kod do projektu, wybierając węzeł projektu i wybierając przycisk **Dodaj** , aby otworzyć okno dialogowe **Dodaj nowy element** . Kod zostanie dodany w osobnym pliku.

Jeśli projekt jest zaewidencjonowany do kontroli kodu źródłowego, każdy element **Widok klasy** wyświetli ikonę wskazującą stan kodu źródłowego pliku. Typowe polecenia kontroli kodu źródłowego, takie jak **wyewidencjonowywanie**, **ewidencjonowanie**i **pobieranie najnowszej wersji** są również dostępne w menu skrótów dla elementu.

### <a name="class-view-toolbar"></a>Widok klasy pasek narzędzi

Pasek narzędzi **Widok klasy** zawiera następujące polecenia:

|||
|-|-|
|**Nowy folder**|Tworzy folder wirtualny lub podfolder, w którym można organizować często używane elementy. Są one zapisywane w aktywnym pliku rozwiązania ( *. suo*). Po zmianie nazwy lub usunięciu elementu w kodzie może on pojawić się w folderze wirtualnym jako węzeł błędu. Aby rozwiązać ten problem, Usuń węzeł błędu. Jeśli zmieniono nazwę elementu, można go przenieść z hierarchii projektu do folderu ponownie.|
|**Wstecz**|Przechodzi do poprzednio wybranego elementu.|
|**Prześlą**|Przechodzi do następnego wybranego elementu.|
|**Widok diagramu klas** (tylko projekty kodu zarządzanego)|Staną się dostępne po wybraniu przestrzeni nazw lub typu w **Widok klasy**. Po wybraniu przestrzeni nazw Diagram klas pokazuje wszystkie typy w nim. Po wybraniu typu Diagram klas pokazuje tylko ten typ.|

### <a name="class-view-settings"></a>Ustawienia Widok klasy

Przycisk **ustawienia widok klasy** na pasku narzędzi ma następujące ustawienia:

|||
|-|-|
|**Pokaż typy podstawowe**|Typy podstawowe są wyświetlane.|
|**Pokaż odwołania projektu**|Odwołania do projektu są wyświetlane.|
|**Pokaż ukryte typy i składowe**|Ukryte typy i elementy członkowskie (nieprzeznaczone do użycia przez klientów) są wyświetlane w kolorze szarym.|
|**Pokaż publiczne składowe**|Wyświetlane są publiczne składowe.|
|**Pokaż chronione elementy członkowskie**|Są wyświetlane chronione elementy członkowskie.|
|**Pokaż prywatne składowe**|Wyświetlane są prywatne składowe.|
|**Pokaż inne elementy członkowskie**|Są wyświetlane inne rodzaje elementów członkowskich, w tym wewnętrzne (lub zaprzyjaźnione w Visual Basic) członków.|
|**Pokaż Odziedziczone składowe**|Są wyświetlane dziedziczone elementy członkowskie.|

### <a name="class-view-shortcut-menu"></a>Widok klasy menu skrótów

Menu skrótów (lub kliknij prawym przyciskiem myszy) w **Widok klasy** mogą zawierać następujące polecenia, w zależności od rodzaju wybranego projektu:

|||
|-|-|
|**Przejdź do definicji**|Znajduje definicję elementu w kodzie źródłowym lub w **Przeglądarka obiektów**, jeśli element nie jest zdefiniowany w otwartym projekcie.|
|**Przeglądaj definicję**|Wyświetla wybrany element w **Przeglądarka obiektów**.|
|**Znajdź wszystkie odwołania**|Znajduje aktualnie zaznaczony element obiektu i wyświetla wyniki w oknie **Wyszukiwanie wyników** .|
|**Filtruj do typu** (tylko kod zarządzany)|Wyświetla tylko wybrany typ lub przestrzeń nazw. Filtr można usunąć, wybierając przycisk **Wyczyść wyszukiwanie** (**X**) obok pola **Znajdź** .|
|**Kopiuj**|Kopiuje w pełni kwalifikowaną nazwę elementu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i składowych alfabetycznie według nazwy.|
|**Sortuj według typu elementu członkowskiego**|Wyświetla listę typów i składowych w kolejności według typu (takie jak klasy poprzedzają interfejsy, interfejsy poprzedzają delegatów, a metody poprzedzają właściwości).|
|**Sortuj według dostępu do składowej**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, na przykład Public lub Private.|
|**Grupuj według typu elementu członkowskiego**|Sortuje typy i składowe w grupach według typu obiektu.|
|**Przejdź do deklaracji** (C++ tylko kod)|Wyświetla deklarację typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetl hierarchię wywołań**|Wyświetla wybraną metodę w oknie **Hierarchia wywołań** .|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Okno hierarchii wywołań (Visual Basic, C#, C++)

Okno **Hierarchia wywołań** pokazuje, gdzie wywoływana jest dana metoda lub właściwość. Wyświetla również metody, które są wywoływane z tej metody. Można wyświetlić wiele poziomów grafu wywołań, który pokazuje relacje wywoływane przez wywołującego między metodami w określonym zakresie.

Możesz wyświetlić okno **Hierarchia wywołań** , wybierając metodę (lub konstruktora) w edytorze, a następnie wybierając pozycję **Wyświetl hierarchię wywołań** w menu skrótów. Ekran powinien wyglądać podobnie do poniższej ilustracji:

![Okno hierarchii wywołań w programie Visual Studio](../ide/media/multiplenodes.png)

Korzystając z listy rozwijanej na pasku narzędzi, można określić zakres hierarchii: rozwiązanie, bieżący projekt lub bieżący dokument.

W okienku głównym są wyświetlane wywołania do i z metody, a w okienku **Wywołaj Lokacje** zostanie wyświetlona lokalizacja wybranego wywołania. W przypadku elementów członkowskich, które są wirtualne lub abstrakcyjne, zostanie wyświetlony węzeł **Nazwa metody zastąpień** . W przypadku elementów członkowskich interfejsu pojawia się węzeł **Nazwa metody implementującej** .

W oknie **Hierarchia wywołań** nie znajdują się odwołania do grup metod, w tym miejsca, w których metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisana do delegata. Aby znaleźć te odwołania, użyj polecenia **Znajdź wszystkie odwołania** .

Menu skrótów w oknie **Hierarchia wywołań** zawiera następujące polecenia:

|||
|-|-|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł jako nowy węzeł główny.|
|**Usuń element główny**|Usuwa wybrany węzeł główny z okienka widoku drzewa.|
|**Przejdź do definicji**|Przechodzi do oryginalnej definicji metody.|
|**Znajdź wszystkie odwołania**|Znajduje w projekcie wszystkie odwołania do wybranej metody.|
|**Kopiuj**|Kopiuje wybrany węzeł (ale nie jego węzły podrzędne).|
|**Odowieżenie**|Odświeża informacje.|

## <a name="BKMK_ObjectBrowser"></a>Przeglądarka obiektów

W oknie **Przeglądarka obiektów** są wyświetlane opisy kodu w projektach.

Można filtrować składniki, które mają być wyświetlane, za pomocą listy rozwijanej w górnej części okna. Składniki niestandardowe mogą obejmować pliki wykonywalne kodu zarządzanego, zestawy bibliotek, biblioteki typów i plików *ocx* . Nie można dodać C++ składników niestandardowych.

::: moniker range="vs-2017"

Ustawienia niestandardowe są zapisywane w katalogu aplikacji użytkownika programu Visual Studio, *%AppData%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

::: moniker-end

::: moniker range=">=vs-2019"

Ustawienia niestandardowe są zapisywane w katalogu aplikacji użytkownika programu Visual Studio, *%AppData%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat*.

::: moniker-end

W lewym okienku **Przeglądarka obiektów** są wyświetlane zestawy. Można rozwinąć zestawy, aby wyświetlić zawarte w nich przestrzenie nazw, a następnie rozwinąć przestrzenie nazw, aby wyświetlić zawarte w nich typy. Po wybraniu typu, jego elementy członkowskie (takie jak właściwości i metody) są wyświetlane w okienku po prawej stronie. W dolnym okienku po prawej stronie są wyświetlane szczegółowe informacje o wybranym elemencie.

Konkretny element można wyszukać, korzystając z pola **wyszukiwania** w górnej części okna. W wyszukiwaniu nie jest rozróżniana wielkość liter. Wyniki wyszukiwania są wyświetlane w okienku po lewej stronie. Aby wyczyścić wyszukiwanie, wybierz przycisk **Wyczyść wyszukiwanie** (**X**) obok pola **wyszukiwania** .

**Przeglądarka obiektów** śledzi dokonane wybory i można przechodzić między wybranymi elementami przy użyciu przycisków **do przodu** i do **tyłu** na pasku narzędzi.

Możesz użyć **Przeglądarka obiektów** , aby dodać odwołanie do zestawu do otwartego rozwiązania, wybierając element (zestaw, przestrzeń nazw, typ lub element członkowski) i wybierając przycisk **Dodaj odwołanie** na pasku narzędzi.

### <a name="object-browser-settings"></a>Ustawienia Przeglądarka obiektów

Za pomocą przycisku **ustawienia Przeglądarka obiektów** na pasku narzędzi można określić jeden z następujących widoków:

|||
|-|-|
|**Wyświetl przestrzenie nazw**|Wyświetla przestrzenie nazw, a nie kontenery fizyczne, w okienku po lewej stronie. Obszary nazw przechowywane w wielu kontenerach fizycznych są scalane.|
|**Wyświetl kontenery**|Wyświetla kontenery fizyczne, a nie przestrzenie nazw, w okienku po lewej stronie. **Wyświetl obszary nazw** i **kontenery widoku** są wzajemnie wykluczające się ustawienia.|
|**Pokaż typy podstawowe**|Wyświetla typy podstawowe.|
|**Pokaż ukryte typy i składowe**|Wyświetla ukryte typy i elementy członkowskie (nie przeznaczone do użycia przez klientów) w jasnym kolorze szarym.|
|**Pokaż publiczne składowe**|Wyświetla publiczne elementy członkowskie.|
|**Pokaż chronione elementy członkowskie**|Wyświetla chronione elementy członkowskie.|
|**Pokaż prywatne składowe**|Wyświetla prywatnych członków.|
|**Pokaż inne elementy członkowskie**|Wyświetla inne typy elementów członkowskich, w tym wewnętrzne (lub zaprzyjaźnione w Visual Basic) członków.|
|**Pokaż Odziedziczone składowe**|Wyświetla dziedziczone elementy członkowskie.|
|**Pokaż metody rozszerzenia**|Wyświetla metody rozszerzenia.|

### <a name="object-browser-shortcut-menu-commands"></a>Polecenia menu skrótów Przeglądarka obiektów

Menu skrótów (lub kliknij prawym przyciskiem myszy) w **Przeglądarka obiektów** mogą zawierać następujące polecenia, w zależności od rodzaju wybranego elementu:

|||
|-|-|
|**Przeglądaj definicję**|Pokazuje węzeł podstawowy wybranego elementu.|
|**Znajdź wszystkie odwołania**|Znajduje aktualnie zaznaczony element obiektu i wyświetla wyniki w oknie **Wyszukiwanie wyników** .|
|**Filtruj do typu**|Wyświetla tylko wybrany typ lub przestrzeń nazw. Filtr można usunąć, wybierając przycisk **Wyczyść wyszukiwanie** .|
|**Kopiuj**|Kopiuje w pełni kwalifikowaną nazwę elementu.|
|**Usuń**|Jeśli zakres jest zestaw składnika niestandardowego, usuwa wybrany składnik z zakresu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i składowych alfabetycznie według nazwy.|
|**Sortuj według typu obiektu**|Wyświetla listę typów i składowych w kolejności według typu (takie jak klasy poprzedzają interfejsy, interfejsy poprzedzają delegatów, a metody poprzedzają właściwości).|
|**Sortuj według dostępu do obiektów**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, na przykład Public lub Private.|
|**Grupuj według typu obiektu**|Sortuje typy i składowe w grupach według typu obiektu.|
|**Przejdź do deklaracji** (C++ tylko projekty)|Wyświetla deklarację typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetl hierarchię wywołań**|Wyświetla wybraną metodę w oknie **Hierarchia wywołań** .|

## <a name="code-definition-window-c"></a>Okno Definicja kodu (C++)

W oknie **definicji kodu** zostanie wyświetlona definicja wybranego C++ typu lub elementu członkowskiego w aktywnym projekcie. Typ lub element członkowski można wybrać w edytorze kodu lub w oknie widoku kodu.

Mimo że to okno jest tylko do odczytu, można ustawić punkty przerwania lub zakładki. Aby zmodyfikować wyświetlaną definicję, wybierz polecenie **Edytuj definicję** w menu skrótów. Spowoduje to otwarcie pliku źródłowego w edytorze kodu i przeniesienie punktu wstawiania do wiersza, w którym rozpoczyna się definicja.

> [!NOTE]
> Począwszy od programu Visual Studio 2015, okno **definicji kodu** może być używane tylko z C++ kodem.

### <a name="code-definition-shortcut-menu"></a>Menu skrótów definicji kodu

Menu skrótów (lub kliknij prawym przyciskiem myszy) w oknie **definicji kodu** mogą zawierać następujące polecenia:

|||
|-|-|
|**Szybkie akcje i refaktoryzacje**||
|**Zmiana nazwy**||
|**Generowanie grafu plików dołączanych**||
|**Definicja wglądu**||
|**Przejdź do definicji**|Znajduje definicję (lub definicje, dla klas częściowych) i wyświetla je w oknie **Znajdź wyniki** .|
|**Przejdź do deklaracji**||
|**Znajdź wszystkie odwołania**|Znajduje odwołania do typu lub elementu członkowskiego w rozwiązaniu.|
|**Wyświetl hierarchię wywołań**|Wyświetla metodę w oknie **Hierarchia wywołań** .|
|**Przełącz nagłówek/plik kodu**||
|**Uruchom testy**|Jeśli w projekcie są testy jednostkowe, program uruchamia testy dla zaznaczonego kodu.|
|**Debuguj testy**||
|**Punkt**|Wstawia punkt przerwania (lub punkt śledzenia).|
|**Uruchom do kursora**|Uruchamia program w trybie debugowania do lokalizacji kursora.|
|**Fragment kodu**||
|**Wytnij**, **Kopiuj**, **Wklej**||
|**Adnotacja**||
|**Obramowanie**|Standardowe polecenia tworzenia konspektu.|
|**Skanuj ponownie**||
|**Edytuj definicję**|Przenosi punkt wstawiania do definicji w oknie kodu.|
|**Wybierz kodowanie**|Otwiera okno **kodowania** , aby można było ustawić kodowanie dla tego pliku.|

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Możesz użyć okna **Konspekt dokumentu** w połączeniu z widokami projektanta, takimi jak projektant dla strony XAML lub Projektant formularzy systemu Windows lub za pomocą stron HTML. To okno wyświetla elementy w widoku drzewa, aby można było wyświetlić logiczną strukturę formularza lub strony i znaleźć formanty, które są głęboko osadzone lub ukryte.

## <a name="see-also"></a>Zobacz też

- [Widok klasy i Przeglądarka obiektów, ikony](../ide/class-view-and-object-browser-icons.md)
