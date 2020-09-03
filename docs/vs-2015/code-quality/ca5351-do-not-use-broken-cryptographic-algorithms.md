---
title: CA5351 nie używają uszkodzonych algorytmów kryptograficznych | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad4698fe469176ae8ed590c44b4efbb4ccf39de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545057"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nie używaj uszkodzonych algorytmów kryptograficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|Kategoria|Microsoft. Cryptography|
|Zmiana kluczowa|Bez przerywania|

> [!NOTE]
> To ostrzeżenie zostało ostatnio zaktualizowane w listopadzie 2015.

## <a name="cause"></a>Przyczyna
 Funkcje tworzenia skrótów, takie jak <xref:System.Security.Cryptography.MD5> i algorytmy szyfrowania, takie jak <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.RC2> mogą ujawniać znaczne ryzyko i mogą powodować narażenie poufnych informacji przez proste techniki ataków, takie jak ataki z wymuszeniem i kolizje skrótów.

 Lista algorytmów kryptograficznych poniżej podlega znanym atakom kryptograficznym. Algorytm wyznaczania wartości skrótu <xref:System.Security.Cryptography.MD5> jest objęty atakami polegającymi na kolizji.  W zależności od użycia kolizja skrótów może prowadzić do personifikacji, naruszenia lub innego rodzaju ataków w systemach, które opierają się na unikatowych danych wyjściowych funkcji tworzenia skrótów. Algorytmy szyfrowania <xref:System.Security.Cryptography.DES> i <xref:System.Security.Cryptography.RC2> podlegają atakom kryptograficznym, które mogą spowodować niezamierzone ujawnienie zaszyfrowanych danych.

## <a name="rule-description"></a>Opis reguły
 Uszkodzone algorytmy kryptograficzne nie są uznawane za bezpieczne i nie należy ich stosować. Algorytm wyznaczania wartości skrótu MD5 jest podatny na znane ataki kolizji, chociaż konkretna usterka różni się w zależności od kontekstu użytkowania.  Algorytmy wyznaczania wartości skrótu używane do zapewnienia integralności danych (np. podpisu pliku lub certyfikatu cyfrowego) są szczególnie podatne na ataki.  W tym kontekście osoby atakujące mogą generować dwa oddzielne fragmenty danych, dzięki czemu niegroźne dane mogą zostać zastąpione złośliwymi danymi, bez zmiany wartości skrótu ani unieważniania skojarzonego podpisu cyfrowego.

 Dla algorytmów szyfrowania:

- <xref:System.Security.Cryptography.DES> Szyfrowanie zawiera mały rozmiar klucza, który może być wymuszany w ciągu krótszym niż dzień.

- <xref:System.Security.Cryptography.RC2> szyfrowanie jest podatne na atak z kluczem pokrewnym, gdzie osoba atakująca znajdzie relacje matematyczne między wszystkimi wartościami klucza.

  Ta reguła jest wyzwalana po znalezieniu którejkolwiek z powyższych funkcji kryptograficznych w kodzie źródłowym i zgłaszaniu użytkownikowi ostrzeżenia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Użyj opcji silnie silniejszych:

- W przypadku algorytmu MD5 należy używać skrótów w rodzinie [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) (np. <xref:System.Security.Cryptography.SHA512> <xref:System.Security.Cryptography.SHA384> <xref:System.Security.Cryptography.SHA256> ).

- W przypadku algorytmu DES i RC2 należy użyć <xref:System.Security.Cryptography.Aes> szyfrowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, chyba że została sprawdzona przez eksperta kryptograficznego.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu
 Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę i możliwe alternatywy.

### <a name="md5-hashing-violation"></a>Naruszenie skrótu MD5

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Rozwiązanie

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>Naruszenie szyfrowania RC2

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

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

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Naruszenie szyfrowania

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

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