---
title: Dokumentacja interfejsu API do modelowania SDK
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2cbf516b5ed999623c05e7f68656199363906bf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63408440"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Visualization i Modeling SDK udostępnia platformę, na którym są wbudowane narzędzia UML i języków specyficznych dla domeny (DSL).

> [!NOTE]
> Aby uzyskać informacje o interfejsie API do modelowania UML, zobacz [wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Aby uzyskać informacji na temat przekształcania tekstu, zobacz [Dostosowywanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md).

 Ta sekcja zawiera dokumentacja dotycząca przestrzeni nazw, które mają nazwy rozpoczynające się od "Microsoft.VisualStudio.Modeling".

|Przestrzeń nazw|Zawartość|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy, takie jak element modelu, który jest klasą bazową dla wszystkich klas domeny, które należy zdefiniować w języka DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy, które stanowią część definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Model Store Podgląd i wydajności pomiaru narzędzia.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy, takie jak ShapeElement, która jest klasą bazową dla wszystkich kształtów, które definiujesz w języka DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gestami i wybór metody.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Klasy wewnętrzne projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które pozwolą na rozszerzenie projektanta DSL za pomocą poleceń i gestów i sprawdzania poprawności.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzenia dla element modelu, które implementują rozszerzalności DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Rozszerzeń atrybuty|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Pozwala udostępnić części modelu w trybie tylko do odczytu.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Modelbus interfejsu API, która ułatwia integrowanie różnych modeli.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Okno dialogowe, która umożliwia użytkownikom, przejdź do modeli i elementów, aby utworzyć odwołania Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Usługa selektora.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Modelbus karty umożliwiająca [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Okno dialogowe selektora, który umożliwia użytkownikom, przejdź do modeli i elementów, aby utworzyć odwołania Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między językami DSL i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie polecenia menu skrótów (kontekstu).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia definiowanie ograniczeń walidacji.|

## <a name="see-also"></a>Zobacz też
 [Dokumentacja interfejsu API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md) [dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)
