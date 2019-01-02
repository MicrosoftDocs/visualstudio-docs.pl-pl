---
title: 'Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 424e6d6295b0a9af1ec5d155353f766d4ba17689
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950189"
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Instrukcje: Dodawanie właściwości do rozszerzenia elementu projektu SharePoint
  Rozszerzenia elementu projektu umożliwia dodawanie właściwości do dowolnego elementu projektu programu SharePoint, która jest już zainstalowana w programie Visual Studio. Właściwość pojawia się w **właściwości** okna po wybraniu elementu projektu w **Eksploratora rozwiązań**.  
  
 W następujących krokach założono, że utworzono już rozszerzenie elementu projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Aby dodać właściwość do rozszerzenia elementu projektu  
  
1.  Zdefiniuj klasę z właściwością publiczną, odpowiadający właściwości, które dodajesz do typu elementu projektu. Jeśli chcesz dodać wiele właściwości do typu elementu projektu, można zdefiniować wszystkie właściwości w tej samej klasy lub w różnych klas.  
  
2.  W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> metody usługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementacji, uchwyt <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenia *projectItemType* parametru.  
  
3.  W procedurze obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> zdarzenia dodaje wystąpienie klasy właściwości do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> zbiór parametr argumenty zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dodać właściwość o nazwie **właściwość przykład** do elementu projektu odbiorcy zdarzeń.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understand-the-code"></a>Rozumienie kodu  
 Aby upewnić się, że to samo wystąpienie elementu `CustomProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> wystąpi zdarzenie, przykładowy kod dodaje właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość czas pierwszego elementu projektu, to zdarzenie występuje. Kod pobiera ten obiekt zawsze wtedy, gdy ponownego wystąpienia tego zdarzenia. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość do skojarzenia danych z elementów projektu, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Aby utrwalić zmiany wartości właściwości **ustaw** akcesora `ExampleProperty` zapisuje nowa wartość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiekt, który jest skojarzony właściwość. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości do utrwalenia danych za pomocą elementów projektu, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowe  
 Można zdefiniować jak właściwość niestandardową wygląda i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeń nazw do definicji właściwości. Następujące atrybuty są przydatne w wielu scenariuszach:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która pojawia się w **właściwości** okna.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okno po wybraniu właściwości.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Określa domyślną wartość właściwości.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowe konwersji między ciąg, który jest wyświetlany w **właściwości** okna, a wartość właściwości innych niż ciąg.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowy Edytor służące do modyfikowania właściwości.  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Te przykłady wymagają projekt biblioteki klas z odwołaniami do następujących zestawów:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia  
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Tworzenie rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Instrukcje: Dodawanie pozycji menu skrótów do rozszerzenia elementu projektu SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Rozszerzanie elementów projektu programu SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
