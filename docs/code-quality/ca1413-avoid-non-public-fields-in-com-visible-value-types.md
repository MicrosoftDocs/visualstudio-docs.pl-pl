---
title: 'CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM'
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
ms.openlocfilehash: 0d4fed5b16120ec069eaa4101670c88ad8f3a247
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234650"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM

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

Domyślnie wszystkie publiczne typy wartości są widoczne dla modelu COM. Aby jednak zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności modelu COM. Zestaw zawierający <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> musi być oznaczony zestawem do `false` , a typ <xref:System.Runtime.InteropServices.ComVisibleAttribute> musi być oznaczony z ustawioną na `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły i zachować pole ukrywane, Zmień typ wartości na typ referencyjny lub Usuń <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut z typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku akceptowalności publicznego ujawnienia pola można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1407: Unikaj statycznych elementów członkowskich w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)