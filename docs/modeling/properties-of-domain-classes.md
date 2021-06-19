---
title: Właściwości klas domeny
description: Dowiedz się więcej o różnych właściwościach klas domen, takich jak modyfikator dostępu, atrybuty niestandardowe i generowanie podwójnego pochodnego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eaaae0028d574a521319ae045cdb4f7f1bdafaa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390011"
---
# <a name="properties-of-domain-classes"></a>Właściwości klas domeny
Klasy domen mają właściwości w poniższej tabeli. Aby uzyskać informacje o klasach domeny, zobacz [Understanding Models, Classes and Relationships (Opis modeli, klas i relacji).](../modeling/understanding-models-classes-and-relationships.md) Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i rozszerzanie [Domain-Specific języku .](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Właściwość|Opis|Domyślne|
|-|-|-|
|Modyfikator dostępu|Poziom dostępu klasy domeny ( `public` lub `internal` ).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tej klasy domeny.|\<none>|
|Generuje podwójne pochodne|Jeśli zostanie wygenerowana zarówno klasa bazowa, jak i klasa częściowa (w celu obsługi dostosowywania za pomocą `True` zastąpień). Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma konstruktor niestandardowy|Jeśli , w kodzie źródłowym `True` zostanie podany konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [Zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego generowanego na podstawie klasy domeny ( `none` lub `abstract` `sealed` ).|`none`|
|Klasa bazowa|Jeśli ta klasa domeny jest pochodna, nazwa klasy bazowej.|\<none>|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw tej klasy domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Uwagi nieformalne skojarzone z tą klasą domeny.|\<none>|
|Opis|Opis używany do dokumentować interfejs użytkownika wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none>|
|Słowo kluczowe Pomocy|Opcjonalne słowo kluczowe używane do indeksowania pomocy F1 dla tej klasy domeny.|\<none>|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))