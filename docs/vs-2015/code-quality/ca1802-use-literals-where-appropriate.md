---
title: 'CA1802: Użyj literałów, jeśli są odpowiednie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671513"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów wszędzie, gdzie jest to odpowiednie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Pole jest zadeklarowane `static` i `readonly` (`Shared` i `ReadOnly` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) i jest inicjowane z wartością obliczanej w czasie kompilacji.

## <a name="rule-description"></a>Opis reguły
 Wartość pola `static``readonly` jest obliczana w czasie wykonywania, gdy jest wywoływany statyczny Konstruktor dla typu deklarującego. Jeśli pole `static``readonly` jest inicjowane, gdy jest zadeklarowany, a Konstruktor statyczny nie jest zadeklarowany jawnie, kompilator emituje konstruktora statycznego w celu zainicjowania pola.

 Wartość pola `const` jest obliczana w czasie kompilacji i przechowywana w metadanych, co zwiększa wydajność środowiska uruchomieniowego, gdy jest porównywana z polem `static``readonly`.

 Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na `const` pole, aby wartość była obliczana w czasie kompilacji, a nie w środowisku uruchomieniowym.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp Modyfikatory `static` i `readonly` modyfikatorem `const`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły lub wyłączania reguły, jeśli wydajność nie jest istotna.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, `UseReadOnly`, który narusza regułę i typ `UseConstant`, który spełnia regułę.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
