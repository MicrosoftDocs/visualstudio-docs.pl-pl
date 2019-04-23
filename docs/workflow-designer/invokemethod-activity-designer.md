---
title: Projektant przepływu pracy — InvokeMethod, Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eed5d81cce05b316ef7593639e868936e7f2fa69
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039256"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod, projektant działań

**InvokeMethod** projektanta jest używany do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeMethod> działania.

## <a name="the-invokemethod-activity"></a>Działania InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> Wywołuje metodę publicznych określonego obiektu lub typu.

### <a name="use-the-invokemethod-activity-designer"></a>Użyj InvokeMethod, Projektant działań

Dostęp do **InvokeMethod** projektanta działań w **podstawowych** kategorii **przybornika**. **InvokeMethod** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy, gdzie odkąd działań są zazwyczaj umieszczane, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Projektant działań porzucenie tworzy <xref:System.Activities.Statements.InvokeMethod> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> z InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A> Mogą być edytowane w nagłówku **InvokeMethod** projektanta działań lub **DisplayName** pola siatki właściwości.

### <a name="the-invokemethod-properties"></a>Właściwości InvokeMethod

W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeMethod> właściwości oraz opisano sposoby ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich mogą być edytowane na powierzchni projektanta przepływów pracy.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa <xref:System.Activities.Statements.InvokeMethod> działania. Wartość domyślna to InvokeMethod.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, zaleca się go użyć.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Prawda|Nazwa metody do wywołania, gdy działanie wykonuje. Metoda wywoływana musi być zadeklarowany jako **publicznych**. Ta właściwość może być edytowany na powierzchni projektanta i jest wymagana.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekcja parametrów wywoływanej metody. Parametry muszą zostać dodane do kolekcji w tej samej kolejności, które są wyświetlane w podpisie metody. Aby wyświetlić **parametry** okna dialogowego, w którym można ustawić tę właściwość, kliknij przycisk wielokropka w **parametry** pola siatki właściwości. Kliknij przycisk **Utwórz Argument** przycisk, aby dodać parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Wartość zwracaną przez wywołanie metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Prawda|Określa, czy metoda jest wywoływana asynchronicznie. Wartość domyślna to **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Obiekt, który zawiera metodę do wywołania. Tej właściwości można edytować na powierzchni projektowej.<br /><br /> Albo <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> lub <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> jest wymagany do skonfigurowania.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tej właściwości można edytować na powierzchni projektowej. Ta właściwość musi można ustawić tylko, gdy wywoływana metoda jest statyczna.|

Do przekazania parametrów jako C# **się** parametrów (na przykład `Method1(out myParam))`, użyj **OutArgument** zamiast **InOutArgument**

Metody z argumentami o nazwie **TargetObject** lub **wynik** nie można wywołać za pomocą <xref:System.Activities.Statements.InvokeMethod> działania. Jest to spowodowane tym, że <xref:System.Activities.Statements.InvokeMethod> rejestruje działanie <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> i <xref:System.Activities.Statements.InvokeMethod.Result%2A> w <xref:System.Activities.Activity.CacheMetadata%2A>.

Algorytm parametry w rejestrowaniu <xref:System.Activities.Activity.CacheMetadata%2A> jest wyświetlany na poniższej liście:

1. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argumentu.

2. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.Result%2A> argumentu.

3. Iteracyjne przeglądanie <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekcji i zarejestrować każdy argument.

Wyjątek wynikowa jest typu <xref:System.Activities.InvalidWorkflowException> z następującym komunikatem: "InvokeMethod": Istnieje RuntimeArgument lub DelegateArgument już zmienną o nazwie "TargetObject". Nazwy muszą być unikatowe w obrębie zakresu środowiska.

To ograniczenie nie ma zastosowania do <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> i <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>. Nie ma argumentów przepływu pracy i w związku z tym nie są zarejestrowane w <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> zbiór <xref:System.Activities.Statements.InvokeMethod> działania w <xref:System.Activities.Activity.CacheMetadata%2A> metody.

## <a name="see-also"></a>Zobacz także

- [Typy pierwotne](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)