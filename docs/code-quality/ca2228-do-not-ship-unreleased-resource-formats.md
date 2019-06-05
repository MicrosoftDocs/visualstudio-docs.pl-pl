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
ms.openlocfilehash: 5f8a672056c8663c2e27ec730e542083aee9738f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714981"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Nie publikuj zasobów w formatach z wersji wstępnych

|||
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Plik zasobów został skompilowany przy użyciu wersji platformy .NET, który nie jest obecnie obsługiwane.

## <a name="rule-description"></a>Opis reguły

Pliki zasobów, które zostały utworzone przy użyciu wersji platformy .NET w wersji wstępnej może nie być użyteczne z obsługiwanymi wersjami programu .NET.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy utworzyć ten zasób, używając obsługiwanej wersji programu .NET.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.
