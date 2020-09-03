---
title: Właściwości relacji domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95372b2bc7537e017a4eeca9b414ef054d82046d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671541"
---
# <a name="properties-of-domain-relationships"></a>Właściwości relacji domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Właściwości w poniższej tabeli są skojarzone z relacją domeny. Aby uzyskać informacje na temat relacji domeny, zobacz [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślne|
|--------------|-----------------|-------------|
|Modyfikator dostępu|Poziom dostępu do relacji domeny ( `public` lub `internal` ).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z relacji domeny.|\<none>|
|Generuje podwójny pochodny|Jeśli `True` jest generowana Klasa podstawowa i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma Konstruktor niestandardowy|Jeśli `True` , wskazuje, że w kodzie źródłowym znajduje się Konstruktor niestandardowy. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z relacji domeny ( `none` `abstract` lub `sealed` ).|\<none>|
|Zezwala na duplikaty|Jeśli `True` zduplikowane linki relacji domeny mogą być tworzone między tymi samymi dwoma elementami.|`False`|
|Relacje podstawowe|Jeśli relacja domeny jest pochodna, podstawową relacją relacji domeny.|\<none>|
|Jest osadzaniem|Jeśli `True` Relacja domeny jest relacją osadzania. Jeśli `False` relacja jest relacją odwołania.|\<both>|
|Nazwa|Nazwa relacji domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw, która jest powiązana z relacją domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Nieformalne uwagi, które są skojarzone z relacją domeny.|\<none>|
|Opis|Opis używany do dokumentowania kodu i jest używany w interfejsie użytkownika wygenerowanego projektanta.|\<none>|
|Nazwa wyświetlana|Nazwa wyświetlana w wygenerowanym projektancie dla relacji domeny.|\<none>|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla relacji domeny.|\<none>|

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
