---
title: 'Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu programu SharePoint | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 752a782bb4aafd977ff10a0b57dd971f7ad6bed4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584259"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint
  Możesz użyć rozszerzenia elementu projektu, aby dodać właściwość do dowolnego elementu projektu programu SharePoint, który jest już zainstalowany w programie Visual Studio. Właściwość pojawia się w oknie **Właściwości** , gdy element projektu jest wybrany w **Eksplorator rozwiązań**.

 W poniższych krokach przyjęto założenie, że już utworzono rozszerzenie elementu projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

### <a name="to-add-a-property-to-a-project-item-extension"></a>Aby dodać właściwość do rozszerzenia elementu projektu

1. Zdefiniuj klasę z właściwością publiczną, która reprezentuje właściwość dodawaną do typu elementu projektu. Jeśli chcesz dodać wiele właściwości do typu elementu projektu, możesz zdefiniować wszystkie właściwości w tej samej klasie lub w różnych klasach.

2. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metodzie <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji należy obsłużyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenie parametru *projectItemType* .

3. W obsłudze zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenia Dodaj wystąpienie klasy Properties do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> kolekcji parametru argumenty zdarzenia.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje, jak dodać właściwość o nazwie **przykład właściwości** do elementu projektu odbiorcy zdarzeń.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]

### <a name="understand-the-code"></a>Zrozumienie kodu
 Aby upewnić się, że to samo wystąpienie `CustomProperties` klasy jest używane za każdym razem <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> , gdy wystąpi zdarzenie, przykład kodu dodaje obiekt właściwości do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości elementu projektu przy pierwszym wystąpieniu tego zdarzenia. Kod pobiera ten obiekt po każdym wystąpieniu tego zdarzenia. Aby uzyskać więcej informacji o używaniu <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości do kojarzenia danych z elementami projektu, zobacz [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Aby zachować zmiany wartości właściwości, metoda dostępu **Set** dla `ExampleProperty` zapisuje nową wartość do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu, z którym skojarzona jest ta właściwość. Aby uzyskać więcej informacji o używaniu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalania danych za pomocą elementów projektu, zobacz [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowych
 Można zdefiniować sposób wyświetlania właściwości niestandardowej i zachowania jej w oknie **Właściwości** przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeni nazw do definicji właściwości. Następujące atrybuty są przydatne w wielu scenariuszach:

- <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która pojawia się w oknie **Właściwości** .

- <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się u dołu okna **Właściwości** , gdy właściwość jest zaznaczona.

- <xref:System.ComponentModel.DefaultValueAttribute>: Określa wartość domyślną właściwości.

- <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardową konwersję między ciągiem, który jest wyświetlany w oknie **Właściwości** i wartością właściwości niebędącą ciągiem.

- <xref:System.ComponentModel.EditorAttribute>: Określa Edytor niestandardowy do użycia w celu zmodyfikowania właściwości.

## <a name="compile-the-code"></a>Kompiluj kod
 Te przykłady wymagają projektu biblioteki klas z odwołaniami do następujących zestawów:

- Microsoft. VisualStudio. SharePoint

- System. ComponentModel. kompozycji

## <a name="deploy-the-extension"></a>Wdróż rozszerzenie
 Aby wdrożyć rozszerzenie, Utwórz [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX) dla zestawu i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Instrukcje: Dodawanie elementu menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Zwiększ elementy projektu SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Przewodnik: zwiększanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
