---
title: Szablony elementów/szablony projektów dla elementów projektu programu SharePoint
description: Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint. Tworzenie kreatorów szablonów elementów i szablonów projektu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 59710eb4651f363d669dc27b6190f8d224d9917f
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850640"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint

Podczas definiowania niestandardowego typu elementu projektu programu SharePoint można go skojarzyć z szablonem elementu lub szablonem projektu. To skojarzenie umożliwia innym deweloperom używanie elementu projektu w programie Visual Studio. Możesz również utworzyć kreatora dla szablonu.

Na przykład program Visual Studio nie zawiera szablonu projektu ani szablonu elementu do dodania pola do witryny programu SharePoint. Można zdefiniować typ elementu projektu programu SharePoint, który reprezentuje pole, a następnie skonstruować szablon elementu, który może być używany przez innych deweloperów do dodawania elementu pola do projektu programu SharePoint. Można też skonstruować szablon projektu, aby deweloperzy mogli utworzyć nowy projekt programu SharePoint, który ma element pola. W obu przypadkach można także udostępnić kreatora, który jest wyświetlany, gdy deweloperzy korzystają z szablonu. Ten kreator może zbierać informacje od deweloperów w celu skonfigurowania nowego elementu lub projektu.

Szablony elementów i szablony projektów to pliki *. zip* , które zawierają pliki, które są używane przez program Visual Studio do tworzenia projektu lub elementu projektu. Aby uzyskać więcej informacji na temat podstawowych szablonów elementów i szablonów projektu, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Tworzenie szablonów elementów
 Gdy tworzysz szablon elementu dla elementu projektu programu SharePoint, istnieje kilka plików, które są zawsze wymagane i opcjonalne pliki, które mogą być używane przez niektóre typy elementów projektu. Aby zapoznać się z przewodnikiem, który pokazuje, jak zdefiniować typ elementu projektu programu SharePoint i utworzyć dla niego szablon elementu, zobacz [Przewodnik: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Poniższa tabela zawiera listę plików wymaganych do utworzenia szablonu elementu dla elementu projektu programu SharePoint.

|Wymagany plik|Opis|
|-------------------|-----------------|
|Plik *. spdata*|Ten plik XML określa zawartość i domyślne zachowanie elementu projektu. Ten plik musi być uwzględniony w szablonie elementu. Aby uzyskać więcej informacji o zawartości plików *. spdata* , zobacz [Dokumentacja schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|Plik *. vstemplate* .|Ten plik zawiera program Visual Studio z informacjami wymaganymi do wyświetlenia szablonu w oknie dialogowym **Dodaj nowy element** oraz do tworzenia elementu projektu na podstawie szablonu. Ten plik musi być uwzględniony w szablonie elementu. Aby uzyskać więcej informacji, zobacz [pliki metadanych szablonu programu Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Zestaw rozszerzeń programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejs.|Ten zestaw definiuje zachowanie w czasie wykonywania elementu projektu. Ten zestaw musi być zawarty w pakiecie VSIX z szablonem elementu. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) i [Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 W poniższej tabeli wymieniono niektóre z najpopularniejszych plików opcjonalnych, które można uwzględnić w szablonie elementu. Niektóre typy elementów projektu mogą wymagać innych plików, które nie są wymienione w tym miejscu.

| Plik opcjonalny | Opis |
|----------------------| - |
| *Elements.xml* | Plik *elementu funkcji* . Ten plik definiuje interfejs użytkownika i zachowanie dostosowania utworzonego przez element projektu. Każdy typ dostosowania, taki jak wystąpienia list, typy zawartości lub akcje niestandardowe, ma inny schemat, który definiuje zawartość tego pliku. Aby uzyskać więcej informacji, zobacz [Budowanie bloków: funkcje](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) i [schematy funkcji](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)). |
| *Schema.xml* | Plik schematu dla definicji listy. Aby uzyskać więcej informacji, zobacz [Building Block: lists and Document](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)) librarys i [Schema.xml](/previous-versions/office/developer/sharepoint-2010/ms459356(v=office.14)). |
| *. WebPart* | Plik *definicji części sieci Web* . Ten plik zawiera ustawienia właściwości składnika Web Part. Aby uzyskać więcej informacji, zobacz [Building Block: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)). |
| *. ascx* | Plik UserControl ASP.NET. Ten plik definiuje interfejs użytkownika wizualnego składnika Web Part. |
| *. aspx* | Plik stronicowania ASP.NET. Ten plik zawiera znaczniki XML definiujące stronę aplikacji. |
| pliki *. cs* lub *. vb* | Te pliki kodu definiują zachowanie dostosowań programu SharePoint z modelem programowania dostępnym z poziomu języka Visual C# lub kodu Visual Basic, takich jak strony aplikacji, składniki Web Part i przepływy pracy. |

## <a name="create-project-templates"></a>Tworzenie szablonów projektu
 Podczas tworzenia szablonu projektu programu SharePoint istnieje kilka plików, które są zawsze wymagane i opcjonalne pliki, które mogą być używane przez niektóre typy projektów. Zazwyczaj projekty programu SharePoint obejmują co najmniej jeden element projektu programu SharePoint. Nie jest to jednak wymagane. Można na przykład zdefiniować szablon projektu programu SharePoint, który ma być używany tylko do wdrażania rozwiązań programu SharePoint utworzonych w innych projektach.

 Aby zapoznać się z przewodnikiem, który pokazuje, jak zdefiniować typ elementu projektu programu SharePoint i utworzyć dla niego szablon projektu, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Poniższa tabela zawiera listę plików, które muszą być dołączone do szablonu projektu programu SharePoint.

|Wymagany plik|Opis|
|-------------------|-----------------|
|Plik *. vstemplate*|Ten plik udostępnia program Visual Studio z informacjami wymaganymi do wyświetlania szablonu w oknie dialogowym **Nowy projekt** i tworzenia projektu na podstawie szablonu. Aby uzyskać więcej informacji, zobacz [pliki metadanych szablonu programu Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Plik *. csproj* lub *. vbproj*|Jest to plik projektu. Definiuje zawartość i ustawienia konfiguracji projektu.|
|*Package. Package*|Ten plik definiuje pakiet wdrożeniowy dla projektu. Gdy korzystasz z projektanta pakietów do dostosowywania pakietu rozwiązań dla projektu, program Visual Studio przechowuje dane dotyczące pakietu rozwiązania w tym pliku.<br /><br /> Podczas tworzenia niestandardowego szablonu projektu programu SharePoint zaleca się dołączenie tylko minimalnej wymaganej zawartości w pliku *Package. Package* oraz skonfigurowanie pakietu rozwiązania przy użyciu interfejsów API w <xref:Microsoft.VisualStudio.SharePoint.Packages> przestrzeni nazw w rozszerzeniu skojarzonym z szablonem projektu. W takim przypadku szablon projektu jest chroniony przed przyszłymi zmianami w strukturze pliku *Package. Package* . Aby zapoznać się z przykładem, który pokazuje, jak utworzyć plik *Package. Package* o minimalnej wymaganej zawartości, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Jeśli chcesz zmodyfikować plik *Package. Package* bezpośrednio, możesz sprawdzić zawartość przy użyciu schematu w lokalizacji *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\PackageModelSchema.xsd*.|
|*Package.Template.xml*|Ten plik zawiera podstawowe informacje na temat pliku manifestu rozwiązania (*manifest.xml*) dla pakietu rozwiązania programu SharePoint (*wsp*) wygenerowanego na podstawie projektu. Możesz dodać zawartość do tego pliku, jeśli chcesz określić zachowanie, które nie jest przeznaczone do zmiany przez użytkowników typu projektu. Aby uzyskać więcej informacji, zobacz [Kompilowanie bloków: rozwiązania](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)) i [schemat rozwiązania](/sharepoint/dev/schema/solution-schema).<br /><br /> Podczas kompilowania pakietu rozwiązania z projektu program Visual Studio scala zawartość *pakietu Package. Package* i plików *Package.Template.xml* w pliku manifestu rozwiązania. Aby uzyskać więcej informacji na temat tworzenia pakietów rozwiązań, zobacz [jak: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Poniższa tabela zawiera listę opcjonalnych plików, które mogą być zawarte w szablonie projektu.

|Plik opcjonalny|Opis|
|-------------------|-----------------|
|SharePoint — Elementy projektu|Można uwzględnić jeden lub więcej plików. spdata, które definiują typy elementów projektu programu SharePoint. Każdy plik *. spdata* musi mieć zgodną <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementację w zestawie rozszerzeń, który znajduje się w pakiecie VSIX przy użyciu szablonu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów](#create-item-templates).<br /><br /> Zazwyczaj projekty programu SharePoint obejmują co najmniej jeden element projektu programu SharePoint. Nie jest to jednak wymagane.|
|*\<featureName>. funkcja*|Ten plik definiuje funkcję programu SharePoint, która jest używana do grupowania kilku elementów projektu do wdrożenia. Gdy korzystasz z projektanta funkcji, aby dostosować funkcję w projekcie, program Visual Studio przechowuje dane dotyczące funkcji w tym pliku. Jeśli chcesz grupować elementy projektu w różne funkcje, możesz dołączyć wiele plików *funkcji* .<br /><br /> Podczas tworzenia niestandardowego szablonu projektu programu SharePoint zaleca się dołączenie tylko minimalnej wymaganej zawartości w każdym pliku *funkcji* oraz skonfigurowanie funkcji przy użyciu interfejsów API w <xref:Microsoft.VisualStudio.SharePoint.Features> przestrzeni nazw w rozszerzeniu skojarzonym z szablonem projektu. W takim przypadku szablon projektu jest chroniony przed przyszłymi zmianami w strukturze pliku *. feature* . Aby zapoznać się z przykładem, który pokazuje, jak utworzyć plik *. feature* o minimalnej wymaganej zawartości, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Jeśli chcesz zmodyfikować plik *funkcji* bezpośrednio, możesz sprawdzić zawartość przy użyciu schematu w *% Program Files (x86)% \ Microsoft Visual Studio 11.0 \ Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName>.Template.xml*|Ten plik zawiera podstawowe informacje dotyczące pliku manifestu funkcji (*Feature.xml*) dla każdej funkcji wygenerowanej na podstawie projektu. Możesz dodać zawartość do tego pliku, jeśli chcesz określić zachowanie, które nie jest przeznaczone do zmiany przez użytkowników typu projektu. Aby uzyskać więcej informacji, zobacz [Building Block: Features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)) and [Feature.xml](/sharepoint/dev/schema/feature-xml-files) Files.<br /><br /> Podczas kompilowania pakietu rozwiązania z projektu program Visual Studio scala zawartość poszczególnych par plików *\<featureName> funkcji* i plików *\<featureName>.Template.xml* w pliku manifestu funkcji. Aby uzyskać więcej informacji na temat tworzenia pakietów rozwiązań, zobacz [jak: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Tworzenie kreatorów szablonów elementów i szablonów projektu
 Po zdefiniowaniu typu elementu projektu SharePoint i skojarzeniu go z szablonem elementu lub projektu można także utworzyć kreatora. Kreator jest wyświetlany, gdy deweloper używa szablonu elementu do dodawania elementu projektu programu SharePoint do projektu, lub gdy deweloper używa szablonu projektu do tworzenia nowego projektu, który zawiera element projektu programu SharePoint. Za pomocą kreatora można zbierać informacje od deweloperów i inicjować nowy element projektu programu SharePoint.

 Aby zapoznać się z przewodnikami demonstrującymi tworzenie kreatorów szablonów elementów i szablonów projektów, zobacz [Przewodnik: Tworzenie elementu projektu akcji niestandardowej z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) i [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Zobacz także

- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
