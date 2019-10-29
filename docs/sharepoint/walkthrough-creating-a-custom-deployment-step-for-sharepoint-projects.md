---
title: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0053b279dfdc0fd80608efb7fb663cacf217f1c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984940"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint
  Podczas wdrażania projektu programu SharePoint, program Visual Studio wykonuje serię kroków wdrożenia w określonej kolejności. Program Visual Studio zawiera wiele wbudowanych kroków wdrażania, ale można również utworzyć własne.

 W tym instruktażu utworzysz niestandardowy krok wdrożenia w celu uaktualnienia rozwiązań na serwerze, na którym działa program SharePoint. Program Visual Studio zawiera wbudowaną procedurę wdrażania dla wielu zadań, takich wycofywania lub dodawania rozwiązań, ale nie obejmuje krok wdrożenia na potrzeby uaktualniania rozwiązań. Domyślnie podczas wdrażania rozwiązania programu SharePoint program Visual Studio najpierw wycofuje rozwiązanie (jeśli zostało już wdrożone), a następnie ponownie wdraża całe rozwiązanie. Aby uzyskać więcej informacji na temat wbudowanych kroków wdrażania, zobacz [wdrażanie, publikowanie i uaktualnianie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie rozszerzenia programu Visual Studio, które wykonuje dwa podstawowe zadania:

  - Rozszerzenie definiuje niestandardowy krok wdrożenia w celu uaktualnienia rozwiązań programu SharePoint.

  - Rozszerzenie tworzy rozszerzenie projektu, które definiuje nową konfigurację wdrożenia, która jest zestawem kroków wdrożenia, które są wykonywane dla danego projektu. Nowa konfiguracja wdrożenia obejmuje niestandardowy krok wdrożenia i kilka wbudowanych kroków wdrożenia.

- Tworzenie dwóch niestandardowych poleceń programu SharePoint, do których odwołuje się zestaw rozszerzenia. Polecenia programu SharePoint to metody, które mogą być wywoływane przez zestawy rozszerzeń do używania interfejsów API w modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [Wywoływanie modeli obiektów programu SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Kompilowanie pakietu rozszerzenia Visual Studio (VSIX) w celu wdrożenia obu zestawów.

- Testowanie nowego kroku wdrożenia.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są następujące składniki na komputerze deweloperskim:

- Obsługiwane wersje systemu Windows, SharePoint i Visual Studio.

- Zestaw SDK programu Visual Studio. W tym instruktażu zostanie użyty szablon **projektu VSIX** w zestawie SDK w celu utworzenia pakietu VSIX do wdrożenia rozszerzenia. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzającą narzędzia programu SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  Znajomość następujących pojęć jest pomocna, ale nie jest wymagana, aby ukończyć Przewodnik:

- Korzystanie z modelu obiektów serwera dla programu SharePoint. Aby uzyskać więcej informacji, zobacz [Korzystanie z modelu obiektów po stronie serwera programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Rozwiązania programu SharePoint. Aby uzyskać więcej informacji, zobacz [Omówienie rozwiązań](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- Uaktualnianie rozwiązań programu SharePoint. Aby uzyskać więcej informacji, zobacz [uaktualnianie rozwiązania](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Tworzenie projektów
 Aby ukończyć ten Instruktaż, należy utworzyć trzy projekty:

- Projekt VSIX, aby utworzyć pakiet VSIX do wdrożenia rozszerzenia.

- Projekt biblioteki klas, który implementuje rozszerzenie. Ten projekt musi być przeznaczony dla .NET Framework 4,5.

- Projekt biblioteki klas, który definiuje niestandardowe polecenia programu SharePoint. Ten projekt musi być przeznaczony dla .NET Framework 3,5.

  Rozpocznij przewodnik, tworząc projekty.

#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz kolejno pozycje **plik**  > **Nowy**  > **projekt**.

3. W oknie dialogowym **Nowy projekt** rozwiń węzły **wizualizacji C#**  lub **Visual Basic** , a następnie wybierz węzeł **rozszerzalności** .

    > [!NOTE]
    > Węzeł **rozszerzalności** jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz sekcję wymagania wstępne we wcześniejszej części tego tematu.

4. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework.

5. Wybierz szablon **projektu VSIX** , nazwij projekt **UpgradeDeploymentStep**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **UpgradeDeploymentStep** do **Eksplorator rozwiązań**.

#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie UpgradeDeploymentStep, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzły **wizualizacji C#**  lub **Visual Basic** , a następnie wybierz węzeł **systemu Windows** .

3. W górnej części okna dialogowego wybierz pozycję **.NET Framework 4,5** na liście wersji .NET Framework.

4. Wybierz szablon projektu **Biblioteka klas** , nazwij projekt **DeploymentStepExtension**, a następnie wybierz przycisk **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje projekt **DeploymentStepExtension** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

#### <a name="to-create-the-sharepoint-command-project"></a>Aby utworzyć projekt polecenia programu SharePoint

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła rozwiązanie UpgradeDeploymentStep, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz węzeł **systemu Windows** .

3. W górnej części okna dialogowego wybierz pozycję **.NET Framework 3,5** na liście wersji .NET Framework.

4. Wybierz szablon projektu **Biblioteka klas** , nazwij projekt **SharePointCommands**, a następnie wybierz przycisk **OK** .

     Program Visual Studio dodaje projekt **SharePointCommands** do rozwiązania i otwiera domyślny plik kodu Class1.

5. Usuń plik kodu Class1 z projektu.

## <a name="configure-the-projects"></a>Konfigurowanie projektów
 Przed napisaniem kodu w celu utworzenia niestandardowego kroku wdrożenia należy dodać pliki kodu i odwołania do zestawów i należy skonfigurować projekty.

#### <a name="to-configure-the-deploymentstepextension-project"></a>Aby skonfigurować Projekt DeploymentStepExtension

1. W projekcie **DeploymentStepExtension** Dodaj dwa pliki kodu, które mają następujące nazwy:

    - UpgradeStep

    - DeploymentConfigurationExtension

2. Otwórz menu skrótów w projekcie DeploymentStepExtension, a następnie wybierz polecenie **Dodaj odwołanie**.

3. Na karcie **Struktura** zaznacz pole wyboru dla zestawu System. ComponentModel. kompozycji.

4. Na karcie **rozszerzenia** zaznacz pole wyboru dla zestawu Microsoft. VisualStudio. SharePoint, a następnie wybierz przycisk **OK** .

#### <a name="to-configure-the-sharepointcommands-project"></a>Aby skonfigurować projekt SharePointCommands

1. W projekcie **SharePointCommands** Dodaj plik kodu o nazwie Commands.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów węzła projektu **SharePointCommands** , a następnie wybierz polecenie **Dodaj odwołanie**.

3. Na karcie **rozszerzenia** zaznacz pola wyboru dla następujących zestawów, a następnie kliknij przycisk **OK** .

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

## <a name="define-the-custom-deployment-step"></a>Definiowanie niestandardowego kroku wdrożenia
 Utwórz klasę, która definiuje krok wdrożenia uaktualniania. Aby zdefiniować krok wdrożenia, Klasa implementuje interfejs <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz zdefiniować niestandardowy krok wdrożenia.

#### <a name="to-define-the-custom-deployment-step"></a>Aby zdefiniować niestandardowy krok wdrożenia

1. W projekcie **DeploymentStepExtension** Otwórz plik kodu UpgradeStep, a następnie wklej do niego następujący kod.

    > [!NOTE]
    > Po dodaniu tego kodu projekt będzie miał pewne błędy kompilacji, ale w późniejszych krokach zostanie dodany kod.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Utwórz konfigurację wdrożenia obejmującą niestandardowy krok wdrożenia
 Utwórz rozszerzenie projektu dla nowej konfiguracji wdrożenia, w tym kilka wbudowanych kroków wdrażania i nowego kroku wdrożenia uaktualnienia. Utworzenie tego rozszerzenia ułatwia deweloperom programu SharePoint korzystanie z kroku Uaktualnij wdrożenie w projektach programu SharePoint.

 Aby utworzyć konfigurację wdrożenia, Klasa implementuje interfejs <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>. Zaimplementuj ten interfejs w każdym przypadku, gdy chcesz utworzyć rozszerzenie projektu SharePoint.

#### <a name="to-create-the-deployment-configuration"></a>Aby utworzyć konfigurację wdrożenia

1. W projekcie **DeploymentStepExtension** Otwórz plik kodu DeploymentConfigurationExtension, a następnie wklej do niego następujący kod.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Tworzenie niestandardowych poleceń programu SharePoint
 Utwórz dwa niestandardowe polecenia, które wywołują model obiektów serwera dla programu SharePoint. Jedno polecenie określa, czy rozwiązanie jest już wdrożone; inne polecenie uaktualnia rozwiązanie.

#### <a name="to-define-the-sharepoint-commands"></a>Aby zdefiniować polecenia programu SharePoint

1. W projekcie **SharePointCommands** Otwórz plik poleceń kod, a następnie wklej do niego następujący kod.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Elementu
 W tym momencie w przewodniku wszystkie kod niestandardowego kroku wdrożenia i poleceń programu SharePoint znajdują się teraz w projektach. Kompiluj je, aby upewnić się, że kompilują się bez błędów.

#### <a name="to-build-the-projects"></a>Aby skompilować projekty

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **DeploymentStepExtension** , a następnie wybierz polecenie **Kompiluj**.

2. Otwórz menu skrótów dla projektu **SharePointCommands** , a następnie wybierz polecenie **Kompiluj**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Tworzenie pakietu VSIX w celu wdrożenia rozszerzenia
 Aby wdrożyć rozszerzenie, użyj projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw skonfiguruj pakiet VSIX, modyfikując plik source. Extension. vsixmanifest w projekcie VSIX. Następnie Utwórz pakiet VSIX, tworząc rozwiązanie.

#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX

1. W **Eksplorator rozwiązań**, w ramach projektu **UpgradeDeploymentStep** , otwórz menu skrótów dla pliku **source. Extension. vsixmanifest** , a następnie wybierz polecenie **Otwórz**.

     Program Visual Studio otwiera plik w edytorze manifestu. Plik source. Extension. vsixmanifest jest podstawą dla pliku Extension. vsixmanifest, który wymaga wszystkich pakietów VSIX. Aby uzyskać więcej informacji na temat tego pliku, zobacz [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. W polu **Nazwa produktu** wprowadź **krok Uaktualnij uaktualnienie dla projektów programu SharePoint**.

3. W polu **autor** wprowadź wartość **contoso**.

4. W polu **Opis** wprowadź polecenie **zawiera niestandardowy krok wdrożenia uaktualniania, który może być używany w projektach programu SharePoint**.

5. Na karcie **zasoby** edytora wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

6. Na liście **Typ** wybierz **Microsoft. VisualStudio. MefComponent**.

    > [!NOTE]
    > Ta wartość odpowiada elementowi `MefComponent` w pliku Extension. vsixmanifest. Ten element określa nazwę zestawu rozszerzenia w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MefComponent element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

8. Na liście **projekt** wybierz pozycję **DeploymentStepExtension**, a następnie wybierz przycisk **OK** .

9. W edytorze manifestu ponownie wybierz przycisk **Nowy** .

     Pojawi się okno dialogowe **Dodaj nowy element zawartości** .

10. Na liście **Typ** wprowadź wartość **SharePoint. Commands. v4**.

    > [!NOTE]
    > Ten element określa niestandardowe rozszerzenie, które ma zostać dołączone do rozszerzenia programu Visual Studio. Aby uzyskać więcej informacji, zobacz [element zawartości (schemat VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. Z listy **Źródło** wybierz **projekt w bieżącym rozwiązaniu**.

12. Na liście **projekt** wybierz pozycję **SharePointCommands**, a następnie wybierz przycisk **OK** .

13. Na pasku menu wybierz **kompiluj** > **Kompiluj rozwiązanie**, a następnie upewnij się, że rozwiązanie kompiluje się bez błędów.

14. Upewnij się, że folder danych wyjściowych kompilacji dla projektu UpgradeDeploymentStep zawiera teraz plik UpgradeDeploymentStep. VSIX.

     Domyślnie folder wyjściowy kompilacji to... folder \bin\Debug w folderze, który zawiera plik projektu.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Przygotowanie do przetestowania kroku wdrożenia uaktualnienia
 Aby przetestować krok wdrożenia uaktualnienia, należy najpierw wdrożyć przykładowe rozwiązanie w witrynie programu SharePoint. Zacznij od debugowania rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio. Następnie Utwórz definicję listy i wystąpienie listy do użycia w celu przetestowania kroku wdrożenia, a następnie wdróż je w witrynie programu SharePoint. Następnie zmodyfikuj definicję listy i wystąpienie listy, a następnie wdróż je ponownie, aby zademonstrować, jak domyślny proces wdrażania zastępuje rozwiązania w witrynie programu SharePoint.

 W dalszej części tego instruktażu zmodyfikujesz definicję listy i wystąpienie listy, a następnie uaktualnisz je w witrynie programu SharePoint.

#### <a name="to-start-debugging-the-extension"></a>Aby rozpocząć debugowanie rozszerzenia

1. Uruchom ponownie program Visual Studio z poświadczeniami administracyjnymi, a następnie otwórz rozwiązanie UpgradeDeploymentStep.

2. W projekcie DeploymentStepExtension Otwórz plik kodu UpgradeStep, a następnie Dodaj punkt przerwania do pierwszego wiersza kodu w metodzie `CanExecute` i `Execute`.

3. Rozpocznij debugowanie, wybierając klawisz **F5** lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

4. Program Visual Studio instaluje rozszerzenie%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade krok wdrożenia dla programu SharePoint Projects\1.0 i uruchamia eksperymentalne wystąpienie programu Visual Studio. Krok Uaktualnij wdrożenie zostanie przetestowany w tym wystąpieniu programu Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Aby utworzyć projekt programu SharePoint z definicją listy i wystąpieniem listy

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

2. W oknie **dialogowym Nowy projekt** rozwiń węzeł **wizualizacji C#**  lub **Visual Basic** węzeł, rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

3. Na początku okna dialogowego upewnij się, że na liście wersji .NET Framework pojawia się **.NET Framework 3,5** .

    Projekty dla [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] i [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] wymagają tej wersji .NET Framework.

4. Na liście szablonów projektu wybierz **projekt SharePoint 2010**, nazwij projekt **EmployeesListDefinition**, a następnie wybierz przycisk **OK** .

5. W **Kreatorze dostosowania programu SharePoint**wprowadź adres URL witryny, która ma być używana do debugowania.

6. W obszarze **jaki jest poziom zaufania dla tego rozwiązania programu SharePoint**wybierz przycisk opcji **Wdróż jako farmę** .

   > [!NOTE]
   > Krok Uaktualnij wdrożenie nie obsługuje rozwiązań w trybie piaskownicy.

7. Wybierz przycisk **Zakończ** .

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt EmployeesListDefinition.

8. Otwórz menu skrótów dla projektu EmployeesListDefinition, wybierz **Dodaj**, a następnie wybierz **nowy element**.

9. W oknie dialogowym **Dodaj nowy element — EmployeesListDefinition** rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

10. Wybierz szablon elementu **listy** , nadaj nazwę elementowi **Employees**, a następnie wybierz przycisk **Dodaj** .

     Zostanie wyświetlony Kreator dostosowania programu SharePoint

11. Na stronie **Wybierz Ustawienia listy** Sprawdź poniższe ustawienia, a następnie wybierz przycisk **Zakończ** :

    1. **Lista pracowników** jest wyświetlana w polu **Nazwa, która ma być wyświetlana na liście?**

    2. Zostanie wybrany przycisk opcji **Utwórz listę dostosowywalną opartą na:** .

    3. **Wartość domyślna (pusta)** jest wybierana na liście **Utwórz listę dostosowywalną opartą na:** .

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy element listy pracownicy z kolumną title i jednym pustym wystąpieniem i otwiera projektanta list.

12. W projektancie list na karcie **kolumny** wybierz wiersz **Nazwa nowej lub istniejącej kolumny** , a następnie Dodaj następujące kolumny do listy **Nazwa wyświetlana kolumny** :

    1. Imię

    2. Przedsiębiorstwo

    3. Telefon służbowy

    4. E-Mail

13. Zapisz wszystkie pliki, a następnie zamknij projektanta list.

14. W **Eksplorator rozwiązań**rozwiń węzeł **Lista pracownicy** , a następnie rozwiń węzeł podrzędny **wystąpienia listy pracowników** .

15. W pliku repliks *. XML* Zastąp domyślny kod XML w tym pliku następującym kodem XML. Ten kod XML zmienia nazwę listy na **pracowników** i dodaje informacje dla pracownika o nazwie Jim Hance.

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

16. Zapisz i zamknij plik *. XML* .

17. Otwórz menu skrótów dla projektu EmployeesListDefinition, a następnie wybierz **Otwórz** lub **Właściwości**.

     Zostanie otwarty projektant właściwości.

18. Na karcie **SharePoint** wyczyść pole wyboru **automatycznie Wycofaj po debugowaniu** , a następnie Zapisz właściwości.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Aby wdrożyć definicję listy i wystąpienie listy

1. W **Eksplorator rozwiązań**wybierz węzeł projektu **EmployeesListDefinition** .

2. W oknie **Właściwości** upewnij się, że właściwość **Konfiguracja aktywnego wdrożenia** ma wartość **domyślne**.

3. Wybierz klawisz **F5** lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

4. Sprawdź, czy projekt został pomyślnie skompilowany, że przeglądarka sieci Web otworzy witrynę programu SharePoint, że element **listy** na pasku szybkiego uruchamiania zawiera listę nowych **pracowników** i że lista **pracownicy** zawiera wpis dla Jim Hance.

5. Zamknij przeglądarkę sieci Web.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Aby zmodyfikować definicję listy i wystąpienie listy i ponownie je wdrożyć

1. W projekcie EmployeesListDefinition Otwórz plik Items *. XML* , który jest elementem podrzędnym elementu projektu **wystąpienia listy pracowników** .

2. Usuń element `Data` i jego elementy podrzędne, aby usunąć z listy wpis Jim Hance.

     Po zakończeniu plik powinien zawierać następujący kod XML.

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

3. Zapisz i zamknij plik *. XML* .

4. Otwórz menu skrótów dla elementu projektu **listy Employees** , a następnie wybierz **Otwórz** lub **Właściwości**.

5. W projektancie list wybierz kartę **widoki** .

6. Na liście **wybrane kolumny** wybierz **załączniki**, a następnie wybierz klucz <, aby przenieść tę kolumnę do listy **Dostępne kolumny** .

7. Powtórz poprzedni krok, aby przenieść kolumnę **telefon służbowy** z listy **wybrane kolumny** na listę **Dostępne kolumny** .

     Ta akcja spowoduje usunięcie tych pól z widoku domyślnego listy **pracownicy** w witrynie programu SharePoint.

8. Rozpocznij debugowanie, wybierając klawisz **F5** lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

9. Sprawdź, czy pojawia się okno dialogowe **konflikty wdrożenia** .

     To okno dialogowe pojawia się, gdy program Visual Studio próbuje wdrożyć rozwiązanie (wystąpienie listy) w witrynie programu SharePoint, do której zostało już wdrożone to rozwiązanie. To okno dialogowe nie zostanie wyświetlone po wykonaniu kroku Uaktualnij wdrożenie w dalszej części tego przewodnika.

10. W oknie dialogowym **konflikty wdrożenia** wybierz przycisk opcji **Rozwiąż automatycznie** .

     Program Visual Studio usuwa wystąpienie listy w witrynie programu SharePoint, wdraża element listy w projekcie, a następnie otwiera witrynę programu SharePoint.

11. W sekcji **listy** paska szybkiego uruchamiania wybierz listę **pracownicy** , a następnie sprawdź następujące szczegóły:

    - **Załączniki** i kolumny **telefonu domowego** nie są wyświetlane w tym widoku listy.

    - Lista jest pusta. W przypadku użycia **domyślnej** konfiguracji wdrożenia w celu ponownego wdrożenia rozwiązania lista **pracowników** została zastąpiona nową listą pustą w projekcie.

## <a name="test-the-deployment-step"></a>Testowanie kroku wdrożenia
 Teraz można przystąpić do testowania kroku wdrożenia uaktualniania. Najpierw Dodaj element do wystąpienia listy w programie SharePoint. Następnie Zmień definicję listy i wystąpienie listy, Uaktualnij je w witrynie programu SharePoint i upewnij się, że krok Uaktualnij wdrożenie nie zastąpi nowego elementu.

#### <a name="to-manually-add-an-item-to-the-list"></a>Aby ręcznie dodać element do listy

1. Na Wstążce w witrynie programu SharePoint, na karcie **Narzędzia listy** wybierz kartę **elementy** .

2. W **nowej** grupie wybierz pozycję **nowy element**.

     Alternatywnie można wybrać link **Dodaj nowy element** na liście elementów.

3. W oknie **pracownicy — nowy element** w polu **tytuł** wprowadź nazwę **Menedżer obiektów**.

4. W polu **imię** wpisz **Adam**.

5. W polu **firma** wpisz **contoso**.

6. Wybierz przycisk **Zapisz** , sprawdź, czy nowy element pojawi się na liście, a następnie zamknij przeglądarkę sieci Web.

     W dalszej części tego przewodnika użyjesz tego elementu, aby sprawdzić, czy krok wdrożenia uaktualniania nie zastępuje zawartości tej listy.

#### <a name="to-test-the-upgrade-deployment-step"></a>Aby przetestować krok wdrożenia uaktualniania

1. W eksperymentalnym wystąpieniu programu Visual Studio, w **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła projektu **EmployeesListDefinition** , a następnie wybierz polecenie **Właściwości**.

    Zostanie otwarty Edytor właściwości/Projektant.

2. Na karcie **SharePoint** ustaw właściwość **Konfiguracja aktywnego wdrożenia** na **uaktualnienie**.

    Ta konfiguracja wdrożenia niestandardowego obejmuje nowy krok Uaktualnij wdrożenie.

3. Otwórz menu skrótów dla elementu projektu **listy Employees** , a następnie wybierz **Właściwości** lub **Otwórz**.

    Zostanie otwarty Edytor właściwości/Projektant.

4. Na karcie **widoki** wybierz kolumnę **wiadomość E-mail** , a następnie wybierz klucz **<** , aby przenieść tę kolumnę z listy **wybrane kolumny** na listę **Dostępne kolumny** .

    Ta akcja spowoduje usunięcie tych pól z widoku domyślnego listy **pracownicy** w witrynie programu SharePoint.

5. Rozpocznij debugowanie, wybierając klawisz **F5** lub na pasku menu wybierz **Debuguj** > **Rozpocznij debugowanie**.

6. Sprawdź, czy kod w innym wystąpieniu programu Visual Studio jest zatrzymany w punkcie przerwania, który został ustawiony wcześniej w metodzie `CanExecute`.

7. Wybierz ponownie klawisz **F5** lub na pasku menu wybierz kolejno opcje **Debuguj** > **Kontynuuj**.

8. Sprawdź, czy kod został zatrzymany w punkcie przerwania, który został ustawiony wcześniej w metodzie `Execute`.

9. Wybierz klawisz **F5** lub na pasku menu wybierz kolejno opcje **Debuguj** > **Kontynuuj** czas ostateczny.

     Przeglądarka sieci Web otworzy witrynę programu SharePoint.

10. W sekcji **listy** obszaru szybkie uruchamianie wybierz listę **pracownicy** , a następnie sprawdź następujące szczegóły:

    - Element, który został ręcznie dodany wcześniej (dla Adam, Menedżer obiektów) nadal znajduje się na liście.

    - Kolumny **telefon służbowy** i **adres E-mail** nie są wyświetlane w tym widoku listy.

      Konfiguracja wdrożenia **uaktualniania** modyfikuje istniejące wystąpienie listy **Employees** w witrynie programu SharePoint. Jeśli zamiast konfiguracji **uaktualnienia** użyto **domyślnej** konfiguracji wdrożenia, wystąpi konflikt wdrożenia. Program Visual Studio rozwiązał konflikt, zastępując listę **pracownicy** i element dla elementu "Adam", Menedżer obiektów, który zostanie usunięty.

## <a name="clean-up-the-development-computer"></a>Czyszczenie komputera deweloperskiego
 Po zakończeniu testowania wdrożenia Uaktualnij, Usuń wystąpienie listy i definicję listy z witryny programu SharePoint, a następnie Usuń rozszerzenie kroku wdrożenia z programu Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Aby usunąć wystąpienie listy z witryny programu SharePoint

1. Otwórz listę **pracownicy** w witrynie programu SharePoint, jeśli lista nie jest jeszcze otwarta.

2. Na Wstążce w witrynie programu SharePoint wybierz kartę **listy narzędzia** , a następnie wybierz kartę **Lista** .

3. W grupie **Ustawienia** wybierz element **Ustawienia listy** .

4. W obszarze **uprawnienia i zarządzanie**wybierz polecenie **Usuń tę listę** , wybierz **przycisk OK** , aby potwierdzić, że chcesz wysłać listę do kosza, a następnie zamknij przeglądarkę sieci Web.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Aby usunąć definicję listy z witryny programu SharePoint

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **kompilacja** > **wycofywanie**.

     Program Visual Studio wycofuje definicję listy z witryny programu SharePoint.

#### <a name="to-uninstall-the-extension"></a>Aby odinstalować rozszerzenie

1. W eksperymentalnym wystąpieniu programu Visual Studio na pasku menu wybierz kolejno opcje **narzędzia** > **rozszerzenia i aktualizacje**.

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Na liście rozszerzeń wybierz **krok Uaktualnij wdrożenie dla projektów programu SharePoint**, a następnie wybierz polecenie **Odinstaluj** .

3. W wyświetlonym oknie dialogowym wybierz pozycję **tak** , aby potwierdzić, że chcesz odinstalować rozszerzenie, a następnie wybierz pozycję **Uruchom ponownie teraz** , aby ukończyć dezinstalację.

4. Zamknij oba wystąpienia programu Visual Studio (wystąpienie eksperymentalne i wystąpienie programu Visual Studio, w którym jest otwarte rozwiązanie UpgradeDeploymentStep).

## <a name="see-also"></a>Zobacz także
- [Rozszerzona pakowanie i wdrażanie programu SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
