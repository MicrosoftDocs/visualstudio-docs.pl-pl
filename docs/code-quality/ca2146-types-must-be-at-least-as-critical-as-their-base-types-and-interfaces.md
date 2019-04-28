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
ms.openlocfilehash: 01a8a5609394f0dd428066e32fb425a2abb486c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542056"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Przezroczysty typ pochodzi z typu, który jest oznaczony przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityCriticalAttribute>, lub typu, który jest oznaczony za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu jest tworzony na podstawie typu, który jest oznaczony przy użyciu <xref:System.Security.SecurityCriticalAttribute> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. Powoduje naruszenie tej zasady przezroczystości poziomu 2 <xref:System.TypeLoadException> przypadku typ pochodny.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem to naruszenie, należy oznaczyć typu pochodnego lub implementującej atrybutem przejrzystości, który jest co najmniej tak krytyczne jak typem bazowym lub interfejsem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]