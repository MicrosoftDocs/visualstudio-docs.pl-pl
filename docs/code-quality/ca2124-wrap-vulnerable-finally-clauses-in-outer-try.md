---
title: 'CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a15c5019dd5f3084ff250015e8a9725f4dbf971
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829293"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 W wersjach 1.0 i 1.1 programu .NET Framework, metoda publiczna lub chroniona zawiera `try` / `catch` / `finally` bloku. `finally` Bloku pojawia się, aby zresetować stan zabezpieczeń i nie jest ujęty w `finally` bloku.

## <a name="rule-description"></a>Opis reguły
 Ta zasada lokalizuje `try` / `finally` bloki w kodzie, który jest przeznaczony dla wersji 1.0 i 1.1 programu .NET Framework, które mogą być narażone na filtry wyjątków złośliwego obecne w stosie wywołań. Jeśli poufnych operacje, takie jak personifikacji występują w bloku try, zgłaszany jest wyjątek, filtr, można wykonać przed `finally` bloku. Na przykład personifikacji oznacza to, że filtr jest wykonywany jako nazwa spersonifikowanego użytkownika. Filtry są obecnie implementable tylko w języku Visual Basic.

> [!NOTE]
> W wersji 2.0 i nowsze wersje programu .NET Framework, automatycznie chroni środowisko uruchomieniowe `try` / `catch` /  `finally` uniemożliwiaj filtry wyjątków złośliwy, gdy następuje bezpośrednio w metodzie, zawiera blok wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Umieść nieopakowane `try` / `finally` w zewnętrzny blok try. Zobacz drugim przykładzie poniżej. Zmusza to `finally` do wykonania przed uruchomieniem kodu filtru.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykładowy pseudo-kod

### <a name="description"></a>Opis

Poniższy pseudo-kod przedstawiono wzorzec wykryte przez tę regułę.

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

Pseudo-poniższy kod przedstawia wzorzec służące do ochrony kodu i spełniają tej reguły.

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