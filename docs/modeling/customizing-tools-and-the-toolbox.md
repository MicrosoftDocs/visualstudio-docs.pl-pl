---
title: Dostosowywanie narzędzi i przybornika
description: Dowiedz się, jak definiować elementy przybornika dla elementów, które chcesz pozwolić użytkownikom dodawać do swoich modeli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 956955a9c2feb9982bee0101965336be2ca29ab7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385815"
---
# <a name="customizing-tools-and-the-toolbox"></a>Dostosowywanie narzędzi i przybornika

Elementy przybornika należy definiować dla elementów, które mają być umożliwiane użytkownikom dodawanie ich do modeli. Istnieją dwa rodzaje narzędzi: narzędzia elementów i narzędzia połączeń. W wygenerowanym projektancie użytkownik może wybrać narzędzie elementu, aby przeciągać kształty do diagramu, i wybrać narzędzie połączenia do narysowania linków między kształtami. Ogólnie rzecz biorąc, narzędzia elementów umożliwiają użytkownikom dodawanie wystąpień klas domen do modeli, a narzędzia połączeń umożliwiają dodawanie wystąpień relacji domeny.

## <a name="how-the-toolbox-is-defined"></a><a name="ToolboxDef"></a> Jak jest zdefiniowany przybornik
 W Eksploratorze DSL rozwiń węzeł Edytor i węzły poniżej. Zazwyczaj zobaczysz hierarchię, która przypomina następującą:

```
Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool
```

W tej części eksploratora DSL można:

- Utwórz nowe karty. Karty definiują nagłówki sekcji w przyborniku.

- Tworzenie nowych narzędzi.

- Narzędzia do kopiowania i wklejania.

- Przenieś narzędzia w górę lub w dół na liście.

- Usuwanie kart i narzędzi.

> [!IMPORTANT]
> Aby dodać lub wkleić elementy w eksploratorze DSL, kliknij prawym przyciskiem myszy element grandparent nowego węzła. Aby na przykład dodać narzędzie, kliknij prawym przyciskiem myszy kartę, a nie **węzeł** Narzędzia. Aby dodać kartę, kliknij prawym przyciskiem myszy węzeł **Edytor.**

Właściwość **Ikona przybornika** każdego narzędzia odwołuje się do pliku mapy bitowej 16x16. Te pliki są zwykle przechowywane w **folderze Dsl\Resources.**

Właściwość **Class** narzędzia elementu odwołuje się do konkretnej klasy domeny. Domyślnie narzędzie tworzy wystąpienia tej klasy. Można jednak napisać kod, aby narzędzie tworzyło grupy elementów lub elementy różnych typów.

Właściwość **Konstruktor połączeń** narzędzia połączenia odnosi się do konstruktora połączeń, który definiuje typy elementów, które narzędzie może połączyć, oraz relacje między nimi. Konstruktory połączeń są definiowane jako węzły w eksploratorze DSL. Konstruktory połączeń są tworzone automatycznie podczas definiowania relacji domeny, ale można napisać kod, aby je dostosować.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Aby dodać narzędzie do przybornika

1. Zazwyczaj narzędzie elementu jest tworzone po utworzeniu klasy kształtu i zamapowania jej na klasę domeny.

     Narzędzie łącznika jest zazwyczaj tworzone po utworzeniu klasy łącznika i zamapowania jej na relację referencyjną.

2. W Eksploratorze DSL rozwiń węzeł **Edytor** i węzeł **Karty przybornika.**

     Kliknij prawym przyciskiem myszy węzeł karty przybornika, a następnie kliknij polecenie Dodaj nowy **element Tool** lub Dodaj nowe **narzędzie połączenia.**

3. Ustaw właściwość **Ikona przybornika,** aby odwoływać się do mapy bitowej 16x16.

     Jeśli chcesz zdefiniować nową ikonę, utwórz plik mapy bitowej w folderze Eksplorator rozwiązań **w folderze Dsl\Resources.** Plik powinien mieć następujące wartości właściwości: **Zawartość akcji**  =  **kompilacji;** **Kopiowanie do katalogu wyjściowego**  =  **Nie kopiuj pliku**.

4. **Dla narzędzia elementu:** Ustaw właściwość **Class** narzędzia tak, aby odwoływał się do konkretnej klasy domeny, która jest mapowana na kształt.

     **W przypadku narzędzia łącznika:** Ustaw właściwość **Connection Builder** narzędzia na jeden z elementów, które są oferowane na liście rozwijanej. Konstruktory połączeń są tworzone automatycznie podczas mapowania łącznika na relację domeny. Jeśli niedawno utworzono łącznik, zazwyczaj wybiera się skojarzonego konstruktora połączeń.

5. Aby przetestować DSL, naciśnij klawisz F5 lub CTRL + F5, a w eksperymentalnym wystąpieniu Visual Studio otwórz przykładowy plik modelu. Nowe narzędzie powinno pojawić się w przyborniku. Przeciągnij go na diagram, aby sprawdzić, czy tworzy nowy element.

     Jeśli narzędzie nie jest wyświetlane, zatrzymaj eksperymentalne Visual Studio. W menu **Start systemu** Windows uruchom polecenie **Resetuj Microsoft Visual Studio 2010 Experimental Instance**. W menu **Build (Kompilacja)** kliknij pozycję **Rebuild Solution (Skompilowanie rozwiązania).** Następnie ponownie przetestuj DSL.

## <a name="customizing-element-tools"></a><a name="customizing"></a> Narzędzia dostosowywania elementów
 Domyślnie narzędzie utworzy pojedyncze wystąpienie określonej klasy, ale można to zmienić na dwa sposoby:

- Zdefiniuj dyrektywy scalania elementów w innych klasach, umożliwiając im akceptowanie nowych wystąpień tej klasy i umożliwiając im tworzenie dodatkowych linków po utworzeniu nowego elementu. Na przykład można zezwolić użytkownikowi na upuszczenie komentarza do innego elementu, a tym samym utworzyć łącze odwołania między nimi.

     Te dostosowania mają również wpływ na to, co się dzieje, gdy użytkownik wkleja lub przeciąga i upuszcza element.

     Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przemieszczania elementów.](../modeling/customizing-element-creation-and-movement.md)

- Napisz kod, aby dostosować narzędzie tak, aby można było tworzyć grupy elementów. Narzędzie jest inicjowane przez metody w przybornikuHelper.cs, które można zastąpić. Aby uzyskać więcej informacji, zobacz Creating Groups of Elements from a Tool (Tworzenie grup [elementów za pomocą narzędzia).](#groups)

## <a name="creating-groups-of-elements-from-a-tool"></a><a name="groups"></a> Tworzenie grup elementów z narzędzia
 Każde narzędzie elementu zawiera prototyp elementów, które należy utworzyć. Domyślnie każde narzędzie elementu tworzy jeden element, ale istnieje również możliwość utworzenia grupy powiązanych obiektów za pomocą jednego narzędzia. W tym celu należy zainicjować narzędzie za pomocą narzędzia <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> zawierającego powiązane elementy.

 Poniższy przykład pochodzi z DSL, w którym istnieje typ Transistor. Każdy tranzystor ma trzy terminale o nazwie Terminale. Narzędzie elementu dla tranzystorów przechowuje prototyp zawierający cztery elementy modelu i trzy linki relacji. Gdy użytkownik przeciągnie narzędzie na diagram, zostanie utworzyć jego wystąpienia i połączyć je z katalogiem głównym modelu.

 Ten kod zastępuje metodę zdefiniowaną w katalogu **Dsl\GeneratedCode\ToolboxHelper.cs.**

 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [Navigating and Updating a Model in Program Code (Nawigowanie i aktualizowanie modelu w kodzie programu).](../modeling/navigating-and-updating-a-model-in-program-code.md)

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

## <a name="customizing-connection-tools"></a><a name="connections"></a> Dostosowywanie narzędzi połączeń
 Zazwyczaj narzędzie elementu jest tworzyć podczas tworzenia nowej klasy łącznika. Alternatywnie można przeciążyć jedno narzędzie, zezwalając typom obu kończy się na określenie typu relacji. Można na przykład zdefiniować jedno narzędzie połączenia, które może tworzyć relacje Person-Person i Person-Town relacje.

 Narzędzia połączeń wywołują konstruktory połączeń. Użyj konstruktorów połączeń, aby określić, jak użytkownicy mogą łączyć elementy w wygenerowanym projektancie. Konstruktorzy połączeń określają elementy, które mogą być połączone, oraz rodzaj tworzonego połączenia między nimi.

 Podczas tworzenia relacji odwołania między klasami domeny jest automatycznie tworzony konstruktor połączeń. Tego konstruktora połączeń można użyć podczas mapowania narzędzia połączenia. Aby uzyskać więcej informacji na temat tworzenia narzędzi do połączeń, zobacz [Konfigurowanie przybornika](../modeling/customizing-tools-and-the-toolbox.md).

 Domyślny konstruktor połączeń można zmodyfikować tak, aby radził sobie z różnymi typami źródłowymi i docelowymi oraz tworzył różne typy relacji.

 Można również napisać kod niestandardowy dla konstruktorów połączeń, aby określić klasy źródłowe i docelowe dla połączenia, zdefiniować typ połączenia do nawiązaniu i podjąć inne akcje skojarzone z tworzeniem połączenia.

### <a name="the-structure-of-connection-builders"></a>Struktura konstruktorów połączeń
 Konstruktorzy połączeń zawierają co najmniej jedną dyrektywę połączenia łącza, która określa relację domeny oraz elementy źródłowe i docelowe. Na przykład w szablonie rozwiązania przepływu zadań można zobaczyć **CommentReferencesSubjectsBuilder** w **Eksploratorze DSL**. Ten konstruktor połączeń zawiera jedną dyrektywę połączenia linku o **nazwie CommentReferencesSubjects,** która jest mapowana na relację domeny **CommentReferencesSubjects**. Ta dyrektywa connect linku zawiera dyrektywę roli źródła, która wskazuje na klasę domeny, oraz dyrektywę roli docelowej, która `Comment` wskazuje na `FlowElement` klasę domeny.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Używanie konstruktorów połączeń do ograniczania ról źródłowych i docelowych
 Konstruktorów połączeń można użyć do ograniczenia wystąpienia niektórych klas w roli źródłowej lub docelowej danej relacji domeny. Na przykład możesz mieć podstawową klasę domeny, która ma relację domeny z inną klasą domeny, ale nie chcesz, aby wszystkie klasy pochodne klasy bazowej miały te same role w tej relacji. W rozwiązaniu przepływu zadań istnieją cztery konkretne klasy domen **(StartPoint,** **EndPoint,** **MergeBranch** i **Synchronization),** które dziedziczą bezpośrednio z abstrakcyjnej klasy domeny **FlowElement** i dwie konkretne klasy domen **(Task** i **ObjectInState),** które dziedziczą bezpośrednio z niego pośrednio. Istnieje również relacja referencyjna usługi **Flow,** która przyjmuje klasy domeny **FlowElement** zarówno w roli źródłowej, jak i docelowej. Jednak wystąpienie klasy domeny **endPoint** nie powinno być źródłem wystąpienia relacji usługi **Flow** ani wystąpienie klasy **startPoint** nie powinno być elementem docelowym wystąpienia relacji usługi **Flow.** Konstruktor **połączeń FlowBuilder** ma dyrektywę połączenia linku o nazwie **Flow,** która określa, które klasy domeny mogą odgrywać rolę źródłową **(Zadanie**, **MergeBranch,** **StartPoint** i **synchronizacja),** która może odgrywać rolę docelową(**MergeBranch,** **Endpoint** i **Synchronization**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Konstruktorzy połączeń z wieloma dyrektywami połączenia linku
 Do konstruktora połączeń można dodać więcej niż jedną dyrektywę connect linku. Może to pomóc ukryć niektóre złożone funkcje modelu domeny przed użytkownikami i zapewnić, że **przybornik** nie będzie zbyt zaśmiecony. Do jednego konstruktora połączeń można dodać dyrektywy połączenia dla kilku różnych relacji domeny. Należy jednak połączyć relacje domeny, gdy wykonują one w przybliżeniu tę samą funkcję.

 W rozwiązaniu przepływu zadań **narzędzie** połączenia przepływu służy  do rysowania wystąpień relacji domeny przepływu **i** przepływu obiektów. Konstruktor **połączeń FlowBuilder** ma oprócz opisanej wcześniej dyrektywy **Connect** linku przepływu dwie dyrektywy połączenia linku o nazwie **ObjectFlow**. Dyrektywy te określają, że wystąpienie relacji **ObjectFlow** może być narysowane między wystąpieniami klasy domeny **ObjectInState** lub z wystąpienia **obiektu ObjectInState** do wystąpienia zadania **,** ale nie między dwoma wystąpieniami obiektu **lub** z wystąpienia klasy **Task** do wystąpienia **obiektu ObjectInState**. Jednak wystąpienie relacji **przepływu** może być rysowane między dwoma wystąpieniami **zadania**. Po skompilowaniu i uruchomieniu rozwiązania przepływu  zadań można zobaczyć, że rysowanie przepływu  z wystąpienia **obiektu ObjectInState** do  wystąpienia zadania powoduje  utworzenie wystąpienia obiektu **ObjectFlow,** ale rysowanie przepływu między dwoma wystąpieniami zadania powoduje utworzenie wystąpienia **przepływu**.

### <a name="custom-code-for-connection-builders"></a>Kod niestandardowy dla konstruktorów połączeń
 W interfejsie użytkownika znajdują się cztery pola wyboru, które definiują różne typy dostosowywania konstruktorów połączeń:

- Pole **wyboru Niestandardowe akceptowanie** w dyrektywie roli źródłowej lub docelowej

- Pole **wyboru Połączenie niestandardowe** w dyrektywie roli źródłowej lub docelowej

- Pole **wyboru Używa połączenia niestandardowego** w dyrektywie connect

- właściwość **Jest niestandardowa** konstruktora połączeń

  Aby wprowadzić te dostosowania, musisz podać kod programu. Aby dowiedzieć się, jaki kod należy podać, zaznacz jedno z tych pól, kliknij pozycję Przekształć wszystkie szablony, a następnie skompilować rozwiązanie. Zostanie wynikowy raport o błędach. Kliknij dwukrotnie raport o błędach, aby zobaczyć komentarz wyjaśniacy, jaki kod należy dodać.

> [!NOTE]
> Aby dodać kod niestandardowy, utwórz definicję klasy częściowej w pliku kodu oddzielnym od plików kodu w folderach GeneratedCode. Aby uniknąć utraty pracy, nie należy edytować wygenerowanych plików kodu. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Tworzenie niestandardowego kodu połączenia
 W każdej dyrektywie connect linku karta **Dyrektywy roli źródła** definiuje typy, które można przeciągać. Podobnie karta **Dyrektywy roli docelowej** definiuje typy, które można przeciągać. Dla każdego typu można dodatkowo określić, czy zezwolić na połączenie (dla tej dyrektywy connect linku), ustawiając flagę **Custom Accept,** a następnie określając dodatkowy kod.

 Możesz również dostosować, co się dzieje po nawiązaniu połączenia. Na przykład można dostosować tylko przypadek, w którym występuje przeciąganie do lub z określonej klasy, wszystkie przypadki, w których reguluje jedna dyrektywa connect linku, lub cały konstruktor połączeń FlowBuilder. Dla każdej z tych opcji można ustawić flagi niestandardowe na odpowiednim poziomie. Gdy przekształcasz wszystkie szablony i próbujesz skompilować rozwiązanie, komunikaty o błędach kierują Cię do komentarzy, które znajdują się w wygenerowanym kodzie. Te komentarze identyfikują, co należy podać.

 W przykładzie diagramu składników konstruktor połączeń dla relacji domeny połączenia jest dostosowany w celu ograniczenia połączeń, które mogą być dokonywane między portami. Na poniższej ilustracji pokazano, że można połączenia tylko z elementów do elementów, ale można `OutPort` `InPort` zagnieżdżać składniki wewnątrz siebie.

 **Połączenie pochodzące z zagnieżdżonych składników do outportu**

 ![Konstruktor połączeń](../modeling/media/connectionbuilder_3.png)

 W związku z tym można określić, że połączenie może pochodzić z zagnieżdżonych składników do outPort. Aby określić takie połączenie,  należy ustawić wartość Używa niestandardowego akceptowania dla typu **InPort** jako rolę źródłową, a typ **OutPort** jako rolę docelową w oknie **Szczegóły DSL,** jak pokazano na poniższych ilustracjach:

 **Link Connect , dyrektywa w eksploratorze DSL**

 ![Obraz konstruktora połączeń](../modeling/media/connectionbuilder_4a.png)

 **Link Connect, dyrektywa w oknie szczegółów DSL**

 ![Dyrektywa Connect linku w oknie szczegółów DSL](../modeling/media/connectionbuilder_4b.png)

 Następnie należy podać metody w klasie ConnectionBuilder:

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

 Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [Navigating and Updating a Model in Program Code (Nawigowanie i aktualizowanie modelu w kodzie programu).](../modeling/navigating-and-updating-a-model-in-program-code.md)

 Możesz na przykład użyć podobnego kodu, aby uniemożliwić użytkownikom tworzenie pętli z linkami nadrzędny-podrzędny. Te ograniczenia są uznawane za "twarde" ograniczenia, ponieważ użytkownicy nie mogą ich naruszać w żadnym momencie. Można również utworzyć "nieustałego" sprawdzanie poprawności, które użytkownicy mogą tymczasowo pominąć, tworząc nieprawidłowe konfiguracje, których nie mogą zapisać.

### <a name="good-practice-in-defining-connection-builders"></a>Dobre rozwiązanie dotyczące definiowania konstruktorów połączeń
 Należy zdefiniować jednego konstruktora połączeń, aby tworzyć różne typy relacji tylko wtedy, gdy są one powiązane koncepcyjnie. W przykładowym przepływie zadań tego samego konstruktora używa się do tworzenia przepływów między zadaniami, a także między zadaniami i obiektami. Jednak używanie tego samego konstruktora do tworzenia relacji między komentarzami i zadaniami byłoby mylące.

 W przypadku definiowania konstruktora połączeń dla wielu typów relacji należy się upewnić, że nie może on być taki sam jak jeden typ z tej samej pary obiektów źródłowych i docelowych. W przeciwnym razie wyniki będą nieprzewidywalne.

 Kod niestandardowy umożliwia stosowanie "trudnych" ograniczeń, ale należy rozważyć, czy użytkownicy powinni mieć możliwość tymczasowego nawiązań nieprawidłowych połączeń. W razie potrzeby można modyfikować ograniczenia, tak aby połączenia nie były weryfikowane, dopóki użytkownicy nie spróbują zapisać zmian.

## <a name="see-also"></a>Zobacz też

- [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
- [Dostosowywanie zachowania dotyczącego kopiowania](../modeling/customizing-copy-behavior.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Przykładowy DSL diagramów obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
