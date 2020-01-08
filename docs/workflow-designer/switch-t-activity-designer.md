---
title: Projektant przepływu pracy-Przełącz projektanta działań<T>
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
ms.openlocfilehash: a39e8c1e789c1c448e30962789d1a9ab7f3e65c5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593125"
---
# <a name="switcht-activity-designer"></a>Przełącz\<projektanta aktywności T >

Działanie <xref:System.Activities.Statements.Switch%601> oblicza określone wyrażenie i wykonuje działanie z kolekcji działań, których skojarzony klucz jest zgodny z wartością uzyskaną z oceny.

**\>** Projektant działań służy do tworzenia i konfigurowania działania <xref:System.Activities.Statements.Switch%601> w Projektant przepływu pracy.

## <a name="the-switchtactivity"></a>Działanie przełącznika\<T >

Działanie <xref:System.Activities.Statements.Switch%601> zawiera <xref:System.Activities.Statements.Switch%601.Expression%2A> i słownika <xref:System.Activities.Statements.Switch%601.Cases%2A>. Każdy przypadek w słowniku składa się z pary zawierającej *klucz* i działanie, które służy jako odpowiadająca mu *wartość*. Działanie <xref:System.Activities.Statements.Switch%601> szacuje <xref:System.Activities.Statements.Switch%601.Expression%2A> i porównuje je z każdym z kluczy. W przypadku znalezienia dopasowania zostanie wykonane odpowiednie działanie. Możliwe jest tylko jedno dopasowanie, ponieważ klucze słownika muszą być unikatowe w zależności od typu równości zdefiniowanego przez funkcję porównującą równość słownika. Jeśli nie zostanie znalezione żadne dopasowanie, działanie <xref:System.Activities.Statements.Switch%601.Default%2A> zostanie wykonane.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak używać narzędzia Switch\<T > Activity Designer

Dostęp do **przełącznika\<t >** Designer w kategorii **przepływ sterowania** w **przyborniku**. Po porzucenie go do Projektant przepływu pracy wyświetla okno dialogowe **Wybieranie typów** , aby zezwolić użytkownikowi na określenie typu ogólnego *T* używanego w działaniu <xref:System.Activities.Statements.Switch%601>. Wartość domyślna to **Int32**. Po wybraniu typu ogólnego *t* do projektanta przepływu pracy zostanie dodany **przełącznik < T\>** Designer.

Poniżej znajdują się właściwości **przełącznika < T\>** Designer. Wszystkie te właściwości można edytować w siatce właściwości. Niektóre z nich mogą być również edytowane na powierzchni projektanta.

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.Switch%601> właściwości i opisano sposób ich używania w projektancie.

|Nazwa właściwości|Wymagane|Pomiar|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Fałsz|Określa przyjazną nazwę projektanta działań <xref:System.Activities.Statements.Switch%601>. Wartość domyślna to switch < Int32\>. Wartość można edytować w oknie **Właściwości** lub bezpośrednio w nagłówku projektanta.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Prawda|Określa wyrażenie używane do porównywania z kluczami w kolekcji cases, aby określić przypadek do wykonania.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Określa działanie wykonywane, jeśli nie znaleziono żadnego dopasowania. Kliknij przycisk **Dodaj działanie** w projektancie, aby otworzyć pole **domyślne** , w którym działanie może zostać porzucone.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Określa przypadki, które mają zostać ocenione. Aby dodać przypadek, kliknij przycisk **Dodaj nowy przypadek** u dołu **przełącznika\<t >** Designer. Przycisk zmienia się w polu tekstowym (pole kombi, jeśli typ ogólny wybrany podczas dodawania przełącznika\<T > jest ciągiem lub wyliczeniem). Po dodaniu klucza w polu **wartość wielkości** liter zostanie rozwinięte miejsce i będzie można usunąć działanie, gdzie w tym miejscu tekst wskazówki "upuść aktywność tutaj", aby zdefiniować logikę wykonywania dla przypadku.|

Można dodać wiele przypadków, dopóki klucze przypadków nie są zduplikowane. W przeciwnym razie okno dialogowe błędu wyświetla raport o określonym kluczu Case już istnieje i należy wybrać inny klucz. W oknie **przełącznika\<t >** Designer tylko jeden obszar Case może być jednocześnie w widoku rozszerzonym. Jeśli obszar przypadku jest w widoku zwinięte, kliknięcie obszaru wielkość liter zostanie rozwinięte. Zwróć uwagę, że w przypadku zwiniętego przypadku Projektant wyświetla nazwę wyświetlaną działania w przypadku, gdy jest to możliwe. W przeciwnym razie pokazuje przycisk **Dodaj działanie** , który rozszerza wielkość liter po kliknięciu go i umożliwia dodanie działania.

Kliknięcie klucza istniejącej sprawy spowoduje zmianę klucza z etykiety do pola tekstowego, aby można było edytować klucz przypadku.

Istnieją dwa sposoby usunięcia przypadku:

- Wybierz wielkość liter i usuń ją.

- Zaznacz wielkość liter, kliknij prawym przyciskiem myszy, aby wyświetlić menu kontekstowe, a następnie wybierz pozycję **Usuń**.

Pamiętaj, że musisz wybrać sam przypadek, aby go usunąć. Zaznaczenie i usunięcie działania w ramach przypadku powoduje usunięcie tylko tego działania.

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)
