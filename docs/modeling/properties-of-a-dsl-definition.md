---
title: Właściwości definicji DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e63a5ab794261a395fb091016f177ffca9d35692
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964303"
---
# <a name="properties-of-a-dsl-definition"></a>Właściwości definicji DSL
Zdefiniuj właściwości DslDefinition *języka specyficznego dla domeny* definicji właściwości, takie jak numerowanie wersji. Właściwości DslDefinition są wyświetlane w **właściwości** okno po kliknij pusty obszar na diagramie w *projektanta języka specyficznego dla domeny*.

 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition ma właściwości w poniższej tabeli:

|Właściwość|Opis|Domyślny|
|-|-|-|
|Modyfikator dostępu|Określa, czy modyfikator dostępu dla klasy domeny jest publiczny lub wewnętrzny.|public|
|Atrybuty niestandardowe|Niestandardowe zdefiniowane atrybuty dla klasy domeny.<br /><br /> **Uwaga** używaj przycisku Przeglądaj, aby dodać atrybut.|\<Brak >|
|Nazwa firmy|Nazwa bieżącej nazwy firmy w rejestrze systemowym.|Bieżąca nazwa firmy|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw stowarzyszona z tą klasą domeny.|Bieżąca przestrzeń nazw|
|Identyfikator Guid pakietu|Identyfikator guid pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<Brak >|
|Namespace pakietu|Przestrzeń nazw dla pakietu programu Visual Studio wygenerowanego dla tego języka DSL.|\<Brak >|
|Nazwa produktu|Nazwa produktu, który ma zostać zarejestrowany dla pakietu Visual Studio wygenerowanego dla tego języka DSL.|\<Brak >|
|Uwagi|Informacje o skojarzone z tą klasą domeny.|\<Brak >|
|Opis|Opis dla tej klasy domeny.|\<Brak >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<Brak >|
|Słowo kluczowe pomocy|Słowo kluczowe Pomocy skojarzone z tą klasą domeny.|\<Brak >|
|Kompilacja|Numer kompilacji przyrostowych dla tej definicji języka specyficznego dla domeny.|0|
|Wersja główna|Numer kompilacji przyrostowej głównych dla tej definicji języka specyficznego dla domeny.|1|
|Wersja pomocnicza|Numer kompilacji przyrostowej pomocniczej dla tej definicji języka specyficznego dla domeny.|0|
|Poprawki|Przyrostowych wersji kompilacji numer dla tej definicji języka specyficznego dla domeny.|0|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)