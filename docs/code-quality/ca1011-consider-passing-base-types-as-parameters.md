---
title: 'CA1011: Rozważ przekazywanie typów podstawowych jako parametrów'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dcb5937f58088684e7bfc204ab4143434b0684ae
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236408"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Rozważ przekazywanie typów podstawowych jako parametrów

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Deklaracja metody zawiera formalny parametr, który jest typem pochodnym, a metoda wywołuje tylko elementy członkowskie typu podstawowego parametru.

## <a name="rule-description"></a>Opis reguły

Jeśli typ podstawowy jest określony jako parametr w deklaracji metody, dowolny typ, który pochodzi od typu podstawowego, może zostać przekazany jako odpowiadający argument do metody. Gdy argument jest używany wewnątrz treści metody, określona metoda jest zależna od typu argumentu. Jeśli dodatkowe funkcje dostarczone przez typ pochodny nie są wymagane, użycie typu podstawowego umożliwia szersze użycie metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień typ parametru na jego typ podstawowy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły

- Jeśli metoda wymaga określonej funkcjonalności, która jest dostarczana przez typ pochodny

     \- lub —

- Aby wymusić, że tylko typ pochodny lub bardziej pochodny typ jest przekazanie do metody.

W takich przypadkach kod będzie bardziej niezawodny ze względu na ścisłe sprawdzanie typu dostarczone przez kompilator i środowisko uruchomieniowe.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę, `ManipulateFileStream`, która może być używana tylko <xref:System.IO.FileStream> z obiektem, co narusza tę regułę. Druga metoda `ManipulateAnyStream`,,, spełnia regułę przez <xref:System.IO.FileStream> zastąpienie parametru za pomocą <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1059: Składowe nie powinny ujawniać niektórych typów konkretnych](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)