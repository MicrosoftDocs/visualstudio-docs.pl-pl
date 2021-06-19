---
title: Wprowadzenie do języków specyficznych dla domeny
description: Poznaj podstawowe pojęcia dotyczące definiowania i używania języka specyficznego dla domeny (DSL) utworzonego za pomocą zestawu SDK modelowania dla Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2637703e068a98e20f209d5de51a6003a4dd7f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386738"
---
# <a name="get-started-with-domain-specific-languages"></a>Wprowadzenie do języków specyficznych dla domeny

W tym temacie wyjaśniono podstawowe pojęcia dotyczące definiowania i używania języka specyficznego dla domeny (DSL) utworzonego za pomocą zestawu SDK modelowania dla Visual Studio.

> [!NOTE]
> Zestaw SDK przekształcania szablonu tekstu i Visual Studio SDK modelowania tekstu są instalowane automatycznie podczas instalowania określonych funkcji Visual Studio. Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Jeśli nie masz jeszcze dostępu do języka DSL, zalecamy zapoznanie się z laboratorium **narzędzi DSL Tools Lab,** które można znaleźć w tej witrynie: Zestaw SDK wizualizacji [i modelowania](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Co można zrobić za pomocą Domain-Specific Language?

Język specyficzny dla domeny jest notacją, zazwyczaj graficzną, która jest przeznaczona do określonego celu. Z kolei języki, takie jak UML, są ogólnego przeznaczenia. W DSL można zdefiniować typy elementu modelu i ich relacje oraz sposób ich prezentowanie na ekranie.

Po zaprojektowania DSL, można dystrybuować go jako część pakietu Visual Studio Integration Extension (VSIX). Użytkownicy pracują z DSL w Visual Studio:

![Diagram drzewa rodziny, przybornik i eksplorator](../modeling/media/familyt_instance.png)

Notacja jest tylko częścią DSL. Wraz z notacją pakiet VSIX zawiera narzędzia, które użytkownicy mogą zastosować, aby ułatwić im edytowanie i generowanie materiałów na podstawie modeli.

Jedną z głównych aplikacji plików DSL jest generowanie kodu programu, plików konfiguracji i innych artefaktów. Szczególnie w dużych projektach i liniach produktów, w których zostanie utworzonych kilka wariantów produktu, generowanie wielu zmiennych aspektów z poziomu plików DSL może zapewnić duży wzrost niezawodności i bardzo szybkie reagowanie na zmiany wymagań.

Pozostała część tego przeglądu to przewodnik wprowadzający podstawowe operacje tworzenia i używania języka specyficznego dla domeny w Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:

| Składnik | Link |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| Zestaw SDK modelowania dla Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Tworzenie rozwiązania DSL

Aby utworzyć nowy język specyficzny dla domeny, należy utworzyć nowe rozwiązanie Visual Studio przy użyciu szablonu projektu Domain-Specific Language.

1. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

2. W **obszarze Project types**(Typy projektów) rozwiń węzeł Other Project Types **(Inne typy projektów)** i kliknij pozycję **Extensibility (Rozszerzalność).**

3. Kliknij **projektant języka specyficznego dla domeny**.

     ![Okno dialogowe Tworzenie DSL](../modeling/media/create_dsldialog.png)

4. W polu **Nazwa** wpisz **FamilyTree**. Kliknij przycisk **OK**.

     Zostanie **otwarty Kreator języka specyficznego** dla domeny z wyświetloną listą szablonów rozwiązań DSL.

     Kliknij każdy szablon, aby wyświetlić opis.

     Szablony są przydatnymi punktami początkowymi. Każdy z nich zapewnia kompletny, roboczy DSL, który można edytować w zależności od potrzeb. Zazwyczaj należy wybrać szablon najbliżej tego, co chcesz utworzyć.

5. W tym przewodniku wybierz szablon **Minimalny** język.

6. Wprowadź rozszerzenie nazwy pliku dla DSL na odpowiedniej stronie kreatora. Jest to rozszerzenie, które będzie używać plików zawierających wystąpienia DSL.

    - Wybierz rozszerzenie, które nie jest skojarzone z żadnej aplikacji na komputerze lub na dowolnym komputerze, na którym chcesz zainstalować DSL. Na przykład rozszerzenia **docx** i **htm** byłyby nieakceptowalnymi rozszerzeniami nazw plików.

    - Kreator ostrzega, jeśli wprowadzone rozszerzenie jest używane jako DSL. Rozważ użycie innego rozszerzenia nazwy pliku. Można również zresetować wystąpienie eksperymentalne zestawu SDK Visual Studio, aby wyczyścić starych projektantów eksperymentalnych. Kliknij **przycisk Start**, kliknij pozycję Wszystkie **programy,** **Microsoft Visual Studio 2010 SDK,** **Narzędzia**, a następnie zresetuj **Microsoft Visual Studio 2010 Eksperymentalne wystąpienie** programu .

7. Sprawdź pozostałe strony, a następnie kliknij przycisk **Zakończ.**

     Generowane jest rozwiązanie, które zawiera dwa projekty. Mają nazwy Dsl i DslPackage. Zostanie otwarty plik diagramu o nazwie DslDefinition.dsl.

    > [!NOTE]
    > Większość kodu, który można zobaczyć w folderach w dwóch projektach, jest generowana z dslDefinition.dsl. Z tego powodu większość modyfikacji DSL są wprowadzone w tym pliku.

Interfejs użytkownika jest teraz podobny do poniższego obrazu.

![dsl designer](../modeling/media/dsl_designer.png)

To rozwiązanie definiuje język specyficzny dla domeny. Aby uzyskać więcej informacji, [zobacz Overview of the Domain-Specific Language Tools Interfejs użytkownika](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Ważne części rozwiązania DSL

Zwróć uwagę na następujące aspekty nowego rozwiązania:

- **Dsl\DslDefinition.dsl** Jest to plik, który jest wyświetlony podczas tworzenia rozwiązania DSL. Prawie cały kod w rozwiązaniu jest generowany na podstawie tego pliku, a większość zmian wprowadzonych w definicji DSL jest wprowadzana tutaj. Aby uzyskać więcej informacji, zobacz Praca z [diagramem definicji DSL](../modeling/working-with-the-dsl-definition-diagram.md).

- **Projekt DSL** Ten projekt zawiera kod, który definiuje język specyficzny dla domeny.

- **Projekt DslPackage** Ten projekt zawiera kod, który umożliwia otwarcie i edytowanie wystąpień DSL w Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Uruchamianie DSL

Rozwiązanie DSL można uruchomić natychmiast po jego utworzeniu. Później można stopniowo modyfikować definicję DSL, uruchamiając rozwiązanie ponownie po każdej zmianie.

### <a name="to-experiment-with-the-dsl"></a>Aby poeksperymentować z DSL

1. Kliknij **pozycję Przekształć wszystkie** szablony na **Eksplorator rozwiązań** narzędzi. To ponownie generuje większość kodu źródłowego z DslDefinition.dsl.

    > [!NOTE]
    > Za każdym razem, *gdy zmieniasz dslDefinition.dsl,* musisz kliknąć pozycję Przekształć **wszystkie szablony** przed przebudową rozwiązania. Ten krok można zautomatyzować. Aby uzyskać więcej informacji, zobacz How to Automate Transform All Templates (Jak [zautomatyzować przekształcanie wszystkich szablonów).](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

2. Naciśnij **klawisz F5** lub w menu **Debugowanie** kliknij pozycję **Rozpocznij debugowanie.**

     DSL jest kompilowany i instalowany w eksperymentalnym wystąpieniu Visual Studio.

     Uruchamia się eksperymentalne wystąpienie Visual Studio. Wystąpienie eksperymentalne pobiera ustawienia z oddzielnego poddrzewo rejestru, w którym Visual Studio rozszerzenia są rejestrowane na potrzeby debugowania. Normalne wystąpienia Visual Studio nie mają dostępu do zarejestrowanych tam rozszerzeń.

3. W eksperymentalnym wystąpieniu Visual Studio otwórz plik modelu o nazwie **Test z** Eksplorator rozwiązań **.**

     \- lub —

     Kliknij prawym przyciskiem myszy projekt Debugowanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Element**. W **oknie dialogowym** Dodawanie elementu wybierz typ pliku DSL.

     Plik modelu zostanie otwarty jako pusty diagram.

     Zostanie otwarte przybornik z wyświetlonymi narzędziami odpowiednimi dla typu diagramu.

4. Użyj narzędzi do tworzenia kształtów i łączników na diagramie.

    1. Aby utworzyć kształty, przeciągnij z przykładowej narzędzie Kształt na diagram.

    2. Aby połączyć dwa kształty, kliknij narzędzie Przykładowy łącznik, kliknij pierwszy kształt, a następnie kliknij drugi kształt.

5. Kliknij etykiety kształtów, aby je zmienić.

Eksperymentalny Visual Studio podobny do następującego przykładu:

![Drzewo przykładowe języka specyficznego dla domeny w Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Zawartość modelu

Zawartość pliku, który jest wystąpieniem DSL, jest nazywana *modelem*. Model zawiera *elementy modelu* <em>i</em> *połączenia* między elementami. Definicja DSL określa, jakie typy elementów modelu i linki mogą istnieć w modelu. Na przykład w języku DSL utworzonym na podstawie szablonu Minimalny język istnieje jeden typ elementu modelu i jeden typ linku.

Definicja DSL może określać sposób, w jaki model jest wyświetlany na diagramie. Możesz wybierać spośród różnych stylów kształtów i łączników. Możesz określić, że niektóre kształty są wyświetlane wewnątrz innych kształtów.

Model można wyświetlić jako drzewo w widoku **Eksploratora** podczas edytowania modelu. Podczas dodawania kształtów do diagramu elementy modelu są również wyświetlane w eksploratorze. Eksploratora można używać nawet wtedy, gdy nie ma diagramu.

Jeśli eksplorator nie jest wyświetlony w wystąpieniu debugowania programu Visual Studio, w **menu** Widok wskaż pozycję **Inne okna**, a następnie kliknij pozycję *\<Your Language>* **Eksplorator**.

### <a name="the-api-of-your-dsl"></a>Interfejs API DSL

Dsl generuje interfejs API, który umożliwia odczytywanie i aktualizowanie modeli, które są wystąpieniami DSL. Jedną z aplikacji interfejsu API jest generowanie plików tekstowych z modelu. Aby uzyskać więcej informacji, zobacz Design-Time Code Generation by using T4 Text Templates (Generowanie kodu [w czasie projektowania przy użyciu szablonów tekstowych T4).](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

W rozwiązaniu Debugowanie otwórz pliki szablonów z rozszerzeniem ".tt". Te przykłady pokazują, jak można wygenerować tekst z modeli i umożliwiają testowanie interfejsu API DSL. Jeden z przykładów jest napisany w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , drugi w . [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

W obszarze każdego pliku szablonu znajduje się plik, który generuje. Rozwiń plik szablonu w Eksplorator rozwiązań, a następnie otwórz wygenerowany plik.

Plik szablonu zawiera krótki segment kodu, który zawiera listę wszystkich elementów w modelu.

Wygenerowany plik zawiera wynik.

Po zmianie pliku modelu po ich wygenerowaniu zobaczysz odpowiednie zmiany w wygenerowanych plikach.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Aby ponownie wygenerować pliki tekstowe po zmianie pliku modelu

1. W eksperymentalnym wystąpieniu Visual Studio zapisz plik modelu.

2. Upewnij się, że parametr nazwy pliku w każdym pliku tt odwołuje się do pliku modelu, który jest w eksperymentach. Zapisz plik tt.

3. Kliknij **pozycję Przekształć wszystkie** szablony na pasku narzędzi **Eksplorator rozwiązań**.

     \- lub —

     Kliknij prawym przyciskiem myszy szablony, które chcesz ponownie wygenerować, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe.**

Do projektu można dodać dowolną liczbę plików szablonów tekstowych. Każdy szablon generuje jeden plik wyników.

> [!NOTE]
> Po zmianie definicji DSL kod przykładowego szablonu tekstowego nie będzie działać, chyba że go zaktualizujemy.

Aby uzyskać więcej informacji, zobacz Generowanie kodu z języka [Domain-Specific i](../modeling/generating-code-from-a-domain-specific-language.md) Pisanie kodu w celu dostosowania Domain-Specific [języku .](../modeling/writing-code-to-customise-a-domain-specific-language.md)

## <a name="customizing-the-dsl"></a>Dostosowywanie DSL

Jeśli chcesz zmodyfikować definicję DSL, zamknij wystąpienie eksperymentalne i zaktualizuj definicję w głównym Visual Studio wystąpienia.

> [!NOTE]
> Po zmodyfikowaniu definicji DSL można utracić informacje w modelach testowych utworzonych przy użyciu wcześniejszych wersji.  Na przykład rozwiązanie debugowania zawiera plik o nazwie Sample, który zawiera pewne kształty i łączniki. Po rozpoczęciu tworzenia definicji DSL nie będą one widoczne i zostaną utracone podczas zapisywania pliku.

Można wprowadzić wiele różnych rozszerzeń dsl. Poniższe przykłady dają wrażenie możliwości.

Po każdej zmianie zapisz definicję  DSL, kliknij pozycję Przekształć wszystkie szablony w Eksplorator rozwiązań , **a** następnie naciśnij **klawisz F5,** aby poeksperymentować ze zmienionym DSL.

### <a name="rename-the-types-and-tools"></a>Zmienianie nazw typów i narzędzi

Zmień nazwy istniejących klas domen i relacji. Na przykład, zaczynając od definicji DSL utworzonej na podstawie szablonu Języka minimalnego, można wykonać następujące operacje zmiany nazwy, aby utworzyć DSL reprezentujące drzewa rodziny.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Aby zmienić nazwy klas domeny, relacji i narzędzi

1. Na diagramie DslDefinition zmień nazwę **ExampleModel** na **FamilyTreeModel,** **ExampleElement** na **Person,** **Targets** to **Parents** i **Sources** na **Children**. Możesz kliknąć każdą etykietę, aby ją zmienić.

     ![Diagram definicji DSL &#45; modelu drzewa rodziny](../modeling/media/familyt_person.png)

2. Zmień nazwę narzędzi elementu i łącznika.

    1. Otwórz okno Eksplorator DSL, klikając kartę w obszarze Eksplorator rozwiązań. Jeśli go nie widzisz, w menu **Widok** wskaż pozycję **Inne okna,** a następnie kliknij pozycję **Eksplorator DSL.** Eksplorator DSL jest widoczny tylko wtedy, gdy diagram definicji DSL jest aktywnym oknem.

    2. Otwórz okno Właściwości i umieść go w taki sposób, aby w tym samym czasie można było zobaczyć eksplorator DSL i właściwości.

    3. W Eksploratorze DSL **rozwiń pozycję Edytor,** **Karty przybornika** *\<your DSL>* , , a następnie pozycję **Narzędzia**.

    4. Kliknij pozycję ExampleElement ( **Przykład)**. Jest to element przybornika, który służy do tworzenia elementów.

    5. W okno Właściwości zmień właściwość **Name** na **Person**.

         Zwróć uwagę, **że właściwość Caption** również się zmienia.

    6. W ten sam sposób zmień nazwę narzędzia **ExampleConnector** na **ParentLink.** Zmodyfikować **właściwość Caption** tak, aby nie była kopią właściwości Name. Na przykład wprowadź link **nadrzędny**.

3. Ponownie skompilować DSL.

    1. Zapisz plik definicji DSL.

    2. Kliknij **pozycję Przekształć wszystkie** szablony na pasku narzędzi Eksplorator rozwiązań

    3. Naciśnij F5. Poczekaj na wystąpienie eksperymentalne Visual Studio.

4. W rozwiązaniu Debugowanie w eksperymentalnym wystąpieniu Visual Studio otwórz plik modelu testowego. Przeciągnij na nie elementy z przybornika. Zwróć uwagę, że nazwy narzędzi i nazwy typów w eksploratorze DSL uległy zmianie.

5. Zapisz plik modelu.

6. Otwórz plik tt i zastąp wystąpienia starego typu i nazw właściwości nowymi nazwami.

7. Upewnij się, że nazwa pliku określona w pliku tt określa model testowy.

8. Zapisz plik tt. Otwórz wygenerowany plik, aby zobaczyć wynik uruchomienia kodu w pliku tt. Sprawdź, czy jest prawidłowa.

### <a name="add-domain-properties-to-classes"></a>Dodawanie właściwości domeny do klas
 Dodaj właściwości do klasy domeny, na przykład reprezentujące lata urodzenia i zgonu osoby.

 Aby nowe właściwości były widoczne na diagramie, należy dodać dekoratory do kształtu, który wyświetla element modelu.  Należy również zamapować właściwości na dekoratory.

##### <a name="to-add-properties-and-display-them"></a>Aby dodać właściwości i wyświetlić je

1. Dodaj właściwości.

   1. Na diagramie definicji DSL kliknij prawym przyciskiem myszy **klasę domeny** **Person,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję Właściwość domeny .

   2. Wpisz listę nowych nazw właściwości, takich jak **Birth (Urodzenia)** i **Death (Zgon).** Po każdym z nich naciśnij klawisz **Enter.**

2. Dodaj dekoratory, które będą wyświetlać właściwości w kształcie.

   1. Postępuj zgodnie z szarą linią, która rozciąga się od klasy domeny Person do drugiej strony diagramu. Jest to mapa elementu diagramu. Łączy klasę domeny z klasą kształtu.

   2. Kliknij prawym przyciskiem myszy tę klasę kształtu, wskaż **polecenie Dodaj**, a następnie kliknij pozycję **Text Decorator**.

   3. Dodaj dwa dekoratory o nazwach takich jak **BirthDecorator** i **DeathDecorator.**

   4. Wybierz każdy nowy dekorator i w okno Właściwości ustaw **pole Pozycja.** Określa, gdzie wartość właściwości domeny będzie wyświetlana w kształcie. Na przykład ustaw **wartość InnerBottomLeft** i **InnerBottomRight**.

        ![Definicja kształtu przedziału](../modeling/media/familyt_compartment.png)

3. Zamapuj dekoratory na właściwości.

   1. Otwórz okno Szczegóły DSL. Zazwyczaj znajduje się on na karcie obok okna Dane wyjściowe. Jeśli go nie widzisz, w menu **Widok** wskaż pozycję **Inne okna,** a następnie kliknij pozycję **Szczegóły DSL.**

   2. Na diagramie definicji DSL kliknij wiersz, który łączy **klasę domeny Person** z klasą kształtu.

   3. W **obszarze Szczegóły DSL** na karcie **Decorator Maps (Mapy** dekoratora) kliknij pole wyboru dla niezamapowanych dekoratorów. W **właściwości wyświetlania** wybierz właściwość domeny, do której ma być mapowana. Na przykład **zamapuj birthDecorator** na **birth**.

4. Zapisz DSL, kliknij przycisk Przekształć wszystkie szablony, a następnie naciśnij klawisz F5.

5. Na przykładowym diagramie modelu sprawdź, czy możesz teraz kliknąć wybrane pozycje i wpisać w nich wartości. Ponadto po wybraniu kształtu **Osoba** na okno Właściwości zostaną wyświetlone nowe właściwości Birth and Death.

6. W pliku tt można dodać kod, który uzyskuje właściwości poszczególnych osób.

   ![Diagram drzewa rodziny, przybornik i eksplorator](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definiowanie nowych klas
 Do modelu można dodawać klasy domen i relacje. Można na przykład utworzyć nową klasę reprezentującą miejscowość i nową relację reprezentującą osobę mieszkaną w mieście.

 Aby odróżnić różne typy na diagramie modelu, można mapować klasy domen na różne rodzaje kształtów lub na kształty o różnych geometriach i kolorach.

##### <a name="to-add-and-display-a-new-domain-class"></a>Aby dodać i wyświetlić nową klasę domeny

1. Dodaj klasę domeny i nadaj jej nazwę podrzędną katalogu głównego modelu.

    1. Na diagramie definicji DSL kliknij narzędzie **Osadzanie** relacji, kliknij klasę główną **FamilyTreeModel,** a następnie kliknij pustą część diagramu.

         Zostanie wyświetlona nowa klasa domeny połączona z modelem FamilyTreeModel za pomocą relacji osadzania.

         Ustaw jego nazwę, na przykład **Miejscowość**.

        > [!NOTE]
        > Każda klasa domeny z wyjątkiem katalogu głównego modelu musi być obiektem docelowym co najmniej jednej relacji osadzania lub musi dziedziczyć z klasy, która jest obiektem docelowym osadzania. Z tego powodu często wygodnie jest utworzyć klasę domeny za pomocą narzędzia relacji osadzania.

    2. Dodaj właściwość domeny do nowej klasy, na przykład **Nazwa**.

2. Dodaj relację odwołania między osobami i miejscowością.

    1. Kliknij narzędzie **Relacja** referencyjna, kliknij pozycję Osoba, a następnie kliknij pozycję Miejscowość.

         ![Fragment definicji DSL: główny drzewo rodziny](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Relacje odwołań reprezentują odwołania krzyżowe między częściami drzewa modelu.

3. Dodaj kształt reprezentujący kształt na diagramach modelu.

    1. Przeciągnij kształt **geometrycznych** z przybornika do diagramu i zmień jego nazwę, na przykład **TownShape**.

    2. W okno Właściwości pola Wygląd nowego kształtu, takie jak Kolor wypełnienia i Geometria.

    3. Dodaj dekorator, aby wyświetlić nazwę miejscowości, i zmień jej nazwę na NameDecorator. Ustaw jej właściwość Position.

4. Zamapuj klasę domeny Miejscowość na klasę TownShape.

    1. Kliknij narzędzie **Mapa elementu diagramu,** a następnie kliknij klasę domeny Miejscowość, a następnie klasę kształtu TownShape.

    2. Na karcie **Decorator Maps (Mapy** dekoratora) w oknie DSL Details (Szczegóły **DSL)** z wybranym łącznikiem mapy zaznacz pole nameDecorator i ustaw właściwość **display na** wartość Name (Nazwa).

5. Utwórz łącznik, aby wyświetlić relację między osobami i cytą.

    1. Przeciągnij łącznik z przybornika do diagramu. Zmień jego nazwę i ustaw jej właściwości wyglądu.

    2. Użyj narzędzia **Mapa elementu diagramu,** aby połączyć nowy łącznik z relacją między osobami i miejscowością.

         ![Definicja drzewa rodziny z dodaną mapą kształtów](../modeling/media/familyt_shapemap.png)

6. Utwórz narzędzie elementu do tworzenia nowej miejscowości.

    1. W **Eksploratorze DSL rozwiń** pozycję **Edytor,** a następnie **pozycję Karty przybornika**.

    2. Kliknij prawym przyciskiem *\<your DSL>* myszy, a następnie kliknij **polecenie Dodaj nowe narzędzie elementu**.

    3. Ustaw właściwość **Name** nowego narzędzia i ustaw jej właściwość **Class** na miejscowość.

    4. Ustaw właściwość **Ikona przybornika.** Kliknij **przycisk [...]** i w polu Nazwa **pliku** wybierz plik ikony.

7. Utwórz narzędzie łącznika do tworzenia połączenia między osobami i osobami.

    1. Kliknij prawym przyciskiem *\<your DSL>* myszy, a następnie kliknij polecenie **Dodaj nowe narzędzie łącznika.**

    2. Ustaw właściwość Name nowego narzędzia.

    3. We właściwości **ConnectionBuilder** wybierz konstruktora, który zawiera nazwę Person-Town relacji.

    4. Ustaw **ikonę przybornika**.

8. Zapisz definicję DSL, kliknij **pozycję Przekształć wszystkie szablony,** a następnie naciśnij **klawisz F5.**

9. W eksperymentalnym wystąpieniu Visual Studio otwórz plik modelu testowego. Nowe narzędzia pozwalają tworzyć łaziki i połączenia między miastami i osobami. Zwróć uwagę, że można tworzyć tylko połączenia między właściwymi typami elementów.

10. Utwórz kod, który zawiera listę miejscowości, w której znajduje się każda osoba. Szablony tekstowe to jedno z miejsc, w których można uruchomić taki kod. Można na przykład zmodyfikować istniejący plik Sample.tt w rozwiązaniu debugowania, tak aby zawierał następujący kod:

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

     Zapisanie pliku *.tt spowoduje utworzenie pliku podmiotu zależnego zawierającego listę osób i ich mieszkańców. Aby uzyskać więcej informacji, zobacz [Generowanie kodu z Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Walidacja i polecenia
 Możesz dalej rozwijać ten DSL, dodając ograniczenia walidacji. Te ograniczenia to metody, które można zdefiniować, aby upewnić się, że model jest w poprawnym stanie. Można na przykład zdefiniować ograniczenie, aby upewnić się, że data urodzenia dziecka jest późniejsza niż data jego rodziców. Funkcja walidacji wyświetla ostrzeżenie, jeśli użytkownik DSL próbuje zapisać model, który przerywa dowolny z ograniczeń. Aby uzyskać więcej informacji, zobacz Validation in a Domain-Specific Language (Walidacja [w Domain-Specific Języku ).](../modeling/validation-in-a-domain-specific-language.md)

 Można również zdefiniować polecenia menu, które użytkownik może wywołać. Polecenia mogą modyfikować model. Mogą również wchodzić w interakcje z innymi modelami w Visual Studio i z zasobami zewnętrznymi. Aby uzyskać więcej informacji, [zobacz How to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Wdrażanie DSL
 Aby umożliwić innym użytkownikom korzystanie z języka specyficznego dla domeny, należy rozpowszechnić plik Visual Studio Extension (VSIX). Jest on tworzony podczas kompilowania rozwiązania DSL.

 Znajdź plik .vsix w folderze bin rozwiązania. Skopiuj go na komputer, na którym chcesz go zainstalować. Na tym komputerze kliknij dwukrotnie plik VSIX. DSL może być używany we wszystkich wystąpieniach Visual Studio na tym komputerze.

 Tej samej procedury można użyć do zainstalowania DSL na własnym komputerze, dzięki czemu nie trzeba używać eksperymentalnego wystąpienia Visual Studio.

 Aby uzyskać więcej informacji, zobacz [Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Usuwanie starych eksperymentalnych plików DSL
 Jeśli nie chcesz już tworzyć eksperymentalnych plików DSL, możesz je usunąć z komputera, resetując Visual Studio eksperymentalne.

 Spowoduje to usunięcie z komputera wszystkich eksperymentalnych rozszerzeń DSL i innych rozszerzeń Visual Studio eksperymentalnych. Są to rozszerzenia, które zostały wykonane w trybie debugowania.

 Ta procedura nie powoduje usunięcia rozszerzeń DSL ani innych rozszerzeń Visual Studio, które zostały w pełni zainstalowane przez wykonanie pliku VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Aby zresetować wystąpienie Visual Studio eksperymentalne

1. Kliknij **przycisk Start**, kliknij pozycję Wszystkie **programy,** Microsoft Visual Studio SDK **2010,** **Narzędzia**, a następnie Microsoft Visual Studio wystąpienie eksperymentalne programu **2010.**

2. Ponownie skompilować wszystkie eksperymentalne rozszerzenia DSL Visual Studio rozszerzenia eksperymentalne, których nadal chcesz używać.

## <a name="see-also"></a>Zobacz też

- [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
