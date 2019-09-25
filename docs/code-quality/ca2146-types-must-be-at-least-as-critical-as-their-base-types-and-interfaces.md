---
title: 'CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce7870077cb859a25de70c726c78cad1d50270e5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231948"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ przezroczysty pochodzi <xref:System.Security.SecuritySafeCriticalAttribute> od typu, który jest oznaczony za pomocą <xref:System.Security.SecurityCriticalAttribute>lub lub typu, <xref:System.Security.SecuritySafeCriticalAttribute> który jest oznaczony atrybutem, pochodzi <xref:System.Security.SecurityCriticalAttribute> od typu, który jest oznaczony atrybutem.

## <a name="rule-description"></a>Opis reguły
Ta reguła jest uruchamiana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. Naruszenia tej reguły w wyniku <xref:System.TypeLoadException> przejrzystości poziomu 2 dla typu pochodnego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby rozwiązać ten problem, należy oznaczyć typ pochodny lub implementujący atrybutem przezroczystości, który jest co najmniej jako krytyczny dla typu podstawowego lub interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
[!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]