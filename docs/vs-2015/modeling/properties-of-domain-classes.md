---
title: Właściwości klas domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652006"
---
# <a name="properties-of-domain-classes"></a>Właściwości klas domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klasy domeny mają właściwości w poniższej tabeli. Aby uzyskać informacje o klasach domen, zobacz [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślny|
|--------------|-----------------|-------------|
|Modyfikator dostępu|Poziom dostępu do klasy domeny (`public` lub `internal`).|`public`|
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tej klasy domeny.|\<none >|
|Generuje podwójny pochodny|Jeśli `True`, zostaną wygenerowane zarówno klasę bazową, jak i Klasa częściowa (do obsługi dostosowywania za pomocą przesłonięć). Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ma Konstruktor niestandardowy|Jeśli `True`, Konstruktor niestandardowy zostanie udostępniony w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [przesłanianie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modyfikator dziedziczenia|Opisuje rodzaj dziedziczenia klasy kodu źródłowego, która jest generowana z klasy domeny (`none`, `abstract` lub `sealed`).|`none`|
|Klasa bazowa|Jeśli ta klasa domeny jest pochodna, nazwa klasy podstawowej.|\<none >|
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|
|Przestrzeń nazw|Przestrzeń nazw tej klasy domeny.|Bieżąca przestrzeń nazw|
|Uwagi|Nieformalne uwagi, które są skojarzone z tą klasą domeny.|\<none >|
|Opis|Opis używany do dokumentowania interfejsu użytkownika wygenerowanego projektanta.|\<none >|
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<none >|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tej klasy domeny.|\<none >|

## <a name="see-also"></a>Zobacz też
 [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
