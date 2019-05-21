---
title: 'CA2208: Poprawnie twórz wystąpienia wyjątków argumentów'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2110a8d0b58d87a4554971cf00af6441d293aa91
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975891"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Poprawnie twórz wystąpienia wyjątków argumentów

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Możliwe przyczyny: w następujących sytuacjach:

- Połączenie jest nawiązywane w przypadku domyślnego (bezparametrowego) konstruktora typu wyjątku, lub pochodzi z <xref:System.ArgumentException>.

- Niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku, lub pochodzi z <xref:System.ArgumentException>.

## <a name="rule-description"></a>Opis reguły

Zamiast wywoływania domyślnego konstruktora, należy wywołać jedną z przeciążeń konstruktora, które umożliwia bardziej zrozumiały komunikat o wyjątku należy podać. Komunikat o wyjątku powinien docelowe dewelopera i wyjaśniają warunek błędu i jak rozwiązać lub uniknąć wyjątku.

Podpisy konstruktorów ciąg jednego i dwa z <xref:System.ArgumentException> i jego typów pochodnych nie są spójne względem pozycji `message` i `paramName` parametrów. Upewnij się, że te konstruktory są wywoływane z argumentami prawidłowy ciąg. Podpisy są następujące:

- <xref:System.ArgumentException>(string `message`)
- <xref:System.ArgumentException>(string `message`, ciąg `paramName`)
- <xref:System.ArgumentNullException>(string `paramName`)
- <xref:System.ArgumentNullException>(string `paramName`, ciąg `message`)
- <xref:System.ArgumentOutOfRangeException>(string `paramName`)
- <xref:System.ArgumentOutOfRangeException>(string `paramName`, ciąg `message`)
- <xref:System.DuplicateWaitObjectException>(string `parameterName`)
- <xref:System.DuplicateWaitObjectException>(string `parameterName`, ciąg `message`)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, wywołanie konstruktora przyjmującego komunikat i/lub nazwę parametru i upewnij się, argumenty są odpowiednie dla typu <xref:System.ArgumentException> wywoływana.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, tylko wtedy, gdy jest to sparametryzowania konstruktora jest wywoływana z argumentami prawidłowy ciąg.

## <a name="example"></a>Przykład

Poniższy kod pokazuje konstruktora, który jest niepoprawnie tworzy wystąpienie <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Poniższy kod naprawia wcześniejszego naruszenia praw, przełączając argumentach konstruktora.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1507: Użyj nameof zamiast ciągów](ca1507.md)