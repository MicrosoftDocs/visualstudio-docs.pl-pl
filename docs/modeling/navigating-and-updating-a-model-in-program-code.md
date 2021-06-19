---
title: Nawigowanie i aktualizowanie modelu w kodzie programu
description: Dowiedz się, jak pisać kod, aby tworzyć i usuwać elementy modelu, ustawiać ich właściwości oraz tworzyć i usuwać linki między elementami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b34c51744c6bab1c6021a006f7ec9b4da0f4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390974"
---
# <a name="navigate-and-update-a-model-in-program-code"></a>Nawigowanie po modelu i aktualizowanie go w kodzie programu

Możesz napisać kod, aby tworzyć i usuwać elementy modelu, ustawiać ich właściwości oraz tworzyć i usuwać linki między elementami. Wszystkie zmiany muszą zostać wprowadzone w ramach transakcji. Jeśli elementy są przeglądane na diagramie, diagram zostanie automatycznie "naprawiony" na końcu transakcji.

## <a name="an-example-dsl-definition"></a><a name="example"></a> Przykładowa definicja DSL
 Jest to główna część dslDefinition.dsl przykładów w tym temacie:

 ![Diagram definicji DSL &#45; modelu drzewa rodziny](../modeling/media/familyt_person.png)

 Ten model jest wystąpieniem tego DSL:

 ![Tudor Family Tree Model](../modeling/media/tudor_familytreemodel.png)

### <a name="references-and-namespaces"></a>Odwołania i przestrzenie nazw
 Aby uruchomić kod w tym temacie, należy odwołać się do:

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 Kod będzie używać tej przestrzeni nazw:

 `using Microsoft.VisualStudio.Modeling;`

 Ponadto, jeśli piszesz kod w innym projekcie niż ten, w którym zdefiniowano DSL, należy zaimportować zestaw, który jest budowany przez projekt Dsl.

## <a name="navigating-the-model"></a><a name="navigation"></a> Nawigowanie po modelu

### <a name="properties"></a>Właściwości
 Właściwości domeny, które definiujesz w definicji DSL stają się właściwościami, do których można uzyskać dostęp w kodzie programu:

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 Jeśli chcesz ustawić właściwość, musisz to zrobić w ramach [transakcji](#transaction):

 `henry.Name = "Henry VIII";`

 Jeśli w definicji DSL kind  właściwości jest **obliczany**, nie można go ustawić. Aby uzyskać więcej informacji, zobacz [Właściwości magazynu obliczeniowego i niestandardowego.](../modeling/calculated-and-custom-storage-properties.md)

### <a name="relationships"></a>Relacje
 Relacje domeny, które definiujesz w definicji DSL, stają się parami właściwości, po jednej na klasie na każdym końcu relacji. Nazwy właściwości są wyświetlane na diagramie DslDefinition jako etykiety ról po każdej stronie relacji. W zależności od liczebności roli typ właściwości jest klasą na drugim końcu relacji lub kolekcją tej klasy.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 Właściwości po przeciwnych końcach relacji są zawsze odwrotne. Po utworzeniu lub usunięciu linku właściwości roli w obu elementach zostaną zaktualizowane. Następujące wyrażenie (które używa rozszerzeń ) jest zawsze prawdziwe dla relacji `System.Linq` ParentsHave Nie dotyczy w przykładzie:

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **ElementLinks**. Relacja jest również reprezentowana przez element modelu o nazwie *link*, który jest wystąpieniem typu relacji domeny. Łącze zawsze ma jeden element źródłowy i jeden element docelowy. Element źródłowy i element docelowy mogą być takie same.

 Możesz uzyskać dostęp do linku i jego właściwości:

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 Domyślnie nie więcej niż jedno wystąpienie relacji może połączyć dowolną parę elementów modelu. Jeśli jednak w definicji DSL flaga jest prawdziwa dla relacji, wówczas może być więcej niż `Allow Duplicates` jedno łącze i należy użyć : `GetLinks`

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 Istnieją również inne metody uzyskiwania dostępu do linków. Na przykład:

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **Ukryte role.** Jeśli w definicji DSL właściwość **Jest generowana** ma wartość **false** dla określonej roli, nie jest generowana żadna właściwość odpowiadająca tej roli. Nadal można jednak uzyskać dostęp do linków i przechodzić między linkami przy użyciu metod relacji:

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 Najczęściej używanym przykładem jest relacja, która łączy element modelu z <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> kształtem, który wyświetla go na diagramie:

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>Katalog elementów
 Dostęp do wszystkich elementów w magazynie można uzyskać przy użyciu katalogu elementów:

 `store.ElementDirectory.AllElements`

 Istnieją również metody znajdowania elementów, takie jak następujące:

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> Uzyskiwanie dostępu do informacji o klasie
 Możesz uzyskać informacje o klasach, relacjach i innych aspektach definicji DSL. Na przykład:

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 Klasy nadrzędne elementów modelu są następujące:

- ModelElement — wszystkie elementy i relacje są elementami modelu

- ElementLink — wszystkie relacje są elementLinks

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> Wykonywanie zmian wewnątrz transakcji
 Za każdym razem, gdy kod programu zmienia coś w magazynie, musi to zrobić w ramach transakcji. Dotyczy to wszystkich elementów modelu, relacji, kształtów, diagramów i ich właściwości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Modeling.Transaction>.

 Najbardziej wygodną metodą zarządzania transakcją jest instrukcja `using` ujęta w `try...catch` instrukcje :

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

 W ramach jednej transakcji można wprowadzić dowolną liczbę zmian. Nowe transakcje można otwierać wewnątrz aktywnej transakcji.

 Aby zmiany stały, należy `Commit` transakcję przed ich usunięcia. Jeśli wystąpi wyjątek, który nie zostanie przechwycony wewnątrz transakcji, magazyn zostanie zresetowany do stanu przed zmianami.

## <a name="creating-model-elements"></a><a name="elements"></a> Tworzenie elementów modelu
 W tym przykładzie dodano element do istniejącego modelu:

```csharp
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

 W tym przykładzie pokazano następujące podstawowe kwestie dotyczące tworzenia elementu:

- Utwórz nowy element w określonej partycji magazynu. W przypadku elementów modelu i relacji, ale nie kształtów, jest to zazwyczaj partycja domyślna.

- Nadaj jej element docelowy relacji osadzania. W definicji DslDefinition tego przykładu każda osoba musi być celem osadzania relacji FamilyTreeHasPeople. Aby to osiągnąć, możemy ustawić właściwość roli FamilyTreeModel obiektu Person lub dodać właściwość Person do właściwości roli People obiektu FamilyTreeModel.

- Ustaw właściwości nowego elementu, szczególnie właściwość , dla której ma `IsName` wartość true w DslDefinition. Ta flaga oznacza właściwość, która służy do unikatowego identyfikowania elementu w obrębie jego właściciela. W tym przypadku właściwość Name ma tę flagę.

- Definicja DSL tego DSL musi być załadowana do magazynu. Jeśli piszesz rozszerzenie, takie jak polecenie menu, zwykle będzie to już prawdziwe. W innych przypadkach można jawnie załadować model do magazynu lub załadować go przy użyciu [magistrali](/previous-versions/ee904639(v=vs.140)) modelu. Aby uzyskać więcej informacji, [zobacz How to: Open a Model from File in Program Code](../modeling/how-to-open-a-model-from-file-in-program-code.md)(Jak otworzyć model z pliku w kodzie programu).

  Podczas tworzenia elementu w ten sposób kształt jest tworzony automatycznie (jeśli DSL ma diagram). Jest ona wyświetlana w automatycznie przypisanej lokalizacji z domyślnym kształtem, kolorem i innymi cechami. Jeśli chcesz kontrolować, gdzie i jak pojawia się skojarzony kształt, zobacz [Creating an Element and its Shape (Tworzenie elementu i jego kształtu).](#merge)

## <a name="creating-relationship-links"></a><a name="links"></a> Tworzenie linków relacji
 W przykładowej definicji DSL zdefiniowano dwie relacje. Każda relacja definiuje *właściwość roli* w klasie na każdym końcu relacji.

 Istnieją trzy sposoby tworzenia wystąpienia relacji. Każda z tych trzech metod ma taki sam efekt:

- Ustaw właściwość odtwarzacza roli źródła. Na przykład:

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- Ustaw właściwość odtwarzacza roli docelowej. Na przykład:

  - `edward.familyTreeModel = familyTree;`

       Liczebność tej roli to `1..1` , więc przypisujemy wartość.

  - `henry.Children.Add(edward);`

       Liczebność tej roli to `0..*` , więc dodamy ją do kolekcji .

- Konstruuj wystąpienie relacji jawnie. Na przykład:

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  Ostatnia metoda jest przydatna, jeśli chcesz ustawić właściwości dla samej relacji.

  Podczas tworzenia elementu w ten sposób łącznik na diagramie jest tworzony automatycznie, ale ma domyślny kształt, kolor i inne funkcje. Aby kontrolować sposób tworzenia skojarzonego łącznika, zobacz [Creating an Element and its Shape (Tworzenie elementu i jego kształtu).](#merge)

## <a name="deleting-elements"></a><a name="deleteelements"></a> Usuwanie elementów

Usuń element, wywołując `Delete()` element :

`henry.Delete();`

Ta operacja spowoduje również usunięcie:

- Relacja łączy się z elementem i z elementu . Na przykład nie `edward.Parents` będzie już zawierać . `henry`

- Elementy w rolach, dla których `PropagatesDelete` flaga ma wartość true. Na przykład kształt, który wyświetla element, zostanie usunięty.

Domyślnie każda relacja osadzania ma wartość `PropagatesDelete` true w roli docelowej. Usunięcie `henry` nie powoduje usunięcia , ale spowoduje usunięcie wszystkich elementów `familyTree` `familyTree.Delete()` `Persons` .

Domyślnie nie `PropagatesDelete` ma wartości true dla ról relacji odwoływać.

Podczas usuwania obiektu reguły usuwania mogą pomijać określone propagacje. Jest to przydatne, jeśli podmień jeden element na inny. Należy podać identyfikator GUID co najmniej jednej roli, dla której usunięcie nie powinno być propagowane. Identyfikator GUID można uzyskać z klasy relacji:

`henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

(Ten konkretny przykład nie będzie mieć żadnego efektu, ponieważ `PropagatesDelete` dotyczy `false` ról `ParentsHaveChildren` relacji).

W niektórych przypadkach usunięcie jest blokowane przez istnienie blokady dla elementu lub elementu, który zostałby usunięty przez propagację. Można użyć , `element.CanDelete()` aby sprawdzić, czy element można usunąć.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> Usuwanie linków relacji
 Łącze relacji można usunąć, usuwając element z właściwości roli:

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 Możesz również jawnie usunąć link:

 `edwardHenryLink.Delete();`

 Wszystkie te trzy metody mają taki sam efekt. Wystarczy użyć tylko jednego z nich.

 Jeśli rola ma liczebność 0..1 lub 1..1, możesz ustawić ją na `null` wartość lub na inną wartość:

 `edward.FamilyTreeModel = null;` Lub:

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> Ponowne uporządkowanie linków relacji
 Linki określonej relacji, które są źródłem lub są celem określonego elementu modelu, mają określoną sekwencję. Są one wyświetlane w kolejności, w której zostały dodane. Na przykład ta instrukcja zawsze daje dzieci w tej samej kolejności:

 `foreach (Person child in henry.Children) ...`

 Możesz zmienić kolejność linków:

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> Blokad
 Zmiany mogą być blokowane przez blokadę. Blokady można ustawiać dla poszczególnych elementów, na partycjach i w magazynie. Jeśli którykolwiek z tych poziomów ma blokadę uniemożliwiającą zmianę, którą chcesz wprowadzić, podczas próby może zostać zgłoszony wyjątek. Można sprawdzić, czy blokady są ustawiane przy użyciu elementu . GetLocks(), czyli metoda rozszerzenia zdefiniowana w przestrzeni nazw <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 Aby uzyskać więcej informacji, [zobacz Definiowanie zasad blokowania w celu tworzenia Read-Only segmentów](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).

## <a name="copy-and-paste"></a><a name="copy"></a> Kopiowanie i wklejanie
 Możesz skopiować elementy lub grupy elementów do pliku <xref:System.Windows.Forms.IDataObject> :

```csharp
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 Elementy są przechowywane jako serializowana grupa elementów.

 Elementy z IDataObject można scalić w model:

```csharp
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` może akceptować zarówno `PresentationElement` , jak i `ModelElement` . Jeśli nadasz mu `PresentationElement` wartość , możesz również określić pozycję na diagramie docelowym jako trzeci parametr.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> Nawigowanie i aktualizowanie diagramów
 W DSL element modelu domeny, który reprezentuje koncepcję, taką jak Person lub Song, jest oddzielony od elementu kształtu, który reprezentuje to, co widzisz na diagramie. Element modelu domeny przechowuje ważne właściwości i relacje pojęć. Element kształtu przechowuje rozmiar, położenie i kolor widoku obiektu na diagramie oraz układ jego części składowych.

### <a name="presentation-elements"></a>Elementy prezentacji
 ![Diagram klas podstawowych typów kształtów i elementów](../modeling/media/dslshapesandelements.png)

 W definicji DSL każdy określony element tworzy klasę, która jest pochodną jednej z następujących klas standardowych.

|Rodzaj elementu|Klasa bazowa|
|-|-|
|Klasa domeny|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|Relacja domeny|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|Kształt|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|Łącznik|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 Element na diagramie zazwyczaj reprezentuje element modelu. Zazwyczaj (ale nie zawsze) reprezentuje wystąpienie klasy <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> domeny, a reprezentuje <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> wystąpienie relacji domeny. Relacja <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> łączy kształt węzła lub linku z elementem modelu, który reprezentuje.

 Każdy kształt węzła lub łącza należy do jednego diagramu. Binarny kształt linku łączy dwa kształty węzłów.

 Kształty mogą mieć kształty podrzędne w dwóch zestawach. Kształt w zestawie jest ograniczony do pola granicy jego `NestedChildShapes` elementu nadrzędnego. Kształt na liście może pojawić się na zewnątrz lub częściowo poza granicami elementu nadrzędnego — na przykład `RelativeChildShapes` etykietą lub portem. Diagram ma nie `RelativeChildShapes` i nie `Parent` .

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> Nawigowanie między kształtami i elementami
 Elementy modelu domeny i elementy kształtu są powiązane przez <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relację.

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 Ta sama relacja łączy relacje z łącznikami na diagramie:

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 Ta relacja łączy również katalog główny modelu z diagramem:

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 Aby uzyskać element modelu reprezentowany przez kształt, użyj:

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>Poruszanie się po diagramie
 Ogólnie rzecz biorąc, nie zaleca się nawigowania między kształtami i łącznikami na diagramie. Lepiej jest nawigować po relacjach w modelu, przenosząc się między kształtami i łącznikami tylko wtedy, gdy konieczne jest pracę nad wyglądem diagramu. Te metody połączą łączniki z kształtami na każdym końcu:

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 Wiele kształtów jest złożonymi elementami. Są one składa się z kształtu nadrzędnego i co najmniej jednej warstwy dzieci. Kształty, które są pozycjonowane względem innego kształtu, są mówione jako *jego dzieci*. Gdy kształt nadrzędny przesuwa się, dzieci są przesuwane razem z nim.

 *Względne dzieci* mogą pojawić się poza polem granicznym kształtu nadrzędnego. *Zagnieżdżone* dzieci są wyświetlane wyłącznie wewnątrz granic elementu nadrzędnego.

 Aby uzyskać górny zestaw kształtów na diagramie, użyj:

 `Diagram.NestedChildShapes`

 Klasy nadrzędne kształtów i łączników to:

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *YourShape*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *TwójŁącz*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> Właściwości kształtów i łączników
 W większości przypadków nie trzeba wprowadzać jawnych zmian kształtów. Po zmianie elementów modelu reguły "napraw" aktualizują kształty i łączniki. Aby uzyskać więcej informacji, zobacz [Odpowiadanie na zmiany i propagowanie ich.](../modeling/responding-to-and-propagating-changes.md)

 Jednak warto wprowadzić pewne jawne zmiany kształtów we właściwościach, które są niezależne od elementów modelu. Można na przykład zmienić następujące właściwości:

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> — określa wysokość i szerokość kształtu.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> — położenie względem kształtu lub diagramu nadrzędnego

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> — zestaw pióra i pędzli używanych do rysowania kształtu lub łącznika

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> — sprawia, że kształt jest niewidoczny

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> — sprawia, że kształt jest widoczny po `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> Tworzenie elementu i jego kształtu

Gdy utworzysz element i połączysz go z drzewem osadzania relacji, kształt zostanie automatycznie utworzony i skojarzony z nim. Jest to wykonywane przez reguły "naprawy", które są wykonywane na końcu transakcji. Jednak kształt zostanie wyświetlony w automatycznie przypisanej lokalizacji, a jego kształt, kolor i inne cechy będą mieć wartości domyślne. Aby kontrolować sposób tworzenia kształtu, można użyć funkcji scalania. Należy najpierw dodać elementy, które chcesz dodać do elementu ElementGroup, a następnie scalić grupę z diagramem.

Ta metoda:

- Ustawia nazwę, jeśli przypisano właściwość jako nazwę elementu.

- Obserwuje wszystkie dyrektywy scalania elementów, które zostały określone w definicji DSL.

Ten przykład tworzy kształt na pozycji myszy, gdy użytkownik dwukrotnie kliknie diagram. W definicji DSL dla tego przykładu właściwość `FillColor` została `ExampleShape` ujawniona.

```csharp
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

 Jeśli udostępnisz więcej niż jeden kształt, ustaw jego położenie względne przy użyciu `AbsoluteBounds` .

 Za pomocą tej metody można również ustawić kolor i inne widoczne właściwości łączników.

### <a name="use-transactions"></a>Korzystanie z transakcji
 Kształty, łączniki i diagramy są podtypami i <xref:Microsoft.VisualStudio.Modeling.ModelElement> znajdują się w magazynie. W związku z tym należy wprowadzić w nich zmiany tylko wewnątrz transakcji. Aby uzyskać więcej informacji, [zobacz How to: Use Transactions to Update the Model (Jak: używanie transakcji do aktualizowania modelu).](../modeling/how-to-use-transactions-to-update-the-model.md)

## <a name="document-view-and-document-data"></a><a name="docdata"></a> Widok dokumentu i dane dokumentu
 ![Diagram klas standardowych typów diagramów](../modeling/media/dsldiagramsanddocs.png)

## <a name="store-partitions"></a>Przechowywanie partycji
 Podczas ładowania modelu towarzyszący diagram jest ładowany w tym samym czasie. Zazwyczaj model jest ładowany do klasy Store.DefaultPartition, a zawartość diagramu jest ładowana do innej partycji. Zazwyczaj zawartość każdej partycji jest ładowana i zapisywana w oddzielnym pliku.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Modeling.ModelElement>
- [Sprawdzanie poprawności w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)
- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
- [Porady: użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md)
- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
