---
title: Element elementy projektu szablony szablony/projektu programu SharePoint
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
ms.openlocfilehash: 8f41783689e572ca823788e1a8dbcf772f07e924
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177613"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint

Podczas definiowania programu SharePoint projektu elementu Typ niestandardowy, należy ją skojarzyć z szablonem elementu lub szablonu projektu. To skojarzenie umożliwia innym deweloperom używanie elementu projektu w programie Visual Studio. Można również utworzyć Kreatora szablonu.

Na przykład programu Visual Studio nie ma szablonu projektu lub szablon elementu Dodawanie pola do witryny programu SharePoint. Można zdefiniować typ elementu projektu SharePoint, który reprezentuje pole i następnie utworzyć szablon elementu, używanego przez innych programistów można dodać elementu pola do projektu programu SharePoint. Alternatywnie można skonstruować szablon projektu, dzięki czemu deweloperzy mogą tworzyć nowy projekt programu SharePoint, który ma element pola. W obu przypadkach można również dołączyć kreatora, który jest wyświetlany, gdy deweloperzy używać szablonu. Ten kreator może zbierać informacje, od deweloperów, aby skonfigurować nowy element lub projektu.

Szablony elementów i szablonów projektu są *zip* pliki, które zawierają pliki, które są używane przez program Visual Studio do tworzenia projektu lub elementu projektu. Aby uzyskać więcej informacji na temat podstawowe informacje dotyczące szablonów elementów i szablonów projektu, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Tworzenie szablonów elementów
 Podczas tworzenia szablonu elementu dla elementu projektu programu SharePoint, istnieją pewne pliki, które zawsze są wymagane i opcjonalne pliki, które mogą być używane przez niektóre rodzaje elementów projektu. Aby wskazówki, który demonstruje, jak zdefiniować typ elementu projektu programu SharePoint i Utwórz szablon elementu dla niego, zobacz [wskazówki: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Poniższa tabela zawiera listę wymaganych plików, aby utworzyć szablon elementu dla elementu projektu programu SharePoint.

|Wymaganego pliku|Opis|
|-------------------|-----------------|
|*Spdata* pliku|Ten plik XML określa zawartości i domyślne zachowanie elementu projektu. Tego pliku muszą być zawarte w szablonie elementu. Aby uzyskać więcej informacji na temat zawartości *spdata* plików, zobacz [odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).|
|A *.vstemplate* pliku.|Ten plik zawiera program Visual Studio z informacjami wymaganymi do wyświetlić szablon w **Dodaj nowy element** okno dialogowe i utworzyć elementu projektu z szablonu. Tego pliku muszą być zawarte w szablonie elementu. Aby uzyskać więcej informacji, zobacz [pliki metadanych szablonu w usłudze Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Zestaw rozszerzeń programu Visual Studio, który implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu.|Ten zestaw definiuje zachowanie w czasie wykonywania elementu projektu. Ten zestaw muszą być zawarte w pakiecie VSIX z szablonem elementu. Aby uzyskać więcej informacji, zobacz [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md) i [wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 W poniższej tabeli wymieniono niektóre z najczęściej używanych plikach opcjonalne, które mogą być zawarte w szablonie elementu. Niektóre typy elementów projektu może wymagać innych plików, nie na tej liście.

| Opcjonalny plik | Opis |
|----------------------| - |
| *Elements.xml* | A *element funkcji* pliku. Ten plik definiuje interfejs użytkownika i zachowanie dostosowania utworzone przez element projektu. Każdy typ dostosowania, takie jak wystąpienia listy, typy zawartości lub akcje niestandardowe ma inny schemat, który definiuje zawartość tego pliku. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Funkcje](http://go.microsoft.com/fwlink/?LinkId=169183) i [funkcji Schematy](http://go.microsoft.com/fwlink/?LinkId=169192). |
| *Schema.xml* | Plik schematu definicji listy. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: List i bibliotek dokumentów](http://go.microsoft.com/fwlink/?LinkId=177792) i [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793). |
| *.webpart* | A *definicji składnika Web Part* pliku. Ten plik zawiera ustawienia właściwości składnika Web Part. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Składniki Web Part](http://go.microsoft.com/fwlink/?LinkId=177791). |
| *.ascx* | An ASP.NET UserControl file. Ten plik definiuje interfejs użytkownika programu Visual Web Part. |
| *.aspx* | Plik strony ASP.NET. Ten plik zawiera znacznik XML, który definiuje strony aplikacji. |
| *.cs* lub *.vb* plików | Te pliki kodu Definiowanie zachowania dostosowania programu SharePoint, które mają model programowania, który jest możliwy z wizualizacji C# lub kod języka Visual Basic, takich jak strony aplikacji, składników Web Part i przepływów pracy. |

## <a name="create-project-templates"></a>Tworzenie szablonów projektu
 Podczas tworzenia szablonu projektu programu SharePoint, istnieją pewne pliki, które są zawsze plików wymaganych i opcjonalnych, które mogą być używane przez niektóre rodzaje projektów. Zazwyczaj projektów programu SharePoint może zawierać co najmniej jeden element projektu programu SharePoint. Jednak nie jest to wymagane. Na przykład można zdefiniować szablon projektu programu SharePoint, która ma być używany tylko do wdrażania rozwiązań programu SharePoint, utworzone w innych projektach.

 Aby uzyskać przewodnik pokazuje, jak zdefiniować typ elementu projektu programu SharePoint i Utwórz szablon projektu dla niego, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Poniższa tabela zawiera listę plików, które muszą być zawarte w szablonie projektu programu SharePoint.

|Wymaganego pliku|Opis|
|-------------------|-----------------|
|A *.vstemplate* pliku|Ten plik zawiera program Visual Studio z informacjami wymaganymi do wyświetlić szablon w **nowy projekt** okno dialogowe i utworzyć projekt z szablonu. Aby uzyskać więcej informacji, zobacz [pliki metadanych szablonu w usłudze Visual Studio](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|A *.csproj* lub *.vbproj* pliku|To jest plik projektu. Definiuje zawartość i ustawienia konfiguracji projektu.|
|*Package.package*|Ten plik definiuje pakietu wdrożeniowego dla projektu. Gdy Dostosowywanie pakietu rozwiązania dla Twojego projektu za pomocą projektanta pakietu Visual Studio przechowuje dane dotyczące pakietu rozwiązań w tym pliku.<br /><br /> Podczas tworzenia niestandardowego szablonu projektu programu SharePoint, zaleca się dołączyć tylko minimalną wymaganą zawartość w *Package.package* plików i konfigurowanie pakietu rozwiązania przy użyciu interfejsów API w <xref:Microsoft.VisualStudio.SharePoint.Packages> przestrzeń nazw w rozszerzeniu, który jest skojarzony z szablonem projektu. Jeśli to zrobisz, szablon projektu jest zabezpieczony przed przyszłe zmiany w strukturze *Package.package* pliku. Aby uzyskać przykład, który demonstruje, jak utworzyć *Package.package* zawartość pliku z minimalnym wymaganiem, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Jeśli chcesz zmodyfikować *Package.package* plików bezpośrednio, możesz sprawdzić zawartość przy użyciu schematu w *% Program Files (11.0\Xml\Schemas\PackageModelSchema.xsd programu Visual Studio x86)%\Microsoft* .|
|*Package.Template.xml*|Ten plik stanowi podstawę dla plik manifestu rozwiązania (*manifest.xml*) dla pakietu rozwiązania programu SharePoint (*.wsp*), jest generowany na podstawie projektu. Jeśli chcesz określić niektóre zachowania, które nie mają być zmieniane przez użytkowników tego typu projektu, możesz dodać zawartość do tego pliku. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Rozwiązania](http://go.microsoft.com/fwlink/?LinkId=169186) i [schematu rozwiązania](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Podczas tworzenia pakietu rozwiązań z projektu programu Visual Studio Scala zawartość *Package.package* i *Package.Template.xml* plik manifestu plików do rozwiązania. Aby uzyskać więcej informacji o tworzeniu pakietów rozwiązania, zobacz [jak: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Poniższa lista zawiera pliki opcjonalne, które mogły zostać uwzględnione w szablonie projektu.

|Opcjonalny plik|Opis|
|-------------------|-----------------|
|SharePoint — Elementy projektu|Może zawierać jeden lub więcej .spdata — pliki, które określają typy elementów projektu programu SharePoint. Każdy *spdata* plik musi mieć zgodną <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementacji zestawu rozszerzeń, który znajduje się w pakiecie VSIX przy użyciu szablonu projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów](#create-item-templates).<br /><br /> Zazwyczaj projektów programu SharePoint może zawierać co najmniej jeden element projektu programu SharePoint. Jednak nie jest to wymagane.|
|*\<featureName>.feature*|Ten plik definiuje funkcję programu SharePoint, która służy do grupowania kilka elementów projektu dla wdrożenia. Gdy dostosowywanie funkcji w projekcie za pomocą projektanta funkcji programu Visual Studio przechowuje dane dotyczące tej funkcji, w tym pliku. Jeśli chcesz grupować elementy projektu w różnych funkcji, możesz uwzględnić wiele *.feature* plików.<br /><br /> Podczas tworzenia niestandardowego szablonu projektu programu SharePoint, zaleca się zawierały minimalnej wymaganej zawartości w każdym *.feature* plików i konfigurowanie funkcji przy użyciu interfejsów API w <xref:Microsoft.VisualStudio.SharePoint.Features> przestrzeni nazw w rozszerzenie, który jest skojarzony z szablonem projektu. Jeśli to zrobisz, szablon projektu jest zabezpieczony przed przyszłe zmiany w strukturze *.feature* pliku. Aby uzyskać przykład, który demonstruje, jak utworzyć *.feature* zawartość pliku z minimalnym wymaganiem, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Jeśli chcesz zmodyfikować *.feature* plików bezpośrednio, możesz sprawdzić zawartość przy użyciu schematu w *% Program Files (11.0\Xml\Schemas\FeatureModelSchema.xsd programu Visual Studio x86)%\Microsoft*.|
|*\<featureName>.Template.xml*|Ten plik stanowi podstawę dla pliku manifestu funkcji (*Feature.xml*) dla każdej funkcji, który jest generowany na podstawie projektu. Jeśli chcesz określić niektóre zachowania, które nie mają być zmieniane przez użytkowników tego typu projektu, możesz dodać zawartość do tego pliku. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Funkcje](http://go.microsoft.com/fwlink/?LinkId=169183) i [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) plików.<br /><br /> Podczas tworzenia pakietu rozwiązań z projektu programu Visual Studio Scala zawartość każdej pary  *\<featureName > .feature* pliku i  *\<featureName >. Template.XML* plik manifestu plików do funkcji. Aby uzyskać więcej informacji o tworzeniu pakietów rozwiązania, zobacz [jak: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Tworzenie kreatorów szablonów elementów i szablonów projektu
 Po zdefiniowaniu typu elementu projektu programu SharePoint i skojarzyć go z szablonem projektu lub elementu, można również utworzyć kreatora. Kreator wyświetla, gdy deweloper za pomocą szablonu elementu Dodawanie elementu projektu programu SharePoint do projektu lub gdy deweloper za pomocą szablonu projektu Utwórz nowy projekt, który zawiera element projektu programu SharePoint. Kreator może służyć do zbierania informacji od deweloperów i zainicjować nowy element projektu programu SharePoint.

 Aby uzyskać wskazówki dotyczące pokazują, jak tworzenie kreatorów szablonów elementów i szablonów projektu, zobacz [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) i [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Zobacz także

- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
