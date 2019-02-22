---
title: Projectitem — Element | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6fc30ff87d02013a95ea7950841e3185b2bdc69d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643668"
---
# <a name="projectitem-element"></a>ProjectItem — element
  Reprezentuje element projektu programu SharePoint. Ten element wymaganego głównego elementu z *spdata* pliku.

## <a name="syntax"></a>Składnia

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|**DefaultFile**|Opcjonalnie **xs: ciąg** atrybutu.<br /><br /> Ścieżka względna, łącznie z nazwą pliku, pliku, który zostanie otwarty w edytorze programu Visual Studio, po otwarciu elementu projektu programu SharePoint w **Eksploratora rozwiązań**. Ścieżka jest względna wobec folderu, który zawiera *spdata* pliku.|
|**FeatureReceiverClass**|Opcjonalnie **xs:string** atrybutu.<br /><br /> W pełni kwalifikowana nazwa klasę odbiorcy funkcji dla tego elementu projektu programu SharePoint. Aby uzyskać więcej informacji na temat funkcji odbiorcy, zobacz [zapewniają informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Określa pełni kwalifikowaną nazwę zestawu, który definiuje odbiorcę funkcji dla tego elementu projektu programu SharePoint. Aby uzyskać więcej informacji na temat funkcji odbiorcy, zobacz [zapewniają informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Aby uzyskać więcej informacji o w pełni kwalifikowane nazwy zestawów, zobacz [nazw zestawów](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Określa poziomy zaufania, które obsługuje tego elementu projektu programu SharePoint. Ta wartość może być jednym z następujących ciągów: Piaskownicy, FullTrust, lub wszystkie. Wartość określa wszystkie Sandboxed i FullTrust.<br /><br /> W programie SharePoint projektu elementu Typ niestandardowy, wartość tego atrybutu odpowiada wartości, które można przypisać do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> właściwość w danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Jeśli określisz inną wartość dla tego atrybutu, Visual Studio zastępuje wartość, dzięki czemu Określa on taki sam poziom zaufania, który określisz w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> właściwości.|
|**SupportedDeploymentScopes**|Opcjonalnie **xs:string** atrybutu.<br /><br /> Określa zakresów wdrożenia, które obsługuje tego elementu projektu programu SharePoint. Ta wartość jest rozdzielana przecinkami ciąg, który składa się z co najmniej jedną z następujących ciągów: Farma, witryny, sieci Web, aplikacji sieci Web lub pakietu. Na przykład: `Web, Site`<br /><br /> W programie SharePoint projektu elementu Typ niestandardowy, wartość tego atrybutu odpowiada wartości, które można przypisać do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> właściwość w danej implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Jeśli określisz inną wartość dla tego atrybutu, Visual Studio zastępuje wartość, dzięki czemu Określa on taki sam poziom zaufania, który określisz w <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> właściwości.|
|**Typ**|Wymagane **xs:string** atrybutu.<br /><br /> Identyfikator elementu projektu programu SharePoint. W programie SharePoint projektu elementu Typ niestandardowy, identyfikator jest ciąg, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Aby uzyskać listę identyfikatorów dla wbudowanych elementów projektu programu SharePoint, dołączone do programu Visual Studio, zobacz [elementów projektu programu SharePoint z rozszerzenia](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję elementów danych niestandardowych, które są skojarzone z elementem projektu programu SharePoint.<br /><br /> Może zawierać tylko jeden **extensiondata —** elementu.|
|[Featureproperties —](../sharepoint/featureproperties-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję wartości właściwości, które są uwzględniane przy użyciu funkcji, gdy aplikacja jest wdrożona w programie SharePoint.<br /><br /> Może zawierać tylko jeden **featureproperties —** elementu.|
|[Pliki](../sharepoint/files-element.md)|Opcjonalnie **FileCollectionType** elementu.<br /><br /> Określa pliki do wdrożenia przy użyciu elementu projektu programu SharePoint, takich jak funkcja elementu pliki i dane wyjściowe projektów zależnych programu SharePoint.<br /><br /> Włącz **pliki** lub **projectitemfolder —** elementu, ale nie oba.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Opcjonalnie **ProjectItemFolderType** elementu.<br /><br /> Reprezentuje zamapowany folder.<br /><br /> Włącz **pliki** lub **projectitemfolder —** elementu, ale nie oba.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję formantów ASPX i składniki Web Part, które zostały oznaczone jako bezpieczne dla każdego użytkownika, dostęp do w dowolnej strony ASPX w witrynie programu SharePoint.<br /><br /> Może zawierać tylko jeden **SafeControls** elementu.|

### <a name="parent-elements"></a>Elementy nadrzędne
 Brak.

## <a name="element-information"></a>Informacje o elementach

|||
|-|-|
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema.xsd|
|**Może być pusta.**|Nie|

## <a name="see-also"></a>Zobacz także
[Rseference schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
