---
title: 'CA2140: kod przezroczysty nie może odwoływać się do krytycznych elementów zabezpieczeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5c3e624e4210e59406fd1d5955cd37c2e83ed79a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602865"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Jawny kod nie może odwoływać się do elementów krytycznych dla zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

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
 Element kodu, który jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute>, ma krytyczne znaczenie dla zabezpieczeń. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli typ przezroczysty próbuje użyć typu krytycznego dla zabezpieczeń, zostanie zgłoszony <xref:System.TypeAccessException>, <xref:System.MethodAccessException> lub <xref:System.FieldAccessException>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wykonaj jedną z następujących czynności:

- Oznacz element kodu, który używa krytycznego kodu zabezpieczeń z atrybutem <xref:System.Security.SecurityCriticalAttribute>

     \- lub-

- Usuń atrybut <xref:System.Security.SecurityCriticalAttribute> z elementów kodu, które są oznaczone jako krytyczne dla zabezpieczeń, a zamiast tego oznacz je atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityTransparentAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach przejrzysta Metoda próbuje odwołać się do krytycznej kolekcji ogólnej zabezpieczeń, krytycznego pola zabezpieczeń i krytycznej metody zabezpieczeń.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Security.SecurityTransparentAttribute><xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
