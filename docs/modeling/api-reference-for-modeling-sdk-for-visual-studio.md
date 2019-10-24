---
title: Dokumentacja interfejsu API dla zestawu SDK modelowania
ms.date: 11/04/2016
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30a0ef7a4b94e6d9cb55583c8bc7317e28d08b93
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747640"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio

Zestaw SDK wizualizacji i modelowania programu Visual Studio zapewnia platformę, na której są kompilowane narzędzia dla języków specyficznych dla domeny.

Ta sekcja zawiera materiały referencyjne dla przestrzeni nazw o nazwach zaczynających się od "Microsoft. VisualStudio. Modeling".

|Przestrzeń nazw|Zawartość|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy takie jak ModelElement, które są klasą bazową wszystkich klas domeny zdefiniowanych w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy tworzące część definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Narzędzia do przeglądania i pomiaru wydajności magazynu modeli.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy takie jak ShapeElement, które są klasą bazową wszystkich kształtów zdefiniowanych w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Metody gestu i wyboru.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Wewnętrzne klasy projektanta definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które umożliwiają rozszeranie projektanta DSL przy użyciu poleceń, gestów i walidacji.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzające ModelElement, które implementują rozszerzalność DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atrybuty rozszerzalności|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umożliwia tworzenie części modelu tylko do odczytu.|
|[Microsoft. VisualStudio. Modeling. Integration](/previous-versions/ee904412(v=vs.140))|Interfejs API ModelBus, który pomaga zintegrować różne modele.|
|[Microsoft. VisualStudio. Modeling. Integration. wybierak](/previous-versions/ee904394(v=vs.140))|Okno dialogowe, które umożliwia użytkownikom nawigowanie do modeli i elementów w celu utworzenia odwołań ModelBus.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|Wybór usługi.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell](/previous-versions/ee869435(v=vs.140))|Platforma adapterów ModelBus dla programu Visual Studio.|
|[Microsoft. VisualStudio. Modeling. Integration. Shell. wybierak](/previous-versions/ee886769(v=vs.140))|Okno dialogowe selektora, które umożliwia użytkownikom nawigowanie do modeli i elementów w celu utworzenia odwołań ModelBus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między językami DSL i Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie poleceń menu skrótów (kontekstu).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia zdefiniowanie ograniczeń walidacji.|

## <a name="see-also"></a>Zobacz także

- [Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)
