---
title: 'CA1009: Zadeklaruj poprawnie procedury obsługi zdarzeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547891"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Poprawnie deklaruj procedury obsługi zdarzeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Delegat, który obsługuje zdarzenie publiczne lub chronione, nie ma poprawnej sygnatury, zwracanego typu ani nazw parametrów.

## <a name="rule-description"></a>Opis reguły
 Metody obsługi zdarzeń przyjmują dwa parametry. Pierwszy jest typu <xref:System.Object?displayProperty=fullName> i nosi nazwę "Sender". Jest to obiekt, który wywołał zdarzenie. Drugi parametr jest typu <xref:System.EventArgs?displayProperty=fullName> i nosi nazwę "e". To dane, które są skojarzone ze zdarzeniem. Na przykład jeśli zdarzenie jest zgłaszane za każdym razem, gdy plik zostanie otwarty, dane zdarzenia zazwyczaj zawierają nazwę pliku.

 Metody obsługi zdarzeń nie powinny zwracać wartości. W języku programowania C# jest to wskazywane przez zwracany typ `void` . Procedura obsługi zdarzeń może wywoływać wiele metod w wielu obiektach. Jeśli metody mogły zwrócić wartość, w każdym zdarzeniu wystąpią wiele wartości zwracanych i będzie dostępna tylko wartość ostatniej metody, która została wywołana.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Popraw sygnaturę, zwracany typ lub nazwy parametrów delegata. Aby uzyskać szczegółowe informacje, zobacz Poniższy przykład.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia delegata, który jest odpowiedni do obsługi zdarzeń. Metody, które mogą być wywoływane przez ten program obsługi zdarzeń, są zgodne z podpisem określonym w wytycznych dotyczących projektowania. `AlarmEventHandler`jest nazwą typu delegata. `AlarmEventArgs`pochodzi z klasy podstawowej dla danych zdarzenia, <xref:System.EventArgs> i przechowuje dane zdarzenia alarmu.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2109: Przejrzyj widoczne procedury obsługi zdarzeń](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: zdarzenia i Delegaty](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
