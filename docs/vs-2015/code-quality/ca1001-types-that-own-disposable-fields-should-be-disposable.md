---
title: 'CA1001: typy, które są własnością pól jednorazowych, powinny być jednorazowe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dab4532f082bd81eaa7b812eb038c5957636d453
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548320"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Bez przerywania — Jeśli typ nie jest widoczny poza zestawem.<br /><br /> Przerywanie — Jeśli typ jest widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
 Klasa deklaruje i implementuje pole wystąpienia, które jest <xref:System.IDisposable?displayProperty=fullName> typem, a Klasa nie implementuje <xref:System.IDisposable> .

## <a name="rule-description"></a>Opis reguły
 Klasa implementuje <xref:System.IDisposable> interfejs do usuwania niezarządzanych zasobów, których jest właścicielem. Pole wystąpienia, które jest <xref:System.IDisposable> typem wskazuje, że pole jest właścicielem niezarządzanego zasobu. Klasa, która deklaruje <xref:System.IDisposable> pole pośrednio jest właścicielem niezarządzanego zasobu i powinna implementować <xref:System.IDisposable> interfejs. Jeśli Klasa nie jest bezpośrednio własnością żadnych niezarządzanych zasobów, nie należy implementować finalizatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj <xref:System.IDisposable> i z <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metody wywołać <xref:System.IDisposable.Dispose%2A> metodę pola.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje klasę, która narusza regułę i klasę, która spełnia reguły przez implementację <xref:System.IDisposable> . Klasa nie implementuje finalizatora, ponieważ Klasa nie jest bezpośrednio własnością żadnych niezarządzanych zasobów.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2213: Pola możliwe do likwidacji należy likwidować](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
