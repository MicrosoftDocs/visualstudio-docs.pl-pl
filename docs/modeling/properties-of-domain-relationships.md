---
title: Właściwości relacji domeny
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d08f453c3c52f8520dacc26f9b636fd8c8bcafde
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747470"
---
# <a name="properties-of-domain-relationships"></a>Właściwości relacji domeny
Właściwości w poniższej tabeli są skojarzone z relacją domeny. Aby uzyskać informacje na temat relacji domeny, zobacz [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślny|
|-|-|-|
|Modyfikator dostępu|Poziom dostępu do relacji domeny (`public` lub `internal`).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z relacji domeny.|\<none >|
|Generuje podwójny pochodny|Jeśli `True`, generowany jest zarówno Klasa bazowa, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma Konstruktor niestandardowy|Jeśli `True`, wskazuje, że w kodzie źródłowym znajduje się Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z relacji domeny (`none`, `abstract` lub `sealed`).|\<none >|
|Zezwala na duplikaty|Jeśli `True`, zduplikowane linki relacji domeny mogą być tworzone między tymi samymi dwoma elementami.|`False`|
|Relacje podstawowe|Jeśli relacja domeny jest pochodna, podstawową relacją relacji domeny.|\<none >|
|Jest osadzaniem|W przypadku `True` Relacja domeny jest relacją osadzania. W przypadku `False` relacja jest relacją odwołania.|\<both >|
|Nazwa|Nazwa relacji domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z relacją domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Nieformalne uwagi, które są skojarzone z relacją domeny.|\<none >|
|Opis|Opis używany do dokumentowania kodu i jest używany w interfejsie użytkownika wygenerowanego projektanta.|\<none >|
|Nazwa wyświetlana|Nazwa wyświetlana w wygenerowanym projektancie dla relacji domeny.|\<none >|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla relacji domeny.|\<none >|

## <a name="see-also"></a>Zobacz także

- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)