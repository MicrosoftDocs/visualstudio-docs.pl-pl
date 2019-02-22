---
title: 'Instrukcje: Dodawanie właściwości do typu elementu projektu SharePoint niestandardowego | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 45ccabfbeceeeb64a07764cc4ed32d6dead00db8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644487"
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint
  Podczas definiowania niestandardowego typu elementu projektu SharePoint, można dodać właściwość do elementu projektu. Właściwość pojawia się w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**.

 W następujących krokach założono, że swój własny typ elementu projektu programu SharePoint został już zdefiniowany. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Aby dodać właściwość do definicji typu elementu projektu

1.  Zdefiniuj klasę z właściwością publiczną, który reprezentuje właściwość, którą chcesz dodać do tego typu elementu niestandardowego projektu. Jeśli chcesz dodać wiele właściwości do typu elementu niestandardowego projektu, można zdefiniować wszystkie właściwości w tej samej klasy lub w różnych klas.

2.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metody usługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji, uchwyt <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenia *projectItemTypeDefinition* parametru.

3.  W procedurze obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenia dodaje wystąpienie klasy właściwości niestandardowych do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> zbiór parametr argumenty zdarzenia.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje, jak dodać właściwość o nazwie **właściwość przykład** do niestandardowego elementu typ projektu.

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]

### <a name="understand-the-code"></a>Rozumienie kodu
 Aby upewnić się, że to samo wystąpienie elementu `CustomProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> wystąpi zdarzenie, na przykład kodu zapisuje właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość czas pierwszego elementu projektu, to zdarzenie występuje. Kod pobiera ten obiekt zawsze wtedy, gdy ponownego wystąpienia tego zdarzenia. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości, aby zapisać dane z elementów projektu, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Aby utrwalić zmiany wartości właściwości **ustaw** akcesora `ExampleProperty` zapisuje nowa wartość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiekt, który jest skojarzony właściwość. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalenia danych za pomocą elementów projektu, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowe
 Można zdefiniować jak właściwość niestandardową wygląda i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeń nazw do definicji właściwości. Następujące atrybuty są przydatne w wielu scenariuszach:

-   <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która pojawia się w **właściwości** okna.

-   <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okno po wybraniu właściwości.

-   <xref:System.ComponentModel.DefaultValueAttribute>: Określa domyślną wartość właściwości.

-   <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowe konwersji między ciąg, który jest wyświetlany w **właściwości** okna, a wartość właściwości innych niż ciąg.

-   <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowy Edytor służące do modyfikowania właściwości.

## <a name="compile-the-code"></a>Skompilować kod
 Te przykłady kodu wymagają projekt biblioteki klas z odwołaniami do następujących zestawów:

-   Microsoft.VisualStudio.SharePoint

-   System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Wdrożenia elementu projektu
 Aby włączyć innych deweloperzy mogą używać element projektu, należy utworzyć szablon projektu lub szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Aby wdrożyć elementu projektu, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu, szablon i inne pliki, które chcesz rozesłać za pomocą elementu projektu. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Definiowanie typu elementu projektu SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Instrukcje: Dodawanie pozycji menu skrótów do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
