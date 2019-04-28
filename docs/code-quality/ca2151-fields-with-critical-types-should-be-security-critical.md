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
ms.openlocfilehash: 2b75425d35e51125b0cfe1f76c8c18d7f155a12c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796746"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151: Pola typu krytycznego powinny być krytyczne pod względem zabezpieczeń

|||
|-|-|
|TypeName||
|CheckId|CA2151|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

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

W tym przykładzie `m_field` jest polem przezroczystym zabezpieczeń typu, który jest krytyczny dla bezpieczeństwa.

## <a name="rule-description"></a>Opis reguły

Aby używać typów krytycznych pod względem zabezpieczeń, kod odwołujący się do typu musi być albo krytyczny pod względem zabezpieczeń, albo bezpieczny-krytyczny pod względem zabezpieczeń. Ta zasada obowiązuje nawet w przypadku odwołania pośredniego. Na przykład w przypadku odwołania do pola przezroczystego, które ma typ krytyczny, kod musi być krytyczny pod względem zabezpieczeń lub bezpieczny pod względem zabezpieczeń. Dlatego pole mające zabezpieczenia przezroczyste lub pole bezpieczne-krytyczne pod względem zabezpieczeń jest mylące, ponieważ przezroczysty kod nadal nie będzie mógł uzyskać dostępu do pola.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaznaczyć pole z <xref:System.Security.SecurityCriticalAttribute> atrybut lub zmień typ, który jest przywoływany przez pole albo zabezpieczeń przezroczysty lub bezpieczny krytycznych.

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