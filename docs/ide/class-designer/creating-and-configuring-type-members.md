---
title: Tworzenie i konfigurowanie typów członków (Projektant klas)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7063b536c50cff39bfeb3adabe989b3cd9a56ddf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828140"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Tworzenie i konfigurowanie składowych typu w Projektancie klas

Możesz dodać te składowe do typów w klasie na diagramie i skonfigurować te składowe w **szczegóły klasy** okna:

|**Typ**|**Elementy członkowskie, jakie mogą one zawierać**|
|--------------| - |
|Class|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Wyliczenie|członek|
|Interface|metoda, właściwość, zdarzenie (w języku C# i Visual Basic)|
|Klasa abstrakcyjna|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Struktura (konstrukcja Struct w języku C#)|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), stała|
|Delegate|parametr|
|Moduł (tylko w języku VB)|metoda, właściwość, pole, zdarzenie, konstruktor, stała|

> [!NOTE]
> Utwórz bardziej zwartą deklarację właściwości, gdy akcesory właściwości get i set nie potrzebują dodatkowej logiki, za pomocą automatycznie wdrożonych właściwości (tylko C#). Aby wyświetlić pełny podpis z **Diagram klas** menu wybierz opcję **Zmień Format elementów członkowskich** > **Wyświetl pełną sygnaturę**. Aby uzyskać więcej informacji dotyczących automatycznie implementowanych właściwości, zobacz [implemented Properties](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pomocnicza|
|----------| - |
|**Rozpocznij pracę:** Zanim utworzysz i skonfigurujesz składowe typu, należy otworzyć **szczegóły klasy** okna.|- [Otwieranie okna Szczegóły klasy](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Uwagi dotyczące użycia szczegóły klasy](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Wyświetlanie informacji tylko do odczytu](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Skróty myszy i klawiatury w oknie Diagram klas i szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Tworzenie i modyfikowanie składowych typu:** Tworzenie nowych elementów członkowskich, modyfikowanie składowych i Dodawanie parametrów do metody przy użyciu **szczegóły klasy** okna.|- [Utwórz członków](creating-and-configuring-type-members.md#create-members)<br />- [Modyfikowanie składowych typu](creating-and-configuring-type-members.md#modify-type-members)<br />- [Dodaj parametry do metod](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otwieranie okna Szczegóły klasy

Domyślnie **szczegóły klasy** zostanie wyświetlone okno automatycznie po otwarciu nowego diagramu klas. Zobacz [jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md)). Możesz również otworzyć **szczegóły klasy** okna w następujący sposób:

- Kliknij prawym przyciskiem myszy w dowolnej klasie na diagramie, aby wyświetlić menu kontekstowe, a następnie wybierz **szczegóły klasy**.

- Wybierz **widoku** > **Windows inne** > **szczegóły klasy** z paska menu.

## <a name="create-members"></a>Utwórz członków

Można utworzyć element członkowski, używając dowolnego z następujących narzędzi:

- **Projektant klas**

- **Klasa szczegóły** pasek narzędzi okna

- **Klasa szczegóły** okna

> [!NOTE]
> Można również utworzyć konstruktory i destruktory przy użyciu procedur opisanych w tej sekcji. Należy pamiętać, że konstruktory i destruktory to szczególne rodzaje metod i jako takie pojawiają się na **metody** przedziału w kształtach diagramu klas i w **metody** sekcji  **Klasa szczegóły** siatki okna.

> [!NOTE]
> Jedyna jednostka, jaką można dodać do obiektu delegowanego, to parametr. Należy pamiętać, że uprawniony procedury "Aby utworzyć składową za pomocą **szczegóły klasy** pasek narzędzi okna" jest nieprawidłowy dla tej akcji.

### <a name="create-a-member-using-class-designer"></a>Utworzyć składową za pomocą projektanta klas

1.  Kliknij prawym przyciskiem myszy typ, do którego chcesz dodać element członkowski, wskaż polecenie **Dodaj**, a następnie wybierz typ elementu członkowskiego, które chcesz dodać.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Otrzymuje nazwę domyślną, która może zmieniać w **projektanta klas**, **szczegóły klasy** oknie lub w **właściwości** okna.

2.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Tworzenie składnika za pomocą paska narzędzi okna Szczegóły klasy

1.  Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w **szczegóły klasy** okna.

2.  W **szczegóły klasy** pasek narzędzi okna, kliknij górną ikonę i wybierz pozycję **New \<składowej >** z listy rozwijanej.

     Kursor przesuwa się do **nazwa** pola w wierszu dla rodzaju elementu członkowskiego, które chcesz dodać. Na przykład, jeśli kliknięto przycisk **nową właściwość**, kursor zostanie przeniesiony do nowego wiersza w **właściwości** części **szczegóły klasy** okna.

3.  Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, i naciśnij klawisz Enter (lub przenieś fokus w inny sposób, np. za pomocą klawisza Tab).

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Składowa istnieje teraz w kodzie i jest wyświetlany w **projektanta klas**, **szczegóły klasy** okna i okna właściwości.

4.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

### <a name="create-a-member-using-the-class-details-window"></a>Tworzenie składnika za pomocą okna Szczegóły klasy

1.  Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w **szczegóły klasy** okna.

2.  W **szczegóły klasy** okna, w sekcji zawierającej rodzaj elementu członkowskiego, które chcesz dodać, kliknij przycisk  **\<Dodawanie elementu członkowskiego >**. Na przykład jeśli chcesz dodać pole, kliknij pozycję  **\<Dodaj pole >**.

3.  Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, a następnie naciśnij klawisz Enter.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Składowa istnieje teraz w kodzie i jest wyświetlany w **projektanta klas**, **szczegóły klasy** okna i okna właściwości.

4.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

     **Uwaga:** Skróty klawiaturowe można również użyć do tworzenia elementów członkowskich. Aby uzyskać więcej informacji, zobacz [skróty myszy i klawiaturowe w diagramie klas i szczegóły klasy okna](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Modyfikowanie składowych typu

Projektant klas umożliwia modyfikowanie składowych typów, które są wyświetlane na diagramie. Można modyfikować składowe dowolnego typu wyświetlane na diagramie klasy, które nie są tylko do odczytu. Składowe typu modyfikuje się za pomocą edycji w miejscu na powierzchni projektowej, w oknie właściwości i **szczegóły klasy** okna.

Wszystkie składowe wyświetlane w **szczegóły klasy** okna reprezentują składowe typów na diagramie klas. Istnieją cztery rodzaje elementów członkowskich: metody, właściwości, pola i zdarzenia.

Wszystkie wiersze elementów członkowskich pojawiają się pod nagłówkami, które grupują elementy członkowskie według rodzaju. Na przykład, wszystkie właściwości są wyświetlane pod nagłówkiem **właściwości**, który, jako węzeł w siatce, zwijania i rozwijania.

Każdy wiersz elementu członkowskiego zawiera następujące elementy:

- **Ikona elementu członkowskiego**

     Każdy rodzaj elementu członkowskiego jest reprezentowany przez własną ikonę. Wskaż myszą ikonę elementu członkowskiego, aby wyświetlić podpisu elementu członkowskiego. Kliknij ikonę elementu członkowskiego lub przestrzeń z lewej strony ikony elementu członkowskiego, aby zaznaczyć wiersz.

- **Nazwa elementu członkowskiego**

     **Nazwa** kolumny w wierszu elementu członkowskiego Wyświetla nazwę elementu członkowskiego. Ta nazwa jest wyświetlany na **nazwa** właściwości w oknie dialogowym właściwości. Ta komórka służy do zmiany nazwy któregokolwiek elementu członkowskiego, który ma uprawnienia odczytu i zapisu.

     Jeśli **nazwa** kolumna jest zbyt wąska, aby wyświetlić całą nazwę, wskazanie myszą na nazwę elementu członkowskiego powoduje wyświetlenie całej nazwy.

- **Typ elementu członkowskiego**

     **MemberType** komórki korzysta z technologii IntelliSense, która pozwala na wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub w projektach odwołania.

- **Modyfikator składowej**

     Zmień widoczność modyfikator elementu członkowskiego albo `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), lub `Default`.

- **\<Dodaj element członkowski >**

     Ostatni wiersz w **szczegóły klasy** okno zawiera tekst  **\<Dodawanie elementu członkowskiego >** w **nazwa** komórki. Po kliknięciu tej komórki, można utworzyć nowy element członkowski. Aby uzyskać więcej informacji, zobacz [Utwórz członków](creating-and-configuring-type-members.md#create-members).

- **Właściwości elementu członkowskiego w oknie dialogowym właściwości**

     **Szczegóły klasy** podzbiór właściwości składowych, które są wyświetlane w oknie dialogowym właściwości jest wyświetlana w oknie. Zmiana właściwości w jednej lokalizacji zaktualizuje globalnie wartość właściwości. Obejmuje to wyświetlanie jej wartości w innej lokalizacji.

- **Podsumowanie**

     **Podsumowania** komórki uwidacznia podsumowanie informacji na temat elementu członkowskiego. Kliknij przycisk wielokropka w **Podsumowanie** komórki, aby wyświetlić lub edytować informacje o **Podsumowanie**, **typie zwracanym**, i **uwagi** dla elementu członkowskiego .

- **Ukryj**

     Gdy **Ukryj** pole wyboru jest zaznaczone, element członkowski nie jest wyświetlany w typie.

### <a name="to-modify-a-type-member"></a>Aby zmodyfikować element członkowski typu

1.  Za pomocą Projektanta klas, wybierz typ.

2.  Jeśli **szczegóły klasy** nie zostanie wyświetlone okno, kliknij przycisk **szczegóły klasy** okna przycisk na pasku narzędzi projektanta klas.

3.  Edytuj wartości w polach **szczegóły klasy** siatki okna. Po każdej modyfikacji naciśnij klawisz ENTER lub w inny sposób przenieś fokus kursora z edytowanego pola, na przykład, naciskając klawisz TAB. Zmiany odzwierciedlają się bezpośrednio w kodzie.

    > [!NOTE]
    > Jeśli chcesz zmodyfikować jedynie nazwę elementu członkowskiego, możesz to zrobić za pomocą edycji w miejscu.

## <a name="add-parameters-to-methods"></a>Dodaj parametry do metod

Dodawanie parametrów do metod przy użyciu **szczegóły klasy** okna. Parametry mogą być skonfigurowane jako wymagane lub opcjonalne. Podanie wartości dla **opcjonalny domyślny** właściwości parametru powoduje, że projektant generuje kod jako parametr opcjonalny.

Wiersze parametrów zawierają następujące elementy:

- **Nazwa**

     **Nazwa** kolumna w wierszu parametru wyświetla nazwę parametru. Ta nazwa jest wyświetlany na **nazwa** właściwości w oknie dialogowym właściwości. Ta komórka służy do zmiany nazwy któregokolwiek parametru, który ma uprawnienia odczytu i zapisu.

     Wskazuje na nazwę parametru wyświetla nazwę parametru, jeśli **nazwa** kolumna jest zbyt wąska, aby wyświetlić całą nazwę.

- **Typ**

     **Typ parametru** komórki korzysta z technologii IntelliSense, która pozwala na wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub w projektach odwołania.

- **Modyfikator**

     **Modyfikator** komórki w wierszu parametru akceptuje i wyświetla nowy modyfikator parametru. Aby wprowadzić nowy modyfikator parametru, użyj pola listy rozwijanej, aby dokonać wyboru spośród **Brak**, **ref**, **się**, lub **params** w języku C# i **ByVal**, **ByRef**, lub **ParamArray** w VB.

- **Podsumowanie**

     **Podsumowanie** komórki w wierszu parametru umożliwia wprowadzanie komentarzy do kodu, które są wyświetlane w IntelliSense podczas wprowadzania parametru w edytorze kodu.

- **\<Dodaj parametr >**

     Ostatni wiersz parametru elementu członkowskiego zawiera tekst **<add parameter>** w **nazwa** komórki. Kliknięcie tej komórki pozwala utworzyć nowy parametr. Aby uzyskać więcej informacji, zobacz [Aby dodać parametr do metody](creating-and-configuring-type-members.md#add-parameters-to-methods).

**Właściwości** okno wyświetla te same właściwości parametru wyświetlane w **szczegóły klasy** okna: **Nazwa**, **typu**, **modyfikator**, **Podsumowanie**, jak również **opcjonalny domyślny** właściwości. Zmiana właściwości w jednej lokalizacji aktualizuje globalnie wartość właściwości, włącznie z wyświetlaniem jej wartości w innej lokalizacji.

> [!NOTE]
> Aby dodać parametr do delegata, zobacz [Utwórz członków](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Chociaż destruktor jest metodą, to nie może mieć parametrów.

### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody

1.  Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać parametr.

     Typ uzyskuje fokus i jego zawartość wyświetla się w **szczegóły klasy** okna.

2.  W **szczegóły klasy** okna, Rozszerz wiersz metody, do której chcesz dodać parametr.

     Pojawi się wiersz parametru z wcięciem, zawierający tylko parę nawiasów i wyrazy  **\<Dodaj parametr >.**

3.  Kliknij przycisk  **\<Dodaj parametr >**, wpisz nazwę nowego parametru, a następnie naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kodu metody. Wyświetla w **szczegóły klasy** okna i okna właściwości.

4.  Opcjonalnie określ inne szczegóły dotyczące parametru, takie jak jego typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Aby dodać opcjonalny parametr do metody

1.  Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać opcjonalny parametr.

     Typ uzyskuje fokus i jego zawartość wyświetla się w **szczegóły klasy** okna.

2.  W **szczegóły klasy** okna, Rozszerz wiersz metody, do której chcesz dodać opcjonalny parametr.

     Pojawi się wiersz parametru z wcięciem, zawierający tylko parę nawiasów i wyrazy  **\<Dodaj parametr >.**

3.  Kliknij przycisk  **\<Dodaj parametr >**, wpisz nazwę nowego parametru, a następnie naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kodu metody. Wyświetla w **szczegóły klasy** okna i okna właściwości.

4.  W oknie właściwości wpisz wartość dla **opcjonalny domyślny** właściwości. Ustawienie właściwości Opcjonalny domyślny parametru powoduje, że ten parametr staje się opcjonalny.

    > [!NOTE]
    > Opcjonalne parametry muszą być ostatnimi parametrami na liście parametrów.

## <a name="class-details-usage-notes"></a>Uwagi dotyczące użycia okna Szczegóły klasy

Należy pamiętać, poniższe porady dotyczące korzystania z **szczegóły klasy** okna.

### <a name="editable-and-non-editable-cells"></a>Komórki edytowalne i nieedytowalne

Wszystkie komórki w **szczegóły klasy** są edytowalne, z pewnymi wyjątkami:

- Cały typ jest tylko do odczytu, gdy, na przykład znajduje się w zestawie odwołania. Po zaznaczeniu kształtu w konstruktorze klasy **szczegóły klasy** okna wyświetla jego szczegóły w stanie tylko do odczytu.

- Dla indeksatorów nazwa jest tylko do odczytu, a pozostałe (typ, modyfikator, podsumowanie) są edytowalne.

- Wszystkie elementy rodzajowe mają parametry tylko do odczytu **szczegóły klasy** okna. Aby zmienić parametr rodzajowy, wyedytuj jego kod źródłowy.

- Nazwa parametru typu, który jest zdefiniowany w typie rodzajowym, jest tylko do odczytu.

- Gdy kod typu jest uszkodzony (Błędny), **szczegóły klasy** okna zawartość typu jest wyświetlana jako tylko do odczytu.

### <a name="the-class-details-window-and-source-code"></a>Szczegóły klasy okna i kod źródłowy

- Możesz wyświetlić kod źródłowy, klikając prawym przyciskiem myszy kształt w **szczegóły klasy** okna (lub Projektant klas), a następnie klikając przycisk Wyświetl kod. Plik źródłowy kodu otwiera się i przewija do wybranego elementu.

- Zmiana kodu źródłowego jest natychmiast odzwierciedlana w wyświetlaniu sygnatury w Projektancie klas i **szczegóły klasy** okna. Jeśli **szczegóły klasy** okno zostanie zamknięte w czasie, nowe informacje są widoczne przy następnym otwarciu.

- Gdy kod typu jest uszkodzony (Błędny), **szczegóły klasy** okna zawartość typu jest wyświetlana jako tylko do odczytu.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funkcja Schowka w oknie Szczegóły klasy

Można skopiować lub wyciąć pola lub wiersze z **szczegóły klasy** okna i wklej je do innego typu. Wiersz można wyciąć tylko wtedy, gdy nie jest tylko do odczytu. Podczas wklejania wiersza, **szczegóły klasy** okna przypisuje nową nazwę (pochodzącą z nazwy skopiowanego wiersza), aby uniknąć konfliktu.

## <a name="display-of-read-only-information"></a>Wyświetlanie informacji tylko do odczytu

Projektant klasy i **szczegóły klasy** można wyświetlić w oknie dla następujących typów (i składowe typów):

- projekt, który zawiera diagram klas

- projekt stanowiący odwołanie z projektu, który zawiera diagram klas

- zestaw stanowiący odwołanie z projektu, który zawiera diagram klas

W dwóch ostatnich przypadkach, jednostka, do której istnieje odwołanie (typ lub składowa), jest tylko do odczytu na diagramie klasy, który ją reprezentuje.

Cały projekt lub jego części, takie jak pojedyncze pliki, mogą być tylko do odczytu. Najbardziej typowe przypadki, w których projekt lub jeden z jego plików jest tylko do odczytu, występują wtedy, gdy projekt jest pod kontrolą kodu źródłowego (i nie jest wyewidencjonowany), istnieje w zestawie zewnętrznym, lub gdy system operacyjny uzna, że pliki są tylko do odczytu.

**Kontrola kodu źródłowego**

Ponieważ diagram klas jest zapisywany jako plik w projekcie, należy wyewidencjonować projekt, aby zapisać zmiany wprowadzone w Projektancie klas lub **szczegóły klasy** okna.

**Projekty tylko do odczytu**

Projekt może być tylko do odczytu z przyczyn innych niż kontrola kodu źródłowego. Zamknięcie projektu wyświetla okno dialogowe z pytaniem, czy zastąpić plik projektu, odrzucić zmiany (nie zapisywać) lub anulować operację zamknięcia. Jeśli wybierzesz zastąpienie, pliki projektu są zastępowane i udostępnione do odczytu i zapisu. Dodawany jest nowy plik diagramu klasy.

**Typy tylko do odczytu**

Jeśli zostanie podjęta próba zapisania projektu zawierającego typ, którego plik kodu źródłowego jest tylko do odczytu, **Zapisz z uprawnieniami tylko do odczytu pliku** pojawi się okno dialogowe, które daje wybór, aby zapisać plik pod nową nazwą lub w nowej lokalizacji lub zastąpienia pliku tylko do odczytu . Jeśli plik zostanie zastąpiony, nowa kopia nie będzie już tylko do odczytu.

Jeśli plik kodu zawiera błąd składni, kształty wyświetlające kod w tym pliku zostaną tymczasowo ustawione tylko do odczytu, dopóki błąd składni nie zostanie poprawiony. Kształty w tym stanie wyświetlają czerwony tekst i czerwoną ikonę, która wyświetla etykietkę z napisem „plik kodu źródłowego zawiera błąd analizy składni”.

Odwołanie typu (np. typ .NET Framework), które występuje w obszarze innego węzła projektu lub węzła odwołania do zestawu, jest wskazany na powierzchni projektowej Projektanta klas jako tylko do odczytu. Typ lokalny, który istnieje w otwartym projekcie, jest do odczytu i zapisu, a jego kształt na powierzchni projektowej Projektanta klas jest odpowiednio opisany.

Indeksatory są odczytu i zapisu w kodzie i **szczegóły klasy** okna, ale nazwa indeksatora jest tylko do odczytu.

Metod częściowych nie można edytować za pomocą projektanta klas lub **szczegóły klasy** okna; do ich edycji należy użyć edytora kodu.

Macierzystego kodu C++ nie można edytować za pomocą projektanta klas lub **szczegóły klasy** okna; należy użyć edytora kodu, aby edytować macierzystego kodu C++.

## <a name="see-also"></a>Zobacz także

- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)