---
title: Właściwości definicji DSL
description: Dowiedz się, że właściwości DslDefinition definiują specyficzne dla domeny właściwości definicji języka, takie jak numer wersji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef8f49e46c554efca89862c787fbfbe97c48c8f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959119"
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
Właściwości DslDefinition definiują *specyficzne dla domeny* właściwości definicji języka, takie jak numer wersji. Właściwości DslDefinition są wyświetlane w oknie **Właściwości** po kliknięciu otwartego obszaru diagramu w *Projektant języka specyficznego dla domeny*.

 Aby uzyskać więcej informacji, zobacz [How to define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat sposobu korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition ma właściwości w poniższej tabeli:

|Właściwość|Opis|Domyślne|
|-|-|-|
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny, czy wewnętrzny.|public|
|Atrybuty niestandardowe|Niestandardowe atrybuty zdefiniowane dla klasy domeny.<br /><br /> **Uwaga** Użyj przycisku Przeglądaj, aby dodać atrybut.|\<none>|
|Nazwa firmy|Nazwa bieżącej nazwy firmy w rejestrze systemowym.|Nazwa bieżącej firmy|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw stowarzyszona z tą klasą domeny.|Bieżąca przestrzeń nazw|
|Identyfikator GUID pakietu|Identyfikator GUID dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<none>|
|Przestrzeń nazw pakietu|Przestrzeń nazw dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<none>|
|Nazwa produktu|Nazwa produktu, która zostanie zarejestrowana dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<none>|
|Uwagi|Uwagi skojarzone z tą klasą domeny.|\<none>|
|Opis|Opis tej klasy domeny.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe pomocy skojarzone z tą klasą domeny.|\<none>|
|Kompilacja|Numer kompilacji przyrostowej dla tej definicji języka specyficznego dla domeny.|0|
|Wersja główna|Przyrostowy numer kompilacji głównej dla tej definicji języka specyficznego dla domeny.|1|
|Wersja pośrednia|Przyrostowy numer kompilacji dla tej definicji języka specyficznego dla domeny.|0|
|Przegląd|Numer kompilacji poprawki przyrostowej dla tej definicji języka specyficznego dla domeny.|0|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))