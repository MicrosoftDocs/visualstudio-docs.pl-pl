---
title: 'CA1025: Zastąp powtarzające się argumenty tablicą params | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 22e0597d84e6261de95210a8234c2f90d6b83036
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987419"
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025: Zastąp powtarzające się argumenty tablicą params
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|
|CheckId|CA1025|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma więcej niż trzy parametry, a jego trzy ostatnie parametry są tego samego typu.

## <a name="rule-description"></a>Opis reguły
 Użyj tablicy parametrów zamiast powtarzających się argumentów, jeśli dokładna liczba argumentów jest nieznany i argumenty zmiennych są tego samego typu lub mogą być przekazywane jako tego samego typu. Na przykład <xref:System.Console.WriteLine%2A> metoda zapewnia ogólnego przeznaczenia przeciążenia, które używa tablicy parametrów, aby zaakceptować dowolną liczbę <xref:System.Object> argumentów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zastąp powtarzające się argumenty tablicą parametrów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest zawsze bezpieczne ostrzeżenia od tej reguły; Jednak ten projekt może spowodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Design.RepeatArgs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RepeatArgs/cs/FxCop.Design.RepeatArgs.cs#1)]
