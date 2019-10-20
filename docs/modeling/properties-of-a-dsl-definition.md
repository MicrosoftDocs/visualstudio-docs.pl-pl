---
title: Właściwości definicji DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c7ff2be87a91e6c01ec275bcff1d77aa6481df1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658274"
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
Właściwości DslDefinition definiują *specyficzne dla domeny* właściwości definicji języka, takie jak numer wersji. Właściwości DslDefinition są wyświetlane w oknie **Właściwości** po kliknięciu otwartego obszaru diagramu w *Projektant języka specyficznego dla domeny*.

 Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition ma właściwości w poniższej tabeli:

|Właściwość|Opis|Domyślny|
|-|-|-|
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny, czy wewnętrzny.|public|
|Atrybuty niestandardowe|Niestandardowe atrybuty zdefiniowane dla klasy domeny.<br /><br /> **Uwaga** Użyj przycisku Przeglądaj, aby dodać atrybut.|\<none >|
|Nazwa firmy|Nazwa bieżącej nazwy firmy w rejestrze systemowym.|Nazwa bieżącej firmy|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw stowarzyszona z tą klasą domeny.|Bieżąca przestrzeń nazw|
|Identyfikator GUID pakietu|Identyfikator GUID dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<none >|
|Przestrzeń nazw pakietu|Przestrzeń nazw dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<none >|
|Nazwa produktu|Nazwa produktu, która zostanie zarejestrowana dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<none >|
|Uwagi|Uwagi skojarzone z tą klasą domeny.|\<none >|
|Opis|Opis tej klasy domeny.|\<none >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none >|
|Słowo kluczowe pomocy|Słowo kluczowe pomocy skojarzone z tą klasą domeny.|\<none >|
|Kompilacja|Numer kompilacji przyrostowej dla tej definicji języka specyficznego dla domeny.|0|
|Wersja główna|Przyrostowy numer kompilacji głównej dla tej definicji języka specyficznego dla domeny.|1|
|Wersja pomocnicza|Przyrostowy numer kompilacji dla tej definicji języka specyficznego dla domeny.|0|
|skorygowan|Numer kompilacji poprawki przyrostowej dla tej definicji języka specyficznego dla domeny.|0|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)