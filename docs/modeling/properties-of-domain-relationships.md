---
title: Właściwości relacji domeny
description: Dowiedz się więcej o właściwościach skojarzonych z relatorem domeny, takich jak Modyfikator dostępu, Atrybuty niestandardowe i Generuje podwójne pochodne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc92bbc32a454208f3d455734b7697a2e69037b4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390662"
---
# <a name="properties-of-domain-relationships"></a>Właściwości relacji domeny
Właściwości w poniższej tabeli są skojarzone z relacją domeny. Aby uzyskać informacje o relacjach domeny, zobacz [Opis modeli, klas i relacji.](../modeling/understanding-models-classes-and-relationships.md) Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i rozszerzanie [Domain-Specific języku .](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Właściwość|Opis|Domyślne|
|-|-|-|
|Modyfikator dostępu|Poziom dostępu relacji domeny ( `public` lub `internal` ).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana na podstawie relacji domeny.|\<none>|
|Generuje podwójne pochodne|Jeśli jest generowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi `True` dostosowywania za pomocą zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma konstruktor niestandardowy|Jeśli , wskazuje, że w kodzie źródłowym `True` znajduje się konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego generowanego na podstawie relacji domeny ( `none` lub `abstract` `sealed` ).|\<none>|
|Zezwala na duplikaty|W `True` przypadku wartości można utworzyć zduplikowane linki relacji domeny między tymi samymi dwoma elementami.|`False`|
|Relacje podstawowe|Jeśli relacja domeny jest pochodna, relacja podstawowa relacji domeny.|\<none>|
|Jest osadzanie|Jeśli `True` , relacja domeny jest relacją osadzania. Jeśli `False` , relacja jest relacją referencyjną.|\<both>|
|Nazwa|Nazwa relacji domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw powiązana z relacją domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Notatki nieformalne skojarzone z relacją domeny.|\<none>|
|Opis|Opis używany do dokumentować kod i używany w interfejsie użytkownika wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa wyświetlana w wygenerowanym projektancie relacji domeny.|\<none>|
|Słowo kluczowe Pomocy|Opcjonalne słowo kluczowe używane do indeksowania pomocy F1 dla relacji domeny.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))