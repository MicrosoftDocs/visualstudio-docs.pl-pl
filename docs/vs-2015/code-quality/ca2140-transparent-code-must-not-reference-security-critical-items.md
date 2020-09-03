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
ms.openlocfilehash: 6f11125f43fd06b0442d1c40cbd4da41e346fd1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546461"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
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
 Element kodu, który jest oznaczony <xref:System.Security.SecurityCriticalAttribute> atrybutem ma krytyczne znaczenie dla zabezpieczeń. Przezroczysta metoda nie może użyć elementu krytycznego dla zabezpieczeń. Jeśli typ przezroczysty próbuje użyć krytycznego typu <xref:System.TypeAccessException> , <xref:System.MethodAccessException> , lub <xref:System.FieldAccessException> jest wywoływany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wykonaj jedną z następujących czynności:

- Oznacz element kodu, który używa krytycznego kodu zabezpieczeń z <xref:System.Security.SecurityCriticalAttribute> atrybutem

     \- oraz

- Usuń <xref:System.Security.SecurityCriticalAttribute> atrybut z elementów kodu, które są oznaczone jako krytyczne dla zabezpieczeń, a zamiast tego oznacz je <xref:System.Security.SecuritySafeCriticalAttribute> <xref:System.Security.SecurityTransparentAttribute> atrybutem or.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach przejrzysta Metoda próbuje odwołać się do krytycznej kolekcji ogólnej zabezpieczeń, krytycznego pola zabezpieczeń i krytycznej metody zabezpieczeń.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2140.transparentmethodsmustnotreferencecriticalcode/cs/ca2140 - transparentmethodsmustnotreferencecriticalcode.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute>
 <xref:System.Security.SecurityTransparentAttribute>
 <xref:System.Security.SecurityTreatAsSafeAttribute>
 <xref:System.Security?displayProperty=fullName>
