---
title: 'CA1061: nie ukrywaj metod klasy bazowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 24579e6aa3ba1bf70ed6f195091152b60f3232a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604017"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Nie należy ukrywać metod klasy bazowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Kategoria|Microsoft. Design|
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

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]
