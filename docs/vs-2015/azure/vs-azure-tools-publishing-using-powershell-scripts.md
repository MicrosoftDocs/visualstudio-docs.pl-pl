---
title: Publikowanie w środowiskach deweloperskich i testowych przy użyciu skryptów środowiska Windows PowerShell | Microsoft Docs
description: Dowiedz się, jak publikować w środowiskach deweloperskich i testowych przy użyciu skryptów środowiska Windows PowerShell z programu Visual Studio.
author: ghogen
manager: jillfra
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: a6d6611c8ce8bdb09023794b5eca029b6b972afb
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849986"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Publikowanie w środowisku deweloperskim i testowym za pomocą skryptów programu Windows PowerShell

Podczas tworzenia aplikacji sieci Web w programie Visual Studio można wygenerować skrypt programu Windows PowerShell, za pomocą którego można później zautomatyzować publikowanie witryny sieci Web na platformie Azure jako aplikację internetową w Azure App Service lub maszynie wirtualnej. Można edytować i rozbudować skrypt programu Windows PowerShell w edytorze programu Visual Studio zgodnie z wymaganiami lub zintegrować skrypt z istniejącymi skryptami kompilacji, testowania i publikowania.

Korzystając z tych skryptów, można zarezerwować dostosowane wersje (znane również jako środowiska deweloperskie i testowe) lokacji do tymczasowego użytku. Na przykład możesz skonfigurować określoną wersję witryny sieci Web na maszynie wirtualnej platformy Azure lub w miejscu przejściowym w witrynie sieci Web, aby uruchomić zestaw testów, odtworzyć usterkę, przetestować poprawkę błędów, proponowaną zmianę w wersji próbnej lub skonfigurować środowisko niestandardowe dla pokazu lub prezentacji. Po utworzeniu skryptu, który publikuje projekt, można odtworzyć identyczne środowiska przez ponowne uruchomienie skryptu w razie potrzeby lub uruchomić skrypt przy użyciu własnej kompilacji aplikacji sieci Web, aby utworzyć niestandardowe środowisko do testowania.

## <a name="prerequisites"></a>Wymagania wstępne

* Zestaw Azure SDK 2,3 lub nowszy. Zobacz [pliki do pobrania w programie Visual Studio](https://visualstudio.microsoft.com/downloads/). (Zestaw Azure SDK nie jest potrzebny do generowania skryptów dla projektów sieci Web. Ta funkcja jest przeznaczony dla projektów sieci Web, a nie ról sieci Web w usługach Cloud Services.
* Azure PowerShell 0.7.4 lub nowszy. Zobacz artykuł [Instalowanie i konfigurowanie programu Azure PowerShell](/powershell/azure/overview).
* Program [Windows PowerShell 3,0](https://docs.microsoft.com/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control) lub nowszy.

## <a name="additional-tools"></a>Dodatkowe narzędzia

Dostępne są dodatkowe narzędzia i zasoby umożliwiające pracę z programem PowerShell w programie Visual Studio dla deweloperów platformy Azure. Zobacz [PowerShell Tools for Visual Studio](https://visualstudiogallery.msdn.microsoft.com/c9eb3ba8-0c59-4944-9a62-6eee37294597).

## <a name="generating-the-publish-scripts"></a>Generowanie skryptów publikowania

Można generować skrypty publikowania dla maszyny wirtualnej, która hostuje witrynę internetową podczas tworzenia nowego projektu, wykonując [te instrukcje](/azure/virtual-machines/windows/classic/web-app-visual-studio?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Możesz również [generować skrypty publikowania dla aplikacji sieci Web w Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Skrypty generowane przez program Visual Studio

Program Visual Studio generuje folder na poziomie rozwiązania o nazwie **PublishScripts** , który zawiera dwa pliki programu Windows PowerShell, skrypt publikacji dla maszyny wirtualnej lub witryny sieci Web oraz moduł, który zawiera funkcje, których można użyć w skryptach. Program Visual Studio generuje również plik w formacie JSON, który określa szczegóły projektu, który jest wdrażany.

### <a name="windows-powershell-publish-script"></a>Skrypt publikacji programu Windows PowerShell

Skrypt publikacji zawiera określone kroki publikowania dotyczące wdrażania w witrynie sieci Web lub na maszynie wirtualnej. Program Visual Studio oferuje kolorowanie składni dla rozwoju programu Windows PowerShell. Pomoc dla funkcji jest dostępna i można swobodnie edytować funkcje w skrypcie, aby odpowiadały na zmieniające się wymagania.

### <a name="windows-powershell-module"></a>Moduł programu Windows PowerShell

Moduł programu Windows PowerShell generowany przez program Visual Studio zawiera funkcje, które są używane przez skrypt publikacji. Te Azure PowerShell funkcje nie są przeznaczone do zmodyfikowania. Zobacz artykuł [Instalowanie i konfigurowanie programu Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Plik konfiguracji JSON

Plik JSON zostanie utworzony w folderze **konfiguracje** i zawiera dane konfiguracyjne, które określają, które zasoby należy wdrożyć na platformie Azure. Nazwa pliku generowanego przez program Visual Studio to Project-Name-WAWS-dev. JSON, jeśli utworzono witrynę sieci Web lub nazwę projektu-VM-dev. JSON, jeśli utworzono maszynę wirtualną. Oto przykład pliku konfiguracji JSON, który jest generowany podczas tworzenia witryny sieci Web. Większość wartości nie wymaga wyjaśnień. Nazwa witryny sieci Web jest generowana przez platformę Azure, więc może być niezgodna z nazwą projektu.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

Podczas tworzenia maszyny wirtualnej plik konfiguracji JSON wygląda podobnie do poniższego. Usługa w chmurze jest tworzona jako kontener dla maszyny wirtualnej. Maszyna wirtualna zawiera zwykłe punkty końcowe dla dostępu do sieci Web za pośrednictwem protokołów HTTP i HTTPS, a także punkty końcowe dla Web Deploy, które umożliwiają publikowanie w witrynie sieci Web z komputera lokalnego, Pulpit zdalny i programu Windows PowerShell.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Konfigurację JSON można edytować, aby zmienić działanie wykonywane po uruchomieniu skryptów publikacji. Sekcje `cloudService` i `virtualMachine` są wymagane, ale można usunąć sekcję `databases`, jeśli nie jest ona potrzebna. Właściwości, które są puste w domyślnym pliku konfiguracyjnym generowanym przez program Visual Studio, są opcjonalne; te właściwości, które mają wartości w domyślnym pliku konfiguracji, są wymagane.

Jeśli masz witrynę sieci Web, która ma wiele środowisk wdrażania (nazywanych miejscami), a nie pojedynczej lokacji produkcyjnej na platformie Azure, możesz dołączyć nazwę miejsca w nazwie witryny sieci Web w pliku konfiguracyjnym JSON. Jeśli na przykład masz witrynę sieci Web o nazwie **Moja witryna** i gniazdo o nazwie **test** , identyfikator URI jest `mysite-test.cloudapp.net`, ale poprawna nazwa do użycia w pliku konfiguracji to moja witryna (test). Tę czynność można wykonać tylko wtedy, gdy witryna sieci Web i gniazda już istnieją w Twojej subskrypcji. Jeśli nie istnieją, Utwórz witrynę sieci Web, uruchamiając skrypt bez określania miejsca, a następnie utwórz miejsce w [Azure Portal](https://portal.azure.com/), a następnie uruchom skrypt ze zmodyfikowaną nazwą witryny sieci Web. Aby uzyskać więcej informacji na temat miejsc wdrożenia dla aplikacji sieci Web, zobacz [Konfigurowanie środowisk przejściowych dla aplikacji sieci Web w Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Jak uruchomić skrypty publikowania

Jeśli wcześniej nie uruchomiono skryptu środowiska Windows PowerShell, należy najpierw ustawić zasady wykonywania, aby włączyć uruchamianie skryptów. Zasady są funkcją zabezpieczeń, która uniemożliwia użytkownikom uruchamianie skryptów programu Windows PowerShell, jeśli są one podatne na złośliwe oprogramowanie lub wirusy, które wymagają wykonywania skryptów.

### <a name="run-the-script"></a>Uruchamianie skryptu

1. Utwórz pakiet Web Deploy dla projektu. Pakiet Web Deploy to skompresowany plik archiwalny (zip) zawierający pliki, które mają zostać skopiowane do witryny sieci Web lub maszyny wirtualnej. W programie Visual Studio można tworzyć pakiety Web Deploy dla dowolnej aplikacji sieci Web.

   ![Utwórz pakiet Web Deploy](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Aby uzyskać więcej informacji, zobacz [How to: Create a Web Deployment Package in Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). Możesz również zautomatyzować tworzenie pakietu Web Deploy, zgodnie z opisem w temacie [Dostosowywanie i rozszerzanie skryptów publikacji](#customizing-and-extending-the-publish-scripts).

1. W **Eksplorator rozwiązań**Otwórz menu kontekstowe dla skryptu, a następnie wybierz **Otwórz za pomocą programu PowerShell ISE**.
1. Jeśli uruchamiasz skrypty środowiska Windows PowerShell na tym komputerze po raz pierwszy, Otwórz okno wiersza polecenia z uprawnieniami administratora i wpisz następujące polecenie:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Zaloguj się do platformy Azure przy użyciu następującego polecenia.

    ```powershell
    Add-AzureAccount
    ```

    Po wyświetleniu monitu podaj nazwę użytkownika i hasło.

    Należy pamiętać, że w przypadku automatyzowania skryptu ta metoda udostępniania poświadczeń platformy Azure nie działa. Zamiast tego należy użyć pliku `.publishsettings`, aby podać poświadczenia. Tylko jednorazowo Użyj polecenia **Get-AzurePublishSettingsFile** , aby pobrać plik z platformy Azure, a następnie zaimportuj plik przy użyciu pliku **Import-AzurePublishSettingsFile** . Aby uzyskać szczegółowe informacje, zobacz [How to install and configure Azure PowerShell (Jak zainstalować i skonfigurować program Azure PowerShell)](/powershell/azure/overview).

1. Obowiązkowe Jeśli chcesz utworzyć zasoby platformy Azure, takie jak maszyna wirtualna, baza danych i witryna internetowa bez publikowania aplikacji sieci Web, użyj polecenia **Publish-WebApplication. ps1** z argumentem **-Configuration** ustawionym na plik konfiguracji JSON. Ten wiersz polecenia używa pliku konfiguracji JSON do określenia zasobów do utworzenia. Ponieważ używa ustawień domyślnych dla innych argumentów wiersza polecenia, tworzy zasoby, ale nie publikuje aplikacji sieci Web. Opcja – verbose zawiera więcej informacji na temat tego, co się dzieje.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Użyj polecenia **Publish-WebApplication. ps1** , jak pokazano w jednym z poniższych przykładów, aby wywołać skrypt i opublikować aplikację sieci Web. Jeśli zachodzi potrzeba zastąpienia ustawień domyślnych dla dowolnego z innych argumentów, takich jak nazwa subskrypcji, nazwa pakietu publikowania, poświadczenia maszyny wirtualnej lub poświadczenia serwera bazy danych, można określić te parametry. Użyj opcji **– verbose** , aby wyświetlić więcej informacji o postępie procesu publikowania.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Jeśli tworzysz maszynę wirtualną, polecenie wygląda podobnie do poniższego. Ten przykład pokazuje również, jak określić poświadczenia dla wielu baz danych. W przypadku maszyn wirtualnych tworzonych przez te skrypty certyfikat SSL nie pochodzi z zaufanego głównego urzędu certyfikacji. W związku z tym należy użyć opcji **– AllowUntrusted** .

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    Skrypt może tworzyć bazy danych, ale nie tworzy serwerów baz danych. Jeśli chcesz utworzyć serwer bazy danych, możesz użyć funkcji **New-AzureSqlDatabaseServer** w module platformy Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Dostosowywanie i rozszerzanie skryptów publikowania

Można dostosować skrypt publikacji i plik konfiguracji JSON. Nie ma potrzeby modyfikowania funkcji w module programu Windows PowerShell **AzureWebAppPublishModule. PSM1** . Jeśli chcesz tylko określić inną bazę danych lub zmienić niektóre właściwości maszyny wirtualnej, edytuj plik konfiguracji JSON. Jeśli chcesz zwiększyć funkcjonalność skryptu w celu zautomatyzowania kompilowania i testowania projektu, można zaimplementować klasy zastępcze w **Publish-WebApplication. ps1**.

Aby zautomatyzować Kompilowanie projektu, Dodaj kod wywołujący MSBuild do `New-WebDeployPackage`, jak pokazano w tym przykładzie kodu. Ścieżka do polecenia MSBuild jest inna w zależności od zainstalowanej wersji programu Visual Studio. Aby uzyskać poprawną ścieżkę, można użyć funkcji **Get-MSBuildCmd**, jak pokazano w tym przykładzie.

### <a name="to-automate-building-your-project"></a>Aby zautomatyzować Kompilowanie projektu

1. Dodaj parametr `$ProjectFile` w sekcji Global PARAM.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Skopiuj funkcję `Get-MSBuildCmd` do pliku skryptu.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. Zastąp `New-WebDeployPackage` poniższym kodem i Zastąp symbole zastępcze w wierszu konstrukcja `$msbuildCmd`. Ten kod jest przeznaczony dla programu Visual Studio 2015. Jeśli używasz programu Visual Studio 2017, Zmień właściwość **VisualStudioVersion** na `15.0` (`12.0` dla Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Aby skompilować aplikację sieci Web, użyj programu MsBuild. exe. Aby uzyskać pomoc, zobacz informacje w wierszu polecenia programu MSBuild w: [http://go.microsoft.com/fwlink/?LinkId=391339](https://msdn.microsoft.com/library/ms164311.aspx)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Rozpocznij wykonywanie polecenia Build

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. Wywołaj funkcję `New-WebDeployPackage` przed tym wierszem: `$Config = Read-ConfigFile $Configuration` dla aplikacji sieci Web lub `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` dla maszyn wirtualnych.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Wywołaj dostosowany skrypt z wiersza polecenia przy użyciu argumentu `$Project`, tak jak w poniższym przykładzie:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Aby zautomatyzować testowanie aplikacji, Dodaj kod do `Test-WebApplication`. Pamiętaj, aby usunąć komentarz z wierszy w **Publish-WebApplication. ps1** , gdy te funkcje są wywoływane. Jeśli nie podano implementacji, możesz ręcznie skompilować projekt przy użyciu programu Visual Studio, a następnie uruchomić skrypt publikacji w celu opublikowania na platformie Azure.

## <a name="publishing-function-summary"></a>Publikowanie podsumowania funkcji
Aby uzyskać pomoc dotyczącą funkcji, których można użyć w wierszu polecenia programu Windows PowerShell, użyj polecenia `Get-Help function-name`. Pomoc zawiera pomoc i przykłady parametrów. Ten sam tekst pomocy znajduje się również w plikach źródłowych skryptu **AzureWebAppPublishModule. PSM1** i **Publish-WebApplication. ps1**. Skrypt i pomoc są zlokalizowane w języku programu Visual Studio.

**AzureWebAppPublishModule**

| Nazwa funkcji | Opis |
| --- | --- |
| Add-AzureSQLDatabase |Tworzy nową bazę danych SQL Azure. |
| Add-AzureSQLDatabases |Tworzy bazy danych SQL platformy Azure na podstawie wartości w pliku konfiguracyjnym JSON, który generuje program Visual Studio. |
| Add-AzureVM |Tworzy maszynę wirtualną platformy Azure i zwraca adres URL wdrożonej maszyny wirtualnej. Funkcja konfiguruje wymagania wstępne, a następnie wywołuje funkcję **New-AzureVM** (moduł platformy Azure), aby utworzyć nową maszynę wirtualną. |
| Add-AzureVMEndpoints |Dodaje nowe wejściowe punkty końcowe do maszyny wirtualnej i zwraca maszynę wirtualną z nowym punktem końcowym. |
| Add-AzureVMStorage |Tworzy nowe konto usługi Azure Storage w bieżącej subskrypcji. Nazwa konta rozpoczyna się od ciągu "DevTest", po którym następuje unikatowy ciąg alfanumeryczny. Funkcja zwraca nazwę nowego konta magazynu. Określ lokalizację lub grupę koligacji dla nowego konta magazynu. |
| Add-AzureWebsite |Tworzy witrynę sieci Web o określonej nazwie i lokalizacji. Ta funkcja wywołuje funkcję **New-AzureWebsite** w module platformy Azure. Jeśli subskrypcja nie zawiera jeszcze witryny sieci Web o określonej nazwie, ta funkcja utworzy witrynę sieci Web i zwróci obiekt witryny sieci Web. W przeciwnym razie zwraca `$null`. |
| Backup-Subscription |Zapisuje bieżącą subskrypcję platformy Azure w zmiennej `$Script:originalSubscription` w zakresie skryptu. Ta funkcja zapisuje bieżącą subskrypcję platformy Azure (uzyskaną przez `Get-AzureSubscription -Current`) i jej konto magazynu oraz subskrypcję, która została zmieniona przez ten skrypt (zapisany w zmiennej `$UserSpecifiedSubscription`) i jego konto magazynu w zakresie skryptu. Zapisując wartości, można użyć funkcji, takiej jak `Restore-Subscription`, aby przywrócić oryginalną bieżącą subskrypcję i konto magazynu na bieżący stan, jeśli bieżący stan zmienił się. |
| Find-AzureVM |Pobiera określoną maszynę wirtualną platformy Azure. |
| Format-DevTestMessageWithTime |Dołącza datę i godzinę do komunikatu. Ta funkcja została zaprojektowana z myślą o komunikatach zapisywana w błędach i pełnych strumieniach. |
| Get-AzureSQLDatabaseConnectionString |Składa parametry połączenia w celu nawiązania połączenia z bazą danych Azure SQL Database. |
| Get-AzureVMStorage |Zwraca nazwę pierwszego konta magazynu z wzorcem Name "DevTest *" (bez uwzględniania wielkości liter) w określonej lokalizacji lub grupie koligacji. Jeśli konto magazynu "DevTest*" jest niezgodne z lokalizacją lub grupą koligacji, funkcja zignoruje ją. Określ lokalizację lub grupę koligacji. |
| Get-MSDeployCmd |Zwraca polecenie, aby uruchomić narzędzie MsDeploy. exe. |
| New-AzureVMEnvironment |Znajduje lub tworzy maszynę wirtualną w subskrypcji, która pasuje do wartości w pliku konfiguracji JSON. |
| Publish-WebPackage |Używa programu MsDeploy. exe i pakietu publikacji w sieci Web. Plik zip służący do wdrażania zasobów w witrynie sieci Web. Ta funkcja nie generuje żadnych danych wyjściowych. Jeśli wywołanie programu MSDeploy. exe nie powiedzie się, funkcja zgłasza wyjątek. Aby uzyskać bardziej szczegółowe dane wyjściowe, użyj opcji **-verbose** . |
| Publish-WebPackageToVM |Weryfikuje wartości parametrów, a następnie wywołuje funkcję **Publish-webpackage** . |
| Read-ConfigFile |Sprawdza poprawność pliku konfiguracji JSON i zwraca tabelę skrótów dla wybranych wartości. |
| Restore-Subscription |Resetuje bieżącą subskrypcję do oryginalnej subskrypcji. |
| Test-AzureModule |Zwraca `$true`, jeśli zainstalowana wersja modułu platformy Azure to 0.7.4 lub nowsza. Zwraca `$false`, jeśli moduł nie jest zainstalowany lub jest wcześniejszą wersją. Ta funkcja nie ma parametrów. |
| Test-AzureModuleVersion |Zwraca `$true`, jeśli wersja modułu platformy Azure to 0.7.4 lub nowszego. Zwraca `$false`, jeśli moduł nie jest zainstalowany lub jest wcześniejszą wersją. Ta funkcja nie ma parametrów. |
| Test-HttpsUrl |Konwertuje wejściowy adres URL na obiekt system. URI. Zwraca `$True`, jeśli adres URL jest bezwzględny, a jego schemat to https. Zwraca `$false`, jeśli adres URL jest względny, jego schemat nie jest typu HTTPS lub nie można przekonwertować ciągu wejściowego na adres URL. |
| Test-Member |Zwraca `$true`, jeśli właściwość lub metoda jest elementem członkowskim obiektu. W przeciwnym razie zwraca `$false`. |
| Write-ErrorWithTime |Zapisuje komunikat o błędzie poprzedzony bieżącą godziną. Ta funkcja wywołuje funkcję **Format-DevTestMessageWithTime, aby dołączać** czas przed zapisaniem komunikatu do strumienia błędów. |
| Write-HostWithTime |Zapisuje komunikat do programu hosta (**write-host**) poprzedzonego bieżącą godziną. Efekt zapisu w programie hosta jest różny. Większość programów, które obsługują program Windows PowerShell, zapisuj te komunikaty w standardowym wyjściu. |
| Write-VerboseWithTime |Zapisuje pełny komunikat poprzedzony bieżącą godziną. Ponieważ wywołuje metodę **Write-verbose**, komunikat jest wyświetlany tylko wtedy, gdy skrypt jest uruchamiany z parametrem **verbose** lub gdy preferencja **VerbosePreference** jest ustawiona na **Kontynuuj**. |

**Publish-WebApplication**

| Nazwa funkcji | Opis |
| --- | --- |
| New-AzureWebApplicationEnvironment |Tworzy zasoby platformy Azure, takie jak witryna sieci Web lub maszyna wirtualna. |
| New-WebDeployPackage |Ta funkcja nie jest zaimplementowana. Polecenia w tej funkcji można dodać do skompilowania projektu. |
| Publish-AzureWebApplication |Publikuje aplikację sieci Web na platformie Azure. |
| Publish-WebApplication |Tworzy i wdraża Web Apps, maszyny wirtualne, bazy danych SQL i konta magazynu dla projektu sieci Web programu Visual Studio. |
| Test-WebApplication |Ta funkcja nie jest zaimplementowana. Aby przetestować aplikację, możesz dodać polecenia w tej funkcji. |

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o skryptach programu PowerShell, odczytując [skrypty za pomocą programu Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) i Zobacz inne skrypty Azure PowerShell w [Centrum skryptów](https://azure.microsoft.com/documentation/scripts/).
