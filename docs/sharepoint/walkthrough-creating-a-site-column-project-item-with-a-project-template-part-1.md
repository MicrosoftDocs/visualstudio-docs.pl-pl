---
title: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 60e4f4e035b381b8bfda8e14ee705471b0fad2b8
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177550"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1
  Projekty programu SharePoint są kontenerami dla jednego lub więcej elementów projektu programu SharePoint. System projektu programu SharePoint w programie Visual Studio można rozszerzyć przez utworzenie własnych typów elementów projektu programu SharePoint i kojarzenie ich z szablonem projektu. W tym przewodniku określi typ elementu projektu programu do tworzenia kolumny witryny, a następnie zostanie utworzony szablon projektu, który może służyć do tworzenia nowego projektu, który zawiera elementu projektu kolumn witryny.

 W tym instruktażu pokazano następujące zagadnienia:

- Tworzenie rozszerzenia programu Visual Studio, który definiuje nowy typ elementu projektu programu SharePoint dla kolumny witryny. Typ elementu projektu zawiera proste właściwości niestandardowej, która pojawia się w **właściwości** okna.

- Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] szablon projektu służący do elementu projektu.

- Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) do wdrożenia szablonu projektu i zestawu rozszerzeń.

- Debugowanie i testowanie elementu projektu.

  Jest to przewodnik autonomicznej. Po ukończeniu tego przewodnika element projektu można zwiększyć przez dodanie kreatora do szablonu projektu. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Aby szereg przykładowych przepływów pracy, zobacz [przepływu pracy SharePoint — przykłady](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Wymagania wstępne
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows, SharePoint i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących koncepcji jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:

- Kolumny witryny w programie SharePoint. Aby uzyskać więcej informacji, zobacz [kolumn](http://go.microsoft.com/fwlink/?LinkId=183547).

- Szablony projektów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [tworzenie projektów i szablonów elementów](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, musisz utworzyć trzy projekty:

- A VSIX project. Ten projekt tworzy pakiet VSIX do wdrożenia elementu projektu kolumn witryny i szablon projektu.

- Projekt szablonu projektu. Ten projekt tworzy szablon projektu, który może służyć do tworzenia nowego projektu programu SharePoint, który zawiera elementu projektu kolumn witryny.

- Projekt biblioteki klas. Ten projekt, który implementuje rozszerzenie programu Visual Studio, która definiuje zachowanie elementu projektu kolumn witryny.

  Instruktaż należy rozpocząć od utworzenia projektów.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz **pliku** > **New** > **projektu**.

3. W górnej części **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest wybierany w listę wersji programu .NET Framework.

4. Rozwiń **języka Visual Basic** lub **Visual C#** węzłów, a następnie wybierz **rozszerzalności** węzła.

    > [!NOTE]
    > **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.

5. Na liście szablonów projektu wybierz **projekt VSIX**.

6. W **nazwa** wprowadź **SiteColumnProjectItem**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **SiteColumnProjectItem** projekt **Eksploratora rozwiązań**.

#### <a name="to-create-the-project-template-project"></a>Aby utworzyć projekt szablonu projektu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2. W górnej części **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest wybierany w listę wersji programu .NET Framework.

3. Rozwiń **Visual C#** lub **języka Visual Basic** węzła, a następnie wybierz **rozszerzalności** węzła.

4. Na liście szablonów projektu wybierz **szablonu projektu C#** lub **szablon projektu Visual Basic** szablonu.

5. W **nazwa** wprowadź **SiteColumnProjectTemplate**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **SiteColumnProjectTemplate** projektu do rozwiązania.

6. Usuń plik kodu Class1 z projektu.

7. Jeśli utworzono projekt języka Visual Basic, także Usuń następujące pliki z projektu:

    - *MyApplication.Designer.vb*

    - MyApplication.myapp

    - *Resources.Designer.vb*

    - *Resources.resx*

    - *Settings.Designer.vb*

    - Settings.settings

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2. W górnej części **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest wybierany w listę wersji programu .NET Framework.

3. Rozwiń **Visual C#** lub **języka Visual Basic** Wybierz węzły, **Windows** węzła, a następnie wybierz **biblioteki klas** szablonu.

4. W **nazwa** wprowadź **ProjectItemTypeDefinition** , a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ProjectItemTypeDefinition** projektu do rozwiązania i otwiera plik domyślny kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurowanie projektu rozszerzenia
 Dodaj pliki kodu i odwołania do zestawów, aby skonfigurować projekt rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W projekcie ProjectItemTypeDefinition, należy dodać plik kodu, który nosi nazwę **SiteColumnProjectItemTypeProvider**.

2. Na pasku menu wybierz **projektu** > **Dodaj odwołanie**.

3. W **Menadżer odwołań - ProjectItemTypeDefinition** okna dialogowego rozwiń **zestawy** węzła, wybierz **Framework** węzłem, a następnie wybierz pozycję Elementy System.ComponentModel.Composition pole wyboru.

4. Wybierz **rozszerzenia** węzeł, zaznacz pole wyboru obok zestawu Microsoft.VisualStudio.SharePoint, a następnie wybierz **OK** przycisku.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definiowanie nowego typu elementu projektu SharePoint
 Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu do określania zachowania nowym typem elementu projektu. Zawsze, gdy chcesz zdefiniować nowy typ elementu projektu, należy zaimplementować ten interfejs.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Aby zdefiniować nowym typem elementu projektu SharePoint

1. W **SiteColumnProjectItemTypeProvider** plik kodu, Zastąp domyślny kod następującym kodem, a następnie zapisz plik.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Create a Visual Studio project template
 Tworząc szablon projektu, możesz włączyć innym deweloperom tworzenie projektów programu SharePoint, które zawierają elementy projektu kolumn witryny. Szablon projektu programu SharePoint zawiera pliki, które są wymagane dla wszystkich projektów w programie Visual Studio, takie jak *.csproj* lub *.vbproj* i *.vstemplate* pliki i pliki są specyficzne dla projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 W tej procedurze należy utworzyć pusty projekt programu SharePoint, który ma generować pliki, które są specyficzne dla projektów programu SharePoint. Te pliki można następnie dodać do projektu SiteColumnProjectTemplate, dzięki czemu są one dołączone w szablonie, który jest generowany na podstawie tego projektu. Możesz także skonfigurować plik projektu SiteColumnProjectTemplate, aby określić, gdzie szablon projektu pojawia się w **nowy projekt** okno dialogowe.

#### <a name="to-create-the-files-for-the-project-template"></a>Aby utworzyć pliki dla szablonu projektu

1. Uruchom drugie wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu poświadczeń administracyjnych.

2. Utwórz projekt programu SharePoint 2010, który nosi nazwę **BaseSharePointProject**.

   > [!IMPORTANT]
   > W **Kreator ustawień niestandardowych SharePoint**, nie wybieraj **Wdróż jako rozwiązanie farmy** przycisku opcji.

3. Dodawanie elementu pustego elementu do projektu, a następnie nadaj nazwę elementu **pole1**.

4. Zapisz projekt, a następnie zamknij drugie wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

5. To wystąpienie elementu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SiteColumnProjectItem Otwórz rozwiązanie, które ma w programie **Eksploratora rozwiązań**, otwórz menu skrótów dla **SiteColumnProjectTemplate** węzła projektu, wybierz polecenie  **Dodaj**, a następnie wybierz **istniejący element**.

6. W **Dodaj istniejący element** okno dialogowe, Otwórz listę rozszerzeń plików, a następnie wybierz **wszystkie pliki (\*.\*)** .

7. W katalogu, który zawiera projekt BaseSharePointProject, wybierz plik key.snk, a następnie wybierz **Dodaj** przycisku.

   > [!NOTE]
   > W tym przewodniku szablon projektu, które tworzysz używa tego samego pliku key.snk do podpisywania każdego projektu, który jest tworzony przy użyciu szablonu. Aby dowiedzieć się, jak w celu rozszerzenia tego przykładu, aby utworzyć plik key.snk różne dla każdego wystąpienia projektu, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Powtórz kroki 5 – 8, aby dodać następujące pliki z podfolderów określonego w katalogu BaseSharePointProject:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.Feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Dodaj te pliki bezpośrednio do projektu SiteColumnProjectTemplate; Nie, ponownie utwórz podfoldery pole1, funkcji lub pakietów w projekcie. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Aby skonfigurować, jak deweloperzy odnaleźć szablonu projektu w oknie dialogowym Nowy projekt

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SiteColumnProjectTemplate** węzła projektu, a następnie wybierz **Zwolnij projekt**. Jeśli zostanie wyświetlony monit, aby zapisać zmiany do wszystkich plików, wybierz opcję **tak** przycisku.

2. Otwórz menu skrótów dla **SiteColumnProjectTemplate** węzła ponownie, a następnie wybierz **Edytuj SiteColumnProjectTemplate.csproj** lub **Edytuj SiteColumnProjectTemplate.vbproj**.

3. W pliku projektu zlokalizuj następujące `VSTemplate` elementu.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Zamień ten element na następujący kod XML.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Element określa dodatkowe foldery w ścieżce, w którym tworzony jest szablon projektu podczas kompilowania projektu. Foldery określone w tym miejscu, upewnij się, że szablon projektu będą dostępne tylko wtedy, gdy klienci otworzyć **nowy projekt** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010**  węzła.

5. Zapisz i zamknij plik.

6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SiteColumnProjectTemplate** projektu, a następnie wybierz **Załaduj ponownie projekt**.

## <a name="edit-the-project-template-files"></a>Edytuj pliki szablonu projektu
 W projekcie SiteColumnProjectTemplate edytować następujące pliki do określania zachowania szablonu projektu:

- *AssemblyInfo.cs* lub *AssemblyInfo.vb*

- *Elements.xml*

- *SharePointProjectItem.spdata*

- *Feature1.Feature*

- *Package.package*

- *SiteColumnProjectTemplate.vstemplate*

- *ProjectTemplate.csproj* lub *ProjectTemplate.vbproj*

  W poniższych procedurach dodasz parametrów zastępowalnych do niektórych z tych plików. Parametr wymienny jest token, który zaczyna się i kończy się znakiem dolara ($). Gdy użytkownik używa tego szablonu projektu, aby utworzyć projekt, Visual Studio automatycznie zastępuje tych parametrów w nowym projekcie z określonymi wartościami. Aby uzyskać więcej informacji, zobacz [parametrów zastępowalnych](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Aby edytować plik AssemblyInfo.cs lub AssemblyInfo.vb

1. W projekcie SiteColumnProjectTemplate Otwórz *AssemblyInfo.cs* lub *AssemblyInfo.vb* pliku, a następnie dodaj następującą instrukcję na początku:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Gdy **rozwiązanie w trybie piaskownicy** projektu programu SharePoint zostaje ustalona **True**, Visual Studio dodaje <xref:System.Security.AllowPartiallyTrustedCallersAttribute> do pliku kodu AssemblyInfo. Jednak nie importuje pliku AssemblyInfo kodu w szablonie projektu <xref:System.Security> przestrzeni nazw, domyślnie. Należy dodać to **przy użyciu** lub **Importy** instrukcję, aby uniemożliwić błędy kompilacji.

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-elementsxml-file"></a>Aby edytować plik Elements.xml

1. W projekcie SiteColumnProjectTemplate, Zastąp zawartość *Elements.xml* pliku następujący kod XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
          Name="$safeprojectname$"
          DisplayName="$projectname$"
          Type="Text"
          Group="Custom Columns">
      </Field>
    </Elements>
    ```

     Dodaje nowy plik XML `Field` element, który definiuje nazwę kolumny witryny, jego typ podstawowy i grupy, w której chcesz wyświetlić listę kolumny witryny w galerii. Aby uzyskać więcej informacji o zawartości tego pliku, zobacz [schematu definicji pola](http://go.microsoft.com/fwlink/?LinkId=184290).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Aby edytować plik SharePointProjectItem.spdata

1. W projekcie SiteColumnProjectTemplate, Zastąp zawartość *SharePointProjectItem.spdata* pliku następujący kod XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Nowy plik XML wprowadza następujące zmiany w pliku:

   - Zmiany `Type` atrybutu `ProjectItem` elementu do tego samego ciągu, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> w definicji elementu projektu ( `SiteColumnProjectItemTypeProvider` klasy, który został utworzony we wcześniejszej części tego przewodnika).

   - Usuwa `SupportedTrustLevels` i `SupportedDeploymentScopes` atrybuty z `ProjectItem` elementu. Te wartości atrybutów są zbędne, ponieważ poziomy zaufania i zakresy wdrożenia, które są określone w `SiteColumnProjectItemTypeProvider` klasy w projekcie ProjectItemTypeDefinition.

     Aby uzyskać więcej informacji na temat zawartości *spdata* plików, zobacz [odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-feature1feature-file"></a>Aby edytować plik Feature1.feature

1. W projekcie SiteColumnProjectTemplate, Zastąp zawartość *Feature1.feature* pliku następujący kod XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"
            imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""
            deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">
     <projectItems>
       <projectItemReference itemId="$guid2$" />
     </projectItems>
   </feature>
   ```

    Nowy plik XML wprowadza następujące zmiany w pliku:

   - Powoduje zmianę wartości `Id` i `featureId` atrybuty `feature` elementu `$guid4$`.

   - Powoduje zmianę wartości `itemId` atrybutu `projectItemReference` elementu `$guid2$`.

     Aby uzyskać więcej informacji na temat *.feature* plików, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-packagepackage-file"></a>Aby edytować plik Package.package

1. W projekcie SiteColumnProjectTemplate, Zastąp zawartość *Package.package* pliku następujący kod XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"
            Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"
            xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">
     <features>
       <featureReference itemId="$guid4$" />
     </features>
   </package>
   ```

    Nowy plik XML wprowadza następujące zmiany w pliku:

   - Powoduje zmianę wartości `Id` i `solutionId` atrybuty `package` elementu `$guid3$`.

   - Powoduje zmianę wartości `itemId` atrybutu `featureReference` elementu `$guid4$`.

     Aby uzyskać więcej informacji na temat *.package* plików, zobacz [Tworzenie elementu szablonów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Aby edytować plik sitecolumnprojecttemplate.vstemplate

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku SiteColumnProjectTemplate.vstemplate przy użyciu jednego z poniższych sekcji w pliku XML.

   - Jeśli tworzysz szablon projektu Visual C#, należy użyć następujący kod XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>CSharp</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

   - Jeśli tworzysz szablon projektu Visual Basic, należy użyć następujący kod XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">
     <TemplateData>
       <Name>Site Column</Name>
       <Description>Creates a new site column in SharePoint</Description>
       <FrameworkVersion>3.5</FrameworkVersion>
       <ProjectType>VisualBasic</ProjectType>
       <CreateNewFolder>true</CreateNewFolder>
       <CreateInPlace>true</CreateInPlace>
       <ProvideDefaultName>true</ProvideDefaultName>
       <DefaultName>SiteColumn</DefaultName>
       <LocationField>Enabled</LocationField>
       <EnableLocationBrowseButton>true</EnableLocationBrowseButton>
       <PromptForSaveOnCreation>true</PromptForSaveOnCreation>
       <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
       <Icon>SiteColumnProjectTemplate.ico</Icon>
       <SortOrder>1000</SortOrder>
     </TemplateData>
     <TemplateContent>
       <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">
         <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>
         <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>
         <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
       </Project>
     </TemplateContent>
   </VSTemplate>
   ```

    Nowy plik XML wprowadza następujące zmiany w pliku:

   - Zestawy `Name` element na wartość **kolumny witryny**. (Ta nazwa jest wyświetlana w **nowy projekt** okno dialogowe).

   - Dodaje `ProjectItem` elementy dla każdego filethat użytkownika uwzględnione w każdym wystąpieniu projektu.

   - Używa przestrzeni nazw "<http://schemas.microsoft.com/developer/vstemplate/2005>". Inne pliki projektu, w tym rozwiązaniu "<http://schemas.microsoft.com/developer/msbuild/2003>" przestrzeni nazw. W związku z tym zostaną wygenerowane komunikaty ostrzegawcze schematu XML, ale można go zignorować w tym przewodniku.

     Aby uzyskać więcej informacji na temat zawartości *.vstemplate* plików, zobacz [odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Aby edytować plik projecttemplate.csproj lub projecttemplate.vbproj

1. W projekcie SiteColumnProjectTemplate, Zastąp zawartość *ProjectTemplate.csproj* pliku lub *ProjectTemplate.vbproj* plik z jednym z następujących sekcji w pliku XML.

    - Jeśli tworzysz szablon projektu Visual C#, należy użyć następujący kod XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <AppDesignerFolder>Properties</AppDesignerFolder>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Web" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="Properties\AssemblyInfo.cs" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <ItemGroup>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

    1. Jeśli tworzysz szablon projektu Visual Basic, należy użyć następujący kod XML.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
        <ProductVersion>
        </ProductVersion>
        <SchemaVersion>
        </SchemaVersion>
        <ProjectGuid>{$guid1$}</ProjectGuid>
        <OutputType>Library</OutputType>
        <RootNamespace>$safeprojectname$</RootNamespace>
        <AssemblyName>$safeprojectname$</AssemblyName>
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>
        <FileAlignment>512</FileAlignment>
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        <OptionExplicit>On</OptionExplicit>
        <OptionCompare>Binary</OptionCompare>
        <OptionStrict>Off</OptionStrict>
        <OptionInfer>On</OptionInfer>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <DefineDebug>true</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <OutputPath>bin\Debug\</OutputPath>
        <WarningLevel>4</WarningLevel>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <DebugType>pdbonly</DebugType>
        <DefineDebug>false</DefineDebug>
        <DefineTrace>true</DefineTrace>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <UseVSHostingProcess>false</UseVSHostingProcess>
      </PropertyGroup>
      <PropertyGroup>
        <SignAssembly>true</SignAssembly>
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="System" />
        <Reference Include="System.Core" />
        <Reference Include="System.Data" />
        <Reference Include="System.Data.DataSetExtensions" />
        <Reference Include="System.Xml" />
        <Reference Include="System.Xml.Linq" />
        <Reference Include="Microsoft.SharePoint" />
        <Reference Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Import Include="Microsoft.VisualBasic" />
        <Import Include="System" />
        <Import Include="System.Collections" />
        <Import Include="System.Collections.Generic" />
        <Import Include="System.Data" />
        <Import Include="System.Diagnostics" />
        <Import Include="System.Linq" />
        <Import Include="System.Xml.Linq" />
        <Import Include="Microsoft.SharePoint" />
        <Import Include="Microsoft.SharePoint.Security" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="My Project\AssemblyInfo.vb" />
      </ItemGroup>
      <ItemGroup>
        <AppDesigner Include="My Project\" />
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.feature">
          <FeatureId>{$guid4$}</FeatureId>
        </None>
        <None Include="Field1\SharePointProjectItem.spdata">
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>
        </None>
        <None Include="key.snk" />
        <None Include="Package\Package.package">
          <PackageId>{$guid3$}</PackageId>
        </None>
        <None Include="Package\Package.Template.xml">
          <DependentUpon>Package.package</DependentUpon>
        </None>
      </ItemGroup>
      <ItemGroup>
        <None Include="Features\Feature1\Feature1.Template.xml">
          <DependentUpon>Feature1.feature</DependentUpon>
        </None>
        <None Include="Field1\Elements.xml" />
      </ItemGroup>
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />
    </Project>
    ```

     Nowy plik XML wprowadza następujące zmiany w pliku:

    - Używa `TargetFrameworkVersion` elementu, aby określić .NET Framework 3.5, nie 4.5.

    - Dodaje `SignAssembly` i `AssemblyOriginatorKeyFile` elementy do podpisywania wyniku projektu.

    - Dodaje `Reference` elementy dla zestawu odwołuje się do projektów używających programu SharePoint.

    - Dodaje elementy dla każdego domyślnego pliku w projekcie, takie jak *Elements.xml* i *SharePointProjectItem.spdata*.

2. Zapisz i zamknij plik.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Utwórz pakiet VSIX do wdrożenia szablonu projektu
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w **SiteColumnProjectItem** rozwiązania, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest, który znajduje się w projekcie VSIX. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksploratora rozwiązań**w **SiteColumnProjectItem** projektu, otwórz plik source.extension.vsixmanifest w edytorze manifestu.

     Plik source.extension.vsixmanifest jest podstawą dla pliku extension.vsixmanifest, które wymagają wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W **nazwa produktu** wprowadź **kolumny witryny**.

3. W **Autor** wprowadź **Contoso**.

4. W **opis** wprowadź **projekt programu SharePoint do tworzenia kolumny witryny**.

5. Wybierz **zasoby** kartę, a następnie wybierz **New** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

6. W **typu** wybierz **Microsoft.VisualStudio.ProjectTemplate**.

    > [!NOTE]
    > Ta wartość odpowiada `ProjectTemplate` elementu w pliku extension.vsixmanifest. Ten element umożliwia określenie podfolderu w pakiecie VSIX, który zawiera szablon projektu. Aby uzyskać więcej informacji, zobacz [ProjectTemplate — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

8. W **projektu** i wybierz polecenie **SiteColumnProjectTemplate**, a następnie wybierz **OK** przycisku.

9. Wybierz **New** ponownie przycisk.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

10. W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

12. W **projektu** wybierz **ProjectItemTypeDefinition**, a następnie wybierz **OK** przycisku.

13. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt kompiluje bez błędów.

## <a name="test-the-project-template"></a>Testowanie szablonu projektu
 Teraz można przystąpić do testowania szablonu projektu. Po pierwsze uruchom debugowanie rozwiązania SiteColumnProjectItem w doświadczalnym wystąpieniu programu Visual Studio. Następnie sprawdź **kolumny witryny** projektu w doświadczalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i uruchom projekt programu SharePoint, aby sprawdzić, czy kolumny witryny działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1. Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie SiteColumnProjectItem.

2. W pliku kodu SiteColumnProjectItemTypeProvider, Dodaj punkt przerwania do pierwszego wiersza kodu w `InitializeType` metody, a następnie wybierz **F5** klawisz, aby rozpocząć debugowanie.

     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu spowoduje przetestowanie w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Aby przetestować projekt w programie Visual Studio

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** węzeł (w zależności od języka obsługującego przez szablon projektu), rozwiń węzeł **SharePoint** węzła, a następnie wybierz polecenie **2010** węzła.

3. Na liście szablonów projektu wybierz **kolumny witryny** szablonu.

4. W **nazwa** wprowadź **SiteColumnTest** , a następnie wybierz **OK** przycisku.

     W **Eksploratora rozwiązań**, pojawi się nowy projekt z elementem projektu, który nosi nazwę **pole1**.

5. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `InitializeType` metody, a następnie wybierz **F5** klawisz, aby kontynuować debugowanie projektu.

6. W **Eksploratora rozwiązań**, wybierz **pole1** węzła, a następnie wybierz **F4** klucza.

     **Właściwości** zostanie otwarte okno.

7. Na liście właściwości, upewnij się, że właściwość **właściwość przykład** pojawia się.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Aby przetestować kolumny witryny w programie SharePoint

1. W **Eksploratora rozwiązań**, wybierz **SiteColumnTest** węzła.

2. W **właściwości** okna, w polu tekstowym, koło **adres URL witryny** właściwości wprowadź **http://localhost**.

     Ten krok określa lokalnej witryny programu SharePoint na komputerze programisty, który ma być używane do debugowania.

    > [!NOTE]
    > **Adres URL witryny** właściwość jest domyślnie puste, ponieważ szablon projektu kolumn witryny nie udostępnia kreatora pobierania tej wartości podczas tworzenia projektu. Aby dowiedzieć się, jak dodać kreatora, który pyta dewelopera dla tej wartości, a następnie konfiguruje tę właściwość w nowym projekcie, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Wybierz **F5** klucza.

     Kolumny witryny zostaje spakowany i wdrożyć w witrynie programu SharePoint, który jest określony w **adres URL witryny** właściwość projektu. Przeglądarka sieci web zostanie otwarta domyślna strona tej lokacji.

    > [!NOTE]
    > Jeśli **wyłączenia debugowania skryptu** pojawi się okno dialogowe, wybierz **tak** przycisk, aby kontynuować debugowanie projektu.

4. Na **Akcje witryny** menu, wybierz **ustawienia lokacji**.

5. Na **ustawienia lokacji** w obszarze **galerie** wybierz **kolumny witryny** łącza.

6. Na liście kolumn witryn, upewnij się, że **kolumn niestandardowych** grupa zawiera kolumnę o nazwie **SiteColumnTest**.

7. Zamknij przeglądarkę sieci web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu testowania projektu, należy usunąć szablon projektu w doświadczalnym wystąpieniu programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputerze deweloperskim

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2. Na liście rozszerzeń wybierz **kolumny witryny** rozszerzenie, a następnie wybierz **Odinstaluj** przycisku.

3. W oknie dialogowym wybierz **tak** przycisk, aby upewnić się, że chcesz odinstalować rozszerzenie.

4. Wybierz **Zamknij** przycisk, aby ukończyć dezinstalację.

5. Zamknij oba wystąpienia programu Visual Studio (wystąpienie doświadczalne i wystąpienie programu Visual Studio, w którym rozwiązanie SiteColumnProjectItem jest otwarty).

## <a name="next-steps"></a>Następne kroki
 Po ukończeniu tego przewodnika kreatora można dodać do szablonu projektu. Gdy użytkownik tworzy projekt kolumny witryny, Kreator zapyta użytkownika o adres URL witryny na potrzeby debugowania i nowe rozwiązanie jest w trybie piaskownicy, a Kreator konfiguruje nowy projekt z tymi informacjami. Kreator również zbiera informacje o kolumnie (na przykład typ podstawowy i grupy, w której ma na liście kolumn w galerii kolumny) i dodaje te informacje do *Elements.xml* plik w nowym projekcie. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)