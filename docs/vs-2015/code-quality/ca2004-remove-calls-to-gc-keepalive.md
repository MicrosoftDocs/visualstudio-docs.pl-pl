---
title: 'CA2004: Usuń wywołania do GC. Utrzymywanie aktywności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 53fa5f61cb7c503502956831452bc3eca1a9fece
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521202"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Usuń wywołania funkcji GC.KeepAlive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategoria|Microsoft. niezawodność|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Klasy używają `SafeHandle` , ale nadal zawierają wywołania do `GC.KeepAlive` .

## <a name="rule-description"></a>Opis reguły
 Jeśli konwertujesz na `SafeHandle` użycie, Usuń wszystkie wywołania do `GC.KeepAlive` (Object). W takim przypadku klasy nie powinny mieć wywołania `GC.KeepAlive` , przy założeniu, że nie mają finalizatora, ale polegają na `SafeHandle` zakończeniu dojścia systemu operacyjnego.  Chociaż koszt opuszczenia w wywołaniu `GC.KeepAlive` może być nieistotny jako mierzony przez wydajność, postrzeganie, że wywołanie `GC.KeepAlive` jest niezbędne lub wystarczające, aby rozwiązać problem z okresem istnienia, który może już nie istnieć, sprawia, że kod jest trudniejszy do utrzymania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Usuń wywołania do `GC.KeepAlive` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 To ostrzeżenie można pominąć tylko wtedy, gdy nie jest technicznie poprawna do konwersji do `SafeHandle` użycia w klasie.
