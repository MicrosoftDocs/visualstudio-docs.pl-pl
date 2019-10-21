---
title: Tworzenie i Konfigurowanie elementów członkowskich typu (Projektant klas) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b871c406b0a2b36d1e7f02a070ab1052510ed20b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619234"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Tworzenie i konfigurowanie typów członków (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można dodać tych członków do typów na diagramie klasy i skonfigurować te elementy członkowskie w oknie **Szczegóły klasy** :

|**Wprowadź**|**Elementy członkowskie, które mogą zawierać**|
|--------------|--------------------------------|
|Class|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Wyliczenie|członek|
|Interface|metoda, właściwość, zdarzenie (w języku C# i Visual Basic)|
|Klasa abstrakcyjna|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|
|Struktura (konstrukcja Struct w języku C#)|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), stała|
|Delegate|Parametr|
|Moduł (tylko w języku VB)|metoda, właściwość, pole, zdarzenie, konstruktor, stała|

> [!NOTE]
> Utwórz bardziej zwartą deklarację właściwości, gdy akcesory właściwości get i set nie potrzebują dodatkowej logiki, za pomocą automatycznie wdrożonych właściwości (tylko C#). Aby wyświetlić pełny podpis, w menu **Diagram klas** wybierz pozycję **Zmień format elementów członkowskich**i **Wyświetl pełny podpis**. Aby uzyskać więcej informacji na temat właściwości, które są implementowane, zobacz [zaimplementowane właściwości](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Rozpocznij:** Przed utworzeniem i skonfigurowaniem elementów członkowskich typu należy otworzyć okno Szczegóły klasy.|-   [otwieranie okno szczegółów klasy](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />[Informacje o użyciu dotyczące klasy](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes) -   <br />-   [wyświetlania informacji tylko do odczytu](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [skróty klawiaturowe i myszy w diagramie klas i okno szczegółów klasy (Projektant klas)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|
|**Tworzenie i modyfikowanie elementów członkowskich typu:** Można tworzyć nowych członków, modyfikować członków i dodawać parametry do metody przy użyciu okna Szczegóły klasy.|-   [tworzenia członków](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [modyfikowanie elementów członkowskich typu](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [dodawania parametrów do metod](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|

## <a name="OpenClassDetails"></a>Otwieranie Okno szczegółów klasy
 Domyślnie Okno szczegółów klasy pojawia się automatycznie po otwarciu nowego diagramu klas (zobacz [jak: Dodawanie diagramów klas do projektów (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Okno Szczegóły klasy można otworzyć także jawnie, w następujący sposób.

#### <a name="to-open-the-class-details-window"></a>Aby otworzyć okno Szczegóły klasy

1. Kliknij prawym przyciskiem myszy dowolną klasę na diagramie, aby wyświetlić menu kontekstowe.

2. W menu kontekstowym kliknij **okno szczegółów klasy**.

   — lub —

- Wskaż **inne okna** w menu Widok, a następnie kliknij pozycję **Szczegóły klasy**.

## <a name="CreateMembers"></a>Tworzenie elementów członkowskich
 Można utworzyć element członkowski, używając dowolnego z następujących narzędzi:

- Projektant klas

- Pasek narzędzi okna Szczegóły klasy

- Okno Szczegóły klasy

> [!NOTE]
> Można również utworzyć konstruktory i destruktory przy użyciu procedur opisanych w tej sekcji. Należy pamiętać, że konstruktory i destruktory są specjalnymi rodzajami metod i w ten sposób pojawiają się w przedziale **metod** w kształtach diagramu klas i w sekcji **metody** siatki okna Szczegóły klasy.

> [!NOTE]
> Jedyna jednostka, jaką można dodać do obiektu delegowanego, to parametr. Należy zauważyć, że procedura „Aby utworzyć składową przy użyciu paska narzędzi okna Szczegóły klasy” nie jest prawidłowa dla tej czynności.

#### <a name="to-create-a-member-using-class-designer"></a>Aby utworzyć składową za pomocą Projektanta klas

1. Kliknij prawym przyciskiem myszy typ, do którego chcesz dodać element członkowski, wskaż polecenie **Dodaj**, a następnie wybierz typ elementu członkowskiego, który chcesz dodać.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Otrzymuje nazwę domyślną, którą można zmienić w **Projektant klas**, oknie **Szczegóły klasy** lub w oknie **Właściwości** .

2. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Aby utworzyć składową za pomocą paska narzędzi okna Szczegóły klasy

1. Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w oknie Szczegóły klasy.

2. Na pasku narzędzi okna Szczegóły klasy kliknij górną ikonę i wybierz pozycję **nowy \<member >** z listy rozwijanej.

     Kursor zostanie przeniesiony do pola **Nazwa** w wierszu dla rodzaju elementu członkowskiego, który chcesz dodać. Jeśli na przykład klikniesz pozycję **Nowa właściwość**, kursor przejdzie do nowego wiersza w sekcji **Właściwości** okna Szczegóły klasy.

3. Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, i naciśnij klawisz Enter (lub przenieś fokus w inny sposób, np. za pomocą klawisza Tab).

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski już istnieje w kodzie i jest wyświetlany w **Projektant klas**, w oknie Szczegóły klasy i okno właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

#### <a name="to-create-a-member-using-the-class-details-window"></a>Aby utworzyć składową za pomocą okna Szczegóły klasy

1. Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.

     Typ uzyskuje fokus i jego zawartość jest wyświetlana w oknie Szczegóły klasy.

2. W oknie Szczegóły klasy, w sekcji zawierającej rodzaj elementu członkowskiego, który chcesz dodać, kliknij **\<add > członka**. Na przykład, jeśli chcesz dodać pole, kliknij **\<add pole >** .

3. Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, a następnie naciśnij klawisz Enter.

     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Element członkowski już istnieje w kodzie i jest wyświetlany w **Projektant klas**, w oknie Szczegóły klasy i okno właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.

     **Uwaga:** Do tworzenia elementów członkowskich można także używać skrótów klawiaturowych. Aby uzyskać więcej informacji, zobacz [skróty klawiaturowe i myszy na diagramie klas i okno szczegółów klasy (Projektant klas)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).

## <a name="ModifyTypeMembers"></a>Modyfikowanie elementów członkowskich typu
 Projektant klas umożliwia modyfikowanie składowych typów, które są wyświetlane na diagramie. Można modyfikować składowe dowolnego typu wyświetlane na diagramie klasy, które nie są tylko do odczytu. (Zobacz [Wyświetlanie informacji tylko do odczytu (Projektant klas)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a). Elementy członkowskie typu są modyfikowane za pomocą edycji w miejscu na powierzchni projektowej, okno Właściwości i w oknie Szczegóły klasy.

 Wszystkie składowe wyświetlane w oknie Szczegóły klasy reprezentują składowe typów na diagramie klasy. Istnieją cztery rodzaje elementów członkowskich: metody, właściwości, pola i zdarzenia.

 Wszystkie wiersze elementów członkowskich pojawiają się pod nagłówkami, które grupują elementy członkowskie według rodzaju. Na przykład wszystkie właściwości są wyświetlane pod **właściwościami**nagłówka, które jako węzeł w siatce mogą być zwinięte lub rozwinięte.

 Każdy wiersz elementu członkowskiego zawiera następujące elementy:

- **Ikona elementu członkowskiego**

     Każdy rodzaj elementu członkowskiego jest reprezentowany przez własną ikonę. Wskaż myszą ikonę elementu członkowskiego, aby wyświetlić sygnaturę elementu członkowskiego. Kliknij ikonę elementu członkowskiego lub przestrzeń z lewej strony ikony elementu członkowskiego, aby zaznaczyć wiersz.

- **Nazwa elementu członkowskiego**

     Kolumna **Nazwa** w wierszu elementu członkowskiego zawiera nazwę elementu członkowskiego. Ta nazwa jest również wyświetlana w właściwości **Nazwa** w okno właściwości. Ta komórka służy do zmiany nazwy któregokolwiek elementu członkowskiego, który ma uprawnienia odczytu i zapisu.

     Jeśli kolumna **Nazwa** jest zbyt wąska, aby wyświetlić całą nazwę, wskaż myszą nazwy elementu członkowskiego, która zawiera całą nazwę.

- **Typ elementu członkowskiego**

     Komórka **MemberType** korzysta z technologii IntelliSense, która umożliwia wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub projektach, do których istnieją odwołania.

- **Modyfikator elementu członkowskiego**

     Zmień modyfikator widoczności elementu członkowskiego na `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`) lub 0.

- **\<add składową >**

     Ostatni wiersz w oknie Szczegóły klasy zawiera tekst **\<add składowej >** w komórce **Nazwa** . Po kliknięciu tej komórki, można utworzyć nowy element członkowski. Aby uzyskać więcej informacji, zobacz [Tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

- **Właściwości elementu członkowskiego w okno Właściwości**

     Okno Szczegóły klasy zawiera podzbiór właściwości składowych, które są wyświetlane w oknie Właściwości. Zmiana właściwości w jednej lokalizacji zaktualizuje globalnie wartość właściwości. Obejmuje to wyświetlanie jej wartości w innej lokalizacji.

- **Podsumowanie**

     Komórka **Podsumowanie** uwidacznia podsumowanie informacji o elemencie członkowskim. Kliknij wielokropek w komórce **Podsumowanie** , aby wyświetlić lub edytować informacje o **podsumowaniu**, **zwracanym typie**i **uwagach** dla elementu członkowskiego.

- **Usuń**

     Gdy pole wyboru **Ukryj** jest zaznaczone, element członkowski nie jest wyświetlany w typie.

#### <a name="to-modify-a-type-member"></a>Aby zmodyfikować element członkowski typu

1. Za pomocą Projektanta klas, wybierz typ.

2. Jeśli okno Szczegóły klasy nie zostanie wyświetlone, kliknij przycisk **okno szczegółów klasy** na pasku narzędzi Projektant klas.

3. Edytuj wartości w polach w siatce okna Szczegóły klasy. Po każdej modyfikacji naciśnij klawisz ENTER lub w inny sposób przenieś fokus kursora z edytowanego pola, na przykład, naciskając klawisz TAB. Zmiany odzwierciedlają się bezpośrednio w kodzie.

    > [!NOTE]
    > Jeśli chcesz zmodyfikować jedynie nazwę elementu członkowskiego, możesz to zrobić za pomocą edycji w miejscu.

## <a name="AddMethodParams"></a>Dodawanie parametrów do metod
 Dodaj parametry do metod przy użyciu okna Szczegóły klasy. Parametry mogą być skonfigurowane jako wymagane lub opcjonalne. Podanie wartości **opcjonalnej właściwości domyślnej** parametru powoduje, że Projektant generuje kod jako opcjonalny parametr.

 Wiersze parametrów zawierają następujące elementy:

- **Nazwa**

   W kolumnie **Nazwa** w wierszu parametru wyświetlana jest nazwa parametru. Ta nazwa jest również wyświetlana w właściwości **Nazwa** w okno właściwości. Ta komórka służy do zmiany nazwy któregokolwiek parametru, który ma uprawnienia odczytu i zapisu.

   Wskazanie nazwy parametru wyświetla nazwę parametru, jeśli kolumna **Nazwa** jest zbyt wąska, aby wyświetlić całą nazwę.

- **Wprowadź**

   Komórka **typu parametru** korzysta z technologii IntelliSense, która umożliwia wybór z listy wszystkich typów dostępnych w bieżącym projekcie lub projektach, do których istnieją odwołania.

- **Modyfikator**

   Komórka **modyfikująca** w wierszu parametru akceptuje i wyświetla nowy modyfikator parametru. Aby wprowadzić nowy modyfikator parametrów, użyj pola listy rozwijanej, aby wybrać opcję z **Brak**, **ref**, **out**lub **params** w C#, i **ByVal**, **ByRef**lub **ParamArray** w języku VB.

- **Podsumowanie**

   Komórka **podsumowania** w wierszu parametru umożliwia wprowadzanie komentarzy do kodu, które pojawiają się w IntelliSense podczas wprowadzania parametru do edytora kodu.

- **\<add parametr >**

   Ostatni wiersz parametru elementu członkowskiego zawiera tekst **< Dodaj parametr \>** w komórce **Nazwa** . Kliknięcie tej komórki pozwala utworzyć nowy parametr. Aby uzyskać więcej informacji, zobacz [Aby dodać parametr do metody](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).

  **Właściwości parametru w okno Właściwości**

  Okno Właściwości wyświetla te same właściwości parametrów, które są wyświetlane w oknie Szczegóły klasy: **nazwę**, **typ**, **modyfikator**, **Podsumowanie**, a także **opcjonalną właściwość domyślną** . Zmiana właściwości w jednej lokalizacji aktualizuje globalnie wartość właściwości, włącznie z wyświetlaniem jej wartości w innej lokalizacji.

> [!NOTE]
> Aby dodać parametr do delegata, zobacz [Tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).

> [!NOTE]
> Chociaż destruktor jest metodą, to nie może mieć parametrów.

### <a name="HowToAddParameterToMethod"></a>Aby dodać parametr do metody

1. Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać parametr.

     Typ uzyskuje fokus i jego zawartość wyświetla się w oknie Szczegóły klasy.

2. W oknie Szczegóły klasy rozszerz wiersz metody, do której chcesz dodać parametr.

     Pojawia się wiersz parametru z wcięciem, zawierający tylko parę nawiasów i słowa **\<add parametr >.**

3. Kliknij **\<add parametr >** , wpisz nazwę nowego parametru i naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kodu metody. Wyświetla się w oknie Szczegóły klasy i w oknie Właściwości.

4. Opcjonalnie określ inne szczegóły dotyczące parametru, takie jak jego typ.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Aby dodać opcjonalny parametr do metody

1. Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać opcjonalny parametr.

     Typ uzyskuje fokus i jego zawartość wyświetla się w oknie Szczegóły klasy.

2. W oknie Szczegóły klasy rozszerz wiersz metody, do której chcesz dodać opcjonalny parametr.

     Pojawia się wiersz parametru z wcięciem, zawierający tylko parę nawiasów i słowa **\<add parametr >.**

3. Kliknij **\<add parametr >** , wpisz nazwę nowego parametru i naciśnij klawisz **Enter**.

     Nowy parametr jest dodawany do metody i kodu metody. Wyświetla się w oknie Szczegóły klasy i w oknie Właściwości.

4. W okno Właściwości wpisz wartość **opcjonalnej właściwości domyślnej** . Ustawienie właściwości Opcjonalny domyślny parametru powoduje, że ten parametr staje się opcjonalny.

    > [!NOTE]
    > Opcjonalne parametry muszą być ostatnimi parametrami na liście parametrów.

## <a name="ClassDetailsUsageNotes"></a>Uwagi dotyczące użycia szczegółów klasy
 Zwróć uwagę na poniższe porady dotyczące korzystania z okna Szczegóły klasy.

 **Edytowalne i nieedytowalne komórki**

 Wszystkie komórki w oknie Szczegóły klasy są edytowalne, z kilkoma wyjątkami:

- Cały typ jest tylko do odczytu, gdy na przykład znajduje się w przywoływanym zestawie (zobacz [Wyświetlanie informacji tylko do odczytu (Projektant klas)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Po wybraniu kształtu w Projektant klas okno Szczegóły klasy wyświetla jego szczegóły w stanie tylko do odczytu.

- Dla indeksatorów nazwa jest tylko do odczytu, a pozostałe (typ, modyfikator, podsumowanie) są edytowalne.

- Wszystkie elementy rodzajowe mają parametry tylko do odczytu w oknie Szczegóły klasy. Aby zmienić parametr rodzajowy, wyedytuj jego kod źródłowy.

- Nazwa parametru typu, który jest zdefiniowany w typie rodzajowym, jest tylko do odczytu.

- Jeżeli kod typu jest uszkodzony (błędny), zawartość typu jest wyświetlana w oknie Szczegóły klasy jako tylko do odczytu.

  **Okno szczegółów klasy i kod źródłowy**

- Możesz wyświetlić kod źródłowy, klikając prawym przyciskiem myszy kształt w oknie Szczegóły klasy (lub Projektant klasy), a następnie klikając przycisk Wyświetl kod. Plik źródłowy kodu otwiera się i przewija do wybranego elementu.

- Zmiana kodu źródłowego jest natychmiast odzwierciedlana w wyświetlaniu sygnatury w Projektancie klas i w oknie Szczegóły klasy. Jeśli okno Szczegóły klasy jest akurat zamknięte, nowe informacje są widoczne przy następnym otwarciu.

- Jeżeli kod typu jest uszkodzony (błędny), zawartość typu jest wyświetlana w oknie Szczegóły klasy jako tylko do odczytu.

  **Funkcje Schowka w Okno szczegółów klasy**

  Można skopiować lub wyciąć pola lub wiersze w oknie Szczegóły klasy i wkleić je do innego typu. Wiersz można wyciąć tylko wtedy, gdy nie jest tylko do odczytu. Podczas wklejania wiersza, okno Szczegóły klasy przypisuje nową nazwę (pochodzącą z nazwy skopiowanego wiersza), aby uniknąć konfliktu.

## <a name="ReadOnlyInfo"></a>Wyświetlanie informacji tylko do odczytu
 Projektant klasy i okno Szczegóły klasy mogą wyświetlać typy (i składowe) dla następujących składowych:

- projekt, który zawiera diagram klas

- projekt stanowiący odwołanie z projektu, który zawiera diagram klas

- zestaw stanowiący odwołanie z projektu, który zawiera diagram klas

  W dwóch ostatnich przypadkach, jednostka, do której istnieje odwołanie (typ lub składowa), jest tylko do odczytu na diagramie klasy, który ją reprezentuje.

  Cały projekt lub jego części, takie jak pojedyncze pliki, mogą być tylko do odczytu. Najbardziej typowe przypadki, w których projekt lub jeden z jego plików jest tylko do odczytu, występują wtedy, gdy projekt jest pod kontrolą kodu źródłowego (i nie jest wyewidencjonowany), istnieje w zestawie zewnętrznym, lub gdy system operacyjny uzna, że pliki są tylko do odczytu.

  **Kontrola kodu źródłowego**

  Ponieważ diagram klas jest zapisywany jako plik w projekcie, należy wyewidencjonować projekt, aby zapisać zmiany wprowadzone w Projektancie klas lub oknie Szczegóły klasy.

  **Projekty tylko do odczytu**

  Projekt może być tylko do odczytu z przyczyn innych niż kontrola kodu źródłowego. Zamknięcie projektu wyświetla okno dialogowe z pytaniem, czy zastąpić plik projektu, odrzucić zmiany (nie zapisywać), czy anulować operację zamknięcia. Jeśli wybierzesz zastąpienie, pliki projektu są zastępowane i udostępnione do odczytu i zapisu. Dodawany jest nowy plik diagramu klasy.

  **Typy tylko do odczytu**

  W przypadku próby zapisania projektu zawierającego typ, którego plik kodu źródłowego jest tylko do odczytu, zostanie wyświetlone okno dialogowe **Zapisywanie pliku tylko do odczytu** , które umożliwia zapisanie pliku pod nową nazwą lub nową lokalizację lub zastąpienie pliku tylko do odczytu. Jeśli plik zostanie zastąpiony, nowa kopia nie będzie już tylko do odczytu.

  Jeśli plik kodu zawiera błąd składni, kształty wyświetlające kod w tym pliku zostaną tymczasowo ustawione tylko do odczytu, dopóki błąd składni nie zostanie poprawiony. Kształty w tym stanie wyświetlają czerwony tekst i czerwoną ikonę, która wyświetla etykietkę z napisem „plik kodu źródłowego zawiera błąd analizy składni”.

  Odwołanie typu (np. typ .NET Framework), które występuje w obszarze innego węzła projektu lub węzła odwołania do zestawu, jest wskazany na powierzchni projektowej Projektanta klas jako tylko do odczytu. Typ lokalny, który istnieje w otwartym projekcie, jest do odczytu i zapisu, a jego kształt na powierzchni projektowej Projektanta klas jest odpowiednio opisany.

  Indeksatory są do odczytu i zapisu w kodzie i oknie Szczegóły klasy, ale nazwa indeksatora jest tylko do odczytu.

  Metod częściowych nie można edytować za pomocą Projektanta klas lub okna Szczegóły klasy; do ich edycji należy użyć Edytora kodu.

  Macierzystego kodu C++ nie można edytować za pomocą Projektanta klas lub okna Szczegóły klasy; do jego edycji należy użyć Edytora kodu.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wyświetlanie typów i relacji (Projektant klas)](../ide/viewing-types-and-relationships-class-designer.md)|Na diagramie klasy można wyświetlić istniejące typy, składowe i relacje.|
|[Refaktoryzacja klas i typów (Projektant klas)](../ide/refactoring-classes-and-types-class-designer.md)|Za pomocą refaktoryzacji można łatwo zmienić typ i elementy członkowskie typu. Można także przenosić składowe między klasami, podzielić klasę na klasy częściowe i implementować interfejsy.|