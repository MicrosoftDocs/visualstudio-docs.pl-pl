---
title: Nawigowanie po relacjach z UML API | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: a4d11d45-b8c0-40f9-a597-363f07659610
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cb2a02ba27f06ef027001c2de07308c153b21c2b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780878"
---
# <a name="navigate-relationships-with-the-uml-api"></a>Nawigowanie po relacjach za pomocą interfejsu API UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Model składa się z elementów, połączone ze sobą różne rodzaje relacji. W tym temacie opisano sposób nawigowanie po modelu w kodzie programu.  
  
## <a name="traversing-relationships"></a>Nakierowanych relacji  
  
### <a name="any-relationship"></a>Każda relacja  
 Użyj `GetRelatedElements<T>()` można znaleźć wszystkie elementy podłączone do określonego elementu. Któryś zbiór `T` do `IRelationship` przenosisz relacje wszelkiego rodzaju lub skorzystania z bardziej specyficznego typu takich jak `IAssociation` przechodzenie po prostu tego typu.  
  
```  
IElement anElement;  
// Select all elements related to anElement.  
Context.CurrentDiagram.SelectShapes (  
   anElement.GetRelatedElements<IRelationship>()  
    .SelectMany(e=>e.Shapes()).ToArray());  
  
```  
  
 Użyj `GetRelatedLinks<T>()` można znaleźć wszystkie relacje połączone z elementem.  
  
```  
// Process all relationships connected to an element.  
foreach (IRelationship relationship in   
   anElement.GetRelatedLinks<IRelationship>())  
{  
  Debug.Assert(relationship.SourceElement == anElement  
      || relationship.TargetElement == anElement);  
}  
  
```  
  
### <a name="association"></a>Skojarzenie  
 Asocjacja jest relacja między dwie właściwości, z których każdy należy do klasyfikatora.  
  
```  
IClassifier classifier; // class, interface, component, actor, ...  
// Get all the associations sourced from this classifier  
foreach (IProperty p in classifier.GetOutgoingAssociationEnds())  
{  
  // p represents the end further end of an association.  
  IType oppositeElement = p.Type;   
    // The type to which this association connects classifier  
  
  IProperty oppositeProperty = p.Opposite;  
    // The nearer end of the association.  
  Debug.Assert(oppositeProperty.Type == classifier);  
  IAssociation association = p.Association;  
  Debug.Assert(association.MemberEnds.Contains(p)  
     && association.MemberEnds.Contains(oppositeProperty));  
}  
```  
  
### <a name="generalization-and-realization"></a>Generalizacja i realizacji  
 Przeciwny dostępu kończy się z Generalizacja:  
  
```  
foreach (IClassifier supertype in classifier.Generals) {…}  
foreach (IClassifier subtype in classifier.GetSpecifics()) {…}  
Access the relationship itself:  
foreach (IGeneralization gen in classifier.Generalizations)   
{ Debug.Assert(classifier == gen.Specific); }  
```  
  
```  
  
/// InterfaceRealization:  
IEnumerable<IInterface> GetRealizedInterfaces  
    (this IBehavioredClassifier classifier);  
IEnumerable<IBehavioredClassifier> GetRealizingClassifiers  
    (this IInterface interface);  
  
```  
  
### <a name="dependency"></a>Zależność  
  
```  
/// Returns the elements depending on this element  
IEnumerable<INamedElement> GetDependencyClients(this INamedElement element);   
/// Returns the elements this element depends on  
IEnumerable<INamedElement> INamedElement GetDependencySuppliers(this INamedElement element);  
  
```  
  
### <a name="activity-edge"></a>Działanie usługi Edge  
  
```  
/// Returns the nodes targeted by edges outgoing from this one  
IEnumerable<IActivityNode> GetActivityEdgeTargets(this IActivityNode node);  
/// Returns the nodes sourcing edges incoming to this one  
IEnumerable<IActivityNode> GetActivityEdgeSources(this IActivityNode node);  
  
```  
  
### <a name="connector-assembly-and-delegation"></a>Łącznik (zestawu i delegowanie)  
  
```  
/// Returns the elements connected via assembly   
/// or delegation to this one  
IEnumerable<IConnectableElement> GetConnectedElements(this IConnectableElement element);  
  
```  
  
### <a name="messages-and-lifelines"></a>Wiadomości i linii życia  
  
```  
IEnumerable<IMessage> GetAllOutgoingMessages(this ILifeline  lifeline);   
// both from lifeline and execution occurrences  
IEnumerable<IMessage> GetAllIncomingMessages(this ILifeline  lifeline);  
ILifeline GetSourceLifeline(this IMessage message);   
    // may return null for found messages  
ILifeline GetTargetLifeline(this IMessage message);    
    // may return null for lost messages  
  
```  
  
### <a name="package-import"></a>Importowanie pakietu  
  
```  
IEnumerable<IPackage>GetImportedPackages(this INamespace namespace);  
IEnumerable<INamespace> GetImportingNamespaces(this IPackage package);  
  
```  
  
### <a name="use-case-extend-and-include"></a>Przypadek użycia, rozszerzanie i obejmują  
  
```  
IEnumerable<IUseCase>GetExtendedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetExtendingCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludedCases(this IUseCase usecase);  
IEnumerable<IUseCase>GetIncludingCases(this IUseCase usecase);  
```  
  
## <a name="enumerating-relationships"></a>Wyliczanie relacji  
 Wszystkie właściwości modelu UML, zwracanie wielu wartości, które są zgodne z <> interfejsu IEnumerable. Oznacza to, że można użyć [wyrażenia zapytań Linq](http://go.microsoft.com/fwlink/?LinkId=168834) i metody rozszerzenia zdefiniowane w **System.Linq** przestrzeni nazw.  
  
 Na przykład:  
  
```  
from shape in     Context.CurrentDiagram.GetSelectedShapes<IClassifier>()  
where shape.Color == System.Drawing.Color.Red  
select shape.Element  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)
