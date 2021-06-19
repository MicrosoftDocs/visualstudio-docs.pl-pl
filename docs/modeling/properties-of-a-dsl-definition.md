---
title: Właściwości definicji DSL
description: Dowiedz się, że właściwości DslDefinition definiują właściwości definicji języka specyficzne dla domeny, takie jak numerowanie wersji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6212dfcb9e93110a97e7143e5b1c946efebee89f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390844"
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
Właściwości DslDefinition definiują *właściwości definicji* języka specyficzne dla domeny, takie jak numerowanie wersji. Właściwości DslDefinition są wyświetlane w **oknie Właściwości** po kliknięciu otwartego obszaru diagramu w *projektant języka specyficznego dla domeny*.

 Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i [rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition ma właściwości w poniższej tabeli:

|Właściwość|Opis|Domyślne|
|-|-|-|
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny lub wewnętrzny.|public|
|Atrybuty niestandardowe|Atrybuty zdefiniowane niestandardowo dla klasy domeny.<br /><br /> **Uwaga** Użyj przycisku przeglądania, aby dodać atrybut.|\<none>|
|Nazwa firmy|Nazwa bieżącej nazwy firmy w rejestrze systemu.|Bieżąca nazwa firmy|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z tą klasą domeny.|Bieżąca przestrzeń nazw|
|Identyfikator GUID pakietu|Identyfikator GUID pakietu Visual Studio dla tego DSL.|\<none>|
|Przestrzeń nazw pakietu|Przestrzeń nazw dla pakietu Visual Studio wygenerowany dla tego DSL.|\<none>|
|Nazwa produktu|Nazwa produktu, który zostanie zarejestrowany dla pakietu Visual Studio dla tego DSL.|\<none>|
|Uwagi|Uwagi skojarzone z tą klasą domeny.|\<none>|
|Opis|Opis tej klasy domeny.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none>|
|Słowo kluczowe pomocy|Słowo kluczowe pomocy skojarzone z tą klasą domeny.|\<none>|
|Kompilacja|Przyrostowy numer kompilacji dla tej definicji języka specyficznego dla domeny.|0|
|Wersja główna|Przyrostowy główny numer kompilacji dla tej definicji języka specyficznego dla domeny.|1|
|Wersja pośrednia|Przyrostowy pomocniczy numer kompilacji dla tej definicji języka specyficznego dla domeny.|0|
|Przegląd|Numer kompilacji przyrostowej poprawki dla tej definicji języka specyficznego dla domeny.|0|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))