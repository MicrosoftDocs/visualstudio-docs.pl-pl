---
title: 'CA1401: Elementy P-Invoke nie powinny być widoczne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d4a0a1c001407d947988497c422fdb8e88dd7c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234896"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: Elementy P/Invoke nie powinny być widoczne

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda publiczna lub chroniona w typie publicznym ma <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybut (również zaimplementowany `Declare` przez słowo kluczowe in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Opis reguły
Metody, które są oznaczone <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutem (lub metodami, które są zdefiniowane za `Declare` pomocą słowa kluczowego in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), używają usług wywołania platformy w celu uzyskania dostępu do kodu niezarządzanego. Takie metody nie powinny być udostępniane. Utrzymując te metody w trybie prywatnym lub wewnętrznym, upewnij się, że biblioteka nie może zostać użyta w celu naruszenia zabezpieczeń przez umożliwienie wywołujących dostępu do niezarządzanych interfejsów API, które nie mogły ich wywołać w przeciwnym razie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień poziom dostępu metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład deklaruje metodę, która narusza tę regułę.

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]