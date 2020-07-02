---
title: Wyświetlanie struktury kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
- document outline window.
- Visual Studio, object browser
- Visual Studio, code definition window
- call hierarchy
- Visual Studio, document outline window
- code definition window
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
ms.assetid: e6064f58-5ad9-4f05-8c3f-12e994b6583f
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1a860fbb88bb15786fad5fdf277f8f65b245056b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545018"
---
# <a name="viewing-the-structure-of-code"></a>Wyświetlanie struktury kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można przeanalizować obiekty i członków w projektach programu Visual Studio oraz obiekty i elementy członkowskie w .NET Framework składniki, składniki COM, biblioteki dołączane dynamicznie (DLL) i biblioteki typów (TLB).

 W poniższych sekcjach tego dokumentu opisano różne okna struktury kodu.

 [Widok klasy (Visual Basic, C#, C++)](#BKMK_ClassView)

 [Hierarchia wywołań (Visual Basic, C#, C++)](#BKMK_CallHierarchy)

 [Przeglądarka obiektów](#BKMK_ObjectBrowser)

 [Okno definicji kodu (C#, C++)](#BKMK_CodeDefinition)

 Możesz również użyć **Eksplorator rozwiązań** do przeglądania typów i członków w projektach, wyszukiwania symboli, wyświetlania hierarchii wywołań metod, znajdowania odwołań do symboli i innych elementów bez konieczności przełączania się między wymienionymi wcześniej oknami narzędzi.

 Jeśli masz Visual Studio Enterprise możesz użyć map kodu do wizualizacji struktury kodu i jego zależności w całym rozwiązaniu, a następnie przechodzenie do części kodu, który Cię interesuje. Aby uzyskać więcej informacji, zobacz [Mapowanie zależności między rozwiązaniami](../modeling/map-dependencies-across-your-solutions.md).

> [!NOTE]
> Wersja programu Visual Studio i używane ustawienia mogą mieć wpływ na funkcje w środowisku IDE. Mogą się one różnić od tych opisanych w tym temacie.

## <a name="class-view-visual-basic-c-c"></a><a name="BKMK_ClassView"></a>Widok klasy (Visual Basic, C#, C++)
 **Widok klasy** jest pokazywany jako część **Eksplorator rozwiązań** , jak również w osobnym oknie. W oknie **Widok klasy** są wyświetlane elementy aplikacji. W górnym okienku są wyświetlane przestrzenie nazw, typy, interfejsy, wyliczenia i klasy, a w dolnym okienku są wyświetlane elementy członkowskie należące do typu wybranego w górnym okienku. Za pomocą tego okna można przenieść do definicji elementów członkowskich w kodzie źródłowym (lub w **Przeglądarka obiektów** , jeśli element jest zdefiniowany poza rozwiązaniem).

 Nie trzeba kompilować projektu, aby wyświetlić jego elementy **Widok klasy**. Okno jest odświeżane w miarę modyfikowania kodu w projekcie.

 Możesz dodać kod do projektu, wybierając węzeł projektu i wybierając przycisk **Dodaj** , aby otworzyć okno dialogowe **Dodaj nowy element** . Kod zostanie dodany w osobnym pliku.

 Jeśli projekt jest zaewidencjonowany do kontroli kodu źródłowego, każdy element **Widok klasy** wyświetli ikonę wskazującą stan kodu źródłowego pliku. Typowe polecenia kontroli kodu źródłowego, takie jak **wyewidencjonowywanie**, **ewidencjonowanie**i **pobieranie najnowszej wersji** są również dostępne w menu skrótów dla elementu.

### <a name="class-view-toolbar"></a>Widok klasy pasek narzędzi
 Pasek narzędzi Widok klasy zawiera następujące polecenia.

|Polecenie|Opis|
|-|-|
|**Nowy folder**|Tworzy folder wirtualny lub podfolder, w którym można organizować często używane elementy. Są one zapisywane w aktywnym pliku rozwiązania (. suo). Po zmianie nazwy lub usunięciu elementu w kodzie może on pojawić się w folderze wirtualnym jako węzeł błędu. Aby rozwiązać ten problem, Usuń węzeł błędu. Jeśli zmieniono nazwę elementu, można go przenieść z hierarchii projektu do folderu ponownie.|
|**Wstecz**|Przechodzi do poprzednio wybranego elementu.|
|**do przodu**|Przechodzi do następnego wybranego elementu.|
|**Widok diagramu klas** (tylko projekty kodu zarządzanego)|Staną się dostępne po wybraniu przestrzeni nazw lub typu w **Widok klasy**. Po wybraniu przestrzeni nazw Diagram klas pokazuje wszystkie typy w nim. Po wybraniu typu Diagram klas pokazuje tylko ten typ.|

### <a name="class-view-settings"></a>Ustawienia Widok klasy
 Przycisk **ustawienia widok klasy** na pasku narzędzi ma następujące ustawienia.

|Nazwa|Opis|
|-|-|
|**Pokaż typy podstawowe**|Typy podstawowe są wyświetlane.|
|**Pokaż typy pochodne**|Typy pochodne są wyświetlane.|
|**Pokaż ukryte typy i składowe**|Ukryte typy i elementy członkowskie (nieprzeznaczone do użycia przez klientów) są wyświetlane w kolorze szarym.|
|**Pokaż publiczne składowe**|Wyświetlane są publiczne składowe.|
|**Pokaż chronione elementy członkowskie**|Są wyświetlane chronione elementy członkowskie.|
|**Pokaż prywatne składowe**|Wyświetlane są prywatne składowe.|
|**Pokaż inne elementy członkowskie**|Są wyświetlane inne rodzaje elementów członkowskich, w tym wewnętrzne (lub zaprzyjaźnione w Visual Basic) członków.|
|**Pokaż Odziedziczone składowe**|Są wyświetlane dziedziczone elementy członkowskie.|
|**Pokaż metody rozszerzenia**|Są wyświetlane metody rozszerzające.|

### <a name="class-view-shortcut-menu"></a>Widok klasy menu skrótów
 Menu skrótów w **Widok klasy** może zawierać następujące polecenia, w zależności od wybranego typu projektu.

|Polecenie|Opis|
|-|-|
|**Przejdź do definicji**|Znajduje definicję elementu w kodzie źródłowym lub w **Przeglądarka obiektów**, jeśli element nie jest zdefiniowany w otwartym projekcie.|
|**Przeglądaj definicję**|Wyświetla wybrany element w **Przeglądarka obiektów**.|
|**Znajdź wszystkie odwołania**|Znajduje aktualnie zaznaczony element obiektu i wyświetla wyniki w oknie **Wyszukiwanie wyników** .|
|**Filtruj do typu** (tylko kod zarządzany)|Wyświetla tylko wybrany typ lub przestrzeń nazw. Filtr można usunąć, wybierając przycisk **Wyczyść wyszukiwanie** (X) obok pola **Znajdź** .|
|**Kopiuj**|Kopiuje w pełni kwalifikowaną nazwę elementu.|
|**Sortuj alfabetycznie**|Wyświetla listę typów i składowych alfabetycznie według nazwy.|
|**Sortuj według typu elementu członkowskiego**|Wyświetla listę typów i składowych w kolejności według typu (takie jak klasy poprzedzają interfejsy, interfejsy poprzedzają delegatów, a metody poprzedzają właściwości).|
|**Sortuj według dostępu do składowej**|Wyświetla listę typów i elementów członkowskich w kolejności według typu dostępu, na przykład Public lub Private.|
|**Grupuj według typu elementu członkowskiego**|Sortuje typy i składowe w grupach według typu obiektu.|
|**Przejdź do deklaracji** (tylko kod C++)|Wyświetla deklarację typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetl hierarchię wywołań**|Wyświetla wybraną metodę w oknie **Hierarchia wywołań** .|

## <a name="call-hierarchy-visual-basic-c-c"></a><a name="BKMK_CallHierarchy"></a>Hierarchia wywołań (Visual Basic, C#, C++)
 Okno **Hierarchia wywołań** pokazuje, gdzie wywoływana jest dana metoda (lub właściwość lub Konstruktor), a także listę metod, które są wywoływane z tej metody. Można wyświetlić wiele poziomów grafu wywołań, który pokazuje relacje wywołujące/wywoływane między metodami w określonym zakresie.

 Możesz wyświetlić okno **Hierarchia wywołań** , wybierając metodę (lub konstruktora), a następnie wybierając opcję **Wyświetl hierarchię klas** w menu skrótów. Ekran powinien wyglądać podobnie do poniższej ilustracji.

 ![Otwórz hierarchię wywołań z wieloma węzłami](../ide/media/multiplenodes.png "MultipleNodes") Okno hierarchii wywołań

 Za pomocą listy rozwijanej na pasku narzędzi można określić zakres hierarchii: rozwiązanie, bieżący projekt lub bieżący dokument.

 W okienku głównym są wyświetlane wywołania do i z metody, a w okienku **Wywołaj Lokacje** zostanie wyświetlona lokalizacja wybranego wywołania. W przypadku elementów członkowskich, które są wirtualne lub abstrakcyjne, zostanie wyświetlony węzeł **Nazwa metody zastąpień** . W przypadku elementów członkowskich interfejsu pojawia się węzeł **Nazwa metody implementującej** .

 W oknie **Hierarchia wywołań** nie znajdują się odwołania do grup metod, w tym miejsca, w których metoda jest dodawana jako procedura obsługi zdarzeń lub jest przypisana do delegata. Aby znaleźć te odwołania, użyj polecenia **Znajdź wszystkie odwołania** .

 Menu skrótów w oknie **Hierarchia wywołań** zawiera następujące polecenia.

|Polecenie|Opis|
|-|-|
|**Dodaj jako nowy element główny**|Dodaje wybrany węzeł jako nowy węzeł główny.|
|**Usuń element główny**|Usuwa wybrany węzeł główny z okienka widoku drzewa.|
|**Przejdź do definicji**|Przechodzi do oryginalnej definicji metody.|
|**Znajdź wszystkie odwołania**|Znajduje w projekcie wszystkie odwołania do wybranej metody.|
|**Kopiuj**|Kopiuje wybrany węzeł (ale nie jego węzły podrzędne).|
|**Odświeżanie**|Odświeża informacje.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a>Przeglądarka obiektów
 **Przeglądarka obiektów** Wyświetla opisy kodu w projektach.

 Można filtrować elementy, które mają być wyświetlane w **Przeglądarka obiektów**. Korzystając z listy rozwijanej w górnej części okna, można wybrać jedną z następujących opcji:

- Wszystkie .NET Framework

- Silverlight

- Aktywne rozwiązanie

- Niestandardowy zestaw składników

  Składniki niestandardowe mogą obejmować pliki wykonywalne kodu zarządzanego, zestawy bibliotek, biblioteki typów i plików OCX. Nie można dodać niestandardowych składników języka C++. Ustawienia niestandardowe są zapisywane w katalogu aplikacji użytkownika programu Visual Studio,%APPDATA%\Roaming\Microsoft\VisualStudio\11.0\ObjBrowEX.dat.

  W lewym okienku **Przeglądarka obiektów** są wyświetlane kontenery fizyczne, takie jak .NET Framework i składniki com. Można rozwinąć węzły kontenera, aby wyświetlić zawarte w nich przestrzenie nazw, a następnie rozwinąć przestrzenie nazw, aby wyświetlić typy, które zawierają. Po wybraniu typu, jego elementy członkowskie (takie jak właściwości i metody) są wyświetlane w okienku po prawej stronie. W dolnym okienku po prawej stronie są wyświetlane szczegółowe informacje o wybranym elemencie.

  Konkretny element można wyszukać, korzystając z pola **wyszukiwania** w górnej części okna. W wyszukiwaniu nie jest rozróżniana wielkość liter. Wyniki wyszukiwania są wyświetlane w okienku po lewej stronie. Aby wyczyścić wyszukiwanie, wybierz przycisk **Wyczyść wyszukiwanie** (X) obok pola **wyszukiwania** .

  **Przeglądarka obiektów** śledzi dokonane wybory i można przechodzić między wybranymi elementami przy użyciu przycisków **do przodu** i do **tyłu** na pasku narzędzi.

  Możesz użyć **Przeglądarka obiektów** , aby dodać odwołanie do zestawu do otwartego rozwiązania, wybierając element (zestaw, przestrzeń nazw, typ lub element członkowski) i wybierając przycisk **Dodaj odwołanie** na pasku narzędzi.

### <a name="object-browser-settings"></a>Ustawienia Przeglądarka obiektów
 Za pomocą przycisku **ustawienia Przeglądarka obiektów** na pasku narzędzi można określić jeden z następujących widoków.

|Nazwa|Opis|
|-|-|
|**Wyświetl przestrzenie nazw**|Wyświetla przestrzenie nazw, a nie kontenery fizyczne, w okienku po lewej stronie. Obszary nazw przechowywane w wielu kontenerach fizycznych są scalane.|
|**Wyświetl kontenery**|Wyświetla kontenery fizyczne, a nie przestrzenie nazw, w okienku po lewej stronie. **Wyświetl obszary nazw** i **kontenery widoku** są wzajemnie wykluczające się ustawienia.|
|**Pokaż typy podstawowe**|Wyświetla typy podstawowe.|
|**Pokaż typy pochodne**|Wyświetla typy pochodne.|
|**Pokaż ukryte typy i składowe**|Wyświetla ukryte typy i elementy członkowskie (nie przeznaczone do użycia przez klientów) w jasnym kolorze szarym.|
|**Pokaż publiczne składowe**|Wyświetla publiczne elementy członkowskie.|
|**Pokaż chronione elementy członkowskie**|Wyświetla chronione elementy członkowskie.|
|**Pokaż prywatne składowe**|Wyświetla prywatnych członków.|
|**Pokaż inne elementy członkowskie**|Wyświetla inne typy elementów członkowskich, w tym wewnętrzne (lub zaprzyjaźnione w Visual Basic) członków.|
|**Pokaż Odziedziczone składowe**|Wyświetla dziedziczone elementy członkowskie.|
|**Pokaż metody rozszerzenia**|Wyświetla metody rozszerzenia.|

### <a name="object-browser-shortcut-menu-commands"></a>Polecenia menu skrótów Przeglądarka obiektów
 Menu skrótów w **Przeglądarka obiektów** mogą zawierać następujące polecenia, w zależności od rodzaju wybranego elementu.

|Polecenie|Opis|
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
|**Przejdź do deklaracji** (tylko projekty C++)|Wyświetla deklarację typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do definicji**|Wyświetla definicję typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Przejdź do odwołania**|Wyświetla odwołanie do typu lub elementu członkowskiego w kodzie źródłowym, jeśli jest dostępny.|
|**Wyświetl hierarchię wywołań**|Wyświetla wybraną metodę w oknie **Hierarchia wywołań** .|

## <a name="code-definition-window-c-c"></a><a name="BKMK_CodeDefinition"></a>Okno definicji kodu (C#, C++)
 W oknie **definicji kodu** zostanie wyświetlona definicja wybranego typu lub elementu członkowskiego w aktywnym projekcie. Typ lub element członkowski można wybrać w edytorze kodu lub w oknie widoku kodu.

 Mimo że to okno jest tylko do odczytu, można ustawić punkty przerwania lub zakładki. Aby zmodyfikować wyświetlaną definicję, wybierz polecenie **Edytuj definicję** w menu skrótów. Spowoduje to otwarcie pliku źródłowego w edytorze kodu i przeniesienie punktu wstawiania do wiersza, w którym rozpoczyna się definicja.

### <a name="code-definition-shortcut-menu"></a>Menu skrótów definicji kodu
 Menu skrótów w oknie **definicji kodu** może zawierać następujące polecenia, w zależności od języka programowania.

|Polecenie|Opis|
|-|-|
|**Utwórz testy jednostkowe**|Tworzy testy jednostkowe dla wybranego elementu.|
|**Generuj diagram sekwencji**|Gdy wybrana jest metoda, generuje diagram sekwencji.|
|**Tworzenie prywatnego dostępu**|Jeśli test jednostkowy jest obecny w rozwiązaniu, generuje metodę, która jest stosowana przez test w celu uzyskania dostępu do kodu.|
|**Przejdź do definicji**|Znajduje definicję (lub definicje, dla klas częściowych) i wyświetla je w oknie **Znajdź wyniki** .|
|**Znajdź wszystkie odwołania**|Znajduje odwołania do typu lub elementu członkowskiego w rozwiązaniu.|
|**Wyświetl hierarchię wywołań**|Wyświetla metodę w oknie **Hierarchia wywołań** .|
|**Pokaż testy wywołań**|Jeśli w projekcie są testy jednostkowe, program wyświetli testy wywołujące wybrany kod.|
|**Uruchom testy wywołujące**|Jeśli w projekcie są testy jednostkowe, program uruchamia testy dla zaznaczonego kodu.|
|**Punkt**|Wstawia punkt przerwania (lub punkt śledzenia).|
|**Uruchom do kursora**|Uruchamia program w trybie debugowania do lokalizacji kursora.|
|**Kopiuj**|Kopiuje wybrany wiersz.|
|**Tworzenie konspektu**|Standardowe polecenia tworzenia konspektu.|
|**Edytuj definicję**|Przenosi punkt wstawiania do definicji w oknie kodu.|
|**Wybierz kodowanie**|Otwiera okno **kodowania** , aby można było ustawić kodowanie dla tego pliku.|

### <a name="document-outline-window"></a>Okno konspektu dokumentu
 Możesz użyć okna **Konspekt dokumentu** w połączeniu z widokami projektanta, takimi jak projektant dla strony XAML lub Projektant formularzy systemu Windows lub za pomocą stron HTML. To okno wyświetla elementy w widoku drzewa, aby można było wyświetlić logiczną strukturę formularza lub strony oraz znaleźć formanty, które są głęboko osadzone lub ukryte.

## <a name="see-also"></a>Zobacz też
 [Widok klasy i Przeglądarka obiektów ikon](../ide/class-view-and-object-browser-icons.md)
