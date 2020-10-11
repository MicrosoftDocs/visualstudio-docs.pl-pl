---
title: Operatory logiczne w wyrażeniach wyszukiwania (Podgląd pomocy)
description: Dowiedz się, jak używać operatorów logicznych i operatorów wyszukiwania zaawansowanego do uściślenia wyrażeń wyszukiwania w Podgląd Pomocy firmy Microsoft.
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bfa869bed2bc4462c050ac77e08665958f60598
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91878933"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operatory logiczne i zaawansowane w wyrażeniach wyszukiwania

Możesz użyć operatorów logicznych i operatorów wyszukiwania zaawansowanego, aby uściślić Wyszukiwanie zawartości pomocy w **podglądzie pomocy**.

## <a name="logical-operators"></a>Operatory logiczne

Operatory logiczne określają, jak wiele terminów wyszukiwania ma być połączonych w zapytaniu wyszukiwania. W poniższej tabeli przedstawiono operatory logiczne oraz, lub, nie i blisko.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|
|-------------------|---------|-------------|------------|
|Oba warunki w tym samym artykule|AND|DIB i paleta|Tematy zawierające obie wersje "DIB" i "paleta".|
|Dowolny termin w artykule|LUB|Raster lub Vector|Tematy zawierające "rastrowe" lub "Vector".|
|Pierwszy termin bez drugiego terminu w tym samym artykule|NOT|"system operacyjny" nie jest DOS|Tematy zawierające "system operacyjny", ale nie "DOS".|
|Oba terminy, blisko siebie w artykule|POBLIŻU|Użytkownik blisko jądra|Tematy zawierające "użytkownika" w bliskim sąsiedztwie "jądra".|

> [!IMPORTANT]
> Należy wprowadzić operatory logiczne we wszystkich wielkich literach, aby aparat wyszukiwania mógł je rozpoznać.

## <a name="advanced-operators"></a>Operatory zaawansowane

Zaawansowane Operatory wyszukiwania uściśliją Wyszukiwanie zawartości, określając miejsce w artykule, w którym ma zostać wyszukany termin wyszukiwania. W poniższej tabeli opisano cztery dostępne Operatory wyszukiwania zaawansowanego.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|
|-------------------|---------|-------------|------------|
|Termin w tytule artykułu|`title:`|`title:binaryreader`|Tematy zawierające "BinaryReader" w ich tytułach.|
|Termin w przykładowym kodzie|`code:`|`code:readdouble`|Tematy zawierające "readDouble" w przykładowym kodzie.|
|Termin z przykładu określonego języka programowania|`code:vb:`|`code:vb:string`|Tematy zawierające ciąg "String" w przykładowym kodzie Visual Basic.|
|Artykuł, który jest skojarzony z określonym indeksem słowa kluczowego|`keyword:`|`keyword:readbyte`|Tematy, które są skojarzone ze słowem kluczowym "ReadByte".|

> [!IMPORTANT]
> Należy wprowadzić zaawansowane Operatory wyszukiwania z końcowym dwukropkiem i bez odstępu przed dwukropkiem, aby aparat wyszukiwania mógł je rozpoznać.

### <a name="programming-languages-for-code-examples"></a>Języki programowania dla przykładów kodu

Możesz użyć operatora, `code:` Aby znaleźć zawartość dla dowolnego z kilku języków programowania. Aby zwrócić przykłady dla określonego języka programowania, użyj jednej z następujących wartości języka programowania:

|Język programowania|Składnia operatora wyszukiwania|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:`Operator odnajduje tylko zawartość, która jest oznaczona za pomocą etykiety języka programowania, w przeciwieństwie do zawartości, która jest ogólnie oznaczona jako kod.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: wyszukiwanie tematów](../help-viewer/find-topics.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)
