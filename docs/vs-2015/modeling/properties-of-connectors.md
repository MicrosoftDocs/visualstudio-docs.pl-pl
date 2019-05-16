---
title: Właściwości łączników | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3673a818f9460b8b40bb3fee2dcd5fe65fd02a8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701730"
---
# <a name="properties-of-connectors"></a>Właściwości łączników
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Łączniki reprezentują relacje domeny w wygenerowanym projektancie.  
  
 Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md). Aby uzyskać więcej informacji o tym, jak korzystać z tych właściwości, zobacz [dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Łączniki mają właściwości, które są wymienione w poniższej tabeli.  
  
|Właściwość|Opis|Domyślny|  
|--------------|-----------------|-------------|  
|Kolor|Kolor tego łącznika.|Czarny|  
|Styl kreskowania|Styl kreskowania dla linii tego łącznika (stałe, kreski, kropki, DashDot, DashDotDot lub niestandardowy).|Stałe|  
|Styl końca źródła|Styl końca źródła dla tego łącznika (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub brak).|Brak|  
|Styl końca|Styl końca tego łącznika (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond lub brak).|Brak|  
|Kolor tekstu|Kolor, który jest używany dla dekoratorów tekstu, które są skojarzone z tym łącznikiem.|Czarny|  
|Grubość|Grubość linii dla tego łącznika (w calach).|0.03125|  
|Modyfikator dostępu|Poziom dostępu klasy (`public` lub `internal`).|Public|  
|Atrybuty niestandardowe|Służy do dodawania atrybutów do klasy kodu źródłowego, która jest generowany na podstawie tego łącznika.|\<Brak >|  
|Generuje Double pochodne|Jeśli `True`, zostaną wygenerowane klasy podstawowej i klasy częściowej (obsługuje dostosowywania przy użyciu zastąpień). Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ma konstruktora niestandardowego|Jeśli `True`, konstruktora niestandardowego, które będą dostępne w kodzie źródłowym. Aby uzyskać więcej informacji, zobacz [zastępowanie i rozszerzanie wygenerowanych klas](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modyfikator dziedziczenia|Opisuje typ dziedziczenia klasy kodu źródłowego, która jest generowana z łącznika usługi (`none`, `abstract` lub `sealed`).|brak|  
|Podstawowy łącznik|Klasa bazowa tego łącznika.|(Brak)|  
|Nazwa|Nazwa tego łącznika.|Bieżąca nazwa|  
|Przestrzeń nazw|Przestrzeń nazw, która jest połączona za pomocą tego łącznika.|Bieżąca przestrzeń nazw|  
|Typ etykietki narzędzia|Jak etykietka narzędzia jest zdefiniowane (stałe, zmienna lub brak). Jeśli następnie stałej wartości `Fixed Tooltip Text` właściwość jest używana jako etykietka narzędzia; Jeśli jest to zmienna, następnie etykietki narzędzia jest definiowana w kodzie niestandardowym.|\<Brak >|  
|Uwagi|Uwagi informacyjne, które są skojarzone z tym łącznikiem.|\<Brak >|  
|Styl routingu|Styl, który jest używany do routingu łącznika. A `Rectilinear` łącznika sprawia, że prostokątnej włącza zgodnie z wymaganiami; `Straight` łącznika nie ma.|Prostoliniowego|  
|Kolor uwidocznione jako właściwość<br /><br /> Styl kreskowania uwidocznione jako właściwość<br /><br /> Grubość uwidocznione jako właściwość<br /><br /> Opisuje kolor tekstu|Jeśli `True`, użytkownik może ustawić właściwość podane kształtu. Aby to ustawić, kliknij prawym przyciskiem myszy definicję kształtu, a następnie kliknij przycisk **Dodaj udostępniane**.|False|  
|Opis|Umożliwia dokumentowanie wygenerowanego projektanta.|\<Brak >|  
|Nazwa wyświetlana|Nazwa która będzie wyświetlana w wygenerowanym projektancie dla tego łącznika.|\<Brak >|  
|Stały tekst etykietki narzędzia|Tekst, który jest używany dla ustalonej etykietki narzędzia.|\<Brak >|  
|Słowo kluczowe pomocy|Słowo kluczowe, które jest używane do indeksowania pomocy F1 dla tego elementu.|\<Brak >|  
  
## <a name="see-also"></a>Zobacz też  
 [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
