---
title: 'CA5350: nie używaj słabych algorytmów kryptograficznych | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c2c996c383c8834e44e16f382c14b695c83f26
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668997"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nie używaj słabych algorytmów kryptograficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|CheckId|CA5350|
|Kategoria|Microsoft. Cryptography|
|Zmiana kluczowa|Bez przerywania|

> [!NOTE]
> To ostrzeżenie zostało ostatnio zaktualizowane w listopadzie 2015.

## <a name="cause"></a>Przyczyna
 Algorytmy szyfrowania, takie jak <xref:System.Security.Cryptography.TripleDES> i algorytmy wyznaczania wartości skrótu, takie jak <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160>, są uznawane za słabe.

 Te algorytmy kryptograficzne nie zapewniają jako stopnia bezpieczeństwa bardziej nowoczesnych odpowiedników. Algorytmy wyznaczania wartości skrótu kryptograficznego <xref:System.Security.Cryptography.SHA1> i <xref:System.Security.Cryptography.RIPEMD160> zapewniają odporność mniejszą kolizję niż bardziej nowoczesne algorytmy mieszania. Algorytm szyfrowania <xref:System.Security.Cryptography.TripleDES> zapewnia mniejszą liczbę bitów zabezpieczeń niż bardziej nowoczesne algorytmy szyfrowania.

## <a name="rule-description"></a>Opis reguły
 Słabe algorytmy szyfrowania i funkcje mieszania są obecnie używane z wielu powodów, ale nie powinny być używane w celu zagwarantowania poufności chronionych danych.

 Reguła jest wyzwalana, gdy odnajdzie algorytmy 3DES, SHA1 lub RIPEMD160 w kodzie i zgłasza użytkownikowi ostrzeżenie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Użyj opcji silnie silniejszych:

- W przypadku szyfrowania TripleDES Użyj szyfrowania <xref:System.Security.Cryptography.Aes>.

- W przypadku funkcji skrótu SHA1 lub RIPEMD160 należy używać ich w rodzinie [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) (np. <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli poziom ochrony wymagany dla danych nie wymaga gwarancji zabezpieczeń.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu
 Od momentu tego zapisu Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę.

### <a name="sha-1-hashing-violation"></a>Naruszenie skrótu SHA-1

```
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();

```

### <a name="solution"></a>Rozwiązanie

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="ripemd160-br-br-hashing-violation"></a>RIPEMD160 <br /><br />Naruszenie skrótu

```
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();

```

### <a name="solution"></a>Rozwiązanie

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="tripledes-encryption-violation"></a>TripleDES naruszenie szyfrowania

```
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

### <a name="solution"></a>Rozwiązanie

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```