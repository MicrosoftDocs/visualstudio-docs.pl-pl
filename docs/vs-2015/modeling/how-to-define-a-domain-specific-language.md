---
title: Jak zdefiniować język specyficzny dla domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
ms.assetid: d1772463-0eb1-40a5-b7c0-9a008bc76760
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ded7dcc05907f2f6a3d8c43af175ad55c499f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543328"
---
# <a name="how-to-define-a-domain-specific-language"></a>Porady: definiowanie języka właściwego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby zdefiniować język specyficzny dla domeny (DSL), należy utworzyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie na podstawie szablonu. Kluczową częścią rozwiązania jest diagram definicji DSL, który jest przechowywany w DslDefinition. DSL. Definicja DSL definiuje klasy i kształty DSL. Po zmodyfikowaniu i dodaniu tych elementów możesz dodać kod programu, aby dostosować DSL w bardziej szczegółowy sposób.

## <a name="selecting-a-template-solution"></a><a name="templates"></a> Wybieranie rozwiązania szablonu
 Aby zdefiniować DSL, należy zainstalować następujące składniki:

|Produkt|Link pobierania|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio Wizualizacja i Modeling SDK|[Pobieranie zestawu SDK modelowania](https://www.microsoft.com/download/details.aspx?id=48148)|

 Aby utworzyć nowy język specyficzny dla domeny, należy utworzyć nowe [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie przy użyciu szablonu projektu języka specyficznego dla domeny.

#### <a name="to-create-a-dsl-solution"></a>Aby utworzyć rozwiązanie DSL

1. Utwórz rozwiązanie z szablonem **języka specyficznego dla domeny** , który można znaleźć w obszarze **Inne typy projektów/rozszerzalność** w oknie dialogowym **Nowy projekt** .

    ![Utwórz okno dialogowe DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")

    Po kliknięciu przycisku **OK**zostanie otwarty **Kreator języka specyficznego dla domeny** i zostanie wyświetlona lista rozwiązań opartych na szablonie.

2. Kliknij każdy szablon, aby wyświetlić opis. Wybierz rozwiązanie najlepiej przypominające to, co chcesz utworzyć.

    Każdy szablon DSL Definiuje podstawową działającą sieć DSL. Edytujesz to połączenie DSL zgodnie z własnymi wymaganiami.

    Kliknij każdy przykład, aby uzyskać więcej informacji.

   - Wybierz pozycję **przepływ zadań** , aby utworzyć DSL z podsieciami. Tory to pionowe lub poziome partycje diagramu.

   - Wybierz pozycję **modele składników** , aby utworzyć DSL z portami. Porty to małe kształty na granicy większego kształtu.

   - Wybierz **diagramy klas** , aby zdefiniować DSL, które mają kształty przedziału. Kształty przedziału zawierają listy elementów.

   - Wybierz opcję **minimalny język** w innych przypadkach lub jeśli jesteś nieokreślony.

       > [!NOTE]
       > Jeśli chcesz utworzyć diagram klas lub diagram składników, rozważ użycie modeli UML. Narzędzia modelowania UML zapewniają zestaw diagramów zintegrowanych wokół jednego modelu. Są one rozszerzalne i mogą być zintegrowane z DSL przy użyciu ModelBus. Aby uzyskać więcej informacji, zobacz [Tworzenie modeli dla aplikacji](../modeling/create-models-for-your-app.md).

   - Wybierz **minimalny Projektant WinForm** lub **minimalny Projektant WPF** , aby utworzyć DSL, który jest wyświetlany na powierzchni Windows Forms lub WPF. Musisz napisać kod w celu zdefiniowania edytora. Aby uzyskać więcej informacji, zobacz następujące tematy:

        [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

        [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3. Wprowadź rozszerzenie nazwy pliku dla języka DSL na odpowiedniej stronie kreatora. Jest to rozszerzenie, które będzie używać plików zawierających wystąpienia DSL.

   - Wybierz rozszerzenie nazwy pliku, które nie jest skojarzone z żadną aplikacją na komputerze lub na dowolnym komputerze, na którym chcesz zainstalować DSL. Na przykład, **docx** i **htm** byłyby nieakceptowalnymi rozszerzeniami nazw plików.

   - Kreator wyświetli ostrzeżenie, jeśli wprowadzone rozszerzenie jest używane jako DSL. Rozważ użycie innego rozszerzenia nazwy pliku. Możesz również zresetować wystąpienie eksperymentalne zestawu Visual Studio SDK, aby wyczyścić stare eksperymentalne projektanci. Kliknij przycisk **Start**, kliknij pozycję **wszystkie programy**, **Microsoft Visual Studio zestaw SDK 2010**, **Narzędzia**, a następnie **Zresetuj wystąpienie eksperymentalne Microsoft Visual Studio 2010**.

4. Można dostosować ustawienia na innych stronach lub pozostawić wartości domyślne.

5. Kliknij przycisk **Zakończ**.

    Kreator tworzy rozwiązanie, które zawiera dwa lub trzy projekty i generuje kod z definicji DSL.

   Interfejs użytkownika jest teraz podobny do poniższego obrazu.

   ![Projektant DSL](../modeling/media/dsl-designer.png "dsl_designer")

   To rozwiązanie definiuje język specyficzny dla domeny. Aby uzyskać więcej informacji, zobacz [Omówienie interfejsu użytkownika narzędzia języka specyficznego dla domeny](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Testowanie rozwiązania
 Rozwiązanie szablonu udostępnia działającą sieć DSL, którą można modyfikować lub używać.

 Aby przetestować rozwiązanie, naciśnij klawisz F5 lub CTRL + F5. Nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otwiera się w trybie eksperymentalnym.

 W nowym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w Eksplorator rozwiązań Otwórz przykładowy plik. Zostanie otwarty jako diagram z przybornikiem.

 Jeśli zostanie uruchomione rozwiązanie utworzone przy użyciu szablonu **minimalnego języka** , eksperymentalny [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] będzie wyglądać podobnie do poniższego przykładu:

 ![](../modeling/media/dsl-min.png "DSL_min")

 Eksperymentuj z narzędziami. Utwórz elementy i połącz je.

 Zamknij wystąpienie eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

> [!NOTE]
> Po zmodyfikowaniu DSL nie będzie już można zobaczyć kształtów w przykładowym pliku testowym. Jednak będzie można tworzyć nowe elementy.

### <a name="modifying-the-template-dsl"></a>Modyfikowanie szablonu DSL
 Zmień nazwę i Zachowaj niektóre lub wszystkie klasy domeny i klasy kształtów w definicji szablonu DSL. Nowe nazwy klas powinny być Prawidłowymi nazwami CLR, bez spacji i znaków interpunkcyjnych.

 Jest to szczególnie przydatne do przechowywania tych klas:

- Klasa główna pojawia się w lewym górnym rogu diagramu definicji DSL, w obszarze **klasy i relacje**. Zmień nazwę na inną niż nazwa inna niż DSL. Na przykład DSL o nazwie **MusicLibrary** może mieć klasę główną o nazwie **muzyka**.

- Klasa diagram jest wyświetlana w prawym dolnym rogu diagramu definicji DSL w kolumnie **elementy diagramu** . Może być konieczne przewinięcie w prawo, aby je zobaczyć. Ma zwykle nazwę diagram _YourDsl_**Diagram**.

- Jeśli użyto szablonu **przepływu zadań** i chcesz utworzyć diagramy z tormi, Zachowaj i Zmień nazwę klasy domeny aktora i kształtu ActorSwimlane.

  Usuń inne klasy lub zmień ich nazwy zgodnie z wymaganiami.

## <a name="patterns-for-defining-a-dsl"></a><a name="patterns"></a> Wzorce definiowania linii DSL
 Zalecamy tworzenie DSL przez dodanie lub dostosowanie jednej lub dwóch funkcji jednocześnie. Dodaj funkcję, uruchom ją i przetestuj ją, a następnie Dodaj jedną lub dwie więcej funkcji. Typową funkcją sieci DSL może być:

- Klasa domeny, relacja osadzania łącząca element z modelem, kształt wymagany do wyświetlania elementów tej klasy na diagramie oraz narzędzie elementu, które umożliwia użytkownikom tworzenie elementów.

- Właściwości domeny klasy domeny i dekoratory, które wyświetlają je na kształcie.

- Relacja odwołania i łącznik, który wyświetla go na diagramie i narzędziu łącznika, które umożliwia użytkownikom tworzenie linków.

- Dostosowanie, które wymaga kodu programu, takiego jak ograniczenie walidacji lub polecenie menu.

  W poniższych sekcjach opisano sposób konstruowania najbardziej przydatnych rodzajów funkcji DSL. Istnieje wiele innych wzorców, z którymi można utworzyć DSL, ale są one najczęściej używane.

> [!NOTE]
> Po dodaniu funkcji nie zapomnij kliknąć polecenie **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań przed rozpoczęciem kompilowania i uruchamiania programu DSL.

 Poniższy rysunek przedstawia klasy i relacje z częścią DSL, która jest używana jako przykład w tym temacie.

 ![Relacje osadzania i odwołania](../modeling/media/music-classes.png "Music_Classes")

 Następnym rysunkiem jest przykładowy model tego języka DSL:

 ![Model wystąpienia wygenerowanego DSL](../modeling/media/music-instance.png "Music_Instance")

> [!NOTE]
> "Model" odnosi się do instancji DSL tworzonego przez użytkowników i zazwyczaj jest wyświetlana jako diagram. W tym temacie omówiono zarówno diagram definicji DSL, jak i diagramy modelu, które są wyświetlane, gdy używany jest język DSL.

## <a name="defining-domain-classes"></a><a name="classes"></a> Definiowanie klas domeny
 Klasy domeny reprezentują koncepcje DSL. Wystąpienia są *elementami modelu*. Na przykład w **MusicLibrary** DSL mogą istnieć klasy domeny o nazwie **album** i **utwór**.

 Aby utworzyć klasę domeny, możesz przeciągnąć ją z narzędzia **klasy nazwanej domeny** do diagramu, a następnie zmienić nazwę klasy.

 Aby uzyskać więcej informacji, zobacz [właściwości klas domeny](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Utwórz relację osadzania dla każdej klasy domeny
 Każda klasa domeny z wyjątkiem klasy głównej musi być elementem docelowym co najmniej jednej relacji osadzania lub musi dziedziczyć z klasy, która jest elementem docelowym relacji osadzania.

 W modelu każdy element modelu jest węzłem w jednym drzewie relacji osadzania. Źródłowa i docelowa relacja osadzania jest często określana jako element nadrzędny i podrzędny.

 Wybór elementu nadrzędnego dla klasy domeny zależy od tego, w jaki sposób jego elementy życia są zależne od innych elementów. Jeśli węzeł drzewa zostanie usunięty, jego poddrzewo jest zazwyczaj również usuwane. Klasy elementów, które mają niezależny istnienie, są w związku z tym osadzone bezpośrednio w klasie głównej.

 Zwykle, Jeśli wyświetlasz element wewnątrz innego elementu, chcesz wskazać relację właściciela. W takim przypadku najbardziej odpowiednia Klasa nadrzędna jest klasą kontenera. Wyjątek występuje, gdy element widoczny wewnątrz kontenera jest w rzeczywistości jedynie odwołaniem do niezależnego elementu. W takim przypadku usunięcie kontenera usuwa odwołanie, ale nie jego cel.

 We wzorcu definicji DSL opisanej w tym temacie przyjęto założenie, że elementy wyświetlane wewnątrz kontenera zostaną usunięte po usunięciu kontenera. Możliwe jest bardziej złożone schematy i można je osiągnąć przez definiowanie reguł.

|Sposób wyświetlania elementu|Klasa nadrzędna (osadzania)|Przykład w szablonie rozwiązania DSL|
|------------------------------|--------------------------------|--------------------------------------|
|Kształt na diagramie.<br /><br /> Toru.|Klasa główna DSL.|Minimalny język.<br /><br /> Przepływ zadań: Klasa aktora.|
|Kształt w tor.|Klasa domeny elementów, które są wyświetlane jako ścieżki.|Przepływ zadań: Klasa zadań.|
|Element na liście w kształcie, gdzie element jest usuwany po usunięciu kontenera.<br /><br /> Port na krawędzi kształtu.|Klasa domeny, która jest mapowana na kształt kontenera.|Diagram klas: Klasa atrybutu.<br /><br /> Diagram składników: Klasa portu.|
|Element na liście, nie został usunięty, jeśli kontener został usunięty.|Klasa główna DSL.<br /><br /> Na liście są wyświetlane linki odwołań.||
|Nie są wyświetlane bezpośrednio.|Klasa, dla której jest częścią.||

 W bibliotece Muzyka przykładowo albumy są wyświetlane jako prostokąty, w których są wyświetlane tytuły utworów. W związku z tym nadrzędnym albumem jest muzyka klasy głównej, a nadrzędny utwór jest albumem.

 Aby utworzyć klasę domeny i jej osadzenie w tym samym czasie, kliknij narzędzie **osadzanie relacji** , a następnie kliknij klasę nadrzędną, a następnie kliknij pustą część diagramu.

 Nie jest zwykle konieczna zmiana nazwy relacji osadzania i jej ról, ponieważ będą one automatycznie śledzić nazwy klas.

 Aby uzyskać więcej informacji, zobacz [właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i [Właściwości ról domeny](../modeling/properties-of-domain-roles.md).

> [!NOTE]
> Osadzanie nie jest takie samo jak dziedziczenie. Elementy podrzędne w relacji osadzania nie dziedziczą funkcji z ich nadrzędnych.

### <a name="add-domain-properties-to-each-domain-class"></a>Dodawanie właściwości domeny do każdej klasy domeny
 Właściwości domeny przechowują wartości. Przykłady: imię i nazwisko, tytuł, Data publikacji.

 Kliknij pozycję **właściwości domeny** w klasie, naciśnij klawisz ENTER, a następnie wpisz nazwę właściwości. Domyślny typ właściwości domeny to ciąg. Jeśli chcesz zmienić typ, wybierz właściwość domena i ustaw **Typ** w oknie **Właściwości** . Jeśli typ, który chcesz, nie znajduje się na liście rozwijanej, zobacz [Dodawanie typów właściwości](#addTypes).

 **Ustaw właściwość nazwy elementu.** Wybierz właściwość domeny, która może służyć do identyfikowania elementów w Eksploratorze języka. Na przykład w klasie utwór, w której można wybrać właściwość Nazwa domeny. W oknie **Właściwości** ustaw wartość **Nazwa elementu** na `true` .

### <a name="create-derived-domain-classes"></a>Utwórz klasy domeny pochodnej
 Jeśli chcesz, aby Klasa domeny miała różne odmiany, które dziedziczą jej właściwości i relacje, Utwórz klasy pochodne od niej. Na przykład album może mieć klasy pochodne WMA i MP3.

 Utwórz klasę pochodną przy użyciu narzędzia **klasy domeny** .

 Kliknij narzędzie **dziedziczenia** , kliknij klasę pochodną, a następnie kliknij klasę bazową.

 Rozważ ustawienie **modyfikatora dziedziczenia** klasy podstawowej na **abstrakcyjną**. Jeśli uważasz, że może być konieczne wystąpienie klasy bazowej, rozważ zamiast tego utwórz oddzielną klasę pochodną.

 Klasy pochodne dziedziczą właściwości i role ich klas podstawowych.

### <a name="tidy-the-dsl-definition-diagram"></a>Uporządkowanego diagramu definicji DSL
 Gdy dodajesz relacje, niektóre klasy będą wyświetlane w więcej niż jednym miejscu. Aby zmniejszyć liczbę wyglądów i zwiększyć poziom tego diagramu, kliknij prawym przyciskiem myszy klasę docelową relacji, a następnie kliknij pozycję **Umieść Drzewo tutaj**. Dla efektu odwrotnego kliknij prawym przyciskiem myszy klasę docelową relacji i kliknij polecenie **Podziel drzewo**. Jeśli te polecenia menu nie są wyświetlane, upewnij się, że wybrana jest tylko Klasa domeny.

 Aby przenieść klasy domeny i klasy kształtów, użyj kombinacji klawiszy CTRL + up i CTRL + Down.

### <a name="test-the-domain-classes"></a>Testowanie klas domeny

##### <a name="to-test-the-new-domain-classes"></a>Aby przetestować nowe klasy domeny

1. **Kliknij pozycję Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL. Możesz zautomatyzować ten krok. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować transformację wszystkie szablony](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2. **Kompiluj i uruchamiaj DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie eksperymentalnym. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Otwórz Eksploratora.** Po stronie diagramu jest oknem Eksploratora języka, które jest zwykle nazywane *YourLanguage* Explorer. Jeśli to okno nie jest widoczne, może ono znajdować się na karcie poniżej Eksplorator rozwiązań. Jeśli nie można go znaleźć, w menu **Widok** wskaż polecenie **inne okna**, a następnie kliknij pozycję Eksplorator _YourLanguage_**Explorer**.

     Eksplorator przedstawia widok drzewa modelu.

4. **Utwórz nowe elementy.** Kliknij prawym przyciskiem myszy węzeł główny u góry, a następnie kliknij pozycję **Dodaj nowe**_YourClass_.

     W Eksploratorze języka zostanie wyświetlone nowe wystąpienie klasy.

5. Sprawdź, czy każde wystąpienie ma inną nazwę podczas tworzenia nowych wystąpień. Będzie to miało miejsce tylko wtedy, gdy ustawiono flagę **Nazwa elementu** na właściwości domeny.

6. **Zapoznaj się z właściwościami domeny. Po wybraniu wystąpienia klasy** sprawdź okno właściwości. Powinien on zawierać właściwości domeny zdefiniowane w tej klasie domeny.

7. **Zapisz plik, zamknij go, a następnie otwórz go ponownie**. Wszystkie utworzone wystąpienia powinny być widoczne w Eksploratorze po rozszerzeniu węzłów.

## <a name="defining-shapes-on-the-diagram"></a><a name="shapes"></a> Definiowanie kształtów na diagramie
 Możesz definiować klasy elementów, które są wyświetlane na diagramie jako prostokąty, wielokropek lub ikony.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Aby zdefiniować klasę elementów, które są wyświetlane jako kształty na diagramie

1. **Zdefiniuj i przetestuj klasę domeny zgodnie z opisem w**temacie[Definiowanie klas domeny](#classes) **.**  

   - Elementem nadrzędnym klasy powinna być Klasa główna. Oznacza to, że powinna istnieć relacja osadzania między klasą główną i nową klasą domeny.

   - Jeśli diagram ma tory, obiekt nadrzędny może być klasą domeny, która jest mapowana na tor. Przed kontynuowaniem tej procedury zapoznaj się z tematem [Definiowanie DSL, które ma tory](#swimlanes).

2. **Dodaj klasę Shape** do reprezentowania elementów na diagramie modelu. Przeciągnij z jednego z następujących narzędzi na diagram definicji DSL:

   - **Kształt geometrii** zawiera prostokąt lub elipsę.

   - **Kształt obrazu** zawiera obraz, który jest udostępniany.

   - **Kształt przedziału** jest prostokątem zawierającym co najmniej jedną listę elementów.

     Zmień nazwę klasy Shape, która zostanie wyświetlona po prawej stronie diagramu definicji DSL, w obszarze kształty i łączniki.

3. **Zdefiniuj obraz, jeśli został utworzony kształt obrazu**.

   1. Utwórz plik obrazu o dowolnym rozmiarze. Formaty BMP, JPEG, GIF i EMF są obsługiwane.

   2. W Eksplorator rozwiązań Dodaj plik do rozwiązania w obszarze Dsl\Resources.

   3. Wróć do diagramu definicji DSL i wybierz nową klasę kształtu obrazu.

   4. W okno Właściwości kliknij właściwość **obraz** .

   5. W oknie dialogowym **Wybierz obraz** kliknij menu rozwijane w polu **Nazwa pliku**, a następnie wybierz obraz.

4. **Dodaj dekoratory tekstu do kształtu, aby wyświetlić właściwości domeny.**

    Aby wyświetlić nazwę lub tytuł elementu modelu, prawdopodobnie potrzebny będzie co najmniej jeden tekst dekoratora.

    Kliknij prawym przyciskiem myszy nagłówek klasy Shape, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Text dekoratora**. Ustaw nazwę dekoratora, a w okno Właściwości ustaw jej **pozycję**.

5. **Połącz każdy kształt z mapą elementu diagramu z klasą domeny, która powinna zostać wyświetlona**.

    Kliknij narzędzie **Mapa elementu diagramu** , a następnie kliknij klasę domena, a następnie kliknij klasę Shape.

6. **Mapuj właściwości do tekstu dekoratory.**

   1. Wybierz szary wiersz między klasą domeny a klasą Shape, która reprezentuje mapę elementu diagramu.

   2. W oknie **Szczegóły DSL** kliknij kartę **mapy dekoratora** . Jeśli nie widzisz okna **Szczegóły DSL** , w menu **Widok** wskaż polecenie **inne okna** , a następnie kliknij pozycję **Szczegóły DSL**. Często konieczne jest podwyższenie poziomu tego okna, aby zobaczyć całą jego zawartość.

   3. Wybierz nazwę dekoratora. W obszarze **Właściwość wyświetlania**wybierz nazwę właściwości klasy domeny. Powtórz tę czynność dla każdego dekoratorau.

       Jeśli chcesz wyświetlić właściwość powiązanego elementu, kliknij Nawigator drzewa listy rozwijanej w obszarze **ścieżka do właściwości wyświetlania**.

   4. Upewnij się, że obok każdej nazwy dekoratora pojawia się znacznik wyboru.

      ![Mapowanie kształtów i okno szczegółów języka DSL](../modeling/media/dsldetailswindow.png "DslDetailsWindow")

7. **Utwórz element przybornika do tworzenia elementów klasy domeny.**

   1. W **Eksploratorze DSL**rozwiń węzeł **Edytor** i wszystkie jego węzły podrzędne.

   2. Kliknij prawym przyciskiem myszy węzeł w obszarze **karty przybornik** , który ma taką samą nazwę jak linia DSL, na przykład MusicLibrary. Kliknij **narzędzie Dodawanie elementu**.

       > [!NOTE]
       > Jeśli klikniesz prawym przyciskiem myszy węzeł **Narzędzia** , nie zobaczysz **narzędzia Dodawanie elementu**. Zamiast tego kliknij węzeł powyżej.

   3. W okno Właściwości z wybranym narzędziem nowego elementu Ustaw **klasę** na klasę domeny, która została ostatnio dodana.

   4. Ustawianie **podpisu** i **etykietki narzędzia**.

   5. Ustaw **ikonę przybornika** na ikonę, która będzie wyświetlana w przyborniku. Można ustawić nową ikonę lub ikonę, która jest już używana przez inne narzędzie.

        Aby utworzyć nową ikonę, Otwórz Dsl\Resources w **Eksplorator rozwiązań**. Skopiuj i wklej jeden z istniejących plików narzędzia elementu. Zmień nazwę wklejonej kopii, a następnie kliknij ją dwukrotnie, aby ją edytować.

        Wróć do diagramu definicji DSL, wybierz narzędzie, a następnie w okno właściwości kliknij **[...]** w **ikonie przybornika**. W oknie dialogowym **Wybierz mapę bitową** wybierz swoje. Plik BMP z menu rozwijanego.

   Aby uzyskać więcej informacji, zobacz [Właściwości kształtów geometrycznych](../modeling/properties-of-geometry-shapes.md) i [Właściwości kształtów obrazu](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Aby przetestować kształty

1. **Kliknij pozycję Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL.

2. **Kompiluj i uruchamiaj DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie eksperymentalnym. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Sprawdź, czy narzędzia elementów są widoczne w przyborniku.**

4. **Utwórz kształty** przeciągając je z narzędzia na diagram modelu.

5. **Sprawdź, czy każdy tekst dekoratora pojawia się** i że:

   1. Możesz ją edytować, chyba że ustawisz flagę **tylko odczyt interfejsu użytkownika** dla właściwości domeny.

   2. Gdy edytujesz właściwość w okno Właściwości lub w dekoratora, drugi widok zostanie zaktualizowany.

   Po pierwszym przetestowaniu kształtu warto dostosować jego właściwości i dodać bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-reference-relationships"></a><a name="references"></a> Definiowanie relacji odwołania
 Istnieje możliwość zdefiniowania relacji odwołania między dowolnymi klasami domeny źródłowej i dowolnymi klasami domeny docelowej. Relacje odwołań są zwykle wyświetlane na diagramie jako łączniki, które są liniami między kształtami.

 Na przykład jeśli Albumy muzyczne i artyści są wyświetlane jako kształty na diagramie, można zdefiniować relację o nazwie ArtistsAppearedOnAlbums, która łączy artystów z albumami, na których pracują. Zobacz przykład na rysunku.

 ![Model wystąpienia wygenerowanego DSL](../modeling/media/music-instance.png "Music_Instance")

 Relacje odwołań mogą również łączyć elementy tego samego typu. Na przykład w DSL reprezentujące drzewo rodziny relacja między elementami nadrzędnymi i ich elementami podrzędnymi jest relacją odwołania od osoby do osoby.

### <a name="define-a-reference-relationship"></a>Definiowanie relacji odwołania
 Kliknij narzędzie relacja odwołania, a następnie kliknij klasę źródłową domeny relacji, a następnie kliknij klasę docelową domeny. Klasa docelowa może być taka sama jak Klasa źródłowa.

 Każda relacja ma dwie role reprezentowane przez wiersz po każdej stronie pola relacji. Można wybrać każdą rolę i ustawić jej właściwości w okno Właściwości.

 **Rozważ zmianę nazwy ról**. Na przykład w relacji między osobą i osobą można zmienić nazwy domyślne na nadrzędne i podrzędne, kierownika i podwładnych, nauczycieli i uczniów itd.

 **Dostosuj liczebność poszczególnych ról**, jeśli jest to konieczne. Jeśli chcesz, aby każda osoba miała co najwyżej jednego menedżera, ustaw liczebność, która pojawia się poniżej etykiety kierownika na diagramie, na 0.. 1.

 **Dodaj właściwości domeny do relacji.** Na rysunku relacja wykonawcy dla albumu ma właściwość role.

 **Ustaw właściwość Zezwalaj na duplikaty relacji,** Jeśli istnieje więcej niż jedno łącze tej samej klasy między tą samą parą elementów modelu. Na przykład możesz umożliwić nauczycielowi naukę więcej niż jednego podmiotu w tym samym uczniu.

 ![Mapowanie kształtów dla łączników](../modeling/media/music-connector.png "Music_Connector")

 Aby uzyskać więcej informacji, zobacz [właściwości relacji domeny](../modeling/properties-of-domain-relationships.md) i [Właściwości ról domeny](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Zdefiniuj łącznik, aby wyświetlić relację
 Łącznik wyświetla linię między dwoma kształtami na diagramie modelu.

 Przeciągnij narzędzie **Łącznik** na diagram definicji DSL.

 Dodaj tekst dekoratory, jeśli chcesz wyświetlić etykiety na łączniku. Ustaw ich pozycje. Aby pozwolić użytkownikowi na przeniesienie tekstu dekoratora, ustaw jego **ruchomą** właściwość.

 Użyj narzędzia **Mapa elementu diagramu** , aby połączyć łącznik z relacją odwołania.

 Po wybraniu mapy elementu diagramu Otwórz okno **Szczegóły DSL** i Otwórz kartę **mapy dekoratora** .

 Zaznacz każdy **dekoratora** i ustaw **Właściwość Display** na poprawną właściwość domeny.

 Upewnij się, że obok każdego elementu na liście **dekoratory** pojawia się znacznik wyboru.

### <a name="define-a-connection-builder-tool"></a>Definiowanie narzędzia do tworzenia połączeń
 W oknie **Eksplorator DSL** rozwiń węzeł **Edytor** i wszystkie jego węzły podrzędne.

 Kliknij prawym przyciskiem myszy węzeł, który ma taką samą nazwę jak DSL, a następnie kliknij polecenie **Dodaj nowe połączenie**.

 Gdy wybrane jest nowe narzędzie, w okno Właściwości:

- Ustaw **podpis** i **etykietkę narzędzia**.

- Kliknij pozycję **Konstruktor połączeń** i wybierz odpowiedni Konstruktor dla nowej relacji.

- Ustaw **ikonę przybornika** na ikonę, która ma być wyświetlana w przyborniku. Można ustawić nową ikonę lub ikonę, która jest już używana przez inne narzędzie.

     Aby utworzyć nową ikonę, Otwórz Dsl\Resources w **Eksplorator rozwiązań**. Skopiuj i wklej jeden z istniejących plików narzędzia elementu. Zmień nazwę wklejonej kopii, a następnie kliknij ją dwukrotnie, aby ją edytować.

     Wróć do diagramu definicji DSL, wybierz narzędzie, a następnie w okno właściwości kliknij **[...]** w **ikonie przybornika**. W oknie dialogowym **Wybierz mapę bitową** wybierz swoje. Plik BMP z menu rozwijanego.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Aby przetestować relację odwołania i łącznik

1. **Kliknij pozycję Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL.

2. **Kompiluj i uruchamiaj DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie eksperymentalnym. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Sprawdź, czy narzędzie połączenia jest wyświetlane w przyborniku.**

4. **Utwórz kształty** przeciągając je z narzędzia na diagram modelu.

5. **Utwórz połączenia** między kształtami. Kliknij narzędzie łącznik, kliknij kształt, a następnie kliknij inny kształt.

6. **Sprawdź, czy nie można utworzyć połączeń między niewłaściwymi klasami.** Na przykład jeśli relacja jest między albumami i Artystówami, sprawdź, czy nie możesz połączyć artystów z artyści.

7. **Sprawdź, czy liczebność są poprawne. Na przykład sprawdź, czy nie można połączyć osoby z więcej niż jednym menedżerem.**

8. **Sprawdź, czy każdy tekst dekoratora pojawia się** i że:

   1. Możesz ją edytować, chyba że ustawisz flagę **tylko odczyt interfejsu użytkownika** dla właściwości domeny.

   2. Gdy edytujesz właściwość w okno Właściwości lub w dekoratora, drugi widok zostanie zaktualizowany.

   Po pierwszym przetestowaniu łącznika warto dostosować jego właściwości i dodać bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="defining-shapes-that-contain-lists-compartment-shapes"></a><a name="compartments"></a> Definiowanie kształtów zawierających listy: kształty przedziału
 Kształt przedziału zawiera co najmniej jedną listę elementów. Na przykład w bibliotece Muzyka DSL można użyć kształtów przedziału do reprezentowania albumów muzycznych. W każdym albumie znajduje się lista utworów muzycznych.

 ![Kształt przedziału](../modeling/media/compartmentshape.png "Element CompartmentShape")

 W najprostszym metodzie osiągnięcia tego efektu w definicji DSL należy zdefiniować jedną klasę domeny dla kontenera i jedną klasę domeny dla każdej z nich. Klasa kontenera jest zamapowana na kształt przedziału.

 ![Mapa kształtów](../modeling/media/music-mapcomp.png "Music_MapComp")

 Aby uzyskać więcej informacji, zobacz [Właściwości kształtów przedziału](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Aby zdefiniować kształt przedziału

1. **Utwórz klasę domeny kontenera**. Kliknij narzędzie **osadzanie relacji** , kliknij klasę główną modelu, a następnie kliknij pustą część DIAGRAMU definicji DSL. Spowoduje to utworzenie klasy domeny o nazwie album na przykład.

     Alternatywnie zamiast osadzania w klasie głównej, można osadzić kontener w klasie domeny, która jest mapowana na tor.

     Dodaj właściwość domeny, taką jak nazwa do klasy, i ustaw jej flagę **Nazwa elementu** na okno właściwości.

2. **Utwórz klasę elementu listy**. Kliknij narzędzie **osadzanie relacji** , kliknij klasę kontenera (album), a następnie kliknij pustą część diagramu. Spowoduje to utworzenie klasy domeny o nazwie Song na przykład.

     Dodaj właściwość domeny, taką jak tytuł do klasy, i ustaw jej flagę **Nazwa elementu** .

     Dodaj inne właściwości domeny.

     Dodaj inną klasę elementów listy dla każdej listy, która ma być wyświetlana.

3. **Aby mieszać kilka typów elementów na liście**, Utwórz klasy dziedziczące z klasy list. Ustaw klasę listy jako abstrakcyjną, ustawiając jej **modyfikator dziedziczenia**.

     Na przykład jeśli chcesz, aby muzyka klasyczna była posortowana przez układacz zamiast wykonawcy, możesz utworzyć dwie podklasy utworu Song, ClassicalSong i NonClassicalSong.

4. **Utwórz kształt przedziału**. Przeciągnij z narzędzia **kształt przedziału** na diagram definicji DSL.

     Dodaj dekoratora tekstu i ustaw jego nazwę.

     Dodaj przedział i ustaw jego nazwę.

5. Aby pozwolić użytkownikowi na ukrycie przedziałów listy, kliknij prawym przyciskiem myszy klasę kształt przedziału, wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Rozwiń/Zwiń dekoratora**. W okno Właściwości ustaw pozycję dekoratora.

6. Kliknij narzędzie **Mapa elementu diagramu** , kliknij klasę domena kontenera, a następnie kliknij kształt Przedział.

7. Wybierz łącze mapowanie elementu diagramu między klasą domeny a kształtem. W oknie **Szczegóły DSL** :

    1. Kliknij kartę **dekoratory** . Kliknij nazwę dekoratora, a następnie wybierz odpowiedni element w obszarze **Właściwość wyświetlania**. Upewnij się, że obok nazwy dekoratora znajduje się znacznik wyboru.

    2. Kliknij kartę **mapy przedziałów** .

         Kliknij nazwę przedziału.

         W obszarze **wyświetlana ścieżka kolekcji elementów**przejdź do klasy elementu listy (utwór). Kliknij strzałkę listy rozwijanej, aby użyć narzędzia Nawigator.

         W obszarze **Właściwość wyświetlania**wybierz właściwość, która ma zostać wyświetlona na liście. W tym przykładzie jest to tytuł.

> [!NOTE]
> Za pomocą pól ścieżki w polach mapy dekoratora i przedziału można utworzyć bardziej złożone relacje między klasami domeny i kształtem przedziału.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Aby zdefiniować narzędzie do tworzenia kształtu

1. **Utwórz element przybornika do tworzenia elementów klasy domeny.**

2. W **Eksploratorze DSL**rozwiń węzeł **Edytor** i wszystkie jego węzły podrzędne.

3. Kliknij prawym przyciskiem myszy węzeł w obszarze **karty przybornik** , który ma taką samą nazwę jak linia DSL, na przykład MusicLibrary. Kliknij **narzędzie Dodawanie elementu**.

    > [!NOTE]
    > Jeśli klikniesz prawym przyciskiem myszy węzeł **Narzędzia** , nie zobaczysz **narzędzia Dodawanie elementu**. Zamiast tego kliknij węzeł powyżej.

4. W okno Właściwości z wybranym narzędziem nowego elementu Ustaw **klasę** na klasę domeny, która została ostatnio dodana.

5. Ustawianie **podpisu** i **etykietki narzędzia**.

6. Ustaw **ikonę przybornika** na ikonę, która będzie wyświetlana w przyborniku. Można ustawić nową ikonę lub ikonę, która jest już używana przez inne narzędzie.

     Aby utworzyć nową ikonę, Otwórz Dsl\Resources w **Eksplorator rozwiązań**. Skopiuj i wklej jedno z istniejących narzędzi elementów. Pliki BMP. Zmień nazwę wklejonej kopii, a następnie kliknij ją dwukrotnie, aby ją edytować.

     Wróć do diagramu definicji DSL, wybierz narzędzie, a następnie w okno właściwości kliknij **[...]** w **ikonie przybornika**. W oknie dialogowym **Wybierz mapę bitową** wybierz plik BMP z menu rozwijanego.

#### <a name="to-test-a-compartment-shape"></a>Aby przetestować kształt przedziału

1. **Kliknij pozycję Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań, aby wygenerować kod projektanta DSL.

2. **Kompiluj i uruchamiaj DSL.** Naciśnij klawisz F5 lub CTRL + F5, aby uruchomić nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w trybie eksperymentalnym. W eksperymentalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Otwórz lub Utwórz plik, który ma rozszerzenie nazwy pliku DSL.

3. **Sprawdź, czy narzędzie jest wyświetlane w przyborniku.**

4. Przeciągnij narzędzie na diagram modelu. Kształt zostanie utworzony.

    Sprawdź, czy nazwa elementu pojawia się i jest automatycznie ustawiana na wartość domyślną.

5. Kliknij prawym przyciskiem myszy nagłówek nowego kształtu, a następnie kliknij pozycję Dodaj *element listy.* W przykładzie polecenie dodaje utwór.

    Sprawdź, czy element pojawia się na liście i czy ma nową nazwę.

6. Kliknij jeden z elementów listy, a następnie Przeanalizuj okno Właściwości. Powinny pojawić się właściwości elementów listy.

7. Otwórz Eksploratora języka. Sprawdź, czy węzły kontenera znajdują się w węzłach elementów listy.

   ![Wygenerowany Eksplorator DSL](../modeling/media/music-explorer.png "Music_Explorer")

   Po pierwszym przetestowaniu kształtu przedziału warto dostosować niektóre jego właściwości i dodać bardziej zaawansowane funkcje. Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Wyświetlanie linku odwołania w przedziale
 Zwykle element, który jest wyświetlany w przedziale, jest elementem podrzędnym elementu, który jest reprezentowany przez kształt przedziału. Ale czasami chcesz wyświetlić element, który jest połączony z nim z relacją odwołania.

 Na przykład można dodać drugi przedział do AlbumShape, który wyświetla listę artystów, które są połączone z albumem.

 W takim przypadku przedział powinien wyświetlić link zamiast elementu, do którego się odwołuje. Jest to spowodowane tym, że gdy użytkownik wybierze element w przedziale i naciśnie klawisz DELETE, chcesz usunąć łącze, a nie element, do którego się odwołuje.

 Niemniej jednak w przedziale może znajdować się nazwa elementu, do którego istnieje odwołanie.

 W poniższej procedurze przyjęto założenie, że została już utworzona klasa domeny, relacja odwołania, kształt przedziału i mapa elementów diagramu, jak opisano wcześniej w tej sekcji.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Aby wyświetlić łącze odwołania w przedziale

1. **Dodaj przedział do kształtu przedziału**. Na diagramie definicji DSL kliknij prawym przyciskiem myszy klasę kształt przedziału, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **przedział**.

2. Ustaw **ścieżkę kolekcji wyświetlanych elementów** , aby przejść do linku zamiast jego elementu docelowego. Kliknij menu rozwijane i użyj widoku drzewa, aby wybrać relację odwołania, a nie jej obiekt docelowy. W tym przykładzie relacja to **ArtistAppearedOnAlbums**.

3. Ustaw **Właściwość Path na Display** , aby przejść z linku do elementu docelowego. W tym przykładzie jest to **wykonawca**.

4. Ustaw **Właściwość Display** na odpowiednią właściwość elementu docelowego, na przykład **name**.

5. **Przekształć wszystkie szablony**, Kompiluj i uruchamiaj DSL, a następnie otwórz model testowy.

6. Na diagramie modelu Utwórz odpowiednie klasy kształtu, ustaw ich nazwy i Utwórz łącze między nimi. W kształcie przedziału powinny zostać wyświetlone nazwy połączonych elementów.

7. Wybierz link lub element w kształcie przedziału. Zarówno łącze, jak i element powinny zniknąć.

## <a name="defining-ports-on-the-boundary-of-another-shape"></a><a name="ports"></a> Definiowanie portów na granicy innego kształtu
 Port jest kształtem znajdującym się na granicy innego kształtu.

 Portów można także użyć w celu zapewnienia stałego punktu połączenia w innym kształcie, do którego użytkownik może rysować łączniki. W takim przypadku można sprawić, aby kształt portu był przezroczysty.

 Aby zobaczyć przykład, który korzysta z portów, wybierz szablon **diagramu składników** podczas tworzenia nowego rozwiązania DSL. W tym przykładzie przedstawiono główne punkty, które można wziąć pod uwagę podczas definiowania portów:

- Istnieje Klasa domeny, która reprezentuje kontener portów `Component` .

- Istnieje Klasa domeny, która reprezentuje porty. w tym przykładzie jest to `ComponentPort`.

- Istnieje relacja osadzania z klasy kontenera domeny do klasy domeny portu. Aby uzyskać więcej informacji, zobacz [Definiowanie klas domen](#classes).

- Jeśli chcesz, aby różne typy portów były mieszane w tym samym kontenerze, możesz utworzyć podklasy klasy port. W przykładzie `InPort` i `OutPort` Dziedzicz z `ComponentPort` .

- Klasę domeny kontenera można zamapować na dowolny rodzaj kształtu. W tym przykładzie jest to `ComponentShape` . Aby uzyskać więcej informacji, zobacz [Definiowanie kształtów](#shapes).

- Klasy domeny portów są mapowane na kształty portów. Można zmapować klasy pochodne na oddzielne klasy kształtu portu lub zmapować klasę bazową na jedną klasę kształtu portu.

  W innych aspektach kształty portów działają zgodnie z opisem w temacie [Definiowanie kształtów](#shapes).

  Aby uzyskać więcej informacji, zobacz [Właściwości kształtów portów](../modeling/properties-of-port-shapes.md).

## <a name="defining-a-dsl-that-has-swimlanes"></a><a name="swimlanes"></a> Definiowanie DSL z Tormi
 Tory to pozioma lub pionowa partycja diagramu. Każdy tor odpowiada elementowi modelu. Definicja DSL wymaga jednej klasy domeny dla elementów toru.

 Najlepszym sposobem utworzenia DSL z tormi jest utworzenie nowego rozwiązania DSL i wybranie szablonu rozwiązania przepływu zadań. W definicji DSL Klasa aktora jest klasą domeny zamapowana do toru. Zmień nazwę tej i innych klas, aby dopasować je do projektu.

 Aby dodać klasę, która będzie wyświetlana jako kształt wewnątrz toru, Utwórz relację osadzania między klasą toru i nową klasą. Użytkownicy będą mogli przeciągać elementy z jednego toru do drugiego, ale każdy element będzie zawsze znajdować się w określonym toru. W szablonie rozwiązania przepływu zadań FlowElement jest elementem podrzędnym klasy toru.

 Aby dodać klasę, która będzie wyświetlana jako kształt niezależnie od torów, Utwórz relację osadzania między klasą główną i nową klasą. Użytkownicy będą mogli umieścić te kształty w dowolnym miejscu na diagramie, w tym między granicami torów i poza nimi. W szablonie rozwiązania przepływu zadań komentarz jest elementem podrzędnym klasy głównej.

 Aby uzyskać więcej informacji, zobacz [Właściwości torów](../modeling/properties-of-swimlanes.md).

## <a name="adding-property-types"></a><a name="addTypes"></a> Dodawanie typów właściwości

### <a name="domain-enumerations-and-literals"></a>Wyliczenia domen i literały
 Wyliczenie domen jest typem z kilkoma wartościami literału.

 Aby dodać Wyliczenie domen, kliknij prawym przyciskiem myszy katalog główny modelu w **Eksploratorze DSL** , a następnie kliknij polecenie **Dodaj nowe Wyliczenie domeny**. Element pojawi się w **Eksploratorze DSL** w węźle **typy domeny** . Ten element nie jest wyświetlany na diagramie.

 Aby dodać literały wyliczenia do wyliczenia domen, kliknij prawym przyciskiem myszy Wyliczenie domeny w **Eksploratorze DSL** , a następnie kliknij polecenie **Dodaj nowy literał wyliczenia**.

 Domyślnie właściwość, która ma typ wyliczeniowy, można ustawić tylko dla jednej wartości wyliczenia jednocześnie. Jeśli chcesz, aby użytkownicy i programiści mogli ustawić dowolną kombinację wartości-"pole bitowe" — Ustaw właściwość **IsFlags** wyliczenia.

### <a name="external-types"></a>Typy zewnętrzne
 Po ustawieniu typu właściwości domeny, jeśli nie znajdziesz żądanego typu na liście rozwijanej **Typ** , można dodać typ zewnętrzny. Na przykład można dodać typ **System. Drawing. Color** do listy.

 Aby dodać typ, kliknij prawym przyciskiem myszy element główny modelu w Eksploratorze DSL, a następnie kliknij polecenie **Dodaj nowy typ zewnętrzny**. W okno Właściwości ustaw wartość w polu Nazwa na **kolor** i przestrzeń nazw na **System. Drawing**. Ten typ jest teraz wyświetlany w Eksploratorze DSL w obszarze **typy domen**. Możesz wybrać tę opcję, gdy ustawisz typ właściwości domeny.

## <a name="customizing-the-dsl"></a><a name="custom"></a> Dostosowywanie DSL
 Korzystając z technik opisanych w tym temacie, można szybko utworzyć DSL z notacją diagramowy, czytelną postać XML i podstawowych narzędzi, które są wymagane do generowania kodu i innych artefaktów.

 Istnieją dwie metody rozszerzania definicji DSL:

1. Dostosuj DSL przy użyciu większej liczby funkcji definicji DSL. Można na przykład utworzyć narzędzie jednego łącznika, które może tworzyć kilka typów łączników, i kontrolować reguły, za pomocą których usunięcie jednego elementu powoduje także usunięcie powiązanych elementów. Te techniki są najczęściej osiągane przez ustawienie wartości w definicji DSL, a niektóre wymagają kilku wierszy kodu programu.

     Aby uzyskać więcej informacji, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

2. Rozszerzając narzędzia modelowania przy użyciu kodu programu, aby osiągnąć bardziej zaawansowane efekty. Można na przykład utworzyć polecenia menu, które mogą zmienić model, i można utworzyć narzędzia, które integrują dwa lub więcej językami DSL. VMSDK został zaprojektowany specjalnie w celu ułatwienia integracji rozszerzeń z kodem, który jest generowany na podstawie definicji DSL.  Aby uzyskać więcej informacji, zobacz [pisanie kodu w celu dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Zmiana definicji DSL
 Podczas tworzenia dowolnego elementu w definicji DSL wiele wartości domyślnych jest ustawianych automatycznie. Po ich ustawieniu można je zmienić. Upraszcza to programowanie DSL, a jednocześnie pozwala na zaawansowane dostosowania.

 Na przykład podczas mapowania kształtu do elementu ścieżka elementu nadrzędnego mapowania jest automatycznie ustawiana według relacji osadzania klasy domeny. Jednak w przypadku późniejszej zmiany relacji osadzania ścieżka elementu nadrzędnego nie zostanie zmieniona automatycznie.

 Należy pamiętać, że w przypadku zmiany niektórych relacji w definicji DSL nie jest to nietypowe w przypadku błędów zgłaszanych podczas zapisywania definicji lub podczas przekształcania wszystkich szablonów. Większość z tych błędów jest łatwa do naprawienia. Kliknij dwukrotnie raport o błędach, aby zobaczyć lokalizację błędu.

 Zobacz również [: zmienianie przestrzeni nazw języka specyficznego dla domeny](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="troubleshooting"></a><a name="trouble"></a> Rozwiązywanie problemów z
 W poniższej tabeli wymieniono najbardziej typowe problemy, które można napotkać podczas projektowania DSL, wraz z sugestiami dotyczącymi rozwiązania. Więcej porad można znaleźć na [forum narzędzi wizualizacji Extensibililty](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

|Problem|Sugestia|
|-------------|----------------|
|Zmiany wprowadzone w pliku definicji DSL nie mają żadnego wpływu.|Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi powyżej Eksplorator rozwiązań, a następnie Skompiluj ponownie rozwiązanie.|
|Kształty zawierają nazwę dekoratora zamiast wartości właściwości.|Skonfiguruj mapowanie dekoratora. Na diagramie definicji DSL kliknij mapę elementu diagramu, która jest szarą linią między klasą domeny a klasą Shape.<br /><br /> Otwórz okno **Szczegóły DSL** . Jeśli nie widzisz go, w menu Widok wskaż polecenie **inne okna**, a następnie kliknij pozycję **Szczegóły DSL**.<br /><br /> Kliknij kartę **mapy dekoratora** . Wybierz nazwę dekoratora. Upewnij się, że pole obok niego jest zaznaczone. W obszarze **Właściwość wyświetlania**wybierz nazwę właściwości domeny.<br /><br /> Aby uzyskać więcej informacji, zobacz [kształty na diagramie](#shapes).|
|W Eksploratorze DSL nie można dodać do kolekcji. Na przykład po kliknięciu prawym przyciskiem myszy narzędzia nie ma polecenia "Dodaj narzędzie" w menu.<br /><br /> W Eksploratorze dla My DSL nie mogę dodać elementu do listy.|Kliknij prawym przyciskiem myszy element powyżej węzła, który próbujesz. Gdy chcesz dodać do listy, polecenie Dodaj nie znajduje się w węźle listy, ale w jego właścicielu.|
|Po utworzeniu klasy domeny nie można tworzyć wystąpień w Eksploratorze języka.|Każda klasa domeny z wyjątkiem elementu głównego musi być elementem docelowym relacji osadzania.|
|W Eksploratorze dla mojego języka DSL elementy są wyświetlane tylko przy użyciu ich nazw typów.|W definicji DSL wybierz właściwość domeny klasy, a w okno Właściwości ustaw wartość **Nazwa elementu** na true.|
|Mój DSL zawsze otwiera się w edytorze XML.|Może się tak zdarzyć z powodu błędu podczas odczytywania pliku. Jednak nawet po usunięciu tego błędu należy jawnie zresetować Edytor, aby był projektantem DSL.<br /><br /> Kliknij prawym przyciskiem myszy element projektu, kliknij polecenie **Otwórz za pomocą** i wybierz pozycję Projektant _YourLanguage_**(domyślnie)**.|
|Przybornik elementu DSL nie pojawia się po zmianie nazw zestawów.|**Aby uzyskać** więcej informacji, zobacz [temat jak: zmienianie przestrzeni nazw języka specyficznego dla domeny](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|Przybornik elementu DSL nie jest wyświetlany, ale nie zmieniono nazwy zestawu.<br /><br /> Lub pojawi się okno komunikatu z raportowaniem niepowodzenia załadowania rozszerzenia.|Zresetuj wystąpienie eksperymentalne i Skompiluj ponownie rozwiązanie.<br /><br /> 1. w menu Start systemu Windows w obszarze **Wszystkie programy**rozwiń pozycję [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)] **Narzędzia**, a następnie kliknij pozycję **Zresetuj Microsoft Visual Studio wystąpienie eksperymentalne**.<br />2. w menu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**.|

## <a name="see-also"></a>Zobacz też
 [Wprowadzenie za pomocą języków specyficznych dla domeny](../modeling/getting-started-with-domain-specific-languages.md) [Tworzenie języka specyficznego dla domeny opartego na Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md) [tworzeniu języka specyficznego dla domeny opartego na platformie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)
