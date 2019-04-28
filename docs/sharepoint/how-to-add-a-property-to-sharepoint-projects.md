---
title: 'Instrukcje: Dodawanie właściwości do projektów programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: a6f1ecd427b1c715649bc2118be5ab384a74c585
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967217"
---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>Instrukcje: Dodawanie właściwości do projektów SharePoint
  Można użyć rozszerzenia projektu, aby dodać właściwość do każdego projektu programu SharePoint. Właściwość pojawia się w **właściwości** okna, jeśli projekt jest wybrany w **Eksploratora rozwiązań**.

 W następujących krokach założono, że utworzono już rozszerzenia projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

### <a name="to-add-a-property-to-a-sharepoint-project"></a>Aby dodać właściwość do projektu programu SharePoint

1. Zdefiniuj klasę z właściwością publiczną, reprezentujący właściwość, którą chcesz dodać do projektów programu SharePoint. Jeśli chcesz dodać wiele właściwości, można zdefiniować wszystkie właściwości w tej samej klasy lub w różnych klas.

2. W <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metody usługi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji, uchwyt <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzenia *projectService* parametru.

3. W procedurze obsługi zdarzeń dla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> zdarzenia dodaje wystąpienie klasy właściwości do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> zbiór parametr argumenty zdarzenia.

## <a name="example"></a>Przykład
 Poniższy przykład kodu demonstruje sposób dodawania dwóch właściwości do projektów programu SharePoint. Jedna właściwość będzie się powtarzał swoje dane w pliku projektu użytkownika opcji ( *. csproj.user* pliku lub *. vbproj.user* pliku). Innych właściwości będzie się powtarzał swoje dane w pliku projektu (*.csproj* pliku lub *.vbproj* pliku).

 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)]
 [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]

### <a name="understand-the-code"></a>Rozumienie kodu
 Aby upewnić się, że to samo wystąpienie elementu `CustomProjectProperties` klasa jest używana zawsze <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> wystąpi zdarzenie, przykładowy kod dodaje właściwości obiektu do <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwości podczas pierwszego projektu to zdarzenie występuje. Kod pobiera ten obiekt zawsze wtedy, gdy ponownego wystąpienia tego zdarzenia. Aby uzyskać więcej informacji o korzystaniu z <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> właściwość do skojarzenia danych z projektami, zobacz [rozszerzeń narzędzi kojarzenie danych niestandardowych z programem SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

 Aby zachować zmiany wartości właściwości **ustaw** metod dostępu właściwości przy użyciu następujących interfejsów API:

- `CustomUserFileProperty` używa <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> właściwości, aby zapisać plik opcji użytkownika projektu jego wartość.

- `CustomProjectFileProperty` używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> metodę, aby zapisać jego wartość do pliku projektu.

  Aby uzyskać więcej informacji na temat utrwalanie danych w tych plikach, zobacz [zapisywać danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

### <a name="specify-the-behavior-of-custom-properties"></a>Określ zachowanie właściwości niestandardowe
 Można zdefiniować jak właściwość niestandardową wygląda i zachowuje się tak **właściwości** okna przez zastosowanie atrybutów z <xref:System.ComponentModel> przestrzeń nazw do definicji właściwości. Następujące atrybuty są przydatne w wielu scenariuszach:

- <xref:System.ComponentModel.DisplayNameAttribute>: Określa nazwę właściwości, która pojawia się w **właściwości** okna.

- <xref:System.ComponentModel.DescriptionAttribute>: Określa ciąg opisu, który pojawia się w dolnej części **właściwości** okno po wybraniu właściwości.

- <xref:System.ComponentModel.DefaultValueAttribute>: Określa domyślną wartość właściwości.

- <xref:System.ComponentModel.TypeConverterAttribute>: Określa niestandardowe konwersji między ciąg, który jest wyświetlany w **właściwości** okna, a wartość właściwości innych niż ciąg.

- <xref:System.ComponentModel.EditorAttribute>: Określa niestandardowy Edytor służące do modyfikowania właściwości.

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład wymaga odwołania do następujących zestawów:

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.Shell

- Microsoft.VisualStudio.Shell.Interop

- Microsoft.VisualStudio.Shell.Interop.8.0

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Wdrażanie rozszerzenia
 Aby wdrożyć rozszerzenie, należy utworzyć [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenie (VSIX), pakiet dla zestawu i innych plików, które chcesz dystrybuować z rozszerzeniem. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Instrukcje: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Instrukcje: Dodawanie pozycji menu skrótów do projektów SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
