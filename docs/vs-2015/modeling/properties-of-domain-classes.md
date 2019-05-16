---
title: Właściwości klas domeny | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c668317fba69100701fac95bfa333ed7b3446488
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701967"
---
# <a name="properties-of-domain-classes"></a>Właściwości klas domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klasy domeny mają właściwości podane w poniższej tabeli. Aby uzyskać informacji na temat klas domeny, zobacz [objaśnienie modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Modyfikator dostępu|Poziom dostępu dla klasy domeny (`public` lub `internal`).|`public`|  
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowana z tą klasą domeny.|\<Brak >|  
|Generuje Double pochodne|Jeśli `True`, zostaną wygenerowane klasy podstawowej i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Ma konstruktora niestandardowego|Jeśli `True`, konstruktora niestandardowego, które będą dostępne w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowany na podstawie klasy domeny (`none`, `abstract` lub `sealed`).|`none`|  
|Klasa bazowa|Jeśli pochodzi ta klasa domeny, nazwa klasy bazowej.|\<Brak >|  
|Nazwa|Nazwa tej klasy domeny.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw tą klasą domeny.|Bieżąca przestrzeń nazw|  
|Uwagi|Uwagi informacyjne, które są skojarzone z tą klasą domeny.|\<Brak >|  
|Opis|Opis, który jest używany do dokumentów interfejsu użytkownika w wygenerowanym projektancie.|\<Brak >|  
|Nazwa wyświetlana|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej klasy domeny.|\<Brak >|  
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tej klasy domeny.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
