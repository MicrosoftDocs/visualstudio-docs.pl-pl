---
title: Hierarchiczna organizacja zasobów dla lokalizacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a79caca18c7813605ff851eea6bda642e6300a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645612"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchiczna organizacja zasobów do lokalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio zlokalizowane zasoby (dane, takie jak ciągi i obrazy odpowiednie dla każdej kultury) są przechowywane w oddzielnych plikach i ładowane zgodnie z ustawieniem kultury interfejsu użytkownika. Aby zrozumieć, jak zlokalizowane są załadowane zasoby, warto traktować je jako uporządkowane w sposób hierarchiczny.

## <a name="kinds-of-resources-in-the-hierarchy"></a>Rodzaje zasobów w hierarchii

- W górnej części hierarchii znajdują się zasoby rezerwowe dla domyślnej kultury, na przykład angielski ("en"). Są to jedyne zasoby, które nie mają własnego pliku; są one przechowywane w głównym zestawie.

- Poniżej zasobów rezerwowych są zasoby dla wszelkich neutralnych kultur. Neutralna kultura jest skojarzona z językiem, ale nie z krajem/regionem. Na przykład francuski ("fr") jest kulturą neutralną. (Należy zauważyć, że zasoby rezerwowe są również dla kulturą neutralną, ale specjalną).

- Poniżej znajdują się zasoby dla określonych kultur. Określona kultura jest skojarzona z językiem i krajem/regionem. Na przykład francuski kanadyjski ("fr-CA") jest określoną kulturą.

  Jeśli aplikacja podejmie próbę załadowania dowolnego zlokalizowanego zasobu, takiego jak ciąg, i nie znajdzie go, zostanie przekierowany do hierarchii do momentu znalezienia pliku zasobów zawierającego żądany zasób.

  Najlepszym sposobem przechowywania zasobów jest ich uogólnianie do możliwie największej ilości. Oznacza to, że można przechowywać zlokalizowane ciągi, obrazy i tak dalej w plikach zasobów dla kultur neutralnych, a nie określonych kultur wszędzie tam, gdzie to możliwe. Na przykład jeśli masz zasoby dla kultury francuskiej ("fr-to"), a zasoby znajdujące się bezpośrednio powyżej są zasobami rezerwowymi w języku angielskim, problem może skutkować tym, że ktoś korzysta z aplikacji w systemie skonfigurowanym dla francuskiej kultury kanadyjskiej. System wyszuka zestawu satelickiego dla "fr-CA", nie znajdzie go i załaduje główny zestaw zawierający zasób rezerwowy, który jest w języku angielskim, zamiast ładowania zasobów francuskich. Na poniższej ilustracji przedstawiono ten niepożądany scenariusz.

  ![Tylko określone zasoby](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")

  Jeśli zgodnie z zalecaną metodą umieszczania możliwie największej liczby zasobów w niezależnym pliku zasobów dla kultury "fr", francuskiego użytkownika Kanady nie zobaczy zasobów oznaczonych jako kultura "fr-to", ale będzie ona wyświetlana w języku francuskim. W poniższej sytuacji przedstawiono ten preferowany scenariusz.

  ![Grafika NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")

## <a name="see-also"></a>Zobacz też
 [Neutralne Języki zasobów dla zabezpieczeń lokalizacji](../ide/neutral-resources-languages-for-localization.md) [i zlokalizowanych zestawów satelickich](../ide/security-and-localized-satellite-assemblies.md) [lokalizowania aplikacji](../ide/localizing-applications.md) [globalizacji i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md) [instrukcje: Ustawianie kultury i kulturę interfejsu użytkownika dla Windows Forms Globalizacja](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) [How to: Set kulturę i kulturę interfejsu użytkownika dla globalizacji strony sieci Web ASP.NET](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)
