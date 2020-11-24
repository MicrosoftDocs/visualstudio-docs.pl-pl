---
title: Zapisywanie danych w rozszerzeniach systemu projektu SharePoint | Microsoft Docs
titleSuffix: ''
description: Dowiedz się, jak zapisać dane ciągów, które są utrwalane po zamknięciu projektu programu SharePoint, który zawiera rozszerzenie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1e3c05b9ad570febcfc28fec367a8d180dd2b222
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440652"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Zapisywanie danych w rozszerzeniach systemu projektu SharePoint
  Rozszerzając system projektu programu SharePoint, można zapisać dane ciągów, które są utrwalane po zamknięciu projektu programu SharePoint. Dane są zwykle skojarzone z konkretnym elementem projektu lub z samym projektem.

 Jeśli masz dane, które nie muszą być utrwalane, możesz dodać dane do dowolnego obiektu w modelu obiektów narzędzi programu SharePoint, który implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfejs. Aby uzyskać więcej informacji, zobacz [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Zapisz dane, które są skojarzone z elementem projektu
 Gdy masz dane skojarzone z konkretnym elementem projektu programu SharePoint, takie jak wartość właściwości dodawanej do elementu projektu, możesz zapisać dane w pliku *. spdata* dla elementu projektu. W tym celu należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu. Dane dodawane do tej właściwości są zapisywane w elemencie **ExtensionData —** w pliku *spdata* dla elementu projektu. Aby uzyskać więcej informacji, zobacz [ExtensionData — element](../sharepoint/extensiondata-element.md).

 Poniższy przykład kodu demonstruje, jak użyć właściwości, <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Aby zapisać wartość właściwości ciągu, która jest zdefiniowana w niestandardowym typie elementu projektu programu SharePoint. Aby zobaczyć ten przykład w kontekście większego przykładu, zobacz [jak: Dodawanie właściwości do niestandardowego typu elementu projektu programu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Zapisz dane, które są skojarzone z projektem
 Gdy masz dane na poziomie projektu, takie jak wartość właściwości dodawanej do projektów programu SharePoint, możesz zapisać dane w pliku projektu (plik *. csproj* lub plik *. vbproj* ) lub pliku opcji użytkownika projektu (plik *. csproj. User* lub *. vbproj. User* ). Plik, w którym można zapisywać dane, zależy od tego, w jaki sposób dane mają być używane:

- Jeśli chcesz, aby dane były dostępne dla wszystkich deweloperów, którzy otworzą projekt programu SharePoint, Zapisz dane w pliku projektu. Ten plik jest zawsze zaewidencjonowany do baz danych kontroli źródła, więc dane w tym pliku są dostępne dla innych deweloperów, którzy ewidencjonują projekt.

- Jeśli chcesz, aby dane były dostępne tylko dla bieżącego dewelopera, który ma otwarty projekt programu SharePoint w programie Visual Studio, Zapisz dane w pliku opcji użytkownika projektu. Ten plik nie jest zwykle zaewidencjonowany do baz danych kontroli źródła, więc dane w tym pliku nie są dostępne dla innych deweloperów, którzy ewidencjonują projekt.

### <a name="save-data-to-the-project-file"></a>Zapisz dane w pliku projektu
 Aby zapisać dane w pliku projektu, przekonwertuj <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekt na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> obiekt, a następnie użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody. Poniższy przykład kodu ilustruje sposób użycia tej metody w celu zapisania wartości właściwości projektu w pliku projektu. Aby zobaczyć ten przykład w kontekście większego przykładu, zobacz [How to: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Aby uzyskać więcej informacji na temat konwertowania <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektów na inne typy w modelu obiektów automatyzacji programu Visual Studio lub modelu obiektów integracji, zobacz [konwertowanie między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Zapisz dane w pliku opcji użytkownika projektu
 Aby zapisać dane w pliku opcji użytkownika projektu, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> właściwości <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu. Poniższy przykład kodu demonstruje sposób użycia tej właściwości, aby zapisać wartość właściwości projektu do pliku opcji użytkownika projektu. Aby zobaczyć ten przykład w kontekście większego przykładu, zobacz [How to: Dodawanie właściwości do projektów programu SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Zobacz także
- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Konwersja między typami systemu projektu SharePoint a innymi typami projektów programu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
