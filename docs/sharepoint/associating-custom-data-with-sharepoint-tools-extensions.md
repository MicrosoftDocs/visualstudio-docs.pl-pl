---
title: Kojarzenie danych niestandardowych z programem SharePoint rozszerzeń narzędzi | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112276"
---
# <a name="associate-custom-data-with-sharepoint-tools-extensions"></a>Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint
  Możesz dodać niestandardowe dane do niektórych obiektów w rozszerzenia narzędzi programu SharePoint. Jest to przydatne, gdy masz dane w jednej części Twojego rozszerzenia, który chcesz uzyskać dostęp później z innym kodem Twojego rozszerzenia. Zamiast wykonywania niestandardowych sposób przechowywania i dostępu do danych, można skojarzyć dane z obiektu w rozszerzeniu i następnie później pobrać dane z tego samego obiektu.

 Dodawanie niestandardowych danych do obiektów jest również przydatne, jeśli chcesz zachować dane, która jest odpowiednia dla określonego elementu w programie Visual Studio. Rozszerzenia narzędzi programu SharePoint są ładowane tylko w przypadku, gdy w programie Visual Studio, więc rozszerzenie może pracować kilka różnych elementów (takich jak projekty, elementy, projektu lub **Eksploratora serwera** węzłach) w dowolnym momencie. Jeśli masz niestandardowe dane, które ma zastosowanie tylko do określonego elementu, można dodać dane do obiektu, który reprezentuje dany element.

 Po dodaniu danych niestandardowych do obiektów w rozszerzenia narzędzi programu SharePoint, dane nie są zachowywane. Dane są dostępne tylko w czasie trwania obiektu. Po obiektu jest odzyskiwane przez wyrzucanie elementów bezużytecznych, dane zostaną utracone.

 W rozszerzeniach systemu projektu programu SharePoint można także zapisać dane ciągu, która utrzymuje się po rozszerzenia jest zwalniana. Aby uzyskać więcej informacji, zobacz [zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="objects-that-can-contain-custom-data"></a>Obiekty, które mogą zawierać dane niestandardowe
 Możesz dodać niestandardowe dane do dowolnego obiektu w modelu obiektów programu SharePoint narzędzia, która implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfejsu. Ten interfejs definiuje tylko jedną właściwość <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, który jest kolekcją obiektów danych niestandardowych. Następujące typy implementują <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:

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
 Aby dodać niestandardowe dane do obiektu w rozszerzenia narzędzi programu SharePoint, Pobierz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość obiektu, aby dodać dane do, a następnie użyj <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> metodę, aby dodać dane do obiektu.

 Aby pobrać dane niestandardowe z obiektu rozszerzenia narzędzi programu SharePoint, Pobierz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości tego obiektu i skorzystaj z jednej z następujących metod:

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Ta metoda zwraca **true** istnienia obiektu danych lub **false** Jeśli nie istnieje. Ta metoda służy do pobierania wystąpień typów wartości lub typów referencyjnych.

- <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Ta metoda zwraca dane obiektu, jeśli kończy pracę, lub **null** Jeśli nie istnieje. Tej metody można użyć tylko w celu pobrania wystąpienia typu referencyjnego.

  Poniższy przykład kodu Określa, czy obiekt danych jest już skojarzony z elementem projektu. Jeśli obiekt danych nie jest już skojarzona z elementem projektu, a następnie ten kod dodaje obiekt do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości elementu projektu. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [jak: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
  [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]

## <a name="see-also"></a>Zobacz także
- [Koncepcje programowania oraz funkcje dla rozszerzeń narzędzi SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Instrukcje: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Instrukcje: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
