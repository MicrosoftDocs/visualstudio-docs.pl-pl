---
title: 'CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f07fc7639bd08c2cae6f7e066c2f8ea0192b22c5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823741"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła jest uruchamiana, gdy metoda oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> zastępuje metodę, która jest przezroczysta lub oznaczona za pomocą <xref:System.Security.SecuritySafeCriticalAttribute>. Reguła jest również uruchamiana, gdy metoda, która jest przezroczysta lub oznaczona za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> zastępuje metodę, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute>.

 Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na próby zmiany ułatwień dostępu zabezpieczeń metodę dalsze górę łańcucha dziedziczenia. Na przykład jeśli metoda wirtualna w klasie bazowej jest przezroczysty lub bezpieczny krytyczny, następnie klasy pochodnej musi zastąpić ją metoda przezroczysty lub bezpieczny krytyczny. Z drugiej strony Jeśli wirtualnej jest krytyczny dla bezpieczeństwa, klasy pochodnej musi zastąpić ją zabezpieczeń metody krytycznej. Ta sama zasada dotyczy implementacji metody interfejsu.

 Zasady przezroczystości są wymuszane, gdy kod jest skompilowana zamiast w czasie wykonywania w trybie JIT, tak, aby obliczenia przejrzystości nie ma informacji o typie dynamicznych. W związku z tym wynik obliczenia przejrzystości musi mieć możliwość można określić wyłącznie z typów statycznych jest kompilowany dokładnie na czas, niezależnie od typu dynamicznego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień przezroczystość metodę, która jest zastępowania metody wirtualnej lub implementującej interfejs do dopasowania przezroczystości, wirtualnej lub metody interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń od tej reguły. Naruszenie tej zasady spowoduje w środowisku uruchomieniowym <xref:System.TypeLoadException> dla zestawów, które używać przezroczystości poziomu 2.

## <a name="examples"></a>Przykłady

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency/cs/ca2134 - methodsmustoverridewithconsistenttransparency.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
