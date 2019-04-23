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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e06317aa91cf71d109a2e90bc955aa28cc4b4903
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101863"
---
# <a name="customizing-tools-and-the-toolbox"></a>Dostosowywanie narzędzi i przybornika

Zdefiniuj elementy przybornika dla elementów, które chcesz powiadomić użytkowników, Dodaj do swoich modeli. Istnieją dwa rodzaje tools: narzędzia elementu i narzędzi do nawiązywania połączenia. W wygenerowanym projektancie użytkownika można wybrać narzędzie elementu przeciągnij kształty do diagramu, a narzędzie połączenia, aby narysować łącza między kształtami można wybrać. Ogólnie rzecz biorąc narzędzi elementów zezwolić użytkownikom na dodawanie wystąpień klas domeny do swoich modeli i narzędzi do nawiązywania połączenia pozwolić im na dodawanie wystąpienia relacji domeny.

## <a name="ToolboxDef"></a> Jak jest zdefiniowany przybornika
 W Eksploratorze DSL rozwiń węzeł edytora i węzły podrzędne. Zazwyczaj zobaczysz hierarchii, która jest podobny do tego:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

W tej części Eksplorator DSL możesz wykonywać następujące czynności:

- Utwórz nowe karty. Karty zdefiniować nagłówki sekcji w przyborniku.

- Tworzenie nowych narzędzi.

- Skopiuj i Wklej narzędzia.

- Przenieś narzędzia w górę lub w dół na liście.

- Usuń karty i narzędzi.

> [!IMPORTANT]
> Aby dodać lub wkleić elementy w Eksplorator DSL, kliknij prawym przyciskiem myszy pokolenia nowego węzła. Na przykład, aby dodać narzędzia, kliknij prawym przyciskiem myszy kartę, a nie **narzędzia** węzła. Aby dodać kartę, kliknij prawym przyciskiem myszy **edytora** węzła.

**Ikonę przybornika** właściwości każdego narzędzia odwołuje się do pliku mapy bitowej 16 x 16. Pliki te są zwykle przechowywane w **Dsl\Resources** folderu.

**Klasy** właściwość narzędzia element odwołuje się do klasy konkretnej domeny. Domyślnie narzędzie utworzy wystąpienia tej klasy. Jednakże można napisać kod do narzędzia tworzenia grup elementów lub elementów o różnych typach.

**Konstruktora połączeń** właściwości narzędzia połączenia odwołuje się do konstruktora połączeń, który definiuje, jakie rodzaje elementów można połączyć w narzędziu i w jakich relacje między nimi. Konstruktory połączeń są definiowane jako węzły w Eksploratorze DSL. Konstruktory połączeń są tworzone automatycznie, gdy zdefiniujesz relacje domeny, ale można napisać kod, aby dostosować je.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Aby dodać narzędzie do przybornika

1. Po utworzeniu klasy kształt i mechanizmowi klasy domeny, zazwyczaj utworzyć narzędzie elementu.

     Po utworzeniu klasy łącznika i mechanizmowi relacja odwołania, zwykle utworzyć narzędzia Łącznik.

2. W Eksploratorze DSL rozwiń **edytora** węzła i **karty przybornika** węzła.

     Kliknij prawym przyciskiem myszy węzeł kartę przybornika, a następnie kliknij przycisk **dodać nowe narzędzie Element** lub **dodać nowe narzędzie połączenia**.

3. Ustaw **ikonę przybornika** właściwości do odwoływania się do mapy bitowej 16 x 16.

     Jeśli chcesz zdefiniować nową ikonę, Utwórz plik mapy bitowej w Eksploratorze rozwiązań w **Dsl\Resources** folderu. Ten plik powinien zawierać następujące wartości właściwości: **Akcja kompilacji** = **zawartości**; **Kopiuj do katalogu wyjściowego** = **nie Kopiuj**.

4. **Dla narzędzia elementu:** Ustaw **klasy** właściwości narzędzia do odwoływania się do klasy konkretnej domeny, która jest mapowana na kształt.

     **Aby uzyskać narzędzie łącznika:** Ustaw **konstruktora połączeń** właściwości narzędzia do jednego z elementów, które są oferowane na liście rozwijanej. Konstruktory połączeń są tworzone automatycznie podczas mapowania łącznik do relacji domeny. Jeśli niedawno po utworzeniu łącznika, będą zazwyczaj wybiera się konstruktora skojarzone z nimi połączenie.

5. Aby przetestować język DSL, naciśnij klawisz F5 lub CTRL + F5, a w doświadczalnym wystąpieniu programu Visual Studio, Otwórz przykładowy plik modelu. Nowe narzędzie powinna zostać wyświetlona w przyborniku. Przeciągnij go na diagram, aby sprawdzić, czy tworzy nowy element.

     Jeśli nie ma narzędzia, należy zatrzymać eksperymentalne programu Visual Studio. W Windows **Start** menu, uruchom **Zresetuj wystąpienie eksperymentalne programu Microsoft Visual Studio 2010**. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Następnie ponownie przetestuj język DSL.

## <a name="customizing"></a> Narzędzia dostosowywania elementów
 Domyślnie narzędzie utworzy jedno wystąpienie określonej klasy, ale można wybrać różne na dwa sposoby:

- Zdefiniuj dyrektywy scalania elementów w innych klas, umożliwiające im na akceptowanie nowe wystąpienia tej klasy, a następnie utwórz dodatkowe linki, po utworzeniu nowego elementu. Można na przykład umożliwia użytkownikowi Dodaj komentarz do innego elementu, a przez to tworzyć łącza między tymi dwoma.

     Te modyfikacje również wpływać na, co się stanie po użytkownik wkleja przeciągnie lub porzuca element.

     Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).

- Napisz kod, aby dostosować narzędzie, dzięki czemu może utworzyć grupy elementów. Narzędzie jest inicjowany za pomocą metod ToolboxHelper.cs, którą można przesłonić. Aby uzyskać więcej informacji, zobacz [tworzenia grup z elementów przy użyciu narzędzia](#groups).

## <a name="groups"></a> Tworzenie grup elementów przy użyciu narzędzia
 Każde narzędzie element zawiera prototyp elementów, które należy utworzyć. Domyślnie każde narzędzie element tworzy pojedynczy element, ale jest również można utworzyć grupy powiązanych obiektów za pomocą jednego narzędzia. Aby to zrobić, należy zainicjować narzędzia z <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> zawierający elementy pokrewne.

 Poniższy przykład jest pobierana z DSL, w którym jest typem tranzystor. Każdy tranzystor ma trzy terminale nazwanych. Narzędzie elementu dla tranzystory przechowuje prototyp zawierający cztery elementy modelu i trzy łącza relacji. Gdy użytkownik przeciągnie narzędzie na diagram, prototyp jest tworzone i połączone do korzenia modelu.

 Ten kod zastępuje metodę, która jest zdefiniowana w **Dsl\GeneratedCode\ToolboxHelper.cs**.

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

## <a name="connections"></a> Dostosowywanie narzędzi do nawiązywania połączenia
 Zazwyczaj należy utworzyć narzędzia elementu, po utworzeniu nowej klasy łącznika. Alternatywnie możesz doprowadzić do przeciążenia jedno narzędzie, umożliwiając typy po obu stronach w celu określenia typu relacji. Na przykład można zdefiniować jedno narzędzie połączenia, który można utworzyć relacji osoby osoby i relacje miasta osoby.

 Narzędzia połączeń wywoływać konstruktory połączeń. Konstruktory połączeń umożliwia określenie, jak użytkownicy mogą tworzyć połączenia elementów w wygenerowanym projektancie. Konstruktory połączeń określić elementy, które mogą być połączone i rodzaju łącza, który jest tworzony między nimi.

 Konstruktor połączeń jest tworzony automatycznie podczas tworzenia relacji między klasami domeny. Podczas mapowania narzędzia połączenia, można użyć tego konstruktora połączeń. Aby uzyskać więcej informacji o sposobie tworzenia połączenia narzędzi, zobacz [Konfigurowanie przybornika](../modeling/customizing-tools-and-the-toolbox.md).

 Można zmodyfikować domyślnego konstruktora połączeń, dzięki czemu mogą dotyczyć szereg różnych typami źródłowym i docelowym i tworzyć różne typy relacji.

 Można również napisać niestandardowy kod konstruktory połączeń określić klas źródłowych i docelowych dla połączenia, zdefiniuj typ połączenia, które ma zostać wykonane i wykonywać inne czynności związane z tworzeniem połączenia.

### <a name="the-structure-of-connection-builders"></a>Struktura konstruktory połączeń
 Konstruktory połączeń zawiera jeden lub więcej łączy Połącz dyrektyw, które określają relacji domeny i elementy źródłowe i docelowe. Na przykład w szablonie przepływu zadań rozwiązania widać **CommentReferencesSubjectsBuilder** w **Eksplorator DSL**. Ten konstruktor połączeń zawiera jedno łącze połączyć dyrektywy o nazwie **CommentReferencesSubjects**, która jest mapowana do relacji domeny **CommentReferencesSubjects**. Połącz ten link dyrektywa zawiera dyrektywy roli źródła, który wskazuje na `Comment` klasy domeny i dyrektywą docelową roli, który wskazuje na `FlowElement` klasy domeny.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Przy użyciu konstruktory połączeń, aby ograniczyć źródła i określania elementów docelowych ról
 Konstruktory połączeń można użyć do ograniczenia wystąpienia niektórych klas w roli źródłowej lub rola docelowa relacji danej domeny. Na przykład masz bazową klasę domeny mającej relację domeny do innej klasy domeny, ale nie ma wszystkie klasy pochodne klasy bazowej, aby te same role w tej relacji. W rozwiązaniu przepływu zadań są cztery klasy konkretnej domeny (**punktu StartPoint**, **punktu końcowego**, **MergeBranch**, i **synchronizacji**) dziedziczyć bezpośrednio klasy abstrakcyjnej domeny **FlowElement**, i dwie klasy domeny (**zadań** i **ObjectInState**), dziedziczyć pośrednio go. Istnieje również **przepływu** odwoływać się do relacji, który przyjmuje **FlowElement** klasy domeny w jego roli źródłowej i docelowej roli. Jednak wystąpienie **punktu końcowego** klasy domeny nie powinny być źródło wystąpienie **przepływu** relacji, ani nie powinna wystąpienie **punktu StartPoint** można klasy docelowym wystąpienia **przepływu** relacji. **FlowBuilder** Konstruktor połączeń ma link połączyć dyrektywy o nazwie **przepływu** , który określa klas domeny, które mogą pełnić roli źródłowej (**zadań**,  **MergeBranch**, **punktu StartPoint**, i **synchronizacji**) i które mogą pełnić rolę docelową (**MergeBranch**,  **Punkt końcowy**, i **synchronizacji**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Konstruktory połączeń przy użyciu wielu Linku dyrektywy łączenia
 Możesz dodać więcej niż jednego połączenia dyrektywa łączenia do konstruktora połączeń. Może to ułatwić ukryć niektóre komplikacje związane z modelu domeny od użytkowników i zachować **przybornika** zbyt uniknąć. Możesz dodać łącze dyrektywy dla kilka relacji z inną domeną nawiązać połączenie z konstruktora jednego połączenia. Jednak należy połączyć relacje domeny, gdy wykonują tę samą funkcję.

 W rozwiązaniu przepływu zadań **przepływu** narzędzia połączenia jest używany do rysowania oba wystąpienia **przepływu** i **przejścia przepływu obiektu** relacji domeny. **FlowBuilder** Konstruktor połączeń ma dodatkowo do **przepływu** opisanej wcześniej dyrektywa łączenia linku, o nazwie dyrektywy łączenia linku dwóch **przejścia przepływu obiektu**. Te dyrektywy określić, że wystąpienie **przejścia przepływu obiektu** relacji mogą pochodzić między wystąpieniami **ObjectInState** klasy domeny lub z wystąpienia **ObjectInState**  do wystąpienia **zadań**, ale nie między dwoma rodzajami **zadań**, lub z wystąpienia programu **zadań** na wystąpienie **ObjectInState**. Jednak wystąpienie **przepływu** relacji może być rysowany między dwoma rodzajami **zadań**. Jeśli skompilować i uruchomić rozwiązanie przepływu zadań, możesz zobaczyć ten rysunek **przepływu** z wystąpienia programu **ObjectInState** do wystąpienia **zadań** tworzy wystąpienie klasy **Przejścia przepływu obiektu**, ale rysowania **przepływu** między dwoma rodzajami **zadań** tworzy wystąpienie **przepływu**.

### <a name="custom-code-for-connection-builders"></a>Niestandardowy kod konstruktory połączeń
 Istnieją cztery pola wyboru w interfejsie użytkownika, określające różnego rodzaju dostosowanie konstruktory połączeń:

- **akceptowanie niestandardowe** pole wyboru w dyrektywie roli źródłowej lub docelowej

- **niestandardowe połączenia** pole wyboru w dyrektywie roli źródłowej lub docelowej

- **używa niestandardowych connect** pole wyboru w dyrektywie connect

- **jest niestandardowa** właściwości konstruktora połączeń

  Należy podać niektóre kodu programu, aby wykonać te dostosowania. Aby sprawdzić, jaki kod, musisz podać, zaznacz jeden z tych pól, kliknij Przekształć wszystkie szablony, a następnie Skompiluj rozwiązanie. Powoduje, że raport o błędach. Kliknij dwukrotnie raport o błędach można wyświetlić komentarz, który objaśnia, jaki kod należy dodać.

> [!NOTE]
>  Aby dodać niestandardowy kod, Utwórz definicję klasy częściowej w pliku kodu niezależnie od plików kodu w folderach GeneratedCode. Aby uniknąć utraty wyników pracy, nie należy edytować pliki wygenerowanego kodu. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Tworzenie połączenia niestandardowego kodu
 W każdym odnośniku dyrektywa, łączenia **dyrektywy ról źródłowych** definiuje kartę co typów można przeciągnąć. Podobnie **dyrektywy ról docelowych** definiuje kartę co typów można przeciągnąć. Dla każdego typu, możesz podać, czy zezwolić na połączenia (dla dyrektywy łączenia tego linku), ustawiając **akceptowanie niestandardowe** Flaga, a następnie podając dodatkowego kodu.

 Można również dostosować, co występuje, gdy połączenie zostało nawiązane. Na przykład, można dostosować tylko przypadku realizowana przeciąganie z konkretną klasą lub połączyć tego jedno łącze wszystkie przypadki dyrektywy decyduje, lub całego FlowBuilder konstruktora połączeń. Dla każdej z tych opcji można ustawić flagi niestandardowe na odpowiednim poziomie. Gdy Transformuj wszystkie szablony i spróbował to zbudować rozwiązanie, komunikaty o błędach kierować do komentarzy, które znajdują się w wygenerowanym kodzie. Te komentarze identyfikują, należy podać.

 W tym przykładzie Diagram składników konstruktora połączeń dla relacji domeny połączenia jest dostosowany do ograniczenia połączeń, które mogą być pomylone portów. Na poniższej ilustracji przedstawiono, że połączenia można tworzyć tylko z `OutPort` elementów `InPort` elementów, ale można zagnieżdżać składniki wewnątrz siebie nawzajem.

 **Połączeń przychodzących na elementu OutPort zagnieżdżonych składników**

 ![Konstruktor połączeń](../modeling/media/connectionbuilder_3.png)

 W związku z tym można określić, że połączenia mogą pochodzić z zagnieżdżonych składników do elementu OutPort. Aby określić takie połączenie, należy ustawić **używa akceptowanie niestandardowe** na **InPort** typ jako roli źródłowej i **elementu OutPort** typ jako rolę docelową w **szczegóły języka DSL**  okna, jak pokazano na poniższych ilustracjach:

 **Dyrektywa w Eksplorator DSL łączenia linku**

 ![Obraz przedstawiający konstruktora połączeń](../modeling/media/connectionbuilder_4a.png)

 **Dyrektywa w oknie Szczegóły języka DSL łączenia linku**

 ![](../modeling/media/connectionbuilder_4b.png)

 Następnie należy podać metody w klasie elementu ConnectionBuilder:

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

 Podobny kod, można użyć na przykład, aby uniemożliwić użytkownikom tworzenie pętli za pomocą łącza nadrzędny podrzędny. Te ograniczenia są traktowane jako ograniczenia "twarde", ponieważ użytkownicy nie mogą naruszyć ich w dowolnym momencie. Można również utworzyć sprawdzanie poprawności "elastyczne", które użytkownicy mogą tymczasowo obejść, tworząc nieprawidłowe konfiguracje, których nie można zapisać.

### <a name="good-practice-in-defining-connection-builders"></a>Dobrym rozwiązaniem w definiowaniu konstruktory połączeń
 Należy zdefiniować jedną konstruktora połączeń, aby utworzyć różne typy relacji, tylko wtedy, gdy są koncepcyjnie powiązane. W tym przykładzie przepływu zadań umożliwia ten sam Konstruktor tworzenie przepływów między zadaniami, a także między zadaniami i obiektów. Jednakże może być mylące, tworzyć relacje między komentarze i zadań za pomocą tego samego konstruktora.

 Jeśli zdefiniujesz konstruktora połączeń dla wielu typów relacji, należy upewnić się, że nie są zgodne więcej niż jeden typ z tej samej pary obiektów źródłowych i docelowych. W przeciwnym razie wyniki są nieprzewidywalne.

 Użyj niestandardowego kodu, aby zastosować ograniczenia "twarde", ale należy rozważyć, czy użytkownicy powinien móc tymczasowo wprowadzać nieprawidłowe połączeń. Jeśli te powinny ograniczenia można zmodyfikować tak, aby połączenia nie są weryfikowane, dopóki użytkownicy próbują zapisać zmiany.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Przykładowe diagramy obwodu DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)