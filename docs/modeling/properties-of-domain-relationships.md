---
title: Właściwości relacji domeny
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2693994c9ead711f3bb536d0e37f485bc00047b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998908"
---
# <a name="properties-of-domain-relationships"></a>Właściwości relacji domeny
W poniższej tabeli przedstawiono właściwości są skojarzone z relacją domeny. Aby uzyskać informacji na temat relacji domeny, zobacz [objaśnienie modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślny|
|-|-|-|
|Modyfikator dostępu|Poziom dostępu relacji domeny (`public` lub `internal`).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowany na podstawie relacji domeny.|\<Brak >|
|Generuje Double pochodne|Jeśli `True`, generowany jest zarówno klasy bazowej, jak i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma konstruktora niestandardowego|Jeśli `True`, wskazuje, że Konstruktor niestandardowy znajduje się w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie relacji domeny (`none`, `abstract` lub `sealed`).|\<Brak >|
|Umożliwia tworzenie duplikatów|Jeśli `True`, może zostać utworzony duplikatów linków relacji domeny między dwoma tymi samymi elementami.|`False`|
|Relacji podstawowych|Jeśli domena relacja jest relacją pochodną, relacja podstawowa tej relacji domeny.|\<Brak >|
|Jest osadzania|Jeśli `True`, relacji domeny relacja osadzania. Jeśli `False`, relacja jest relacją odwołania.|\<both>|
|Nazwa|Nazwa relacji domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona z relacji domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Uwagi informacyjne, które są skojarzone z relacji domeny.|\<Brak >|
|Opis|Opis, który jest używany do dokumentowania kodu i jest używany w Interfejsie użytkownika wygenerowanego projektanta.|\<Brak >|
|Nazwa wyświetlana|Nazwa która jest wyświetlana w wygenerowanym projektancie dla relacji domeny.|\<Brak >|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla relacji domeny.|\<Brak >|

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)