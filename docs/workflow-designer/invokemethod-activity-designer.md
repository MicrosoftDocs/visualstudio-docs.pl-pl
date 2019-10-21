---
title: Projektant przepływu pracy-InvokeMethod — Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 593ec198cdfdd8acd1967abb046384711e1fa9ac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650165"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod, projektant działań

Projektant **InvokeMethod** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>Działanie InvokeMethod

@No__t_0 wywołuje publiczną metodę określonego obiektu lub typu.

### <a name="use-the-invokemethod-activity-designer"></a>Korzystanie z projektanta działań InvokeMethod

Dostęp do projektanta działań **InvokeMethod** w kategorii elementy **pierwotne** w **przyborniku**. Projektant działań **InvokeMethod** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracyą powierzchnię, w której są zwykle umieszczane działania, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Porzucenie projektanta działań powoduje utworzenie działania <xref:System.Activities.Statements.InvokeMethod> z domyślną <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. @No__t_0 można edytować w nagłówku projektanta działań **InvokeMethod** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokemethod-properties"></a>Właściwości InvokeMethod

W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.InvokeMethod> i opisano, jak są one używane w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na Projektant przepływu pracy powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.InvokeMethod>. Wartość domyślna to InvokeMethod.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepiej użyć jednej z nich.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Oznacza|Nazwa metody, która ma zostać wywołana, gdy działanie jest wykonywane. Wywoływana metoda musi być zadeklarowana jako **publiczna**. Tę właściwość można edytować na powierzchni projektanta i jest obowiązkowe.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekcja parametrów wywoływanej metody. Parametry należy dodać do kolekcji w takiej samej kolejności, w jakiej występują w podpisie metody. Aby wyświetlić okno dialogowe **parametrów** , w którym można ustawić tę właściwość, kliknij przycisk wielokropka w polu **Parametry** siatki właściwości. Kliknij przycisk **Utwórz argument** , aby dodać parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Wartość zwracana wywołania metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Oznacza|Określa, czy metoda jest wywoływana asynchronicznie. Wartość domyślna to **false**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Obiekt, który zawiera metodę do wywołania. Tę właściwość można edytować na powierzchni projektanta.<br /><br /> Należy ustawić <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> lub <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tę właściwość można edytować na powierzchni projektanta. Tę właściwość należy ustawić tylko wtedy, gdy wywoływana metoda jest statyczna.|

Aby przekazać parametry C# jako parametr **out** (na przykład `Method1(out myParam))`, użyj wartości **unargument** zamiast **InOutArgument**

Metody z argumentami o nazwie **TargetObject** lub **Result** nie mogą być wywoływane przy użyciu działania <xref:System.Activities.Statements.InvokeMethod>. Przyczyną jest to, że <xref:System.Activities.Statements.InvokeMethod> działanie rejestruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> i <xref:System.Activities.Statements.InvokeMethod.Result%2A> w <xref:System.Activities.Activity.CacheMetadata%2A>.

Algorytm rejestrowania parametrów w <xref:System.Activities.Activity.CacheMetadata%2A> przedstawiono na poniższej liście:

1. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argument.

2. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.Result%2A> argument.

3. Wykonaj iterację w kolekcji <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> i zarejestruj każdy argument.

Wyjątek wynikający z typu <xref:System.Activities.InvalidWorkflowException> z następującym komunikatem: "InvokeMethod": zmienna, obiekt RuntimeArgument lub obiekt DelegateArgument już istnieje o nazwie "TargetObject". Nazwy muszą być unikatowe w obrębie zakresu środowiska.

To ograniczenie nie ma zastosowania do <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> i <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Nie są to argumenty przepływu pracy i w związku z tym nie są rejestrowane w kolekcji <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> działania <xref:System.Activities.Statements.InvokeMethod> w metodzie <xref:System.Activities.Activity.CacheMetadata%2A>.

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)