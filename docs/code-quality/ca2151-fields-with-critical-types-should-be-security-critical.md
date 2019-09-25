---
title: 'CA2151: Pola typu krytycznego powinny być krytyczne pod względem zabezpieczeń'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46cb99f00bbbd9969899121f82ba591980b5b288
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231922"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Pola typu krytycznego powinny być krytyczne pod względem zabezpieczeń

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Pole przezroczyste zabezpieczeń lub bezpieczne-krytyczne jest zadeklarowane. Jego typ jest określony jako krytyczny pod względem zabezpieczeń. Na przykład:

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

W tym przykładzie `m_field` jest przezroczystym polem zabezpieczeń typu, który ma krytyczne znaczenie dla zabezpieczeń.

## <a name="rule-description"></a>Opis reguły

Aby używać typów krytycznych pod względem zabezpieczeń, kod odwołujący się do typu musi być albo krytyczny pod względem zabezpieczeń, albo bezpieczny-krytyczny pod względem zabezpieczeń. Ta zasada obowiązuje nawet w przypadku odwołania pośredniego. Na przykład w przypadku odwołania do pola przezroczystego, które ma typ krytyczny, kod musi być krytyczny pod względem zabezpieczeń lub bezpieczny pod względem zabezpieczeń. Dlatego pole mające zabezpieczenia przezroczyste lub pole bezpieczne-krytyczne pod względem zabezpieczeń jest mylące, ponieważ przezroczysty kod nadal nie będzie mógł uzyskać dostępu do pola.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy oznaczyć pole <xref:System.Security.SecurityCriticalAttribute> atrybutem lub określić typ, do którego odwołuje się pole zabezpieczenia przezroczyste lub bezpieczne krytyczne.

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]