---
title: Wprowadzenie do języków specyficznych dla domeny | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ca90a90d476acc0bdbc1df426b981d98207bbd28
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687250"
---
# <a name="getting-started-with-domain-specific-languages"></a>Wprowadzenie do języków specyficznych dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano podstawowe pojęcia związane z definiowanie i korzystanie z języka specyficznego dla domeny (DSL), utworzone za pomocą zestawu Modeling SDK for Visual Studio.  
  
 Jeśli jesteś nowym użytkownikiem językami DSL, firma Microsoft zaleca pracy za pośrednictwem **laboratorium narzędzia DSL**, która znajduje się w tej lokacji: [Visualizaton i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>Co można zrobić za pomocą języka dotyczącego określonej domeny?  
 Języka specyficznego dla domeny jest notacji, zwykle graficzny, który jest przeznaczony do użycia do określonego celu. Z drugiej strony języków, takich jak UML są ogólnego przeznaczenia. W języku DSL można zdefiniować typów elementu modelu i ich wzajemne relacje i jak są przedstawione na ekranie.  
  
 DSL zostały tak zaprojektowane, mogą dystrybuować je jako część pakietu Visual Studio Integration rozszerzenie (VSIX). Użytkownicy korzystają z DSL w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
 ![Diagram drzewa rodziny, przybornika i Eksplorator](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 Jest tylko część DSL. Wraz z notacji pakietu VSIX zawiera narzędzia, które użytkownicy mogą stosować, aby pomóc im edytować i generowanie materiału na podstawie ich modeli.  
  
 Jedną z głównych aplikacji językami DSL ma generować kod programu, pliki konfiguracji i innych artefaktów. Szczególnie w dużych projektach i linie produktów, w którym zostanie utworzona kilka wariantów produktu, generowanie wiele aspektów zmiennej z językami DSL może zapewnić duży wzrost niezawodności i bardzo szybkie przesłanie odpowiedzi na zmiany wymagań.  
  
 Pozostała część tego omówienia jest przewodnik, który wprowadza podstawowe operacje tworzenia i używania języka specyficznego dla domeny w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modeling SDK for Visual Studio|[Pobierz MSDK](https://www.microsoft.com/download/details.aspx?id=48148)|  
  
## <a name="creating-a-dsl-solution"></a>Tworzenie rozwiązania języka DSL  
 Aby utworzyć nowego języka specyficznego dla domeny, należy utworzyć nową [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania za pomocą szablonu projektu języka specyficznego dla domeny.  
  
#### <a name="to-create-a-dsl-solution"></a>Aby utworzyć rozwiązanie DSL  
  
1. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2. W obszarze **typów projektów**, rozwiń węzeł **inne typy projektów** węzeł, a następnie kliknij przycisk **rozszerzalności**.  
  
3. Kliknij przycisk **projektanta języka specyficznego dla domeny**.  
  
    ![Tworzenie okna dialogowego DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
4. W **nazwa** wpisz **FamilyTree**. Kliknij przycisk **OK**.  
  
    **Kreatora języka specyficznego dla domeny** otwiera i wyświetla listę rozwiązań DSL szablonu.  
  
    Kliknij każdy szablon, aby zapoznać się z opisem  
  
    Szablony są przydatne punktów początkowych. Każdy z nich zawiera pełną pracy DSL, który można edytować w zależności od potrzeb. Zazwyczaj należy wybrać szablon w najbliższym ma zostać utworzona.  
  
5. W ramach tego przewodnika wybierz **minimalny języka** szablonu.  
  
6. Wprowadź rozszerzenie nazwy pliku DSL w odpowiedniej strony w kreatorze. To rozszerzenie, używanego przez pliki zawierające wystąpienia elementu DSL.  
  
   - Wybierz rozszerzenie, które nie jest skojarzony z dowolnej aplikacji na komputerze lub w dowolnym komputerze, na którym chcesz zainstalować język DSL. Na przykład **docx** i **htm** będzie niedopuszczalne pliku rozszerzenia nazw.  
  
   - Kreator wyświetli ostrzeżenie, jeśli jest używane rozszerzenie, które zostały wprowadzone jako języka DSL. Należy rozważyć użycie innym rozszerzeniem nazwy pliku. Możesz także zresetować Visual Studio SDK eksperymentalne wystąpienie wyczyszczenie stare projektantów eksperymentalne. Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, a następnie **resetowania firmy Microsoft Wystąpienie programu Visual Studio 2010 eksperymentalne**.  
  
7. Zbadaj inne strony, a następnie kliknij przycisk **Zakończ**.  
  
    To rozwiązanie jest generowany, która zawiera dwa projekty. Są one nazywane Dsl i DslPackage. Plik diagramu zostanie otwarty to znaczy DslDefinition.dsl nazwanych.  
  
   > [!NOTE]
   > Większość kodu, który można zobaczyć w foldery w dwóch projektów jest generowany na podstawie DslDefinition.dsl. Z tego powodu większość modyfikacji DSL zostały wprowadzone w tym pliku.  
  
   Interfejs użytkownika jest teraz podobny do poniższej ilustracji.  
  
   ![Projektant DSL](../modeling/media/dsl-designer.png "dsl_designer")  
  
   To rozwiązanie definiuje języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [omówienie interfejsu użytkownika narzędzi języka specyficznego dla domeny](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>Ważne elementy rozwiązania DSL  
 Należy zauważyć następujące aspekty nowego rozwiązania.  
  
- **Dsl\DslDefinition.DSL** jest plik, zostanie wyświetlony podczas tworzenia rozwiązania języka DSL. Prawie cały kod w rozwiązaniu jest generowany na podstawie tego pliku, a większość zmian, które wprowadzasz do definicji DSL są wprowadzone w tym miejscu. Aby uzyskać więcej informacji, zapoznaj się z praca [Praca z diagramem definicji DSL](../modeling/working-with-the-dsl-definition-diagram.md).  
  
- **Projektu DSL** ten projekt zawiera kod, który definiuje języka specyficznego dla domeny.  
  
- **Projekt DslPackage** ten projekt zawiera kod, który umożliwia wystąpienia elementu DSL, aby go otworzyć i edytować w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="Debugging"></a> Uruchamianie język DSL  
 Możesz uruchomić rozwiązanie DSL, zaraz po jego utworzeniu. Później można zmodyfikować definicję DSL stopniowo, uruchamianie rozwiązania ponownie po każdej zmianie.  
  
#### <a name="to-experiment-with-the-dsl"></a>Aby eksperymentować z język DSL  
  
1. Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań. Większość kodu źródłowego z DslDefinition.dsl to generuje.  
  
   > [!NOTE]
   > Zawsze, gdy zmienisz DslDefinition.dsl, należy kliknąć przycisk **Przekształć wszystkie szablony** przed Kompiluj rozwiązanie. Możesz zautomatyzować ten krok. Aby uzyskać więcej informacji, zobacz [jak zautomatyzować Przekształć wszystkie szablony](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2. Naciśnij klawisz F5, lub na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
    Język DSL zostanie skompilowany i będzie zainstalowany w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    Eksperymentalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpoczyna się. Wystąpienie eksperymentalne zapasowe jego ustawieniami z oddzielnych poddrzewo rejestru, gdzie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia są zarejestrowane na potrzeby debugowania. Normalne wystąpień [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie mają dostępu do rozszerzenia ma zarejestrowane.  
  
3. W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otwórz plik modelu o nazwie **testu** z **Eksploratora rozwiązań**.  
  
    \- lub —  
  
    Kliknij prawym przyciskiem myszy projekt debugowania, wskaż opcję **Dodaj**, a następnie kliknij przycisk **elementu**. W **elementu Dodawanie** okno dialogowe, wybierz typ pliku DSL.  
  
    Plik modelu zostanie otwarty jako pusty diagram.  
  
    Przybornik otwiera i wyświetla narzędzia odpowiednie dla typu diagramu.  
  
4. Narzędzia do tworzenia kształtów i łączników na diagramie.  
  
   1. Aby tworzyć kształty, przeciągnij za pomocą narzędzia przykład kształt na diagramie.  
  
   2. Aby połączyć dwa kształty, kliknij narzędzie przykład łącznik, kliknij pierwszy kształt, a następnie kliknij drugi kształt.  
  
5. Kliknij pozycję etykiety kształty, aby je zmienić.  
  
   Twoje eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] będą podobne do następującego przykładu:  
  
   ![](../modeling/media/dsl-min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>Zawartość modelu  
 Zawartość pliku, który jest wystąpieniem DSL jest nazywany *modelu*. Model zawiera *elementów modelu* i *łącza* między elementami. Określa, jakie typy elementów modelu w definicji DSL i łącza może znajdować się w modelu. Na przykład w utworzone na podstawie szablonu minimalnego języka DSL, istnieje jeden typ elementu modelu i jednego typu łącza.  
  
 W definicji DSL można określić, jak model pojawia się na diagramie. Możesz wybrać spośród różnych stylów kształtów i łączników. Można określić, czy niektóre kształty są widoczne w innych kształtów.  
  
 Model można przeglądać w postaci drzewa w **Explorer** wyświetlania podczas edycji modelu. W miarę dodawania kształtów na diagramie elementy modelu są również wyświetlane w Eksploratorze. Można Eksploratora, nawet jeśli dostępny jest nie diagramu.  
  
 Jeśli nie widzisz Eksploratora w wystąpienie debugowania programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]na **widoku** menu wskaż **Windows inne**, a następnie kliknij przycisk  *\<Twój język >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>Interfejs API DSL  
 DSL generuje interfejsu API, która umożliwia odczytywanie i aktualizowanie modeli, które są wystąpieniami język DSL. Jednej aplikacji interfejsu API jest generowanie plików tekstowych z modelu. Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 W tym rozwiązaniu debugowanie Otwórz pliki szablonu z rozszerzeniem ".tt". Te przykłady pokazują, jak można wygenerować tekst ze modeli i umożliwiają testowanie interfejsu API DSL. Jednym z przykładów są zapisywane [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], inne w [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
 Na podstawie każdego szablonu plik jest plikiem, który generuje. Rozwiń plik szablonu w Eksploratorze rozwiązań, a następnie otwórz wygenerowany plik.  
  
 Plik szablonu zawiera krótki segment kodu, który wyświetla listę wszystkich elementów w modelu.  
  
 Wygenerowany plik zawiera wynik.  
  
 Po zmianie pliku modelu zobaczysz odpowiednie zmiany w wygenerowanych plików po ponownym wygenerowaniu plików.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Aby ponownie wygenerować pliki tekstowe, po zmianie pliku modelu  
  
1. W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Zapisz plik modelu.  
  
2. Upewnij się, że parametr nazwy pliku w każdym pliku .tt odwołuje się do pliku modelu, którego używasz do doświadczeń. Zapisz plik .tt.  
  
3. Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi **Eksploratora rozwiązań**.  
  
    \- lub —  
  
    Kliknij prawym przyciskiem myszy szablonów, które chcesz wygenerować ponownie, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
   Można dodać dowolną liczbę plików szablonów tekstu do projektu. Każdy szablon generuje jednego pliku wyników.  
  
> [!NOTE]
> Po zmianie definicji DSL przykładowego kodu szablonu tekstu nie będzie działać, o ile go zaktualizować.  
  
 Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md) i [pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Dostosowywanie języka DSL  
 Jeśli chcesz zmodyfikować definicję DSL, zamknij wystąpienie doświadczalne i zaktualizuj definicję w oknie głównym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wystąpienia.  
  
> [!NOTE]
> Po zmodyfikowaniu definicji DSL, mogą utracić informacji w modelach testów, które zostały utworzone za pomocą wcześniejszych wersji.  Na przykład debugowania rozwiązań zawiera plik o nazwie przykładowy, który zawiera niektóre kształtów i łączników. Po rozpoczęciu tworzenia definicji DSL, nie będą widoczne, a zostaną one utracone podczas zapisywania pliku.  
  
 Istnieje możliwość szerokiej gamy rozszerzenia DSL. W poniższych przykładach przedstawiono pojęcie o możliwościach.  
  
 Po każdej zmianie, Zapisz definicji DSL kliknij **Przekształć wszystkie szablony** w **Eksploratora rozwiązań**, a następnie naciśnij klawisz **F5** eksperymentować zmienione DSL.  
  
### <a name="rename-the-types-and-tools"></a>Zmiana nazwy, typy i narzędzia  
 Zmień nazwę istniejącej klasy domeny i relacje. Na przykład począwszy od definicji Dsl, utworzone na podstawie szablonu minimalnego języka, możesz można wykonać następujące operacje zmiany nazwy, aby DSL reprezentują drzew rodziny.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Aby zmienić nazwę klasy domeny, relacje i narzędzia  
  
1. Na diagramie DslDefinition, Zmień nazwę **ExampleModel** do **FamilyTreeModel**, **ExampleElement** do **osoby**,  **Obiekty docelowe** do **rodzice**, i **źródeł** do **dzieci**. Możesz kliknąć każdej etykiety, aby ją zmienić.  
  
     ![Diagramem definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt-person.png "FamilyT_Person")  
  
2. Zmień nazwę elementu i łącznika narzędzia.  
  
    1. Otwórz okno Eksplorator DSL, klikając kartę w Eksploratorze rozwiązań. Jeśli nie jest widoczna, na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **Eksplorator DSL**. Eksplorator modelu DSL jest widoczny tylko wtedy, gdy aktywne okno diagramem definicji DSL.  
  
    2. Otwórz okno właściwości i umieść ją, aby mogli przeglądać Eksplorator DSL i właściwości, które znajdują się w tym samym czasie.  
  
    3. W Eksploratorze DSL rozwiń **edytora**, **karty przybornika**,  *\<DSL >*, a następnie **narzędzia**.  
  
    4. Kliknij przycisk **ExampleElement**. Jest to element przybornika, który służy do tworzenia elementów.  
  
    5. W oknie Właściwości zmień **nazwa** właściwości **osoby**.  
  
         Należy zauważyć, że **podpis** zmienia także właściwości.  
  
    6. W ten sam sposób, Zmień nazwę **ExampleConnector** narzędzia, aby **ParentLink**. Instrukcja ALTER **podpis** właściwości, tak że nie jest kopią właściwości Name. Na przykład, wprowadź **Link elementu nadrzędnego**.  
  
3. Ponownie skompiluj język DSL.  
  
    1. Zapisz plik w definicji DSL.  
  
    2. Kliknij przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań  
  
    3. Naciśnij F5. Poczekaj, aż wystąpienie eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pojawia się.  
  
4. W rozwiązaniu debugowanie w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otwórz plik modelu testu. Przeciągnij elementy go z przybornika. Zauważ, że zmieniono podpisy narzędzia i nazwy typów w Eksplorator DSL.  
  
5. Zapisz plik modelu.  
  
6. Otwórz plik .tt i zastąp stare nazwy typu i właściwości wystąpienia nowych nazw.  
  
7. Upewnij się, że nazwa pliku, który jest określony w pliku .tt Określa model testu.  
  
8. Zapisz plik .tt. Otwórz wygenerowany plik, aby zobaczyć wynik uruchomienia kodu w pliku .tt. Sprawdź, czy jest poprawna.  
  
### <a name="add-domain-properties-to-classes"></a>Dodawanie właściwości domeny do klas  
 Dodaj właściwości do klasy domeny, na przykład do reprezentowania lat urodzenia i śmierci osoby.  
  
 Aby wyświetlić właściwości nowej na diagramie, należy dodać *dekoratory* do kształtu, który wyświetla elementu modelu. Właściwości musi być również mapować do dekoratory.  
  
##### <a name="to-add-properties-and-display-them"></a>Aby dodać właściwości i wyświetlaj je  
  
1. Dodaj właściwości.  
  
   1. W definicji DSL diagramu, kliknij prawym przyciskiem myszy **osoby** klasy domeny, wskaż **Dodaj**, a następnie kliknij przycisk **właściwość domeny**.  
  
   2. Wpisz listę nowych nazw właściwości, takie jak **urodzenia** i **śmierci**. Naciśnij klawisz **Enter** po każdej z nich.  
  
2. Dodaj dekoratory, które będą wyświetlane właściwości w kształcie.  
  
   1. Postępuj zgodnie z szara linia, rozciąga się od klasy domeny osoba po drugiej stronie diagramu. To mapowanie elementu diagramu. Klasy domeny łączy do klasy kształtu.  
  
   2. Kliknij prawym przyciskiem myszy tę klasę kształtu, wskaż opcję **Dodaj**, a następnie kliknij przycisk **Dekoratora tekstu**.  
  
   3. Dodaj dwa dekoratory przy użyciu nazwy, takie jak **BirthDecorator** i **DeathDecorator**.  
  
   4. Wybierz każdy dekorator nowe, a w oknie właściwości ustaw **pozycji** pola. Określa, gdzie zostaną wyświetlone wartości właściwości domeny na kształcie. Na przykład ustawić **InnerBottomLeft** i **InnerBottomRight**.  
  
        ![Definicja kształtu przedziału](../modeling/media/familyt-compartment.png "FamilyT_Compartment")  
  
3. Mapowania dekoratorów do właściwości.  
  
   1. Otwórz okno Szczegóły języka DSL. Zazwyczaj jest na karcie obok w oknie danych wyjściowych. Jeśli nie jest widoczna, na **widoku** menu wskaż **Windows inne**, a następnie kliknij przycisk **szczegóły języka DSL**.  
  
   2. Polecenie diagramem definicji DSL linii łączącej **osoby** klasy domeny do klasy kształtu.  
  
   3. W **szczegóły języka DSL**na **mapy Dekoratora** kliknij pole wyboru na niezamapowane dekoratora. W **Właściwość wyświetlania**, wybierz właściwość domeny, do której ma on zamapowany. Na przykład mapować **BirthDecorator** do **urodzenia**.  
  
4. Zapisz język DSL, a następnie kliknij przycisk Przekształć wszystkie szablony i naciśnij klawisz F5.  
  
5. W przykładowy diagram modelu Sprawdź, czy można teraz kliknąć pozycje, które wybrałeś i wpisz wartości do nich. Ponadto po wybraniu **osoby** kształtu, okno właściwości wyświetla nowe właściwości urodzenia i śmierci.  
  
6. W pliku .tt można dodać kod, który uzyskuje właściwości każdej osoby.  
  
   ![Diagram drzewa rodziny, przybornika i Eksplorator](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Definiowanie nowych klas  
 Można dodać klasy domeny i relacje do modelu. Na przykład można utworzyć nowej klasy reprezentujące miast i nową relację do reprezentowania osoby znajdowały się w mieście.  
  
 Aby różne typy distinct diagramu modelu, można mapować klasami domeny różne rodzaje kształtów lub kształtów różne typy geometryczne i kolorów.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Aby dodać i wyświetlić nową klasę domeny  
  
1. Dodaj klasę domeny i Uczyń elementem podrzędnym elementu głównego.  
  
    1. W definicji DSL diagramu, kliknij **relacji osadzania** narzędzia, kliknij przycisk Klasa główna **FamilyTreeModel**, a następnie kliknij pustą część diagramu.  
  
         Nową klasę domeny zostanie wyświetlony podłączonego do FamilyTreeModel przy użyciu relacji osadzania.  
  
         Ustaw jego nazwę, na przykład **miejscowość**.  
  
        > [!NOTE]
        > Każda klasa domeny, z wyjątkiem głównym modelu musi być elementem docelowym co najmniej jedna relacja osadzania lub ten typ musi dziedziczyć z klasy, która jest lokalizacją docelową osadzania. Z tego powodu często wygodne jest Utwórz klasę domeny przy użyciu narzędzia do relacji osadzania.  
  
    2. Dodaj właściwość domeny do nowej klasy, na przykład **nazwa**.  
  
2. Dodawanie relacji między miejscowości i osoby.  
  
    1. Kliknij przycisk **relacja odwołania** narzędzia, kliknij przycisk osoby, a następnie kliknij przycisk miejscowości.  
  
         ![Fragment definicji DSL: katalogu głównego drzewa rodziny](../modeling/media/familyt-root.png "FamilyT_Root")  
  
        > [!NOTE]
        > Relacje odniesienia reprezentuje odsyłacze z jednej części drzewa modelu do innego.  
  
3. Dodawanie kształtu do reprezentowania miast na diagramach modelu.  
  
    1. Przeciągnij **kształt geometryczny** z przybornika do diagramu i zmienić jej nazwę na przykład **TownShape**.  
  
    2. W oknie właściwości ustaw pola wygląd nowy kształt, takich jak kolor wypełnienia i geometrii.  
  
    3. Dodaj Dekoratora, aby wyświetlić nazwę miejscowości, a następnie zmień jego nazwę na NameDecorator. Ustaw jego właściwość pozycji.  
  
4. Miejscowość klasy domeny są mapowane na TownShape.  
  
    1. Kliknij przycisk **mapowanie elementu diagramu** narzędzia, a następnie kliknij klasy domeny miejscowości, a następnie TownShape klasy kształtu.  
  
    2. W **mapy Dekoratora** karcie **szczegóły języka DSL** wybrane okno za pomocą łącznika mapy, sprawdź NameDecorator i ustawić **Właściwość wyświetlania** nazwy.  
  
5. Utwórz łącznik do wyświetlania relacji między osoby i miast.  
  
    1. Przeciągnij łącznika z przybornika do diagramu. Zmień jej nazwę, a następnie ustaw jego właściwości wyglądu.  
  
    2. Użyj **mapowanie elementu diagramu** narzędzie, aby połączyć nowy łącznik do relacji między miejscowości i osoby.  
  
         ![Definicja drzewa rodziny o mapowanie kształtów dodano](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")  
  
6. Utworzyć element narzędzie do tworzenia nowych miast.  
  
    1. W **Eksplorator DSL**, rozwiń węzeł **edytora** następnie **karty przybornika**.  
  
    2. Kliknij prawym przyciskiem myszy  *\<DSL >* a następnie kliknij przycisk **dodać nowe narzędzie elementu**.  
  
    3. Ustaw **nazwa** właściwość nowego narzędzia i zestaw jej **klasy** właściwość miejscowości.  
  
    4. Ustaw **ikonę przybornika** właściwości. Kliknij przycisk **[...]**  i **nazwy pliku** wybierz plik ikony.  
  
7. Utwórz łącznik narzędzie do tworzenia łącza między miast i osób.  
  
    1. Kliknij prawym przyciskiem myszy  *\<DSL >* a następnie kliknij przycisk **dodać nowe narzędzie łącznika**.  
  
    2. Ustaw właściwość Nazwa nowego narzędzia.  
  
    3. W **elementu ConnectionBuilder** właściwości, wybierz konstruktora, który zawiera nazwę relacji miasta osoby.  
  
    4. Ustaw **ikonę przybornika**.  
  
8. Kliknij pozycję Zapisz definicję DSL **Przekształć wszystkie szablony**, a następnie naciśnij klawisz **F5**.  
  
9. W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otwórz plik modelu testu. Użycie nowych narzędzi do tworzenia miast i łącza między miast i osób. Należy zauważyć, że tylko można tworzyć łącza między poprawne typy elementu.  
  
10. Tworzenie kodu, który zawiera miejscowości, w którym znajduje się każda osoba. Szablony tekstowe są jednym z miejsc, gdzie można uruchomić tego kodu. Na przykład można zmodyfikować istniejący plik Sample.tt w rozwiązaniu do debugowania, tak, aby zawierała następujący kod:  
  
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
  
     Podczas zapisywania pliku *.tt utworzy plik pomocniczy, który zawiera listę osób i miejsc ich zamieszkania. Aby uzyskać więcej informacji, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Sprawdzanie poprawności i polecenia  
 Dalsze tego języka DSL można rozwijać, dodając ograniczenia sprawdzania poprawności. Te ograniczenia są metody, które można zdefiniować, które upewnij się, że model jest w poprawnym stanie. Na przykład można zdefiniować ograniczenie, aby upewnić się, że, Data urodzenia dziecka jest późniejsza niż jego elementów nadrzędnych. Funkcję weryfikacji zostanie wyświetlone ostrzeżenie, jeśli użytkownik DSL próbuje zapisać modelu, który przerywa żadne ograniczenia. Aby uzyskać więcej informacji, zobacz [weryfikacji języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md).  
  
 Można również zdefiniować polecenia menu, które użytkownik może wywołać. Polecenia można modyfikować modelu. Może również korzystać z innych modeli w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oraz z zasobami zewnętrznymi. Aby uzyskać więcej informacji, zobacz [jak: Modyfikowanie standardowego polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Wdrażanie język DSL  
 Aby umożliwić innym użytkownikom korzystanie z języka specyficznego dla domeny, rozpowszechniać [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pliku rozszerzenie (VSIX). Zostanie on utworzony podczas kompilowania rozwiązania DSL.  
  
 Zlokalizuj plik .vsix w folder bin rozwiązania. Skopiuj go do komputera, na którym chcesz go zainstalować. Na tym komputerze kliknij dwukrotnie plik VSIX. Język DSL może służyć we wszystkich wystąpieniach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na tym komputerze.  
  
 Można użyć tej samej procedury, aby zainstalować język DSL na swoim komputerze, tak aby nie trzeba używać doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="Reset"></a> Usuwanie starego eksperymentalne językami DSL  
 Jeśli zostały utworzone języków eksperymentalnych DSL nie są już potrzebne, Usuń z komputera poprzez zresetowanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wystąpienie eksperymentalne.  
  
 Spowoduje to usunięcie z komputera wszystkie eksperymentalne językami DSL i inne eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia. Są to rozszerzenia, które zostały wykonane w trybie debugowania.  
  
 Ta procedura nie powoduje usunięcia języków DSL lub inne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeń, które zostały w pełni zainstalowane przez wykonanie pliku VSIX.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Aby zresetować wystąpienie eksperymentalne programu Visual Studio  
  
1. Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, **Microsoft Visual Studio 2010 SDK**, **narzędzia**, a następnie **resetowania firmy Microsoft Wystąpienie programu Visual Studio 2010 eksperymentalne**.  
  
2. Ponownie skompiluj żadnych języków eksperymentalnych DSL lub inne eksperymentalne [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzeń, które nadal chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Objaśnienie modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)   
 [Jak zdefiniować języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   
 [Visualizaton i modelowania SDK](http://go.microsoft.com/fwlink/?LinkID=186128)
