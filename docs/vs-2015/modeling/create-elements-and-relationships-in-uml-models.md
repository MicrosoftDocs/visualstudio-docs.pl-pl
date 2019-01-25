---
title: Tworzenie elementów i relacji w modelach UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b31faa7c71a0f4072d922528a1abc4d040e7dae
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834972"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Tworzenie elementów i relacji w modelach UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kodzie programu do rozszerzenia programu Visual Studio można tworzyć i usuwać elementy i relacje.  
  
## <a name="create-a-model-element"></a>Utwórz Element modelu  
  
### <a name="namespace-imports"></a>Importy Namespace  
 Należy uwzględnić następujące `using` instrukcji.  
  
 Metody tworzenia są zdefiniowane jako metody rozszerzenia w tej przestrzeni nazw:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Uzyskaj właściciela element, którego chcesz utworzyć  
 Model stanowi jedno drzewo tak, aby każdy element ma jeden właściciel, z wyjątkiem głównym modelu. Element główny modelu jest typu `IModel`, który jest typem `IPackage`.  
  
 W przypadku tworzenia elementu, który pojawi się na diagramie określonego na przykład użytkownika bieżącego diagramu, należy zwykle tworzenia go w pakiecie, który jest połączony z tym diagramem. Na przykład:  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 Ta tabela zawiera podsumowanie własności wspólne elementy modelu:  
  
|Element ma zostać utworzony|Właściciel|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>Wywoływanie metody tworzenia właściciela  
 Nazwa metody jest następujący: `Create`*OwnedType*`()`. Na przykład:  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 Niektóre typy mają metody tworzenia bardziej skomplikowane, zwłaszcza w diagramach sekwencji. Zobacz [diagramy sekwencji UML edytować za pomocą interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 W przypadku niektórych typów elementu, można zmienić właściciela elementu jego okres istnienia przy użyciu `SetOwner(newOwner)`.  
  
### <a name="set-the-name-and-other-properties"></a>Ustaw nazwę i inne właściwości  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>Przykład  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>Utwórz skojarzenie  
  
#### <a name="to-create-an-association"></a>Aby utworzyć skojarzenie  
  
1.  Uzyskaj właściciela skojarzenia, zwykle jest to pakiet lub model zawierający końcowy relacji w źródle.  
  
2.  Wywołaj wymaganej metody tworzenia właściciela.  
  
3.  Ustaw właściwości relacji, takie jak jego nazwa.  
  
     Na przykład:  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4.  Ustaw właściwości każdy koniec relacji. Są zawsze dwa `MemberEnds`. Na przykład:  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>Utwórz generalizacji  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Usunąć Element, relacji lub Generalizacja z modelu  
  
```  
anElement.Delete();  
```  
  
 Gdy usuniesz element z modelu:  
  
-   Każda relacja, który stanowi łącze do niego są także usuwane.  
  
-   Każdy kształt, który go reprezentowane na diagramie są także usuwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie modeli i diagramów UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Wyświetlanie modelu UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md)
