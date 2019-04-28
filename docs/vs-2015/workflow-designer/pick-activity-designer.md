---
title: Pick, Projektant działań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7de5d9189906d72c96372acb1a361d315f973df6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938225"
---
# <a name="pick-activity-designer"></a>Pick, projektant działań
<xref:System.Activities.Statements.Pick> Aktywności zawiera przepływ sterowania opartego na zdarzeniach. Działanie wykonuje jedną kilka gałęzi w odpowiedzi na wyzwalającą zdarzenie.  
  
## <a name="the-pick-activity"></a>Działania Pick  
 A <xref:System.Activities.Statements.Pick> aktywności zawiera zbiór <xref:System.Activities.Statements.PickBranch> obiektów, z których jedna <xref:System.Activities.Statements.Pick> działania można wykonywać z powodu niektóre zdarzenia przychodzące, która służy jako wyzwalacz. W ten sposób [!INCLUDE[wfd1](../includes/wfd1-md.md)] udostępnia modelowanie przepływu sterowania opartego na zdarzeniach. Każdy <xref:System.Activities.Statements.PickBranch> zawiera <xref:System.Activities.Statements.PickBranch.Trigger%2A> i <xref:System.Activities.Statements.PickBranch.Action%2A>. Na początku <xref:System.Activities.Statements.Pick> wykonanie tego działania, wszystkie działania wyzwalacza z <xref:System.Activities.Statements.PickBranch> elementy są zaplanowane. Po zakończeniu pierwszego działania zaplanowano odpowiadającego im działania akcji, a inne działania wyzwalacza zostały anulowane.  
  
### <a name="how-to-use-the-pick-activity-designer"></a>Jak używać Projektanta wybierz działanie  
 **Wybierz** projektanta działań można znaleźć w **przepływ sterowania** kategorii **przybornika**, które jest dostępne po kliknięciu **przybornika**karcie [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać **narzędzi** z **widoku** menu lub klawiszy CTRL + ALT + X.)  
  
 **Wybierz** projektanta działań mogą być przeciągnięte z **przybornika** i porzuconych do [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni wszędzie tam, gdzie Projektanci działań są zazwyczaj umieszczone, na przykład wewnątrz  **Sekwencja** projektanta działań. Po upuszczając go do [!INCLUDE[wfd2](../includes/wfd2-md.md)], tworzy on <xref:System.Activities.Statements.Pick> działania, które domyślnie zawiera dwa puste <xref:System.Activities.Statements.PickBranch> działań jako elementy za pomocą wyświetlania nazw Branch1 i Branch2. Te odpowiednich <xref:System.Activities.Statements.PickBranch.DisplayName%2A> wartości właściwości mogą być edytowane w **PickBranch** nagłówka projektanta działań lub w ramach **właściwości** okna dla każdej gałęzi.  
  
 Istnieją dwa sposoby dodawania <xref:System.Activities.Statements.PickBranch> działań do kolekcji <xref:System.Activities.Statements.Pick> obiektu: przeciąganie i upuszczanie **PickBranch** projektanta z **przybornika** lub za pomocą menu kontekstowego w ramach **wybierz** powierzchni projektowej. Aby uzyskać więcej informacji, zobacz [PickBranch](../workflow-designer/pickbranch-activity-designer.md) tematu. Zwróć uwagę, że tylko element, którego można umieścić wewnątrz **wybierz** jest Projektant działań **PickBranch** projektanta działań.  
  
### <a name="pick-activity-properties-in-the-workflow-designer"></a>Wybierz właściwości działania w Projektancie przepływu pracy  
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.Pick> właściwości i w tym artykule opisano, jak są używane w projektancie. Te właściwości można edytować w siatce właściwości lub na powierzchni projektowej.  
  
|Nazwa właściwości|Wymagane|Użycie|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Pick> projektanta działań w nagłówku. Wartość domyślna to pobranie. Wartość można edytować w siatce właściwości lub bezpośrednio w nagłówku projektanta działań.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)   
 [Wybieranie działania](http://msdn.microsoft.com/library/b3e49b7f-0285-4720-8c09-11ae18f0d53e)   
 [Używanie działania Pick](http://msdn.microsoft.com/library/b89be812-a247-4025-b0e3-ffb20db027a6)