---
title: 'CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef4bff83b1921b3cf15b25aaf225645379478f38
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236354"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Typy abstrakcyjne nie powinny mieć konstruktorów

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ jest abstrakcyjny i ma konstruktora.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Konstruktory dla typów abstrakcyjnych mogą być wywoływane tylko przez typy pochodne. Ponieważ konstruktory publiczne tworzą wystąpienia typu i nie można tworzyć wystąpień typu abstrakcyjnego, typ abstrakcyjny, który ma Konstruktor publiczny jest nieprawidłowo zaprojektowany.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, ustaw Konstruktor jako chroniony lub nie deklaruj typu jako abstract.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Typ abstrakcyjny ma konstruktora publicznego.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1012.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

Poniższy fragment kodu zawiera typ abstrakcyjny, który narusza tę regułę.

[!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
[!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

Poniższy fragment kodu naprawia poprzednie naruszenie, zmieniając ułatwienia dostępu konstruktora z `public` do. `protected`

[!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
[!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]