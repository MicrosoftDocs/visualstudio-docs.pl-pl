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
ms.openlocfilehash: d4f02938aed7456762f1ef51da716b6b96bdf437
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232149"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda przezroczysta:

- obsługuje typ wyjątku zabezpieczenia krytyczne dla zabezpieczeń

- ma parametr, który jest oznaczony jako typ krytyczny zabezpieczeń

- ma ogólny parametr z ograniczeniami krytycznymi dotyczącymi zabezpieczeń

- ma lokalną zmienną typu krytycznego dla zabezpieczeń

- odwołuje się do typu, który jest oznaczony jako krytyczny dla zabezpieczeń

- wywołuje metodę, która jest oznaczona jako krytyczna dla zabezpieczeń

- odwołuje się do pola, które jest oznaczone jako krytyczne dla zabezpieczeń

- zwraca typ, który jest oznaczony jako krytyczny dla zabezpieczeń

## <a name="rule-description"></a>Opis reguły

Element kodu, który jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute> ma krytyczne znaczenie dla zabezpieczeń. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli typ przezroczysty próbuje użyć krytycznego typu <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , lub <xref:System.FieldAccessException> jest wywoływany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, wykonaj jedną z następujących czynności:

- Oznacz element kodu, który używa krytycznego kodu zabezpieczeń z <xref:System.Security.SecurityCriticalAttribute> atrybutem

     \- lub —

- Usuń atrybut z elementów kodu, które są oznaczone jako krytyczne dla <xref:System.Security.SecuritySafeCriticalAttribute> zabezpieczeń, a zamiast tego oznacz je atrybutem or <xref:System.Security.SecurityTransparentAttribute>. <xref:System.Security.SecurityCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

W poniższych przykładach przejrzysta Metoda próbuje odwołać się do krytycznej kolekcji ogólnej zabezpieczeń, krytycznego pola zabezpieczeń i krytycznej metody zabezpieczeń.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>