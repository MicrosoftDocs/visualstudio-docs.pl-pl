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
ms.openlocfilehash: 9f9425ab1ea9eadd3bd06d950118ce83ba5c35f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231645"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Poprawnie twórz wystąpienia wyjątków argumentów

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Możliwe przyczyny są następujące:

- Wykonano wywołanie domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest lub pochodzi od, <xref:System.ArgumentException>.

- Do sparametryzowanego konstruktora typu wyjątku jest przenoszona niepoprawnym argumentem ciągu, który jest lub pochodzi od <xref:System.ArgumentException>,.

## <a name="rule-description"></a>Opis reguły

Zamiast wywoływania domyślnego konstruktora, wywołaj jedno z przeciążeń konstruktora, które pozwala na podano bardziej zrozumiały komunikat wyjątku. Komunikat o wyjątku powinien wskazywać dewelopera i jasno wyjaśnić warunek błędu oraz jak poprawić lub uniknąć wyjątku.

Sygnatury jednego i dwóch konstruktorów <xref:System.ArgumentException> ciągów i jego typów pochodnych nie są spójne z uwzględnieniem pozycji `message` i `paramName` parametrów. Upewnij się, że te konstruktory są wywoływane z prawidłowymi argumentami ciągu. Podpisy są następujące:

- <xref:System.ArgumentException>(ciąg `message`)
- <xref:System.ArgumentException>(String `message`, String `paramName`)
- <xref:System.ArgumentNullException>(ciąg `paramName`)
- <xref:System.ArgumentNullException>(String `paramName`, String `message`)
- <xref:System.ArgumentOutOfRangeException>(ciąg `paramName`)
- <xref:System.ArgumentOutOfRangeException>(String `paramName`, String `message`)
- <xref:System.DuplicateWaitObjectException>(ciąg `parameterName`)
- <xref:System.DuplicateWaitObjectException>(String `parameterName`, String `message`)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Wywołaj konstruktora, który przyjmuje komunikat, nazwę parametru lub oba parametry, i upewnij się, że argumenty są odpowiednie dla typu <xref:System.ArgumentException> wywoływanego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły tylko wtedy, gdy Konstruktor sparametryzowany jest wywoływany z prawidłowymi argumentami ciągu.

## <a name="example"></a>Przykład

Poniższy kod przedstawia konstruktora, który nieprawidłowo tworzy wystąpienie wystąpienia <xref:System.ArgumentNullException>.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

Poniższy kod naprawia poprzednie naruszenie przez przełączenie argumentów konstruktora.

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1507: Użyj nameof zamiast ciągu](ca1507.md)