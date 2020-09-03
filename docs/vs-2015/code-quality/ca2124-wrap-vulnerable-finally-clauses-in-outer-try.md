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
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544303"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124: Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 W wersjach 1,0 i 1,1 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] metody publicznej lub chronionej zawiera `try` / `catch` / `finally` blok. `finally`Zostanie wyświetlony blok służący do resetowania stanu zabezpieczeń i nie jest on ujęty w `finally` bloku.

## <a name="rule-description"></a>Opis reguły
 Ta zasada umożliwia zlokalizowanie `try` / `finally` bloków w kodzie, które są przeznaczone dla wersji 1,0 i 1,1, [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] które mogą być podatne na złośliwe filtry wyjątków obecne w stosie wywołań. Jeśli w bloku try występują poufne operacje, takie jak personifikacja, a wyjątek jest zgłaszany, filtr można wykonać przed `finally` blokiem. W przypadku przykładu personifikacji oznacza to, że filtr będzie wykonywany jako personifikowany użytkownik. Filtry są obecnie implementowane tylko w Visual Basic.

> [!WARNING]
> W wersji 2,0 i nowszych systemu [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowisko uruchomieniowe automatycznie chroni `try` / `catch` /  `finally` blok przed złośliwymi filtrami wyjątków, jeśli Reset występuje bezpośrednio w metodzie zawierającej blok wyjątku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Umieść niezapakowany `try` / `finally` w zewnętrznym bloku try. Zobacz drugi przykład poniżej. Wymusza to `finally` wykonanie przed filtrowaniem kodu.

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
