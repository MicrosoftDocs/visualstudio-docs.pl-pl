---
title: 'CA2130: Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a33b650570981f5496813f575b1ae2413a960026
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920771"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Pole stałej lub element członkowski wyliczenia jest oznaczony przy użyciu <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Opis reguły
Wymuszanie przezroczystości nie jest wymuszane dla wartości stałych, ponieważ kompilatory wbudowują stałe wartości, tak aby nie było wymagane żadne wyszukiwanie w czasie wykonywania. Stałe pola powinny być przezroczyste dla zabezpieczeń, tak aby recenzenci kodu nie zakładali, że przezroczysty kod nie może uzyskać dostępu do stałej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Usuń atrybut SecurityCritical z pola lub wartości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższych przykładach wartość `EnumWithCriticalValues.CriticalEnumValue` enum i stała `CriticalConstant` powodują wystąpienie tego ostrzeżenia. Aby rozwiązać te problemy, Usuń atrybut [`SecurityCritical`], aby zapewnić, że zabezpieczenia są przezroczyste.

[!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]