---
title: Zapisywanie danych w rozszerzeniach systemu projektu SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 52b04490a646c7ced27d4a2d7f2344e27cbbae8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827248"
---
# <a name="save-data-in-extensions-of-the-sharepoint-project-system"></a>Zapisywanie danych w rozszerzeniach systemu projektu SharePoint
  Podczas rozszerzania systemu projektu programu SharePoint, możesz zapisać dane ciągu, która utrzymuje się po zamknięciu projektu programu SharePoint. Dane są zwykle skojarzone z elementem określonego projektu lub z samym projekcie.

 Jeśli masz dane, które nie wymagają, aby utrwalić, można dodać dane do dowolnego obiektu w modelu obiektów programu SharePoint narzędzia, która implementuje <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interfejsu. Aby uzyskać więcej informacji, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="save-data-that-is-associated-with-a-project-item"></a>Zapisywanie danych, który jest skojarzony z elementem projektu
 W przypadku danych, który jest skojarzony z określonego elementu projektu programu SharePoint, takich jak wartość właściwości, które dodasz do elementu projektu można zapisać danych do *spdata* pliku dla elementu projektu. Aby to zrobić, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> obiektu. Danymi dodawanymi do tej właściwości jest zapisywany w **extensiondata —** element *spdata* pliku dla elementu projektu. Aby uzyskać więcej informacji, zobacz [extensiondata — Element](../sharepoint/extensiondata-element.md).

 Poniższy przykład kodu demonstruje sposób używania <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> właściwości, aby zapisać wartość właściwości ciągu, który jest zdefiniowany w programie SharePoint projektu elementu Typ niestandardowy. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [jak: Dodawanie właściwości do niestandardowego typu elementu projektu SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]

## <a name="save-data-that-is-associated-with-a-project"></a>Zapisywanie danych, który jest skojarzony z projektem
 W przypadku danych na poziomie projektu, takich jak wartość właściwości, które dodajesz do projektów programu SharePoint, możesz zapisać dane do pliku projektu ( *.csproj* pliku lub *.vbproj* plików) lub opcji użytkownika projektu plik ( *. csproj.user* pliku lub *. vbproj.user* pliku). Plik, który chcesz zapisać dane w zależy od tego, jaki ma dane do użycia:

- Jeśli chcesz, aby dane, które mają być dostępne dla wszystkich deweloperów, którzy Otwórz projekt programu SharePoint, należy zapisać danych do pliku projektu. Ten plik jest zawsze ewidencjonowane bazy danych kontroli źródła, więc dane w tym pliku jest dostępna dla innych deweloperów, którzy zapoznaj się z projektu.

- Jeśli chcesz, aby dane, które mają być dostępne tylko dla bieżącego Deweloper, który został otwarty w programie Visual Studio projekt programu SharePoint, należy zapisać danych do pliku projektu, opcja użytkownika. Ten plik jest zwykle niezaewidencjonowane do bazy danych kontroli źródła, więc dane w tym pliku nie jest dostępna dla innych deweloperów, którzy wyewidencjonować projekt.

### <a name="save-data-to-the-project-file"></a>Zapisywanie danych w pliku projektu
 Aby zapisać dane w pliku projektu, należy przekonwertować <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> obiektu, a następnie użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metody. Poniższy przykład kodu demonstruje sposób używania tej metody można zapisać wartości właściwości projektu do pliku projektu. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [jak: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]

 Aby uzyskać więcej informacji na temat konwertowania <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiekty do innych typów w modelu obiektu automatyzacji programu Visual Studio lub model obiektów integracji, zobacz [konwersji między typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

### <a name="save-data-to-the-project-user-option-file"></a>Zapisywanie danych do projektu plik opcji użytkownika
 Aby zapisać dane w pliku projektu użytkownika opcji, należy użyć <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> właściwość <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> obiektu. Poniższy przykład kodu pokazuje, jak używać tej właściwości można zapisać wartości właściwości projektu do projektu plik opcji użytkownika. Aby wyświetlić ten przykład w kontekście większego przykładu, zobacz [jak: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
