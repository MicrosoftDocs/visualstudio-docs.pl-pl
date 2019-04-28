---
title: 'CA1053: Statyczne typy przechowujące nie powinny mieć konstruktorów'
ms.date: 11/04/2016
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
ms.openlocfilehash: 52f04355a266f87a039b8197675c2f5377b840ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388311"
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
> Niektóre kompilatory automatycznie tworzyć publicznego konstruktora domyślnego, jeśli typ nie zdefiniujesz żadnych konstruktorów. Jeśli ma to miejsce w przypadku danego typu, Dodaj Konstruktor prywatny, aby wyeliminować naruszenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Obecność konstruktora sugeruje, że typ nie jest typu statycznego.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę. Należy zauważyć, że w kodzie źródłowym jest Brak domyślnego konstruktora. Gdy ten kod jest kompilowany do zestawu, kompilator języka C# powoduje wstawienie domyślnego konstruktora, który będzie narusza tę regułę. Aby rozwiązać ten problem, należy zadeklarować Konstruktor prywatny.

 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]