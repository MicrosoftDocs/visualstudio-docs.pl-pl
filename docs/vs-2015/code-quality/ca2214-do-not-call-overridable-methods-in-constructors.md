---
title: 'CA2214: Nie wywołuj metod do zastąpienia w konstruktorach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad467e880b3281a75db2627108af0e0b2f90ea99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534462"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Konstruktor niezapieczętowanego typu wywołuje metodę wirtualną zdefiniowaną w jej klasie.

## <a name="rule-description"></a>Opis reguły
 Gdy wywoływana jest metoda wirtualna, faktyczny typ, który wykonuje metodę, nie jest wybierany do czasu wykonywania. Gdy Konstruktor wywołuje metodę wirtualną, istnieje możliwość, że Konstruktor wystąpienia, który wywołuje metodę, nie został wykonany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, nie wywołuj metod wirtualnych typu z poziomu konstruktorów typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Konstruktor powinien zostać przeprojektowany w celu wyeliminowania wywołania metody wirtualnej.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje efekt naruszenia tej reguły. Aplikacja testowa tworzy wystąpienie `DerivedType` , które powoduje wykonanie jego konstruktora klasy bazowej ( `BadlyConstructedType` ). `BadlyConstructedType`Konstruktor niepoprawnie wywołuje metodę wirtualną `DoSomething` . Ponieważ dane wyjściowe są wyświetlane, `DerivedType.DoSomething()` wykonywane i robią przed wykonaniem `DerivedType` konstruktora.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Wywoływanie podstawowego elementu ctor.** 
 **Pochodny DoSomething jest wywoływany-zainicjowany? Brak** 
 **wywoływanego pochodnego elementu ctor.**
