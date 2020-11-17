---
title: Wdrażanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio | Microsoft Docs
description: Wdróż rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio. Użyj projektów rozszerzeń programu Visual Studio (VSIX) do tworzenia pakietów VSIX.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c8b05b5cb74a28157436f95f01992515c716e6a
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672681"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Wdróż rozszerzenia dla narzędzi programu SharePoint w programie Visual Studio

Aby wdrożyć rozszerzenie narzędzi SharePoint, Utwórz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX), który zawiera zestaw rozszerzeń i wszystkie inne pliki, które chcesz dystrybuować z rozszerzeniem. Pakiet VSIX to skompresowany plik zgodny ze standardem Open Package Conventions (OPC). Pakiety VSIX mają rozszerzenie *. vsix* .

Po utworzeniu pakietu VSIX inni użytkownicy mogą uruchomić plik. vsix, aby zainstalować rozszerzenie. Gdy użytkownik zainstaluje rozszerzenie, wszystkie pliki zostaną zainstalowane do folderu%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Aby wdrożyć rozszerzenie, można przekazać pakiet VSIX do witryny sieci Web programu [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub rozproszyć pakiet do klientów w inny sposób, na przykład hostowanie pakietu w udziale sieciowym lub w innej witrynie sieci Web.

Aby uzyskać więcej informacji na temat tworzenia pakietów VSIX i wdrażania ich w [Visual Studio Marketplace](https://marketplace.visualstudio.com/), zobacz [wysyłanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Pakiet VSIX można utworzyć przy użyciu szablonu **projektu VSIX** w programie Visual Studio lub ręcznie utworzyć pakiet VSIX.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Tworzenie pakietów VSIX przy użyciu projektów VSIX

Aby utworzyć pakiety VSIX dla rozszerzeń narzędzi SharePoint, można użyć szablonu **projektu VSIX** dostarczonego przez zestaw SDK programu Visual Studio. Użycie projektu VSIX zapewnia kilka korzyści w porównaniu do ręcznego tworzenia pakietu VSIX:

- Program Visual Studio automatycznie generuje pakiet VSIX podczas kompilowania projektu. Zadania takie jak dodanie plików wdrożenia do pakietu i utworzenie pliku [Content_Types]. XML dla pakietu.

- Można skonfigurować projekt VSIX w taki sposób, aby zawierał dane wyjściowe kompilacji projektu rozszerzenia i innych plików, takich jak szablony projektów i szablony elementów, w pakiecie VSIX.

Aby uzyskać więcej informacji na temat korzystania z projektu VSIX, zobacz [szablon projektu VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizowanie projektów

Domyślnie projekty VSIX generują tylko pakiety VSIX, a nie zestawy. W związku z tym zazwyczaj nie implementuje się rozszerzenia narzędzi programu SharePoint w projekcie VSIX. Zwykle pracujesz z co najmniej dwoma projektami:

- Projekt VSIX.

- Projekt biblioteki klas implementujący rozszerzenie.

Możesz również korzystać z dodatkowych projektów dla niektórych typów rozszerzeń:

- Projekt biblioteki klas, który implementuje wszystkie polecenia programu SharePoint, które są używane przez rozszerzenie. Aby zapoznać się z przewodnikiem, który ilustruje ten scenariusz, zobacz [Przewodnik: rozszerzona Eksplorator serwera w celu wyświetlenia części sieci Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Szablon elementu lub projekt szablonu projektu, który tworzy szablon elementu lub szablon projektu, jeśli rozszerzenie definiuje nowy typ elementu projektu programu SharePoint. Aby zapoznać się z przewodnikiem, który ilustruje ten scenariusz, zobacz [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Projekt biblioteki klas, który implementuje kreatora niestandardowego dla szablonu elementu lub szablonu projektu, jeśli rozszerzenie zawiera szablon. Aby zapoznać się z przewodnikiem, który ilustruje ten scenariusz, zobacz [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

W przypadku uwzględnienia wszystkich projektów w tym samym rozwiązaniu programu Visual Studio można zmodyfikować plik source. Extension. vsixmanifest w projekcie VSIX, aby uwzględnić dane wyjściowe kompilacji projektów biblioteki klas.

### <a name="edit-the-vsix-manifest"></a>Edytuj manifest VSIX

Należy edytować plik source. Extension. vsixmanifest w projekcie VSIX, aby uwzględnić wpisy dla wszystkich elementów, które mają zostać dołączone do rozszerzenia. Po otwarciu pliku source. Extension. vsixmanifest z jego menu skrótów, plik jest wyświetlany w projektancie, który udostępnia interfejs użytkownika do edycji kodu XML w pliku. Aby uzyskać więcej informacji, zobacz [projektant manifestu VSIX](../extensibility/vsix-manifest-designer.md).

Należy dodać wpisy do pliku source. Extension. vsixmanifest dla następujących elementów:

- Zestaw rozszerzenia.

- Zestaw, który implementuje wszystkie polecenia programu SharePoint, które są używane przez rozszerzenie.

- Wszystkie szablony projektu lub szablony elementów, które są skojarzone z danym rozszerzeniem.

- Niestandardowy Kreator dla szablonu, który jest skojarzony z danym rozszerzeniem.

W poniższych procedurach opisano sposób dodawania wpisów do pliku vsixmanifest dla każdego z tych elementów.

#### <a name="to-include-the-extension-assembly"></a>Aby dołączyć zestaw rozszerzeń

1. W projekcie VSIX Otwórz menu skrótów dla pliku source. Extension. vsixmanifest, a następnie wybierz polecenie **Otwórz**.

     Plik zostanie otwarty w projektancie

2. Na karcie **zasoby** edytora wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

3. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

4. Na liście **Źródło** wykonaj jedną z następujących czynności:

    - Jeśli zestaw rozszerzeń jest zbudowany z projektu, który znajduje się w tym samym rozwiązaniu co projekt VSIX, wybierz **projekt w bieżącym rozwiązaniu**. Na liście **projekt** wybierz nazwę projektu.

    - Jeśli zestaw rozszerzeń jest dołączony jako plik w projekcie, wybierz opcję **plik w systemie plików**. Na liście **ścieżka** wprowadź pełną ścieżkę do pliku zestawu rozszerzenia lub użyj przycisku **Przeglądaj** , aby zlokalizować i wybrać plik zestawu.

5. Wybierz przycisk **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Aby dołączyć zestaw poleceń programu SharePoint

1. W projekcie VSIX Otwórz menu skrótów dla pliku source. Extension. vsixmanifest, a następnie wybierz przycisk **Otwórz** .

     Plik zostanie otwarty w projektancie.

2. W sekcji **zasoby** edytora wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

3. W polu **Typ** wprowadź wartość **SharePoint. Commands. v4**.

4. Na liście **Źródło** wykonaj jedną z następujących czynności:

    - Jeśli zestaw poleceń jest zbudowany z projektu, który znajduje się w tym samym rozwiązaniu co projekt VSIX, wybierz **projekt w bieżącym rozwiązaniu**. Na liście **projekt** wybierz nazwę projektu.

    - Jeśli zestaw poleceń jest dołączony jako plik w projekcie, wybierz opcję **plik w systemie plików**. Na liście **ścieżka** wprowadź pełną ścieżkę do pliku zestawu rozszerzenia lub użyj przycisku **Przeglądaj** , aby zlokalizować i wybrać plik zestawu.

5. Wybierz przycisk **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Aby dołączyć szablon, który tworzysz

1. W projekcie VSIX Otwórz menu skrótów dla pliku source. Extension. vsixmanifest, a następnie wybierz przycisk **Otwórz** .

     Plik zostanie otwarty w projektancie.

2. W sekcji **zasoby** edytora wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

3. Na liście **Typ** wybierz **Microsoft. VisualStudio. ProjectTemplate** lub **Microsoft. VisualStudio. ItemTemplate**.

4. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

5. Na liście **projekt** wybierz nazwę projektu, a następnie wybierz przycisk **OK** .

6. W **Eksplorator rozwiązań** Otwórz menu skrótów dla szablonu projektu lub projektu szablonu elementu, a następnie wybierz polecenie **Zwolnij projekt**.

7. Otwórz menu skrótów dla węzła projektu, a następnie wybierz polecenie **Edytuj**_YourTemplateProjectName_**. csproj** lub **Edytuj**_YourTemplateProjectName_**. vbproj**.

8. Zlokalizuj następujący `VSTemplate` element w pliku projektu.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Zamień ten element na następujący kod XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath`Element określa dodatkowe foldery w ścieżce, w której tworzony jest szablon projektu podczas kompilowania projektu. Foldery określone w tym miejscu zapewniają, że szablon elementu będzie dostępny tylko wtedy, gdy klienci otworzą okno dialogowe **Dodaj nowy projekt** , rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

10. Zapisz i zamknij plik.

11. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu szablonu lub szablonu elementu, a następnie wybierz polecenie **Załaduj ponownie projekt**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Aby dołączyć szablon, który tworzysz ręcznie

1. W projekcie VSIX Dodaj nowy folder do projektu, aby zawierał szablon.

2. W obszarze tego nowego folderu Utwórz następujące podfoldery, a następnie Dodaj plik szablonu (zip) do folderu *ID ustawień regionalnych* .

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Identyfikator ustawień regionalnych*

     *YourTemplateName*. zip

     Na przykład jeśli masz szablon elementu o nazwie ContosoCustomAction.zip, który obsługuje ustawienia regionalne w języku angielskim (Stany Zjednoczone), pełna ścieżka może być *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. W **Eksplorator rozwiązań** wybierz plik szablonu (*YourTemplateName*. zip).

4. W oknie **Właściwości** ustaw właściwość **Akcja kompilacji** na **zawartość**.

5. Otwórz menu skrótów dla pliku source. Extension. vsixmanifest, a następnie wybierz polecenie **Otwórz**.

     Plik zostanie otwarty w projektancie.

6. W sekcji **zasoby** edytora wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

7. Na liście **Typ** wybierz **Microsoft. VisualStudio. ItemTemplate** lub **Microsoft. VisualStudio. ProjectTemplate**.

8. Z listy **Źródło** wybierz pozycję **plik w systemie plików**.

9. W polu **ścieżka** wprowadź pełną ścieżkę do zestawu (na przykład *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip* lub użyj przycisku **Przeglądaj** , aby zlokalizować i wybrać zestaw, a następnie wybierz przycisk **OK** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Aby dodać kreatora dla szablonu projektu lub szablonu elementu

1. W projekcie VSIX Otwórz menu skrótów dla pliku source. Extension. vsixmanifest, a następnie wybierz polecenie **Otwórz**.

     Plik zostanie otwarty w projektancie.

2. W sekcji **zasoby** edytora wybierz przycisk **Nowy** .

     Zostanie otwarte okno dialogowe **Dodaj nowy element zawartości** .

3. Z listy **Typ** wybierz **Microsoft. VisualStudio. Assembly**.

4. Na liście **Źródło** wykonaj jedną z następujących czynności:

    - Jeśli zestaw kreatora został skompilowany z projektu, który znajduje się w tym samym rozwiązaniu co projekt VSIX, wybierz **projekt w bieżącym rozwiązaniu**. Na liście **projekt** wybierz nazwę projektu.

    - Jeśli zestaw kreatora jest dołączony jako plik w projekcie, wybierz opcję **plik w systemie plików**. W polu **ścieżka** wprowadź pełną ścieżkę do pliku zestawu lub użyj przycisku **Przeglądaj** , aby zlokalizować i wybrać zestaw.

5. Wybierz przycisk **OK** .

### <a name="related-walkthroughs"></a>Powiązane instruktaże

W poniższej tabeli przedstawiono wskazówki, które pokazują, jak używać projektu VSIX do wdrażania różnych typów rozszerzeń narzędzi programu SharePoint.

|Typ rozszerzenia|Powiązane instruktaże|
|--------------------|--------------------------|
|Rozszerzenie, które zawiera tylko zestaw rozszerzeń|[Przewodnik: zwiększanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Przewodnik: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Przewodnik: wywoływanie modelu obiektów klienta programu SharePoint w rozszerzeniu Eksplorator serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Rozszerzenie, które zawiera polecenia programu SharePoint|[Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Przewodnik: rozszerzona Eksplorator serwera do wyświetlania składników Web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Rozszerzenie obejmujące szablon programu Visual Studio|[Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Rozszerzenie, które zawiera Kreatora szablonu|[Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Przewodnik: Tworzenie elementu projektu kolumny witryny z szablonem projektu, część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Utwórz ręcznie pakiety VSIX

Jeśli chcesz ręcznie utworzyć pakiet VSIX dla rozszerzenia narzędzi programu SharePoint, wykonaj następujące czynności:

1. Utwórz plik Extension. vsixmanifest oraz plik [Content_Types]. XML w nowym folderze. Aby uzyskać więcej informacji, zobacz [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. W Eksploratorze Windows kliknij prawym przyciskiem myszy folder zawierający dwa pliki XML, kliknij polecenie Wyślij do, a następnie kliknij folder skompresowany (zip). Zmień nazwę otrzymanego pliku zip na filename. vsix, gdzie filename to nazwa pliku redystrybucyjnego, który instaluje pakiet.

3. Dodaj zestaw rozszerzeń do pakietu VSIX. Jeśli rozszerzenie zawiera polecenie programu SharePoint, należy również dodać zestaw, który implementuje polecenie programu SharePoint do pakietu VSIX.

4. Zmodyfikuj plik rozszerzenia vsixmanifest:

    - Dodaj `Microsoft.VisualStudio.MefComponent` element poniżej `Assets` elementu, a następnie ustaw wartość nowego elementu na ścieżkę względną zestawu, który implementuje rozszerzenie w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Jeśli rozszerzenie zawiera polecenie programu SharePoint, które wywołuje do modelu obiektów serwera dla programu SharePoint, Dodaj `Microsoft.VisualStudio.Assembly` element w obszarze `Assets` elementu. Ustaw wartość nowego elementu na ścieżkę względną zestawu, który implementuje polecenie programu SharePoint w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [element zawartości (schemat VSX)](/previous-versions/dd393737(v=vs.110)).

    - Jeśli rozszerzenie zawiera szablon projektu lub szablon elementu, Dodaj `ProjectTemplate` `ItemTemplate` element lub w obszarze `Assets` elementu. Ustaw wartość nowego elementu na ścieżkę względną folderu zawierającego szablon w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [element ProjectTemplate (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) i [element ITEMTEMPLATE (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Jeśli rozszerzenie zawiera kreatora niestandardowego szablonu lub szablonu elementu, Dodaj `Assembly` element w obszarze `Assets` elementu. Ustaw wartość nowego elementu na ścieżkę względną zestawu w pakiecie VSIX, a następnie ustaw `AssemblyName` atrybut na pełną nazwę zestawu (w tym wersję, kulturę i token klucza publicznego). Aby uzyskać więcej informacji, zobacz [element zależności (schemat VSX)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Przykład

Poniższy przykład przedstawia zawartość pliku Extension. vsixmanifest rozszerzenia narzędzi SharePoint Tools. Rozszerzenie jest zaimplementowane w zestawie o nazwie Contoso.ProjectExtension.dll. Rozszerzenie zawiera zestaw poleceń programu SharePoint o nazwie Contoso.ExtensionCommands.dll i szablon elementu w folderze o nazwie **elementów** w pakiecie VSIX. W tym przykładzie przyjęto założenie, że oba zestawy znajdują się w tym samym folderze, co plik Extension. vsixmanifest w pakiecie VSIX.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Zobacz także

- [Poszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozwiń węzeł połączenia programu SharePoint w Eksplorator serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Debugowanie rozszerzeń dla narzędzi programu SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)