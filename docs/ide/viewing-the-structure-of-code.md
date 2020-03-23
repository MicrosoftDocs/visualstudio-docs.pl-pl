---
title: Widok klasy, hierarchia połączeń, przeglądarka obiektów, okno definicji kodu
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303058"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Wyświetlanie struktury kodu przy użyciu różnych okien narzędzi

Klasy i ich elementy członkowskie można badać w programie Visual Studio przy użyciu różnych okien narzędzi, w tym **widok klasy,** **hierarchia wywołań,** **przeglądarka obiektów**i **definicja kodu** (tylko c++). Te narzędzia windows można sprawdzić kod w projektach programu Visual Studio, składniki .NET, składniki COM, biblioteki łączy dynamicznych (DLL) i biblioteki typów (TLB).

Za pomocą **Eksploratora rozwiązań** można również przeglądać typy i elementy członkowskie w projektach, wyszukiwać symbole, wyświetlać hierarchię wywołań metody, znajdować odniesienia do symboli i nie tylko, bez konieczności przełączania się między wieloma oknami narzędzi.

Jeśli masz visual studio enterprise edition, można użyć *map kodu* do wizualizacji struktury kodu i jego zależności w całym rozwiązaniu. Aby uzyskać więcej informacji, zobacz [Zależności mapowania z mapami kodu](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Widok klasy (Visual Basic, C#, C++)

**Widok klasy** jest wyświetlany jako część **Eksploratora rozwiązań** i jako oddzielne okno. **Widok klasy** wyświetla elementy aplikacji. W górnym okienku są wyświetlane przestrzenie nazw, typy, interfejsy, wyliczenia i klasy, a w dolnym okienku są wyświetlane elementy członkowskie należące do typu wybranego w górnym okienku. Za pomocą tego okna, można przejść do definicji elementów członkowskich w kodzie źródłowym (lub w **przeglądarce obiektów,** jeśli element jest zdefiniowany poza rozwiązaniem).

Nie trzeba skompilować projektu, aby wyświetlić jego elementy w **widoku klasy**. Okno jest odświeżane podczas modyfikowania kodu w projekcie.

Kod można dodać do projektu, wybierając węzeł projektu i wybierając przycisk **Dodaj,** aby otworzyć okno dialogowe **Dodawanie nowego elementu.** Kod jest dodawany w osobnym pliku.

Jeśli projekt jest zaewidencjonowany do kontroli kodu źródłowego, każdy element **widoku klasy** wyświetla ikonę wskazującą stan kodu źródłowego pliku. Typowe polecenia kontroli kodu źródłowego, takie jak **Wyewidencjonuj,** **Zaewidencjonuj**i **Pobierz najnowszą wersję,** są również dostępne w menu skrótów dla elementu.

### <a name="class-view-toolbar"></a>Pasek narzędzi Widok klasy

Pasek narzędzi **Widok klasy** zawiera następujące polecenia:

|||
|-|-|
|**Nowy folder**|Tworzy folder wirtualny lub podfolder, w którym można organizować często używane elementy. Są one zapisywane w aktywnym pliku rozwiązania (*.suo).* Po zmianie nazwy lub usunąć element w kodzie, może pojawić się w folderze wirtualnym jako węzeł błędu. Aby rozwiązać ten problem, usuń węzeł błędu. Jeśli nazwa elementu została zmieniona, można go ponownie przenieść z hierarchii projektów do folderu.|
|**Back**|Przechodzi do poprzednio wybranego elementu.|
|**do przodu**|Przechodzi do następnego zaznaczonego elementu.|
|**Wyświetlanie diagramu klas** (tylko projekty kodu zarządzanego)|Staje się dostępna po wybraniu obszaru nazw lub typu w **widoku klasy**. Po wybraniu obszaru nazw diagram klasy pokazuje wszystkie typy w nim. Po wybraniu typu diagram klasy pokazuje tylko ten typ.|

### <a name="class-view-settings"></a>Ustawienia widoku klasy

Przycisk **Ustawienia widoku klasy** na pasku narzędzi ma następujące ustawienia:

|||
|-|-|
|**Pokaż typy podstawowe**|Wyświetlane są typy podstawowe.|
|**Pokaż odwołania do projektu**|Wyświetlane są odwołania do projektu.|
|**Pokaż ukryte typy i członków**|Ukryte typy i elementy członkowskie (nieprzeznaczone do użytku przez klientów) są wyświetlane w jasnoszarym tekście.|
|**Pokaż członków publicznych**|Zostaną wyświetleni członkowie publiczni.|
|**Pokaż chronionych członków**|Chronione elementy członkowskie są wyświetlane.|
|**Pokaż prywatnych członków**|Zostaną wyświetleni członkowie prywatni.|
|**Pokaż innych członków**|Inne rodzaje członków są wyświetlane, w tym wewnętrznych (lub Friend w języku Visual Basic) członków.|
|**Pokaż odziedziczone elementy członkowskie**|Dziedziczone elementy członkowskie są wyświetlane.|

### <a name="class-view-shortcut-menu"></a>Menu skrótów Widok klasy

Menu skrótu (lub kliknięcie prawym przyciskiem myszy) w **widoku klasy** może zawierać następujące polecenia, w zależności od rodzaju wybranego projektu:

|||
|-|-|
|**Przejdź do definicji**|Znajduje definicję elementu w kodzie źródłowym lub w **przeglądarce obiektów,** jeśli element nie jest zdefiniowany w otwartym projekcie.|
|**Przeglądaj definicję**|Wyświetla zaznaczony element w **przeglądarce obiektów**.|
|**Znajdź wszystkie odwołania**|Wyszukuje aktualnie zaznaczony element obiektu i wyświetla wyniki w oknie **Znajdź wyniki.**|
|**Filtrowanie do typu** (tylko kod zarządzany)|Wyświetla tylko wybrany typ lub obszar nazw. Filtr można usunąć, wybierając przycisk **Wyczyść znajdź** (**X**) obok pola **Znajdź.**|
|**Kopii**|Kopiuje w pełni kwalifikowaną nazwę towaru.|
|**Sortowanie alfabetycznie**|Wyświetla listę typów i członków alfabetycznie według nazwy.|
|**Sortowanie według typu elementu członkowskiego**|Listy typów i elementów członkowskich w kolejności według typu (takie, że klasy poprzedzają interfejsy, interfejsy poprzedzają delegatów, a metody poprzedzają właściwości).|
|**Sortowanie według dostępu do elementu członkowskiego**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, takich jak publiczne lub prywatne.|
|**Grupa według typu elementu członkowskiego**|Sortuje typy i elementy członkowskie w grupy według typu obiektu.|
|**Przejdź do deklaracji** (tylko kod C++)|Wyświetla deklarację typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetlanie hierarchii połączeń**|Wyświetla wybraną metodę w oknie **Hierarchia połączeń.**|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Okno Hierarchia połączeń (Visual Basic, C#, C++)

Okno **Hierarchia wywołań** pokazuje, gdzie wywoływana jest dana metoda lub właściwość. Zawiera również listę metod, które są wywoływane z tej metody. Można wyświetlić wiele poziomów wykresu wywołania, który pokazuje relacje wywołujący wywoływany między metodami w określonym zakresie.

Okno **Hierarchia wywołań** można wyświetlić, wybierając metodę (lub właściwość lub konstruktor) w edytorze, a następnie wybierając **polecenie Wyświetl hierarchię wywołań** w menu skrótów. Wyświetlacz powinien przypominać następujący obraz:

![Okno Hierarchia połączeń w programie Visual Studio](../ide/media/multiplenodes.png)

Korzystając z listy rozwijanej na pasku narzędzi, można określić zakres hierarchii: rozwiązanie, bieżący projekt lub bieżący dokument.

W głównym okienku są wyświetlane wywołania do i z metody, a w okienku **Witryny wywołania** jest wyświetlana lokalizacja wybranego wywołania. Dla elementów członkowskich, które są wirtualne lub abstrakcyjne, zastępuje węzeł **nazwy metody.** Dla elementów członkowskich interfejsu pojawia się węzeł **nazwa metody implementuje.**

Okno **Hierarchia wywołań** nie znajduje odwołań do grup metod, które obejmują miejsca, w których metoda jest dodawana jako program obsługi zdarzeń lub jest przypisana do pełnomocnika. Aby znaleźć te odwołania, użyj polecenia **Znajdź wszystkie odwołania.**

Menu skrótów w oknie **Hierarchia połączeń** zawiera następujące polecenia:

|||
|-|-|
|**Dodaj jako nowy katalog główny**|Dodaje wybrany węzeł jako nowy węzeł główny.|
|**Usuń katalog główny**|Usuwa zaznaczony węzeł główny z okienka widoku drzewa.|
|**Przejdź do definicji**|Przechodzi do oryginalnej definicji metody.|
|**Znajdź wszystkie odwołania**|Znajduje w projekcie wszystkie odwołania do wybranej metody.|
|**Kopii**|Kopiuje zaznaczony węzeł (ale nie jego podwęzły).|
|**Odświeżanie**|Odświeża informacje.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a>Przeglądarka obiektów

Okno **Przeglądarka obiektów** wyświetla opisy kodu w projektach.

Komponenty, które mają być wyświetlane, można filtrować za pomocą listy rozwijanej u góry okna. Składniki niestandardowe mogą zawierać pliki wykonywalne kodu zarządzanego, zestawy bibliotek, biblioteki typów i pliki *ocx.* Nie można dodać składników niestandardowych języka C++.

::: moniker range="vs-2017"

Ustawienia niestandardowe są zapisywane w katalogu aplikacji użytkownika programu Visual Studio, *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

::: moniker-end

::: moniker range=">=vs-2019"

Ustawienia niestandardowe są zapisywane w katalogu aplikacji użytkownika programu Visual Studio, *%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat*.

::: moniker-end

W lewym okienku **przeglądarki obiektów** są wyświetlane zestawy. Można rozwinąć zestawy, aby wyświetlić zawarte w nich przestrzenie nazw, a następnie rozwinąć obszary nazw, aby wyświetlić typy, które zawierają. Po wybraniu typu jego elementy członkowskie (takie jak właściwości i metody) są wyświetlane w prawym okienku. W prawym dolnym okienku są wyświetlane szczegółowe informacje o wybranym elemencie.

Możesz wyszukać określony element, korzystając z pola **Wyszukiwania** w górnej części okna. Wyszukiwanie jest niewrażliwe na sprawy. Wyniki wyszukiwania są wyświetlane w lewym okienku. Aby wyczyścić wyszukiwanie, wybierz przycisk **Wyczyść wyszukiwanie** (**X**) obok pola **Wyszukiwania.**

**Przeglądarka obiektów** śledzi dokonane wybory i można poruszać się między wybranymi opcjami za pomocą przycisków **Prześlij dalej** i **Wstecz** na pasku narzędzi.

Za pomocą **przeglądarki obiektów** można dodać odwołanie do zestawu do otwartego rozwiązania, wybierając element (zestaw, obszar nazw, typ lub element członkowski) i wybierając przycisk **Dodaj odwołanie** na pasku narzędzi.

### <a name="object-browser-settings"></a>Ustawienia przeglądarki obiektów

Za pomocą przycisku **Ustawienia przeglądarki obiektów** na pasku narzędzi można określić jeden z następujących widoków:

|||
|-|-|
|**Wyświetlanie obszarów nazw**|Wyświetla przestrzenie nazw, a nie fizyczne kontenery, w lewym okienku. Obszary nazw przechowywane w wielu kontenerach fizycznych są scalane.|
|**Wyświetl kontenery**|Wyświetla fizyczne kontenery, a nie obszary nazw, w lewym okienku. **Wyświetl przestrzenie nazw** i **Kontenery widoku** są wzajemnie wykluczające się ustawienia.|
|**Pokaż typy podstawowe**|Wyświetla typy bazowe.|
|**Pokaż ukryte typy i członków**|Wyświetla ukryte typy i elementy członkowskie (nieprzeznaczone do użytku przez klientów) w jasnoszarym tekście.|
|**Pokaż członków publicznych**|Wyświetla członków publicznych.|
|**Pokaż chronionych członków**|Wyświetla chronione elementy członkowskie.|
|**Pokaż prywatnych członków**|Wyświetla członków prywatnych.|
|**Pokaż innych członków**|Wyświetla inne typy członków, w tym członków wewnętrznych (lub znajomych w języku Visual Basic).|
|**Pokaż odziedziczone elementy członkowskie**|Wyświetla odziedziczone elementy członkowskie.|
|**Pokaż metody rozszerzenia**|Wyświetla metody rozszerzenia.|

### <a name="object-browser-shortcut-menu-commands"></a>Polecenia menu skrótów przeglądarki obiektów

Menu skrótu (lub kliknięcie prawym przyciskiem myszy) w **przeglądarce obiektów** może zawierać następujące polecenia, w zależności od rodzaju wybranego elementu:

|||
|-|-|
|**Przeglądaj definicję**|Pokazuje węzeł podstawowy dla zaznaczonego elementu.|
|**Znajdź wszystkie odwołania**|Wyszukuje aktualnie zaznaczony element obiektu i wyświetla wyniki w oknie **Znajdź wyniki.**|
|**Filtruj do wpisywać**|Wyświetla tylko wybrany typ lub obszar nazw. Filtr można usunąć, wybierając przycisk **Wyczyść wyszukiwanie.**|
|**Kopii**|Kopiuje w pełni kwalifikowaną nazwę towaru.|
|**Usuń**|Jeśli zakres jest niestandardowym zestawem składników, usuwa wybrany składnik z zakresu.|
|**Sortowanie alfabetycznie**|Wyświetla listę typów i członków alfabetycznie według nazwy.|
|**Sortowanie według typu obiektu**|Listy typów i elementów członkowskich w kolejności według typu (takie, że klasy poprzedzają interfejsy, interfejsy poprzedzają delegatów, a metody poprzedzają właściwości).|
|**Sortowanie według dostępu do obiektu**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, takich jak publiczne lub prywatne.|
|**Grupowanie według typu obiektu**|Sortuje typy i elementy członkowskie w grupy według typu obiektu.|
|**Przejdź do deklaracji** (tylko projekty w języku C++)|Wyświetla deklarację typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetlanie hierarchii połączeń**|Wyświetla wybraną metodę w oknie **Hierarchia połączeń.**|

## <a name="code-definition-window-c"></a>Okno Definicja kodu (C++)

Okno **Definicja kodu** wyświetla definicję wybranego typu języka C++ lub elementu członkowskiego w aktywnym projekcie. Typ lub element członkowski można wybrać w edytorze kodu lub w oknie widoku kodu.

Mimo że to okno jest tylko do odczytu, można ustawić punkty przerwania lub zakładki w nim. Aby zmodyfikować wyświetlaną definicję, wybierz polecenie **Edytuj definicję** w menu skrótów. Spowoduje to otwarcie pliku źródłowego w edytorze kodu i przeniesienie punktu wstawiania do wiersza, w którym rozpoczyna się definicja.

> [!NOTE]
> Począwszy od programu Visual Studio 2015, okno **definicji kodu** można używać tylko z kodem języka C++.

### <a name="code-definition-shortcut-menu"></a>Menu skrótów definicji kodu

Menu skrótu (lub kliknięcie prawym przyciskiem myszy) w oknie **Definicja kodu** może zawierać następujące polecenia:

|||
|-|-|
|**Szybkie akcje i operacje refaktoryzacji**||
|**Zmień nazwę**||
|**Generowanie wykresu plików dołączanych**||
|**Podejrzyj definicję**||
|**Przejdź do definicji**|Znajduje definicję (lub definicje dla klas częściowych) i wyświetla je w oknie **Znajdź wyniki.**|
|**Przejdź do deklaracji**||
|**Znajdź wszystkie odwołania**|Znajduje odwołania do typu lub elementu członkowskiego w rozwiązaniu.|
|**Wyświetlanie hierarchii połączeń**|Wyświetla metodę w oknie **Hierarchia wywołań.**|
|**Przełączanie nagłówka / pliku kodu**||
|**Uruchamianie testów**|Jeśli istnieją testy jednostkowe w projekcie, uruchamia testy dla wybranego kodu.|
|**Testy debugowania**||
|**Punkt przerwania**|Wstawia punkt przerwania (lub punkt śledzenia).|
|**Uruchom do kursora**|Uruchamia program w trybie debugowania do lokalizacji kursora.|
|**Fragment kodu**||
|**Wytnij,** **Kopiuj,** **Wklej**||
|**Adnotacja**||
|**Tworzenie konspektu**|Standardowe polecenia przedstawiające.|
|**Skanuj ponownie**||
|**Edytuj definicję**|Przenosi punkt wstawiania do definicji w oknie kodu.|
|**Wybierz kodowanie**|Otwiera okno **Kodowanie,** dzięki czemu można ustawić kodowanie pliku.|

## <a name="document-outline-window"></a>Okno Konspekt dokumentu

Okna **Konspektu dokumentu** można używać w połączeniu z widokami projektanta, takimi jak projektant strony XAML lub projektanta formularzy systemu Windows lub ze stronami HTML. To okno wyświetla elementy w widoku drzewa, dzięki czemu można wyświetlić strukturę logiczną formularza lub strony i znaleźć formanty, które są głęboko osadzone lub ukryte.

## <a name="see-also"></a>Zobacz też

- [Widok klasy i Przeglądarka obiektów, ikony](../ide/class-view-and-object-browser-icons.md)
