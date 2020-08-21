---
title: Projektant przepływu pracy — &lt; &gt; Projektant aktywności T
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7430dec75e898a6695b146ce50076b8f57ed9d3e
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711615"
---
# <a name="switcht-activity-designer"></a>Switch\<T>, projektant działań

<xref:System.Activities.Statements.Switch%601>Działanie oblicza określone wyrażenie i wykonuje działanie z kolekcji działań, których skojarzony klucz jest zgodny z wartością uzyskaną z oceny.

**Przełącznik<T \> ** Activity Designer służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Switch%601> działania w Projektant przepływu pracy.

## <a name="the-switchtactivity"></a>Działanie Switch \<T>

<xref:System.Activities.Statements.Switch%601>Działanie zawiera <xref:System.Activities.Statements.Switch%601.Expression%2A> słownik i <xref:System.Activities.Statements.Switch%601.Cases%2A> . Każdy przypadek w słowniku składa się z pary zawierającej *klucz* i działanie, które służy jako odpowiadająca mu *wartość*. <xref:System.Activities.Statements.Switch%601>Działanie oblicza <xref:System.Activities.Statements.Switch%601.Expression%2A> i porównuje go z każdym z kluczy. W przypadku znalezienia dopasowania zostanie wykonane odpowiednie działanie. Możliwe jest tylko jedno dopasowanie, ponieważ klucze słownika muszą być unikatowe w zależności od typu równości zdefiniowanego przez funkcję porównującą równość słownika. Jeśli nie zostanie znalezione dopasowanie, <xref:System.Activities.Statements.Switch%601.Default%2A> działanie jest wykonywane.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak używać \<T> projektanta działania Switch

Dostęp do projektanta działania **Switch \<T> ** w kategorii **przepływ sterowania** w **przyborniku**. Po porzucenie go do Projektant przepływu pracy wyświetla okno dialogowe **Wybieranie typów** , aby zezwolić użytkownikowi na określenie typu ogólnego *T* użytego w <xref:System.Activities.Statements.Switch%601> działaniu. Wartość domyślna to **Int32**. Po wybraniu typu ogólnego *t* do projektanta przepływu pracy zostanie dodany **przełącznik \><T** Designer.

Poniżej znajdują się właściwości **przełącznika<T \> ** Designer. Wszystkie te właściwości można edytować w siatce właściwości. Niektóre z nich mogą być również edytowane na powierzchni projektanta.

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.Switch%601> właściwości i opisano sposób ich użycia w projektancie.

|Nazwa właściwości|Wymagany|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę <xref:System.Activities.Statements.Switch%601> projektanta działań. Wartość domyślna to switch<Int32 \> . Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta.<br /><br /> Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Prawda|Określa wyrażenie używane do porównywania z kluczami w kolekcji cases, aby określić przypadek do wykonania.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Określa działanie wykonywane, jeśli nie znaleziono żadnego dopasowania. Kliknij przycisk **Dodaj działanie** w projektancie, aby otworzyć pole **domyślne** , w którym działanie może zostać porzucone.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Określa przypadki, które mają zostać ocenione. Aby dodać przypadek, kliknij przycisk **Dodaj nowy przypadek** u dołu okna projektanta ** \<T> przełącznika** . Przycisk zmienia się w polu tekstowym (pole kombi, jeśli typ ogólny wybrany podczas dodawania przełącznika \<T> jest ciągiem lub wyliczeniem). Po dodaniu klucza w polu **wartość wielkości** liter zostanie rozwinięte miejsce i będzie można usunąć działanie, gdzie w tym miejscu tekst wskazówki "upuść aktywność tutaj", aby zdefiniować logikę wykonywania dla przypadku.|

Można dodać wiele przypadków, dopóki klucze przypadków nie są zduplikowane. W przeciwnym razie okno dialogowe błędu wyświetla raport o określonym kluczu Case już istnieje i należy wybrać inny klucz. W projektancie **przełączania \<T> ** tylko jeden obszar Case może być jednocześnie w widoku rozszerzonym. Jeśli obszar przypadku jest w widoku zwinięte, kliknięcie obszaru wielkość liter zostanie rozwinięte. Zwróć uwagę, że w przypadku zwiniętego przypadku Projektant wyświetla nazwę wyświetlaną działania w przypadku, gdy jest to możliwe. W przeciwnym razie pokazuje przycisk **Dodaj działanie** , który rozszerza wielkość liter po kliknięciu go i umożliwia dodanie działania.

Kliknięcie klucza istniejącej sprawy spowoduje zmianę klucza z etykiety do pola tekstowego, aby można było edytować klucz przypadku.

Istnieją dwa sposoby usunięcia przypadku:

- Wybierz wielkość liter i usuń ją.

- Zaznacz wielkość liter, kliknij prawym przyciskiem myszy, aby wyświetlić menu kontekstowe, a następnie wybierz pozycję **Usuń**.

Pamiętaj, że musisz wybrać sam przypadek, aby go usunąć. Zaznaczenie i usunięcie działania w ramach przypadku powoduje usunięcie tylko tego działania.

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
