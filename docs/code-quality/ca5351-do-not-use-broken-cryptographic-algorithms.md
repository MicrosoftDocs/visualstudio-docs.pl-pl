---
title: 'CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2729e74e3abf6be2ae5b17a836d920c1376decd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236948"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych

|||
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategoria|Microsoft.Cryptography|
|Zmiana podziału|Nieprzerwanie|

> [!NOTE]
> To ostrzeżenie zostało ostatnio zaktualizowane w listopadzie 2015.

## <a name="cause"></a>Przyczyna

Funkcje tworzenia skrótów, takie <xref:System.Security.Cryptography.MD5> jak i algorytmy szyfrowania <xref:System.Security.Cryptography.DES> , <xref:System.Security.Cryptography.RC2> takie jak i mogą ujawniać znaczne ryzyko i mogą powodować narażenie poufnych informacji przez proste techniki ataków, takie jak ataki typu "odczynniki" i " kolizje skrótów.

Lista algorytmów kryptograficznych poniżej podlega znanym atakom kryptograficznym. Algorytm <xref:System.Security.Cryptography.MD5> wyznaczania wartości skrótu jest objęty atakami polegającymi na kolizji.  W zależności od użycia kolizja skrótów może prowadzić do personifikacji, naruszenia lub innego rodzaju ataków w systemach, które opierają się na unikatowych danych wyjściowych funkcji tworzenia skrótów. Algorytmy <xref:System.Security.Cryptography.DES> szyfrowania i <xref:System.Security.Cryptography.RC2> podlegają atakom kryptograficznym, które mogą spowodować niezamierzone ujawnienie zaszyfrowanych danych.

## <a name="rule-description"></a>Opis reguły

Uszkodzone algorytmy kryptograficzne nie są uznawane za bezpieczne i nie należy ich stosować. Algorytm wyznaczania wartości skrótu MD5 jest podatny na znane ataki kolizji, chociaż konkretna usterka różni się w zależności od kontekstu użytkowania.  Algorytmy wyznaczania wartości skrótu używane do zapewnienia integralności danych (na przykład sygnatury pliku lub certyfikatu cyfrowego) są szczególnie narażone.  W tym kontekście osoby atakujące mogą generować dwa oddzielne fragmenty danych, dzięki czemu niegroźne dane mogą zostać zastąpione złośliwymi danymi, bez zmiany wartości skrótu ani unieważniania skojarzonego podpisu cyfrowego.

Dla algorytmów szyfrowania:

- <xref:System.Security.Cryptography.DES>Szyfrowanie zawiera mały rozmiar klucza, który może być wymuszany w ciągu krótszym niż dzień.

- <xref:System.Security.Cryptography.RC2>szyfrowanie jest podatne na atak z kluczem pokrewnym, gdzie osoba atakująca znajdzie relacje matematyczne między wszystkimi wartościami klucza.

Ta reguła jest wyzwalana po znalezieniu którejkolwiek z powyższych funkcji kryptograficznych w kodzie źródłowym i zgłaszaniu użytkownikowi ostrzeżenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Użyj opcji silnie silniejszych:

- W przypadku algorytmu MD5 należy używać skrótów w rodzinie [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) (na przykład <xref:System.Security.Cryptography.SHA512> <xref:System.Security.Cryptography.SHA384>,,, <xref:System.Security.Cryptography.SHA256>).

- W przypadku algorytmu DES i RC2 <xref:System.Security.Cryptography.Aes> należy użyć szyfrowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły, chyba że została sprawdzona przez eksperta kryptograficznego.

## <a name="pseudo-code-examples"></a>Przykłady pseudo kodu

Poniższe pseudo kodu przykładowe ilustrują wzorzec wykrywany przez tę regułę i możliwe alternatywy.

### <a name="md5-hashing-violation"></a>Naruszenie skrótu MD5

```csharp
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();
```

Narzędzie

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="rc2-encryption-violation"></a>Naruszenie szyfrowania RC2

```csharp
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();
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

### <a name="des-encryption-violation"></a>Naruszenie szyfrowania DES

```csharp
using System.Security.Cryptography;
...
DES encAlg = DES.Create();
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