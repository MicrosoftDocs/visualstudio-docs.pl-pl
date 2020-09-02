---
title: Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9a2c1869791b250fb90c6a634f057797f3c57a62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62987974"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint
  Niestandardowe dane można dodać do określonych obiektów w rozszerzeniach narzędzi programu SharePoint. Jest to przydatne, gdy masz dane w jednej części rozszerzenia, do którego chcesz uzyskać dostęp później z innego kodu w rozszerzeniu. Zamiast implementować niestandardowy sposób przechowywania danych i uzyskiwania do nich dostępu, możesz skojarzyć dane z obiektem w rozszerzeniu, a następnie pobrać dane z tego samego obiektu później.

 Dodawanie niestandardowych danych do obiektów jest również przydatne, gdy chcesz zachować dane, które są istotne dla określonego elementu w programie Visual Studio. Rozszerzenia narzędzi programu SharePoint są ładowane tylko raz w programie Visual Studio, dzięki czemu rozszerzenie może działać z kilkoma różnymi elementami (takimi jak projekty, elementy projektu lub **Eksplorator serwera** węzły) w dowolnym momencie. Jeśli masz dane niestandardowe, które mają zastosowanie tylko do określonego elementu, możesz dodać dane do obiektu, który reprezentuje ten element.

 Po dodaniu niestandardowych danych do obiektów w rozszerzeniach narzędzi programu SharePoint dane nie są zachowywane. Dane są dostępne tylko podczas cykl życia obiektu. Po odzyskiwaniu obiektu przez wyrzucanie elementów bezużytecznych dane zostaną utracone.

 W rozszerzeniach systemu projektu SharePoint można również zapisać dane ciągów, które są utrwalane po rozładowaniu rozszerzenia. Aby uzyskać więcej informacji, zobacz [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Obiekty, które mogą zawierać dane niestandardowe
 Możesz dodać niestandardowe dane do dowolnego obiektu w modelu obiektów narzędzi SharePoint, który implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfejs. Ten interfejs definiuje tylko jedną właściwość, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> która jest kolekcją niestandardowych obiektów danych. Następujące typy implementują <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> :

- <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>

- <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>

- <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>

- <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>

- <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>

## <a name="add-and-retrieve-custom-data"></a>Dodawanie i pobieranie danych niestandardowych
 Aby dodać dane niestandardowe do obiektu w rozszerzeniu narzędzi programu SharePoint, Pobierz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość obiektu, do którego chcesz dodać dane, a następnie użyj <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metody, aby dodać dane do obiektu.

 Aby pobrać dane niestandardowe z obiektu w rozszerzeniu narzędzi programu SharePoint, Pobierz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość obiektu, a następnie użyj jednej z następujących metod:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Ta metoda zwraca **wartość true** , jeśli obiekt danych istnieje lub ma **wartość FAŁSZ** , jeśli nie istnieje. Za pomocą tej metody można pobrać wystąpienia typów wartości lub typów referencyjnych.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Ta metoda zwraca obiekt danych, jeśli zostanie zakończony, lub **wartość null** , jeśli nie istnieje. Tej metody można użyć tylko do pobierania wystąpień typów referencyjnych.

  Poniższy przykład kodu określa, czy określony obiekt danych jest już skojarzony z elementem projektu. Jeśli obiekt danych nie jest już skojarzony z elementem projektu, wówczas kod dodaje obiekt do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości elementu projektu. Aby zobaczyć ten przykład w kontekście większego przykładu, zobacz [jak: Dodawanie właściwości do niestandardowego typu elementu projektu programu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>Zobacz też
- [Koncepcje programowania i funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Przewodnik: rozszerzanie Eksplorator serwera do wyświetlania części sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Instrukcje: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
