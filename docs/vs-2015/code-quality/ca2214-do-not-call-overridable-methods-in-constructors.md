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
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662910"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nie należy wywoływać nadpisywalnych metod w konstruktorach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
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
 Poniższy przykład ilustruje efekt naruszenia tej reguły. Aplikacja testowa tworzy wystąpienie `DerivedType`, które powoduje wykonanie jego konstruktora klasy podstawowej (`BadlyConstructedType`). Konstruktor `BadlyConstructedType` niepoprawnie wywołuje metodę wirtualną `DoSomething`. Jako dane wyjściowe są wyświetlane, `DerivedType.DoSomething()` wykonuje i robi to przed wykonaniem konstruktora `DerivedType`.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Wywoływanie podstawowego elementu ctor.** 
**pochodne DoSomething jest wywoływana-zainicjowany? Brak** 
**wywoływania pochodnego elementu ctor.**
