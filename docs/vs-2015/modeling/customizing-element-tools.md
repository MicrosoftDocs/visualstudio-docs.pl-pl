---
title: Dostosowywanie narzędzi elementów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655021"
---
# <a name="customizing-element-tools"></a>Narzędzia dostosowywania elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niektóre definicje DSL reprezentują pojedyncze koncepcje jako grupę elementów. Na przykład, jeśli tworzysz model, w którym składnik ma stały zestaw portów, zawsze chcesz, aby porty były tworzone w tym samym czasie co ich składnik nadrzędny. W związku z tym należy dostosować narzędzie tworzenia elementów tak, aby tworzyło grupę elementów, a nie tylko jeden. Aby to osiągnąć, możesz dostosować sposób inicjowania narzędzia do tworzenia elementów.

 Można również zastąpić to, co się dzieje, gdy narzędzie zostanie przeciągnięte na diagram lub element.

## <a name="customizing-the-content-of-an-element-tool"></a>Dostosowywanie zawartości narzędzia elementu
 Każde narzędzie elementu przechowuje wystąpienie <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), które zawiera serializowaną wersję co najmniej jednego elementu modelu i linki. Domyślnie EGP narzędzia elementu zawiera jedno wystąpienie klasy, która jest określona dla narzędzia. Możesz to zmienić, zastępując `ToolboxHelper.CreateElementToolPrototype` *YourLanguage* . Ta metoda jest wywoływana, gdy jest ładowany pakiet DSL.

 Parametr metody jest IDENTYFIKATORem klasy, która została określona w definicji DSL. Gdy metoda jest wywoływana z klasą, która Cię interesuje, można dodać dodatkowe elementy do EGP.

 EGP musi zawierać linki osadzania z jednego elementu głównego do elementów zależnych. Może również zawierać linki odwołań.

 Poniższy przykład tworzy element główny i dwa osadzone elementy. Klasa główna jest wywoływana jako opornik i ma dwie relacje osadzania do elementów o nazwie Terminal. Właściwości roli osadzania mają nazwy Terminal1 i Terminal2, a oba mają liczebność 1.. 1.

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md)
