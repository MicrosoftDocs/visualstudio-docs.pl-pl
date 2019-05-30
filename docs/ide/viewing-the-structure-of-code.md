---
title: Widok klas, wywołaj hierarchię, przeglądarka obiektów, okno definicji kodu
ms.date: 05/18/2018
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e2ec8e3e51036749030036eee6ff1d268a44f69
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263068"
---
# <a name="view-the-structure-of-code-using-different-tool-windows"></a>Wyświetlanie struktury kodu za pomocą różne okna narzędzi

Można zbadać klasy i składowe w programie Visual Studio przy użyciu różnych narzędzi systemu windows, w tym **Widok klas**, **hierarchię wywołań,**, **przeglądarki obiektów**i **Kodu definicji** (tylko C++). Te narzędzia okien można sprawdzić kod w projektach programu Visual Studio, składniki .NET Framework, składniki modelu COM, bibliotek dołączanych dynamicznie (DLL), a następnie wpisz biblioteki (TLB).

Można również użyć **Eksploratora rozwiązań** do przeglądania typów i członków w projektach, wyszukiwania symboli, Wyświetl metody hierarchię wywołań, odwołania do symboli Znajdź i inne, bez konieczności przełączania między wieloma oknami narzędzi.

Jeśli masz program Visual Studio Enterprise edition, można użyć *map kodu* wizualizować strukturę kodu i jego zależności dla całego rozwiązania. Aby uzyskać więcej informacji, zobacz [mapowanie zależności z mapami kodu](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Widok klas (Visual Basic, C#, C++)

**Widok klas** jest wyświetlany jako część **Eksploratora rozwiązań** i jako oddzielne okno. **Widok klas** Wyświetla elementy aplikacji. Górne okienko wyświetla przestrzenie nazw, typów, interfejsów, wyliczenia i klas oraz dolne okienko elementów członkowskich, które należą do wybranego w górnym okienku typu. Korzystając z tego okna, można przenieść do definicji elementu członkowskiego w kodzie źródłowym (lub **przeglądarki obiektów** Jeśli element jest zdefiniowane poza rozwiązania).

Nie masz do skompilowania projektu, aby wyświetlić jego elementy w **Widok klas**. Okno zostanie odświeżony, jak zmodyfikować kod w projekcie.

Możesz dodać kod do projektu, wybierając węzeł projektu i wybierając pozycję **Dodaj** przycisk, aby otworzyć **Dodaj nowy element** okno dialogowe. Kod zostanie dodany w oddzielnym pliku.

Jeśli projekt jest zaewidencjonowane do kontroli kodu źródłowego, co **Widok klas** element Wyświetla ikonę która wskazuje stan kodu źródłowego, pliku. Polecenia wspólnej kontroli kodu źródłowego, takie jak **Wyewidencjonuj**, **Zaewidencjonuj**, i **Pobierz najnowszą wersję** są również dostępne w menu skrótów dla elementu.

### <a name="class-view-toolbar"></a>Pasek narzędzi widoku klasy

**Widok klas** narzędzi zawiera następujące polecenia:

|||
|-|-|
|**Nowy Folder**|Tworzy folder wirtualny lub podfolder, w którym można organizować często używanych elementów. Są one zapisywane w aktywnym rozwiązaniu (*.suo*) pliku. Po nazwy lub usunięcie elementu w kodzie, może się pojawić folder wirtualny jako węzeł błędu. Aby rozwiązać ten problem, Usuń węzeł błędu. Jeśli zmieniono element możesz przenieść je z hierarchii projektu do folderu ponownie.|
|**Wstecz**|Powoduje przejście do poprzednio wybranego elementu.|
|**do przodu**|Powoduje przejście do następnego wybranego elementu.|
|**Pokaż Diagram klas** (zarządzane tylko projekty kodu)|Staje się dostępne po wybierz przestrzeń nazw lub wpisać **Widok klas**. Po wybraniu przestrzeni nazw na diagramie klasy są wyświetlane wszystkie typy w nim. Po wybraniu typu na diagramie klasy pokazuje tylko tego typu.|

### <a name="class-view-settings"></a>Widok klasy: ustawienia

**Widok klasy: ustawienia** przycisk na pasku narzędzi ma następujące ustawienia:

|||
|-|-|
|**Pokaż typy podstawowe**|Typy podstawowe są wyświetlane.|
|**Pokaż typy pochodne**|Typy pochodne są wyświetlane.|
|**Pokaż ukryte typy i składowe**|Ukryte typy i składowe (nie przeznaczony do użycia przez klientów) są wyświetlane na szary tekst.|
|**Pokaż publiczne składowe**|Publiczne elementy członkowskie są wyświetlane.|
|**Pokaż chronione składowe**|Chronione elementy członkowskie są wyświetlane.|
|**Pokaż prywatne składowe**|Prywatne elementy członkowskie są wyświetlane.|
|**Pokaż pozostałe składowe**|Inne rodzaje elementów członkowskich są wyświetlane, łącznie z wewnętrznego (lub Friend w języku Visual Basic) elementy członkowskie.|
|**Pokaż odziedziczone składowe**|Dziedziczone elementy członkowskie są wyświetlane.|
|**Pokaż metody rozszerzenia**|Metody rozszerzenia są wyświetlane.|

### <a name="class-view-shortcut-menu"></a>Menu skrótów w widoku klas

Menu skrótów na liście **Widok klas** może zawierać następujące polecenia, w zależności od typu wybranego projektu:

|||
|-|-|
|**Przejdź do definicji**|Umożliwia znalezienie definicję elementu kodu źródłowego lub w **przeglądarki obiektów**, jeśli element nie jest zdefiniowany w otwartym projekcie.|
|**Przeglądaj definicję**|Wyświetla wybrany element w **przeglądarki obiektów**.|
|**Znajdź wszystkie odwołania**|Wyszukuje element aktualnie zaznaczonego obiektu i wyświetla wyniki w parametrze **Find Results** okna.|
|**Typ filtru** (tylko kod zarządzany)|Wyświetla tylko wybranego typu lub przestrzeni nazw. Możesz usunąć filtr, wybierając **wyczyść znaleźć** (**X**) znajdujący się obok **znaleźć** pole.|
|**Kopiuj**|Kopiuje w pełni kwalifikowana nazwa elementu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i elementów członkowskich alfabetycznie według nazwy.|
|**Sortuj według typu składowej**|Wyświetla listę typów i elementów członkowskich w kolejności według typu (taki sposób, że klasy poprzedzać interfejsów, interfejsy, należy poprzedzić delegatów i metod poprzedzać właściwości).|
|**Sortuj według dostępu do elementu członkowskiego**|Wyświetla typy i elementy członkowskie w kolejności według dostępu typ, takich jak publiczny lub prywatny.|
|**Grupuj według typu składowej**|Sortuje typów i elementów członkowskich do grup według typu obiektu.|
|**Przejdź do deklaracji** (tylko kod C++)|Wyświetla deklaracji typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do odwołania**|Wyświetla odwołania do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Pokaż hierarchię wywołań**|Wyświetla wybranej metody w **hierarchię wywołań** okna.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Okno hierarchii wywołań (Visual Basic C#, języka C++)

**Hierarchię wywołań** okno pokazuje, gdzie jest wywoływana danej metody lub właściwości. Zawiera również listę metod, które są wywoływane z tej metody. Można wyświetlić wiele poziomów wykresu wywołań, który pokazuje wywołującego/wywoływanego relacje metody w określonym zakresie.

Możesz wyświetlić **hierarchię wywołań,** okna, wybierając metodę (lub właściwości lub konstruktora) w edytorze, a następnie wybierając **Pokaż hierarchię wywołań,** w menu skrótów. Ekran powinien przypominać ilustrację poniżej:

![Okno hierarchii wywołań w programie Visual Studio](../ide/media/multiplenodes.png)

Za pomocą listy rozwijanej na pasku narzędzi, można określić zakres hierarchii: rozwiązanie, bieżącego projektu lub bieżącego dokumentu.

W okienku głównym wyświetlana wywołania do i z metody i **wywołać witryn** okienko Wyświetla lokalizację wybranego połączenia. Dla elementów członkowskich, które są wirtualne ani abstrakcyjne **nazwę metody zastąpienia** węzeł jest dostępny. Dla członków interfejsu **nazwę metody implementuje** węzeł jest dostępny.

**Hierarchię wywołań** okna nie znaleźć metody odwołania do grupy, które obejmują miejsca, w którym metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisany do delegata. Aby znaleźć te odwołania, użyj **Znajdź wszystkie odwołania** polecenia.

Menu skrótów na liście **hierarchię wywołań** okno zawiera następujące polecenia:

|||
|-|-|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł jako nowy węzeł główny.|
|**Usuń element główny**|Usuwa wybrany główny węzeł, w okienku widoku drzewa.|
|**Przejdź do definicji**|Powoduje przejście do oryginalnej definicji metody.|
|**Znajdź wszystkie odwołania**|Wyszukuje w projekcie wszystkie odwołania do wybranej metody.|
|**Kopiuj**|Kopiuje wybrany węzeł (ale nie jego węzły podrzędne).|
|**Odśwież**|Odświeża informacje.|

## <a name="BKMK_ObjectBrowser"></a> Przeglądarka obiektów

**Przeglądarki obiektów** okno zawiera opisy kodu w projektach.

Można filtrować składniki, które chcesz wyświetlić za pomocą listy rozwijanej w górnej części okna. Składniki niestandardowe mogą obejmować pliki wykonywalne kodu zarządzanego, zestawy bibliotek, bibliotek typów i *.ocx* plików. Nie jest możliwe dodać niestandardowe składniki C++.

::: moniker range="vs-2017"

Ustawienia niestandardowe są zapisywane w katalogu aplikacji programu Visual Studio użytkownika *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

::: moniker-end

::: moniker range=">=vs-2019"

Ustawienia niestandardowe są zapisywane w katalogu aplikacji programu Visual Studio użytkownika *%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat*.

::: moniker-end

Okienka po lewej stronie z **przeglądarki obiektów** pokazuje zestawy. Można rozwinąć zestawów do wyświetlenia przestrzenie nazw, które zawierają, a następnie rozwiń przestrzenie nazw, aby wyświetlić typy, które zawierają. Po wybraniu typu, jej elementów członkowskich (na przykład właściwości i metody) są wyświetlane w okienku po prawej stronie. Dolnym okienku po prawej stronie wyświetla szczegółowe informacje na temat wybranego elementu.

Możesz wyszukać konkretny element przy użyciu **wyszukiwania** polu w górnej części okna. Wyszukiwanie jest rozróżniana wielkość liter. Wyniki wyszukiwania są wyświetlane w okienku po lewej stronie. Aby wyczyścić wyszukiwanie, wybierz opcję **Wyczyść wyszukiwanie** (**X**) znajdujący się obok **wyszukiwania** pole.

**Przeglądarki obiektów** śledzi mają dokonanych wyborów i nawigować między opcje przy użyciu **do przodu** i **ponownie** przycisków na pasku narzędzi.

Możesz użyć **przeglądarki obiektów** można dodać odwołania do zestawu otwartego rozwiązania zaznaczenie elementu (zestawu, przestrzeni nazw, typ lub składowa) i wybierając polecenie **Dodaj odwołanie** przycisk na pasku narzędzi.

### <a name="object-browser-settings"></a>Ustawienia przeglądarki obiektów

Za pomocą **ustawienia przeglądarki obiektów** przycisk na pasku narzędzi, możesz określić jedną z następujących widoków:

|||
|-|-|
|**Wyświetl w przestrzeni nazw**|Wyświetla przestrzenie nazw, a nie fizycznej kontenerów, w okienku po lewej stronie. Przestrzenie nazw, przechowywane w wielu kontenerach fizyczne są scalane.|
|**Wyświetl kontenerów**|Wyświetla kontenery fizyczne, a nie w przestrzeni nazw, w okienku po lewej stronie. **Wyświetlanie przestrzenie nazw** i **kontenery widoku** ustawień wzajemnie się wykluczają.|
|**Pokaż typy podstawowe**|Wyświetla typy podstawowe.|
|**Pokaż typy pochodne**|Wyświetla typy pochodne.|
|**Pokaż ukryte typy i składowe**|Wyświetla ukryte typy i elementy członkowskie (nie przeznaczony do użycia przez klientów), w szary tekst.|
|**Pokaż publiczne składowe**|Wyświetla publiczne elementy członkowskie.|
|**Pokaż chronione składowe**|Wyświetla chronionych składowych.|
|**Pokaż prywatne składowe**|Wyświetla prywatnych elementów członkowskich.|
|**Pokaż pozostałe składowe**|Wyświetla członków innych rodzajów elementów członkowskich, łącznie z wewnętrznego (lub Friend w języku Visual Basic).|
|**Pokaż odziedziczone składowe**|Wyświetla dziedziczone elementy członkowskie.|
|**Pokaż metody rozszerzenia**|Zawiera metody rozszerzenia.|

### <a name="object-browser-shortcut-menu-commands"></a>Polecenia menu skrótów przeglądarki obiektów

Menu skrótów na liście **przeglądarki obiektów** może zawierać następujące polecenia, w zależności od rodzaju elementu wybrane:

|||
|-|-|
|**Przeglądaj definicję**|Pokazuje węzła podstawowego dla wybranego elementu.|
|**Znajdź wszystkie odwołania**|Wyszukuje element aktualnie zaznaczonego obiektu i wyświetla wyniki w parametrze **Find Results** okna.|
|**Filtruj typy**|Wyświetla tylko wybranego typu lub przestrzeni nazw. Możesz usunąć filtr, wybierając **Wyczyść wyszukiwanie** przycisku.|
|**Kopiuj**|Kopiuje w pełni kwalifikowana nazwa elementu.|
|**Usuń**|Jeśli zakres jest zbiór niestandardowych składników, Usuwa wybrany składnik z zakresu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i elementów członkowskich alfabetycznie według nazwy.|
|**Sortuj według typu obiektu**|Wyświetla listę typów i elementów członkowskich w kolejności według typu (taki sposób, że klasy poprzedzać interfejsów, interfejsy, należy poprzedzić delegatów i metod poprzedzać właściwości).|
|**Sortuj według dostępu do obiektów**|Wyświetla typy i elementy członkowskie w kolejności według dostępu typ, takich jak publiczny lub prywatny.|
|**Grupuj według typu obiektu**|Sortuje typów i elementów członkowskich do grup według typu obiektu.|
|**Przejdź do deklaracji** (projektów w języku C++ tylko)|Wyświetla deklaracji typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Przejdź do odwołania**|Wyświetla odwołania do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępna.|
|**Pokaż hierarchię wywołań**|Wyświetla wybranej metody w **hierarchię wywołań** okna.|

## <a name="code-definition-window-c"></a>Okno definicji kodu (C++)

**Definicji kodu** definicji wybranego typu C++ lub elementu członkowskiego w oknie zostaną wyświetlone w aktywnym projekcie. W edytorze kodu lub w oknie Widok kodu można wybrać typ lub element członkowski.

Chociaż w tym oknie jest tylko do odczytu, można ustawić punktów przerwania lub zakładki w nim. Aby zmodyfikować definicję wyświetlany, wybierz opcję **Edytuj definicję** w menu skrótów. To spowoduje otwarcie pliku źródłowego w edytorze kodu i przenosi punkt wstawiania do wiersza, w którym rozpoczyna się definicji.

> [!NOTE]
> Począwszy od programu Visual Studio 2015 **definicji kodu** okna można używać tylko przy użyciu kodu w języku C++.

### <a name="code-definition-shortcut-menu"></a>Menu skrótów definicji kodu

Menu skrótów na liście **definicji kodu** okna może zawierać następujących poleceń:

|||
|-|-|
|**Szybkie akcje i operacje refaktoryzacji**||
|**Zmiana nazwy**||
|**Generowanie grafu plików dołączanych**||
|**Zobacz definicję**||
|**Przejdź do definicji**|Umożliwia znalezienie definicji (lub definicje klas częściowych), a następnie wyświetli je w **Find Results** okna.|
|**Przejdź do deklaracji**||
|**Znajdź wszystkie odwołania**|Umożliwia znalezienie odwołania do typu lub elementu członkowskiego w rozwiązaniu.|
|**Pokaż hierarchię wywołań**|Wyświetla metodę w **hierarchię wywołań** okna.|
|**Przełącz nagłówek / plik kodu**||
|**Uruchom testy**|W przypadku testów jednostkowych w projekcie, uruchamia testy dla zaznaczonego kodu.|
|**Debuguj testy**||
|**Punkt przerwania**|Wstawia punkt przerwania (lub punkt śledzenia).|
|**Uruchom do kursora**|Uruchamia program w trybie debugowania do lokalizacji kursora.|
|**Fragment kodu**||
|**Wytnij**, **kopiowania**, **wklejania**||
|**Adnotacja**||
|**Obramowanie**|Standardowe polecenia konspektu.|
|**Skanuj ponownie**||
|**Edytuj definicję**|Przenosi punkt wstawiania do definicji w oknie kodu.|
|**Wybierz kodowanie**|Otwiera **kodowanie** okna tak, aby ustawić kodowanie dla tego pliku.|

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Możesz użyć **konspekt dokumentu** okna w połączeniu z projektanta widoków, takich jak projektant dla strony XAML lub projektanta formularza Windows lub strony HTML. To okno wyświetla elementy w widoku drzewa, dzięki czemu można wyświetlać Struktura logiczna formularza lub strony i Znajdź formantów, które głęboko zagnieżdżony lub ukryte.

## <a name="see-also"></a>Zobacz także

- [Widok klasy i Przeglądarka obiektów, ikony](../ide/class-view-and-object-browser-icons.md)
