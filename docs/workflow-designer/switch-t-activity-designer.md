---
title: Projektant przepływu pracy — przełącznik<T> Projektant działań
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eb83567a7d59dc02779839a5305b9c1c0329912
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434049"
---
# <a name="switcht-activity-designer"></a>Przełącznik\<T > Projektant działań

<xref:System.Activities.Statements.Switch%601> Działanie oblicza określone wyrażenie i wykonuje działania z kolekcji działań, w których skojarzony klucz pasuje do wartości uzyskanej z oceny.

**Przełącznik < T\>**  projektanta działań służy do tworzenia i konfigurowania <xref:System.Activities.Statements.Switch%601> działania w Projektancie przepływu pracy.

## <a name="the-switchtactivity"></a>Przełącznik\<T > działania

A <xref:System.Activities.Statements.Switch%601> zawiera działanie <xref:System.Activities.Statements.Switch%601.Expression%2A> i słownika <xref:System.Activities.Statements.Switch%601.Cases%2A>. Każdy przypadek w słowniku składa się z parą, która zawiera *klucz* i działań, która służy jako odpowiadającymi mu dostawcami *wartość*. <xref:System.Activities.Statements.Switch%601> Ocenia aktywności <xref:System.Activities.Statements.Switch%601.Expression%2A> i porównuje ją z każdego z kluczy. Jeśli zostanie znalezione dopasowanie, odpowiadające mu działanie jest wykonywana. Tylko jedno dopasowanie jest możliwe, ponieważ klucze słownikowe musi być unikatowy, zależnie od typu równości zdefiniowane przez moduł porównujący równość słownika. Jeśli nie zostanie znalezione dopasowanie, <xref:System.Activities.Statements.Switch%601.Default%2A> jest wykonywane działanie.

## <a name="how-to-use-the-switcht-activity-designer"></a>Jak użyć przełącznika\<T > Projektant działań

Dostęp do **przełącznika\<T >** projektanta działań w **przepływ sterowania** kategorii **przybornika**. Po upuszczając go do projektanta przepływów pracy, wyświetla **wybierz typy** okna dialogowego, aby zezwolić użytkownikom na określanie typu ogólnego *T* używane w <xref:System.Activities.Statements.Switch%601> działania. Wartość domyślna to **Int32**. Po typie ogólnym *T* został zaznaczony, **przełącznik < T\>**  Projektant zostanie dodany do projektanta przepływów pracy.

Poniżej przedstawiono właściwości **przełącznik < T\>**  projektanta. Wszystkie te właściwości można edytować w siatce właściwości. Niektóre z nich, można również edytować na powierzchni projektanta.

W poniższej tabeli przedstawiono najbardziej przydatne <xref:System.Activities.Statements.Switch%601> właściwości i w tym artykule opisano, jak są używane w projektancie.

|Nazwa właściwości|Wymagane|Użycie|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Określa przyjazną nazwę <xref:System.Activities.Statements.Switch%601> projektanta działań. Wartość domyślna to przełącznik < Int32\>. Wartość może być edytowana w **właściwości** okna lub bezpośrednio w nagłówku projektanta.<br /><br /> Mimo że <xref:System.Activities.Activity.DisplayName%2A> nie jest bezwzględnie konieczne jest najlepszym rozwiązaniem, aby użyć jednego.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Prawda|Określa wyrażenie używane do porównania z kluczy w kolekcji spraw, aby ustalić którym to przypadku do wykonania.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Określa działanie wykonywane, jeśli nie zostanie znalezione dopasowanie. Kliknij przycisk **dodać działanie** przycisku w projektancie, aby otworzyć **domyślne** pola, których można było porzucić działania.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Określa przypadki, które ma zostać obliczone. Aby dodać przypadek, kliknij **Dodaj nowy przypadek** znajdujący się u dołu **przełącznika\<T >** projektanta. Przycisk zmienia się na pola tekstowego (pola kombi, w przypadku wybrania typu ogólnego, podczas dodawania przełącznika\<T > jest ciągiem lub typu wyliczeniowego). Po dodaniu klucza w **wartość Case** w polu Obszar przypadków rozszerza i działania można było porzucić gdzie tekst wskazówki "W tym miejscu listy activity" Aby zdefiniować logiki wykonywania w przypadku.|

Można dodać wiele przypadków, tak długo, jak wielkość klucze nie są duplikowane. W przeciwnym razie pojawia się okno dialogowe wyświetla raportowania, określonego klucza przypadków już istnieje i czy należy wybrać inny klucz. W **przełącznika\<T >** projektanta, tylko jeden obszar przypadków mogą znajdować się w widoku rozwiniętego w danym momencie. Jeśli obszar przypadków znajduje się w widoku zwiniętym, klikając przypadków obszar powiększa go. Należy zauważyć, że w przypadku zwinięty Projektant pokazuje nazwę wyświetlaną działania w przypadku po prawej stronie czy dowolny. W przeciwnym razie pokazuje **dodać działanie** przycisk, który rozwija tak, kliknij je, a także pozwala dodać działanie.

Klikając klucz istniejącego przypadku zmienia klucza z etykietę do pola tekstowego, dzięki czemu można edytować klucza przypadków.

Istnieją 2 sposoby usunięcie sprawy:

- Wybierz przypadek i usuń go.

- Wybierz przypadek, kliknij prawym przyciskiem myszy aby wyświetlić menu kontekstowe i wybierz **Usuń**.

Należy pamiętać, że należy wybrać tak, aby go usunąć. Wybierając i usuwając działanie w przypadku usuwa tylko działania inaczej.

## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../workflow-designer/control-flow-activity-designers.md)