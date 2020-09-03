---
title: Dokumentacja interfejsu API dla zestawu SDK modelowania
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 590c9a69-4e22-4841-bb23-f32e80ec1e76
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65f8703597d6297afde6e2685594784fdd1d755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672844"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw SDK wizualizacji i modelowania programu Visual Studio zapewnia platformę, na której są zbudowane Języki specyficzne dla domeny (DSL) i narzędzia UML.

> [!NOTE]
> Aby uzyskać informacje o interfejsie API modelowania UML, zobacz [Dokumentacja interfejsu API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md). Aby uzyskać informacje na temat transformacji tekstu, zobacz [Dostosowywanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md).

 Ta sekcja zawiera materiały referencyjne dla przestrzeni nazw o nazwach zaczynających się od "Microsoft. VisualStudio. Modeling".

|Przestrzeń nazw|Zawartość|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy takie jak ModelElement, które są klasą bazową wszystkich klas domeny zdefiniowanych w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy tworzące część definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Narzędzia do przeglądania i pomiaru wydajności magazynu modeli.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy takie jak ShapeElement, które są klasą bazową wszystkich kształtów zdefiniowanych w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metody gestu i wyboru.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Wewnętrzne klasy projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które umożliwiają rozbudowa projektanta DSL przy użyciu poleceń, gestów i walidacji.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzające ModelElement, które implementują rozszerzalność DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atrybuty rozszerzalności|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umożliwia tworzenie części modelu tylko do odczytu.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Interfejs API ModelBus, który pomaga zintegrować różne modele.|
|[Microsoft. VisualStudio. Modeling. Integration. wybierak](/previous-versions/ee904394(v=vs.140))|Okno dialogowe, które umożliwia użytkownikom nawigowanie do modeli i elementów w celu utworzenia odwołań ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Wybór usługi.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Struktura adaptera ModelBus dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. wybierak](/previous-versions/ee886769(v=vs.140))|Okno dialogowe selektora, które umożliwia użytkownikom nawigowanie do modeli i elementów w celu utworzenia odwołań ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między językami DSL i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie poleceń menu skrótów (kontekstu).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia zdefiniowanie ograniczeń walidacji.|

## <a name="see-also"></a>Zobacz też

- [Wykaz interfejsów API dla rozszerzalności modelowania UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
- [Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)
