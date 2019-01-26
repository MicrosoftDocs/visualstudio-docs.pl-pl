---
title: 'CA1821: Usuwaj puste finalizatory'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01f89e022be966f0d265abd2f4e24b1779ce64b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975182"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuwaj puste finalizatory

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ implementuje finalizatora, który jest pusty, wywołuje tylko finalizator typu podstawowego lub wywołuje tylko warunkowo emitowane metody.

## <a name="rule-description"></a>Opis reguły
 Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Gromadzi informacje o obiekcie, kiedy moduł odśmiecania pamięci uruchomi finalizatora. Oznacza to, czy dwie kolekcje będą wymagane do zbierania obiektu. Pusty finalizator powoduje to dodatkowe obciążenie, bez żadnych korzyści.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń puste finalizatory. Jeśli finalizator jest wymagana do debugowania, ujmij całą finalizator w `#if DEBUG / #endif` dyrektywy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj wiadomości od tej reguły. Nie można wstrzymać finalizację zmniejsza wydajność i oferuje nie korzyści.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano pusty finalizator, który powinien zostać usunięty, finalizator, powinien być sporządzony we `#if DEBUG / #endif` dyrektywy i finalizator, który używa `#if DEBUG / #endif` dyrektywy poprawnie.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]