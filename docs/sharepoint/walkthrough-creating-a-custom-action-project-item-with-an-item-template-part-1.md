---
title: Utwórz niestandardowy element projektu akcji z szablonem elementu, część 1
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
ms.openlocfilehash: 4a114345363deb9c5ddd0f5a4141cd7d99f0ac1c
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189182"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 1
  Można zwiększyć system projektu programu SharePoint w programie Visual Studio, tworząc własne typy elementów projektu. W tym instruktażu utworzysz element projektu, który można dodać do projektu programu SharePoint, aby utworzyć akcję niestandardową w witrynie programu SharePoint. Akcja niestandardowa dodaje element menu do menu **Akcje witryny** w witrynie programu SharePoint.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie rozszerzenia programu Visual Studio, które definiuje nowy typ elementu projektu programu SharePoint dla akcji niestandardowej. Nowy typ elementu projektu implementuje kilka funkcji niestandardowych:

  - Menu skrótów, które służy jako punkt wyjścia dla dodatkowych zadań związanych z elementem projektu, takich jak wyświetlanie projektanta dla akcji niestandardowej w programie Visual Studio.

  - Kod, który jest uruchamiany, gdy deweloper zmieni pewne właściwości elementu projektu i projektu, który go zawiera.

  - Ikona niestandardowa, która pojawia się obok elementu projektu w **Eksplorator rozwiązań**.

- Tworzenie szablonu elementu programu Visual Studio dla elementu projektu.

- Kompilowanie pakietu rozszerzenia Visual Studio (VSIX) w celu wdrożenia szablonu elementu projektu i zestawu rozszerzeń.

- Debugowanie i testowanie elementu projektu.

  Jest to przewodnik samodzielny. Po zakończeniu tego instruktażu można wzbogacić element projektu, dodając kreatora do szablonu elementu. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Możesz pobrać przykład z witryny [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) , który pokazuje, jak utworzyć niestandardowe działania dla przepływu pracy.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Microsoft Windows, SharePoint i Visual Studio.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia elementu projektu. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Akcje niestandardowe w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Akcja niestandardowa](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Szablony elementów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten przewodnik, należy utworzyć trzy projekty:

- Projekt VSIX. Ten projekt tworzy pakiet VSIX do wdrożenia elementu projektu programu SharePoint.

- Projekt szablonu elementu. Ten projekt tworzy szablon elementu, którego można użyć do dodania elementu projektu programu SharePoint do projektu programu SharePoint.

- Projekt biblioteki klas. Ten projekt implementuje rozszerzenie programu Visual Studio, które definiuje zachowanie elementu projektu programu SharePoint.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz kolejno pozycje **plik**  > **Nowy**  > **projekt**.

3. Upewnij się, że na liście u góry okna dialogowego **Nowy projekt** jest zaznaczone pole wyboru **.NET Framework 4,5** .

4. W oknie dialogowym **Nowy projekt** rozwiń węzły **wizualizacji C#**  lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

    > [!NOTE]
    > Węzeł **rozszerzalności** jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

5. Wybierz szablon **projektu VSIX** .

6. W polu **Nazwa** wprowadź **CustomActionProjectItem**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **CustomActionProjectItem** do **Eksplorator rozwiązań**.

#### <a name="to-create-the-item-template-project"></a>Aby utworzyć projekt szablonu elementu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. Upewnij się, że na liście u góry okna dialogowego **Nowy projekt** jest zaznaczone pole wyboru **.NET Framework 4,5** .

3. W oknie dialogowym **Nowy projekt** rozwiń węzły **wizualizacji C#**  lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

4. Na liście szablonów projektu wybierz szablon  **C# elementu** szablonu lub szablon szablonu **Visual Basic** .

5. W polu **Nazwa** wprowadź **ItemTemplate**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **ItemTemplate** do rozwiązania.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. Upewnij się, że na liście u góry okna dialogowego **Nowy projekt** jest zaznaczone pole wyboru **.NET Framework 4,5** .

3. W oknie **dialogowym Nowy projekt** rozwiń węzły  **C# wizualizacji** lub **Visual Basic** , wybierz węzeł **systemu Windows** , a następnie wybierz szablon projektu **Biblioteka klas** .

4. W polu **Nazwa** wprowadź **ProjectItemDefinition**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **ProjectItemDefinition** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-extension-project"></a>Skonfiguruj projekt rozszerzenia
 Przed napisaniem kodu w celu zdefiniowania typu elementu projektu programu SharePoint należy dodać pliki kodu i odwołania do zestawu do projektu rozszerzenia.

#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProjectItemDefinition** , wybierz **Dodaj**, a następnie wybierz **nowy element**.

2. Na liście elementów projektu wybierz pozycję **plik kodu**.

3. W polu **Nazwa** wprowadź wartość Nazwa wystąpienia z odpowiednim **rozszerzeniem nazwy pliku** , a następnie wybierz przycisk **Dodaj** .

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProjectItemDefinition** , a następnie wybierz **Dodaj odwołanie**.

5. W oknie dialogowym **Menedżer odwołań — ProjectItemDefinition** wybierz węzeł **zestawy** , a następnie wybierz węzeł **Struktura** .

6. Zaznacz pole wyboru obok każdego z następujących zestawów:

    - System. ComponentModel. kompozycji

    - System. Windows. Forms

7. Wybierz węzeł **rozszerzenia** , zaznacz pole wyboru obok zestawu Microsoft. VisualStudio. SharePoint, a następnie wybierz przycisk **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Zdefiniuj nowy typ elementu projektu programu SharePoint
 Utwórz klasę, która implementuje interfejs <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, aby zdefiniować zachowanie nowego typu elementu projektu. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zdefiniować nowy typ elementu projektu.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Aby zdefiniować nowy typ elementu projektu programu SharePoint

1. W projekcie ProjectItemDefinition Otwórz plik kodu.

2. Zastąp kod w tym pliku następującym kodem.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Utwórz ikonę dla elementu projektu w Eksplorator rozwiązań
 Podczas tworzenia niestandardowego elementu projektu programu SharePoint można skojarzyć obraz (ikonę lub mapę bitową) z elementem projektu. Ten obraz pojawia się obok elementu projektu w **Eksplorator rozwiązań**.

 W poniższej procedurze utworzysz ikonę dla elementu projektu i osadzisz ikonę w zestawie rozszerzeń. Do tej ikony odwołuje się <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> klasy `CustomActionProjectItemTypeProvider`, która została utworzona wcześniej.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Aby utworzyć niestandardową ikonę dla elementu projektu

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProjectItemDefinition** , wybierz **Dodaj**, a następnie wybierz **nowy element.** ...

2. Na liście elementów projektu wybierz pozycję **plik ikony** .

    > [!NOTE]
    > W projektach Visual Basic należy wybrać węzeł **Ogólne** , aby wyświetlić element **ikony** elementu.

3. W polu **Nazwa** wprowadź **CustomAction_SolutionExplorer. ico**, a następnie wybierz przycisk **Dodaj** .

     Nowa ikona zostanie otwarta w **Edytorze obrazu**.

4. Edytuj wersję 16x16 pliku ikony, aby można było rozpoznać projekt, a następnie Zapisz plik ikony.

5. W **Eksplorator rozwiązań**wybierz **CustomAction_SolutionExplorer. ico**.

6. W oknie **Właściwości** wybierz strzałkę obok właściwości **Akcja kompilacji** .

7. Na wyświetlonej liście wybierz pozycję **zasób osadzony**.

## <a name="checkpoint"></a>Elementu
 W tym momencie w przewodniku cały kod elementu projektu jest teraz w projekcie. Skompiluj projekt, aby upewnić się, że kompiluje się bez błędów.

#### <a name="to-build-your-project"></a>Aby skompilować projekt

1. Otwórz menu skrótów dla projektu **ProjectItemDefinition** i wybierz polecenie **Kompiluj**.

## <a name="create-a-visual-studio-item-template"></a>Utwórz szablon elementu programu Visual Studio
 Aby umożliwić innym deweloperom korzystanie z elementu projektu, należy utworzyć szablon projektu lub szablonu elementu. Deweloperzy używają tych szablonów w programie Visual Studio, aby utworzyć wystąpienie elementu projektu przez utworzenie nowego projektu lub poprzez dodanie elementu do istniejącego projektu. W tym instruktażu należy użyć projektu ItemTemplate, aby skonfigurować element projektu.

#### <a name="to-create-the-item-template"></a>Aby utworzyć szablon elementu

1. Usuń plik kodu Class1 z projektu ItemTemplate.

2. W projekcie ItemTemplate Otwórz plik *ItemTemplate. vstemplate* .

3. Zastąp zawartość pliku następującym kodem XML, a następnie Zapisz i zamknij plik.

    > [!NOTE]
    > Poniższy kod XML jest przeznaczony dla szablonu C# elementu wizualnego. Jeśli tworzysz szablon elementu Visual Basic, Zastąp wartość elementu `ProjectType` elementem `VisualBasic`.

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

     Ten plik definiuje zawartość i zachowanie szablonu elementu. Aby uzyskać więcej informacji na temat zawartości tego pliku, zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ItemTemplate** , wybierz **Dodaj**, a następnie wybierz **nowy element**.

5. W oknie dialogowym **Dodaj nowy element** wybierz szablon **plik tekstowy** .

6. W polu **Nazwa** wprowadź wartość **un. spdata**, a następnie wybierz przycisk **Dodaj** .

7. Dodaj następujący kod XML do pliku *. spdata* , a następnie Zapisz i zamknij plik.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Ten plik zawiera informacje o plikach, które są zawarte w elemencie projektu. Atrybut `Type` elementu `ProjectItem` musi być ustawiony na ten sam ciąg, który jest przesyłany do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> w definicji elementu projektu (Klasa `CustomActionProjectItemTypeProvider` utworzona wcześniej w tym instruktażu). Aby uzyskać więcej informacji o zawartości plików *. spdata* , zobacz [Dokumentacja schematu elementu projektu programu SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ItemTemplate** , wybierz **Dodaj**, a następnie wybierz **nowy element**.

9. W oknie dialogowym **Dodaj nowy element** wybierz szablon **pliku XML** .

10. W polu **Nazwa** wprowadź wartość **elementy. XML**, a następnie wybierz przycisk **Dodaj** .

11. Zastąp zawartość pliku repliks *. XML* następującym kodem XML, a następnie Zapisz i zamknij plik.

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

     Ten plik definiuje domyślną akcję niestandardową, która tworzy element menu w menu **Akcje witryny** w witrynie programu SharePoint. Gdy użytkownik wybierze element menu, adres URL określony w `UrlAction` elementu zostanie otwarty w przeglądarce sieci Web. Aby uzyskać więcej informacji na temat elementów XML, których można użyć do zdefiniowania akcji niestandardowej, zobacz [niestandardowe definicje akcji](/sharepoint/dev/schema/custom-action-definition-schema).

12. Opcjonalnie Otwórz plik *ItemTemplate. ico* i zmodyfikuj go tak, aby miał projekt, który można rozpoznać. Ta ikona będzie wyświetlana obok elementu projektu w oknie dialogowym **Dodaj nowy element** .

13. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ItemTemplate** , a następnie wybierz polecenie **Zwolnij projekt**.

14. Otwórz menu skrótów dla projektu **ItemTemplate** , a następnie wybierz polecenie **Edytuj ItemTemplate. csproj** lub **Edytuj ItemTemplate. vbproj**.

15. Znajdź Poniższy `VSTemplate` element w pliku projektu.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Zastąp ten `VSTemplate` element następującym kodem XML, a następnie Zapisz i zamknij plik.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     `OutputSubPath` element określa dodatkowe foldery w ścieżce, w której szablon elementu jest tworzony podczas kompilowania projektu. Foldery określone w tym miejscu zapewniają, że szablon elementu będzie dostępny tylko wtedy, gdy klienci otworzą okno dialogowe **Dodaj nowy element** , rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

17. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ItemTemplate** , a następnie wybierz polecenie **Załaduj ponownie projekt**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Tworzenie pakietu VSIX do wdrożenia elementu projektu
 Aby wdrożyć rozszerzenie, użyj projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest, który jest zawarty w projekcie VSIX. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku **source. Extension. vsixmanifest** w projekcie CustomActionProjectItem, a następnie wybierz polecenie **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu. Plik source. Extension. vsixmanifest jest podstawą dla pliku Extension. vsixmanifest, który wymaga wszystkich pakietów VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W polu **Nazwa produktu** wprowadź **niestandardowy element projektu akcji**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź **element projektu programu SharePoint, który reprezentuje akcję niestandardową**.

5. Na karcie **zasoby** wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

6. Na liście **Typ** wybierz **Microsoft. VisualStudio. ItemTemplate**.

    > [!NOTE]
    > Ta wartość odpowiada elementowi `ItemTemplate` w pliku Extension. vsixmanifest. Ten element identyfikuje podfolder w pakiecie VSIX, który zawiera szablon elementu projektu. Aby uzyskać więcej informacji, zobacz [ItemTemplate element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

8. Na liście **projekt** wybierz pozycję **ItemTemplate**, a następnie wybierz przycisk **OK** .

9. Na karcie **zasoby** wybierz ponownie przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

10. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odpowiada elementowi `MefComponent` w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

12. Na liście **projekt** wybierz pozycję **ProjectItemDefinition**.

13. Wybierz przycisk **OK** .

14. Na pasku menu wybierz **kompiluj** > **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt kompiluje się bez błędów.

15. Upewnij się, że folder danych wyjściowych kompilacji dla projektu CustomActionProjectItem zawiera plik CustomActionProjectItem. VSIX.

     Domyślnie folder wyjściowy kompilacji to... folder \bin\Debug w folderze, który zawiera projekt CustomActionProjectItem.

## <a name="test-the-project-item"></a>Testowanie elementu projektu
 Teraz można przystąpić do testowania elementu projektu. Najpierw Rozpocznij debugowanie rozwiązania CustomActionProjectItem w eksperymentalnym wystąpieniu programu Visual Studio. Następnie przetestuj element projektu **akcji niestandardowej** w projekcie programu SharePoint w eksperymentalnym wystąpieniu programu Visual Studio. Na koniec Skompiluj i Uruchom projekt programu SharePoint, aby sprawdzić, czy działanie niestandardowe działa zgodnie z oczekiwaniami.

#### <a name="to-start-debugging-the-solution"></a>Aby rozpocząć debugowanie rozwiązania

1. Uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie CustomActionProjectItem.

2. Otwórz plik kodu, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w metodzie `InitializeType`.

3. Wybierz klawisz **F5** , aby rozpocząć debugowanie.

     Program Visual Studio instaluje rozszerzenie do%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom akcji projektu Item\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Testujesz element projektu w tym wystąpieniu programu Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Aby przetestować element projektu w programie Visual Studio

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

2. Rozwiń **element C# Visual** lub **Visual Basic** (w zależności od języka obsługiwanego przez szablon elementu), rozwiń węzeł **SharePoint**, a następnie wybierz węzeł **2010** .

3. Na liście szablonów projektu wybierz **projekt SharePoint 2010**.

4. W polu **Nazwa** wprowadź **CustomActionTest**, a następnie wybierz przycisk **OK** .

5. W **Kreatorze dostosowania programu SharePoint**wprowadź adres URL witryny, która ma być używana do debugowania, a następnie wybierz przycisk **Zakończ** .

6. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

7. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **2010** w węźle **SharePoint** .

     Sprawdź, czy element **akcji niestandardowej** pojawia się na liście elementów projektu.

8. Wybierz element **Akcja niestandardowa** , a następnie wybierz przycisk **Dodaj** .

     Program Visual Studio dodaje element o nazwie **CustomAction1** do projektu i otwiera plik Items *. XML* w edytorze.

9. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony wcześniej w metodzie `InitializeType`.

10. Wybierz klawisz **F5** , aby kontynuować debugowanie projektu.

11. W eksperymentalnym wystąpieniu programu Visual Studio, w **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **CustomAction1** , a następnie wybierz polecenie **Wyświetl niestandardowy Projektant akcji**.

12. Sprawdź, czy pojawi się okno komunikatu, a następnie wybierz przycisk **OK** .

     Za pomocą tego menu skrótów można podać dodatkowe opcje lub polecenia dla deweloperów, takie jak wyświetlanie projektanta dla akcji niestandardowej.

13. Na pasku menu wybierz polecenie **wyświetl** > **dane wyjściowe**.

     Zostanie otwarte okno **dane wyjściowe** .

14. W **Eksplorator rozwiązań**Otwórz menu skrótów dla elementu **CustomAction1** , a następnie zmień jego nazwę na **MyCustomAction**.

     W oknie **dane wyjściowe** zostanie wyświetlony komunikat z potwierdzeniem. Ten komunikat jest zapisywana przez procedurę obsługi zdarzeń <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged>, która została zdefiniowana w klasie `CustomActionProjectItemTypeProvider`. Możesz obsłużyć to zdarzenie i inne zdarzenia elementów projektu, aby zaimplementować zachowanie niestandardowe, gdy deweloper modyfikuje element projektu.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Aby przetestować akcję niestandardową w programie SharePoint

1. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz plik Items *. XML* , który jest elementem podrzędnym elementu projektu **MyCustomAction** .

2. W pliku *elementy. XML* wprowadź następujące zmiany, a następnie Zapisz plik:

    - W elemencie `CustomAction` ustaw atrybut `Id` na identyfikator GUID lub inny ciąg unikatowy, jak pokazano na poniższym przykładzie:

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - W `CustomAction` elementu ustaw atrybut `Title`, jak pokazano na poniższym przykładzie:

        ```xml
        Title="SharePoint Developer Center"
        ```

    - W `CustomAction` elementu ustaw atrybut `Description`, jak pokazano na poniższym przykładzie:

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - W `UrlAction` elementu ustaw atrybut `Url`, jak pokazano na poniższym przykładzie:

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Wybierz klawisz **F5** .

     Akcja niestandardowa zostanie spakowana i wdrożona w witrynie programu SharePoint, która jest określona we właściwości **adres URL witryny** projektu. Przeglądarka sieci Web otworzy się na stronie domyślnej tej witryny.

    > [!NOTE]
    > Jeśli zostanie wyświetlone okno dialogowe **debugowanie skryptu wyłączone** , wybierz przycisk **tak** , aby kontynuować debugowanie projektu.

4. W menu **Akcje witryny** wybierz pozycję **Centrum deweloperów programu SharePoint**, sprawdź, czy przeglądarka otwiera witrynę sieci Web https://docs.microsoft.com/sharepoint/dev/, a następnie zamknij przeglądarkę sieci Web.

## <a name="clean-up-the-development-computer"></a>Czyszczenie komputera deweloperskiego
 Po zakończeniu testowania elementu projektu, Usuń szablon elementu projektu z eksperymentalnego wystąpienia programu Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Aby wyczyścić komputer deweloperski

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **narzędzia** > **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz **element projekt akcji niestandardowej**, a następnie wybierz przycisk **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz przycisk **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie.

4. Wybierz przycisk **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

5. Zamknij zarówno eksperymentalne wystąpienie programu Visual Studio, jak i wystąpienie, w którym jest otwarte rozwiązanie CustomActionProjectItem.

## <a name="next-steps"></a>Następne kroki
 Po zakończeniu tego instruktażu można dodać kreatora do szablonu elementu. Gdy użytkownik dodaje niestandardowy element projektu akcji do projektu programu SharePoint, Kreator zbiera informacje o akcji (na przykład o lokalizacji i adresie URL, do której należy przejść po wybraniu akcji) i dodaje te informacje do pliku Items *. XML* w nowym element projektu. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu, część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie niestandardowego elementu projektu akcji z szablonem elementu część 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Definiowanie niestandardowych typów elementów projektu SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Tworzenie szablonów elementów i szablonów projektu dla elementów projektu SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Korzystanie z usługi projektu SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons)
- [Tworzenie ikony lub innego edytora obrazów &#40;obrazów dla ikon&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)