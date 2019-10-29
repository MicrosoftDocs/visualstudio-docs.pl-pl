---
title: Utwórz element projektu kolumny witryny z szablonem projektu, część 1
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
ms.openlocfilehash: 13ede811cf2e9d900a0c78aca2214b43bd8438fe
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984698"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-1"></a>Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1
  Projekty programu SharePoint są kontenerami dla co najmniej jednego elementu projektu programu SharePoint. System projektu programu SharePoint w programie Visual Studio można rozłożyć przez utworzenie własnych typów elementów projektu programu SharePoint, a następnie skojarzenie ich z szablonem projektu. W tym instruktażu zdefiniujesz typ elementu projektu do tworzenia kolumny witryny, a następnie utworzysz szablon projektu, którego można użyć do utworzenia nowego projektu zawierającego element projektu kolumny witryny.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie rozszerzenia programu Visual Studio, które definiuje nowy typ elementu projektu programu SharePoint dla kolumny witryny. Typ elementu projektu zawiera prostą właściwość niestandardową, która pojawia się w oknie **Właściwości** .

- Tworzenie szablonu projektu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dla elementu projektu.

- Kompilowanie pakietu rozszerzenia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (VSIX) w celu wdrożenia szablonu projektu i zestawu rozszerzeń.

- Debugowanie i testowanie elementu projektu.

  Jest to przewodnik samodzielny. Po zakończeniu tego instruktażu można wzbogacić element projektu, dodając kreatora do szablonu projektu. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

> [!NOTE]
> Aby uzyskać szereg przykładowych przepływów pracy, zobacz [przykłady przepływu pracy programu SharePoint](/sharepoint/dev/general-development/sharepoint-workflow-samples).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Microsoft Windows, SharePoint i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących koncepcji jest przydatna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Kolumny witryny w programie SharePoint. Aby uzyskać więcej informacji, zobacz [kolumny](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

- Szablony projektów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten przewodnik, należy utworzyć trzy projekty:

- Projekt VSIX. Ten projekt tworzy pakiet VSIX do wdrożenia elementu projektu kolumny witryny i szablonu projektu.

- Projekt szablonu projektu. Ten projekt tworzy szablon projektu, którego można użyć do utworzenia nowego projektu programu SharePoint, który zawiera element projektu kolumny witryny.

- Projekt biblioteki klas. Ten projekt implementujący rozszerzenie programu Visual Studio, które definiuje zachowanie elementu projektu kolumny witryny.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz kolejno pozycje **plik**  > **Nowy**  > **projekt**.

3. W górnej części okna dialogowego **Nowy projekt** upewnij się, że na liście wersji .NET Framework wybrano **.NET Framework 4,5** .

4. Rozwiń węzły **Visual Basic** lub **wizualizacji C#**  , a następnie wybierz węzeł **rozszerzalności** .

    > [!NOTE]
    > Węzeł **rozszerzalności** jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

5. Na liście szablonów projektu wybierz pozycję **Projekt VSIX**.

6. W polu **Nazwa** wprowadź **SiteColumnProjectItem**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **SiteColumnProjectItem** do **Eksplorator rozwiązań**.

#### <a name="to-create-the-project-template-project"></a>Aby utworzyć projekt szablonu projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W górnej części okna dialogowego **Nowy projekt** upewnij się, że na liście wersji .NET Framework wybrano **.NET Framework 4,5** .

3. Rozwiń węzeł **wizualizacji C#**  lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

4. Na liście szablonów projektu wybierz  **C# szablon projektu** lub szablon **szablonu projektu Visual Basic** .

5. W polu **Nazwa** wprowadź **SiteColumnProjectTemplate**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **SiteColumnProjectTemplate** do rozwiązania.

6. Usuń plik kodu Class1 z projektu.

7. Jeśli utworzono projekt Visual Basic, Usuń również następujące pliki z projektu:

    - *Aplikacja. Designer. vb*

    - Aplikacja. MojaApl

    - *Resources. Designer. vb*

    - *Plik resources. resx*

    - *Settings. Designer. vb*

    - Settings. Settings

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W górnej części okna dialogowego **Nowy projekt** upewnij się, że na liście wersji .NET Framework wybrano **.NET Framework 4,5** .

3. Rozwiń węzły  **C# wizualizacji** lub **Visual Basic** , wybierz węzeł **systemu Windows** , a następnie wybierz szablon **Biblioteka klas** .

4. W polu **Nazwa** wprowadź **ProjectItemTypeDefinition** , a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **ProjectItemTypeDefinition** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Skonfiguruj projekt rozszerzenia
 Dodaj pliki kodu i odwołania do zestawów, aby skonfigurować projekt rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W projekcie ProjectItemTypeDefinition Dodaj plik kodu o nazwie **SiteColumnProjectItemTypeProvider**.

2. Na pasku menu wybierz **projekt** > **Dodaj odwołanie**.

3. W oknie dialogowym **Menedżer odwołań — ProjectItemTypeDefinition** rozwiń węzeł **zestawy** , wybierz węzeł **Struktura** , a następnie zaznacz pole wyboru System. ComponentModel. kompozycja.

4. Wybierz węzeł **rozszerzenia** , zaznacz pole wyboru obok zestawu Microsoft. VisualStudio. SharePoint, a następnie wybierz przycisk **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Zdefiniuj nowy typ elementu projektu programu SharePoint
 Utwórz klasę, która implementuje interfejs <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, aby zdefiniować zachowanie nowego typu elementu projektu. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zdefiniować nowy typ elementu projektu.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Aby zdefiniować nowy typ elementu projektu programu SharePoint

1. W pliku kodu **SiteColumnProjectItemTypeProvider** Zastąp domyślny kod następującym kodem, a następnie Zapisz plik.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]

## <a name="create-a-visual-studio-project-template"></a>Utwórz szablon projektu programu Visual Studio
 Tworząc szablon projektu, można umożliwić innym deweloperom tworzenie projektów programu SharePoint zawierających elementy projektu kolumny witryny. Szablon projektu programu SharePoint zawiera pliki, które są wymagane dla wszystkich projektów w programie Visual Studio, takich jak pliki *. csproj* lub *. vbproj* i *. vstemplate* , i pliki, które są specyficzne dla projektów programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Ta procedura polega na utworzeniu pustego projektu programu SharePoint w celu wygenerowania plików, które są specyficzne dla projektów programu SharePoint. Następnie należy dodać te pliki do projektu SiteColumnProjectTemplate, aby zostały uwzględnione w szablonie wygenerowanym z tego projektu. Należy również skonfigurować plik projektu SiteColumnProjectTemplate, aby określić, gdzie szablon projektu pojawia się w oknie dialogowym **Nowy projekt** .

#### <a name="to-create-the-files-for-the-project-template"></a>Aby utworzyć pliki dla szablonu projektu

1. Uruchom drugie wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] z poświadczeniami administracyjnymi.

2. Utwórz projekt programu SharePoint 2010 o nazwie **BaseSharePointProject**.

   > [!IMPORTANT]
   > W **Kreatorze dostosowania programu SharePoint**wybierz przycisk opcji **Wdróż jako rozwiązanie farmy** .

3. Dodaj pusty element do projektu, a następnie nadaj mu nazwę **pole1**.

4. Zapisz projekt, a następnie zamknij drugie wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

5. W wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], w którym jest otwarte rozwiązanie SiteColumnProjectItem, w **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **SiteColumnProjectTemplate** , wybierz polecenie **Dodaj**, a następnie wybierz **istniejący element**.

6. W oknie dialogowym **Dodaj istniejący element** Otwórz listę rozszerzeń plików, a następnie wybierz pozycję **wszystkie pliki (\*.\*)** .

7. W katalogu zawierającym projekt BaseSharePointProject wybierz plik Key. snk, a następnie wybierz przycisk **Dodaj** .

   > [!NOTE]
   > W tym instruktażu tworzony szablon projektu używa tego samego pliku Key. snk, aby podpisać każdy projekt, który został utworzony przy użyciu szablonu. Aby dowiedzieć się, jak rozwinąć ten przykład, aby utworzyć inny plik Key. snk dla każdego wystąpienia projektu, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

8. Powtórz kroki 5-8, aby dodać następujące pliki z określonych podfolderów w katalogu BaseSharePointProject:

   - *\Field1\Elements.xml*

   - *\Field1\SharePointProjectItem.spdata*

   - *\Features\Feature1\Feature1.feature*

   - *\Features\Feature1\Feature1.Template.xml*

   - *\Package\Package.package*

   - *\Package\Package.Template.xml*

     Dodaj te pliki bezpośrednio do projektu SiteColumnProjectTemplate; nie należy ponownie tworzyć podfolderów Pole1, Features i Package w projekcie. Aby uzyskać więcej informacji o tych plikach, zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

#### <a name="to-configure-how-developers-discover-the-project-template-in-the-new-project-dialog-box"></a>Aby skonfigurować sposób odnajdywania szablonu projektu przez deweloperów w oknie dialogowym Nowy projekt

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **SiteColumnProjectTemplate** , a następnie wybierz polecenie **Zwolnij projekt**. Jeśli zostanie wyświetlony monit o zapisanie zmian w dowolnych plikach, wybierz przycisk **tak** .

2. Otwórz menu skrótów dla węzła **SiteColumnProjectTemplate** , a następnie wybierz polecenie **Edytuj SiteColumnProjectTemplate. csproj** lub **Edytuj SiteColumnProjectTemplate. vbproj**.

3. W pliku projektu znajdź następujący `VSTemplate` elementu.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
    ```

4. Zamień ten element na następujący kod XML.

    ```xml
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` element określa dodatkowe foldery w ścieżce, w której tworzony jest szablon projektu podczas kompilowania projektu. Foldery określone w tym miejscu zapewniają, że szablon projektu będzie dostępny tylko wtedy, gdy klienci otworzą okno dialogowe **Nowy projekt** , rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

5. Zapisz i zamknij plik.

6. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **SiteColumnProjectTemplate** , a następnie wybierz polecenie **Załaduj ponownie projekt**.

## <a name="edit-the-project-template-files"></a>Edytowanie plików szablonów projektu
 W projekcie SiteColumnProjectTemplate Edytuj następujące pliki, aby zdefiniować zachowanie szablonu projektu:

- *AssemblyInfo.cs* lub *AssemblyInfo. vb*

- *Elementy. XML*

- *SharePointProjectItem.spdata*

- *Feature1. funkcja*

- *Package. Package*

- *SiteColumnProjectTemplate. vstemplate*

- *ProjectTemplate. csproj* lub *ProjectTemplate. vbproj*

  Poniższe procedury służą do dodawania parametrów wymiennych do niektórych z tych plików. Parametr wymienny jest tokenem rozpoczynającym się i kończącym znakiem dolara ($). Gdy użytkownik używa tego szablonu projektu do tworzenia projektu, program Visual Studio automatycznie zastępuje te parametry w nowym projekcie o określonych wartościach. Aby uzyskać więcej informacji, zobacz [Parametry wymienne](../sharepoint/replaceable-parameters.md).

#### <a name="to-edit-the-assemblyinfocs-or-assemblyinfovb-file"></a>Aby edytować plik AssemblyInfo.cs lub AssemblyInfo. vb

1. W projekcie SiteColumnProjectTemplate Otwórz plik *AssemblyInfo.cs* lub *AssemblyInfo. vb* , a następnie Dodaj następującą instrukcję do jego górnej części:

    ```vb
    Imports System.Security
    ```

    ```csharp
    using System.Security;
    ```

     Gdy właściwość **rozwiązanie w trybie piaskownicy** projektu programu SharePoint jest ustawiona na **wartość true**, program Visual Studio dodaje <xref:System.Security.AllowPartiallyTrustedCallersAttribute> do pliku kodu AssemblyInfo. Jednak plik kodu AssemblyInfo w szablonie projektu nie domyślnie importuje <xref:System.Security> przestrzeni nazw. Należy dodać tę instrukcję **using** lub **Imports** , aby zapobiec błędom kompilowania.

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-elementsxml-file"></a>Aby edytować plik. XML

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku repliks *. XML* następującym kodem XML.

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

     Nowy kod XML dodaje element `Field`, który definiuje nazwę kolumny witryny, jej typ podstawowy i grupę, w której ma zostać wystawiona kolumna witryny w galerii. Aby uzyskać więcej informacji na temat zawartości tego pliku, zobacz [schemat definicji pól](/previous-versions/office/developer/sharepoint-2010/ms196289(v=office.14)).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-sharepointprojectitemspdata-file"></a>Aby edytować plik SharePointProjectItem. spdata

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku *SharePointProjectItem. spdata* następującym kodem XML.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"
                xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
     <Files>
       <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />
     </Files>
   </ProjectItem>
   ```

    Nowy kod XML wprowadza następujące zmiany do pliku:

   - Zmienia atrybut `Type` elementu `ProjectItem` na ten sam ciąg, który jest przesyłany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> w definicji elementu projektu (Klasa `SiteColumnProjectItemTypeProvider` utworzona wcześniej w tym instruktażu).

   - Usuwa atrybuty `SupportedTrustLevels` i `SupportedDeploymentScopes` z elementu `ProjectItem`. Te wartości atrybutów są niepotrzebne, ponieważ poziomy zaufania i zakresy wdrożenia są określone w klasie `SiteColumnProjectItemTypeProvider` w projekcie ProjectItemTypeDefinition.

     Aby uzyskać więcej informacji o zawartości plików *. spdata* , zobacz [Dokumentacja schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-feature1feature-file"></a>Aby edytować plik Feature1. feature

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku *Feature1. feature* następującym kodem XML.

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

    Nowy kod XML wprowadza następujące zmiany do pliku:

   - Zmienia wartości `Id` i `featureId` atrybutów elementu `feature` na `$guid4$`.

   - Zmienia wartości atrybutu `itemId` elementu `projectItemReference` na `$guid2$`.

     Aby uzyskać więcej informacji na temat plików *. feature* , zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-packagepackage-file"></a>Aby edytować plik Package. Package

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku *Package. Package* następującym kodem XML.

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

    Nowy kod XML wprowadza następujące zmiany do pliku:

   - Zmienia wartości `Id` i `solutionId` atrybutów elementu `package` na `$guid3$`.

   - Zmienia wartości atrybutu `itemId` elementu `featureReference` na `$guid4$`.

     Aby uzyskać więcej informacji na temat plików *pakietu* , zobacz [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-sitecolumnprojecttemplatevstemplate-file"></a>Aby edytować plik SiteColumnProjectTemplate. vstemplate

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku SiteColumnProjectTemplate. vstemplate jednym z następujących sekcji kodu XML.

   - Jeśli tworzysz szablon projektu wizualnego C# , użyj poniższego kodu XML.

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

   - Jeśli tworzysz szablon projektu Visual Basic, użyj poniższego kodu XML.

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

    Nowy kod XML wprowadza następujące zmiany do pliku:

   - Ustawia element `Name` w **kolumnie witryna**wartości. (Ta nazwa pojawia się w oknie dialogowym **Nowy projekt** ).

   - Dodaje `ProjectItem` elementy dla każdego elementu filethat dołączonego do każdego wystąpienia projektu.

   - Używa przestrzeni nazw "<http://schemas.microsoft.com/developer/vstemplate/2005>". Inne pliki projektu w tym rozwiązaniu używają przestrzeni nazw "<http://schemas.microsoft.com/developer/msbuild/2003>". W związku z tym są generowane komunikaty ostrzegawcze schematu XML, ale można je zignorować w tym instruktażu.

     Aby uzyskać więcej informacji na temat zawartości plików *. vstemplate* , zobacz [Dokumentacja schematu szablonu programu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).

2. Zapisz i zamknij plik.

#### <a name="to-edit-the-projecttemplatecsproj-or-projecttemplatevbproj-file"></a>Aby edytować plik ProjectTemplate. csproj lub ProjectTemplate. vbproj

1. W projekcie SiteColumnProjectTemplate Zastąp zawartość pliku *ProjectTemplate. csproj* lub *ProjectTemplate. vbproj* jednym z następujących sekcji kodu XML.

    - Jeśli tworzysz szablon projektu wizualnego C# , użyj poniższego kodu XML.

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

    1. Jeśli tworzysz szablon projektu Visual Basic, użyj poniższego kodu XML.

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

     Nowy kod XML wprowadza następujące zmiany do pliku:

    - Używa elementu `TargetFrameworkVersion`, aby określić .NET Framework 3,5, a nie 4,5.

    - Dodaje `SignAssembly` i `AssemblyOriginatorKeyFile` elementy do podpisywania danych wyjściowych projektu.

    - Dodaje `Reference` elementy dla odwołań do zestawów, które są używane przez projekty programu SharePoint.

    - Dodaje elementy dla każdego pliku domyślnego w projekcie, takie jak *elementy. XML* i *SharePointProjectItem. spdata*.

2. Zapisz i zamknij plik.

## <a name="create-a-vsix-package-to-deploy-the-project-template"></a>Tworzenie pakietu VSIX w celu wdrożenia szablonu projektu
 Aby wdrożyć rozszerzenie, użyj projektu VSIX w rozwiązaniu **SiteColumnProjectItem** , aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest, który jest zawarty w projekcie VSIX. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksplorator rozwiązań**, w projekcie **SiteColumnProjectItem** , Otwórz plik source. Extension. vsixmanifest w edytorze manifestu.

     Plik source. Extension. vsixmanifest jest podstawą dla pliku Extension. vsixmanifest, który wymaga wszystkich pakietów VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W polu **Nazwa produktu** wprowadź wartość **kolumny witryna**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź **projekt programu SharePoint służący do tworzenia kolumn witryny**.

5. Wybierz kartę **zasoby** , a następnie wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

6. Na liście **Typ** wybierz **Microsoft. VisualStudio. ProjectTemplate**.

    > [!NOTE]
    > Ta wartość odpowiada elementowi `ProjectTemplate` w pliku Extension. vsixmanifest. Ten element identyfikuje podfolder w pakiecie VSIX, który zawiera szablon projektu. Aby uzyskać więcej informacji, zobacz [ProjectTemplate element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)).

7. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

8. Na liście **projekt** , a następnie wybierz pozycję **SiteColumnProjectTemplate**, a następnie wybierz przycisk **OK** .

9. Ponownie wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

10. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odpowiada elementowi `MefComponent` w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

12. Na liście **projekt** wybierz pozycję **ProjectItemTypeDefinition**, a następnie wybierz przycisk **OK** .

13. Na pasku menu wybierz **kompiluj** > **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt kompiluje się bez błędów.

## <a name="test-the-project-template"></a>Testowanie szablonu projektu
 Teraz można przystąpić do testowania szablonu projektu. Najpierw Rozpocznij debugowanie rozwiązania SiteColumnProjectItem w eksperymentalnym wystąpieniu programu Visual Studio. Następnie przetestuj projekt **kolumny witryny** w eksperymentalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i Uruchom projekt programu SharePoint, aby sprawdzić, czy kolumna lokacja działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1. Uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie SiteColumnProjectItem.

2. W pliku kodu SiteColumnProjectItemTypeProvider Dodaj punkt przerwania do pierwszego wiersza kodu w metodzie `InitializeType`, a następnie wybierz klawisz **F5** , aby rozpocząć debugowanie.

     Program Visual Studio instaluje rozszerzenie%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Site Column\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-project-in-visual-studio"></a>Aby przetestować projekt w programie Visual Studio

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

2. Rozwiń węzeł **wizualizacji C#**  lub **Visual Basic** (w zależności od języka obsługiwanego przez szablon projektu), rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

3. Na liście szablonów projektu wybierz szablon **kolumna lokacja** .

4. W polu **Nazwa** wprowadź **SiteColumnTest** , a następnie wybierz przycisk **OK** .

     W **Eksplorator rozwiązań**nowy projekt pojawia się z elementem projektu o nazwie **pole1**.

5. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony wcześniej w metodzie `InitializeType`, a następnie wybierz klawisz **F5** , aby kontynuować debugowanie projektu.

6. W **Eksplorator rozwiązań**wybierz węzeł **pole1** , a następnie wybierz klawisz **F4** .

     Zostanie otwarte okno **Właściwości** .

7. Na liście właściwości Sprawdź, czy jest wyświetlana **Właściwość przykład** właściwości.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Aby przetestować kolumnę witryny w programie SharePoint

1. W **Eksplorator rozwiązań**wybierz węzeł **SiteColumnTest** .

2. W oknie **Właściwości** w polu tekstowym obok właściwości **adres URL witryny** wprowadź **http://localhost** .

     Ten krok określa lokalną witrynę programu SharePoint na komputerze deweloperskim, który ma być używany do debugowania.

    > [!NOTE]
    > Właściwość **adres URL witryny** jest domyślnie pusta, ponieważ szablon projektu kolumny witryny nie udostępnia kreatora do zbierania tej wartości podczas tworzenia projektu. Aby dowiedzieć się, jak dodać kreatora, który prosi projektanta o tę wartość, a następnie konfiguruje tę właściwość w nowym projekcie, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

3. Wybierz klawisz **F5** .

     Kolumna lokacja jest spakowana i wdrożona w witrynie programu SharePoint, która jest określona we właściwości **adres URL witryny** projektu. Przeglądarka sieci Web otworzy się na stronie domyślnej tej witryny.

    > [!NOTE]
    > Jeśli zostanie wyświetlone okno dialogowe **debugowanie skryptu wyłączone** , wybierz przycisk **tak** , aby kontynuować debugowanie projektu.

4. W menu **Akcje witryny** wybierz pozycję **Ustawienia lokacji**.

5. Na stronie **Ustawienia lokacji** w obszarze **Galerie** wybierz łącze **kolumny witryny** .

6. Na liście kolumn lokacji Sprawdź, czy grupa **kolumny niestandardowa** zawiera kolumnę o nazwie **SiteColumnTest**.

7. Zamknij przeglądarkę sieci Web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie komputera deweloperskiego
 Po zakończeniu testowania projektu Usuń szablon projektu z eksperymentalnego wystąpienia programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputer deweloperski

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **narzędzia** > **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz rozszerzenie **kolumna witryny** , a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz przycisk **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie.

4. Wybierz przycisk **Zamknij** , aby ukończyć dezinstalację.

5. Zamknij oba wystąpienia programu Visual Studio (wystąpienie eksperymentalne i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie SiteColumnProjectItem).

## <a name="next-steps"></a>Następne kroki
 Po zakończeniu tego instruktażu można dodać kreatora do szablonu projektu. Gdy użytkownik tworzy projekt kolumny witryny, w kreatorze zostanie wyświetlony monit o podanie adresu URL witryny na potrzeby debugowania oraz tego, czy nowe rozwiązanie jest w trybie piaskownicy, a Kreator konfiguruje nowy projekt przy użyciu tych informacji. Kreator zbiera również informacje o kolumnie (takie jak typ podstawowy i Grupa, w której ma zostać wystawiona kolumna w galerii kolumn witryny) i dodaje te informacje do pliku repliks *. XML* w nowym projekcie. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi programu SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)