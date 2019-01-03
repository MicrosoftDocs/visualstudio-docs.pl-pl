---
title: 'CA5350: Nie używaj słabych algorytmów kryptograficznych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11c13b44c2f09075550dc5872ccf76d00aae4f6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987288"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Kategoria|Microsoft.Cryptography|
|Zmiana kluczowa|Bez podziału|

> [!NOTE]
> To ostrzeżenie Data ostatniej aktualizacji listopada 2015 r.

## <a name="cause"></a>Przyczyna

Algorytmy szyfrowania, takich jak <xref:System.Security.Cryptography.TripleDES> i algorytmy wyznaczania wartości skrótu takich jak <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> są uważane za słabe.

Te algorytmy kryptograficzne nie oferuje tylu Gwarancja bezpieczeństwa jako odpowiednikami nowocześniejszego. Kryptograficznych, algorytmy wyznaczania wartości skrótu <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> zapewniają odporność kolizji, mniej niż bardziej nowoczesne algorytmy wyznaczania wartości skrótu. Algorytm szyfrowania <xref:System.Security.Cryptography.TripleDES> zapewnia mniejszą liczbę bitów zabezpieczeń niż bardziej nowoczesne algorytmy szyfrowania.

## <a name="rule-description"></a>Opis reguły

Słabe szyfrowanie, algorytmy i funkcje wyznaczania wartości skrótu są używane obecnie do szeregu przyczyn, ale nie powinny one być używane dla zagwarantowania poufności danych, które chronią.

Reguła wyzwalania, gdy znajdzie 3DES, SHA1 lub RIPEMD160 algorytmów w kodzie i zgłoszenie ostrzeżenia dla użytkownika.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Użyj kryptograficznie silniejszych opcji:

- W przypadku szyfrowania TripleDES, użyj <xref:System.Security.Cryptography.Aes> szyfrowania.

- Dla funkcji skrótu SHA1 lub RIPEMD160, użyj tych w [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) rodziny (np. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, jeśli poziom ochrony danych przez nie wymaga gwarancji bezpieczeństwa.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

Począwszy od chwili pisania tego dokumentu Poniższy przykładowy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.

### <a name="sha-1-hashing-violation"></a>Naruszenie wyznaczania wartości skrótu SHA-1

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Rozwiązanie:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>RIPEMD160 Naruszenie wyznaczania wartości skrótu

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Rozwiązanie:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>TripleDES szyfrowania naruszenia

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Rozwiązanie:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```