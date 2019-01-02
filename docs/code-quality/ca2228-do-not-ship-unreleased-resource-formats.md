---
title: 'CA2228: Dostarczaj niepublikowanych formatów zasobów'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e6f2216d26315491e7e187acdd31530c0bcf013
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829079"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: Dostarczaj niepublikowanych formatów zasobów

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
