---
title: Nawigowanie i aktualizowanie modelu w kodzie programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb7c99e345b676576d51c97799cdc7b35f8279ad
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668521"
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Nawigowanie i aktualizowanie modelu w kodzie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod, aby tworzyć i usuwać elementy modelu, ustawiać ich właściwości oraz tworzyć i usuwać linki między elementami. Wszystkie zmiany muszą zostać wprowadzone w obrębie transakcji. Jeśli elementy są wyświetlane na diagramie, diagram zostanie automatycznie "rozwiązany" na końcu transakcji.

## <a name="in-this-topic"></a>W tym temacie
 [Przykładowa Definicja DSL](#example)

 [Nawigowanie po modelu](#navigation)

 [Uzyskiwanie dostępu do informacji o klasie](#metadata)

 [Wykonaj zmiany wewnątrz transakcji](#transaction)

 [Tworzenie elementów modelu](#elements)

 [Tworzenie linków relacji](#links)

 [Usuwanie elementów](#deleteelements)

 [Usuwanie linków relacji](#deletelinks)

 [Zmiana kolejności linków relacji](#reorder)

 [Zamki](#locks)

 [Kopiowanie i wklejanie](#copy)

 [Nawigowanie i aktualizowanie diagramów](#diagrams)

 [Nawigowanie między kształtami i elementami](#views)

 [Właściwości kształtów i łączników](#shapeProperties)

 [DocView i DocData](#docdata)

 Kształty, łączniki i diagramy oraz ich relacje z elementami modelu są opisane w osobnym temacie. Aby uzyskać więcej informacji, zobacz [How to: nawigowanie i aktualizowanie diagramu](../misc/how-to-navigate-and-update-a-diagram.md).

## <a name="example"></a>Przykładowa Definicja DSL
 Jest to główna część DslDefinition. DSL dla przykładów w tym temacie:

 ![Model drzewa rodziny &#45; diagramów definicji DSL](../modeling/media/familyt-person.png "FamilyT_Person")

 Ten model jest wystąpieniem tego języka DSL:

 ![Model drzewa rodziny Tudor](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

### <a name="references-and-namespaces"></a>Odwołania i przestrzenie nazw
 Aby uruchomić kod w tym temacie, należy odwołać się do:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Twój kod będzie używać tej przestrzeni nazw:

 `using Microsoft.VisualStudio.Modeling;`

 Ponadto, jeśli piszesz kod w innym projekcie niż ten, w którym zdefiniowano element DSL, należy zaimportować zestaw, który jest skompilowany przez projekt DSL.

## <a name="navigation"></a>Nawigowanie po modelu

### <a name="properties"></a>Właściwości
 Właściwości domeny zdefiniowane w definicji DSL stają się właściwościami, do których można uzyskać dostęp w kodzie programu:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Jeśli chcesz ustawić właściwość, należy to zrobić wewnątrz [transakcji](#transaction):

 `henry.Name = "Henry VIII";`

 Jeśli w definicji DSL jest **obliczana**wartość **rodzaju** właściwości, nie można jej ustawić. Aby uzyskać więcej informacji, zobacz [właściwości magazynu obliczeniowego i niestandardowego](../modeling/calculated-and-custom-storage-properties.md).

### <a name="relationships"></a>Relacje
 Relacje domeny zdefiniowane w definicji DSL stają się parami właściwości, jeden w klasie na każdym końcu relacji. Nazwy właściwości są wyświetlane na diagramie DslDefinition jako etykiety na rolach na każdej stronie relacji. W zależności od liczebności roli typ właściwości jest albo klasą na drugim końcu relacji, albo kolekcją tej klasy.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Właściwości na przeciwnych końcach relacji są zawsze wzajemnie powiązane. Po utworzeniu lub usunięciu linku są aktualizowane jego właściwości. Następujące wyrażenie (które używa rozszerzeń `System.Linq`) ma zawsze wartość true dla relacji ParentsHaveChildren w przykładzie:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Relacja jest również reprezentowana przez element modelu o nazwie *link*, który jest wystąpieniem typu relacji domeny. Link zawsze ma jeden element źródłowy i jeden element docelowy. Element źródłowy i element docelowy mogą być takie same.

 Możesz uzyskać dostęp do linku i jego właściwości:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Domyślnie nie ma więcej niż jednego wystąpienia relacji, aby połączyć dowolną parę elementów modelu. Ale jeśli w definicji DSL, flaga `Allow Duplicates` ma wartość true dla relacji, może istnieć więcej niż jedno łącze i należy użyć `GetLinks`:

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Istnieją również inne metody uzyskiwania dostępu do linków. Na przykład:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ukryte role.** Jeśli w definicji DSL, **jest generowana** przez właściwość **wartość false** dla określonej roli, nie jest generowana żadna właściwość odpowiadająca tej roli. Można jednak nadal uzyskiwać dostęp do linków i przechodzić przez linki przy użyciu metod relacji:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Najczęściej używanym przykładem jest relacja <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>, która łączy element modelu z kształtem, który wyświetla go na diagramie:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Katalog elementu
 Dostęp do wszystkich elementów w sklepie można uzyskać przy użyciu katalogu elementów:

 `store.ElementDirectory.AllElements`

 Istnieją również metody znajdowania elementów, takich jak następujące:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="metadata"></a>Uzyskiwanie dostępu do informacji o klasie
 Możesz uzyskać informacje na temat klas, relacji i innych aspektów definicji DSL. Na przykład:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Klasy nadrzędne elementów modelu są następujące:

- ModelElement — wszystkie elementy i relacje są ModelElements

- ElementLink — wszystkie relacje są ElementLinks

## <a name="transaction"></a>Wykonaj zmiany wewnątrz transakcji
 Za każdym razem, gdy kod programu zmienia się w sklepie, musi to zrobić w ramach transakcji. Dotyczy to wszystkich elementów modelu, relacji, kształtów, diagramów i ich właściwości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Najbardziej wygodną metodą zarządzania transakcjami jest wyrażenie `using` ujęte w instrukcji `try...catch`:

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Można wprowadzić dowolną liczbę zmian w jednej transakcji. Możesz otworzyć nowe transakcje wewnątrz aktywnej transakcji.

 Aby zmiany były trwałe, należy `Commit` transakcji przed jej usunięciem. Jeśli wystąpi wyjątek, który nie jest przechwytywany w ramach transakcji, magazyn zostanie zresetowany do stanu sprzed zmian.

## <a name="elements"></a>Tworzenie elementów modelu
 Ten przykład dodaje element do istniejącego modelu:

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 Ten przykład ilustruje te zasadnicze kwestie dotyczące tworzenia elementu:

- Utwórz nowy element w określonej partycji magazynu. Dla elementów modelu i relacji, ale nie kształtów, jest to zazwyczaj partycja domyślna.

- Ustaw jako element docelowy relacji osadzania. W DslDefinition tego przykładu każda osoba musi być elementem docelowym osadzania relacji FamilyTreeHasPeople. Aby to osiągnąć, można ustawić właściwość roli FamilyTreeModel obiektu Person lub dodać osobę do właściwości rola osoby dla obiektu FamilyTreeModel.

- Ustaw właściwości nowego elementu, szczególnie właściwość, dla której `IsName` ma wartość true w DslDefinition. Ta flaga oznacza właściwość, która służy do unikatowego identyfikowania elementu w jego właścicielu. W tym przypadku właściwość name ma tę flagę.

- Definicja DSL tego elementu DSL musi zostać załadowana do sklepu. Jeśli piszesz rozszerzenie, takie jak polecenie menu, zwykle będzie to prawdziwe. W innych przypadkach można jawnie załadować model do magazynu lub użyć [ModelBus](/previous-versions/ee904639(v=vs.140)) do jego załadowania. Aby uzyskać więcej informacji, zobacz [jak: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).

  Po utworzeniu elementu w ten sposób tworzony jest automatycznie kształt (jeśli DSL ma diagram). Pojawia się w automatycznie przypisanej lokalizacji z domyślnym kształtem, kolorem i innymi funkcjami. Jeśli chcesz kontrolować miejsce i sposób wyświetlania skojarzonego kształtu, zobacz [Tworzenie elementu i jego kształtu](#merge).

## <a name="links"></a>Tworzenie linków relacji
 Istnieją dwie relacje zdefiniowane w przykładowej definicji DSL. Każda relacja definiuje *Właściwość roli* w klasie na każdym końcu relacji.

 Istnieją trzy sposoby, w których można utworzyć wystąpienie relacji. Każda z tych trzech metod ma ten sam skutek:

- Ustaw właściwość obiektu pełniącego rolę źródłową. Na przykład:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Ustaw właściwość docelowego obiektu pełniącego rolę. Na przykład:

  - `edward.familyTreeModel = familyTree;`

       Liczebność tej roli jest `1..1`, więc przypiszemy wartość.

  - `henry.Children.Add(edward);`

       Liczebność tej roli jest `0..*`, więc dodawana jest do kolekcji.

- Jawnie Utwórz wystąpienie relacji. Na przykład:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Ostatnia metoda jest przydatna, jeśli chcesz ustawić właściwości relacji.

  Gdy tworzysz element w ten sposób, łącznik na diagramie jest tworzony automatycznie, ale ma domyślny kształt, kolor i inne funkcje. Aby kontrolować sposób tworzenia skojarzonego łącznika, zobacz [Tworzenie elementu i jego kształtu](#merge).

## <a name="deleteelements"></a>Usuwanie elementów
 Usuń element, wywołując `Delete()`:

 `henry.Delete();`

 Ta operacja spowoduje również usunięcie:

- Linki relacji do i z elementu. Na przykład `edward.Parents` nie będzie już zawierać `henry`.

- Elementy w rolach, dla których flaga `PropagatesDelete` ma wartość true. Na przykład kształt wyświetlający element zostanie usunięty.

  Domyślnie każda relacja osadzania ma `PropagatesDelete` true w roli docelowej. Usunięcie `henry` nie powoduje usunięcia `familyTree`, ale `familyTree.Delete()` usunie wszystkie `Persons`. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania usuwania](../modeling/customizing-deletion-behavior.md).

  Domyślnie `PropagatesDelete` nie jest spełniony dla ról relacji odwołania.

  Można spowodować, że reguły usuwania pomijają określone propagacje po usunięciu obiektu. Jest to przydatne w przypadku podstawiania jednego elementu na inny. Należy podać identyfikator GUID jednej lub więcej ról, dla których usunięcie nie powinno być propagowane. Identyfikator GUID można uzyskać z klasy relacji:

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  (Ten konkretny przykład nie ma żadnego efektu, ponieważ `PropagatesDelete` jest `false` dla ról `ParentsHaveChildren` relacji).

  W niektórych przypadkach usuwanie jest uniemożliwione przez istnienie blokady, elementu lub elementu, który zostałby usunięty przez propagację. Możesz użyć `element.CanDelete()`, aby sprawdzić, czy element może być usunięty.

## <a name="deletelinks"></a>Usuwanie linków relacji
 Łącze relacji można usunąć, usuwając element z właściwości role:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Łącze można również usunąć jawnie:

 `edwardHenryLink.Delete();`

 Wszystkie te trzy metody mają ten sam efekt. Wystarczy użyć jednego z nich.

 Jeśli rola ma wartość 0.. 1 lub 1.. 1 liczebność, można ustawić ją na `null` lub inną wartość:

 `edward.FamilyTreeModel = null;`//lub:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="reorder"></a>Zmiana kolejności linków relacji
 Linki określonej relacji, które są źródłem lub są przeznaczone dla określonego elementu modelu, mają określoną sekwencję. Są one wyświetlane w kolejności, w jakiej zostały dodane. Na przykład ta instrukcja zawsze będzie zwracać elementy podrzędne w tej samej kolejności:

 `foreach (Person child in henry.Children) ...`

 Można zmienić kolejność linków:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a>Zamki
 Zmiany mogą być blokowane przez blokadę. Blokady można ustawić dla poszczególnych elementów, partycji i magazynu. Jeśli którykolwiek z tych poziomów ma blokadę uniemożliwiającą rodzaj zmiany, którą chcesz wprowadzić, wyjątek może zostać wygenerowany podczas próby. Można stwierdzić, czy blokady są ustawiane za pomocą elementu. GetLocks (), czyli Metoda rozszerzająca zdefiniowana w przestrzeni nazw <xref:Microsoft.VisualStudio.Modeling.Immutability>.

 Aby uzyskać więcej informacji, zobacz [Definiowanie zasad blokowania w celu utworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy"></a>Kopiuj i wklej
 Elementy lub grupy elementów można kopiować do <xref:System.Windows.Forms.IDataObject>:

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Elementy są przechowywane jako Grupa elementów serializowanych.

 Elementy z IDataObject można scalać z modelem:

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` może akceptować `PresentationElement` lub `ModelElement`. Jeśli nadasz mu `PresentationElement`, można także określić pozycję na diagramie docelowym jako trzeci parametr.

## <a name="diagrams"></a>Nawigowanie i aktualizowanie diagramów
 W DSL, element modelu domeny, który reprezentuje pojęcie takie jak osoba lub utwór, jest oddzielony od elementu Shape, który reprezentuje zawartość na diagramie. Element modelu domeny przechowuje ważne właściwości i relacje. Element Shape przechowuje rozmiar, położenie i kolor widoku obiektu na diagramie oraz układ części składnika.

### <a name="presentation-elements"></a>Elementy prezentacji
 ![Diagram klas podstawowych typów kształtu i elementu](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")

 W definicji DSL każdy określony element tworzy klasę, która jest pochodną jednej z następujących klas standardowych.

|Rodzaj elementu|Klasa bazowa|
|---------------------|----------------|
|Klasa domeny|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relacja domeny|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Kształt|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Łącznik|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Element na diagramie zazwyczaj reprezentuje element modelu. Zwykle (ale nie zawsze), <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> reprezentuje wystąpienie klasy domeny, a <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> reprezentuje wystąpienie relacji domeny. Relacja <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> łączy węzeł lub kształt łącza z elementem modelu, który reprezentuje.

 Każdy węzeł lub kształt łącza należy do jednego diagramu. Kształt linku binarnego łączy dwa kształty węzła.

 Kształty mogą mieć kształty podrzędne w dwóch zestawach. Kształt w zestawie `NestedChildShapes` jest ograniczony do pola ograniczenia jego elementu nadrzędnego. Kształt na liście `RelativeChildShapes` może pojawić się poza granicami elementu nadrzędnego lub częściowo poza nim, na przykład etykietę lub port. Diagram nie ma `RelativeChildShapes` i nie `Parent`.

### <a name="views"></a>Nawigowanie między kształtami i elementami
 Elementy modelu domeny i elementy kształtu są powiązane z <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relacji.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Te same powiązania relacji z łącznikami na diagramie:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Ta relacja również łączy katalog główny modelu z diagramem:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Aby uzyskać element modelu reprezentowane przez kształt, użyj:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Nawigowanie wokół diagramu
 Ogólnie rzecz biorąc nie jest zalecane Nawigowanie między kształtami i łącznikami na diagramie. Lepszym rozwiązaniem jest nawigowanie po relacjach w modelu, przechodzenie między kształtami i łącznikami tylko wtedy, gdy jest to niezbędne do pracy nad wyglądem diagramu. Te metody łączą łączniki z kształtami na każdym końcu:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Wiele kształtów to złożone; składają się one z kształtu nadrzędnego i co najmniej jednej warstwy podrzędnej. Kształty, które są pozycjonowane względem innego kształtu, są określane jako *elementy podrzędne*. Po przesunięciu kształtu nadrzędnego elementy podrzędne są z nim przenoszone.

 *Względne elementy podrzędne* mogą występować poza polem ograniczenia kształtu nadrzędnego. *Zagnieżdżone* elementy podrzędne są widoczne wyłącznie wewnątrz granic elementu nadrzędnego.

 Aby uzyskać górny zestaw kształtów na diagramie, użyj:

 `Diagram.NestedChildShapes`

 Klasy nadrzędne kształtów i łączników są następujące:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *YourConnector*

### <a name="shapeProperties"></a>Właściwości kształtów i łączników
 W większości przypadków nie trzeba wprowadzać jawnych zmian do kształtów. Po zmianie elementów modelu, reguły "Napraw" aktualizują kształty i łączniki. Aby uzyskać więcej informacji, zobacz [reagowanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).

 Jednak warto wprowadzić pewne jawne zmiany we właściwościach, które są niezależne od elementów modelu. Można na przykład zmienić następujące właściwości:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> — określa wysokość i szerokość kształtu.

- Pozycja <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> względem kształtu nadrzędnego lub diagramu

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> — zestaw piór i pędzle służące do rysowania kształtu lub łącznika

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> — sprawia, że kształt jest niewidoczny

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> — sprawia, że kształt jest widoczny po `Hide()`

### <a name="merge"></a>Tworzenie elementu i jego kształtu
 Podczas tworzenia elementu i łączenia go z drzewem relacji osadzania kształt jest automatycznie tworzony i kojarzony z nim. Jest to realizowane przez reguły "Naprawa", które są wykonywane na końcu transakcji. Jednak kształt pojawi się w automatycznie przypisanej lokalizacji, a jego kształt, kolor i inne funkcje będą mieć wartości domyślne. Aby kontrolować sposób tworzenia kształtu, można użyć funkcji merge. Najpierw należy dodać elementy, które mają zostać dodane do grupy elementów, a następnie scalić je z diagramem.

 Ta metoda:

- Ustawia nazwę, jeśli przypisano właściwość jako nazwę elementu.

- Obserwuje wszystkie dyrektywy scalania elementów określone w definicji DSL.

  Ten przykład tworzy kształt w pozycji wskaźnika myszy, gdy użytkownik kliknie dwukrotnie diagram. W definicji DSL dla tego przykładu Właściwość `FillColor` `ExampleShape` została uwidoczniona.

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 Jeśli podano więcej niż jeden kształt, ustaw ich względne położenia przy użyciu `AbsoluteBounds`.

 Możesz również ustawić kolor i inne uwidocznione właściwości łączników za pomocą tej metody.

### <a name="use-transactions"></a>Użyj transakcji
 Kształty, łączniki i diagramy są podtypemi <xref:Microsoft.VisualStudio.Modeling.ModelElement> i na żywo w sklepie. W związku z tym należy wprowadzać w nich zmiany tylko wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [How to: use Transactions to updateing model](../modeling/how-to-use-transactions-to-update-the-model.md).

## <a name="docdata"></a>Widok dokumentu i dane dokumentu
 ![Diagram klas typów diagramu standardowego](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")

## <a name="store-partitions"></a>Przechowuj partycje
 Podczas ładowania modelu, towarzyszący diagram jest ładowany w tym samym czasie. Zazwyczaj model jest ładowany do magazynu. DefaultPartition, a zawartość diagramu jest załadowana do innej partycji. Zwykle zawartość każdej partycji jest ładowana i zapisywana w oddzielnym pliku.

## <a name="see-also"></a>Zobacz też
 <xref:Microsoft.VisualStudio.Modeling.ModelElement> [weryfikację w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md) , który [generuje kod z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md) , [jak: używać transakcji do aktualizowania modelu](../modeling/how-to-use-transactions-to-update-the-model.md) [integracji modeli przy użyciu programu Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [Odpowiadanie na i Propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
