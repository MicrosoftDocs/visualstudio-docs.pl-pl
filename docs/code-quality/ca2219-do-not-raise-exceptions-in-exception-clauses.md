---
title: 'CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4403ab65be60000bc758cf1a127e6b589c764702
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857711"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału, istotne|

## <a name="cause"></a>Przyczyna
 Wyjątek jest generowany z `finally`, filtr lub klauzuli fault.

## <a name="rule-description"></a>Opis reguły
 Gdy wyjątek jest zgłaszany w klauzuli wyjątek, zwiększa znacznie utrudnia debugowanie.

 Gdy wyjątek jest zgłaszany w `finally` lub klauzuli fault ukrywa aktywny wyjątek, jeśli jest obecny. Dzięki temu można trudno wykrycie i zdebugowanie pierwotnego błędu.

 Gdy wyjątek jest zgłaszany w klauzuli filtru, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek i powoduje, że filtr na wartość false. Nie istnieje żaden sposób odróżnić filtr oceny false, a wyjątek jest wyrzuca wyjątków z filtru. Utrudnia to wykrywanie i debugowanie błędów w logice filtru.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem to naruszenie tej zasady, nie jawnie zgłaszała wyjątku z `finally`, filtr lub klauzuli fault.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Brak żadnych scenariuszy, w których wyjątek zgłaszany w klauzuli wyjątek zapewnia korzyści wykonywanie kodu.

## <a name="related-rules"></a>Powiązane reguły
 [CA1065: Nie zgłaszaj wyjątków w nieoczekiwanych lokalizacjach](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Zobacz także
 [Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)