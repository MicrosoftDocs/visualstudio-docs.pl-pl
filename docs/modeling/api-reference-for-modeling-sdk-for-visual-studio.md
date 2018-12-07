---
title: Dokumentacja interfejsu API do modelowania SDK
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d2176e18678685cc1dbc69f8c33b5aee7e426d57
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53061724"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio

Visual Studio Visualization i Modeling SDK udostępnia platformę, na którym są tworzone z narzędzi języki specyficzne dla domeny (DSL).

Ta sekcja zawiera dokumentacja dotycząca przestrzeni nazw, które mają nazwy rozpoczynające się od "Microsoft.VisualStudio.Modeling".

|Przestrzeń nazw|Zawartość|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy, takie jak element modelu, który jest klasą bazową dla wszystkich klas domeny, które należy zdefiniować w języka DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy, które stanowią część definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Model Store Podgląd i wydajności pomiaru narzędzia.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy, takie jak ShapeElement, która jest klasą bazową dla wszystkich kształtów, które definiujesz w języka DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gestami i wybór metody.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Klasy wewnętrzne projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które pozwolą na rozszerzenie projektanta DSL za pomocą poleceń, gestów i sprawdzania poprawności.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzenia dla element modelu, które implementują rozszerzalności DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Rozszerzeń atrybuty|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Pozwala udostępnić części modelu w trybie tylko do odczytu.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Modelbus interfejsu API, która ułatwia integrowanie różnych modeli.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Okno dialogowe, która umożliwia użytkownikom, przejdź do modeli i elementów, aby utworzyć odwołania Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Usługa selektora.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Struktura karty Modelbus dla programu Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Okno dialogowe selektora, który umożliwia użytkownikom, przejdź do modeli i elementów, aby utworzyć odwołania Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między językami DSL i programu Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie polecenia menu skrótów (kontekstu).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia definiowanie ograniczeń walidacji.|

## <a name="see-also"></a>Zobacz też

- [Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)
