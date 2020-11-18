---
title: 'Instrukcje: Dodawanie właściwości do projektów programu SharePoint | Microsoft Docs'
description: Użyj rozszerzenia projektu, aby dodać właściwość do projektu programu SharePoint. Właściwość pojawia się w okno Właściwości po wybraniu projektu w Eksplorator rozwiązań.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62766b704d140805a3b76dbc3c00acaf6257f5e5
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850159"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Instrukcje: Dodawanie właściwości do projektów programu SharePoint
  Możesz użyć rozszerzenia projektu, aby dodać właściwość do dowolnego projektu programu SharePoint. Właściwość pojawia się w oknie **Właściwości** , gdy projekt jest wybrany w **Eksplorator rozwiązań**.

 W poniższych krokach przyjęto założenie, że już utworzono rozszerzenie projektu. Aby uzyskać więcej informacji, zobacz [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Aby dodać właściwość do projektu programu SharePoint

1. Zdefiniuj klasę z właściwością publiczną, która reprezentuje właściwość dodawaną do projektów programu SharePoint. Jeśli chcesz dodać wiele właściwości, możesz zdefiniować wszystkie właściwości w tej samej klasie lub w różnych klasach.

2. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodzie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzenie parametru *projectService* .

3. W obsłudze zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzenia Dodaj wystąpienie klasy Properties do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> kolekcji parametru argumenty zdarzenia.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak dodać dwie właściwości do projektów programu SharePoint. Jedna Właściwość zachowuje swoje dane w pliku opcji użytkownika projektu (plik *. csproj. User* lub *. vbproj. User* ). Druga Właściwość zachowuje swoje dane w pliku projektu (plik *. csproj* lub *. vbproj* ).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Zrozumienie kodu
 Aby upewnić się, że to samo wystąpienie `CustomProjectProperties` klasy jest używane za każdym razem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> , gdy wystąpi zdarzenie, przykład kodu dodaje obiekt właściwości do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości projektu podczas pierwszego wystąpienia tego zdarzenia. Kod pobiera ten obiekt po każdym wystąpieniu tego zdarzenia. Aby uzyskać więcej informacji o używaniu <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości do kojarzenia danych z projektami, zobacz [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Aby zachować zmiany wartości właściwości, metody dostępu **Set** dla właściwości używają następujących interfejsów API:

- `CustomUserFileProperty` używa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> właściwości, aby zapisać jej wartość w pliku opcji użytkownika projektu.

- `CustomProjectFileProperty` używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody, aby zapisać jej wartość w pliku projektu.

  Aby uzyskać więcej informacji na temat utrwalania danych w tych plikach, zobacz [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowych
 Można zdefiniować sposób wyświetlania właściwości niestandardowej i zachowania jej w oknie **Właściwości** przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji właściwości. Następujące atrybuty są przydatne w wielu scenariuszach:

- <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która pojawia się w oknie **Właściwości** .

- <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się u dołu okna **Właściwości** , gdy właściwość jest zaznaczona.

- <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.

- <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardową konwersję między ciągiem, który jest wyświetlany w oknie **Właściwości** i wartością właściwości niebędącą ciągiem.

- <xref:System.ComponentModel.EditorAttribute>: Określa Edytor niestandardowy do użycia w celu zmodyfikowania właściwości.

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- Microsoft. VisualStudio. Shell

- Microsoft. VisualStudio. Shell. Interop

- Microsoft. VisualStudio. Shell. Interop. 8.0

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Zwiększ projekty programu SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Instrukcje: Dodawanie elementu menu skrótów do projektów programu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
