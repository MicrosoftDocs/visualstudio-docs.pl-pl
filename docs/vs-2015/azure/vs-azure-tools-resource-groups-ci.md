---
title: Ciągła integracja w usługom DevOps platformy Azure przy użyciu projekty grupy zasobów platformy Azure | Dokumentacja firmy Microsoft
description: W tym artykule opisano sposób konfigurowania ciągłej integracji w usługach infrastruktury DevOps platformy Azure przy użyciu projekty wdrażania grupy zasobów platformy Azure w programie Visual Studio.
author: mlearned
manager: jillfra
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: 490ad7e4ee8bcc59530a06ec4eba151e88806028
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079503"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Ciągła integracja w usługom DevOps platformy Azure przy użyciu projekty wdrażania grupy zasobów platformy Azure

Aby wdrożyć szablon platformy Azure, należy wykonać zadania w poszczególnych etapach: Kopiuj kompilacji, testów, na platformie Azure (zwane również "Staging") i wdrożyć szablon. Istnieją dwa różne sposoby wdrażania szablonów usługom DevOps platformy Azure. Obie metody zapewniają takie same wyniki, więc wybierz ten, który najlepiej pasuje do przepływu pracy.

1. Dodaj pojedynczego kroku do potoku Twojej kompilacji, który uruchamia skrypt programu PowerShell, który znajduje się w projekcie wdrożenia grupy zasobów platformy Azure (wdrażanie AzureResourceGroup.ps1). Skrypt kopiuje artefakty, a następnie wdrażania szablonu.
2. Dodaj wielu usługom DevOps platformy Azure kroków kompilacji, każdy z nich do wykonania zadania etapu.

W tym artykule przedstawiono obie opcje. Pierwszym z nich ma tę zaletę przy użyciu tego samego skryptu, które są używane przez deweloperów w programie Visual Studio i zapewniając spójność w całym cyklu życia. Drugiej opcji można używać zamiast wbudowanego skryptu. Obie procedury przyjęto założenie, że masz już program Visual Studio Projekt wdrożenia sprawdzone w usługom DevOps platformy Azure.

## <a name="copy-artifacts-to-azure"></a>Kopiowanie artefaktów na platformie Azure
Niezależnie od tego, w tym scenariuszu jeśli masz wszelkie artefakty, które są potrzebne do wdrożenia szablonu, musisz udzielić dostępu do usługi Azure Resource Manager do nich. Te artefakty mogą zawierać pliki takie jak:

* Zagnieżdżone szablony
* Konfiguracja i skryptów DSC
* Pliki binarne aplikacji

### <a name="nested-templates-and-configuration-scripts"></a>Zagnieżdżone szablony i skryptami konfiguracyjnymi
Jeśli używasz szablonu dostępnego w programie Visual Studio (lub skompilowane przy użyciu fragmentów kodu programu Visual Studio), skrypt programu PowerShell przygotowuje nie tylko artefakty, parametryzuje dane również identyfikator URI zasobów dla różnych wdrożeń. Skrypt, a następnie kopiuje artefakty do bezpiecznego kontenera na platformie Azure, tworzy token SaS dla kontenera i następnie przekazuje informację do wdrożenia szablonu. Zobacz [Utwórz wdrożenie szablonu](https://msdn.microsoft.com/library/azure/dn790564.aspx) Aby dowiedzieć się więcej na temat szablonów zagnieżdżonych.  Korzystając z zadań w usługom DevOps platformy Azure, należy wybrać odpowiednie zadania dla wdrożenia szablonu i jeśli to konieczne, przekazać wartości parametru z kroku przemieszczania do wdrożenia szablonu.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Skonfiguruj ciągłe wdrażanie w potokach platformy Azure
Aby wywołać skrypt programu PowerShell w potokach platformy Azure, musisz zaktualizować swój potok kompilacji. Krótko mówiąc czynności są następujące:

1. Edytuj proces kompilacji.
2. Konfigurowanie autoryzacji platformy Azure w potokach platformy Azure.
3. Dodaj krok kompilacji programu Azure PowerShell, który odwołuje się do skryptu programu PowerShell w projekcie wdrożenia grupy zasobów platformy Azure.
4. Ustaw wartość *- ArtifactsStagingDirectory* parametru, aby pracować z projektem, utworzone w potokach platformy Azure.

### <a name="detailed-walkthrough-for-option-1"></a>Szczegółowy przewodnik dotyczący korzystania opcję 1
Poniższe procedury opisują kroki niezbędne do skonfigurowania ciągłego wdrażania w usłudze Azure Services DevOps za pomocą pojedynczego zadania, które uruchamia skrypt programu PowerShell w projekcie.

1. Edytuj swój potok kompilacji usługom DevOps platformy Azure i Dodaj krok kompilacji programu Azure PowerShell. Wybierz proces kompilacji w ramach **tworzyć potoki** kategorii, a następnie wybierz **Edytuj** łącza.

   ![Edytuj potoku kompilacji](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png)
2. Dodaj nową **programu Azure PowerShell** krok do potoku kompilacji kompilacji, a następnie wybierz **Dodaj krok kompilacji...** przycisk.

   ![Dodaj krok kompilacji](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png)
3. Wybierz **zadania wdrażania** kategorii, wybierz opcję **programu Azure PowerShell** zadań, a następnie wybierz jego **Dodaj** przycisku.

   ![Dodaj zadania](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png)
4. Wybierz **programu Azure PowerShell** krok kompilacji, a następnie wypełnij jego wartości.

   1. Jeśli masz już dodany do usługi Azure DevOps Services punktu końcowego usługi platformy Azure, wybierz subskrypcję, w **subskrypcji platformy Azure** polu listy rozwijanej, a następnie przejdź do następnej sekcji.

      Jeśli w usługom DevOps platformy Azure, nie ma punktu końcowego usługi platformy Azure, musisz dodać jeden. W tej podsekcji przeprowadzi Cię przez proces. Jeśli Twoje konto platformy Azure korzysta z konta Microsoft (np. usługi Hotmail), należy wykonać poniższe kroki, aby uzyskać uwierzytelnianie jednostki usługi.

   2. Wybierz **Zarządzaj** łącze obok **subskrypcji platformy Azure** pole listy rozwijanej.

      ![Zarządzanie subskrypcjami platformy Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png)
   3. Wybierz **Azure** w **nowy punkt końcowy usługi** pole listy rozwijanej.

      ![Nowy punkt końcowy usługi](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png)
   4. W **dodawania subskrypcji platformy Azure** okno dialogowe, wybierz opcję **nazwy głównej usługi** opcji.

      ![Opcja nazwy głównej usługi](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png)
   5. Dodaj informacje o subskrypcji platformy Azure do **dodawania subskrypcji platformy Azure** okno dialogowe. Należy podać następujące elementy:

      * Identyfikator subskrypcji
      * Nazwa subskrypcji
      * Identyfikator jednostki usługi
      * Klucz jednostki usługi
      * Identyfikator dzierżawy
   6. Dodaj nazwę wybranej do **subskrypcji** pola Nazwa podmiotu. Ta wartość znajduje się dalej w **subskrypcji platformy Azure** listy rozwijanej w usługom DevOps platformy Azure.

   7. Jeśli nie znasz Identyfikatora subskrypcji platformy Azure, można użyć jednej z poniższych poleceń, pobrać go.

      Dla skryptów programu PowerShell użyj polecenia:

      `Get-AzureRmSubscription`

      W przypadku interfejsu wiersza polecenia platformy Azure użyj polecenia:

      `azure account show`
   8. Aby uzyskać identyfikator jednostki usługi, klucz jednostki usługi i identyfikator dzierżawy, postępuj zgodnie z procedurą w [aplikacji Utwórz usługi Active Directory i jednostki usługi przy użyciu portalu](/azure/azure-resource-manager/resource-group-create-service-principal-portal) lub [uwierzytelniania jednostki usługi przy użyciu platformy Azure Menedżer zasobów](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Dodaj wartości identyfikator jednostki usługi, klucz jednostki usługi i identyfikator dzierżawy w **dodawania subskrypcji platformy Azure** okna dialogowego pole, a następnie wybierz **OK** przycisku.

      Masz teraz prawidłowe nazwy głównej usługi można użyć, aby uruchomić skrypt programu Azure PowerShell.
5. Edytuj potoku kompilacji, a następnie wybierz **programu Azure PowerShell** krok kompilacji. Wybierz subskrypcję, w **subskrypcji platformy Azure** pole listy rozwijanej. (Jeśli subskrypcja nie jest wyświetlany, wybierz opcję **Odśwież** obok przycisku **Zarządzaj** łącza.)

   ![Konfigurowanie zadania kompilacji programu Azure PowerShell](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png)
6. Podaj ścieżkę do skryptu programu PowerShell AzureResourceGroup.ps1 wdrażania. Aby to zrobić, wybierz przycisk wielokropka (...) obok **ścieżka skryptu** , przejdź do skryptu środowiska PowerShell wdrażanie AzureResourceGroup.ps1 w **skrypty** folder projektu, wybierz go, a następnie Wybierz **OK** przycisku.

   ![Wybierz ścieżkę do skryptu](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png)
7. Po zaznaczeniu skryptu zaktualizuj ścieżkę do skryptu, dzięki czemu jest uruchamiany z Build.StagingDirectory (tym samym katalogu, *ArtifactsLocation* jest równa). Można to zrobić, dodając "$(Build.StagingDirectory)/"do stanu sprzed ścieżka skryptu.

    ![Edytuj ścieżkę do skryptu](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png)
8. W **argumenty skryptu** wprowadź następujące parametry (w jednym wierszu). Po uruchomieniu skryptu w programie Visual Studio, można sprawdzić, jak VS używa parametrów w **dane wyjściowe** okna. Umożliwia to jako punktu wyjścia do ustawiania wartości parametrów w kroku Twojej kompilacji.

   | Parametr | Opis |
   | --- | --- |
   | -ResourceGroupLocation |Wartość lokalizacji geograficznej, gdy grupa zasobów znajduje się, takie jak **eastus** lub **wschodnie stany USA**. (Dodaj pojedynczego apostrofu, jeśli ma to miejsce w nazwie). Zobacz [regionów platformy Azure](https://azure.microsoft.com/regions/) Aby uzyskać więcej informacji. |
   | -ResourceGroupName |Nazwa grupy zasobów, użyty dla tego wdrożenia. |
   | -UploadArtifacts |Tego parametru, jeśli jest obecny, określa, że artefakty, które należy przekazać na platformę Azure z systemu lokalnego. Należy ustawić tego przełącznika, jeśli wdrożenie szablonu wymaga dodatkowego artefaktów, które mają zostać przygotowane za pomocą skryptu programu PowerShell (takich jak skrypty konfiguracji lub zagnieżdżone szablony). |
   | -StorageAccountName |Nazwa konta magazynu używany do etapu artefaktów dla tego wdrożenia. Ten parametr jest używany tylko, jeśli są przemieszczania artefaktów dla wdrożenia. Jeśli parametr ten zostanie dostarczony, nowe konto magazynu zostanie utworzony, jeśli skrypt nie został utworzony w poprzednim wdrożeniu. Jeśli parametr jest określony, konto magazynu musi już istnieć. |
   | -StorageAccountResourceGroupName |Nazwa grupy zasobów skojarzonych z kontem magazynu. Ten parametr jest wymagany tylko wtedy, gdy chcesz podać wartość dla parametru StorageAccountName. |
   | -TemplateFile |Ścieżka do pliku szablonu w projekcie wdrożenia grupy zasobów platformy Azure. Aby zwiększyć elastyczność, należy użyć ścieżki dla tego parametru, która jest względem lokalizacji pliku skryptu programu PowerShell, a nie ścieżkę bezwzględną. |
   | -TemplateParametersFile |Ścieżka do pliku parametrów w projekcie wdrożenia grupy zasobów platformy Azure. Aby zwiększyć elastyczność, należy użyć ścieżki dla tego parametru, która jest względem lokalizacji pliku skryptu programu PowerShell, a nie ścieżkę bezwzględną. |
   | -ArtifactStagingDirectory |Ten parametr umożliwia programu PowerShell, skrypt znany folder, w której powinny zostać skopiowane pliki binarne projektu. Ta wartość zastępuje wartość domyślna używana przez skrypt programu PowerShell. Usługom DevOps platformy Azure do używania, ustaw wartość: - ArtifactStagingDirectory $(Build.StagingDirectory) |

   Oto przykład argumenty skryptu (linia jest uszkodzona czytelności):

   ```
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json'
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct'
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'
   ```

   Gdy skończysz, **argumenty skryptu** pole powinna przypominać przedstawioną poniżej:

   ![Argumenty skryptu](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png)
9. Po dodaniu wymagane elementy do kroku kompilacji programu Azure PowerShell, wybierz **kolejki** kompilacji przycisk, aby skompilować projekt. **Kompilacji** ekran przedstawia dane wyjściowe skryptu programu PowerShell.

### <a name="detailed-walkthrough-for-option-2"></a>Szczegółowy przewodnik dotyczący korzystania z opcji 2
Poniższe procedury opisują czynności niezbędne do skonfigurowania ciągłego wdrażania w usłudze Azure Services DevOps za pomocą wbudowanych zadań.

1. Edytuj potoku kompilacji usługom DevOps platformy Azure, aby dodać dwa nowe kroki kompilacji. Wybierz proces kompilacji w ramach **definicje kompilacji** kategorii, a następnie wybierz **Edytuj** łącza.

   ![Edytuj definicję kompilacji](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png)
2. Dodaj nowe kroki kompilacji do potoku kompilacji przy użyciu **Dodaj krok kompilacji...** przycisk.

   ![Dodaj krok kompilacji](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png)
3. Wybierz **Wdróż** kategorii zadanie, wybierz opcję **kopiowania plików na platformę Azure** zadań, a następnie wybierz jego **Dodaj** przycisku.

   ![Dodaj zadanie kopiowania plików na platformę Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png)
4. Wybierz **wdrożenie grupy zasobów Azure** zadań, a następnie wybierz jego **Dodaj** przycisku i następnie **Zamknij** **wykazu zadań**.

   ![Dodaj zadanie wdrożenia grupy zasobów platformy Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png)
5. Wybierz **kopiowania plików na platformę Azure** zadań, a następnie wypełnij jego wartości.

   Jeśli masz już dodany do usługi Azure DevOps Services punktu końcowego usługi platformy Azure, wybierz subskrypcję, w **subskrypcji platformy Azure** pole listy rozwijanej. Jeśli nie masz subskrypcji, zobacz [opcja 1](#detailed-walkthrough-for-option-1) instrukcje dotyczące konfigurowania w usługom DevOps platformy Azure.

   * Source — naciśnij klawisz enter **$(Build.StagingDirectory)**
   * Typ połączenia platformy Azure — wybierz **usługi Azure Resource Manager**
   * Subskrypcja platformy Azure RM - Wybierz subskrypcję dla konta magazynu, które mają być używane w **subskrypcji platformy Azure** pole listy rozwijanej. Jeśli subskrypcja nie jest wyświetlany, wybierz opcję **Odśwież** obok przycisku **Zarządzaj** łącza.
   * Typ docelowy — umożliwia wybór **obiektów Blob platformy Azure**
   * Menedżer zasobów konta magazynu — wybierz konto magazynu ma być używana do przemieszczania artefaktów
   * Nazwa kontenera — wprowadź nazwę kontenera, o których chcesz użyć dla przemieszczania; go może być dowolną nazwę prawidłowego kontenera, ale użyj jednej przeznaczonych dla tego potoku kompilacji

   W przypadku wartości danych wyjściowych:

   * Wprowadź kontenera magazynu URI - **artifactsLocation**
   * Token sygnatury dostępu Współdzielonego kontenera magazynu — wprowadź **artifactsLocationSasToken**

   ![Konfigurowanie zadania kopiowania plików na platformę Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png)
6. Wybierz **wdrożenie grupy zasobów Azure** krok kompilacji, a następnie wypełnij jego wartości.

   * Typ połączenia platformy Azure — wybierz **usługi Azure Resource Manager**
   * Subskrypcja platformy Azure RM - Wybierz subskrypcję do użycia we wdrożeniach **subskrypcji platformy Azure** pole listy rozwijanej. Są to zazwyczaj tej samej subskrypcji, które są używane w poprzednim kroku
   * Akcja — wybierz **tworzenia lub zaktualizować grupy zasobów**
   * Grupy zasobów — wybierz grupę zasobów lub wprowadź nazwę nowej grupy zasobów dla wdrożenia
   * Lokalizacja — wybierz lokalizację grupy zasobów
   * Szablon — wprowadź ścieżkę i nazwę szablonu do wdrożenia AS **$(Build.StagingDirectory)**, na przykład: **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Parametry szablonu — wprowadź ścieżkę i nazwę parametrów, które ma być używany, AS **$(Build.StagingDirectory)**, na przykład: **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Przesłanianie parametrów szablonu — wpisz lub skopiuj i wklej następujący kod:

     ```
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```

     ![Konfigurowanie zadania wdrożenia grupy zasobów platformy Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png)
7. Po dodaniu wymagane elementy Zapisz potoku kompilacji i wybierz polecenie **nową kompilację w kolejce** u góry.

## <a name="next-steps"></a>Następne kroki

Odczyt [Omówienie usługi Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) Aby dowiedzieć się więcej na temat usługi Azure Resource Manager i grupy zasobów platformy Azure.