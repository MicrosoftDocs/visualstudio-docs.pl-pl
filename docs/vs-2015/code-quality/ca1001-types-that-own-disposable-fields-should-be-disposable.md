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
ms.openlocfilehash: 42d21eb0bf32b3abb0eb26d3723123bf085914ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646330"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Typy, które posiadają pola usuwalne, powinny być usuwalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Bez przerywania — Jeśli typ nie jest widoczny poza zestawem.<br /><br /> Przerywanie — Jeśli typ jest widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
 Klasa deklaruje i implementuje pole wystąpienia, które jest typu <xref:System.IDisposable?displayProperty=fullName>, a Klasa nie implementuje <xref:System.IDisposable>.

## <a name="rule-description"></a>Opis reguły
 Klasa implementuje interfejs <xref:System.IDisposable> do usuwania niezarządzanych zasobów, których jest właścicielem. Pole wystąpienia, które jest typu <xref:System.IDisposable> wskazuje, że pole jest właścicielem niezarządzanego zasobu. Klasa, która deklaruje pole <xref:System.IDisposable> pośrednio jest właścicielem niezarządzanego zasobu i powinna implementować interfejs <xref:System.IDisposable>. Jeśli Klasa nie jest bezpośrednio własnością żadnych niezarządzanych zasobów, nie należy implementować finalizatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować <xref:System.IDisposable> i z metody <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> wywołać metodę <xref:System.IDisposable.Dispose%2A> pola.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje klasę, która narusza regułę i klasę, która spełnia reguły przez implementację <xref:System.IDisposable>. Klasa nie implementuje finalizatora, ponieważ Klasa nie jest bezpośrednio własnością żadnych niezarządzanych zasobów.

 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy podstawowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA1049: Typy z zasobami natywnymi powinny być możliwe do likwidacji](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
