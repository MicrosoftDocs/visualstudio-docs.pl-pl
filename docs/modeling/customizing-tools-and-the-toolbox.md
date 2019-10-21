---
title: Dostosowywanie narzędzi i przybornika
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75e3a791fc53f7a1e9ff093cc46e3d73003417cf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653952"
---
# <a name="customizing-tools-and-the-toolbox"></a>Dostosowywanie narzędzi i przybornika

Należy zdefiniować elementy przybornika dla elementów, które chcesz zezwolić użytkownikom na dodawanie ich do modeli. Istnieją dwa rodzaje narzędzi: narzędzia elementów i narzędzia do nawiązywania połączeń. W wygenerowanym projektancie użytkownik może wybrać narzędzie elementu, aby przeciągnąć kształty do diagramu i można wybrać narzędzie połączenia do rysowania linków między kształtami. Ogólnie rzecz biorąc, elementy Tools pozwalają użytkownikom dodawać wystąpienia klas domeny do ich modeli, a narzędzia połączenia pozwalają im dodawać wystąpienia relacji domeny.

## <a name="ToolboxDef"></a>Sposób definiowania przybornika
 W Eksploratorze DSL rozwiń węzeł Edytor i węzły znajdujące się poniżej. Zwykle zostanie wyświetlona hierarchia podobna do poniższego:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

W tej części Eksploratora DSL można:

- Utwórz nowe karty. Tabulatory definiują nagłówki sekcji w przyborniku.

- Utwórz nowe narzędzia.

- Narzędzia do kopiowania i wklejania.

- Przenoszenie narzędzi w górę lub w dół na liście.

- Usuń karty i narzędzia.

> [!IMPORTANT]
> Aby dodać lub wkleić elementy w Eksploratorze DSL, kliknij prawym przyciskiem myszy nowy węzeł. Na przykład, aby dodać narzędzie, kliknij prawym przyciskiem myszy kartę, a nie węzeł **Narzędzia** . Aby dodać kartę, kliknij prawym przyciskiem myszy węzeł **Edytor** .

Właściwość **ikony przybornika** każdego narzędzia odwołuje się do pliku mapy bitowej. Te pliki są zwykle przechowywane w folderze **Dsl\Resources** .

Właściwość **Class** narzędzia elementu odwołuje się do konkretnej klasy domeny. Domyślnie Narzędzie utworzy wystąpienia tej klasy. Można jednak napisać kod, aby narzędzie utworzyło grupy elementów lub elementy różnych typów.

Właściwość **konstruktora połączeń** narzędzia połączenia odwołuje się do konstruktora połączeń, który definiuje, jakie typy elementów może połączyć narzędzie i jakie relacje tworzy między nimi. Konstruktory połączeń są zdefiniowane jako węzły w Eksploratorze DSL. Konstruktory połączeń są tworzone automatycznie podczas definiowania relacji domeny, ale można napisać kod, aby dostosować je.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Aby dodać narzędzie do przybornika

1. Zwykle można utworzyć narzędzie elementu po utworzeniu klasy kształtu i zamapowaniu jej do klasy domeny.

     Zazwyczaj można utworzyć narzędzie łącznika po utworzeniu klasy łącznika i zamapowaniu jej do relacji odwołania.

2. W Eksploratorze DSL rozwiń węzeł **Edytor** , a następnie węzeł **karty przybornik** .

     Kliknij prawym przyciskiem myszy węzeł karty przybornika, a następnie kliknij polecenie **Dodaj nowy element** lub **Dodaj nowe narzędzie połączenia**.

3. Ustaw właściwość **ikona przybornika** , aby odwołać się do mapy bitowej 16x16.

     Jeśli chcesz zdefiniować nową ikonę, Utwórz plik mapy bitowej w Eksplorator rozwiązań w folderze **Dsl\Resources** . Plik powinien mieć następujące wartości właściwości: **Akcja kompilacji**  = **zawartość**; **Kopiuj do katalogu wyjściowego**  = **nie Kopiuj**.

4. **Dla narzędzia elementu:** Ustaw właściwość **Class** narzędzia, aby odwoływać się do konkretnej klasy domeny, która jest zmapowana do kształtu.

     **Dla narzędzia łącznika:** Ustaw właściwość **Konstruktor połączeń** dla narzędzia na jeden z elementów oferowanych na liście rozwijanej. Konstruktory połączeń są tworzone automatycznie podczas mapowania łącznika do relacji domeny. Jeśli niedawno utworzono łącznik, zazwyczaj wybierz skojarzony Konstruktor połączeń.

5. Aby przetestować DSL, naciśnij klawisz F5 lub CTRL + F5 i w eksperymentalnym wystąpieniu programu Visual Studio Otwórz przykładowy plik modelu. Nowe narzędzie powinno pojawić się w przyborniku. Przeciągnij go na diagram, aby sprawdzić, czy tworzy nowy element.

     Jeśli narzędzie nie jest wyświetlane, Zatrzymaj eksperymentalny program Visual Studio. W menu **Start** systemu Windows uruchom polecenie **Zresetuj wystąpienie eksperymentalne Microsoft Visual Studio 2010**. W menu **kompilacja** kliknij polecenie **Kompiluj ponownie rozwiązanie**. Następnie ponownie przetestuj DSL.

## <a name="customizing"></a>Dostosowywanie narzędzi elementów
 Domyślnie Narzędzie utworzy pojedyncze wystąpienie określonej klasy, ale można to zmienić na dwa sposoby:

- Zdefiniuj dyrektywy scalania elementów dla innych klas, umożliwiając im akceptowanie nowych wystąpień tej klasy i umożliwienie im tworzenia dodatkowych linków po utworzeniu nowego elementu. Na przykład można zezwolić użytkownikowi na porzucenie komentarza do innego elementu, a tym samym utworzyć łącze odwołania między nimi.

     Te dostosowania wpływają również na to, co się dzieje, gdy użytkownik wklei lub przewinie i porzuca element.

     Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).

- Napisz kod w celu dostosowania tego narzędzia, aby można było tworzyć grupy elementów. Narzędzie jest inicjowane przez metody w ToolboxHelper.cs, które można przesłonić. Aby uzyskać więcej informacji, zobacz [Tworzenie grup elementów za pomocą narzędzia](#groups).

## <a name="groups"></a>Tworzenie grup elementów za pomocą narzędzia
 Każdy element narzędzia zawiera prototyp elementów, które powinny być tworzone. Domyślnie każde narzędzie elementu tworzy pojedynczy element, ale można również utworzyć grupę powiązanych obiektów przy użyciu jednego narzędzia. W tym celu należy zainicjować narzędzie za pomocą <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>, które zawiera powiązane elementy.

 Poniższy przykład jest pobierany z linii DSL, w której istnieje tranzystor typu. Każdy tranzystor ma trzy nazwane terminale. Narzędzie elementu dla tranzystorów przechowuje prototyp zawierający cztery elementy modelu i trzy linki relacji. Gdy użytkownik przeciągnie narzędzie na diagram, zostanie utworzone wystąpienie prototypu i połączone z głównym modelem.

 Ten kod przesłania metodę, która jest zdefiniowana w **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }
```

## <a name="connections"></a>Dostosowywanie narzędzi do połączeń
 Zazwyczaj tworzysz narzędzie elementu podczas tworzenia nowej klasy łącznika. Alternatywnie można przeciążyć jedno narzędzie, zezwalając na typy dwóch punktów końcowych, aby określić typ relacji. Można na przykład zdefiniować jedno narzędzie połączenia, które może utworzyć relacje między osobami i osobami.

 Narzędzia połączeń wywołują konstruktory połączeń. Użyj konstruktorów połączeń, aby określić, jak użytkownicy mogą łączyć elementy w wygenerowanym projektancie. Konstruktory połączeń określają elementy, które mogą być połączone, oraz rodzaj linku, który jest tworzony między nimi.

 Podczas tworzenia relacji odwołania między klasami domen automatycznie tworzony jest Konstruktor połączeń. Tego konstruktora połączeń można użyć podczas mapowania narzędzia połączenia. Aby uzyskać więcej informacji o sposobach tworzenia narzędzi do nawiązywania połączeń, zobacz [Konfigurowanie przybornika](../modeling/customizing-tools-and-the-toolbox.md).

 Można zmodyfikować domyślnego konstruktora połączeń, aby mógł on zająć się innym zakresem typów źródłowych i docelowych oraz utworzyć różne typy relacji.

 Możesz również napisać niestandardowy kod dla konstruktorów połączeń, aby określić klasy źródłową i docelową dla połączenia, zdefiniować typ połączenia, który ma zostać utworzony, i wykonać inne akcje związane z tworzeniem połączenia.

### <a name="the-structure-of-connection-builders"></a>Struktura konstruktorów połączeń
 Konstruktory połączeń zawierają co najmniej jedną dyrektywę łączenia linków, która określa relację domeny i elementy źródłowe i docelowe. Na przykład w szablonie rozwiązania przepływu zadań można zobaczyć **CommentReferencesSubjectsBuilder** w **Eksploratorze DSL**. Ten Konstruktor połączeń zawiera jedną dyrektywę Connect link o nazwie **CommentReferencesSubjects**, która jest mapowana na relację domeny **CommentReferencesSubjects**. Ta dyrektywa łączenia linków zawiera dyrektywę z rolą źródłową, która wskazuje na klasę domeny `Comment` i dyrektywę docelową, która wskazuje na klasę `FlowElement` domeny.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Używanie konstruktorów połączeń do ograniczania ról źródłowych i docelowych
 Można użyć konstruktorów połączeń, aby ograniczyć wystąpienia niektórych klas w roli źródłowej lub roli docelowej danej relacji domeny. Na przykład może istnieć podstawowa klasa domeny, która ma relację domeny z inną klasą domeny, ale nie wszystkie klasy pochodne klasy bazowej mogą mieć te same role w tej relacji. W rozwiązaniu przepływu zadań istnieją cztery konkretne klasy domeny (**StartPoint**, **Endpoint**, **MergeBranch**i **Synchronization**), które dziedziczą bezpośrednio ze abstrakcyjnej klasy " **FlowElement**" i dwie konkretne klasy domeny (**Task** i **ObjectInState**) dziedziczące pośrednio od niej. Istnieje również relacja odwołania do **przepływu** , która przyjmuje klasy domeny **FlowElement** zarówno w roli źródłowej, jak i roli docelowej. Niemniej jednak wystąpienie klasy domeny **punktu końcowego** nie powinno być źródłem wystąpienia relacji **przepływu** ani nie powinno być wystąpienie klasy **StartPoint** jako obiekt docelowy wystąpienia relacji **przepływu** . Konstruktor **połączeń FlowBuilder** ma dyrektywę Connect link o nazwie **Flow** , która określa, które klasy domeny mogą odtwarzać rolę źródłową (**Task**, **MergeBranch**, **StartPoint**i **Synchronization**), a które może odtworzyć rolę docelową (**MergeBranch**, **punkt końcowy**i **Synchronizacja**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Konstruktory połączeń z wieloma dyrektywami łączenia linków
 Do konstruktora połączeń można dodać więcej niż jedną dyrektywę łączenia linku. Może to pomóc w ukryciu niektórych złożoności modelu domeny od użytkowników i uniemożliwić zbyt bałaganie **przybornika** . Można dodać dyrektywy łączenia linków dla kilku różnych relacji domeny do konstruktora jednego połączenia. Należy jednak połączyć relacje domeny, gdy wykonują one w przybliżeniu tę samą funkcję.

 W rozwiązaniu przepływu zadań narzędzie połączenia **Flow** służy do rysowania wystąpień zarówno **przepływu** , jak i relacji domeny **ObjectFlow** . Konstruktor połączeń **FlowBuilder** ma oprócz dyrektywy **Flow** link Connect opisanej wcześniej dwie dyrektywy łączenia linków o nazwie **ObjectFlow**. Te dyrektywy określają, że wystąpienie relacji **ObjectFlow** może być rysowane między wystąpieniami klasy domeny **ObjectInState** lub z wystąpienia **ObjectInState** do wystąpienia **zadania**, ale nie między dwoma wystąpienia **zadania**lub z wystąpienia **zadania** do wystąpienia elementu **ObjectInState**. Jednak wystąpienie relacji **przepływu** może być rysowane między dwoma wystąpieniami **zadania**. W przypadku kompilowania i uruchamiania rozwiązania przepływu zadań można zobaczyć, że narysowanie **przepływu** z wystąpienia **ObjectInState** do wystąpienia **zadania** tworzy wystąpienie elementu **ObjectFlow**, ale narysowanie **przepływu** między dwoma wystąpieniami **zadania** tworzy wystąpienie **przepływu**.

### <a name="custom-code-for-connection-builders"></a>Niestandardowy kod dla konstruktorów połączeń
 W interfejsie użytkownika są cztery pola wyboru, które definiują różne typy dostosowań konstruktorów połączeń:

- pole wyboru **niestandardowa akceptacja** dla dyrektywy źródłowej lub docelowej

- pole wyboru **niestandardowe połączenie** w dyrektywie źródłowej lub docelowej

- pole wyboru **Użyj połączenia niestandardowego** dla dyrektywy Connect

- Właściwość **is Custom** konstruktora połączeń

  Musisz podać kod programu, aby wprowadzić te dostosowania. Aby dowiedzieć się, jaki kod należy podać, zaznacz jedno z tych pól, kliknij przycisk Przekształć wszystkie szablony, a następnie Skompiluj rozwiązanie. Zostanie zwrócony raport o błędach. Kliknij dwukrotnie raport o błędach, aby wyświetlić komentarz wyjaśniający, jaki kod należy dodać.

> [!NOTE]
> Aby dodać kod niestandardowy, Utwórz definicję klasy częściowej w pliku kodu oddzielnym od plików kodu w folderach GeneratedCode. Aby uniknąć utraty pracy, nie należy edytować wygenerowanych plików kodu. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Tworzenie niestandardowego kodu połączenia
 W ramach każdej dyrektywy Connect linku na karcie **dyrektywy roli źródłowej** definiuje się, jakie typy można przeciągać. Podobnie karta **dyrektywy Target role** definiuje, jakie typy można przeciągać. Dla każdego typu można określić, czy zezwolić na połączenie (dla danej dyrektywy łączenia linku) przez ustawienie flagi **Zaakceptuj niestandardową** , a następnie dostarczenie dodatkowego kodu.

 Możesz również dostosować to, co dzieje się w przypadku nawiązywania połączenia. Można na przykład dostosować tylko przypadek, w którym występuje przeciągnięcie, do lub z określonej klasy, wszystkie przypadki, w których dana dyrektywa łącząca link jest zarządzana, lub cały Konstruktor połączeń FlowBuilder. Dla każdej z tych opcji można ustawić flagi niestandardowe na odpowiednim poziomie. Podczas przekształcania wszystkich szablonów i próby skompilowania rozwiązania komunikaty o błędach kierują do komentarzy, które znajdują się w wygenerowanym kodzie. Te komentarze identyfikują, co należy dostarczyć.

 W przykładzie diagramu składników Konstruktor połączeń dla relacji domeny połączenia jest dostosowany do ograniczenia połączeń, które mogą być nawiązywane między portami. Na poniższej ilustracji przedstawiono, że można nawiązać połączenia tylko z `OutPort` elementów do `InPort` elementów, ale można zagnieżdżać składniki wewnątrz siebie.

 **Połączenie przychodzące do elementu zewnętrznego z składnika zagnieżdżonego**

 ![Konstruktor połączeń](../modeling/media/connectionbuilder_3.png)

 W związku z tym możesz chcieć określić, że połączenie może pochodzić z składnika zagnieżdżonego do elementu zewnętrznego. Aby określić takie połączenie, należy ustawić opcję **Użyj niestandardowej akceptacji** dla typu **InPort** jako rola źródłowa i **Typ elementu** głównego jako rolę docelową w oknie **Szczegóły DSL** , jak pokazano na poniższej ilustracji:

 **Dyrektywa łączenia linku w programie DSL Explorer**

 ![Obraz konstruktora połączeń](../modeling/media/connectionbuilder_4a.png)

 **Dyrektywa łączenia linku w oknie szczegółów języka DSL**

 ![Dyrektywa łączenia linku w oknie szczegółów języka DSL](../modeling/media/connectionbuilder_4b.png)

 Następnie należy dostarczyć metody klasy elemencie ConnectionBuilder:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Możesz na przykład użyć podobnego kodu, aby uniemożliwić użytkownikom tworzenie pętli z łączami nadrzędny-podrzędny. Ograniczenia te są uznawane za ograniczenia "twarde", ponieważ użytkownicy nie mogą naruszać ich w dowolnym momencie. Można również utworzyć "miękkie" Sprawdzanie poprawności, które użytkownicy mogą tymczasowo ominąć przez utworzenie nieprawidłowych konfiguracji, których nie mogą zapisać.

### <a name="good-practice-in-defining-connection-builders"></a>Dobre rozwiązanie w zakresie definiowania konstruktorów połączeń
 Należy zdefiniować jeden Konstruktor połączeń do tworzenia różnych typów relacji tylko wtedy, gdy są one koncepcyjnie powiązane. W przykładzie przepływu zadań używasz tego samego konstruktora do tworzenia przepływów między zadaniami, a także między zadaniami i obiektami. Jednak w celu utworzenia relacji między komentarzami i zadaniami można użyć tego samego konstruktora.

 Jeśli zdefiniujesz konstruktora połączeń dla wielu typów relacji, upewnij się, że nie można dopasować więcej niż jednego typu z tej samej pary obiektów źródłowych i docelowych. W przeciwnym razie wyniki będą nieprzewidywalne.

 Używasz niestandardowego kodu do zastosowania ograniczeń "twardości", ale należy zastanowić się, czy użytkownicy powinni mieć możliwość tymczasowego nawiązywania nieprawidłowych połączeń. W razie potrzeby można zmodyfikować ograniczenia tak, aby połączenia nie były sprawdzane, dopóki użytkownicy nie spróbują zapisać zmian.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Diagramy obwodów — przykład DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)