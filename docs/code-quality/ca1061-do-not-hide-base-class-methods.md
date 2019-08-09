---
title: 'CA1061: Nie ukrywaj metod klasy bazowej'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f13ac29028472384cfadbf9c397e578f6509670
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922428"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Nie ukrywaj metod klasy bazowej

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ pochodny deklaruje metodę o tej samej nazwie i z tą samą liczbą parametrów co jedna z jej metod podstawowych; jeden lub więcej parametrów jest podstawowym typem odpowiadającego parametru w metodzie podstawowej; i wszystkie pozostałe parametry mają typy, które są identyczne z odpowiednimi parametrami w metodzie podstawowej.

## <a name="rule-description"></a>Opis reguły
Metoda w typie podstawowym jest ukryta przez metodę o identycznej nazwie w typie pochodnym, gdy sygnatura parametru metody pochodnej różni się tylko przez typy, które są bardziej słabo wyprowadzane niż odpowiednie typy w podpisie parametru metody podstawowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, Usuń lub Zmień nazwę metody albo Zmień podpis parametru tak, aby metoda nie ukrywał metody podstawowej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia metodę, która narusza regułę.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]