---
title: 'CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: fae67f8c1ffa3b4e6d7cc2f0fbbaf670733f9ff4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923308"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez przerywania — Jeśli typ nie jest widoczny poza zestawem.<br /><br /> Przerywanie — Jeśli typ jest widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
Klasa deklaruje i implementuje pole wystąpienia, które jest <xref:System.IDisposable?displayProperty=fullName> typem, a Klasa nie implementuje. <xref:System.IDisposable>

## <a name="rule-description"></a>Opis reguły
Klasa implementuje <xref:System.IDisposable> interfejs do usuwania niezarządzanych zasobów, których jest właścicielem. Pole wystąpienia, które jest <xref:System.IDisposable> typem wskazuje, że pole jest właścicielem niezarządzanego zasobu. Klasa, która deklaruje <xref:System.IDisposable> pole pośrednio jest właścicielem niezarządzanego zasobu i powinna <xref:System.IDisposable> implementować interfejs. Jeśli Klasa nie jest bezpośrednio własnością żadnych niezarządzanych zasobów, nie należy implementować finalizatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, zaimplementuj <xref:System.IDisposable> i <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> z metody wywołać <xref:System.IDisposable.Dispose%2A> metodę pola.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje klasę, która narusza regułę i klasę, która spełnia reguły przez implementację <xref:System.IDisposable>. Klasa nie implementuje finalizatora, ponieważ Klasa nie jest bezpośrednio własnością żadnych niezarządzanych zasobów.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2213 Pola jednorazowe powinny zostać usunięte](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216 Typy jednorazowe powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215 Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049: Typy, które są właścicielami zasobów natywnych, powinny być jednorazowe](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)