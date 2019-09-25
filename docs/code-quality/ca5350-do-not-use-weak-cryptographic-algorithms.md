---
title: 'CA5350: Nie używaj słabych algorytmów kryptograficznych'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aecd052e86a4c0366a1a43cb985ad50ab8862d8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236963"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Kategoria|Microsoft.Cryptography|
|Zmiana podziału|Nieprzerwanie|

> [!NOTE]
> To ostrzeżenie zostało ostatnio zaktualizowane w listopadzie 2015.

## <a name="cause"></a>Przyczyna

Algorytmy <xref:System.Security.Cryptography.TripleDES> szyfrowania, takie jak i algorytmy wyznaczania wartości skrótu, takie jak <xref:System.Security.Cryptography.SHA1> i, <xref:System.Security.Cryptography.RIPEMD160> są uznawane za słabe.

Te algorytmy kryptograficzne nie zapewniają jako stopnia bezpieczeństwa bardziej nowoczesnych odpowiedników. Algorytmy <xref:System.Security.Cryptography.SHA1> wyznaczania <xref:System.Security.Cryptography.RIPEMD160> wartości skrótu i zapewniają mniejszą odporność na kolizje niż bardziej nowoczesne algorytmy wyznaczania wartości skrótu. Algorytm <xref:System.Security.Cryptography.TripleDES> szyfrowania zapewnia mniejszą liczbę bitów zabezpieczeń niż bardziej nowoczesne algorytmy szyfrowania.

## <a name="rule-description"></a>Opis reguły

Słabe algorytmy szyfrowania i funkcje mieszania są obecnie używane z wielu powodów, ale nie powinny być używane w celu zagwarantowania poufności chronionych danych.

Reguła jest wyzwalana, gdy odnajdzie algorytmy 3DES, SHA1 lub RIPEMD160 w kodzie i zgłasza użytkownikowi ostrzeżenie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Użyj opcji silnie silniejszych:

- W przypadku szyfrowania TripleDES Użyj <xref:System.Security.Cryptography.Aes> szyfrowania.

- W przypadku funkcji skrótu SHA1 lub RIPEMD160 należy używać ich w rodzinie [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) (np. <xref:System.Security.Cryptography.SHA512> <xref:System.Security.Cryptography.SHA384> <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń ostrzeżenie z tej reguły, jeśli poziom ochrony wymagany dla danych nie wymaga gwarancji zabezpieczeń.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

Od momentu tego zapisu Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę.

### <a name="sha-1-hashing-violation"></a>Naruszenie skrótu SHA-1

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Narzędzie

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>Naruszenie skrótu RIPEMD160

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Narzędzie

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>TripleDES naruszenie szyfrowania

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Narzędzie

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```