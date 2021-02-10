---
title: Wprowadzenie do języków specyficznych dla domeny
description: Zapoznaj się z podstawowymi pojęciami dotyczącymi definiowania i używania języka specyficznego dla domeny (DSL) utworzonego przy użyciu zestawu SDK modelowania dla programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8fe531b127d657228ed68fa79358ef5df69ff17c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941492"
---
# <a name="get-started-with-domain-specific-languages"></a>Wprowadzenie do języków specyficznych dla domeny

W tym temacie objaśniono podstawowe pojęcia związane z definiowaniem i używaniem języka specyficznego dla domeny (DSL) utworzonego przy użyciu zestawu SDK modelowania dla programu Visual Studio.

> [!NOTE]
> Zestaw SDK transformacji szablonu tekstu i Visual Studio Modeling SDK są instalowane automatycznie podczas instalowania określonych funkcji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Jeśli dopiero zaczynasz korzystać z programu językami DSL, zalecamy przechodzenie przez **laboratorium narzędzi DSL**, które można znaleźć w tej witrynie: [Wizualizacja i Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Co możesz zrobić przy użyciu języka Domain-Specificowego?

Język specyficzny dla domeny jest zapisem, zwykle graficznym, który jest przeznaczony do użycia w konkretnym celu. Z kolei, języki takie jak UML są ogólnego przeznaczenia. W DSL można zdefiniować typy elementów modelu i ich relacji oraz sposób ich wyświetlania na ekranie.

Po zaprojektowaniu DSL można je rozpowszechnić w ramach pakietu rozszerzenia programu Visual Studio Integration (VSIX). Użytkownicy pracują z DSL w programie Visual Studio:

![Diagram drzewa rodzin, Przybornik i Eksplorator](../modeling/media/familyt_instance.png)

Notacja jest tylko częścią DSL. Wraz z notacją pakiet VSIX zawiera narzędzia, które użytkownicy mogą stosować, aby ułatwić im edytowanie i generowanie materiału z modeli.

Jedną z głównych aplikacji językami DSL jest generowanie kodu programu, plików konfiguracji i innych artefaktów. Szczególnie w dużych projektach i liniach produktów, w których zostanie utworzona kilka wariantów produktu, generowanie wielu zmiennych aspektów z językami DSL może zapewnić duży wzrost niezawodności i bardzo szybką odpowiedź na zmiany wymagań.

Pozostała część tego omówienia to przewodnik, w którym wprowadzono podstawowe operacje tworzenia i używania języka specyficznego dla domeny w programie Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zdefiniować DSL, należy zainstalować następujące składniki:

| Składnik | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Modeling SDK dla programu Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Tworzenie rozwiązania DSL

Aby utworzyć nowy język specyficzny dla domeny, należy utworzyć nowe rozwiązanie programu Visual Studio przy użyciu szablonu projektu Domain-Specific Language.

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W obszarze **typy projektów** rozwiń węzeł **Inne typy projektów** , a następnie kliknij pozycję **rozszerzalność**.

3. Kliknij **Projektant języka specyficznego dla domeny**.

     ![Utwórz okno dialogowe DSL](../modeling/media/create_dsldialog.png)

4. W polu **Nazwa** wpisz **FamilyTree**. Kliknij przycisk **OK**.

     Zostanie otwarty **Kreator języka specyficznego dla domeny** i zostanie wyświetlona lista rozwiązań opartych na szablonie.

     Kliknij każdy szablon, aby wyświetlić opis,

     Szablony to przydatne punkty startowe. Każdy z nich zapewnia kompletną pracę DSL, którą można edytować zgodnie z potrzebami. Zwykle należy wybrać szablon, który ma zostać utworzony.

5. Na potrzeby tego przewodnika wybierz szablon **minimalny język** .

6. Wprowadź rozszerzenie nazwy pliku dla języka DSL na odpowiedniej stronie kreatora. Jest to rozszerzenie, które będzie używać plików zawierających wystąpienia DSL.

    - Wybierz rozszerzenie, które nie jest skojarzone z żadną aplikacją na komputerze lub na dowolnym komputerze, na którym chcesz zainstalować DSL. Na przykład, **docx** i **htm** byłyby nieakceptowalnymi rozszerzeniami nazw plików.

    - Kreator wyświetli ostrzeżenie, jeśli wprowadzone rozszerzenie jest używane jako DSL. Rozważ użycie innego rozszerzenia nazwy pliku. Możesz również zresetować wystąpienie eksperymentalne zestawu Visual Studio SDK, aby wyczyścić stare eksperymentalne projektanci. Kliknij przycisk **Start**, kliknij pozycję **wszystkie programy**, **Microsoft Visual Studio zestaw SDK 2010**, **Narzędzia**, a następnie **Zresetuj wystąpienie eksperymentalne Microsoft Visual Studio 2010**.

7. Sprawdź inne strony, a następnie kliknij przycisk **Zakończ**.

     Generowane jest rozwiązanie, które zawiera dwa projekty. Są one nazywane DSL i DslPackage. Zostanie otwarty plik diagramu o nazwie DslDefinition. DSL.

    > [!NOTE]
    > Większość kodu, który można wyświetlić w folderach w dwóch projektach, jest generowana z DslDefinition. DSL. Z tego powodu większość modyfikacji DSL została wprowadzona w tym pliku.

Interfejs użytkownika jest teraz podobny do poniższego obrazu.

![Projektant DSL](../modeling/media/dsl_designer.png)

To rozwiązanie definiuje język specyficzny dla domeny. Aby uzyskać więcej informacji, zobacz [Omówienie interfejsu użytkownika narzędzi języka Domain-Specific](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Ważne części rozwiązania DSL

Zwróć uwagę na następujące aspekty nowego rozwiązania:

- **Dsl\DslDefinition.DSL** Jest to plik, który jest wyświetlany podczas tworzenia rozwiązania DSL. Prawie cały kod w rozwiązaniu jest generowany na podstawie tego pliku, a większość zmian wprowadzonych w definicji DSL jest wprowadzana tutaj. Aby uzyskać więcej informacji, zobacz Praca z [pracą z diagramem definicji DSL](../modeling/working-with-the-dsl-definition-diagram.md).

- **Projekt DSL** Ten projekt zawiera kod, który definiuje język specyficzny dla domeny.

- **Projekt DslPackage** Ten projekt zawiera kod umożliwiający otwieranie i edytowanie wystąpień DSL w programie Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Uruchamianie modemu DSL

Rozwiązanie DSL można uruchomić zaraz po jego utworzeniu. Później można zmienić definicję DSL, uruchamiając rozwiązanie ponownie po każdej zmianie.

### <a name="to-experiment-with-the-dsl"></a>Aby eksperymentować z DSL

1. Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi **Eksplorator rozwiązań** . Spowoduje to ponowne wygenerowanie większości kodu źródłowego z DslDefinition. DSL.

    > [!NOTE]
    > Po zmianie *DslDefinition. DSL* należy kliknąć pozycję **Przekształć wszystkie szablony** przed odbudowaniem rozwiązania. Możesz zautomatyzować ten krok. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować transformację wszystkie szablony](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. Naciśnij klawisz **F5** lub w menu **debugowanie** kliknij **Rozpocznij debugowanie**.

     Kompilacja DSL jest instalowana w eksperymentalnym wystąpieniu programu Visual Studio.

     Zostanie uruchomione eksperymentalne wystąpienie programu Visual Studio. Eksperymentalne wystąpienie przyjmuje swoje ustawienia z oddzielnego poddrzewa rejestru, gdzie rozszerzenia programu Visual Studio są zarejestrowane do celów debugowania. Normalne wystąpienia programu Visual Studio nie mają dostępu do rozszerzeń zarejestrowanych w tym miejscu.

3. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz plik modelu o nazwie **test** z **Eksplorator rozwiązań**.

     \- oraz

     Kliknij prawym przyciskiem myszy projekt debugowanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **element**. W oknie dialogowym **Dodaj element** wybierz typ pliku DSL.

     Plik modelu zostanie otwarty jako pusty diagram.

     Przybornik otwiera i wyświetla narzędzia odpowiednie dla danego typu diagramu.

4. Użyj narzędzi do tworzenia kształtów i łączników na diagramie.

    1. Aby utworzyć kształty, przeciągnij z przykładu narzędzie Kształt na diagram.

    2. Aby połączyć dwa kształty, kliknij narzędzie przykładowe łączniki, kliknij pierwszy kształt, a następnie kliknij drugi kształt.

5. Kliknij etykiety kształtów, aby je zmienić.

Eksperymentalny program Visual Studio będzie wyglądać podobnie do poniższego przykładu:

![Przykładowe drzewo języka specyficznego dla domeny w programie Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Zawartość modelu

Zawartość pliku, który jest wystąpieniem DSL, nazywa się *modelem*. Model zawiera elementy *modelu* <em></em> i *linki* między elementami. Definicja DSL określa, jakie typy elementów modelu i linków mogą znajdować się w modelu. Na przykład w przypadku użycia DSL utworzonego na podstawie szablonu minimalnego języka istnieje jeden typ elementu modelu i jeden typ łącza.

Definicja DSL pozwala określić, jak model pojawia się na diagramie. Można wybierać spośród różnych stylów kształtów i łączników. Można określić, że niektóre kształty są wyświetlane wewnątrz innych kształtów.

Model można wyświetlić jako drzewo w widoku **Eksploratora** podczas edytowania modelu. Podczas dodawania kształtów do diagramu elementy modelu są również wyświetlane w Eksploratorze. Eksploratora można używać nawet wtedy, gdy nie ma diagramu.

Jeśli nie widzisz Eksploratora w wystąpieniu debugowania programu Visual Studio, w menu **Widok** wskaż polecenie **inne okna**, a następnie kliknij pozycję *\<Your Language>* **Eksplorator**.

### <a name="the-api-of-your-dsl"></a>Interfejs API DSL

DSL generuje interfejs API, który umożliwia odczytywanie i aktualizowanie modeli, które są wystąpieniami DSL. Jedną z aplikacji interfejsu API jest generowanie plików tekstowych z modelu. Aby uzyskać więcej informacji, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

W rozwiązaniu debugowania Otwórz pliki szablonów z rozszerzeniem ". tt". W tych przykładach pokazano, jak można wygenerować tekst z modeli i umożliwić przetestowanie interfejsu API DSL. Jeden z przykładów jest Zapisano [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , drugi w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

W każdym pliku szablonu jest wygenerowany plik. Rozwiń plik szablonu w Eksplorator rozwiązań i Otwórz wygenerowany plik.

Plik szablonu zawiera krótki segment kodu, który zawiera listę wszystkich elementów w modelu.

Wygenerowany plik zawiera wynik.

Po zmianie pliku modelu zobaczysz odpowiednie zmiany w wygenerowanych plikach po ponownym wygenerowaniu plików.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Aby ponownie wygenerować pliki tekstowe po zmianie pliku modelu

1. W eksperymentalnym wystąpieniu programu Visual Studio Zapisz plik modelu.

2. Upewnij się, że parametr Nazwa pliku w każdym pliku TT odwołuje się do pliku modelu, który jest używany do eksperymentów. Zapisz plik. tt.

3. Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi **Eksplorator rozwiązań**.

     \- oraz

     Kliknij prawym przyciskiem myszy szablony, które chcesz wygenerować ponownie, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe**.

Do projektu można dodać dowolną liczbę plików szablonów tekstowych. Każdy szablon generuje jeden plik wynikowy.

> [!NOTE]
> Po zmianie definicji DSL, kod szablonu tekstu przykładowego nie będzie działał, chyba że zostanie zaktualizowany.

Aby uzyskać więcej informacji, zobacz [generowanie kodu z Domain-Specific języku](../modeling/generating-code-from-a-domain-specific-language.md) i [pisanie kodu w celu dostosowania języka Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>Dostosowywanie DSL

Jeśli chcesz zmodyfikować definicję DSL, Zamknij wystąpienie eksperymentalne i zaktualizuj definicję w głównym wystąpieniu programu Visual Studio.

> [!NOTE]
> Po zmodyfikowaniu definicji DSL można utracić informacje w modelach testów utworzonych przy użyciu wcześniejszych wersji.  Na przykład rozwiązanie debugowania zawiera plik o nazwie Sample, który zawiera niektóre kształty i łączniki. Po rozpoczęciu tworzenia definicji DSL nie będzie ona widoczna i zostanie utracona podczas zapisywania pliku.

Do DSL można utworzyć wiele różnych rozszerzeń. Poniższe przykłady dają wrażenie możliwości.

Po każdej zmianie Zapisz definicję DSL, kliknij pozycję **Przekształć wszystkie szablony** w **Eksplorator rozwiązań**, a następnie naciśnij klawisz **F5** , aby eksperymentować ze zmienionym DSL.

### <a name="rename-the-types-and-tools"></a>Zmień nazwy typów i narzędzi

Zmień nazwy istniejących klas i relacji domeny. Na przykład rozpoczynając od definicji DSL utworzonej na podstawie szablonu minimalnego języka, można wykonać następujące operacje zmiany nazwy, aby umożliwić DSL reprezentuje drzewa rodzinne.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Aby zmienić nazwy klas domen, relacji i narzędzi

1. Na diagramie DslDefinition Zmień nazwę **ExampleModel** na **FamilyTreeModel**, **example** dla **osoba**, **cele** do **rodziców** i **źródła** do **elementów podrzędnych**. Możesz kliknąć każdą etykietę, aby ją zmienić.

     ![Diagram definicji DSL &#45; Model drzewa genealogicznego](../modeling/media/familyt_person.png)

2. Zmień nazwę narzędzi elementów i łączników.

    1. Otwórz okno Eksplorator DSL, klikając kartę w obszarze Eksplorator rozwiązań. Jeśli nie widzisz go, w menu **Widok** wskaż polecenie **inne okna** , a następnie kliknij pozycję **Eksplorator DSL**. Eksplorator DSL jest widoczny tylko wtedy, gdy jest aktywnym oknem diagram definicji DSL.

    2. Otwórz okno Właściwości i umieść go tak, aby można było zobaczyć w tym samym czasie Eksploratora i właściwości DSL.

    3. W Eksploratorze DSL rozwiń węzeł **Edytor**, **karty przybornika**, *\<your DSL>* a następnie **Narzędzia**.

    4. Kliknij przycisk **example**. Jest to element przybornika, który służy do tworzenia elementów.

    5. W okno Właściwości zmień właściwość **Nazwa** na **Person**.

         Zauważ, że właściwość **Caption** również ulega zmianie.

    6. W ten sam sposób Zmień nazwę narzędzia **ExampleConnector** na **ParentLink**. Zmień właściwość **Caption** , tak aby nie była kopią właściwości Nazwa. Na przykład wprowadź **łącze nadrzędne**.

3. Skompiluj ponownie DSL.

    1. Zapisz plik definicji DSL.

    2. Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań

    3. Naciśnij F5. Zaczekaj na wyświetlenie eksperymentalnego wystąpienia programu Visual Studio.

4. W rozwiązaniu debugowania w eksperymentalnym wystąpieniu programu Visual Studio Otwórz plik modelu testowego. Przeciągnij elementy na nie z przybornika. Zauważ, że podpisy narzędzia i nazwy typów w Eksploratorze DSL zostały zmienione.

5. Zapisz plik modelu.

6. Otwórz plik. tt i Zastąp wystąpienia starych typów i nazw właściwości nowymi nazwami.

7. Upewnij się, że nazwa pliku określona w pliku TT Określa model testowy.

8. Zapisz plik. tt. Otwórz wygenerowany plik, aby zobaczyć wynik uruchamiania kodu w pliku TT. Sprawdź, czy jest ona poprawna.

### <a name="add-domain-properties-to-classes"></a>Dodawanie właściwości domeny do klas
 Dodaj właściwości do klasy domeny, na przykład, aby reprezentować lata urodzenia i zgonu osoby.

 Aby nowe właściwości były widoczne na diagramie, należy dodać *dekoratory* do kształtu, który wyświetla element modelu. Należy również zmapować właściwości na dekoratory.

##### <a name="to-add-properties-and-display-them"></a>Aby dodać właściwości i wyświetlić je

1. Dodaj właściwości.

   1. Na diagramie definicji DSL kliknij prawym przyciskiem myszy klasy **osoba** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **właściwość domeny**.

   2. Wpisz listę nowych nazw właściwości, takich jak **urodzenie** i **zgony**. Naciśnij klawisz **Enter** po każdym z nich.

2. Dodaj dekoratory, które będą wyświetlać właściwości w kształcie.

   1. Postępuj zgodnie z szarym wierszem, który rozciąga się od klasy osoby należącej do drugiej strony diagramu. To jest mapa elementu diagramu. Łączy klasy domeny z klasą Shape.

   2. Kliknij prawym przyciskiem myszy tę klasę kształtu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **tekst dekoratora**.

   3. Dodaj dwie dekoratory z nazwami, takimi jak **BirthDecorator** i **DeathDecorator**.

   4. Zaznacz wszystkie nowe dekoratora i w okno Właściwości ustaw pole **pozycja** . Określa miejsce, w którym wartość właściwości domeny będzie wyświetlana na kształcie. Na przykład ustaw **InnerBottomLeft** i **InnerBottomRight**.

        ![Definicja kształtu przedziału](../modeling/media/familyt_compartment.png)

3. Mapuj dekoratory na właściwości.

   1. Otwórz okno Szczegóły DSL. Zazwyczaj znajduje się on na karcie obok okna danych wyjściowych. Jeśli nie widzisz go, w menu **Widok** wskaż polecenie **inne okna**, a następnie kliknij pozycję **Szczegóły DSL**.

   2. Na diagramie definicji DSL kliknij wiersz, który łączy klasę **Persona** z klasą Shape.

   3. W obszarze **szczegóły języka DSL** na karcie **mapy dekoratora** kliknij pole wyboru na niezamapowanym dekoratora. W oknie **właściwości wyświetlania** wybierz właściwość domeny, do której ma zostać zamapowana. Na przykład zamapuj **BirthDecorator** na **urodzenie**.

4. Zapisz DSL, kliknij pozycję Przekształć wszystkie szablony i naciśnij klawisz F5.

5. Na przykładowym diagramie modelu Sprawdź, czy możesz teraz kliknąć wybrane pozycje i wpisać w nich wartości. Ponadto w przypadku wybrania kształtu **osoby** okno właściwości są wyświetlane nowe właściwości urodzenia i zgonu.

6. W pliku. tt można dodać kod, który uzyskuje właściwości każdej osoby.

   ![Diagram drzewa rodzin, Przybornik i Eksplorator](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definiuj nowe klasy
 Do modelu można dodawać klasy domen i relacje. Na przykład można utworzyć nową klasę reprezentującą miejscowości i nową relację, która będzie reprezentować osobę w mieście.

 Aby różne typy były odrębne dla diagramu modelu, można mapować klasy domeny na różne rodzaje kształtu lub do kształtów o różnej geometrii i kolorach.

##### <a name="to-add-and-display-a-new-domain-class"></a>Aby dodać i wyświetlić nową klasę domeny

1. Dodaj klasę domeny i Uczyń ją elementem podrzędnym modelu głównego.

    1. Na diagramie definicji DSL kliknij narzędzie **osadzanie relacji** , kliknij **FamilyTreeModel** klasy głównej, a następnie kliknij w pustej części diagramu.

         Zostanie wyświetlona nowa klasa domeny, która jest połączona z FamilyTreeModel z relacją osadzania.

         Ustaw jej nazwę, na przykład **miejscowość**.

        > [!NOTE]
        > Każda klasa domeny poza elementem głównym modelu musi być elementem docelowym co najmniej jednej relacji osadzania lub musi dziedziczyć po klasie, która jest elementem docelowym osadzania. Z tego powodu często wygodnie jest utworzyć klasy domeny za pomocą narzędzia osadzania relacji.

    2. Dodaj właściwość domeny do nowej klasy, na przykład **name**.

2. Dodaj relację odwołania między osobą i miejscowością.

    1. Kliknij narzędzie **relacja odwołania** , kliknij pozycję osoba, a następnie kliknij pozycję miejscowość.

         ![Fragment definicji DSL: katalog główny drzewa rodziny](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Relacje odwołania reprezentują odwołania krzyżowe z jednej części drzewa modelu do innej.

3. Dodaj kształt reprezentujący miast na diagramach modeli.

    1. Przeciągnij **kształt geometrii** z przybornika do diagramu i zmień jego nazwę, na przykład **TownShape**.

    2. W okno Właściwości Ustaw pola wyglądu nowego kształtu, takie jak kolor wypełnienia i geometria.

    3. Dodaj dekoratora, aby wyświetlić nazwę miejscowości, a następnie zmień jej nazwę na NameDecorator. Ustaw jej Właściwość Position.

4. Zamapuj klasę miejscowości na TownShape.

    1. Kliknij narzędzie **Mapa elementu diagramu** , a następnie kliknij klasę miasto, a następnie klasy Shape TownShape.

    2. Na karcie **mapy dekoratora** okna **Szczegóły DSL** z wybranym łącznikiem mapy zaznacz opcję NameDecorator i ustaw **Właściwość Display** na wartość Name.

5. Utwórz łącznik, aby wyświetlić relacje między osobą a miastem.

    1. Przeciągnij łącznik z przybornika do diagramu. Zmień jego nazwę i ustaw jego właściwości wyglądu.

    2. Użyj narzędzia **Mapa elementu diagramu** , aby połączyć nowy łącznik z relacją między osobą i miejscowością.

         ![Definicja drzewa rodziny z dodaną mapą kształtu](../modeling/media/familyt_shapemap.png)

6. Utwórz narzędzie elementu do tworzenia nowego miasta.

    1. W **Eksploratorze DSL** rozwiń węzeł **Edytor** , a następnie **kartę Przybornik**.

    2. Kliknij prawym przyciskiem myszy *\<your DSL>* , a następnie kliknij polecenie **Dodaj nowy element**.

    3. Ustaw właściwość **name** nowego narzędzia i ustaw jej właściwość **Class** na miejscowość.

    4. Ustaw właściwość **ikona przybornika** . Kliknij pozycję **[...]** i w polu **Nazwa pliku** wybierz plik ikony.

7. Utwórz narzędzie łącznika do tworzenia linku między miastami i osobami.

    1. Kliknij prawym przyciskiem myszy *\<your DSL>* , a następnie kliknij polecenie **Dodaj nowe łączniki**.

    2. Ustaw właściwość Name nowego narzędzia.

    3. We właściwości **elemencie ConnectionBuilder** wybierz konstruktora, który zawiera nazwę relacji Person-Town.

    4. Ustaw **ikonę przybornika**.

8. Zapisz definicję DSL, kliknij pozycję **Przekształć wszystkie szablony**, a następnie naciśnij klawisz **F5**.

9. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz plik modelu testowego. Użyj nowych narzędzi do tworzenia miast i linków między miastami i osobami. Należy zauważyć, że można tworzyć tylko linki między prawidłowymi typami elementu.

10. Utwórz kod, który wyświetla miasto, w którym mieszka każda osoba. Szablony tekstowe są jednym z miejsc, w których można uruchomić ten kod. Na przykład można zmodyfikować istniejący plik Sample.tt w rozwiązaniu debugowania, aby zawierał następujący kod:

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     Po zapisaniu pliku *. tt zostanie utworzony plik pomocniczy zawierający listę osób i ich Residences. Aby uzyskać więcej informacji, zobacz [generowanie kodu z poziomu Domain-Specific języka](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Walidacja i polecenia
 Możesz również opracować ten DSL, dodając ograniczenia walidacji. Te ograniczenia to metody, które można zdefiniować, aby upewnić się, że model jest w poprawnym stanie. Na przykład można zdefiniować ograniczenie, aby upewnić się, że data urodzenia elementu podrzędnego jest późniejsza niż jego nadrzędna. Funkcja walidacji wyświetla ostrzeżenie, jeśli użytkownik DSL próbuje zapisać model, który przerywa dowolne ograniczenia. Aby uzyskać więcej informacji, zobacz [Walidacja w języku Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

 Można także definiować polecenia menu, które użytkownik może wywołać. Polecenia mogą modyfikować model. Mogą również korzystać z innych modeli w programie Visual Studio i z zasobami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [How to: Modify a standardowe polecenie menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Wdrażanie DSL
 Aby umożliwić innym użytkownikom korzystanie z języka specyficznego dla domeny, należy rozpowszechnić plik rozszerzenia programu Visual Studio (VSIX). Ta wartość jest tworzona podczas tworzenia rozwiązania DSL.

 Zlokalizuj plik VSIX w folderze bin Twojego rozwiązania. Skopiuj go do komputera, na którym chcesz go zainstalować. Na tym komputerze kliknij dwukrotnie plik VSIX. DSL można używać we wszystkich wystąpieniach programu Visual Studio na tym komputerze.

 Możesz użyć tej samej procedury, aby zainstalować DSL na własnym komputerze, aby nie trzeba było korzystać z eksperymentalnego wystąpienia programu Visual Studio.

 Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych Domain-Specific](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Usuwanie starej eksperymentalnej językami DSL
 Jeśli utworzono eksperymentalne językami DSL, które nie są już potrzebne, możesz je usunąć z komputera przez zresetowanie wystąpienia eksperymentalnego programu Visual Studio.

 Spowoduje to usunięcie z komputera wszystkich eksperymentalnych językami DSL i innych eksperymentalnych rozszerzeń programu Visual Studio. Są to rozszerzenia, które zostały wykonane w trybie debugowania.

 Ta procedura nie usuwa językami DSL ani innych rozszerzeń programu Visual Studio, które zostały w pełni zainstalowane, wykonując plik VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Aby zresetować wystąpienie eksperymentalne programu Visual Studio

1. Kliknij przycisk **Start**, kliknij pozycję **wszystkie programy**, **Microsoft Visual Studio zestaw SDK 2010**, **Narzędzia**, a następnie **Zresetuj wystąpienie eksperymentalne Microsoft Visual Studio 2010**.

2. Kompiluj wszystkie eksperymentalne językami DSL lub inne eksperymentalne rozszerzenia programu Visual Studio, które nadal mają być używane.

## <a name="see-also"></a>Zobacz też

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
