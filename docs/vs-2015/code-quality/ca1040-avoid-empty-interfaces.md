---
title: 'CA1040: Unikaj pustych interfejsów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ef6dc666cbc3c26d58358c9b59264f93a7bf184
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548255"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: Unikaj pustych interfejsów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Interfejs nie deklaruje żadnych elementów członkowskich ani nie implementuje dwóch lub więcej interfejsów.

## <a name="rule-description"></a>Opis reguły
 Interfejsy definiują elementy członkowskie, które zapewniają zachowanie lub użycie kontraktu. Funkcjonalność opisana przez interfejs może zostać przyjęta przez dowolny typ, niezależnie od tego, gdzie ten typ się pojawia w hierarchii dziedziczenia. Typ implementuje interfejs, dostarczając implementacje dla jego elementów członkowskich. Pusty interfejs nie definiuje żadnych elementów członkowskich. W związku z tym nie definiuje kontraktu, który może być zaimplementowany.

 Jeśli projekt zawiera puste interfejsy, które powinny być zaimplementowane, prawdopodobnie używasz interfejsu jako znacznika lub sposobu identyfikacji grupy typów. Jeśli ta identyfikacja będzie miała miejsce w czasie wykonywania, prawidłowym sposobem osiągnięcia tego celu jest użycie atrybutu niestandardowego. Użyj obecności lub nieobecności atrybutu lub właściwości atrybutu, aby zidentyfikować typy docelowe. Jeśli identyfikacja musi wystąpić w czasie kompilacji, można użyć pustego interfejsu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń interfejs lub Dodaj do niego członków. Jeśli pusty interfejs jest używany do etykietowania zestawu typów, Zastąp interfejs atrybutem niestandardowym.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli interfejs jest używany do identyfikowania zestawu typów w czasie kompilacji, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje pusty interfejs.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
