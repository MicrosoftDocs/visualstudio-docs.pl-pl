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
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544407"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów w odpowiednich miejscach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Pole jest zadeklarowane `static` i `readonly` ( `Shared` i `ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) i jest inicjowane z wartością, która jest obliczanej w czasie kompilacji.

## <a name="rule-description"></a>Opis reguły
 Wartość `static``readonly` pola jest obliczana w czasie wykonywania, gdy wywoływana jest statyczny Konstruktor dla typu deklarującego. Jeśli `static``readonly` pole jest inicjowane, gdy jest zadeklarowany, a Konstruktor statyczny nie jest zadeklarowany jawnie, kompilator emituje konstruktora statycznego, aby zainicjować pole.

 Wartość `const` pola jest obliczana w czasie kompilacji i przechowywana w metadanych, co zwiększa wydajność środowiska uruchomieniowego w porównaniu do `static``readonly` pola.

 Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na `const` pole, aby wartość była obliczana w czasie kompilacji, a nie w środowisku uruchomieniowym.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp `static` modyfikator i modyfikator `readonly` `const` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły lub wyłączania reguły, jeśli wydajność nie jest istotna.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, `UseReadOnly` , który narusza regułę i typ, `UseConstant` który spełnia regułę.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
