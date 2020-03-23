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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590413"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Tworzenie i konfigurowanie elementów członkowskich typu w Projektancie klas

Można dodać te elementy członkowskie do typów na diagramie klasy i skonfigurować te elementy członkowskie w oknie **Szczegóły klasy:**

|**Typ**|**Członkowie mogą ona zawierać**|
|--------------| - |
|Klasa|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Wyliczenie|członek|
|Interface|metoda, właściwość, zdarzenie (w języku C# i Visual Basic)|
|Klasa abstrakcyjna|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Struktura (konstrukcja Struct w języku C#)|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), stała|
|Delegate|parametr|
|Moduł (tylko w języku VB)|metoda, właściwość, pole, zdarzenie, konstruktor, stała|

> [!NOTE]
> Utwórz bardziej zwartą deklarację właściwości, gdy akcesory właściwości get i set nie potrzebują dodatkowej logiki, za pomocą automatycznie wdrożonych właściwości (tylko C#). Aby wyświetlić pełny podpis, z menu **Diagram klas** wybierz polecenie **Zmień format członkowek Wyświetl** > **pełny podpis**. Aby uzyskać więcej informacji na temat właściwości automatycznie zaimplementowanych, zobacz [Właściwości zaimplementowane automatycznie](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Obsługa zawartości|
|----------| - |
|**Zacznij:** Przed utworzeniem i skonfigurowaniem elementów członkowskich typu należy otworzyć okno **Szczegóły klasy.**|- [Otwórz okno Szczegóły klasy](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Uwagi dotyczące użycia szczegółów klasy](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Wyświetlanie informacji tylko do odczytu](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Skróty klawiaturowe i myszy w oknie Diagram klas i Szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Tworzenie i modyfikowanie elementów członkowskich typu:** Można tworzyć nowe elementy członkowskie, modyfikować elementy członkowskie i dodawać parametry do metody przy użyciu okna **Szczegóły klasy.**|- [Tworzenie członków](creating-and-configuring-type-members.md#create-members)<br />- [Modyfikowanie elementów członkowskich typu](creating-and-configuring-type-members.md#modify-type-members)<br />- [Dodawanie parametrów do metod](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Otwórz okno Szczegóły klasy

Domyślnie okno **Szczegóły klasy** pojawia się automatycznie po otwarciu nowego diagramu klas. Zobacz [Jak: Dodawanie diagramów klas do projektów](how-to-add-class-diagrams-to-projects.md)). Okno **Szczegóły klasy** można również otworzyć w następujący sposób:

- Kliknij prawym przyciskiem myszy dowolną klasę na diagramie, aby wyświetlić menu kontekstowe, a następnie wybierz polecenie **Szczegóły klasy**.

- Z paska menu **wybierz pozycję Wyświetl** > inne**szczegóły klasy** **systemu Windows.** > 

## <a name="create-members"></a>Tworzenie członków

Można utworzyć element członkowski, używając dowolnego z następujących narzędzi:

- **Projektant klas**

- Pasek narzędzi okna **Szczegóły klasy**

- Okno **Szczegóły klasy**

> [!NOTE]
> Można również utworzyć konstruktory i destruktory przy użyciu procedur opisanych w tej sekcji. Należy pamiętać, że konstruktory i destruktory są specjalne rodzaje metod i jako takie pojawiają się w **metody** przedziału w kształtach diagramu klasy i w **metody** sekcji **klasy szczegóły** siatki okna.

> [!NOTE]
> Jedyna jednostka, jaką można dodać do obiektu delegowanego, to parametr. Należy zauważyć, że procedura zatytułowana "Aby utworzyć element członkowski przy użyciu paska narzędzi okno **szczegóły klasy"** jest nieprawidłowa dla tej akcji.

### <a name="create-a-member-using-class-designer"></a>Tworzenie elementu członkowskiego przy użyciu Projektanta klas

1. Kliknij prawym przyciskiem myszy typ, do którego chcesz dodać element członkowski, wskaż polecenie **Dodaj**, a następnie wybierz typ elementu członkowskiego, który chcesz dodać.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Otrzymuje domyślną nazwę, którą można zmienić w **Projektancie klas,** oknie **Szczegóły klasy** lub w oknie **Właściwości.**

2. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Tworzenie elementu członkowskiego przy użyciu paska narzędzi okno Szczegóły klasy

1. Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus, a jego zawartość są wyświetlane w oknie **Szczegóły klasy.**

2. Na pasku narzędzi okna **Szczegóły klasy** kliknij górną ikonę i wybierz pozycję **Nowy \<element członkowski>** z listy rozwijanej.

     Kursor zostanie przeniesiony do pola **Nazwa** w wierszu dla rodzaju elementu członkowskiego, który chcesz dodać. Na przykład po kliknięciu **przycisku Nowa właściwość**kursor zostanie przeniesiony do nowego wiersza w sekcji **Właściwości** okna **Szczegóły klasy.**

3. Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, i naciśnij klawisz Enter (lub przenieś fokus w inny sposób, np. za pomocą klawisza Tab).

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski istnieje teraz w kodzie i jest wyświetlany w **Projektancie klas,** oknie **Szczegóły klasy** i oknie Właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

### <a name="create-a-member-using-the-class-details-window"></a>Tworzenie elementu członkowskiego przy użyciu okna Szczegóły klasy

1. Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus, a jego zawartość są wyświetlane w oknie **Szczegóły klasy.**

2. W oknie **Szczegóły klasy** w sekcji zawierającej rodzaj elementu członkowskiego, który chcesz dodać, kliknij pozycję ** \<Dodaj element członkowski>**. Na przykład, jeśli chcesz dodać pole, kliknij ** \<dodaj pole>**.

3. Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, a następnie naciśnij klawisz Enter.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski istnieje teraz w kodzie i jest wyświetlany w **Projektancie klas**, oknie **Szczegóły klasy** i oknie Właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

    > [!NOTE]
    > Do tworzenia elementów członkowskich można również używać skrótów klawiaturowych. Aby uzyskać więcej informacji, zobacz [Skróty klawiaturowe i myszy w oknie Diagram klas i Szczegóły klasy](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Modyfikowanie elementów członkowskich typu

Projektant klas umożliwia modyfikowanie składowych typów, które są wyświetlane na diagramie. Można modyfikować składowe dowolnego typu wyświetlane na diagramie klasy, które nie są tylko do odczytu. Elementy członkowskie typu można modyfikować za pomocą edycji w miejscu na powierzchni projektowej, oknie Właściwości i oknie **Szczegóły klasy.**

Wszystkie elementy członkowskie wyświetlane w oknie **Szczegóły klasy** reprezentują elementy członkowskie typów na diagramie klas. Istnieją cztery rodzaje elementów członkowskich: metody, właściwości, pola i zdarzenia.

Wszystkie wiersze elementów członkowskich pojawiają się pod nagłówkami, które grupują elementy członkowskie według rodzaju. Na przykład wszystkie właściwości są wyświetlane pod nagłówkiem **Właściwości**, które jako węzeł w siatce mogą być zwinięte lub rozwinięte.

Każdy wiersz elementu członkowskiego zawiera następujące elementy:

- **Ikona członka**

     Każdy rodzaj elementu członkowskiego jest reprezentowany przez własną ikonę. Skieruj mysz na ikonę elementu członkowskiego, aby wyświetlić podpis członka. Kliknij ikonę elementu członkowskiego lub przestrzeń z lewej strony ikony elementu członkowskiego, aby zaznaczyć wiersz.

- **Nazwa elementu członkowskiego**

     Kolumna **Nazwa** w wierszu elementu członkowskiego wyświetla nazwę członka. Ta nazwa jest również wyświetlana we właściwości **Name** w oknie Właściwości. Ta komórka służy do zmiany nazwy któregokolwiek elementu członkowskiego, który ma uprawnienia odczytu i zapisu.

     Jeśli **kolumna Nazwa** jest zbyt wąska, aby wyświetlić całą nazwę, wskazując mysz na nazwę elementu członkowskiego wyświetla całą nazwę.

- **Typ elementu członkowskiego**

     **MemberType** Komórka używa IntelliSense, który pozwala wybrać z listy wszystkich typów dostępnych w bieżącym projekcie lub projektów, do których istnieje odwołanie.

- **Modyfikator elementu członkowskiego**

     Zmień modyfikator widoczności elementu `Public` członkowskiego`public` `Private` na`private` `Friend` (`internal` `Protected` ),`protected` `Protected Friend` (`protected internal`), `Default`( ), ( ), ( ), lub .

- **\<dodawanie>członkowskich**

     Ostatni wiersz w oknie **Szczegóły klasy** zawiera tekst ** \<dodaj element członkowski>** w komórce **Nazwa.** Po kliknięciu tej komórki, można utworzyć nowy element członkowski. Aby uzyskać więcej informacji, zobacz [Tworzenie członków](creating-and-configuring-type-members.md#create-members).

- **Właściwości elementu członkowskiego w oknie Właściwości**

     Okno **Szczegóły klasy** wyświetla podzbiór właściwości elementu członkowskiego, które są wyświetlane w oknie Właściwości. Zmiana właściwości w jednej lokalizacji zaktualizuje globalnie wartość właściwości. Obejmuje to wyświetlanie jej wartości w innej lokalizacji.

- **Podsumowanie**

     Podsumowanie **Summary** komórki udostępnia podsumowanie informacji o członem. Kliknij wielokropek w komórce **Podsumowanie,** aby wyświetlić lub edytować informacje o **podsumowaniu,** **typie zwrotu**i **uwagach** dla elementu członkowskiego.

- **Ukryj**

     Gdy pole wyboru **Ukryj** jest zaznaczone, element członkowski nie jest wyświetlany w typie.

### <a name="to-modify-a-type-member"></a>Aby zmodyfikować element członkowski typu

1. Za pomocą Projektanta klas, wybierz typ.

2. Jeśli okno **Szczegóły klasy** nie jest wyświetlane, kliknij przycisk okna **Szczegóły klasy** na pasku narzędzi Projektanta klas.

3. Edytuj wartości w polach siatki okna **Szczegóły klasy.** Po każdej modyfikacji naciśnij klawisz ENTER lub w inny sposób przenieś fokus kursora z edytowanego pola, na przykład, naciskając klawisz TAB. Zmiany odzwierciedlają się bezpośrednio w kodzie.

    > [!NOTE]
    > Jeśli chcesz zmodyfikować jedynie nazwę elementu członkowskiego, możesz to zrobić za pomocą edycji w miejscu.

## <a name="add-parameters-to-methods"></a>Dodawanie parametrów do metod

Dodaj parametry do metod przy użyciu okna **Szczegóły klasy.** Parametry mogą być skonfigurowane jako wymagane lub opcjonalne. Podanie wartości dla **opcjonalnej domyślnej** właściwości parametru nakazuje projektantowi generowanie kodu jako parametru opcjonalnego.

Wiersze parametrów zawierają następujące elementy:

- **Nazwa**

     Kolumna **Nazwa** w wierszu parametru wyświetla nazwę parametru. Ta nazwa jest również wyświetlana we właściwości **Name** w oknie Właściwości. Ta komórka służy do zmiany nazwy któregokolwiek parametru, który ma uprawnienia odczytu i zapisu.

     Wskazując nazwę parametru wyświetla nazwę parametru, jeśli kolumna Nazwa jest zbyt **wąska,** aby wyświetlić całą nazwę.

- **Typ**

     Komórka **Typ parametru** używa intellisense, który umożliwia wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub projektach, do których istnieje odwołanie.

- **Modyfikator**

     Komórka **Modyfikator** w wierszu parametru akceptuje i wyświetla nowy modyfikator parametru. Aby wprowadzić nowy modyfikator parametrów, użyj pola listy rozwijanej, aby wybrać z **pola Brak**, **ref**, **out**lub **params** w języku C#, i **ByVal**, **ByRef**lub **ParamArray** w VB.

- **Podsumowanie**

     Podsumowanie **Summary** komórki w wierszu parametru umożliwia wprowadzanie komentarzy kodu, które pojawiają się w IntelliSense podczas wprowadzania parametru do edytora kodu.

- **\<dodawanie>parametrów**

     Ostatni wiersz parametru elementu członkowskiego zawiera tekst **<\> dodania parametru** w komórce **Nazwa.** Kliknięcie tej komórki pozwala utworzyć nowy parametr. Aby uzyskać więcej informacji, zobacz [Aby dodać parametr do metody](creating-and-configuring-type-members.md#add-parameters-to-methods).

Okno **Właściwości** wyświetla te same właściwości parametru wyświetlane w oknie **Szczegóły klasy:** **Nazwa**, **Typ**, **Modyfikator,** **Podsumowanie,** a także opcjonalna właściwość **domyślna.** Zmiana właściwości w jednej lokalizacji aktualizuje globalnie wartość właściwości, włącznie z wyświetlaniem jej wartości w innej lokalizacji.

> [!NOTE]
> Aby dodać parametr do pełnomocnika, zobacz [Tworzenie członków](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Chociaż destruktor jest metodą, to nie może mieć parametrów.

### <a name="to-add-a-parameter-to-a-method"></a>Aby dodać parametr do metody

1. Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać parametr.

     Typ uzyskuje fokus, a jego zawartość jest wyświetlana w oknie **Szczegóły klasy.**

2. W oknie **Szczegóły klasy** rozwiń wiersz metody, do której chcesz dodać parametr.

     Zostanie wyświetlony wiersz wciętego parametru zawierający tylko parę nawiasów, a wyrazy ** \<dodają parametr>.**

3. Kliknij ** \<przycisk Dodaj parametr>**, wpisz nazwę nowego parametru i naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kodu metody. Jest on wyświetlany w oknie **Szczegóły klasy** i właściwości okna.

4. Opcjonalnie określ inne szczegóły dotyczące parametru, takie jak jego typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Aby dodać opcjonalny parametr do metody

1. Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać opcjonalny parametr.

     Typ uzyskuje fokus, a jego zawartość jest wyświetlana w oknie **Szczegóły klasy.**

2. W oknie **Szczegóły klasy** rozwiń wiersz metody, do której chcesz dodać parametr opcjonalny.

     Zostanie wyświetlony wiersz wciętego parametru zawierający tylko parę nawiasów, a wyrazy ** \<dodają parametr>.**

3. Kliknij ** \<przycisk Dodaj parametr>**, wpisz nazwę nowego parametru i naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kodu metody. Jest on wyświetlany w oknie **Szczegóły klasy** i właściwości okna.

4. W oknie Właściwości wpisz wartość właściwości **Opcjonalne domyślne.** Ustawienie właściwości Opcjonalny domyślny parametru powoduje, że ten parametr staje się opcjonalny.

    > [!NOTE]
    > Opcjonalne parametry muszą być ostatnimi parametrami na liście parametrów.

## <a name="class-details-usage-notes"></a>Uwagi dotyczące użycia szczegółów klasy

Prosimy zwrócić uwagę na poniższe wskazówki dotyczące korzystania z okna **Szczegóły klasy.**

### <a name="editable-and-non-editable-cells"></a>Komórki edytowalne i nieedytowalne

Wszystkie komórki w oknie **Szczegóły klasy** można edytować z kilkoma wyjątkami:

- Cały typ jest tylko do odczytu, gdy, na przykład, znajduje się w zestawie odniesienia. Po wybraniu kształtu w Projektancie klas okno **Szczegóły klasy** wyświetla jego szczegóły w stanie tylko do odczytu.

- Dla indeksatorów nazwa jest tylko do odczytu, a pozostałe (typ, modyfikator, podsumowanie) są edytowalne.

- Wszystkie ogólne mają parametry tylko do odczytu w oknie **Szczegóły klasy.** Aby zmienić parametr rodzajowy, wyedytuj jego kod źródłowy.

- Nazwa parametru typu, który jest zdefiniowany w typie rodzajowym, jest tylko do odczytu.

- Gdy kod typu jest uszkodzony (niedościsty), okno **Szczegóły klasy** wyświetla zawartość typu jako tylko do odczytu.

### <a name="the-class-details-window-and-source-code"></a>Okno Szczegóły klasy i kod źródłowy

- Można wyświetlić kod źródłowy, klikając prawym przyciskiem myszy kształt w oknie **Szczegóły klasy** (lub Projektant klasy), a następnie klikając polecenie Wyświetl kod. Plik źródłowy kodu otwiera się i przewija do wybranego elementu.

- Zmiana kodu źródłowego jest natychmiast odzwierciedlana w wyświetlaniu informacji podpisu w projektancie klasy i oknie **Szczegóły klasy.** Jeśli okno **Szczegóły klasy** jest zamknięty w czasie, nowe informacje są widoczne przy następnym otwarciu.

- Gdy kod typu jest uszkodzony (niedościsty), okno **Szczegóły klasy** wyświetla zawartość typu jako tylko do odczytu.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funkcja schowka w oknie Szczegóły klasy

Pola lub wiersze można kopiować lub wycinać z okna **Szczegóły klasy** i wklejać je do innego typu. Wiersz można wyciąć tylko wtedy, gdy nie jest tylko do odczytu. Po wklejeniu wiersza okno **Szczegóły klasy** przypisuje nową nazwę (pochodzącą od nazwy skopiowanego wiersza), aby uniknąć konfliktu.

## <a name="display-of-read-only-information"></a>Wyświetlanie informacji tylko do odczytu

Projektant klas i okno **Szczegóły klasy** mogą wyświetlać typy (i elementy członkowskie typów) dla następujących typów:

- projekt, który zawiera diagram klas

- projekt stanowiący odwołanie z projektu, który zawiera diagram klas

- zestaw stanowiący odwołanie z projektu, który zawiera diagram klas

W dwóch ostatnich przypadkach, jednostka, do której istnieje odwołanie (typ lub składowa), jest tylko do odczytu na diagramie klasy, który ją reprezentuje.

Cały projekt lub jego części, takie jak pojedyncze pliki, mogą być tylko do odczytu. Najbardziej typowe przypadki, w których projekt lub jeden z jego plików jest tylko do odczytu, występują wtedy, gdy projekt jest pod kontrolą kodu źródłowego (i nie jest wyewidencjonowany), istnieje w zestawie zewnętrznym, lub gdy system operacyjny uzna, że pliki są tylko do odczytu.

**Kontrola kodu źródłowego**

Ponieważ diagram klasy jest zapisywany jako plik w projekcie, należy wyewidencjonować projekt, aby zapisać wszelkie zmiany wprowadzone w Projektancie klas lub oknie **Szczegóły klasy.**

**Projekty tylko do odczytu**

Projekt może być tylko do odczytu z przyczyn innych niż kontrola kodu źródłowego. Zamknięcie projektu wyświetla okno dialogowe z pytaniem, czy zastąpić plik projektu, odrzucić zmiany (nie zapisać) lub anulować operację zamknięcia. Jeśli wybierzesz zastąpienie, pliki projektu są zastępowane i udostępnione do odczytu i zapisu. Dodawany jest nowy plik diagramu klasy.

**Typy tylko do odczytu**

Jeśli spróbujesz zapisać projekt zawierający typ, którego plik kodu źródłowego jest tylko do odczytu, zostanie wyświetlone okno dialogowe Zapisywanie pliku tylko do **odczytu,** które umożliwia zapisanie pliku pod nową nazwą lub nową lokalizacją lub zastąpienie pliku tylko do odczytu. Jeśli plik zostanie zastąpiony, nowa kopia nie będzie już tylko do odczytu.

Jeśli plik kodu zawiera błąd składni, kształty wyświetlające kod w tym pliku zostaną tymczasowo ustawione tylko do odczytu, dopóki błąd składni nie zostanie poprawiony. Kształty w tym stanie wyświetlają czerwony tekst i czerwoną ikonę, która wyświetla etykietkę z napisem „plik kodu źródłowego zawiera błąd analizy składni”.

Typ, do którego istnieje odwołanie (na przykład typ .NET), który istnieje w innym węźle projektu lub w węźle zestawu, do którego istnieje odwołanie, jest wskazywany na powierzchni projektowej projektanta klas jako tylko do odczytu. Typ lokalny, który istnieje w otwartym projekcie, jest do odczytu i zapisu, a jego kształt na powierzchni projektowej Projektanta klas jest odpowiednio opisany.

Indeksatory są odczytu i zapisu w kodzie i **szczegóły klasy** okna, ale nazwa indeksatora jest tylko do odczytu.

Nie można edytować metody częściowe przy użyciu Projektanta klas lub **szczegóły klasy** okna; aby je edytować, należy użyć Edytora kodu.

Nie można edytować natywnego kodu C++ przy użyciu projektanta klas lub okna **Szczegóły klasy;** aby edytować natywny kod języka C++, należy użyć Edytora kodu.

## <a name="see-also"></a>Zobacz też

- [Wyświetlanie typów i relacji](designing-and-viewing-classes-and-types.md)
- [Refaktoryzowanie klas i typów](refactoring-classes-and-types.md)
