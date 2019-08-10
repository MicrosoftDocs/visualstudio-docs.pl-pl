---
title: 'CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c75c7c240f694b18caacefc0f9b1ee07f54faf36
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920801"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
W wersjach 1,0 i 1,1 .NET Framework `try` Metoda publiczna lub chroniona zawiera / `catch` / `finally` blok. `finally` Zostanie wyświetlony `finally` blok służący do resetowania stanu zabezpieczeń i nie jest on ujęty w bloku.

## <a name="rule-description"></a>Opis reguły
Ta zasada umożliwia zlokalizowanie `try` / `finally` bloków w kodzie, które są przeznaczone dla wersji 1,0 i 1,1 .NET Framework, które mogą być podatne na złośliwe filtry wyjątków obecne w stosie wywołań. Jeśli w bloku try występują poufne operacje, takie jak personifikacja, a wyjątek jest zgłaszany, filtr można wykonać przed `finally` blokiem. W przypadku przykładu personifikacji oznacza to, że filtr będzie wykonywany jako personifikowany użytkownik. Filtry są obecnie implementowane tylko w Visual Basic.

> [!NOTE]
> W wersji 2,0 i nowszych `try` .NET Framework środowisko uruchomieniowe automatycznie chroni / `catch` /  `finally` blok przed złośliwymi filtrami wyjątków, jeśli Reset występuje bezpośrednio w metodzie, która zawiera blok wyjątków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Umieść niezapakowany `try` / wzewnętrznymblokutry`finally` . Zobacz drugi przykład poniżej. Wymusza `finally` to wykonanie przed filtrowaniem kodu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu

### <a name="description"></a>Opis

Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę.

```csharp
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

Poniższy pseudo kodu przedstawia wzorzec, którego można użyć do ochrony kodu i spełnienia tej reguły.

```csharp
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```