---
title: 'CA2228: Nie publikuj zasobów w formatach z wersji wstępnych'
ms.date: 11/04/2016
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
ms.openlocfilehash: b3c6298c2186b6a73b4a7ef441b5f4c42c90ff6a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231062"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nie publikuj zasobów w formatach z wersji wstępnych

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Plik zasobów został skompilowany przy użyciu wersji platformy .NET, która nie jest obecnie obsługiwana.

## <a name="rule-description"></a>Opis reguły

Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych programu .NET, mogą nie być używane przez obsługiwane wersje programu .NET.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, skompiluj zasób przy użyciu obsługiwanej wersji platformy .NET.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.
