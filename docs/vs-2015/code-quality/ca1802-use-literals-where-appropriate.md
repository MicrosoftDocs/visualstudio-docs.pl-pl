---
title: 'CA1802: Używaj literałów wszędzie, gdzie jest to odpowiednie | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756108"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Używaj literałów w odpowiednich miejscach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Pole jest zadeklarowane jako `static` i `readonly` (`Shared` i `ReadOnly` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) i jest inicjowany z wartością, która jest obliczana w czasie kompilacji.

## <a name="rule-description"></a>Opis reguły
 Wartość `static``readonly` pola jest obliczana w czasie wykonywania, gdy wywoływana jest konstruktor statyczny dla elementu typ deklarujący. Jeśli `static``readonly` pola jest inicjowane, gdy jest on zadeklarowany jako statyczny Konstruktor nie został zadeklarowany jawnie, kompilator generuje Konstruktor statyczny do inicjowania pola.

 Wartość `const` pola jest obliczane w czasie kompilacji i przechowywany w metadanych, co zwiększa wydajność środowiska uruchomieniowego w porównaniu z `static``readonly` pola.

 Ponieważ wartość przypisana do pola docelowego jest obliczana w czasie kompilacji, zmień deklarację do `const` tak, aby wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastąpić `static` i `readonly` Modyfikatory z `const` modyfikator.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpiecznie Pomijaj ostrzeżeń dla tej reguły lub wyłączyć regułę, jeśli wydajność nie jest istotna.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typem `UseReadOnly`, który narusza regułę i typu `UseConstant`, odpowiadającej reguły.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
