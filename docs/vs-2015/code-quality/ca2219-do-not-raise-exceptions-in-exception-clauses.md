---
title: 'CA2219: nie zgłaszaj wyjątków w klauzulach wyjątków | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538531"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania, przerywania|

## <a name="cause"></a>Przyczyna
 Wyjątek jest generowany z `finally` klauzuli, Filter lub Fault.

## <a name="rule-description"></a>Opis reguły
 Gdy wyjątek jest zgłaszany w klauzuli wyjątku, znacznie zwiększa trudność debugowania.

 Gdy wyjątek jest zgłaszany w `finally` klauzuli lub Fault, nowy wyjątek ukrywa aktywny wyjątek, jeśli jest obecny. Powoduje to, że oryginalny błąd trudno wykryć i debugować.

 Gdy wyjątek jest zgłaszany w klauzuli filtru, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek i powoduje, że filtr jest obliczany na wartość false. Nie ma możliwości poinformowania o różnicy między filtrem a wartością false a błędem zgłaszanym przez filtr. Dzięki temu trudno wykrywać i debugować błędy w logice filtru.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, nie należy jawnie zgłosić wyjątku z `finally` klauzuli, Filter lub Fault.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia dla tej reguły. Nie ma scenariuszy, w których wyjątek zgłoszony w klauzuli wyjątku stanowi korzyść dla wykonywanego kodu.

## <a name="related-rules"></a>Powiązane reguły
 [CA1065: Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia projektu](../code-quality/design-warnings.md)
