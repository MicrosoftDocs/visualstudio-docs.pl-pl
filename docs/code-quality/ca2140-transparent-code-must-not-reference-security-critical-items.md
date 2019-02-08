---
title: 'CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4462bb8ef65fdf593ab0bf64813c19af5d390d97
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916820"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda przezroczysty.

- obsługuje typ wyjątków krytycznych zabezpieczeń

- ma parametr, który jest oznaczony jako typu krytycznego dla zabezpieczeń

- ma parametr ogólny z ograniczeniami krytyczne zabezpieczeń

- ma zmiennej lokalnej typu krytycznego dla zabezpieczeń

- odwołuje się do typu, która jest oznaczona jako zabezpieczeń krytycznych

- wywołuje metodę, która jest oznaczona jako zabezpieczeń krytycznych

- odwołuje się do pola, która jest oznaczona jako zabezpieczeń krytycznych

- Zwraca typ, który jest oznaczony jako zabezpieczeń krytycznych

## <a name="rule-description"></a>Opis reguły

Element kodu, który jest oznaczony za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu jest krytyczny dla bezpieczeństwa. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli przezroczysty typ próbuje użyć typu krytycznego dla zabezpieczeń <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , lub <xref:System.FieldAccessException> jest wywoływane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, wykonaj jedną z następujących czynności:

- Oznacz element kodu, który korzysta z kodu krytycznego zabezpieczeń za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu

     \- lub —

- Usuń <xref:System.Security.SecurityCriticalAttribute> atrybut od elementów kodu, które są oznaczone jako zabezpieczeń krytycznych i zamiast tego oznacz je za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityTransparentAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

W poniższych przykładach metoda przezroczysta pod względem próbuje odwołania zabezpieczeń krytycznych kolekcji ogólnych, zabezpieczeń krytycznych pola i metody krytycznej zabezpieczeń.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>