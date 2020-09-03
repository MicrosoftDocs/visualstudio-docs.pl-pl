---
title: 'CA1026: nie należy używać parametrów domyślnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548449"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Nie należy używać parametrów domyślnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz zawiera zewnętrznie widoczną metodę, która używa domyślnego parametru.

## <a name="rule-description"></a>Opis reguły
 Metody korzystające z parametrów domyślnych są dozwolone pod Common Language Specification (CLS); jednak specyfikacja CLS umożliwia kompilatorom ignorowanie wartości, które są przypisane do tych parametrów. Kod Zapisano dla kompilatorów, które ignorują domyślne wartości parametrów, muszą jawnie podawać argumenty dla każdego domyślnego parametru. Aby zachować zachowanie w różnych językach programowania, metody, które używają parametrów domyślnych, powinny być zastępowane przeciążeniami metod, które udostępniają parametry domyślne.

 Kompilator ignoruje wartości domyślnych parametrów dla rozszerzenia zarządzanego dla języka C++, gdy uzyskuje dostęp do kodu zarządzanego. Kompilator Visual Basic obsługuje metody, które mają domyślne parametry, które używają [opcjonalnego](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) słowa kluczowego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp metodę, która używa domyślnych parametrów z przeciążeniami metod, które dostarczają parametry domyślne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która używa parametrów domyślnych i przeciążonych metod, które zapewniają równoważną funkcjonalność.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1025: Zastąp powtarzalne argumenty tablicą params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Zobacz też
 [Niezależność od języka i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
