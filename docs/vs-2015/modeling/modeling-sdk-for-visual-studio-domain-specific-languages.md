---
title: Modelowanie SDK — Języki specyficzne dla domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
ms.assetid: 17a531e2-1964-4a9d-84fd-6fb1b4aee662
caps.latest.revision: 79
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4907838720e3a68614e4b9774eb2d7e9fb42ff20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916537"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą zestawu SDK modelowania dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (MSDK) można tworzyć zaawansowane narzędzia programistyczne oparte na modelu, które można zintegrować z usługą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Na przykład narzędzia UML są tworzone przy użyciu zestawu MSDK. W ten sam sposób można utworzyć co najmniej jedną definicję modelu i zintegrować ją w zestaw narzędzi.

 Centralnym elementem zestawu MSDK jest definicja modelu tworzona w celu przedstawienia koncepcji z obszaru biznesowego. Model można obsłużyć różnymi narzędziami, takimi jak widok diagramowy, możliwość generowania kodu i innych artefaktów, polecenia służące do przekształcania modelu oraz możliwość korzystania z kodu i innych obiektów w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Podczas opracowywania modelu można połączyć go z innymi modelami i narzędziami w celu utworzenia zestawu narzędzi o dużych możliwościach, który będzie wspomagał proces projektowania.

 Zestaw MSDK umożliwia szybkie opracowanie modelu z użyciem języka specyficznego dla domeny (DSL). Należy rozpocząć od użycia specjalnego edytora w celu zdefiniowania schematu lub abstrakcyjnej składni wraz z notacją graficzną. Na podstawie tej definicji zestaw VMSDK generuje następujące elementy:

- Implementacja modelu z silnie typizowanym interfejsem API, który działa w magazynie opartym na transakcjach.

- Eksplorator oparty na drzewie.

- Edytor graficzny, w którym użytkownicy mogą wyświetlać zdefiniowany model lub jego części.

- Metody serializacji zapisujące modele w przystosowanych do odczytu plikach XML.

- Możliwości generowania kodu programu i innych artefaktów przy użyciu funkcji tworzenia szablonów tekstu.

  Wszystkie te funkcje można dostosowywać i rozszerzać. Rozszerzenia są integrowane w taki sposób, że można aktualizować definicję DSL oraz ponownie generować funkcje bez utraty używanych rozszerzeń.

## <a name="samples-and-the-latest-information"></a>Przykłady i najnowsze informacje
 [Pobierz zestaw SDK modelowania dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

 Aby uzyskać wskazówki dotyczące zaawansowanych technik i rozwiązywania problemów, odwiedź [forum rozszerzalności narzędzi do modelowania programu Visual Studio DSL &](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=dslvsarchx).

## <a name="in-this-section"></a>W tej sekcji
 [Wprowadzenie do języków specyficznych dla domeny](../modeling/getting-started-with-domain-specific-languages.md)

 [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md)

 [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)

 [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Sprawdzanie poprawności w języku specyficznym dla domeny](../modeling/validation-in-a-domain-specific-language.md)

 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)

 [Znajomość kodu DSL](../modeling/understanding-the-dsl-code.md)

 [Dostosowywanie przechowywania plików i serializacji XML](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Wdrażanie rozwiązań dla języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md)

 [Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Tworzenie języka specyficznego dla domeny opartego na podsystemie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Instrukcje: Rozszerzanie projektanta języka specyficznego dla domeny](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Wersje programu Visual Studio obsługiwane przez zestaw Visualization and Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Porady: migracja języka specyficznego dla domeny do nowej wersji](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Odwołania API do modelowania SDK dla Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
