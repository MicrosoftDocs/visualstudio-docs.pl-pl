---
title: Odwołanie do schematu elementu projektu programu SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c261115b21d1067b7494d09ad8031b3f4dc5a8c5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864920"
---
# <a name="sharepoint-project-item-schema-reference"></a>Odwołanie do schematu elementu projektu SharePoint
  Program Visual Studio używa schematu elementu projektu programu SharePoint do sprawdzania poprawności zawartości *spdata* plików. *Spdata* plik Określa zawartości i zachowania elementu projektu programu SharePoint. Aby uzyskać więcej informacji o zawartości elementów projektu programu SharePoint, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Schemat elementu projektu programu SharePoint o nazwie ProjectItemModelSchema.xsd i jest instalowany domyślnie w katalogu % Program Files (11.0\Xml\Schemas x86)%\Microsoft programu Visual Studio.  
  
 Element główny jest [ProjectItem](../sharepoint/projectitem-element.md) elementu. W poniższej tabeli opisano wszystkie elementy zdefiniowane w schemacie.  
  
|Element|Opis|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Reprezentuje kolekcję elementów danych niestandardowych, które są skojarzone z elementem projektu programu SharePoint.|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Reprezentuje element danych niestandardowych, który jest skojarzony z elementu projektu programu SharePoint w formacie klucz/wartość. Klucz i wartość muszą być ciągami.|  
|[Featureproperties —](../sharepoint/featureproperties-element.md)|Reprezentuje kolekcję wartości właściwości, które są uwzględniane przy użyciu funkcji, gdy aplikacja jest wdrożona w programie SharePoint. Po wdrożeniu funkcji wartości właściwości są dostępne w kodzie.|  
|[FeatureProperty —](../sharepoint/featureproperty-element.md)|Reprezentuje właściwość niestandardowa, która jest uwzględniany w funkcji, gdy aplikacja jest wdrożona w programie SharePoint. Po wdrożeniu funkcji właściwości są dostępne w kodzie.|  
|[Pliki](../sharepoint/files-element.md)|Określa pliki, aby wdrożyć elementu projektu programu SharePoint, na przykład danych wyjściowych projektu lub pliku elementu funkcji.|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Reprezentuje element projektu programu SharePoint.|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Reprezentuje plik programu SharePoint, takich jak funkcja element pliku do uwzględnienia przy użyciu elementu projektu, gdy aplikacja jest wdrożona w programie SharePoint.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Reprezentuje zamapowany folder.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Reprezentuje dane wyjściowe projektu do uwzględnienia przy użyciu elementu projektu, gdy aplikacja jest wdrożona w programie SharePoint.|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Reprezentuje kontrolki ASPX lub składnik Web Part, który jest wyznaczony jako bezpieczna opcja dla każdemu użytkownikowi dostęp do strony ASPX w witrynie programu SharePoint.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Reprezentuje kolekcję formantów ASPX i składniki Web Part, które zostały oznaczone jako bezpieczne dla każdego użytkownika, dostęp do w dowolnej strony ASPX w witrynie programu SharePoint.|  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
