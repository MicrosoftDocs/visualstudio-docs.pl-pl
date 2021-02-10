---
title: ProjectItem — element | Microsoft Docs
description: Pobierz informacje referencyjne na temat elementu ProjectItem, który reprezentuje element projektu programu SharePoint w odwołaniu do schematu XML elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b94b44bfa442805c4c785a48c9f60f56eb8e002
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950591"
---
# <a name="projectitem-element"></a>ProjectItem — element
  Reprezentuje element projektu programu SharePoint. Ten element jest wymaganym elementem głównym pliku *. spdata* .

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
|**DefaultFile**|Opcjonalny atrybut **xs: String** .<br /><br /> Ścieżka względna, wraz z nazwą pliku, otwieraną w edytorze programu Visual Studio podczas otwierania elementu projektu programu SharePoint w **Eksplorator rozwiązań**. Ścieżka jest względna do folderu, który zawiera plik *. spdata* .|
|**FeatureReceiverClass**|Opcjonalny atrybut **xs: String** .<br /><br /> W pełni kwalifikowana nazwa klasy odbiorcy funkcji dla tego elementu projektu programu SharePoint. Aby uzyskać więcej informacji na temat odbiorników funkcji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Opcjonalny atrybut **xs: String** .<br /><br /> Określa w pełni kwalifikowaną nazwę zestawu, który definiuje odbiorcę funkcji dla tego elementu projektu programu SharePoint. Aby uzyskać więcej informacji na temat odbiorników funkcji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Aby uzyskać więcej informacji na temat w pełni kwalifikowanych nazw zestawów, zobacz [nazwy zestawów](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Opcjonalny atrybut **xs: String** .<br /><br /> Określa poziomy zaufania obsługiwane przez ten element projektu programu SharePoint. Ta wartość może być jednym z następujących ciągów: piaskownicy, FullTrust lub ALL. Wartość All określa zarówno tryb piaskownicy, jak i FullTrust.<br /><br /> W przypadku niestandardowego typu elementu projektu programu SharePoint wartość tego atrybutu odpowiada wartości przypisanej do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> właściwości w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Jeśli określisz inną wartość dla tego atrybutu, program Visual Studio zastępuje wartość tak, aby określać ten sam poziom zaufania określony we <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> właściwości.|
|**SupportedDeploymentScopes**|Opcjonalny atrybut **xs: String** .<br /><br /> Określa zakresy wdrożenia obsługiwane przez ten element projektu programu SharePoint. Ta wartość jest ciągiem rozdzielanym przecinkami, który składa się z co najmniej jednego z następujących ciągów: farmy, witryny, sieci Web, WebApplication lub pakietu. Na przykład: `Web, Site`<br /><br /> W przypadku niestandardowego typu elementu projektu programu SharePoint wartość tego atrybutu odpowiada wartości przypisanej do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> właściwości w implementacji <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody. Jeśli określisz inną wartość dla tego atrybutu, program Visual Studio zastępuje wartość tak, aby określać ten sam poziom zaufania określony we <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> właściwości.|
|**Typ**|Wymagany atrybut **xs: String** .<br /><br /> Identyfikator elementu projektu programu SharePoint. W przypadku niestandardowego typu elementu projektu programu SharePoint identyfikator jest ciągiem przekazywanym do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Aby uzyskać więcej informacji, zobacz [How to: define a SharePoint Project Type Item](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Aby zapoznać się z listą identyfikatorów wbudowanych elementów projektu programu SharePoint dołączonych do programu Visual Studio, zobacz sekcję [rozszerzając elementy projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ExtensionData —](../sharepoint/extensiondata-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję niestandardowych elementów danych, które są skojarzone z elementem projektu programu SharePoint.<br /><br /> Można uwzględnić tylko jeden element **ExtensionData —** .|
|[FeatureProperties —](../sharepoint/featureproperties-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję wartości właściwości, które są dołączone do funkcji podczas jej wdrażania w programie SharePoint.<br /><br /> Można uwzględnić tylko jeden element **FeatureProperties —** .|
|[Pliki](../sharepoint/files-element.md)|Opcjonalny element **FileCollectionType** .<br /><br /> Określa pliki do wdrożenia za pomocą elementu projektu programu SharePoint, takich jak pliki elementów funkcji i dane wyjściowe zależnych projektów spoza programu SharePoint.<br /><br /> Dołącz **pliki** lub element **projectitemfolder —** , ale nie oba jednocześnie.|
|[Projectitemfolder —](../sharepoint/projectitemfolder-element.md)|Opcjonalny element **ProjectItemFolderType** .<br /><br /> Reprezentuje zamapowany folder.<br /><br /> Dołącz **pliki** lub element **projectitemfolder —** , ale nie oba jednocześnie.|
|[SafeControls —](../sharepoint/safecontrols-element.md)|Element opcjonalny.<br /><br /> Reprezentuje kolekcję formantów ASPX i składniki Web Part, które są wyznaczeni jako bezpieczne dla każdego użytkownika, który ma dostęp do dowolnej strony ASPX w witrynie programu SharePoint.<br /><br /> Można uwzględnić tylko jeden element **SafeControls —** .|

### <a name="parent-elements"></a>Elementy nadrzędne
 Brak.

## <a name="element-information"></a>Informacje o elemencie

|Właściwość|Wartość|
|-|-|
|**Przestrzeń nazw**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nazwa schematu**|Schemat elementu projektu programu SharePoint|
|**Plik walidacji**|ProjectItemModelSchema. xsd|
|**Może być puste**|Nie|

## <a name="see-also"></a>Zobacz też
[Rseference schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
