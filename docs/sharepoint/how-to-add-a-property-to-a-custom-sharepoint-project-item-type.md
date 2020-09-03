---
title: Dodaj właściwość do niestandardowego typu elementu projektu SharePoint
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 54765b9b6b82214a7deccaee4f9ee671a72dd40d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016000"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint
  Podczas definiowania niestandardowego typu elementu projektu programu SharePoint można dodać właściwość do elementu projektu. Właściwość pojawia się w oknie **Właściwości** , gdy element projektu jest wybrany w **Eksplorator rozwiązań**.

 W poniższych krokach przyjęto założenie, że masz już zdefiniowany własny typ elementu projektu programu SharePoint. Aby uzyskać więcej informacji, zobacz [How to: define a SharePoint Project Type Item](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Aby dodać właściwość do definicji typu elementu projektu

1. Zdefiniuj klasę z właściwością publiczną, która reprezentuje właściwość dodawaną do niestandardowego typu elementu projektu. Jeśli chcesz dodać wiele właściwości do niestandardowego typu elementu projektu, możesz zdefiniować wszystkie właściwości w tej samej klasie lub w różnych klasach.

2. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodzie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie parametru *ProjectItemTypeDefinition* .

3. W obsłudze zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenia Dodaj wystąpienie klasy właściwości niestandardowych do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> kolekcji parametru argumenty zdarzenia.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać właściwość o nazwie **example** do niestandardowego typu elementu projektu.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Zrozumienie kodu
 Aby zapewnić, że to samo wystąpienie `CustomProperties` klasy jest używane za każdym razem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , gdy wystąpi zdarzenie, kod przykład zapisuje obiekt właściwości do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości elementu projektu przy pierwszym wystąpieniu tego zdarzenia. Kod pobiera ten obiekt po każdym wystąpieniu tego zdarzenia. Aby uzyskać więcej informacji na temat używania <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości do zapisywania danych za pomocą elementów projektu, zobacz [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Aby zachować zmiany wartości właściwości, metoda dostępu **Set** dla `ExampleProperty` zapisuje nową wartość do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu, z którym skojarzona jest ta właściwość. Aby uzyskać więcej informacji o używaniu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalania danych za pomocą elementów projektu, zobacz [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowych
 Można zdefiniować sposób wyświetlania właściwości niestandardowej i zachowania jej w oknie **Właściwości** przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji właściwości. Następujące atrybuty są przydatne w wielu scenariuszach:

- <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która pojawia się w oknie **Właściwości** .

- <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się u dołu okna **Właściwości** , gdy właściwość jest zaznaczona.

- <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.

- <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardową konwersję między ciągiem, który jest wyświetlany w oknie **Właściwości** i wartością właściwości niebędącą ciągiem.

- <xref:System.ComponentModel.EditorAttribute>: Określa Edytor niestandardowy do użycia w celu zmodyfikowania właściwości.

## <a name="compile-the-code"></a>Kompiluj kod
 Te przykłady kodu wymagają projektu biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-project-item"></a>Wdróż element projektu
 Aby umożliwić innym deweloperom korzystanie z elementu projektu, Utwórz szablon projektu lub szablon elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Aby wdrożyć element projektu, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu, szablonu i innych plików, które chcesz dystrybuować z elementem projektu. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie elementu menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
