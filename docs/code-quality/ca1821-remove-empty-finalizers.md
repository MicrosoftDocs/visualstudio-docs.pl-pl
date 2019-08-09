---
title: 'CA1821: Usuwaj puste finalizatory'
ms.date: 11/04/2016
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
ms.openlocfilehash: 9c8c4d4ca04c7a9a21cd1e80e4dc06e8d5a92c2f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921375"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuwaj puste finalizatory

|||
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ implementuje finalizator, który jest pusty, wywołuje tylko finalizator typu podstawowego lub wywołuje tylko metody, które są emitowane warunkowo.

## <a name="rule-description"></a>Opis reguły
Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Moduł wyrzucania elementów bezużytecznych uruchomi finalizator przed zebraniem obiektu. Oznacza to, że do zebrania obiektu wymagane są dwie kolekcje. Pusty finalizator wiąże się z tym dodatkowym obciążeniem bez żadnej korzyści.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Usuń pusty finalizator. Jeśli finalizator jest wymagany do debugowania, należy ująć cały finalizator w `#if DEBUG / #endif` dyrektywy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj komunikatu z tej reguły. Niepowodzenie pomijania finalizowania zmniejsza wydajność i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono pusty finalizator, który powinien zostać usunięty, finalizator, który powinien być ujęty w `#if DEBUG / #endif` dyrektywy, i finalizator, który poprawnie `#if DEBUG / #endif` używa dyrektyw.

[!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]