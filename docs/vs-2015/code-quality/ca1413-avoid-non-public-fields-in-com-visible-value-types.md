---
title: 'CA1413: Unikaj pól niepublicznych w typach wartości widocznych dla modelu COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548463"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Unikaj niepublicznych pól w typach wartości widocznych w modelu COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ wartości, który jest jawnie oznaczony jako widoczny dla Component Object Model (COM) deklaruje pole niepubliczne wystąpienie.

## <a name="rule-description"></a>Opis reguły
 Pola niepubliczne wystąpień typów wartości widocznych dla modelu COM są widoczne dla klientów COM. Przejrzyj zawartość pola, aby uzyskać informacje, które nie powinny być ujawnione lub które będą miały niezamierzony wpływ na projekt lub zabezpieczenia.

 Domyślnie wszystkie publiczne typy wartości są widoczne dla modelu COM. Aby jednak zmniejszyć liczbę fałszywych wartości dodatnich, ta reguła wymaga jawnego określenia widoczności modelu COM. Zestaw zawierający musi być oznaczony <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> zestawem do `false` , a typ musi być oznaczony z <xref:System.Runtime.InteropServices.ComVisibleAttribute> ustawioną na `true` .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły i zachować pole ukrywane, Zmień typ wartości na typ referencyjny lub Usuń <xref:System.Runtime.InteropServices.ComVisibleAttribute> atrybut z typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku akceptowalności publicznego ujawnienia pola można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1407: Unikaj statycznych składowych w typach widocznych dla modelu COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Oznacz zestawy atrybutem ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z niezarządzanym kodem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [uprawniającym do współdziałania typów .NET](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
