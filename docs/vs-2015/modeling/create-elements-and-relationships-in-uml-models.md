---
title: Tworzenie elementów i relacji w modelach UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ea066aa31cbc1f6408ee55c92a5ca761608f534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667813"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Tworzenie elementów i relacji w modelach UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W kodzie programu rozszerzenia do programu Visual Studio można tworzyć i usuwać elementy i relacje.

## <a name="create-a-model-element"></a>Tworzenie elementu modelu

### <a name="namespace-imports"></a>Importy przestrzeni nazw
 Należy uwzględnić poniższe `using` instrukcje.

 Metody tworzenia są definiowane jako metody rozszerzające w tej przestrzeni nazw:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Uzyskaj właściciela elementu, który chcesz utworzyć
 Model tworzy pojedyncze drzewo, dzięki czemu każdy element ma jednego właściciela, z wyjątkiem katalogu głównego modelu. Element główny modelu jest typu `IModel` , który jest typem `IPackage` .

 Jeśli tworzysz element, który będzie wyświetlany na określonym diagramie, na przykład na bieżącym diagramie użytkownika, należy zwykle utworzyć go w pakiecie połączonym z tym diagramem. Na przykład:

```
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;
```

 Ta tabela podsumowuje własność wspólnych elementów modelu:

|Element do utworzenia|Właściciel|
|---------------------------|-----------|
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|
|`IAttribute, IOperation`|`IClass, IInterface`|
|`IPart, IPort`|`IComponent`|
|`IAction, IObjectNode`|`IActivity`|
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|

### <a name="invoke-the-create-method-on-the-owner"></a>Wywoływanie metody Create na właścicielu
 Nazwa metody ma postać: `Create` *własnośćtype* `()` . Na przykład:

```
IUseCase usecase1 = linkedPackage.CreateUseCase();
```

 Niektóre typy mają bardziej złożone metody tworzenia, szczególnie w diagramach sekwencji. Zobacz [Edytowanie diagramów sekwencji UML przy użyciu interfejsu API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 W przypadku niektórych typów elementów można zmienić właściciela elementu w trakcie jego okresu istnienia przy użyciu `SetOwner(newOwner)` .

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

## <a name="create-an-association"></a>Tworzenie skojarzenia

#### <a name="to-create-an-association"></a>Aby utworzyć skojarzenie

1. Uzyskaj właściciela skojarzenia, który jest zwykle pakietem lub modelem zawierającym koniec źródła relacji.

2. Wywołaj wymaganą metodę Create dla właściciela.

3. Ustaw właściwości relacji, takie jak jej nazwa.

     Na przykład:

    ```
    IAssociation association = subject.Package.CreateAssociation(subject, observer);
    association .Name = "Observes";
    ```

4. Ustaw właściwości każdego końca relacji. Zawsze są dostępne dwa `MemberEnds` . Na przykład:

    ```
    association .MemberEnds[0].Name = "subject";   // role name
    association .MemberEnds[1].Name = "observers"; // role name
    association .MemberEnds[1].SetBounds("0..*");
                // multiplicity defaults to "1"
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;
    ```

## <a name="create-a-generalization"></a>Tworzenie generalizacji

```
IGeneralization generalization =
  subclass.CreateGeneralization(superClass);
```

## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Usuwanie elementu, relacji lub generalizacji z modelu

```
anElement.Delete();
```

 Po usunięciu elementu z modelu:

- Wszystkie powiązane z nim relacje również są usuwane.

- Każdy kształt, który reprezentował go na diagramie, również jest usuwany.

## <a name="see-also"></a>Zobacz też
 [Rozszerzone modele UML i diagramy](../modeling/extend-uml-models-and-diagrams.md) [przedstawiają model UML na diagramach](../modeling/display-a-uml-model-on-diagrams.md)
