---
title: Nawigowanie i aktualizowanie modelu w programie kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b9f53f1c2e28ce84cc59afa1d1db205da61e735
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756528"
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>Nawigowanie i aktualizowanie modelu w kodzie programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod, aby tworzyć i usuwać elementy modelu ustawiać ich właściwości oraz tworzenia i usuwania łączy między elementami. Wszystkie zmiany, musi nastąpić w ramach transakcji. Jeśli elementy są wyświetlane na diagramie, diagram zostanie "rozwiązany" automatycznie na końcu transakcji.  
  
## <a name="in-this-topic"></a>W tym temacie  
 [Definicja DSL przykładowej](#example)  
  
 [Nawigacja modelu](#navigation)  
  
 [Uzyskiwanie dostępu do informacji o klasie](#metadata)  
  
 [Wykonaj zmiany wewnątrz transakcji](#transaction)  
  
 [Tworzenie elementów modelu](#elements)  
  
 [Tworzenie relacji łączy](#links)  
  
 [Usuwanie elementów](#deleteelements)  
  
 [Usuwanie relacji łączy](#deletelinks)  
  
 [Zmiana kolejności łączy relacji](#reorder)  
  
 [Blokady](#locks)  
  
 [Kopiowanie i wklejanie](#copy)  
  
 [Nawigowanie i aktualizowanie diagramów](#diagrams)  
  
 [Nawigacja pomiędzy kształty i elementów](#views)  
  
 [Właściwości kształtów i łączników](#shapeProperties)  
  
 [DocView i DocData](#docdata)  
  
 Kształty, łączników i diagramów oraz ich relacje z elementami modelu są opisane w osobnych tematach. Aby uzyskać więcej informacji, zobacz [jak: Nawigowanie i aktualizowanie diagramu](../misc/how-to-navigate-and-update-a-diagram.md).  
  
##  <a name="example"></a> Definicja DSL przykładowej  
 Jest to główna część DslDefinition.dsl w przykładach w tym temacie:  
  
 ![Diagramem definicji DSL &#45; model drzewa rodziny](../modeling/media/familyt-person.png "FamilyT_Person")  
  
 Ten model jest wystąpienie tego języka DSL:  
  
 ![Model drzewa rodziny Tudorów](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")  
  
### <a name="references-and-namespaces"></a>Odwołań i przestrzeni nazw  
 Aby uruchomić kod, w tym temacie, należy odwołać:  
  
 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`  
  
 Twój kod użyje tej przestrzeni nazw:  
  
 `using Microsoft.VisualStudio.Modeling;`  
  
 Ponadto jeśli piszesz kod w innym projekcie niż ten, w którym zdefiniowano DSL, należy zaimportować zestaw, który jest skompilowany na podstawie projektu Dsl.  
  
##  <a name="navigation"></a> Nawigacja modelu  
  
### <a name="properties"></a>Właściwości  
 Właściwości domeny, które można zdefiniować w definicji DSL stają się właściwości, które są dostępne w kodzie programu:  
  
 `Person henry = ...;`  
  
 `if (henry.BirthDate < 1500) ...`  
  
 `if (henry.Name.EndsWith("VIII")) ...`  
  
 Jeśli chcesz ustawić właściwość, należy to zrobić w [transakcji](#transaction):  
  
 `henry.Name = "Henry VIII";`  
  
 Jeśli w definicji DSL, właściwość firmy **rodzaj** jest **obliczona**, nie można go ustawić. Aby uzyskać więcej informacji, zobacz [obliczeniowe i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md).  
  
### <a name="relationships"></a>Relacje  
 Relacje domeny, które można zdefiniować w definicji DSL stają się pary właściwości, jeden w klasie na każdym końcu relacji. Nazwy właściwości są wyświetlane na diagramie DslDefinition jako etykiety na ról na każdej stronie relacji. W zależności od Liczebność roli typ właściwości jest klasy na drugiej stronie relacji lub kolekcję tej klasy.  
  
 `foreach (Person child in henry.Children) { ... }`  
  
 `FamilyTreeModel ftree = henry.FamilyTreeModel;`  
  
 Właściwości przeciwny końców relacji są zawsze odwrotność. Po utworzeniu lub usunięciu link właściwości roli na oba te elementy są aktualizowane. Poniższe wyrażenie (rozszerzenia, który używa `System.Linq`) ma zawsze wartość true dla relacji ParentsHaveChildren w przykładzie:  
  
 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`  
  
 `&& p.Parents.All(parent => parent.Children.Contains(p));`  
  
 **ElementLinks**. Relacja jest również jest reprezentowanych przez element modelu o nazwie *łącze*, który jest wystąpieniem typu relacji domeny. Link ma zawsze element jedno źródło i element jeden element docelowy. Element źródłowy może być taki sam jak element docelowy.  
  
 Aby uzyskać dostęp, link i jego właściwości:  
  
 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`  
  
 `// This is now true:`  
  
 `link == null || link.Parent == henry && link.Child == edward`  
  
 Domyślnie nie więcej niż jedno wystąpienie relacji może połączyć jakaś para elementów modelu. Ale jeśli w definicji DSL `Allow Duplicates` flaga jest wartość true dla relacji, a następnie może istnieć więcej niż jednego połączenia i trzeba użyć `GetLinks`:  
  
 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`  
  
 Istnieją również inne metody uzyskiwania dostępu do łączy. Na przykład:  
  
 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`  
  
 **Ukryte role.** Jeśli w definicji DSL **wygenerowaniu właściwości** jest **false** dla określonej roli, nie ma właściwości nie jest generowany, która odnosi się do tej roli. Można nadal dostęp do linków i przechodzenie przez łącza za pomocą metod klasy relacji:  
  
 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`  
  
 Przykład najczęściej używane dotyczy <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relacji łączy elementu modelu do kształtu, który wyświetla je na diagramie:  
  
 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`  
  
### <a name="the-element-directory"></a>Element katalogu  
 Aby uzyskać dostęp wszystkie elementy w magazynie przy użyciu katalogu elementów:  
  
 `store.ElementDirectory.AllElements`  
  
 Dostępne są również metody służące do znajdowania elementów, takich jak następujące:  
  
 `store.ElementDirectory.FindElements(Person.DomainClassId);`  
  
 `store.ElementDirectory.GetElement(elementId);`  
  
##  <a name="metadata"></a> Uzyskiwanie dostępu do informacji o klasie  
 Można uzyskać informacji na temat klas, relacje i innych aspektów definicji DSL. Na przykład:  
  
 `DomainClassInfo personClass = henry.GetDomainClass();`  
  
 `DomainPropertyInfo birthProperty =`  
  
 `personClass.FindDomainProperty("BirthDate")`  
  
 `DomainRelationshipInfo relationship =`  
  
 `link.GetDomainRelationship();`  
  
 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`  
  
 Klas nadrzędnych elementów modelu są następujące:  
  
-   ModelElement — wszystkie elementy i relacje są ModelElements  
  
-   ElementLink — wszystkie relacje są ElementLinks  
  
##  <a name="transaction"></a> Wykonaj zmiany wewnątrz transakcji  
 Zmianie kodu źródłowego w Store, jego musi zrobić wewnątrz transakcji. Dotyczy to wszystkich elementów modelu, relacje, kształty, diagramy i ich właściwości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Modeling.Transaction>.  
  
 Najwygodniejsza metoda zarządzania transakcji jest `using` instrukcji ujęta w `try...catch` instrukcji:  
  
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
  
 Można wprowadzić dowolną liczbę zmian w jednej transakcji. Możesz otworzyć nowe transakcje w aktywnej transakcji.  
  
 Aby zmiany były trwałe, należy `Commit` transakcji, zanim zostanie on usunięty. Jeśli wystąpi wyjątek, który nie jest wyłapywany wewnątrz transakcji, Store zostaną zresetowane do stanu przed wdrożeniem zmian.  
  
##  <a name="elements"></a> Tworzenie elementów modelu  
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
  
 Ten przykład ilustruje te podstawowe punkty o utworzenie elementu:  
  
- Utwórz nowy element w określonej partycji Store. W przypadku elementów modelu i relacji, ale nie do kształtów zwykle jest domyślną partycję.  
  
- Wprowadź element docelowy relacji osadzania. W DslDefinition w tym przykładzie każda osoba musi być elementem docelowym FamilyTreeHasPeople relacja osadzania. Aby to osiągnąć, możemy ustawić właściwość roli FamilyTreeModel obiektu osoba lub dodać osoby do roli własności obiektu FamilyTreeModel.  
  
- Ustaw właściwości nowego elementu, szczególnie właściwość, dla którego `IsName` ma wartość true w DslDefinition. Ta flaga oznacza właściwość, która identyfikuje jednoznacznie elemencie jego właściciel. W tym przypadku właściwość Name ma tę flagę.  
  
- Definicję DSL tego języka DSL muszą zostać załadowane do Store. Jeśli piszesz rozszerzenie, takie jak polecenie menu, zwykle będzie to już wartość true. W innych przypadkach możesz jawnie załadować modelu do Store lub użyj <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus> go załadować. Aby uzyskać więcej informacji, zobacz [jak: Otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
  Po utworzeniu elementu w ten sposób kształt zostanie utworzony automatycznie (język DSL ma diagramu). Pojawi się on przypisany automatycznie lokalizacji usługi przy użyciu domyślnego kształt, kolor i inne funkcje. Jeśli chcesz kontrolować, gdzie i jak skojarzone kształt pojawia się, zobacz [Tworzenie elementu i jego kształt](#merge).  
  
##  <a name="links"></a> Tworzenie relacji łączy  
 Istnieją dwie relacje zdefiniowane w przykładzie definicji DSL. Każda relacja *właściwości roli* w klasie na każdym końcu relacji.  
  
 Istnieją trzy sposoby, w których można utworzyć wystąpienie relacji. Każda z tych trzech metod działa tak samo:  
  
- Ustaw właściwość obiekt pełniący rolę źródłową. Na przykład:  
  
  -   `familyTree.People.Add(edward);`  
  
  -   `edward.Parents.Add(henry);`  
  
- Ustaw właściwość obiekt pełniący rolę docelową. Na przykład:  
  
  -   `edward.familyTreeModel = familyTree;`  
  
       Liczebność ta rola jest `1..1`, dzięki czemu możemy przypisać wartość.  
  
  -   `henry.Children.Add(edward);`  
  
       Liczebność ta rola jest `0..*`, dzięki czemu możemy dodać do kolekcji.  
  
- Jawnie tworzyć wystąpienie relacji. Na przykład:  
  
  -   `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`  
  
  -   `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`  
  
  Ostatnie metoda jest przydatna, jeśli chcesz ustawić właściwości relacji, sam.  
  
  Po utworzeniu elementu w ten sposób jest tworzony automatycznie łącznika na diagramie, ale ma domyślne kształt, kolor i inne funkcje. Aby kontrolować sposób tworzenia łącznika skojarzone, zobacz [Tworzenie elementu i jego kształt](#merge).  
  
##  <a name="deleteelements"></a> Usuwanie elementów  
 Usuń element przez wywołanie metody `Delete()`:  
  
 `henry.Delete();`  
  
 Ta operacja spowoduje również usunięcie:  
  
- Relacji łącza do i z elementem. Na przykład `edward.Parents` nie będą już miały `henry`.  
  
- Elementy w ról, dla którego `PropagatesDelete` flaga ma wartość true. Na przykład kształt, który wyświetla element zostaną usunięte.  
  
  Domyślnie każda relacja osadzania ma `PropagatesDelete` prawdziwe w roli docelowej. Usuwanie `henry` nie powoduje usunięcia `familyTree`, ale `familyTree.Delete()` spowoduje usunięcie wszystkich `Persons`. Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania dotyczącego usuwania](../modeling/customizing-deletion-behavior.md).  
  
  Domyślnie `PropagatesDelete` nie jest prawdziwe dla ról relacje odniesienia.  
  
  Może spowodować reguły usuwania pominąć propagacji określonych, gdy obiekt zostanie usunięty. Jest to przydatne, jeśli są podstawianie jednego elementu na inny. Należy podać identyfikator GUID co najmniej jedną rolę, dla których powinna nie propagowane usunięcia. Identyfikator GUID można uzyskać z klasy relacji:  
  
  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`  
  
  (Tym konkretnym przykładzie miałaby żadnego efektu, ponieważ `PropagatesDelete` jest `false` dla ról `ParentsHaveChildren` relacji.)  
  
  W niektórych przypadkach usunięcie nie będzie mógł istnienie blokadę na element lub na element, który może zostać usunięty przez propagacji. Możesz użyć `element.CanDelete()` do sprawdzenia, czy element może zostać usunięty.  
  
##  <a name="deletelinks"></a> Usuwanie relacji łączy  
 Możesz usunąć relację łącza przez usunięcie elementu z właściwości roli:  
  
 `henry.Children.Remove(edward); // or:`  
  
 `edward.Parents.Remove(henry);  // or:`  
  
 Można także jawnie usunąć łącze:  
  
 `edwardHenryLink.Delete();`  
  
 Wszystkie te trzy metody mają ten sam efekt. Należy użyć jednej z nich.  
  
 Jeśli rola ma liczebność od 0 do 1 lub 1.. 1, można ją ustawić, `null`, lub z inną wartością:  
  
 `edward.FamilyTreeModel = null;` lub:  
  
 `edward.FamilyTreeModel = anotherFamilyTree;`  
  
##  <a name="reorder"></a> Zmiana kolejności łączy relacji  
 Linki konkretną relację, które źródło lub przeznaczone dla elementu określonego modelu ma określonej kolejności. Pojawiają się w kolejności, w jakiej zostały dodane. Na przykład ta instrukcja zawsze da dzieci w tej samej kolejności:  
  
 `foreach (Person child in henry.Children) ...`  
  
 Można zmienić kolejności linków:  
  
 `ParentsHaveChildren link = GetLink(henry,edward);`  
  
 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`  
  
 `DomainRoleInfo role =`  
  
 `link.GetDomainRelationship().DomainRoles[0];`  
  
 `link.MoveBefore(role, nextLink);`  
  
##  <a name="locks"></a> Blokady  
 Zmiany może być niemożliwe przez blokadę. Można ustawić blokady na poszczególne elementy, partycji i magazyn. Jeśli dowolny z tych poziomów ma blokady uniemożliwiające rodzaju zmian, które mają być, może być wyjątek po użytkownik podejmie. Aby wykryć, czy blokady są ustawiane przy użyciu elementu. GetLocks(), który jest metodą rozszerzenia, która jest zdefiniowana w przestrzeni nazw <xref:Microsoft.VisualStudio.Modeling.Immutability>.  
  
 Aby uzyskać więcej informacji, zobacz [Definiowanie zasad blokowania do tworzenia segmentów tylko do odczytu](../modeling/defining-a-locking-policy-to-create-read-only-segments.md).  
  
##  <a name="copy"></a> Kopiowanie i wklejanie  
 Elementy lub grup elementów, które można skopiować <xref:System.Windows.Forms.IDataObject>:  
  
```  
Person person = personShape.ModelElement as Person;  
Person adopter = adopterShape.ModelElement as Person;  
IDataObject data = new DataObject();  
personShape.Diagram.ElementOperations  
      .Copy(data, person.Children.ToList<ModelElement>());  
```  
  
 Elementy są przechowywane jako Zserializowany grup elementów.  
  
 Elementy z IDataObject można scalić w modelu:  
  
```  
using (Transaction t = targetDiagram.Store.  
        TransactionManager.BeginTransaction("paste"))  
{  
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);  
}  
```  
  
 `Merge ()` można zaakceptować albo `PresentationElement` lub `ModelElement`. Jeśli zostanie nadana `PresentationElement`, można również określić położenie na diagramie docelowy jako trzeci parametr.  
  
##  <a name="diagrams"></a> Nawigowanie i aktualizowanie diagramów  
 W języku DSL elementu modelu domeny, który reprezentuje pojęcia, takie jak osoba lub utworu, różni się od elementu kształtu, który reprezentuje to, co widać na diagramie. Element modelu domeny przechowuje ważne właściwości i relacje pojęć. Element kształtu przechowuje rozmiar, położenie i kolor widoku obiektu na diagramie i układ jego składniki.  
  
### <a name="presentation-elements"></a>Elementy prezentacji  
 ![Diagram klas typów podstawowych kształt i element](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")  
  
 W definicji DSL każdy element, który określisz tworzy klasę, która jest tworzony na podstawie jednej z następujących standardowych klas.  
  
|Rodzaj elementu|Klasa bazowa|  
|---------------------|----------------|  
|Klasa domeny|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|  
|Relacja domeny|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|  
|Kształt|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|  
|Łącznik|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|  
|Diagram|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|  
  
 Element na diagramie zazwyczaj reprezentuje element modelu. Zazwyczaj (ale nie zawsze) <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> reprezentuje wystąpienie klasy domeny i <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> reprezentuje wystąpienie relacji domeny. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> Relacji łączy kształtu węzła lub łącza do elementu modelu, który reprezentuje.  
  
 Każdego węzła lub łącza należy kształt na jednym diagramie. Kształt łącza binarnego łączy dwa kształty węzła.  
  
 Kształty mogą mieć kształty podrzędne w dwóch zestawów. Kształt w `NestedChildShapes` zestawu jest ograniczona do obwiedni jego elementu nadrzędnego. Kształt w `RelativeChildShapes` listy może występować poza metodą lub częściowo poza granice elementu nadrzędnego — na przykład etykiety lub port. Nie ma diagramu `RelativeChildShapes` i nie `Parent`.  
  
###  <a name="views"></a> Nawigacja pomiędzy kształty i elementów  
 Elementy modelu domeny i elementy kształtu, które są powiązane przez <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> relacji.  
  
```csharp  
// using Microsoft.VisualStudio.Modeling;  
// using Microsoft.VisualStudio.Modeling.Diagrams;  
// using System.Linq;  
Person henry = ...;  
PersonShape henryShape =   
  PresentationViewsSubject.GetPresentation(henry)  
    .FirstOrDefault() as PersonShape;  
```  
  
 Tej samej relacji łączy relacji łączników na diagramie:  
  
```  
Descendants link = Descendants.GetLink(henry, edward);  
DescendantConnector dc =  
   PresentationViewsSubject.GetPresentation(link)  
     .FirstOrDefault() as DescendantConnector;  
// dc.FromShape == henryShape && dc.ToShape == edwardShape  
```  
  
 Ta relacja również linki do korzenia modelu do diagramu:  
  
```  
FamilyTreeDiagram diagram =   
   PresentationViewsSubject.GetPresentation(familyTree)  
      .FirstOrDefault() as FamilyTreeDiagram;  
```  
  
 Aby uzyskać element modelu, reprezentowane przez kształty, należy użyć:  
  
 `henryShape.ModelElement as Person`  
  
 `diagram.ModelElement as FamilyTreeModel`  
  
### <a name="navigating-around-the-diagram"></a>Nawigacja wokół diagramu  
 Ogólnie rzecz biorąc nie jest zalecane, aby poruszać się między kształtów i łączników na diagramie. Jest lepszym rozwiązaniem nawigowanie po relacjach w modelu, przenoszenie między kształtów i łączników, tylko wtedy, gdy należy go zmieniać wygląd diagramu. Te metody połączyć kształty na każdym końcu łączników:  
  
 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`  
  
 `connector.FromShape, connector.ToShape`  
  
 Wiele kształtów są złożone; składają się kształt nadrzędny i jeden lub więcej warstw podrzędnych. Kształty, które są pozycjonowane względem innego kształtu są określane jako jego *dzieci*. Kiedy przesuwa się kształtu nadrzędnego, podrzędnego przenoszą się z nim.  
  
 *Względna dzieci* może znajdować się poza obwiednią kształtu nadrzędnego. *Zagnieżdżone* elementy podrzędne są wyświetlane wyłącznie wewnątrz granice elementu nadrzędnego.  
  
 Aby uzyskać najważniejsze zestaw kształtów na diagramie, należy użyć:  
  
 `Diagram.NestedChildShapes`  
  
 Klas kształtów i łączników są:  
  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>  
  
 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>  
  
 ------- *YourShape*  
  
 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>  
  
 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>  
  
 --------- *YourConnector*  
  
###  <a name="shapeProperties"></a> Właściwości kształtów i łączników  
 W większości przypadków nie jest to niezbędne do zapewnienia jawnego zmiany do kształtów zewnętrznych. Zmiana elementy modelu "Napraw" zasady aktualizacji kształtów i łączników. Aby uzyskać więcej informacji, zobacz [reagowania na zagrożenia i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md).  
  
 Jednak warto wprowadzić pewne zmiany jawne do kształtów zewnętrznych we właściwościach, które są niezależne od elementów modelu. Na przykład można zmienić tych właściwości:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -Określa wysokość i szerokość kształtu.  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -pozycji względem nadrzędnego kształt lub diagram  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -zestaw pióra i pędzle, używany do rysowania kształtów lub łącznika  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -sprawia, że kształt jest niewidoczna  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -sprawia, że kształt jest widoczna po `Hide()`  
  
###  <a name="merge"></a> Tworzenie elementu i jego kształtu  
 Podczas tworzenia elementu i połączyć go do drzewa relacji osadzania kształt jest automatycznie tworzony i skojarzonych z nim. Odbywa się przez reguły "naprawa", które są wykonywane na końcu transakcji. Jednak kształtu pojawi się w lokalizacji automatycznie przypisywane i jego kształt, kolor i inne funkcje mają wartości domyślne. Do kontrolowania, jak jest tworzony kształt, służy funkcja scalania. Należy najpierw dodać elementy, które chcesz dodać do ElementGroup, a następnie scalić grupy do diagramu.  
  
 Tej metody:  
  
- Ustawia nazwę, jeśli przypisano właściwości jak nazwa elementu.  
  
- Przestrzega wszelkie dyrektyw scalania określone w definicji DSL.  
  
  W tym przykładzie tworzy kształt na pozycji myszy, gdy użytkownik kliknie dwukrotnie diagramu. W definicji DSL, w tym przykładzie `FillColor` właściwość `ExampleShape` została udostępniona.  
  
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
  
 Jeśli podasz więcej niż jeden kształt, Ustaw swoje położenie względne, za pomocą `AbsoluteBounds`.  
  
 Można również ustawić kolor i inne właściwości narażonych łączniki przy użyciu tej metody.  
  
### <a name="use-transactions"></a>Użycie transakcji  
 Kształty, łączników i diagramy są podtypów <xref:Microsoft.VisualStudio.Modeling.ModelElement> i na żywo w Store. W związku z tym należy zmiany do nich tylko wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [jak: Użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
##  <a name="docdata"></a> Wyświetlanie dokumentów i danych dokumentu  
 ![Diagram klas diagram standardowych typów](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")  
  
## <a name="store-partitions"></a>Partycje Store  
 Gdy model jest ładowany, towarzyszący diagram jest ładowany w tym samym czasie. Zazwyczaj modelu są ładowane do Store.DefaultPartition, a zawartość diagram zostanie załadowana do innej partycji. Zwykle zawartość każda partycja jest ładowany i zapisane w oddzielnym pliku.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>   
 [Sprawdzanie poprawności języka specyficznego dla domeny](../modeling/validation-in-a-domain-specific-language.md)   
 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)   
 [Instrukcje: Użycie transakcji do aktualizacji modelu](../modeling/how-to-use-transactions-to-update-the-model.md)   
 [Integrowanie modeli za pomocą programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Odpowiadanie na zmiany i propagowanie zmian](../modeling/responding-to-and-propagating-changes.md)
