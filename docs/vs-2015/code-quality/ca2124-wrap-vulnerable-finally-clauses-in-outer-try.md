---
title: 'CA2124: Zawijaj jako zagrożone klauzule finally w zewnętrznym elemencie try | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660247"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Kodowanie wrażliwych klauzul finally w zewnętrznym try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 W wersjach 1,0 i 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Metoda publiczna lub chroniona zawiera `try` / `catch` / `finally` bloku. Blok `finally` wydaje się resetować stan zabezpieczeń i nie znajduje się w bloku `finally`.

## <a name="rule-description"></a>Opis reguły
 Ta zasada lokalizuje `try` / `finally` bloków w kodzie, który jest przeznaczony dla wersji 1,0 i 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], które mogą być podatne na złośliwe filtry wyjątków obecne w stosie wywołań. Jeśli w bloku try występują poufne operacje, takie jak personifikacja, a wyjątek jest zgłaszany, filtr można wykonać przed blokiem `finally`. W przypadku przykładu personifikacji oznacza to, że filtr będzie wykonywany jako personifikowany użytkownik. Filtry są obecnie implementowane tylko w Visual Basic.

> [!WARNING]
> W wersji 2,0 i nowszych [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowisko uruchomieniowe automatycznie chroni `try` / `catch` /  `finally` bloku ze złośliwych filtrów wyjątków, jeśli Reset występuje bezpośrednio w metodzie zawierającej blok wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Umieść nieopakowane `try` / `finally` w zewnętrznym bloku try. Zobacz drugi przykład poniżej. Powoduje to wymuszenie wykonania `finally` przed filtrowaniem kodu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="pseudo-code-example"></a>Przykład pseudo kodu

### <a name="description"></a>Opis
 Poniższy pseudo kodu ilustruje wzorzec wykryty przez tę regułę.

### <a name="code"></a>Kod

```
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

## <a name="example"></a>Przykład
 Poniższy pseudo kodu przedstawia wzorzec, którego można użyć do ochrony kodu i spełnienia tej reguły.

```
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
