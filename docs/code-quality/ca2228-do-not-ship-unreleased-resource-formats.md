---
title: 'CA2228: Nie publikuj zasobów w formatach z wersji wstępnych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3dc7763b8c9dd303ec154dae02db3fb5aa677782
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971169"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nie publikuj zasobów w formatach z wersji wstępnych

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Plik zasobów został skompilowany przy użyciu wersji programu .NET Framework, która nie jest obecnie obsługiwana.

## <a name="rule-description"></a>Opis reguły
 Pliki zasobów, które zostały utworzone za pomocą wersji wstępnej wersji programu .NET Framework nie może być użyteczne z obsługiwanymi wersjami programu .NET Framework.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy utworzyć ten zasób, używając obsługiwanej wersji programu .NET Framework.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.
