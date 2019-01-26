---
title: 'CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab965c8912144350c527517b79de2914e238976e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037723"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategoria|Microsoft.Cryptography|
|Zmiana kluczowa|Bez podziału|

> [!NOTE]
> To ostrzeżenie Data ostatniej aktualizacji listopada 2015 r.

## <a name="cause"></a>Przyczyna

Tworzenie skrótu funkcji, takich jak <xref:System.Security.Cryptography.MD5> i algorytmów szyfrowania, takich jak <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.RC2> może narazić poważne ryzyko i może spowodować narażenie poufnych informacji za pomocą technik ataku trivial, takich jak ataki siłowe i Kolizje wyznaczania wartości skrótu.

Na poniższej liście algorytmów kryptograficznych podlegają znane ataki kryptograficzne. Algorytm skrótu kryptograficznego <xref:System.Security.Cryptography.MD5> jest podatna na ataki kolizji wyznaczania wartości skrótu.  W zależności od użycia kolizji wyznaczania wartości skrótu może prowadzić do personifikacji przechwyceniem, zmanipulowaniem lub inne rodzaje ataków w systemach, które polegają na unikatowe dane wyjściowe kryptograficznych funkcji skrótu. Algorytmy szyfrowania <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.RC2> są ataki kryptograficzne, które mogą spowodować niezamierzone ujawnienie zaszyfrowanych danych.

## <a name="rule-description"></a>Opis reguły

Uszkodzony kryptograficznych algorytmy nie są uznawane za bezpieczne i należy go unikać, ich użycie. Algorytm wyznaczania wartości skrótu MD5 jest podatny na ataki kolizji znane, że określonych luk w zabezpieczeniach będzie zależeć od kontekstu użytkowania.  Algorytmy wyznaczania wartości skrótu używany do zapewnienia integralności danych (na przykład podpisu pliku lub certyfikat cyfrowy) są szczególnie narażone.  W tym kontekście osoby atakujące można wygenerować dwa oddzielne fragmenty danych, w taki sposób, że niegroźne danych można zastąpić za pomocą złośliwe dane, bez zmiany wartości skrótu lub unieważnienie skojarzonego podpisu cyfrowego.

Algorytmy szyfrowania:

- <xref:System.Security.Cryptography.DES> szyfrowanie zawiera mały rozmiar klucza, który może być ataków siłowych w mniej niż jeden dzień.

- <xref:System.Security.Cryptography.RC2> Szyfrowanie jest podatny na atak związane z kluczem, gdy osoba atakująca znajduje matematyczne relacje między wszystkie wartości klucza.

Ta zasada wyzwala umożliwia znalezienie dowolnego z powyższych funkcji kryptograficznych w kodzie źródłowym i generuje ostrzeżenia dla użytkownika.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Użyj kryptograficznie silniejszych opcji:

- Skróty w użytku MD5, [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) rodziny (na przykład <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>).

- DES i RC2 użytku <xref:System.Security.Cryptography.Aes> szyfrowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły, chyba że jest zostały sprawdzone przez eksperta kryptograficznych.

## <a name="pseudo-code-examples"></a>Przykłady pseudo-kodu

Poniższe przykłady pseudo-kodu ilustrują wzorzec wykrywane przez to reguły i możliwe alternatywy.

### <a name="md5-hashing-violation"></a>MD5 Naruszenie wyznaczania wartości skrótu

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

Rozwiązanie:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>RC2 Naruszenie szyfrowania

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
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

### <a name="des-encryption-violation"></a>Naruszenie szyfrowanie DES

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
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