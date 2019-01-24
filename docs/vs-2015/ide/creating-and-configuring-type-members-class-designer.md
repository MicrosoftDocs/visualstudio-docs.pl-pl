---
title: Tworzenie i konfigurowanie składowych typu (Projektant klas) | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51e9f831941fff79c42c8e7fc529db3df0d46b0d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795306"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Tworzenie i konfigurowanie typów członków (Projektant klas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz dodać te składowe do typów w klasie na diagramie i skonfigurować te składowe w **szczegóły klasy** okna:  
  
|**Typ**|**Elementy członkowskie, jakie mogą one zawierać**|  
|--------------|--------------------------------|  
|Class|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|  
|Wyliczenie|członek|  
|Interface|metoda, właściwość, zdarzenie (w języku C# i Visual Basic)|  
|Klasa abstrakcyjna|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), destruktor (metoda), stała|  
|Struktura (konstrukcja Struct w języku C#)|metoda, właściwość (w języku C# i Visual Basic), pole, zdarzenie (w języku C# i Visual Basic), konstruktor (metoda), stała|  
|Delegate|Parametr|  
|Moduł (tylko w języku VB)|metoda, właściwość, pole, zdarzenie, konstruktor, stała|  
  
> [!NOTE]
>  Utwórz bardziej zwartą deklarację właściwości, gdy akcesory właściwości get i set nie potrzebują dodatkowej logiki, za pomocą automatycznie wdrożonych właściwości (tylko C#). Aby wyświetlić pełny podpis z **Diagram klas** menu, wybierz **Zmień Format elementów członkowskich**, **Wyświetl pełną sygnaturę**. Aby uzyskać więcej informacji dotyczących automatycznie implementowanych właściwości, zobacz [implemented Properties](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Rozpocznij pracę:** Zanim utworzysz i skonfigurujesz składowe typu, należy otworzyć okno Szczegóły klasy.|-   [Otwieranie okna Szczegóły klasy](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Uwagi dotyczące użycia okna Szczegóły klasy](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Wyświetlanie informacji tylko do odczytu](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Skróty myszy i klawiaturowe w diagramie klas i oknie szczegółów klasy (Projektant klas)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|  
|**Tworzenie i modyfikowanie składowych typu:** Można tworzyć nowe składowe, modyfikowanie składowych i Dodawanie parametrów do metody przy użyciu okna Szczegóły klasy.|-   [Tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Modyfikowanie elementów członkowskich typu](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Dodawanie parametrów do metod](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|  
  
##  <a name="OpenClassDetails"></a> Otwieranie okna Szczegóły klasy  
 Domyślnie, okno Szczegóły klasy pojawia się automatycznie po otwarciu nowego diagramu klasy (zobacz [jak: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Okno Szczegóły klasy można otworzyć także jawnie, w następujący sposób.  
  
#### <a name="to-open-the-class-details-window"></a>Aby otworzyć okno Szczegóły klasy  
  
1. Kliknij prawym przyciskiem myszy w dowolnej klasie na diagramie, aby wyświetlić menu kontekstowe.  
  
2. W menu kontekstowym kliknij **okna Szczegóły klasy**.  
  
   — lub —  
  
-   Wskaż **Windows inne** w menu Widok, a następnie kliknij przycisk **szczegóły klasy**.  
  
##  <a name="CreateMembers"></a> Tworzenie elementów członkowskich  
 Można utworzyć element członkowski, używając dowolnego z następujących narzędzi:  
  
-   Projektant klas  
  
-   Pasek narzędzi okna Szczegóły klasy  
  
-   Okno Szczegóły klasy  
  
> [!NOTE]
>  Można również utworzyć konstruktory i destruktory przy użyciu procedur opisanych w tej sekcji. Należy pamiętać, że konstruktory i destruktory to szczególne rodzaje metod i jako takie pojawiają się na **metody** przedziału w kształtach diagramu klas i w **metody** sekcji klasy Siatki okna Szczegóły.  
  
> [!NOTE]
>  Jedyna jednostka, jaką można dodać do obiektu delegowanego, to parametr. Należy zauważyć, że procedura „Aby utworzyć składową przy użyciu paska narzędzi okna Szczegóły klasy” nie jest prawidłowa dla tej czynności.  
  
#### <a name="to-create-a-member-using-class-designer"></a>Aby utworzyć składową za pomocą Projektanta klas  
  
1.  Kliknij prawym przyciskiem myszy typ, do którego chcesz dodać element członkowski, wskaż polecenie **Dodaj**, a następnie wybierz typ elementu członkowskiego, które chcesz dodać.  
  
     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Otrzymuje nazwę domyślną, która może zmieniać w **projektanta klas**, **szczegóły klasy** oknie lub w **właściwości** okna.  
  
2.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.  
  
#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Aby utworzyć składową za pomocą paska narzędzi okna Szczegóły klasy  
  
1.  Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.  
  
     Typ uzyskuje fokus i jego zawartość jest wyświetlana w oknie Szczegóły klasy.  
  
2.  Na pasku narzędzi okna Szczegóły klasy kliknij górną ikonę i wybierz pozycję **New \<składowej >** z listy rozwijanej.  
  
     Kursor przesuwa się do **nazwa** pola w wierszu dla rodzaju elementu członkowskiego, które chcesz dodać. Na przykład, jeśli kliknięto przycisk **nową właściwość**, kursor zostanie przeniesiony do nowego wiersza w **właściwości** okna Szczegóły klasy.  
  
3.  Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, i naciśnij klawisz Enter (lub przenieś fokus w inny sposób, np. za pomocą klawisza Tab).  
  
     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Składowa istnieje teraz w kodzie i jest wyświetlany w **projektanta klas**, okno Szczegóły klasy i w oknie właściwości.  
  
4.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.  
  
#### <a name="to-create-a-member-using-the-class-details-window"></a>Aby utworzyć składową za pomocą okna Szczegóły klasy  
  
1.  Na powierzchni diagramu wybierz typ, do którego chcesz dodać element członkowski.  
  
     Typ uzyskuje fokus i jego zawartość jest wyświetlana w oknie Szczegóły klasy.  
  
2.  W oknie Szczegóły klasy, w sekcji zawierającej rodzaj elementu członkowskiego, które chcesz dodać, kliknij  **\<Dodawanie elementu członkowskiego >**. Na przykład jeśli chcesz dodać pole, kliknij pozycję  **\<Dodaj pole >**.  
  
3.  Wpisz nazwę elementu członkowskiego, który chcesz utworzyć, a następnie naciśnij klawisz Enter.  
  
     Nowa sygnatura elementu członkowskiego jest tworzona i dodawana do typu. Składowa istnieje teraz w kodzie i jest wyświetlany w **projektanta klas**, okno Szczegóły klasy i w oknie właściwości.  
  
4.  Opcjonalnie określ inne szczegóły dotyczące elementu członkowskiego, takie jak jego typ.  
  
     **Uwaga:** Skróty klawiaturowe można również użyć do tworzenia elementów członkowskich. Aby uzyskać więcej informacji, zobacz [skróty myszy i klawiaturowe w diagramie klas i oknie szczegółów klasy (Projektant klas)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).  
  
##  <a name="ModifyTypeMembers"></a> Modyfikowanie elementów członkowskich typu  
 Projektant klas umożliwia modyfikowanie składowych typów, które są wyświetlane na diagramie. Można modyfikować składowe dowolnego typu wyświetlane na diagramie klasy, które nie są tylko do odczytu. (Zobacz [wyświetlanie informacji tylko do odczytu (Projektant klas)](http://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Składowe typu modyfikuje się za pomocą edycji w miejscu na powierzchni projektowej, w oknie Właściwości i w oknie Szczegóły klasy.  
  
 Wszystkie składowe wyświetlane w oknie Szczegóły klasy reprezentują składowe typów na diagramie klasy. Istnieją cztery rodzaje elementów członkowskich: metody, właściwości, pola i zdarzenia.  
  
 Wszystkie wiersze elementów członkowskich pojawiają się pod nagłówkami, które grupują elementy członkowskie według rodzaju. Na przykład, wszystkie właściwości są wyświetlane pod nagłówkiem **właściwości**, który, jako węzeł w siatce, zwijania i rozwijania.  
  
 Każdy wiersz elementu członkowskiego zawiera następujące elementy:  
  
-   **Ikona elementu członkowskiego**  
  
     Każdy rodzaj elementu członkowskiego jest reprezentowany przez własną ikonę. Wskaż myszą ikonę elementu członkowskiego, aby wyświetlić sygnaturę elementu członkowskiego. Kliknij ikonę elementu członkowskiego lub przestrzeń z lewej strony ikony elementu członkowskiego, aby zaznaczyć wiersz.  
  
-   **Nazwa elementu członkowskiego**  
  
     **Nazwa** kolumny w wierszu elementu członkowskiego Wyświetla nazwę elementu członkowskiego. Ta nazwa jest wyświetlany na **nazwa** właściwości w oknie dialogowym właściwości. Ta komórka służy do zmiany nazwy któregokolwiek elementu członkowskiego, który ma uprawnienia odczytu i zapisu.  
  
     Jeśli **nazwa** kolumna jest zbyt wąska, aby wyświetlić całą nazwę, wskazanie myszą na nazwę elementu członkowskiego powoduje wyświetlenie całej nazwy.  
  
-   **Typ elementu członkowskiego**  
  
     **MemberType** komórki korzysta z technologii IntelliSense, która pozwala na wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub w projektach odwołania.  
  
-   **Modyfikator składowej**  
  
     Zmień widoczność modyfikator elementu członkowskiego albo `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`), lub `Default`.  
  
-   **\<Dodaj element członkowski >**  
  
     Ostatni wiersz w oknie Szczegóły klasy zawiera tekst  **\<Dodawanie elementu członkowskiego >** w **nazwa** komórki. Po kliknięciu tej komórki, można utworzyć nowy element członkowski. Aby uzyskać więcej informacji, zobacz [tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
-   **Właściwości elementu członkowskiego w oknie dialogowym właściwości**  
  
     Okno Szczegóły klasy zawiera podzbiór właściwości składowych, które są wyświetlane w oknie Właściwości. Zmiana właściwości w jednej lokalizacji zaktualizuje globalnie wartość właściwości. Obejmuje to wyświetlanie jej wartości w innej lokalizacji.  
  
-   **Podsumowanie**  
  
     **Podsumowania** komórki uwidacznia podsumowanie informacji na temat elementu członkowskiego. Kliknij przycisk wielokropka w **Podsumowanie** komórki, aby wyświetlić lub edytować informacje o **Podsumowanie**, **typie zwracanym**, i **uwagi** dla elementu członkowskiego .  
  
-   **Ukryj**  
  
     Gdy **Ukryj** pole wyboru jest zaznaczone, element członkowski nie jest wyświetlany w typie.  
  
#### <a name="to-modify-a-type-member"></a>Aby zmodyfikować element członkowski typu  
  
1.  Za pomocą Projektanta klas, wybierz typ.  
  
2.  Jeśli nie zostanie wyświetlone okno Szczegóły klasy, kliknij przycisk **okna Szczegóły klasy** przycisk na pasku narzędzi projektanta klas.  
  
3.  Edytuj wartości w polach w siatce okna Szczegóły klasy. Po każdej modyfikacji naciśnij klawisz ENTER lub w inny sposób przenieś fokus kursora z edytowanego pola, na przykład, naciskając klawisz TAB. Zmiany odzwierciedlają się bezpośrednio w kodzie.  
  
    > [!NOTE]
    >  Jeśli chcesz zmodyfikować jedynie nazwę elementu członkowskiego, możesz to zrobić za pomocą edycji w miejscu.  
  
##  <a name="AddMethodParams"></a> Dodawanie parametrów do metod  
 Dodaj parametry do metod przy użyciu okna Szczegóły klasy. Parametry mogą być skonfigurowane jako wymagane lub opcjonalne. Podanie wartości dla **opcjonalny domyślny** właściwości parametru powoduje, że projektant generuje kod jako parametr opcjonalny.  
  
 Wiersze parametrów zawierają następujące elementy:  
  
- **Nazwa**  
  
   **Nazwa** kolumna w wierszu parametru wyświetla nazwę parametru. Ta nazwa jest wyświetlany na **nazwa** właściwości w oknie dialogowym właściwości. Ta komórka służy do zmiany nazwy któregokolwiek parametru, który ma uprawnienia odczytu i zapisu.  
  
   Wskazuje na nazwę parametru wyświetla nazwę parametru, jeśli **nazwa** kolumna jest zbyt wąska, aby wyświetlić całą nazwę.  
  
- **Typ**  
  
   **Typ parametru** komórki korzysta z technologii Intellisense, która pozwala na wybranie z listy wszystkich typów dostępnych w bieżącym projekcie lub w projektach odwołania.  
  
- **Modifier**  
  
   **Modyfikator** komórki w wierszu parametru akceptuje i wyświetla nowy modyfikator parametru. Aby wprowadzić nowy modyfikator parametru, użyj pola listy rozwijanej, aby dokonać wyboru spośród **Brak**, **ref**, **się**, lub **params** w języku C# i **ByVal**, **ByRef**, lub **ParamArray** w VB.  
  
- **Podsumowanie**  
  
   **Podsumowanie** komórki w wierszu parametru umożliwia wprowadzanie komentarzy do kodu, które są wyświetlane w IntelliSense podczas wprowadzania parametru w edytorze kodu.  
  
- **\<Dodaj parametr >**  
  
   Ostatni wiersz parametru elementu członkowskiego zawiera tekst **<add parameter>** w **nazwa** komórki. Kliknięcie tej komórki pozwala utworzyć nowy parametr. Aby uzyskać więcej informacji, zobacz [Aby dodać parametr do metody](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).  
  
  **Właściwości parametru w oknie dialogowym właściwości**  
  
  Okno właściwości wyświetla te same właściwości parametru wyświetlane w oknie Szczegóły klasy: **Nazwa**, **typu**, **modyfikator**, **Podsumowanie**, jak również **opcjonalny domyślny** właściwości. Zmiana właściwości w jednej lokalizacji aktualizuje globalnie wartość właściwości, włącznie z wyświetlaniem jej wartości w innej lokalizacji.  
  
> [!NOTE]
>  Aby dodać parametr do delegata, zobacz [tworzenie elementów członkowskich](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
> [!NOTE]
>  Chociaż destruktor jest metodą, to nie może mieć parametrów.  
  
###  <a name="HowToAddParameterToMethod"></a> Aby dodać parametr do metody  
  
1.  Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać parametr.  
  
     Typ uzyskuje fokus i jego zawartość wyświetla się w oknie Szczegóły klasy.  
  
2.  W oknie Szczegóły klasy rozszerz wiersz metody, do której chcesz dodać parametr.  
  
     Pojawi się wiersz parametru z wcięciem, zawierający tylko parę nawiasów i wyrazy  **\<Dodaj parametr >.**  
  
3.  Kliknij przycisk  **\<Dodaj parametr >**, wpisz nazwę nowego parametru, a następnie naciśnij klawisz **Enter**.  
  
     Nowy parametr jest dodawany do metody i kodu metody. Wyświetla się w oknie Szczegóły klasy i w oknie Właściwości.  
  
4.  Opcjonalnie określ inne szczegóły dotyczące parametru, takie jak jego typ.  
  
### <a name="to-add-an-optional-parameter-to-a-method"></a>Aby dodać opcjonalny parametr do metody  
  
1.  Na powierzchni diagramu kliknij typ zawierający metodę, do której chcesz dodać opcjonalny parametr.  
  
     Typ uzyskuje fokus i jego zawartość wyświetla się w oknie Szczegóły klasy.  
  
2.  W oknie Szczegóły klasy rozszerz wiersz metody, do której chcesz dodać opcjonalny parametr.  
  
     Pojawi się wiersz parametru z wcięciem, zawierający tylko parę nawiasów i wyrazy  **\<Dodaj parametr >.**  
  
3.  Kliknij przycisk  **\<Dodaj parametr >**, wpisz nazwę nowego parametru, a następnie naciśnij klawisz **Enter**.  
  
     Nowy parametr jest dodawany do metody i kodu metody. Wyświetla się w oknie Szczegóły klasy i w oknie Właściwości.  
  
4.  W oknie właściwości wpisz wartość dla **opcjonalny domyślny** właściwości. Ustawienie właściwości Opcjonalny domyślny parametru powoduje, że ten parametr staje się opcjonalny.  
  
    > [!NOTE]
    >  Opcjonalne parametry muszą być ostatnimi parametrami na liście parametrów.  
  
##  <a name="ClassDetailsUsageNotes"></a> Uwagi dotyczące użycia okna Szczegóły klasy  
 Zwróć uwagę na poniższe porady dotyczące korzystania z okna Szczegóły klasy.  
  
 **Komórki edytowalne i nieedytowalne**  
  
 Wszystkie komórki w oknie Szczegóły klasy są edytowalne, z kilkoma wyjątkami:  
  
- Cały typ jest tylko do odczytu, gdy, na przykład znajduje się w zestawie odwołania (zobacz [wyświetlanie informacji tylko do odczytu (Projektant klas)](http://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).) Po zaznaczeniu kształtu w Konstruktorze klasy, okno Szczegóły klasy wyświetla jego szczegóły w stanie tylko do odczytu.  
  
- Dla indeksatorów nazwa jest tylko do odczytu, a pozostałe (typ, modyfikator, podsumowanie) są edytowalne.  
  
- Wszystkie elementy rodzajowe mają parametry tylko do odczytu w oknie Szczegóły klasy. Aby zmienić parametr rodzajowy, wyedytuj jego kod źródłowy.  
  
- Nazwa parametru typu, który jest zdefiniowany w typie rodzajowym, jest tylko do odczytu.  
  
- Jeżeli kod typu jest uszkodzony (błędny), zawartość typu jest wyświetlana w oknie Szczegóły klasy jako tylko do odczytu.  
  
  **Okno Szczegóły klasy i kod źródłowy**  
  
- Możesz wyświetlić kod źródłowy, klikając prawym przyciskiem myszy kształt w oknie Szczegóły klasy (lub Projektant klasy), a następnie klikając przycisk Wyświetl kod. Plik źródłowy kodu otwiera się i przewija do wybranego elementu.  
  
- Zmiana kodu źródłowego jest natychmiast odzwierciedlana w wyświetlaniu sygnatury w Projektancie klas i w oknie Szczegóły klasy. Jeśli okno Szczegóły klasy jest akurat zamknięte, nowe informacje są widoczne przy następnym otwarciu.  
  
- Jeżeli kod typu jest uszkodzony (błędny), zawartość typu jest wyświetlana w oknie Szczegóły klasy jako tylko do odczytu.  
  
  **Funkcja Schowka w oknie Szczegóły klasy**  
  
  Można skopiować lub wyciąć pola lub wiersze w oknie Szczegóły klasy i wkleić je do innego typu. Wiersz można wyciąć tylko wtedy, gdy nie jest tylko do odczytu. Podczas wklejania wiersza, okno Szczegóły klasy przypisuje nową nazwę (pochodzącą z nazwy skopiowanego wiersza), aby uniknąć konfliktu.  
  
##  <a name="ReadOnlyInfo"></a> Wyświetlanie informacji tylko do odczytu  
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
  
  Jeśli zostanie podjęta próba zapisania projektu zawierającego typ, którego plik kodu źródłowego jest tylko do odczytu, **Zapisz z uprawnieniami tylko do odczytu pliku** pojawi się okno dialogowe, które daje wybór, aby zapisać plik pod nową nazwą lub w nowej lokalizacji lub zastąpienia pliku tylko do odczytu . Jeśli plik zostanie zastąpiony, nowa kopia nie będzie już tylko do odczytu.  
  
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