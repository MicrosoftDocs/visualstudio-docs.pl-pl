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
ms.openlocfilehash: c3c5d2df6be4fef281d91794b5b71bfa0c3e653f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779678"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Poprawnie deklaruj procedury obsługi zdarzeń

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Delegat, który obsługuje zdarzenie publiczne lub chronione nie ma poprawnej sygnatury zwracanego typu lub nazwy parametrów.

## <a name="rule-description"></a>Opis reguły
 Metody obsługi zdarzeń przyjmują dwa parametry. Pierwszy jest typu <xref:System.Object?displayProperty=fullName> i nosi nazwę "nadawca". Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu <xref:System.EventArgs?displayProperty=fullName> i nosi nazwę "e". To dane, które są skojarzone ze zdarzeniem. Na przykład jeśli zdarzenie jest wywoływane zawsze wtedy, gdy plik jest otwarty, dane zdarzeń zwykle zawiera nazwę pliku.

 Metody obsługi zdarzeń powinny zwracać wartości. W języku programowania C#, jest to wskazywane przez zwracany typ `void`. Program obsługi zdarzeń można wywołać wiele metod w wielu obiektów. Jeśli zezwolono metod w celu zwrócenia wartości, z wieloma wartościami zwracanymi wystąpiłyby dla każdego zdarzenia, a wartość ostatniego metodę, która została wywołana będą dostępne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, popraw sygnatury zwracanego typu i nazwy parametru delegata. Aby uzyskać szczegółowe informacje Zobacz poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje delegata, który jest odpowiedni do obsługi zdarzeń. Metody, które może być wywoływany przez ten program obsługi zdarzeń są zgodne z podpisu, który jest określony w wytycznych projektowych. `AlarmEventHandler` jest nazwą typu delegata. `AlarmEventArgs` pochodzi z klasy bazowej dla danych zdarzeń <xref:System.EventArgs>, i przechowuje alarmu dane zdarzenia.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.EventArgs?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>
- [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)