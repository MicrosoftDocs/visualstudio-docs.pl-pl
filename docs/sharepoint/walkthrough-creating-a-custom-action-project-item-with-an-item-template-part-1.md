---
title: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu — część 1
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e00d87079fe4986dc378540c1456508c2afa0b7
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401115"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 1
  Możesz rozszerzyć systemu projektu programu SharePoint w programie Visual Studio, tworząc własny projekt typów elementów. W tym instruktażu utworzysz element projektu, który można dodać do projektu programu SharePoint w celu utworzenia akcji niestandardowej w witrynie programu SharePoint. Akcja niestandardowa dodaje element menu do **Akcje witryny** menu witryny programu SharePoint.

 W tym instruktażu pokazano następujące zagadnienia:

- Tworzenie rozszerzenia programu Visual Studio, który definiuje nowy typ elementu projektu programu SharePoint dla akcji niestandardowej. Nowy typ elementu projektu implementuje kilka niestandardowych funkcji:

  - Menu skrótów, która służy jako punkt początkowy dla dodatkowych zadań związanych z elementu projektu, takich jak wyświetlanie projektanta dla akcji niestandardowej w programie Visual Studio.

  - Kod, który jest uruchamiany, gdy deweloper zmiany niektórych właściwości elementu projektu i projektu, który go zawiera.

  - Ikony niestandardowej, która pojawia się obok elementu projektu w **Eksploratora rozwiązań**.

- Tworzenie szablonu elementu programu Visual Studio dla elementu projektu.

- Tworzenie pakietu Visual Studio rozszerzenia (VSIX) do wdrożenia szablonu elementu projektu i zestawu rozszerzeń.

- Debugowanie i testowanie elementu projektu.

  Jest to przewodnik autonomicznej. Po ukończeniu tego przewodnika, można zwiększyć elementu projektu, dodając Kreatora szablonu elementu. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Możesz pobrać próbkę z [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) pokazujący sposób tworzenia działań niestandardowych do przepływu pracy.

## <a name="prerequisites"></a>Wymagania wstępne
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows, SharePoint i Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:

- Akcje niestandardowe w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa](http://go.microsoft.com/fwlink/?LinkId=177800).

- Szablony elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [tworzenie projektów i szablonów elementów](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, musisz utworzyć trzy projekty:

- A VSIX project. Ten projekt tworzy pakiet VSIX do wdrożenia elementu projektu programu SharePoint.

- Element projektu szablonu. Ten projekt tworzy szablon elementu, który może służyć do dodawania elementu projektu programu SharePoint do projektu programu SharePoint.

- Projekt biblioteki klas. Ten projekt implementuje rozszerzenie programu Visual Studio, która definiuje zachowanie elementu projektu programu SharePoint.

  Instruktaż należy rozpocząć od utworzenia projektów.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz **pliku** > **New** > **projektu**.

3. Na liście u góry **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest zaznaczone.

4. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności** węzła.

    > [!NOTE]
    > **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.

5. Wybierz **projekt VSIX** szablonu.

6. W **nazwa** wprowadź **CustomActionProjectItem**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **CustomActionProjectItem** projekt **Eksploratora rozwiązań**.

#### <a name="to-create-the-item-template-project"></a>Aby utworzyć projekt szablonu elementu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2. Na liście u góry **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest zaznaczone.

3. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności** węzła.

4. Na liście szablonów projektu wybierz **szablon elementu języka C#** lub **szablon elementu języka Visual Basic** szablonu.

5. W **nazwa** wprowadź **właściwości ItemTemplate**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **właściwości ItemTemplate** projektu do rozwiązania.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.

2. Na liście u góry **nowy projekt** okna dialogowego pole, upewnij się, że **.NET Framework 4.5** jest zaznaczone.

3. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** Wybierz węzły, **Windows** węzła, a następnie wybierz polecenie  **Biblioteka klas** szablonu projektu.

4. W **nazwa** wprowadź **ProjectItemDefinition**, a następnie wybierz **OK** przycisku.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ProjectItemDefinition** projektu do rozwiązania i otwiera plik domyślny kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Konfigurowanie projektu rozszerzenia
 Przed przystąpieniem do napisania kod, aby zdefiniować typ elementu projektu SharePoint, trzeba dodać pliki kodu i odwołania do zestawów do projektu rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProjectItemDefinition** projektu, wybierz **Dodaj**, następnie wybierz **nowy element**.

2. Na liście elementów projektu, wybierz opcję **pliku z kodem**.

3. W **nazwa** wprowadź nazwę **Akcja niestandardowa** z odpowiednie rozszerzenie nazwy pliku, a następnie wybierz **Dodaj** przycisku.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProjectItemDefinition** projektu, a następnie wybierz **Dodaj odwołanie**.

5. W **Menadżer odwołań - ProjectItemDefinition** okna dialogowego wybierz **zestawy** węzła, a następnie wybierz **Framework** węzła.

6. Zaznacz pole wyboru obok każdego następujących zestawów:

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Wybierz **rozszerzenia** węzeł, zaznacz pole wyboru obok zestawu Microsoft.VisualStudio.Sharepoint, a następnie wybierz **OK** przycisku.

## <a name="define-the-new-sharepoint-project-item-type"></a>Definiowanie nowego typu elementu projektu SharePoint
 Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfejsu do określania zachowania nowym typem elementu projektu. Zawsze, gdy chcesz zdefiniować nowy typ elementu projektu, należy zaimplementować ten interfejs.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Aby zdefiniować nowym typem elementu projektu SharePoint

1. W projekcie ProjectItemDefinition Otwórz plik kodu Akcja niestandardowa.

2. Zastąp kod w tym pliku następującym kodem.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Tworzenie ikony dla elementu projektu w Eksploratorze rozwiązań
 Podczas tworzenia niestandardowego elementu projektu programu SharePoint obrazu (ikony lub mapy bitowej) można skojarzyć z elementem projektu. Ten obraz, który pojawia się obok elementu projektu w **Eksploratora rozwiązań**.

 W poniższej procedurze należy utworzyć ikonę dla elementu projektu i osadzić ikonę w zestawu rozszerzeń. Odwołuje się ta ikona <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> z `CustomActionProjectItemTypeProvider` klasę, która została utworzona wcześniej.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Aby utworzyć ikony niestandardowej dla elementu projektu

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProjectItemDefinition** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element...** .

2. Na liście elementów projektu, wybierz opcję **plik ikony** elementu.

    > [!NOTE]
    > W projektach języka Visual Basic, musisz wybrać **ogólne** węzeł, aby wyświetlić **plik ikony** elementu.

3. W **nazwa** wprowadź **CustomAction_SolutionExplorer.ico**, a następnie wybierz **Dodaj** przycisku.

     Nowa ikona otwiera się w **edytora obrazów**.

4. Tak, aby miało projektu może rozpoznać, a następnie zapisz plik ikony, należy edytować plik ikony w wersji 16 x 16.

5. W **Eksploratora rozwiązań**, wybierz **CustomAction_SolutionExplorer.ico**.

6. W **właściwości** okna, wybierz strzałkę obok **Build Action** właściwości.

7. Na wyświetlonej liście wybierz **zasób osadzony**.

## <a name="checkpoint"></a>Punkt kontrolny
 W tym momencie w instruktażu, cały kod dla elementu projektu jest teraz w projekcie. Skompiluj projekt, aby sprawdzić, czy kompiluje bez błędów.

#### <a name="to-build-your-project"></a>Do kompilowania projektu

1. Otwórz menu skrótów dla **ProjectItemDefinition** projektu, a następnie wybierz **kompilacji**.

## <a name="create-a-visual-studio-item-template"></a>Tworzenie szablonu elementu programu Visual Studio
 Aby włączyć innych deweloperzy mogą używać element projektu, należy utworzyć szablon projektu lub szablon elementu. Deweloperzy używać tych szablonów w programie Visual Studio do utworzenia wystąpienia elementu projektu, tworząc nowy projekt lub poprzez dodanie elementu do istniejącego projektu. W ramach tego przewodnika należy użyć projektu właściwości ItemTemplate skonfigurować element projektu.

#### <a name="to-create-the-item-template"></a>Aby utworzyć szablon elementu

1. Usuń plik kodu Class1 z projektu właściwości ItemTemplate.

2. W projekcie właściwości ItemTemplate Otwórz *ItemTemplate.vstemplate* pliku.

3. Zastąp zawartość pliku następujący kod XML, a następnie zapisz i zamknij plik.

    > [!NOTE]
    > Następujący kod XML jest szablon elementu Visual C#. Jeśli tworzysz szablon elementu języka Visual Basic, zastąp wartość `ProjectType` element z `VisualBasic`.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Ten plik definiuje zawartości i zachowania szablon elementu. Aby uzyskać więcej informacji o zawartości tego pliku, zobacz [odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference).

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **właściwości ItemTemplate** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

5. W **Dodaj nowy element** okna dialogowego wybierz **plik tekstowy** szablonu.

6. W **nazwa** wprowadź **CustomAction.spdata**, a następnie wybierz **Dodaj** przycisku.

7. Dodaj następujący kod XML do *CustomAction.spdata* pliku, a następnie zapisz i zamknij plik.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Ten plik zawiera informacje o plikach, które znajdują się elementu projektu. `Type` Atrybutu `ProjectItem` element musi być ustawiony na ten sam ciąg, który jest przekazywany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> w definicji elementu projektu ( `CustomActionProjectItemTypeProvider` klasy utworzonej we wcześniejszej części tego przewodnika). Aby uzyskać więcej informacji na temat zawartości *spdata* plików, zobacz [odwołanie do schematu elementu projektu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **właściwości ItemTemplate** projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

9. W **Dodaj nowy element** okna dialogowego wybierz **pliku XML** szablonu.

10. W **nazwa** wprowadź **Elements.xml**, a następnie wybierz **Dodaj** przycisku.

11. Zastąp zawartość *Elements.xml* plików z następujących XML, a następnie zapisz i zamknij plik.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     Ten plik definiuje niestandardową akcję domyślną, która tworzy element menu na **Akcje witryny** menu witryny programu SharePoint. Gdy użytkownik wybierze element menu, adres URL określony w `UrlAction` element zostanie otwarta w przeglądarce sieci web. Aby uzyskać więcej informacji o elementach języka XML, można użyć do zdefiniowania akcji niestandardowej, zobacz [niestandardowe definicje akcji](http://go.microsoft.com/fwlink/?LinkId=177801).

12. Opcjonalnie można otworzyć *ItemTemplate.ico* pliku i zmodyfikuj go tak, aby miało projekt, który można rozpoznać. Ta ikona pojawi się obok elementu projektu w **Dodaj nowy element** okno dialogowe.

13. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **właściwości ItemTemplate** projektu, a następnie wybierz **Zwolnij projekt**.

14. Otwórz menu skrótów dla **właściwości ItemTemplate** ponownie projekt, a następnie wybierz **Edytuj ItemTemplate.csproj** lub **Edytuj ItemTemplate.vbproj**.

15. Znajdź następujące `VSTemplate` elementu w pliku projektu.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Zastąp to `VSTemplate` element z następujący kod XML, a następnie zapisz i zamknij plik.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` Element określa dodatkowe foldery w ścieżce, w którym szablon elementu jest tworzony podczas kompilowania projektu. Foldery określone w tym miejscu, upewnij się, że szablon elementu będą dostępne tylko wtedy, gdy klienci otworzyć **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010**  węzła.

17. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **właściwości ItemTemplate** projektu, a następnie wybierz **Załaduj ponownie projekt**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Utwórz pakiet VSIX do wdrożenia elementu projektu
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu Aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest, który znajduje się w projekcie VSIX. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **source.extension.vsixmanifest** plik w projekcie CustomActionProjectItem, a następnie wybierz **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu. Plik source.extension.vsixmanifest jest podstawą dla pliku extension.vsixmanifest, które wymagają wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W **nazwa produktu** wprowadź **niestandardowych akcji elementu projektu**.

3. W **Autor** wprowadź **Contoso**.

4. W **opis** wprowadź **elementu projektu programu SharePoint, która reprezentuje akcję niestandardową**.

5. Na **zasoby** kartę, wybrać **New** przycisku.

     **Dodaj nowy zasób** pojawi się okno dialogowe.

6. W **typu** wybierz **Microsoft.VisualStudio.ItemTemplate**.

    > [!NOTE]
    > Ta wartość odpowiada `ItemTemplate` elementu w pliku extension.vsixmanifest. Ten element umożliwia określenie podfolderu w pakiecie VSIX, zawierający szablonu elementu projektu. Aby uzyskać więcej informacji, zobacz [elementów właściwości ItemTemplate (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

8. W **projektu** wybierz **właściwości ItemTemplate**, a następnie wybierz **OK** przycisku.

9. W **zasoby** kartę, wybrać **New** ponownie przycisk.

     **Dodaj nowy zasób** pojawi się okno dialogowe.

10. W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.

12. W **projektu** wybierz **ProjectItemDefinition**.

13. Wybierz **OK** przycisku.

14. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt kompiluje bez błędów.

15. Upewnij się, że folder wyjściowy kompilacji dla projektu CustomActionProjectItem zawiera plik CustomActionProjectItem.vsix.

     Domyślnie folderem wyjściowym kompilacji jest... folderze \bin\Debug w folderze, który zawiera projekt CustomActionProjectItem.

## <a name="test-the-project-item"></a>Testowanie elementu projektu
 Teraz można przystąpić do przetestowania elementu projektu. Po pierwsze uruchom debugowanie rozwiązania CustomActionProjectItem w doświadczalnym wystąpieniu programu Visual Studio. Następnie sprawdź **Akcja niestandardowa** elementu projektu w projekcie programu SharePoint w doświadczalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i uruchom projekt programu SharePoint, aby sprawdzić, czy akcja niestandardowa działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1. Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie CustomActionProjectItem.

2. Otwórz plik kodu Akcja niestandardowa, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `InitializeType` metody.

3. Wybierz **F5** klawisz, aby rozpocząć debugowanie.

     Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 projektu działanie i uruchamia doświadczalne wystąpienie programu Visual Studio. Element projektu będzie testu, w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Aby przetestować element projektu w programie Visual Studio

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** (w zależności od języka obsługującego szablonu elementu), rozwiń węzeł **SharePoint**, a następnie wybierz **2010**  węzła.

3. Na liście szablonów projektu wybierz **projekt programu SharePoint 2010**.

4. W **nazwa** wprowadź **CustomActionTest**, a następnie wybierz **OK** przycisku.

5. W **Kreator ustawień niestandardowych SharePoint**, wprowadź adres URL witryny, której chcesz używać do debugowania, a następnie wybierz **Zakończ** przycisku.

6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła projektu, wybierz pozycję **Dodaj**, a następnie wybierz **nowy element**.

7. W **Dodaj nowy element** okna dialogowego wybierz **2010** węźle **SharePoint** węzła.

     Upewnij się, że **Akcja niestandardowa** element będzie wyświetlany na liście elementów projektu.

8. Wybierz **Akcja niestandardowa** elementu, a następnie wybierz **Dodaj** przycisku.

     Program Visual Studio dodaje element o nazwie **CustomAction1** do projektu i otwiera *Elements.xml* plik w edytorze.

9. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `InitializeType` metody.

10. Wybierz **F5** klawisz, aby kontynuować debugowanie projektu.

11. W doświadczalnym wystąpieniu programu Visual Studio w **Eksploratora rozwiązań**, otwórz menu skrótów dla **CustomAction1** węzła, a następnie wybierz **Projektant akcji niestandardowych widoków**.

12. Sprawdź, czy pojawi się okno komunikatu, a następnie wybierz **OK** przycisku.

     Aby zapewnić dodatkowe opcje lub polecenia dla deweloperów, takie jak wyświetlanie projektanta dla akcji niestandardowej, można użyć tego menu skrótów.

13. Na pasku menu wybierz **widoku** > **dane wyjściowe**.

     **Dane wyjściowe** zostanie otwarte okno.

14. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CustomAction1** elementu, a następnie zmień jego nazwę na **MyCustomAction**.

     W **dane wyjściowe** pojawi się komunikat z potwierdzeniem w oknie. Ta wiadomość została zapisana przy <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> programu obsługi zdarzeń, które zostały zdefiniowane w `CustomActionProjectItemTypeProvider` klasy. Może obsługiwać to zdarzenie i inne zdarzenia element projektu do zaimplementowania niestandardowe zachowanie, gdy deweloper modyfikuje element projektu.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Aby przetestować akcji niestandardowej w programie SharePoint

1. W doświadczalnym wystąpieniu programu Visual Studio, otwórz *Elements.xml* pliku, który jest elementem podrzędnym **MyCustomAction** elementu projektu.

2. W *Elements.xml* pliku, dokonaj następujących zmian, a następnie zapisz plik:

    - W `CustomAction` elementu, ustaw `Id` atrybutu identyfikatora GUID lub unikatowego ciągu, jak w poniższym przykładzie pokazano:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - W `CustomAction` elementu, ustaw `Title` atrybut, co ilustruje poniższy przykład:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - W `CustomAction` elementu, ustaw `Description` atrybut, co ilustruje poniższy przykład:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - W `UrlAction` elementu, ustaw `Url` atrybut, co ilustruje poniższy przykład:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Wybierz **F5** klucza.

     Akcja niestandardowa zostaje spakowany i wdrożyć w witrynie programu SharePoint, który jest określony w **adres URL witryny** właściwość projektu. Przeglądarka sieci web zostanie otwarta domyślna strona tej lokacji.

    > [!NOTE]
    > Jeśli **wyłączenia debugowania skryptu** pojawi się okno dialogowe, wybierz **tak** przycisk, aby kontynuować debugowanie projektu.

4. Na **Akcje witryny** menu, wybierz **Centrum deweloperów programu SharePoint**, sprawdź, czy witryny sieci Web zostanie otwarta przeglądarka https://docs.microsoft.com/sharepoint/dev/, a następnie zamknij przeglądarkę sieci web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu badania elementu projektu, należy usunąć szablonu elementu projektu w doświadczalnym wystąpieniu programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputerze deweloperskim

1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2. Na liście rozszerzeń wybierz **niestandardowych akcji elementu projektu**, a następnie wybierz **Odinstaluj** przycisku.

3. W oknie dialogowym wybierz **tak** przycisk, aby upewnić się, że chcesz odinstalować rozszerzenie.

4. Wybierz **Uruchom ponownie teraz** przycisk, aby ukończyć dezinstalację.

5. Zamknij zarówno w doświadczalnym wystąpieniu programu Visual Studio, jak i wystąpienia, w którym rozwiązanie CustomActionProjectItem jest otwarty.

## <a name="next-steps"></a>Następne kroki
 Po ukończeniu tego przewodnika kreatora można dodać do szablonu elementu. Gdy użytkownik doda Akcja niestandardowa elementu projektu do projektu programu SharePoint, Kreator zbiera informacje o akcji (na przykład lokalizacji i adres URL, aby przejść do po wybraniu akcji) i dodaje te informacje do *Elements.xml*plików do nowego elementu projektu. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie niestandardowej akcji elementu projektu z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu programu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
- [Tworzenie ikony lub innego obrazu &#40;edytor obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)