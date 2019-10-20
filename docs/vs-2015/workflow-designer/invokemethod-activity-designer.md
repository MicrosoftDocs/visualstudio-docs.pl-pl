---
title: Projektant działań InvokeMethod | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fcfba979ba7fce4aeffab1fe9e9a5a3728e513af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658992"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod, projektant działań
Projektant **InvokeMethod** służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.InvokeMethod>.

## <a name="the-invokemethod-activity"></a>Działanie InvokeMethod
 @No__t_0 wywołuje publiczną metodę określonego obiektu lub typu.

### <a name="using-the-invokemethod-activity-designer"></a>Korzystanie z projektanta działań InvokeMethod
 Projektant działań **InvokeMethod** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz pozycję **pasek narzędzi** z menu **Widok** lub CRTL + ALT + X.)

 Projektant działań **InvokeMethod** można przeciągnąć z **przybornika** i porzucić na [!INCLUDE[wfd2](../includes/wfd2-md.md)]ą powierzchnię, w której są zwykle umieszczane działania, takie jak wewnątrz <xref:System.Activities.Statements.Sequence>. Spowoduje to utworzenie działania <xref:System.Activities.Statements.InvokeMethod> z domyślną <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. @No__t_0 można edytować w nagłówku projektanta działań **InvokeMethod** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokemethod-properties"></a>Właściwości InvokeMethod
 W poniższej tabeli przedstawiono właściwości <xref:System.Activities.Statements.InvokeMethod> i opisano sposób ich używania w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)]designer powierzchni.

|Nazwa właściwości|Wymagane|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Przyjazna nazwa działania <xref:System.Activities.Statements.InvokeMethod>. Wartość domyślna to InvokeMethod.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Oznacza|Nazwa metody, która ma zostać wywołana, gdy działanie jest wykonywane. Wywoływana metoda musi być zadeklarowana jako **publiczna**. Tę właściwość można edytować na powierzchni projektanta. Jest to właściwość obowiązkowa.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|Kolekcja parametrów wywoływanej metody. Parametry należy dodać do kolekcji w takiej samej kolejności, w jakiej występują w podpisie metody. W siatce właściwości kliknij przycisk wielokropka w polu **Parametry** , aby wyświetlić okno dialogowe **parametrów** umożliwiające ustawienie tej właściwości. Kliknij przycisk **Utwórz argument** , aby dodać parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|Wartość zwracana wywołania metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Oznacza|Określa, czy metoda jest wywoływana asynchronicznie. Wartość domyślna to **false**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|Obiekt, który zawiera metodę do wywołania. Tę właściwość można edytować na powierzchni projektanta.<br /><br /> Należy ustawić <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> lub <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Tę właściwość można edytować na powierzchni projektanta. Tę właściwość należy ustawić tylko wtedy, gdy wywoływana metoda jest statyczna.|

 Aby przekazać parametry C# jako parametr **out** (na przykład `Method1(out myParam)),` należy używać elementu out zamiast **InOutArgument**

 Metody z argumentami o nazwie **TargetObject** lub **Result** nie mogą być wywoływane przy użyciu działania <xref:System.Activities.Statements.InvokeMethod>. Przyczyną jest to, że <xref:System.Activities.Statements.InvokeMethod> działanie rejestruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> i <xref:System.Activities.Statements.InvokeMethod.Result%2A> w <xref:System.Activities.Activity.CacheMetadata%2A>.

 Algorytm rejestrowania parametrów w <xref:System.Activities.Activity.CacheMetadata%2A> przedstawiono na poniższej liście:

1. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argument.

2. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.Result%2A> argument.

3. Wykonaj iterację w kolekcji <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> i zarejestruj każdy argument.

   Wyjątek wynikający z typu <xref:System.Activities.InvalidWorkflowException> z następującym komunikatem: "InvokeMethod": zmienna, obiekt RuntimeArgument lub obiekt DelegateArgument już istnieje o nazwie "TargetObject". Nazwy muszą być unikatowe w obrębie zakresu środowiska.

   To ograniczenie nie ma zastosowania do <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> i <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>, ponieważ nie są argumentami przepływu pracy i dlatego nie są zarejestrowane w <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> kolekcji działań <xref:System.Activities.Statements.InvokeMethod> w <xref:System.Activities.Activity.CacheMetadata%2A> metodzie.

## <a name="see-also"></a>Zobacz też
 Elementy [pierwotne](../workflow-designer/primitives-activity-designers.md) [przypisują](../workflow-designer/assign-activity-designer.md) [opóźnienie](../workflow-designer/delay-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)