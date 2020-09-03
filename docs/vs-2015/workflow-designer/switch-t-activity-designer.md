---
title: Przełącz &lt; &gt; projektanta aktywności T | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb6d4eb189b75d6e401bca0cfe50a71081760478
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660100"
---
# <a name="switchlttgt-activity-designer"></a>Przełącz &lt; &gt; projektanta aktywności T
<xref:System.Activities.Statements.Switch%601>Działanie oblicza określone wyrażenie i wykonuje działanie z kolekcji działań, których skojarzony klucz jest zgodny z wartością uzyskaną z oceny.

 Projektant **działań \<T> przełączania** służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Switch%601> działania w programie [!INCLUDE[wfd1](../includes/wfd1-md.md)] .

## <a name="the-switchtactivity"></a>Działanie Switch \<T>
 <xref:System.Activities.Statements.Switch%601>Działanie zawiera <xref:System.Activities.Statements.Switch%601.Expression%2A> słownik i <xref:System.Activities.Statements.Switch%601.Cases%2A> . Każdy przypadek w słowniku składa się z pary zawierającej *klucz* i działanie, które służy jako odpowiadająca mu *wartość*. <xref:System.Activities.Statements.Switch%601>Działanie oblicza <xref:System.Activities.Statements.Switch%601.Expression%2A> i porównuje go z każdym z kluczy. W przypadku znalezienia dopasowania zostanie wykonane odpowiednie działanie. Możliwe jest tylko jedno dopasowanie, ponieważ klucze słownika muszą być unikatowe w zależności od typu równości zdefiniowanego przez funkcję porównującą równość słownika. Jeśli nie zostanie znalezione dopasowanie, <xref:System.Activities.Statements.Switch%601.Default%2A> działanie jest wykonywane.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak używać \<T> projektanta działania Switch
 Projektanta **aktywności \<T> przełączania** można znaleźć w kategorii **przepływ sterowania** w **przyborniku**, do którego jest uzyskiwany dostęp przez kliknięcie karty **przybornika** na [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Alternatywnie wybierz **pasek narzędzi** z menu **Widok** lub CTRL + ALT + X). Po usunięciu go do programu w [!INCLUDE[wfd2](../includes/wfd2-md.md)] programie wyświetlane jest okno dialogowe **Wybieranie typów** , w którym użytkownik może określić typ ogólny *T* użyty w <xref:System.Activities.Statements.Switch%601> działaniu. Wartość domyślna to **Int32**. Po wybraniu typu ogólnego *T* , Projektant **przełączeń \<T> ** zostanie dodany do projektanta przepływu pracy.

 Poniżej przedstawiono właściwości projektanta **przełącznika \<T> ** . Wszystkie te właściwości można edytować w siatce właściwości. Niektóre z nich mogą być również edytowane na powierzchni projektanta.

 W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.Switch%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.Switch%601> projektanta działań. Wartość domyślna to Switch \<Int32> . Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Prawda|Określa wyrażenie używane do porównywania z kluczami w kolekcji cases, aby określić przypadek do wykonania.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Określa działanie wykonywane, jeśli nie znaleziono żadnego dopasowania. Kliknij przycisk **Dodaj działanie** w projektancie, aby otworzyć pole **domyślne** , w którym działanie może zostać porzucone.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Określa przypadki, które mają zostać ocenione. Aby dodać przypadek, kliknij przycisk **Dodaj nowy przypadek** u dołu okna projektanta ** \<T> przełącznika** . Przycisk zmienia się w polu tekstowym (pole kombi, jeśli typ ogólny wybrany podczas dodawania przełącznika \<T> jest ciągiem lub wyliczeniem). Po dodaniu klucza w polu **wartość wielkości** liter zostanie rozwinięte miejsce i będzie można usunąć działanie, gdzie w tym miejscu tekst wskazówki "upuść aktywność tutaj", aby zdefiniować logikę wykonywania dla przypadku.|

 Można dodać wiele przypadków, dopóki klucze przypadków nie są zduplikowane. W przeciwnym razie okno dialogowe błędu wyświetla raport o określonym kluczu Case już istnieje i należy wybrać inny klucz. W projektancie **przełączania \<T> ** tylko jeden obszar Case może być jednocześnie w widoku rozszerzonym. Jeśli obszar przypadku jest w widoku zwinięte, kliknięcie obszaru wielkość liter zostanie rozwinięte. Zwróć uwagę, że w przypadku zwiniętego przypadku Projektant wyświetla nazwę wyświetlaną działania w przypadku, gdy jest to możliwe. W przeciwnym razie pokazuje przycisk **Dodaj działanie** , który rozszerza wielkość liter po kliknięciu go i umożliwia dodanie działania.

 Kliknięcie klucza istniejącej sprawy spowoduje zmianę klucza z etykiety do pola tekstowego, aby można było edytować klucz przypadku.

 Istnieją dwa sposoby usunięcia przypadku:

1. Wybierz wielkość liter i usuń ją.

2. Zaznacz wielkość liter, kliknij prawym przyciskiem myszy, aby wyświetlić menu kontekstowe, a następnie wybierz pozycję **Usuń**.

   Pamiętaj, że musisz wybrać sam przypadek, aby go usunąć. Zaznaczenie i usunięcie działania w ramach przypadku powoduje usunięcie tylko tego działania.

## <a name="see-also"></a>Zobacz też
 [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)