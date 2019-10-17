---
title: 'CA1413: Unikaj pól niepublicznych w typach wartościowych widocznych dla modelu COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d47a7ff2633b94de73435168136060e741080de7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444184"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Unikaj pól niepublicznych w typach wartościowych widocznych dla modelu COM

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ wartości, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) deklaruje pole niepubliczne wystąpienie.

## <a name="rule-description"></a>Opis reguły
Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pola, aby uzyskać informacje, które nie powinny być ujawnione lub które będą miały niezamierzony wpływ na projekt lub zabezpieczenia.

Domyślnie wszystkie publiczne typy wartości są widoczne dla modelu COM. Aby jednak zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności modelu COM. Zestaw zawierający musi być oznaczony atrybutem <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> ustawionym na wartość `false`, a typ musi być oznaczony jako <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawionym na `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły i zachować pole ukrywane, Zmień typ wartości na typ referencyjny lub usuń atrybut <xref:System.Runtime.InteropServices.ComVisibleAttribute> z typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku akceptowalności publicznego ujawnienia pola można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1407: Unikaj składowych statycznych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
