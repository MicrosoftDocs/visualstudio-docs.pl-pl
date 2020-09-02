---
title: 'CA1030: Użyj zdarzeń, jeśli są odpowiednie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544524"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: Używaj zdarzeń, o ile to możliwe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Publiczna, chroniona lub prywatna nazwa metody rozpoczyna się od jednego z następujących:

- Dodatki

- RemoveOn

- Zapala

- Nosić

## <a name="rule-description"></a>Opis reguły
 Ta reguła wykrywa metody o nazwach, które normalnie mogą być używane dla zdarzeń. Zdarzenia obserwują Wzorzec projektowy obserwatora lub publikowania/subskrybowania. są one używane, gdy zmiana stanu w jednym obiekcie musi być przekazywana do innych obiektów. Jeśli metoda zostanie wywołana w odpowiedzi na jasno zdefiniowaną zmianę stanu, metoda powinna być wywoływana przez procedurę obsługi zdarzeń. Obiekty, które wywołują tę metodę, powinny wywoływać zdarzenia, a nie bezpośrednio metodę.

 Niektóre typowe przykłady zdarzeń można znaleźć w aplikacjach interfejsu użytkownika, w których akcja użytkownika, taka jak kliknięcie przycisku powoduje, że segment kodu ma zostać wykonany. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Model zdarzenia nie jest ograniczony do interfejsów użytkownika; należy go używać wszędzie tam, gdzie trzeba przekazywać zmiany stanu do jednego lub większej liczby obiektów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Jeśli metoda jest wywoływana, gdy zmienia się stan obiektu, należy rozważyć zmianę projektu w celu użycia [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelu zdarzeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli metoda nie działa z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modelem zdarzeń.
