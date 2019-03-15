---
title: Wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2dd787168d906ce90a50562e5147b45308c54ff5
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868062"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Wdrażanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio

Aby wdrożyć rozszerzenia narzędzi programu SharePoint, należy utworzyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakiet rozszerzenia (VSIX), który zawiera zestaw rozszerzenia i inne pliki, które chcesz dystrybuować z rozszerzeniem. Pakiet VSIX jest skompresowany plik, który postępuje zgodnie ze standardowym otwarte konwencje tworzenia pakietów (OPC). Pakiety VSIX mają *.vsix* rozszerzenia.

Po utworzeniu pakietu VSIX, inni użytkownicy, można uruchomić plik .vsix, aby zainstalować rozszerzenie. Po zainstalowaniu rozszerzenia wszystkie pliki są instalowane w folderze %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Aby wdrożyć rozszerzenie, możesz przekazać pakietu VSIX do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) witryny sieci Web, lub można dystrybuować pakiet do klientów za pomocą innych środków, takich jak hostowanie pakietu na udział sieciowy lub innych sieci Web witryna.

Aby uzyskać więcej informacji o tworzeniu pakietów VSIX i wdrożenie ich [Visual Studio Marketplace](https://marketplace.visualstudio.com/), zobacz [wysyłania rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Możesz utworzyć pakiet VSIX przy użyciu **projekt VSIX** szablonu w programie Visual Studio, lub można ręcznie utworzyć pakiet VSIX.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Używać projektów VSIX do tworzenia pakietów VSIX

Możesz użyć **projekt VSIX** szablonem programu Visual Studio SDK do tworzenia pakietów VSIX dla rozszerzeń narzędzi programu SharePoint. Za pomocą projektu VSIX zapewnia kilka korzyści za pośrednictwem ręczne tworzenie pakietu VSIX:

-   Podczas kompilowania projektu programu Visual Studio automatycznie generuje pakiet VSIX. Zadania, takie jak dodawanie pliki wdrożenia pakietu i tworzenia pliku [Content_Types] .xml dla pakietu są wykonywane tylko dla Ciebie.

-   Można skonfigurować projekt VSIX, aby dołączyć dane wyjściowe kompilacji projektu rozszerzenia i inne pliki, takie jak szablony projektów i szablonów elementów w pakiecie VSIX.

Aby uzyskać więcej informacji na temat używania projektu VSIX, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organizowanie projektów

Domyślnie projektów VSIX generować tylko pakietów VSIX, nie zestawów. Dlatego należy zwykle nie należy implementować rozszerzenia narzędzi programu SharePoint w projekcie VSIX. Ogólnie pracować z co najmniej dwa projekty:

-   A VSIX project.

-   Projekt biblioteki klas, który implementuje rozszerzenie.

Możesz także pracować z projektami dodatkowe dla niektórych typów rozszerzeń:

-   Projekt biblioteki klas, który implementuje żadnych poleceń programu SharePoint, które są używane przez Twoje rozszerzenie. Aby uzyskać wskazówki, które pokazuje, w tym scenariuszu, zobacz [instruktażu: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

-   Na projekt szablonu elementu lub szablon projektu, który tworzy szablon elementu lub szablon projektu, jeśli rozszerzenie definiuje nowy typ elementu projektu programu SharePoint. Aby uzyskać wskazówki, które pokazuje, w tym scenariuszu, zobacz [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

-   Projekt biblioteki klas, który implementuje niestandardowego kreatora szablonu elementu lub szablon projektu, jeśli rozszerzenie zawiera szablon. Aby uzyskać wskazówki, które pokazuje, w tym scenariuszu, zobacz [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Jeśli dodasz wszystkie projekty w rozwiązaniu programu Visual Studio, można zmodyfikować plik source.extension.vsixmanifest w projekcie VSIX, aby zawierał wyniki kompilacji projekty bibliotek klas.

### <a name="edit-the-vsix-manifest"></a>Edytuj manifest w VSIX

Należy zmodyfikować plik source.extension.vsixmanifest w projekcie VSIX, aby dołączyć wpisy dla wszystkich elementów, które mają zostać uwzględnione w rozszerzeniu. Po otwarciu pliku source.extension.vsixmanifest w jego menu skrótów pliku pojawia się w projektancie, który zapewnia interfejs użytkownika do edycji kodu XML w pliku. Aby uzyskać więcej informacji, zobacz [Projektant manifestu VSIX](../extensibility/vsix-manifest-designer.md).

Musisz dodać wpisy do pliku source.extension.vsixmanifest dla następujących elementów:

-   Zestawu rozszerzeń.

-   Zestaw, który implementuje żadnych poleceń programu SharePoint, które są używane przez Twoje rozszerzenie.

-   Szablony projektów i szablonów elementów, które są skojarzone z rozszerzeniem.

-   Kreator niestandardowego szablonu, który jest skojarzony z rozszerzeniem.

W poniższych procedurach opisano sposób dodawania pozycji do pliku .vsixmanifest dla każdego z tych elementów.

#### <a name="to-include-the-extension-assembly"></a>Aby uwzględnić zestawu rozszerzeń

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz**.

     Plik zostanie otwarty w Projektancie

2.  Na **zasoby** karta w edytorze wybierz **nowy** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.

4.  W **źródła** listy, wykonaj jedną z następujących czynności:

    -   Jeśli zestawu rozszerzeń jest zbudowany z projektu, który znajduje się w tym samym rozwiązaniu co projekt VSIX, wybierz **projekt w bieżącym rozwiązaniu**. W **projektu** , wybierz nazwę projektu.

    -   Jeśli zestawu rozszerzeń jest uwzględniany jako plik w projekcie, wybierz opcję **plików w systemie plików**. W **ścieżki** liście, wprowadź pełną ścieżkę do pliku zestawu rozszerzenia lub używanie **Przeglądaj** przycisk, aby zlokalizować i wybierz plik zestawu.

5.  Wybierz **OK** przycisku.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Aby dołączyć do zestawu poleceń programu SharePoint

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz** przycisku.

     Plik zostanie otwarty w projektancie.

2.  W **zasoby** sekcji edytora, wybierz **New** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

3.  W **typu** wprowadź **SharePoint.Commands.v4**.

4.  W **źródła** listy, wykonaj jedną z następujących czynności:

    -   Jeśli zestaw polecenia jest zbudowany z projektu, który znajduje się w tym samym rozwiązaniu co projekt VSIX, wybierz opcję **projekt w bieżącym rozwiązaniu**. W **projektu** , wybierz nazwę projektu.

    -   Jeśli zestaw poleceń jest uwzględniany jako plik w projekcie, wybierz opcję **plików w systemie plików**. W **ścieżki** liście, wprowadź pełną ścieżkę do pliku zestawu rozszerzenia lub używanie **Przeglądaj** przycisk, aby zlokalizować i wybierz plik zestawu.

5.  Wybierz **OK** przycisku.

#### <a name="to-include-a-template-that-you-create"></a>Aby uwzględnić utworzonego szablonu

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz** przycisku.

     Plik zostanie otwarty w projektancie.

2.  W **zasoby** sekcji edytora, wybierz **New** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.ProjectTemplate** lub **Microsoft.VisualStudio.ItemTemplate**.

4.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

5.  W **projektu** , wybierz nazwę projektu, a następnie wybierz **OK** przycisku.

6.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu szablonu projektu lub elementu szablonu, a następnie wybierz **Zwolnij projekt**.

7.  Ponownie otwórz menu skrótów dla węzła projektu, a następnie wybierz **Edytuj**_YourTemplateProjectName_**.csproj** lub **Edytuj**  _YourTemplateProjectName_**.vbproj**.

8.  Znajdź następujące `VSTemplate` elementu w pliku projektu.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Zamień ten element na następujący kod XML.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Element określa dodatkowe foldery w ścieżce, w którym tworzony jest szablon projektu podczas kompilowania projektu. Foldery określone w tym miejscu, upewnij się, że szablon elementu będą dostępne tylko wtedy, gdy klienci otworzyć **Dodaj nowy projekt** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010**  węzła.

10. Zapisz i zamknij plik.

11. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu szablonu projektu lub szablon elementu, a następnie wybierz **Załaduj ponownie projekt**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Aby uwzględnić szablon, który można tworzyć ręcznie

1.  W projekcie VSIX należy dodać nowy folder do projektu, który ma zawierać szablon.

2.  W tym folderze nowe, utwórz następujące podfoldery, a następnie dodaj plik szablonu (.zip) do *identyfikator ustawień regionalnych* folderu.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *Identyfikator ustawień regionalnych*

     *YourTemplateName*zip

     Na przykład, jeśli szablon elementu o nazwie ContosoCustomAction.zip, który obsługuje ustawień regionalnych języka angielskiego (Stany Zjednoczone), pełna ścieżka może być *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3.  W **Eksploratora rozwiązań**, wybierz plik szablonu (*YourTemplateName*zip).

4.  W **właściwości** oknie **Build Action** właściwości **zawartości**.

5.  Otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz**.

     Plik zostanie otwarty w projektancie.

6.  W **zasoby** sekcji edytora, wybierz **New** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

7.  W **typu** wybierz **Microsoft.VisualStudio.ItemTemplate** lub **Microsoft.VisualStudio.ProjectTemplate**.

8.  W **źródła** wybierz **plików w systemie plików**.

9. W **ścieżki** wprowadź pełną ścieżkę do zestawu (na przykład *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, lub użyj **Przeglądaj**przycisk, aby zlokalizować, a następnie wybierz zestaw, a następnie wybierz **OK** przycisku.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Aby uwzględnić Kreator szablonu projektu lub elementu szablonu

1.  W projekcie VSIX, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz**.

     Plik zostanie otwarty w projektancie.

2.  W **zasoby** sekcji edytora, wybierz **New** przycisku.

     **Dodaj nowy zasób** zostanie otwarte okno dialogowe.

3.  W **typu** wybierz **Microsoft.VisualStudio.Assembly**.

4.  W **źródła** listy, wykonaj jedną z następujących czynności:

    -   Jeśli zestaw kreatora jest zbudowany z projektu, który znajduje się w tym samym rozwiązaniu co projekt VSIX, wybierz opcję **projekt w bieżącym rozwiązaniu**. W **projektu** , wybierz nazwę projektu.

    -   Jeśli zestaw kreatora jest uwzględniany jako plik w projekcie, wybierz opcję **plików w systemie plików**. W **ścieżki** pole, wprowadź pełną ścieżkę do pliku zestawu lub używanie **Przeglądaj** przycisk, aby znaleźć i wybrać zestaw.

5.  Wybierz **OK** przycisku.

### <a name="related-walkthroughs"></a>Pokrewne instruktaże

W poniższej tabeli wymieniono instruktaży, które pokazują, jak użyć projektu VSIX do wdrożenia różnych rodzajów rozszerzenia narzędzi programu SharePoint.

|Typ rozszerzenia|Pokrewne instruktaże|
|--------------------|--------------------------|
|Rozszerzenie, które zawiera tylko zestawu rozszerzeń|[Przewodnik: Rozszerzanie typu elementu projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Przewodnik: Tworzenie rozszerzenia projektu SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Przewodnik: Wywołania w modelu obiektu klienta SharePoint w rozszerzeniu Eksploratora serwera](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Rozszerzenie, które zawiera polecenia programu SharePoint|[Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Przewodnik: Rozszerzanie Eksploratora serwera na potrzeby wyświetlania składników web Part](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Rozszerzenie, które zawiera szablon programu Visual Studio|[Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Rozszerzenie, które zawiera Kreatora szablonu|[Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Przewodnik: Tworzenie elementu projektu kolumn witryny z szablonem projektu — część 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Ręczne tworzenie pakietów VSIX

Jeśli chcesz ręcznie utworzyć pakiet VSIX dla rozszerzenia narzędzi programu SharePoint, wykonaj następujące czynności:

1.  Tworzenie pliku extension.vsixmanifest i pliku [Content_Types] .xml w nowym folderze. Aby uzyskać więcej informacji, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2.  W Eksploratorze Windows kliknij prawym przyciskiem myszy folder, który zawiera dwa pliki XML, kliknij przycisk Wyślij do, a następnie kliknij Folder skompresowany (zip). Zmień nazwę wynikowy plik zip na Filename.vsix, gdzie nazwa_pliku to nazwa pliku pakietu redystrybucyjnego, który instaluje pakiet.

3.  Dodaj zestaw rozszerzeń do pakietu VSIX. Jeśli rozszerzenie zawiera polecenia programu SharePoint, należy również dodać zestaw, który implementuje polecenie programu SharePoint, aby pakiet VSIX.

4.  Zmodyfikuj plik extension.vsixmanifest:

    -   Dodaj `Microsoft.VisualStudio.MefComponent` pod `Assets` elementu, a następnie ustaw wartość nowego elementu do ścieżki względnej zestawu, który implementuje rozszerzenie w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    -   Jeśli rozszerzenie zawiera polecenia programu SharePoint, która wywołuje w modelu obiektów serwera dla programu SharePoint, należy dodać `Microsoft.VisualStudio.Assembly` pod `Assets` elementu. Ustaw wartość nowego elementu względną ścieżkę zestawu, który implementuje polecenie programu SharePoint w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [zawartości elementu (schemat VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    -   Jeśli rozszerzenie zawiera szablon projektu lub elementu szablonu, należy dodać `ProjectTemplate` lub `ItemTemplate` pod `Assets` elementu. Ustaw wartość nowego elementu względną ścieżkę folderu, który zawiera szablon w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [ProjectTemplate — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) i [elementów właściwości ItemTemplate (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    -   Jeśli rozszerzenie zawiera Kreatora niestandardowego szablonu projektu lub elementu szablonu, należy dodać `Assembly` pod `Assets` elementu. Ustaw wartość nowego elementu na ścieżkę względną zestawu w pakiecie VSIX, a następnie ustaw `AssemblyName` atrybutu nazwy pełnego zestawu (w tym wersji, kulturę i token klucza publicznego). Aby uzyskać więcej informacji, zobacz [Element zależności (schemat VSX)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje zawartość pliku extension.vsixmanifest dla rozszerzenia narzędzi programu SharePoint. Rozszerzenie jest implementowane w zestawie, który nosi nazwę Contoso.ProjectExtension.dll. Rozszerzenie zawiera zestaw poleceń programu SharePoint, który nosi nazwę Contoso.ExtensionCommands.dll i szablon elementu w folderze o nazwie **elementów** w pakiecie VSIX. W tym przykładzie przyjęto założenie, że oba zestawy znajdują się w tym samym folderze co plik extension.vsixmanifest w pakiecie VSIX.

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

- [Rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Rozszerzanie węzła połączeń SharePoint w Eksploratorze serwera](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Debugowanie rozszerzeń dla narzędzi SharePoint w programie Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
