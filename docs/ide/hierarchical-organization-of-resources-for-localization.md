---
title: Hierarchiczna organizacja zasobów do lokalizacji
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05658e706b2aec4a388c5efff8a5b1d7357c05a9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917706"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchiczna organizacja zasobów do lokalizacji

W programie Visual Studio zlokalizowane zasoby (dane, takie jak ciągi i odpowiednie do poszczególnych kultur obrazów) są przechowywane w oddzielnych plikach i załadować zgodnie z ustawieniem kultury interfejsu użytkownika. Aby zrozumieć, w jaki sposób zlokalizowane zasoby są ładowane, warto traktować je jak zorganizowane hierarchicznie.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Rodzaje zasobów w hierarchii

- Zasoby rezerwowe dla Twojej domyślnej kultury, na przykład język angielski ("PL"), znajdują się na szczycie hierarchii. Te zasoby rezerwowe są jedynymi osobami, które nie mają własnych plików; są one przechowywane w głównym zestawie.

- Poniższe zasoby rezerwowe są zasoby dla dowolnej kultury neutralnej. Kultury neutralnej jest skojarzony z innym języku, ale nie kraj/region. Na przykład francuski ("fr") jest kultury neutralnej. (Zasoby rezerwowe są również dla kultury neutralnej, ale wspaniałe).

- Poniżej kultury neutralnej zasoby są zasoby dla dowolnej określonych kultur. Określonej kultury jest skojarzony z języka i kraju/regionu. Na przykład francuski kanadyjski ("fr-CA") jest określonej kultury.

Jeśli aplikacja próbuje załadować żadnych zlokalizowany zasób, takie jak ciąg i nie zostanie znaleziona, aż do znalezienia pliku zasobu zawierającego żądanego zasobu będą przesyłane w hierarchii.

Najlepszym sposobem przechowywania zasobów jest uogólniać je w miarę możliwości. Oznacza to, do przechowywania zlokalizowane ciągi, obrazy i innych elementów w plikach zasobów dla kultury neutralnej zamiast określonych kultur, jeśli to możliwe. Na przykład jeśli zasoby dla Belgii francuski ("fr-być") kultury i natychmiast wspomniane zasoby znajdują się zasoby rezerwowe w języku angielskim, problem może spowodować, gdy ktoś będzie korzystać z aplikacji w systemie, skonfigurowane dla kultury francuski kanadyjski. System wyszukuje zestaw satelicki dla "fr-CA", ale nie można go odnaleźć, więc ładuje głównego zestawu zawierającego bazoey zasoby, angielski, zamiast ładowanie zasobów francuskim. Na poniższej ilustracji przedstawiono w tym scenariuszu niepożądane.

![Tylko określone zasoby](../ide/media/vbspecificresourcesonly.gif)

W przypadku postępuj zgodnie z zalecaną praktyką składania tylu zasobów, jak to możliwe w pliku zasobów neutralnej kultury "fr", francuski kanadyjski użytkownika nie widział zasoby oznaczone na "fr-być" kultury, ale będą wyświetlane ciągi w języku francuskim. Następującej sytuacji pokazuje, w tym scenariuszu preferowany.

![NeutralSpecificResources — grafika](../ide/media/vbneutralspecificresources.gif)

## <a name="see-also"></a>Zobacz także

- [Neutralny język zasobów dla lokalizacji](../ide/neutral-resources-languages-for-localization.md)
- [Zabezpieczenia a zlokalizowane zestawy satelickie](../ide/security-and-localized-satellite-assemblies.md)
- [Lokalizowanie aplikacji](../ide/localizing-applications.md)
- [Globalizacja i lokalizacja aplikacji](../ide/globalizing-and-localizing-applications.md)