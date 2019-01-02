---
title: 'Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e12f9d8b93b429b0ecdc433eef59809f2ca4c61d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891579"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint
  Podczas wdrażania projektu programu SharePoint, programu Visual Studio wykonuje szereg kroków wdrożenia w określonej kolejności. Program Visual Studio obejmuje wiele kroków wdrożenia wbudowanych, ale można także tworzyć własne.  
  
 W tym przewodniku utworzysz niestandardowego kroku wdrożenia do uaktualnienia rozwiązań na serwerze, na którym uruchomiony jest SharePoint. Program Visual Studio obejmuje kroki wdrażania wbudowane dla wielu zadań, takich wycofywanie lub Dodawanie rozwiązań, ale nie zawiera kroku wdrożenia dla uaktualnienie rozwiązań. Domyślnie podczas wdrażania rozwiązania programu SharePoint, programu Visual Studio najpierw wycofuje rozwiązanie (jeśli została już wdrożona) i następnie ponownie wdraża całego rozwiązania. Aby uzyskać więcej informacji na temat kroków wdrażania wbudowane zobacz [wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
-   Tworzenie rozszerzenia programu Visual Studio, który wykonuje dwa główne zadania:  
  
    -   Rozszerzenie określa niestandardowego kroku wdrożenia do uaktualnienia rozwiązań programu SharePoint.  
  
    -   Rozszerzenie tworzy rozszerzenia projektu, który definiuje nową konfigurację wdrożenia, czyli zestaw kroków wdrażania, które są wykonywane dla danego projektu. Nowej konfiguracji wdrożenia zawiera krok wdrażania niestandardowego i kilka kroków wdrażania wbudowanych.  
  
-   Utwórz dwa niestandardowych poleceń programu SharePoint, które wywołuje zestawu rozszerzeń. Polecenia programu SharePoint są metody, które można wywoływać za pomocą zestawów rozszerzenie użycia interfejsów API w modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [wywoływanie modeli obiektów SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Tworzenie pakietu Visual Studio rozszerzenia (VSIX) do wdrożenia, oba zestawy.  
  
-   Testowanie nowego kroku wdrażania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:  
  
- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.
  
- Program Visual Studio SDK. W tym instruktażu wykorzystano **projekt VSIX** szablonu w zestawie SDK, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Znajomość następujących pojęć jest przydatna, ale nie jest to wymagane, aby ukończyć Instruktaż:  
  
- Za pomocą modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [za pomocą modelu obiektów programu SharePoint Foundation po stronie serwera](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- Rozwiązania programu SharePoint. Aby uzyskać więcej informacji, zobacz [omówienie rozwiązań](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
- Uaktualnianie rozwiązań programu SharePoint. Aby uzyskać więcej informacji, zobacz [uaktualnianie rozwiązania](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Tworzenie projektów
 Do przeprowadzenia tego instruktażu, należy utworzyć trzy projekty:  
  
- Projekt VSIX do stworzenia pakietu VSIX, aby wdrożyć rozszerzenie.  
  
- Projekt biblioteki klas, który implementuje rozszerzenie. Ten projekt musi być przeznaczony .NET Framework 4.5.  
  
- Projekt biblioteki klas, który definiuje niestandardowe polecenia programu SharePoint. Ten projekt musi być przeznaczony dla .NET Framework 3.5.  
  
  Instruktaż należy rozpocząć od utworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  **Rozszerzalności** węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.  
  
4.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
5.  Wybierz **projekt VSIX** szablonu, nazwę projektu **UpgradeDeploymentStep**, a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **UpgradeDeploymentStep** projekt **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązania UpgradeDeploymentStep, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **Windows** węzła.  
  
3.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework.  
  
4.  Wybierz **biblioteki klas** projektu szablonu, nadaj projektowi nazwę **DeploymentStepExtension**, a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **DeploymentStepExtension** projektu do rozwiązania i otwiera plik domyślny kodu Class1.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Aby utworzyć projekt polecenia SharePoint  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązania UpgradeDeploymentStep, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic**, a następnie wybierz **Windows** węzła.  
  
3.  W górnej części okna dialogowego wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.  
  
4.  Wybierz **biblioteki klas** projektu szablonu, nadaj projektowi nazwę **SharePointCommands**, a następnie wybierz **OK** przycisku.  
  
     Program Visual Studio dodaje **SharePointCommands** projektu do rozwiązania i otwiera plik domyślny kodu Class1.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed przystąpieniem do napisania kod, aby utworzyć niestandardowego kroku wdrożenia, należy dodać pliki kodu i odwołania do zestawów, a następnie należy skonfigurować projektów.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Aby skonfigurować projekt DeploymentStepExtension
  
1.  W **DeploymentStepExtension** projektu, należy dodać dwa pliki kodu, które mają następujące nazwy:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Otwórz menu skrótów dla projektu DeploymentStepExtension, a następnie wybierz **Dodaj odwołanie**.  
  
3.  Na **Framework** , a następnie wybierz pole wyboru dla zestawu System.ComponentModel.Composition.  
  
4.  Na **rozszerzenia** kartę, zaznacz pole wyboru dla zestawu Microsoft.VisualStudio.SharePoint, a następnie wybierz **OK** przycisku.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Aby skonfigurować projekt SharePointCommands
  
1.  W **SharePointCommands** projektu, Dodaj plik kodu, który nosi nazwę polecenia.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów na **SharePointCommands** węzła projektu, a następnie wybierz **Dodaj odwołanie**.  
  
3.  Na **rozszerzenia** kartę, zaznacz pole wyboru dla następujących zestawów, a następnie kliknij przycisk Wybierz **OK** przycisku  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Definiowanie niestandardowego kroku wdrożenia
 Utwórz klasę, która definiuje krok uaktualniania wdrożenia. Aby zdefiniować krok wdrażania, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfejsu. Zawsze, gdy chcesz zdefiniować niestandardowego kroku wdrożenia, należy zaimplementować ten interfejs.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Aby zdefiniować krok wdrażania niestandardowego  
  
1.  W **DeploymentStepExtension** projektu, otwórz plik kodu UpgradeStep i wklej następujący kod do niego.  
  
    > [!NOTE]  
    >  Po dodaniu tego kodu, projekt będzie miał pewne błędy kompilacji, ale znikną po dodaniu kodu w dalszych krokach.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Tworzenie konfiguracji wdrożenia, która obejmuje krok wdrażania niestandardowego
 Tworzenie rozszerzenia projektu dla konfiguracji wdrażania nowych obejmuje kilka kroków wdrażania wbudowanych i nowy krok uaktualniania wdrożenia. Tworząc tego rozszerzenia, możesz pomóc deweloperom programu SharePoint do użycia w kroku wdrażania uaktualnienia w projektach programu SharePoint.  
  
 Aby utworzyć konfigurację wdrożenia, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu. Implementuje ten interfejs umożliwia tworzenie rozszerzenia projektu SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Aby utworzyć konfigurację wdrożenia  
  
1.  W **DeploymentStepExtension** projektu, otwórz plik kodu DeploymentConfigurationExtension i wklej następujący kod do niego.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Tworzenie niestandardowych poleceń programu SharePoint
 Utwórz dwa polecenia niestandardowe odwołujące się do modelu obiektów serwera dla programu SharePoint. Jedno polecenie Określa, czy rozwiązanie jest już wdrożony; inne polecenia uaktualnia rozwiązania.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować poleceń programu SharePoint  
  
1.  W **SharePointCommands** projektu, otwórz plik kodu poleceń i następnie wklej następujący kod do niego.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
 W tym momencie w instruktażu, cały kod dla niestandardowego kroku wdrożenia i poleceń programu SharePoint są teraz w projektach. Twórz je, aby upewnić się, że ich skompilować bez błędów.  
  
#### <a name="to-build-the-projects"></a>Tworzenie projektów  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **DeploymentStepExtension** projektu, a następnie wybierz **kompilacji**.  
  
2.  Otwórz menu skrótów dla **SharePointCommands** projektu, a następnie wybierz **kompilacji**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Utwórz pakiet VSIX, aby wdrożyć rozszerzenie
 Aby wdrożyć rozszerzenie, należy użyć projektu VSIX w rozwiązaniu Aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest w projekcie VSIX. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX  
  
1.  W **Eksploratora rozwiązań**w obszarze **UpgradeDeploymentStep** projektu, otwórz menu skrótów dla **source.extension.vsixmanifest** , a następnie wybierz  **Otwórz**.  
  
     Program Visual Studio otwiera plik w edytorze manifestu. Plik source.extension.vsixmanifest jest podstawą dla pliku extension.vsixmanifest, które wymagają wszystkie pakiety VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **uaktualnienia kroku wdrożenia dla projektów programu SharePoint**.  
  
3.  W **Autor** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **zawiera krok wdrażania niestandardowego uaktualnienia, który mogą być używane w projektach SharePoint**.  
  
5.  W **zasoby** karta w edytorze wybierz **nowy** przycisku.  
  
     **Dodaj nowy zasób** pojawi się okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MefComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
8.  W **projektu** wybierz **DeploymentStepExtension**, a następnie wybierz **OK** przycisku.  
  
9. W edytorze manifestu wybierz **New** ponownie przycisk.  
  
     **Dodaj nowy zasób** pojawi się okno dialogowe.  
  
10. W **typu** listy, wprowadź **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Ten element określa niestandardowe rozszerzenie, które mają zostać uwzględnione w rozszerzeniu Visual Studio. Aby uzyskać więcej informacji, zobacz [zawartości elementu (schemat VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. W **źródła** wybierz **projekt w bieżącym rozwiązaniu**.  
  
12. W **projektu** wybierz **SharePointCommands**, a następnie wybierz **OK** przycisku.  
  
13. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje bez błędów.  
  
14. Upewnij się, że folder wyjściowy kompilacji dla projektu UpgradeDeploymentStep zawiera teraz plik UpgradeDeploymentStep.vsix.  
  
     Domyślnie folderem wyjściowym kompilacji jest... folderze \bin\Debug w folderze, który zawiera plik projektu.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Przygotowanie do testowania krok uaktualniania wdrożenia
 Aby przetestować krok uaktualniania wdrożenia, należy wdrożyć przykładowe rozwiązanie w witrynie programu SharePoint. Należy uruchomić debugowanie rozszerzeń w doświadczalnym wystąpieniu programu Visual Studio. Następnie utwórz definicji listy oraz wystąpienie listy na potrzeby testowania kroku wdrożenia, a następnie wdrożyć je do witryny programu SharePoint. Następnie zmodyfikuj definicji listy i instancji list i ponownie wdrożyć je, aby zademonstrować, jak proces wdrażania domyślne zastępuje rozwiązania w witrynie programu SharePoint.  
  
 W dalszej części tego przewodnika zmodyfikujesz definicji listy oraz wystąpienie listy, a następnie można będzie je w witrynie programu SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia  
  
1.  Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie UpgradeDeploymentStep.  
  
2.  W projekcie DeploymentStepExtension, otwórz plik kodu UpgradeStep, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w `CanExecute` i `Execute` metody.  
  
3.  Rozpocznij debugowanie wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.  
  
4.  Visual Studio instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade kroku wdrożenia dla programu SharePoint Projects\1.0 i uruchamia doświadczalne wystąpienie programu Visual Studio. Krok uaktualniania wdrożenia będzie testu, w tym wystąpieniu programu Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Aby utworzyć projekt programu SharePoint przy użyciu definicji listy i instancji list  
  
1. W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
2. W **nowy projekt** okna dialogowego rozwiń **Visual C#** węzła lub **języka Visual Basic** węzła, rozwiń węzeł **programu SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
3. Upewnij się, że w górnej części okna dialogowego **.NET Framework 3.5** pojawia się na liście wersji programu .NET Framework.  
  
    Projekty dla [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] wymagają tej wersji systemu .NET Framework.  
  
4. Na liście szablonów projektu wybierz **projekt programu SharePoint 2010**, nadaj projektowi nazwę **EmployeesListDefinition**, a następnie wybierz **OK** przycisku.  
  
5. W **Kreator ustawień niestandardowych SharePoint**, wprowadź adres URL witryny, której chcesz używać do debugowania.  
  
6. W obszarze **co to jest poziom zaufania dla tego rozwiązania programu SharePoint**, wybierz **Wdróż jako rozwiązanie farmy** przycisku opcji.  
  
   > [!NOTE]  
   >  Krok wdrożenia uaktualnienia nie obsługuje rozwiązania w trybie piaskownicy.  
  
7. Wybierz **Zakończ** przycisku.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt EmployeesListDefinition.  
  
8. Wybierz pozycję Otwórz menu skrótów dla projektu EmployeesListDefinition **Dodaj**, a następnie wybierz **nowy element**.  
  
9. W **Dodaj nowy element - EmployeesListDefinition** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
10. Wybierz **listy** szablonu elementu, określ nazwę elementu **listy pracowników**, a następnie wybierz **Dodaj** przycisku.  
  
     Zostanie wyświetlony Kreator dostosowania programu SharePoint  
  
11. Na **wybierz ustawienia listy** strony, sprawdź następujące ustawienia, a następnie wybierz **Zakończ** przycisku:  
  
    1. **Lista pracowników** pojawia się w **jaką nazwę chcesz wyświetlić listy?** pole.  
  
    2. **Tworzenie na podstawie listy można dostosowywać:** wciśnięcia przycisku opcji.  
  
    3. **Domyślne (pustego)** jest wybierany w **tworzenie na podstawie listy można dostosowywać:** listy.  
  
       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy element listy pracowników z kolumny Title i pojedyncze wystąpienie pusty i zostanie otwarty projektant listy.  
  
12. W Projektancie listy na **kolumn** kartę, wybrać **wpisz nazwę nowej lub istniejącej kolumny** wiersza, a następnie dodaj następujące kolumny w **Nazwa wyświetlana kolumny** listy:  
  
    1.  Imię  
  
    2.  Firmy  
  
    3.  Telefon służbowy  
  
    4.  Wiadomości e-Mail  
  
13. Zapisz wszystkie pliki, a następnie zamknij projektanta listy.  
  
14. W **Eksploratora rozwiązań**, rozwiń węzeł **listy pracowników** węzła, a następnie rozwiń węzeł **wystąpienie listy pracowników** węzeł podrzędny.  
  
15. W *Elements.xml* pliku, Zastąp domyślne XML w tym pliku następujący kod XML. Poniższy kod XML zmienia nazwę na liście, aby **pracowników** i dodaje informacje o pracownika, który ma o nazwie Jan Kowalski.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Zapisz i Zamknij *Elements.xml* pliku.  
  
17. Otwórz menu skrótów dla projektu EmployeesListDefinition, a następnie wybierz **Otwórz** lub **właściwości**.  
  
     Zostanie otwarty projektant właściwości.  
  
18. Na **SharePoint** kartę, usuń zaznaczenie **automatycznie Wycofaj po debugowaniu** pole wyboru, a następnie zapisać wprowadzone właściwości.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Wdrażanie definicji listy i instancji list  
  
1.  W **Eksploratora rozwiązań**, wybierz **EmployeesListDefinition** węzeł projektu.  
  
2.  W **właściwości** okna, upewnij się, że **aktywnej konfiguracji wdrożenia** właściwość jest ustawiona na **domyślne**.  
  
3.  Wybierz **F5** klucza, lub na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie**.  
  
4.  Sprawdź, czy projekt zostanie skompilowany poprawnie, że przeglądarka sieci web otworzy się w witrynie programu SharePoint, **Wyświetla** elementu w pasku Szybkie uruchamianie obejmuje nowy **pracowników** listy, a  **Pracownicy** lista zawiera wpis dla Jan Kowalski.  
  
5.  Zamknij przeglądarkę sieci web.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Modyfikowanie definicji listy i instancji list i ponownie wdrożyć je  
  
1.  W projekcie EmployeesListDefinition Otwórz *Elements.xml* pliku, który jest elementem podrzędnym **wystąpienie listy pracowników** elementu projektu.  
  
2.  Usuń `Data` elementu i jego elementów podrzędnych, aby usunąć wpis dla Jan Kowalski z listy.  
  
     Gdy skończysz, ten plik powinien zawierać następujący kod XML.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Zapisz i Zamknij *Elements.xml* pliku.  
  
4.  Otwórz menu skrótów dla **listy pracowników** elementu projektu, a następnie wybierz **Otwórz** lub **właściwości**.  
  
5.  W Projektancie listy wybierz **widoków** kartę.  
  
6.  W **wybrane kolumny** , wybierz **załączniki**, a następnie wybierz polecenie < klawisz, aby przenieść tej kolumny na **dostępnych kolumn** listy.  
  
7.  Powtórz poprzedni krok, aby przenieść **Telefon służbowy** kolumny z **wybrane kolumny** do listy **dostępnych kolumn** listy.  
  
     Ta akcja usuwa te pola z domyślny widok **pracowników** listy w witrynie programu SharePoint.  
  
8.  Rozpocznij debugowanie wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.  
  
9. Upewnij się, że **konflikty wdrażania** pojawi się okno dialogowe.  
  
     Ten pojawi się okno dialogowe gdy próbuje wdrożyć rozwiązanie (wystąpienie listy) programu Visual Studio w witrynie programu SharePoint, do których już wdrożono rozwiązanie. To okno dialogowe nie będzie wyświetlane podczas wykonywania kroku wdrażania uaktualnienia później w tym przewodniku.  
  
10. W **konflikty wdrażania** okna dialogowego wybierz **rozwiązać automatycznie** przycisku opcji.  
  
     Program Visual Studio usuwa wystąpienie listy w witrynie programu SharePoint, wdraża element listy w projekcie, a następnie otwiera witrynę programu SharePoint.  
  
11. W **Wyświetla** sekcji paska szybkiego uruchamiania wybierz **pracowników** listy, a następnie sprawdź następujące informacje:  
  
    -   **Załączniki** i **Telefon domowy** kolumn nie są wyświetlane w tym widoku listy.  
  
    -   Lista jest pusta. Kiedy użyć **domyślne** konfigurację wdrożenia do ponownego wdrożenia rozwiązania, **pracowników** listy został zastąpiony nową listę pusty w projekcie.  
  
## <a name="test-the-deployment-step"></a>Testowanie kroku wdrożenia
 Teraz można przystąpić do testowania krok uaktualniania wdrożenia. Najpierw należy dodać element do wystąpienia listy w programie SharePoint. Następnie zmień definicji listy i instancji list, uaktualnienia ich w witrynie programu SharePoint i upewnij się, że krok uaktualniania wdrożenia nie zastępuje nowy element.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Aby ręcznie dodać element do listy  
  
1.  Na Wstążce w witrynie programu SharePoint w obszarze **narzędzia do obsługi List** kartę, wybrać **elementów** kartę.  
  
2.  W **New** grupy, wybierz **nowy element**.  
  
     Alternatywnie, możesz wybrać **Dodaj nowy element** łącze w samej listy elementów.  
  
3.  W **pracowników — nowy element** okna w **tytuł** wprowadź **Menedżera urządzeń**.  
  
4.  W **imię** wprowadź **Andy**.  
  
5.  W **firmy** wpisz **Contoso**.  
  
6.  Wybierz **Zapisz** przycisk, sprawdź, czy nowy element jest wyświetlany na liście, a następnie zamknij przeglądarkę sieci web.  
  
     W dalszej części tego przewodnika użyjesz ten element, aby sprawdzić, czy krok uaktualniania wdrożenia nie zastępuje zawartość tej listy.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Aby przetestować krok uaktualniania wdrożenia  
  
1. W doświadczalnym wystąpieniu programu Visual Studio w **Eksploratora rozwiązań**, otwórz menu skrótów dla **EmployeesListDefinition** węzła projektu, a następnie wybierz **właściwości**.  
  
    Zostanie otwarty Edytor właściwości/projektanta.  
  
2. Na **SharePoint** kartę, należy ustawić **aktywnej konfiguracji wdrożenia** właściwości **uaktualnienia**.  
  
    Ta konfiguracja wdrożenia niestandardowego zawiera nowy krok uaktualniania wdrożenia.  
  
3. Otwórz menu skrótów dla **listy pracowników** elementu projektu, a następnie wybierz **właściwości** lub **Otwórz**.  
  
    Zostanie otwarty Edytor właściwości/projektanta.  
  
4. Na **widoków** karty, wybierz polecenie **wiadomości E-Mail** kolumny, a następnie wybierz **<** klawisz, aby przenieść tej kolumny z **wybrane kolumny**do listy **dostępnych kolumn** listy.  
  
    Ta akcja usuwa te pola z domyślny widok **pracowników** listy w witrynie programu SharePoint.  
  
5. Rozpocznij debugowanie wybierając **F5** klucza lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.  
  
6. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `CanExecute` metody.  
  
7. Wybierz **F5** ponownie klucza, lub na pasku menu wybierz **debugowania** > **Kontynuuj**.  
  
8. Sprawdź, czy kod zatrzymuje się na punkcie przerwania, który wcześniej w ustawieniu `Execute` metody.  
  
9. Wybierz **F5** klucza, lub na pasku menu wybierz **debugowania** > **Kontynuuj** raz ostatni.  
  
     Przeglądarka sieci web otwiera witrynę programu SharePoint.  
  
10. W **Wyświetla** sekcji obszaru szybkiego uruchamiania wybierz **pracowników** listy, a następnie sprawdź następujące informacje:  
  
    - Element, który ręcznie dodane wcześniej (dla Andy, Menedżer urządzeń) jest nadal na liście.  
  
    - **Telefon służbowy** i **adres E-mail** kolumn nie są wyświetlane w tym widoku listy.  
  
      **Uaktualnienia** konfiguracji wdrożenia modyfikuje istniejące **pracowników** wystąpienie listy w witrynie programu SharePoint. Jeśli użyto **domyślne** konfiguracji wdrożenia zamiast **uaktualnienia** konfiguracji, może wystąpić konflikt wdrażania. Program Visual Studio może rozwiązać konflikt, zastępując **pracowników** listy i element dla Andy, Menedżera urządzeń, zostaną usunięte.  
  
## <a name="clean-up-the-development-computer"></a>Czyszczenie na komputerze deweloperskim
 Po zakończeniu testowania kroku wdrożenia uaktualnienia Usuń wystąpienie listy i definicji listy z witryny programu SharePoint i usuń rozszerzenie kroku wdrażania z programu Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Aby usunąć wystąpienie listy z witryny programu SharePoint  
  
1.  Otwórz **pracowników** listy w witrynie programu SharePoint, jeśli lista nie jest jeszcze otwarte.  
  
2.  Na Wstążce w witrynie programu SharePoint wybierz **narzędzia do obsługi List** kartę, a następnie wybierz **listy** kartę.  
  
3.  W **ustawienia** grupy, wybierz **ustawienia listy** elementu.  
  
4.  W obszarze **uprawnienia i zarządzanie**, wybierz **Usuń tę listę** polecenia, wybierz **OK** aby upewnić się, że chcesz wysłać listę do Kosza, a następnie zamknij sieci web Przeglądarka.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Aby usunąć definicji listy z witryny programu SharePoint  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **kompilacji** > **Wycofaj**.  
  
     Program Visual Studio wycofuje definicji listy z witryny programu SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie  
  
1.  W doświadczalnym wystąpieniu programu Visual Studio, na pasku menu wybierz **narzędzia** > **rozszerzenia i aktualizacje**.  
  
     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.  
  
2.  Na liście rozszerzeń wybierz **uaktualnienia kroku wdrożenia dla projektów programu SharePoint**, a następnie wybierz **Odinstaluj** polecenia.  
  
3.  W oknie dialogowym wybierz **tak** aby upewnić się, że chcesz odinstalować rozszerzenie, a następnie wybierz **Uruchom ponownie teraz** aby ukończyć dezinstalację.  
  
4.  Zamknij oba wystąpienia programu Visual Studio (wystąpienie doświadczalne i wystąpienie programu Visual Studio, w którym rozwiązanie UpgradeDeploymentStep jest otwarty).  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie pakowania i wdrażania SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
