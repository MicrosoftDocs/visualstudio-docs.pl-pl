---
title: 'CA1821: Usuń puste finalizatory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveEmptyFinalizers
- CA1821
helpviewer_keywords:
- CA1821
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a2e704202773447e353f041df66b05cb5f648c00
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545356"
---
# <a name="ca1821-remove-empty-finalizers"></a>CA1821: Usuwaj puste finalizatory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|RemoveEmptyFinalizers|
|CheckId|CA1821|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ implementuje finalizator, który jest pusty, wywołuje tylko finalizator typu podstawowego lub wywołuje tylko metody, które są emitowane warunkowo.

## <a name="rule-description"></a>Opis reguły
 Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Moduł wyrzucania elementów bezużytecznych uruchomi finalizator przed zebraniem obiektu. Oznacza to, że do zebrania obiektu wymagane są dwie kolekcje. Pusty finalizator wiąże się z tym dodatkowym obciążeniem bez żadnej korzyści.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń pusty finalizator. Jeśli finalizator jest wymagany do debugowania, należy ująć cały finalizator w `#if DEBUG / #endif` dyrektywy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj komunikatu z tej reguły. Niepowodzenie pomijania finalizowania zmniejsza wydajność i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono pusty finalizator, który powinien zostać usunięty, finalizator, który powinien być ujęty w `#if DEBUG / #endif` dyrektywy, i finalizator, który `#if DEBUG / #endif` poprawnie używa dyrektyw.

 [!code-csharp[FxCop.Performance.RemoveEmptyFinalizers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RemoveEmptyFinalizers/cs/FxCop.Performance.RemoveEmptyFinalizers.cs#1)]
