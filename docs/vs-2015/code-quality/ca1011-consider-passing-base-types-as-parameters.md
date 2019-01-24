---
title: 'CA1011: Należy rozważyć przekazywanie typów bazowych jako parametrów | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d3104f7173721668538e6d73c1c5492c5c388ba5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789739"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Rozważ przekazywanie typów podstawowych jako parametrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1059: Składowe nie powinny ujawniać niektórych typów konkretnych](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
