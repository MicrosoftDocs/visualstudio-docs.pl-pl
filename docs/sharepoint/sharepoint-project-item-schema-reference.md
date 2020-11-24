---
title: Odwołanie do schematu elementu projektu programu SharePoint | Microsoft Docs
description: Zobacz Omówienie odwołania do schematu XML elementu projektu programu SharePoint (ProjectItemModelSchema. xsd), który jest używany do sprawdzania poprawności zawartości plików. spdata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd425111e7e3d69e381e69e60daf914f74cd2d11
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442550"
---
# <a name="sharepoint-project-item-schema-reference"></a>Odwołanie do schematu elementu projektu programu SharePoint
  Program Visual Studio używa schematu elementu projektu programu SharePoint do walidacji zawartości plików *. spdata* . Plik *. spdata* określa zawartość i zachowanie elementu projektu programu SharePoint. Aby uzyskać więcej informacji na temat zawartości elementów projektu programu SharePoint, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Schemat elementu projektu programu SharePoint ma nazwę ProjectItemModelSchema. xsd i jest instalowany domyślnie w pliku% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas.

 Element główny to element [ProjectItem](../sharepoint/projectitem-element.md) . W poniższej tabeli opisano wszystkie elementy zdefiniowane przez schemat.

|Element|Opis|
|-------------|-----------------|
|[ExtensionData —](../sharepoint/extensiondata-element.md)|Reprezentuje kolekcję niestandardowych elementów danych, które są skojarzone z elementem projektu programu SharePoint.|
|[ExtensionDataItem —](../sharepoint/extensiondataitem-element.md)|Reprezentuje niestandardowy element danych skojarzony z elementem projektu programu SharePoint w formacie klucz/wartość. Zarówno klucz, jak i wartość muszą być ciągami.|
|[FeatureProperties —](../sharepoint/featureproperties-element.md)|Reprezentuje kolekcję wartości właściwości, które są dołączone do funkcji podczas jej wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostęp do wartości właściwości w kodzie.|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Reprezentuje właściwość niestandardową, która jest dołączana do funkcji podczas jej wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostęp do właściwości w kodzie.|
|[Files](../sharepoint/files-element.md)|Określa pliki do wdrożenia za pomocą elementu projektu programu SharePoint, takich jak plik elementu funkcji lub dane wyjściowe projektu.|
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint.|
|[ProjectItemFile —](../sharepoint/projectitemfile-element.md)|Reprezentuje plik programu SharePoint, taki jak plik elementu funkcji, do dołączenia do elementu projektu, gdy jest wdrażany w programie SharePoint.|
|[Projectitemfolder —](../sharepoint/projectitemfolder-element.md)|Reprezentuje zamapowany folder.|
|[ProjectOutputFile —](../sharepoint/projectoutputfile-element.md)|Przedstawia dane wyjściowe projektu do dołączenia do elementu projektu, gdy jest wdrażany w programie SharePoint.|
|[SafeControl](../sharepoint/safecontrol-element.md)|Reprezentuje kontrolkę ASPX lub składnik Web Part, który jest oznaczony jako bezpieczny dla każdego użytkownika, aby mógł uzyskać dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|
|[SafeControls —](../sharepoint/safecontrols-element.md)|Reprezentuje kolekcję formantów ASPX i składniki Web Part, które są wyznaczeni jako bezpieczne dla każdego użytkownika, który ma dostęp do dowolnej strony ASPX w witrynie programu SharePoint.|

## <a name="see-also"></a>Zobacz także
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
