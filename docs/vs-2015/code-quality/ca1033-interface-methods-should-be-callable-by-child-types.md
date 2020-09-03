---
title: 'CA1033: metody interfejsu powinny być wywoływane przez typy podrzędne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542301"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Metody interfejsu powinny móc zostać wywołane przez typy podrzędne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Niezapieczętowany typ widoczny na zewnątrz zapewnia jawną implementację metody interfejsu publicznego i nie dostarcza alternatywnej metody widocznej z zewnątrz o tej samej nazwie.

## <a name="rule-description"></a>Opis reguły
 Rozważmy typ podstawowy, który jawnie implementuje metodę interfejsu publicznego. Typ, który pochodzi od typu podstawowego, może uzyskać dostęp do dziedziczonej metody interfejsu tylko za pośrednictwem odwołania do bieżącego wystąpienia ( `this` w języku C#), który jest rzutowany do interfejsu. Jeśli typ pochodny ponownie implementuje (jawnie) dziedziczonej metody interfejsu, nie można już uzyskać dostępu do implementacji podstawowej. Wywołanie przez odwołanie do bieżącego wystąpienia wywoła implementację pochodną; powoduje to rekursję i ostateczne przepełnienie stosu.

 Ta zasada nie zgłasza naruszenia dla jawnej implementacji, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> gdy podano zewnętrznie widoczną `Close()` lub `System.IDisposable.Dispose(Boolean)` metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj nową metodę, która uwidacznia te same funkcje i jest widoczna dla typów pochodnych lub Zmień na niejawną implementację. W przypadku akceptowalnej zmiany istotne jest, aby typ był zapieczętowany.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli podano zewnętrznie widoczną metodę, która ma taką samą funkcjonalność, ale inną niż jawnie zaimplementowaną metodę, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, `ViolatingBase` , który narusza regułę i typ, `FixedBase` , który pokazuje poprawkę dla naruszenia.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Interfejsy](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
