---
title: 'CA1026: Nie można używać parametrów domyślnych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9a55d8bc3bd7824733bf0d3dcfa205c1bafa1841
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53930314"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Nie można używać parametrów domyślnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz zawiera widoczne na zewnątrz metodę, która korzysta z domyślnego parametru.

## <a name="rule-description"></a>Opis reguły
 Metody, z wykorzystaniem parametrów domyślnych są dozwolone w ramach Common Language Specification (CLS); jednak CLS umożliwia kompilatory ignorują wartości, które są przypisane do tych parametrów. Kod, który jest przeznaczony dla kompilatory, które będzie ignorować domyślne wartości parametrów należy jawnie określić argumenty dla każdego parametru domyślnego. Aby zapewnić odpowiednie zachowanie w językach programowania, metody, z wykorzystaniem parametrów domyślnych należy zastąpić przeciążeniami metod, które dostarczają parametry domyślne.

 Kompilator ignoruje wartości domyślne parametrów dla rozszerzenia zarządzane, dla języka C++, gdy uzyskuje dostęp do kodu zarządzanego. Kompilator języka Visual Basic obsługuje metody, które mają domyślne parametry, które używają [opcjonalnie](http://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) — słowo kluczowe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastąpić metodę, która korzysta z domyślnych parametrów, które dostarczają parametry domyślne przeciążeniami metod.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia metodę, która korzysta z domyślnych parametrów i przeciążone metody, które zapewniają podobne funkcje.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1025: Zastąp powtarzające się argumenty tablicą params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Zobacz też
 [Niezależność od języka i składniki niezależne od języka](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
