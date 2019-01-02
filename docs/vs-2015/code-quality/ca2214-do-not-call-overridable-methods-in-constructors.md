---
title: 'CA2214: Nie wywoływać nadpisywalnych metod w konstruktorach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2785b214cff904618a9e8baf14aafaea371b554b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893028"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Nie wywoływać nadpisywalnych metod w konstruktorach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Konstruktor obiektu niezapieczętowanego typu wywołuje metody wirtualnej zdefiniowanej w swojej klasie.

## <a name="rule-description"></a>Opis reguły
 Po wywołaniu metody wirtualnej rzeczywisty typ, który wykonuje metodę nie jest zaznaczone do czasu wykonywania. Gdy Konstruktor wywołuje metodę wirtualną, jest możliwe, że Konstruktor wystąpienia, które wywołuje metodę nie zostało wykonane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, nie wywołuj metody wirtualne typu z konstruktorów typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Konstruktor powinien przeprojektowane, aby wyeliminować wywołanie wirtualnej metody.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje efekt naruszenie tej zasady. Aplikacja testowa tworzy wystąpienie `DerivedType`, co powoduje, że jej klasa podstawowa (`BadlyConstructedType`) Konstruktor do wykonania. `BadlyConstructedType`jego Konstruktor niepoprawnie wywołuje metodę wirtualną `DoSomething`. Dane wyjściowe pokazują, `DerivedType.DoSomething()` wykonuje, a więc przed jest `DerivedType`przez konstruktora.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Wywoływanie podstawowy ctor. ** 
 **DoSomething pochodnej jest wywoływana - inicjowane? Nie**
**wywołanie pochodzi ctor.**
