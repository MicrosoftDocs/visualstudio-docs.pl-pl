---
title: 'CA1025: Zastąp powtarzalne argumenty z tablicą parametrów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 21d13611a3c4dd11eb691c746f8746347fb9a83b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661970"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Zastąp powtarzające się argumenty tabelą parametrów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma więcej niż trzy parametry, a jego ostatnie trzy parametry są tego samego typu.

## <a name="rule-description"></a>Opis reguły
 Użyj tablicy parametrów zamiast powtarzanych argumentów, gdy dokładna liczba argumentów jest nieznana, a argumenty zmiennych są tego samego typu lub mogą być przekazane jako ten sam typ. Na przykład Metoda <xref:System.Console.WriteLine%2A> zapewnia Przeciążenie ogólnego przeznaczenia, które używa tablicy parametrów do akceptowania dowolnej liczby argumentów <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp powtarzalne argumenty tablicą parametrów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Zawsze można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak ten projekt może powodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
