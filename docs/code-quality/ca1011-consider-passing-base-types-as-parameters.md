---
title: 'CA1011: Należy rozważyć przekazywanie typów bazowych jako parametrów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9388dc1b6649efd1f43e353e69833ad59ad5ff29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860689"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Należy rozważyć przekazywanie typów bazowych jako parametrów

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Deklaracja metody zawiera parametr formalny, który jest typem pochodnym, a metoda wywołuje tylko członkowie podstawowy typ parametru.

## <a name="rule-description"></a>Opis reguły

Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Jeśli argument jest używana wewnątrz treści metody, określonej metody, która jest wykonywana zależy od typu argumentu. Jeśli dodatkowe funkcje, które są dostarczane przez typ pochodny nie jest wymagana, użycie typu podstawowego umożliwia szersze wykorzystanie metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić typ parametru do jego typ podstawowy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły można bezpiecznie

- Jeśli metoda, która wymaga określonych funkcji, która jest dostarczana przez typ pochodny

     \- lub —

- Aby wymusić typu pochodnego lub typu bardziej pochodnego jest przekazywany do metody.

W takich przypadkach kod będzie bardziej niezawodne z powodu silnego typu sprawdzanie dostarczonego przez kompilatora i środowiska uruchomieniowego.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metodę `ManipulateFileStream`, które mogą być używane tylko w <xref:System.IO.FileStream> obiektu, który narusza tę regułę. Druga metoda `ManipulateAnyStream`, spełnia reguły, zastępując <xref:System.IO.FileStream> parametru za pomocą <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1059: Składowe nie powinny ujawniać niektórych typów konkretnych](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)