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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658992"
---
# <a name="invokemethod-activity-designer"></a>InvokeMethod, projektant działań
Projektant **InvokeMethod** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.InvokeMethod> działania.

## <a name="the-invokemethod-activity"></a>Działanie InvokeMethod
 <xref:System.Activities.Statements.InvokeMethod>Wywołuje metodę publiczną określonego obiektu lub typu.

### <a name="using-the-invokemethod-activity-designer"></a>Korzystanie z projektanta działań InvokeMethod
 Projektant działań **InvokeMethod** można znaleźć w kategorii elementy **pierwotne** **przybornika**, do którego uzyskuje się dostęp przez kliknięcie karty **przybornika** [!INCLUDE[wfd2](../includes/wfd2-md.md)] (można także wybrać pozycję **pasek narzędzi** z menu **Widok** lub Crtl + Alt + X).

 Projektant działań **InvokeMethod** można przeciągać z **przybornika** i znajdować się na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni, gdzie kiedykolwiek są zwykle umieszczane działania, na przykład wewnątrz <xref:System.Activities.Statements.Sequence> . Spowoduje to utworzenie <xref:System.Activities.Statements.InvokeMethod> działania z domyślną wartością <xref:System.Activities.Activity.DisplayName%2A> InvokeMethod. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działań **InvokeMethod** lub w polu **DisplayName** siatki właściwości.

### <a name="the-invokemethod-properties"></a>Właściwości InvokeMethod
 W poniższej tabeli przedstawiono <xref:System.Activities.Statements.InvokeMethod> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości, a niektóre z nich można edytować na [!INCLUDE[wfd2](../includes/wfd2-md.md)] powierzchni projektanta.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Przyjazna nazwa <xref:System.Activities.Statements.InvokeMethod> działania. Wartość domyślna to InvokeMethod.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Prawda|Nazwa metody, która ma zostać wywołana, gdy działanie jest wykonywane. Wywoływana metoda musi być zadeklarowana jako **publiczna**. Tę właściwość można edytować na powierzchni projektanta. Jest to właściwość obowiązkowa.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Fałsz|Kolekcja parametrów wywoływanej metody. Parametry należy dodać do kolekcji w takiej samej kolejności, w jakiej występują w podpisie metody. W siatce właściwości kliknij przycisk wielokropka w polu **Parametry** , aby wyświetlić okno dialogowe **parametrów** umożliwiające ustawienie tej właściwości. Kliknij przycisk **Utwórz argument** , aby dodać parametry.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Fałsz|Wartość zwracana wywołania metody.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Prawda|Określa, czy metoda jest wywoływana asynchronicznie. Wartość domyślna to **false**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Fałsz|Obiekt, który zawiera metodę do wywołania. Tę właściwość można edytować na powierzchni projektanta.<br /><br /> Wymagany jest parametr <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> lub <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> .|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Fałsz|Typ <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> . Tę właściwość można edytować na powierzchni projektanta. Tę właściwość należy ustawić tylko wtedy, gdy wywoływana metoda jest statyczna.|

 Aby przekazać parametry jako parametr **out** języka C# (na przykład, `Method1(out myParam)),` należy użyć elementu **OutArgument** out zamiast **InOutArgument**

 Metody z argumentami o nazwie **TargetObject** lub **Result** nie mogą być wywoływane przy użyciu <xref:System.Activities.Statements.InvokeMethod> działania. Przyczyną tego problemu jest to, że <xref:System.Activities.Statements.InvokeMethod> działanie rejestruje <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> , <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> i <xref:System.Activities.Statements.InvokeMethod.Result%2A> w <xref:System.Activities.Activity.CacheMetadata%2A> .

 Algorytm rejestrowania parametrów w programie <xref:System.Activities.Activity.CacheMetadata%2A> pokazano na poniższej liście:

1. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> argument.

2. Zarejestruj <xref:System.Activities.Statements.InvokeMethod.Result%2A> argument.

3. Wykonaj iterację <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> kolekcji i zarejestruj każdy argument.

   Otrzymany wyjątek jest typu <xref:System.Activities.InvalidWorkflowException> z następującym komunikatem: "InvokeMethod": zmienna, obiekt RuntimeArgument lub obiekt DelegateArgument o nazwie "TargetObject" już istnieje. Nazwy muszą być unikatowe w obrębie zakresu środowiska.

   To ograniczenie nie ma zastosowania do <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> i <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> ponieważ nie są argumentami przepływu pracy i dlatego nie są zarejestrowane w <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> kolekcji <xref:System.Activities.Statements.InvokeMethod> działań w <xref:System.Activities.Activity.CacheMetadata%2A> metodzie.

## <a name="see-also"></a>Zobacz też
 Elementy [pierwotne](../workflow-designer/primitives-activity-designers.md) [przypisują](../workflow-designer/assign-activity-designer.md) [opóźnienie](../workflow-designer/delay-activity-designer.md) [WriteLine](../workflow-designer/writeline-activity-designer.md)