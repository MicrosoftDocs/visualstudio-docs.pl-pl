---
title: 'CA2208: Poprawne wystąpienia wyjątków argumentów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f714dce2691012ae5f5b4cf6dc015160acb0c5ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952756"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Poprawne wystąpienia wyjątków argumentów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Możliwe przyczyny: w następujących sytuacjach:

-   Połączenie jest nawiązywane w przypadku domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest lub pochodzi z [System.ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

-   Niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku, który jest lub pochodzi z [System.ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Opis reguły
 Zamiast wywoływania domyślnego konstruktora, należy wywołać jedną z przeciążeń konstruktora, które umożliwia bardziej zrozumiały komunikat o wyjątku należy podać. Komunikat o wyjątku powinien docelowe dewelopera i wyjaśniają warunek błędu i jak rozwiązać lub uniknąć wyjątku.

 Podpisy konstruktorów ciąg jednego i dwa z <xref:System.ArgumentException> i jego typów pochodnych nie są zgodne w odniesieniu do `message` i `paramName` parametrów. Upewnij się, że te konstruktory są wywoływane z argumentami prawidłowy ciąg. Podpisy są następujące:

 <xref:System.ArgumentException>(string `message`)

 <xref:System.ArgumentException>(string `message`, ciąg `paramName`)

 <xref:System.ArgumentNullException>(string `paramName`)

 <xref:System.ArgumentNullException>(string `paramName`, ciąg `message`)

 <xref:System.ArgumentOutOfRangeException>(string `paramName`)

 <xref:System.ArgumentOutOfRangeException>(string `paramName`, ciąg `message`)

 <xref:System.DuplicateWaitObjectException>(string `parameterName`)

 <xref:System.DuplicateWaitObjectException>(string `parameterName`, ciąg `message`)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołanie konstruktora przyjmującego komunikat i/lub nazwę parametru i upewnij się, argumenty są odpowiednie dla typu <xref:System.ArgumentException> wywoływana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, tylko wtedy, gdy jest to sparametryzowania konstruktora jest wywoływana z argumentami prawidłowy ciąg.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje konstruktora, który jest niepoprawnie tworzy wystąpienie typu ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia powyżej naruszenie, przełączając argumentach konstruktora.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
