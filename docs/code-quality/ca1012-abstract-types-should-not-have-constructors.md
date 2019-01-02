---
title: 'CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 81a9fe50b4141b10e3946e3494ff325d1cc302b5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825100"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny jest abstrakcyjna i ma on publicznego konstruktora.

## <a name="rule-description"></a>Opis reguły
 Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ze względu na to, że publiczne konstruktory tworzą wystąpienia typu, a nie można utworzyć wystąpienia typu abstrakcyjnego, publiczny konstruktor typu abstrakcyjnego został niepoprawnie zaprojektowany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, konstruktora chronione lub nie deklaruj typu jako abstrakcyjny.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Typ abstrakcyjny ma on publicznego konstruktora.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ ogólny, który narusza tę regułę.

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia wcześniejszego naruszenia praw, zmieniając dostępność konstruktora z `public` do `protected`.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]