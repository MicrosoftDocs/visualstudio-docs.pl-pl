---
title: Dokumentacja interfejsu API dla zestawu SDK modelowania
description: Dowiedz się, Visual Studio Sdk do wizualizacji i modelowania udostępnia platformę, na której są zbudowane narzędzia języków specyficznych dla domeny (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9603ace5751443c04d0a7503a43e08c044269817
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385464"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio

Zestaw SDK Visual Studio wizualizacji i modelowania udostępnia platformę, na której są zbudowane narzędzia języków specyficznych dla domeny (DSL).

Ta sekcja zawiera materiały referencyjne dotyczące przestrzeni nazw o nazwach zaczynających się od "Microsoft.VisualStudio.Modeling".

|Przestrzeń nazw|Zawartość|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy, takie jak ModelElement, który jest klasą bazową wszystkich klas domen, które definiujesz w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy, które stanowią część definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Model Store Viewer i narzędzia do pomiaru wydajności.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy, takie jak ShapeElement, która jest klasą bazową wszystkich kształtów, które definiujesz w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metody Gest i Wybór.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Klasy wewnętrzne projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które umożliwiają rozszerzenie projektanta DSL za pomocą poleceń, gestów i walidacji.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzeń dla elementu ModelElement, które implementują rozszerzalność DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atrybuty rozszerzalności|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umożliwia tworzenie części modelu tylko do odczytu.|
|[Microsoft.VisualStudio.Modeling.Integration](/previous-versions/ee904412(v=vs.140))|Interfejs API Modelbus, który pomaga integrować różne modele.|
|[Microsoft.VisualStudio.Modeling.Integration.Picker](/previous-versions/ee904394(v=vs.140))|Okno dialogowe, które umożliwia użytkownikom przechodzenie do modeli i elementów w celu utworzenia odwołań Modelbus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Usługa s wyboru.|
|[Microsoft.VisualStudio.Modeling.Integration.Shell](/previous-versions/ee869435(v=vs.140))|Modelbus adapter framework for Visual Studio.|
|[Microsoft.visualstudio.modeling.integration.shell.picker](/previous-versions/ee886769(v=vs.140))|Okno dialogowe S wyboru, które umożliwia użytkownikom przechodzenie do modeli i elementów w celu utworzenia odwołań Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między językami DSL i Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie poleceń menu skrótów (kontekstowych).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia zdefiniowanie ograniczeń walidacji.|

## <a name="see-also"></a>Zobacz też

- [Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)
