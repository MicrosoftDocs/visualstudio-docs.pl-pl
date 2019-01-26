---
title: 'CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f9b0e55a7417d60187572d3f49d8ae547ff04aa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54995236"
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub publiczny zagnieżdżony deklaruje tylko statyczne elementy członkowskie i ma publiczny lub chroniony konstruktor domyślny.

## <a name="rule-description"></a>Opis reguły
 Konstruktor jest zbędny, ponieważ wywołanie statycznego elementu członkowskiego nie wymaga wystąpienia tego typu. Ponadto ponieważ typ nie ma niestatycznych elementów członkowskich, tworzenia wystąpienia nie zapewnia dostępu do dowolnych elementów członkowskich typu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń domyślnego konstruktora, lub Oznacz jako prywatne.

> [!NOTE]
>  Niektóre kompilatory automatycznie tworzyć publicznego konstruktora domyślnego, jeśli typ nie zdefiniujesz żadnych konstruktorów. Jeśli ma to miejsce w przypadku danego typu, Dodaj Konstruktor prywatny, aby wyeliminować naruszenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Obecność konstruktora sugeruje, że typ nie jest typu statycznego.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę. Należy zauważyć, że w kodzie źródłowym jest Brak domyślnego konstruktora. Gdy ten kod jest kompilowany do zestawu, kompilator języka C# powoduje wstawienie domyślnego konstruktora, który będzie narusza tę regułę. Aby rozwiązać ten problem, należy zadeklarować Konstruktor prywatny.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]