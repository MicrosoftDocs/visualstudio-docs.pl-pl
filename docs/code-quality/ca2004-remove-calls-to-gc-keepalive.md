---
title: 'CA2004: Usuń wywołania funkcji GC.KeepAlive'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a716da8eb0fb1b741c302ed32408e63a4933567b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921138"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Usuń wywołania funkcji GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Klasy używają `SafeHandle` , ale nadal zawierają wywołania `GC.KeepAlive`do.

## <a name="rule-description"></a>Opis reguły
Jeśli konwertujesz na `SafeHandle` użycie, Usuń wszystkie wywołania do `GC.KeepAlive` (Object). W takim przypadku klasy nie powinny mieć wywołania `GC.KeepAlive`, przy założeniu, że nie mają finalizatora, ale `SafeHandle` polegają na zakończeniu dojścia systemu operacyjnego.  Chociaż koszt opuszczenia w wywołaniu `GC.KeepAlive` może być nieistotny jako mierzony przez wydajność, postrzeganie, że `GC.KeepAlive` wywołanie jest niezbędne lub wystarczające, aby rozwiązać problem z okresem istnienia, który może już nie istnieć, sprawia, że kod jest trudniejszy do prowadzą.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Usuń wywołania do `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
To ostrzeżenie można pominąć tylko wtedy, gdy nie jest technicznie poprawna `SafeHandle` do konwersji do użycia w klasie.