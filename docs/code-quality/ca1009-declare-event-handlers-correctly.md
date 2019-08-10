---
title: 'CA1009: Poprawnie deklaruj procedury obsługi zdarzeń'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a98ec47688f289fadba66401aca9fcee7b602cdc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923567"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Poprawnie deklaruj procedury obsługi zdarzeń

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Delegat, który obsługuje zdarzenie publiczne lub chronione, nie ma poprawnej sygnatury, zwracanego typu ani nazw parametrów.

## <a name="rule-description"></a>Opis reguły
Metody obsługi zdarzeń przyjmują dwa parametry. Pierwszy jest typu <xref:System.Object?displayProperty=fullName> i nosi nazwę "Sender". Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu <xref:System.EventArgs?displayProperty=fullName> i nosi nazwę "e". To dane, które są skojarzone ze zdarzeniem. Na przykład jeśli zdarzenie jest zgłaszane za każdym razem, gdy plik zostanie otwarty, dane zdarzenia zazwyczaj zawierają nazwę pliku.

Metody obsługi zdarzeń nie powinny zwracać wartości. W języku C# programowania jest to wskazywane przez zwracany typ `void`. Procedura obsługi zdarzeń może wywoływać wiele metod w wielu obiektach. Jeśli metody mogły zwrócić wartość, w każdym zdarzeniu wystąpią wiele wartości zwracanych i będzie dostępna tylko wartość ostatniej metody, która została wywołana.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Popraw sygnaturę, zwracany typ lub nazwy parametrów delegata. Aby uzyskać szczegółowe informacje, zobacz Poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia delegata, który jest odpowiedni do obsługi zdarzeń. Metody, które mogą być wywoływane przez ten program obsługi zdarzeń, są zgodne z podpisem określonym w wytycznych dotyczących projektowania. `AlarmEventHandler`jest nazwą typu delegata. `AlarmEventArgs`pochodzi z klasy podstawowej dla danych zdarzenia, <xref:System.EventArgs>i przechowuje dane zdarzenia alarmu.

[!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
[!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
[!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)