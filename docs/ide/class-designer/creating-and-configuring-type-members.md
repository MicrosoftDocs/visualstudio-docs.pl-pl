---
title: Tworzenie i konfigurowanie typów członków (Projektant klas)
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfed51812b034d63f250a56548b88f09a98214fe
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590413"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Utwórz i skonfiguruj elementy członkowskie typu w Projektant klas

Można dodać tych członków do typów na diagramie klasy i skonfigurować te elementy członkowskie w oknie **Szczegóły klasy** :

|**Typ**|**Elementy członkowskie, które mogą zawierać**|
|--------------| - |
|Klasa|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Wyliczenie|element członkowski|
|Interfejs|metoda, właściwość, zdarzenie (w języku C# i Visual Basic)|
|Klasa abstrakcyjna|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Struktura (konstrukcja Struct w języku C#)|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), stała|
|Delegate|parametr|
|Moduł (tylko w języku VB)|metoda, właściwość, pole, zdarzenie, konstruktor, stała|

> [!NOTE]
> Utwórz bardziej zwartą deklarację właściwości, gdy akcesory właściwości get i set nie potrzebują dodatkowej logiki, za pomocą automatycznie wdrożonych właściwości (tylko C#). Aby wyświetlić pełną sygnaturę, w menu **Diagram klas** wybierz **Zmień Format elementów członkowskich** > **wyświetlić pełny podpis**. Aby uzyskać więcej informacji na temat właściwości, które są implementowane, zobacz [zaimplementowane właściwości](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pomocnicza|
|----------| - |
|**Rozpocznij:** Przed utworzeniem i skonfigurowaniem elementów członkowskich typu należy otworzyć okno **Szczegóły klasy** .|- [otworzyć okno Szczegóły klasy](creating-and-configuring-type-members.md#open-the-class-details-window)<br />[Informacje o użyciu dotyczące klasy](creating-and-configuring-type-members.md#class-details-usage-notes) - <br />- [wyświetlania informacji tylko do odczytu](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [skróty klawiaturowe i myszy w diagramie klas i oknie Szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Tworzenie i modyfikowanie elementów członkowskich typu:** Można tworzyć nowych członków, modyfikować członków i dodawać parametry do metody przy użyciu okna **Szczegóły klasy** .|- [utworzyć członków](creating-and-configuring-type-members.md#create-members)<br />- [Modyfikuj składowe typu](creating-and-configuring-type-members.md#modify-type-members)<br />- [dodawać parametrów do metod](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otwórz okno Szczegóły klasy

Domyślnie okno **Szczegóły klasy** pojawia się automatycznie po otwarciu nowego diagramu klas. Zobacz [jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md)). Możesz również otworzyć okno **Szczegóły klasy** w następujący sposób:

- Kliknij prawym przyciskiem myszy dowolną klasę na diagramie, aby wyświetlić menu kontekstowe, a następnie wybierz pozycję **Szczegóły klasy**.

- Wybierz pozycję **wyświetl** > inne **Szczegóły klasy** > **systemu Windows** z paska menu.

## <a name="create-members"></a>Utwórz członków

Można utworzyć element członkowski, używając dowolnego z następujących narzędzi:

- **Projektant klas**

- Pasek narzędzi okna **Szczegóły klasy**

- Okno **Szczegóły klasy**

> [!NOTE]
> Można również utworzyć konstruktory i destruktory przy użyciu procedur opisanych w tej sekcji. Należy pamiętać, że konstruktory i destruktory są specjalnymi rodzajami metod i w ten sposób pojawiają się w przedziale **metod** w kształtach diagramu klas i w sekcji **metody** siatki okna **Szczegóły klasy** .

> [!NOTE]
> Jedyna jednostka, jaką można dodać do obiektu delegowanego, to parametr. Należy zauważyć, że procedura zatytułowana "aby utworzyć członka przy użyciu paska narzędzi okna **Szczegóły klasy** " jest nieprawidłowa dla tej akcji.

### <a name="create-a-member-using-class-designer"></a>Tworzenie składowej przy użyciu Projektant klas

1. Kliknij prawym przyciskiem myszy typ, do którego chcesz dodać element członkowski, wskaż polecenie **Dodaj**, a następnie wybierz typ elementu członkowskiego, który chcesz dodać.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Otrzymuje nazwę domyślną, którą można zmienić w **Projektant klas**, oknie **Szczegóły klasy** lub w oknie **Właściwości** .

2. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Tworzenie elementu członkowskiego przy użyciu paska narzędzi okna Szczegóły klasy

1. Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w oknie **Szczegóły klasy** .

2. Na pasku narzędzi okna **Szczegóły klasy** Kliknij górną ikonę i wybierz pozycję **nowy \<członek >** z listy rozwijanej.

     Kursor zostanie przeniesiony do pola **Nazwa** w wierszu dla rodzaju elementu członkowskiego, który chcesz dodać. Jeśli na przykład klikniesz pozycję **Nowa właściwość**, kursor przejdzie do nowego wiersza w sekcji **Właściwości** okna **Szczegóły klasy** .

3. Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, i naciśnij klawisz Enter (lub przenieś fokus w inny sposób, np. za pomocą klawisza Tab).

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski już istnieje w kodzie i jest wyświetlany w **Projektant klas**, w oknie **szczegóły klasy** i okno właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

### <a name="create-a-member-using-the-class-details-window"></a>Tworzenie elementu członkowskiego przy użyciu okna Szczegóły klasy

1. Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w oknie **Szczegóły klasy** .

2. W oknie **Szczegóły klasy** , w sekcji zawierającej rodzaj elementu członkowskiego, który chcesz dodać, kliknij przycisk **\<Dodaj > członka**. Na przykład, jeśli chcesz dodać pole, kliknij **\<dodać pole >** .

3. Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, a następnie naciśnij klawisz Enter.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski już istnieje w kodzie i jest wyświetlany w **Projektant klas**, w oknie **szczegóły klasy** i okno właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

    > [!NOTE]
    > Do tworzenia elementów członkowskich można także używać skrótów klawiaturowych. Aby uzyskać więcej informacji, zobacz [skróty klawiaturowe i myszy w diagramie klas i oknie Szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Modyfikuj elementy członkowskie typu

Projektant klas umożliwia modyfikowanie składowych typów, które są wyświetlane na diagramie. Można modyfikować składowe dowolnego typu wyświetlane na diagramie klasy, które nie są tylko do odczytu. Elementy członkowskie typu są modyfikowane za pomocą edycji w miejscu na powierzchni projektowej, okno Właściwości i w oknie **Szczegóły klasy** .

Wszystkie elementy członkowskie wyświetlane w oknie **Szczegóły klasy** reprezentują elementy członkowskie typów na diagramie klas. Istnieją cztery rodzaje elementów członkowskich: metody, właściwości, pola i zdarzenia.

Wszystkie wiersze elementów członkowskich pojawiają się pod nagłówkami, które grupują elementy członkowskie według rodzaju. Na przykład wszystkie właściwości są wyświetlane pod **właściwościami**nagłówka, które jako węzeł w siatce mogą być zwinięte lub rozwinięte.

Każdy wiersz elementu członkowskiego zawiera następujące elementy:

- **Ikona elementu członkowskiego**

     Każdy rodzaj elementu członkowskiego jest reprezentowany przez własną ikonę. Wskaż myszą ikonę elementu członkowskiego, aby wyświetlić podpis elementu członkowskiego. Kliknij ikonę elementu członkowskiego lub przestrzeń z lewej strony ikony elementu członkowskiego, aby zaznaczyć wiersz.

- **Nazwa elementu członkowskiego**

     Kolumna **Nazwa** w wierszu elementu członkowskiego zawiera nazwę elementu członkowskiego. Ta nazwa jest również wyświetlana w właściwości **Nazwa** w okno właściwości. Ta komórka służy do zmiany nazwy któregokolwiek elementu członkowskiego, który ma uprawnienia odczytu i zapisu.

     Jeśli kolumna **Nazwa** jest zbyt wąska, aby wyświetlić całą nazwę, wskaż myszą nazwy elementu członkowskiego, która zawiera całą nazwę.

- **Typ elementu członkowskiego**

     Komórka **MemberType** korzysta z technologii IntelliSense, która umożliwia wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub projektach, do których istnieją odwołania.

- **Modyfikator elementu członkowskiego**

     Zmień modyfikator widoczności elementu członkowskiego na `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected Friend` (`protected internal`) lub `Default`.

- **\<dodać członka >**

     Ostatni wiersz w oknie **Szczegóły klasy** zawiera tekst **\<Dodaj członka >** w komórce **Nazwa** . Po kliknięciu tej komórki, można utworzyć nowy element członkowski. Aby uzyskać więcej informacji, zobacz [Tworzenie elementów członkowskich](creating-and-configuring-type-members.md#create-members).

- **Właściwości elementu członkowskiego w okno Właściwości**

     W oknie **Szczegóły klasy** zostanie wyświetlony podzestaw właściwości elementów członkowskich, które są wyświetlane w okno właściwości. Zmiana właściwości w jednej lokalizacji zaktualizuje globalnie wartość właściwości. Obejmuje to wyświetlanie jej wartości w innej lokalizacji.

- **Podsumowanie**

     Komórka **Podsumowanie** uwidacznia podsumowanie informacji o elemencie członkowskim. Kliknij wielokropek w komórce **Podsumowanie** , aby wyświetlić lub edytować informacje o **podsumowaniu**, **zwracanym typie**i **uwagach** dla elementu członkowskiego.

- **Usuń**

     Gdy pole wyboru **Ukryj** jest zaznaczone, element członkowski nie jest wyświetlany w typie.

### <a name="to-modify-a-type-member"></a>Aby zmodyfikować element członkowski typu

1. Za pomocą Projektanta klas, wybierz typ.

2. Jeśli okno **Szczegóły klasy** nie zostanie wyświetlone, kliknij przycisk okno **Szczegóły klasy** na pasku narzędzi Projektant klas.

3. Edytuj wartości w polach siatki okna **Szczegóły klasy** . Po każdej modyfikacji naciśnij klawisz ENTER lub w inny sposób przenieś fokus kursora z edytowanego pola, na przykład, naciskając klawisz TAB. Zmiany odzwierciedlają się bezpośrednio w kodzie.

    > [!NOTE]
    > Jeśli chcesz zmodyfikować jedynie nazwę elementu członkowskiego, możesz to zrobić za pomocą edycji w miejscu.

## <a name="add-parameters-to-methods"></a>Dodawanie parametrów do metod

Dodaj parametry do metod przy użyciu okna **Szczegóły klasy** . Parametry mogą być skonfigurowane jako wymagane lub opcjonalne. Podanie wartości **opcjonalnej właściwości domyślnej** parametru powoduje, że Projektant generuje kod jako opcjonalny parametr.

Wiersze parametrów zawierają następujące elementy:

- **Nazwa**

     W kolumnie **Nazwa** w wierszu parametru wyświetlana jest nazwa parametru. Ta nazwa jest również wyświetlana w właściwości **Nazwa** w okno właściwości. Ta komórka służy do zmiany nazwy któregokolwiek parametru, który ma uprawnienia odczytu i zapisu.

     Wskazanie nazwy parametru wyświetla nazwę parametru, jeśli kolumna **Nazwa** jest zbyt wąska, aby wyświetlić całą nazwę.

- **Typ**

     Komórka **typu parametru** korzysta z technologii IntelliSense, która umożliwia wybór z listy wszystkich typów dostępnych w bieżącym projekcie lub projektach, do których istnieją odwołania.

- **Modyfikator**

     Komórka **modyfikująca** w wierszu parametru akceptuje i wyświetla nowy modyfikator parametru. Aby wprowadzić nowy modyfikator parametrów, użyj pola listy rozwijanej, aby wybrać opcję z **Brak**, **ref**, **out**lub **params** w C#, i **ByVal**, **ByRef**lub **ParamArray** w języku VB.

- **Podsumowanie**

     Komórka **podsumowania** w wierszu parametru umożliwia wprowadzanie komentarzy do kodu, które pojawiają się w IntelliSense podczas wprowadzania parametru do edytora kodu.

- **\<Dodaj parametr >**

     Ostatni wiersz parametru elementu członkowskiego zawiera tekst **< Dodaj parametr\>** w komórce **Nazwa** . Kliknięcie tej komórki pozwala utworzyć nowy parametr. Aby uzyskać więcej informacji, zobacz [Aby dodać parametr do metody](creating-and-configuring-type-members.md#add-parameters-to-methods).

W oknie **Właściwości** są wyświetlane te same właściwości parametrów, które są wyświetlane w oknie **Szczegóły klasy** : **Nazwa**, **Typ**, **modyfikator**, **Podsumowanie**, a także **Opcjonalna Właściwość domyślna** . Zmiana właściwości w jednej lokalizacji aktualizuje globalnie wartość właściwości, włącznie z wyświetlaniem jej wartości w innej lokalizacji.

> [!NOTE]
> Aby dodać parametr do delegata, zobacz [Tworzenie członków](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Chociaż destruktor jest metodą, to nie może mieć parametrów.

### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody

1. Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać parametr.

     Typ uzyskuje fokus i jego zawartość wyświetla się w oknie **Szczegóły klasy** .

2. W oknie **Szczegóły klasy** Rozwiń wiersz metody, do której chcesz dodać parametr.

     Zostanie wyświetlony wiersz z wcięciem z wcięciami zawierający tylko parę nawiasów i słowa **\<Dodaj parametr >.**

3. Kliknij przycisk **\<dodać parametr >** , wpisz nazwę nowego parametru i naciśnij klawisz **Enter**.

     Nowy parametr zostanie dodany do metody i kodu metody. Jest on wyświetlany w oknie **Szczegóły klasy** i okno właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące parametru, takie jak jego typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Aby dodać opcjonalny parametr do metody

1. Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać opcjonalny parametr.

     Typ uzyskuje fokus i jego zawartość wyświetla się w oknie **Szczegóły klasy** .

2. W oknie **Szczegóły klasy** Rozwiń wiersz metody, do której chcesz dodać opcjonalny parametr.

     Zostanie wyświetlony wiersz z wcięciem z wcięciami zawierający tylko parę nawiasów i słowa **\<Dodaj parametr >.**

3. Kliknij przycisk **\<dodać parametr >** , wpisz nazwę nowego parametru i naciśnij klawisz **Enter**.

     Nowy parametr zostanie dodany do metody i kodu metody. Jest on wyświetlany w oknie **Szczegóły klasy** i okno właściwości.

4. W okno Właściwości wpisz wartość **opcjonalnej właściwości domyślnej** . Ustawienie właściwości Opcjonalny domyślny parametru powoduje, że ten parametr staje się opcjonalny.

    > [!NOTE]
    > Opcjonalne parametry muszą być ostatnimi parametrami na liście parametrów.

## <a name="class-details-usage-notes"></a>Uwagi dotyczące użycia szczegółów klasy

Zapoznaj się z poniższymi wskazówkami dotyczącymi korzystania z okna **Szczegóły klasy** .

### <a name="editable-and-non-editable-cells"></a>Komórki edytowalne i nieedytowalne

Wszystkie komórki w oknie **Szczegóły klasy** można edytować z kilkoma wyjątkami:

- Cały typ jest tylko do odczytu, gdy na przykład znajduje się w przywoływanym zestawie. Po wybraniu kształtu w Projektant klas okno **Szczegóły klasy** wyświetla jego szczegóły w stanie tylko do odczytu.

- Dla indeksatorów nazwa jest tylko do odczytu, a pozostałe (typ, modyfikator, podsumowanie) są edytowalne.

- Wszystkie typy ogólne mają parametry tylko do odczytu w oknie **Szczegóły klasy** . Aby zmienić parametr rodzajowy, wyedytuj jego kod źródłowy.

- Nazwa parametru typu, który jest zdefiniowany w typie rodzajowym, jest tylko do odczytu.

- Gdy kod typu jest przerwany (niemożliwy do przeanalizowania), w oknie **Szczegóły klasy** jest wyświetlana zawartość tego typu jako tylko do odczytu.

### <a name="the-class-details-window-and-source-code"></a>Okno Szczegóły klasy i kod źródłowy

- Aby wyświetlić kod źródłowy, kliknij prawym przyciskiem myszy kształt w oknie **Szczegóły klasy** (lub Projektant klas), a następnie kliknij polecenie Wyświetl kod. Plik źródłowy kodu otwiera się i przewija do wybranego elementu.

- Zmiany kodu źródłowego są natychmiast odzwierciedlane w wyświetlaniu informacji o sygnaturach w Projektant klas i oknie **Szczegóły klasy** . Jeśli okno **Szczegóły klasy** jest w tym momencie zamknięte, nowe informacje są widoczne przy następnym otwarciu.

- Gdy kod typu jest przerwany (niemożliwy do przeanalizowania), w oknie **Szczegóły klasy** jest wyświetlana zawartość tego typu jako tylko do odczytu.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funkcje Schowka w oknie Szczegóły klasy

Możesz skopiować lub wyciąć pola lub wiersze z okna **Szczegóły klasy** i wkleić je do innego typu. Wiersz można wyciąć tylko wtedy, gdy nie jest tylko do odczytu. Po wklejeniu wiersza okno **Szczegóły klasy** przypisuje nową nazwę (pochodną od nazwy kopiowanego wiersza), aby uniknąć konfliktu.

## <a name="display-of-read-only-information"></a>Wyświetlanie informacji tylko do odczytu

Projektant klas, a w oknie **Szczegóły klasy** można wyświetlić typy (i składowe typów) dla następujących elementów:

- projekt, który zawiera diagram klas

- projekt stanowiący odwołanie z projektu, który zawiera diagram klas

- zestaw stanowiący odwołanie z projektu, który zawiera diagram klas

W dwóch ostatnich przypadkach, jednostka, do której istnieje odwołanie (typ lub składowa), jest tylko do odczytu na diagramie klasy, który ją reprezentuje.

Cały projekt lub jego części, takie jak pojedyncze pliki, mogą być tylko do odczytu. Najbardziej typowe przypadki, w których projekt lub jeden z jego plików jest tylko do odczytu, występują wtedy, gdy projekt jest pod kontrolą kodu źródłowego (i nie jest wyewidencjonowany), istnieje w zestawie zewnętrznym, lub gdy system operacyjny uzna, że pliki są tylko do odczytu.

**Kontrola kodu źródłowego**

Ponieważ Diagram klas jest zapisywany jako plik w projekcie, należy wyewidencjonować projekt w celu zapisania wszelkich zmian wprowadzonych w Projektant klas lub w oknie **Szczegóły klasy** .

**Projekty tylko do odczytu**

Projekt może być tylko do odczytu z przyczyn innych niż kontrola kodu źródłowego. Zamknięcie projektu wyświetla okno dialogowe z pytaniem, czy zastąpić plik projektu, odrzucić zmiany (nie zapisuj), czy anulować operację zamknięcia. Jeśli wybierzesz zastąpienie, pliki projektu są zastępowane i udostępnione do odczytu i zapisu. Dodawany jest nowy plik diagramu klasy.

**Typy tylko do odczytu**

W przypadku próby zapisania projektu zawierającego typ, którego plik kodu źródłowego jest tylko do odczytu, zostanie wyświetlone okno dialogowe **Zapisywanie pliku tylko do odczytu** , które umożliwia zapisanie pliku pod nową nazwą lub nową lokalizację lub zastąpienie pliku tylko do odczytu. Jeśli plik zostanie zastąpiony, nowa kopia nie będzie już tylko do odczytu.

Jeśli plik kodu zawiera błąd składni, kształty wyświetlające kod w tym pliku zostaną tymczasowo ustawione tylko do odczytu, dopóki błąd składni nie zostanie poprawiony. Kształty w tym stanie wyświetlają czerwony tekst i czerwoną ikonę, która wyświetla etykietkę z napisem „plik kodu źródłowego zawiera błąd analizy składni”.

Typ przywoływany (na przykład typ .NET), który istnieje w innym węźle projektu lub w węźle zestawu, do którego się odwołuje, jest wskazany na powierzchni projektowej Projektant klas jako tylko do odczytu. Typ lokalny, który istnieje w otwartym projekcie, jest do odczytu i zapisu, a jego kształt na powierzchni projektowej Projektanta klas jest odpowiednio opisany.

Indeksatory są do odczytu i zapisu w kodzie oraz w oknie **Szczegóły klasy** , ale nazwa indeksatora jest tylko do odczytu.

Nie można edytować metod częściowych przy użyciu Projektant klas lub okna **Szczegóły klasy** ; Aby je edytować, należy użyć edytora kodu.

Nie można edytować kodu C++ natywnego za pomocą Projektant klas lub okna **Szczegóły klasy** ; Aby edytować kod natywny C++ , należy użyć edytora kodu.

## <a name="see-also"></a>Zobacz także

- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
- [Refaktoryzacja klas i typów](refactoring-classes-and-types.md)
