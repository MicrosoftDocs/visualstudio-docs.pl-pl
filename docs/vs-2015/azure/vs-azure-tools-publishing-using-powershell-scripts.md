---
title: Publikowanie dla deweloperów i środowisk testowych za pomocą skryptów programu Windows PowerShell | Dokumentacja firmy Microsoft
description: Dowiedz się, jak publikować do tworzenia i środowisk testowych za pomocą skryptów środowiska Windows PowerShell w programie Visual Studio.
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
ms.openlocfilehash: cfa6c37702eb3f6299061c512081f4c122cee3c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830502"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Publikowanie w środowisku deweloperskim i testowym za pomocą skryptów programu Windows PowerShell

Podczas tworzenia aplikacji sieci web w programie Visual Studio można wygenerować skrypt programu Windows PowerShell, którego można później zautomatyzować publikowanie witryny sieci Web na platformie Azure jako aplikację internetową w usłudze Azure App Service lub maszyny wirtualnej. Można edytować i rozszerzać skrypt programu Windows PowerShell w edytorze programu Visual Studio ze swoimi potrzebami lub zintegrować z istniejącą kompilację, testowania i skryptów publikowania.

Skrypty te można udostępnić dostosowanych wersji (znany także jako środowiska tworzenia i testowania) witryny do tymczasowego użytku. Na przykład skonfigurować konkretnej wersji witryny sieci Web na maszynie wirtualnej platformy Azure lub w miejscu przejściowym w witrynie internetowej można uruchomić zestaw testów, odtworzenia usterki, przetestować poprawki, wersja próbna proponowana zmiana lub skonfigurować niestandardowe środowisko do obsługi demonstracji i prezentacji. Po utworzeniu skryptu, który publikuje projektu można odtworzyć identyczne środowiska zgodnie z potrzebami, uruchamiając skrypt lub uruchom skrypt z kompilacji aplikacji sieci web, aby utworzyć niestandardowe środowiska na potrzeby testowania.

## <a name="prerequisites"></a>Wymagania wstępne

* Zestaw Azure SDK 2.3 lub nowszy. Zobacz [pobrania programu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=624384). (Nie ma potrzeby zestawu SDK usługi Azure, można wygenerować skryptów dla projektów sieci web. Ta funkcja jest dla projektów sieci web, nie ról sieci web w usługach w chmurze).
* Program Azure PowerShell 0.7.4 lub nowszej. Zobacz [jak zainstalować i skonfigurować program Azure PowerShell](/powershell/azure/overview).
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175) lub nowszej.

## <a name="additional-tools"></a>Dodatkowe narzędzia

Dostępne są dodatkowe narzędzia i zasoby dotyczące pracy z programem PowerShell w programie Visual Studio dla deweloperów platformy Azure. Zobacz [narzędzia programu PowerShell dla programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012).

## <a name="generating-the-publish-scripts"></a>Generowanie skryptów publikowania

Można generować skrypty publikowania dla maszyny wirtualnej, który jest hostem witryny sieci Web podczas tworzenia nowego projektu, postępując zgodnie z [w instrukcjach](/azure/virtual-machines/windows/classic/web-app-visual-studio?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json). Możesz również [Generowanie publikowanie skrypty dla usługi web apps w usłudze Azure App Service](/azure/app-service/scripts/app-service-powershell-deploy-github).

## <a name="scripts-that-visual-studio-generates"></a>Skrypty, które generuje programie Visual Studio

Program Visual Studio generuje rozwiązanie na poziomie folder o nazwie **PublishScripts** zawierający dwa pliki programu Windows PowerShell, skrypt publikowania dla maszyny wirtualnej lub witryny sieci Web i moduł, który zawiera funkcje, które można używać w skrypty. Program Visual Studio również wygenerowanie pliku w formacie JSON, który określa szczegółowe informacje dotyczące projektu, który jest wdrażany.

### <a name="windows-powershell-publish-script"></a>Program Windows PowerShell publikować skryptu

Skrypt publikowania zawiera Publikuj określone kroki wdrażania witryny sieci Web lub na maszynie wirtualnej. Program Visual Studio udostępnia kolorowania dla rozwoju programu Windows PowerShell. Pomoc dla funkcji jest dostępna i za darmo można edytować funkcji w skrypcie ze swoimi potrzebami zmiany.

### <a name="windows-powershell-module"></a>Moduł programu Windows PowerShell

Moduł programu Windows PowerShell, który generuje programie Visual Studio zawiera funkcje, które używa skryptów publikowania. Te funkcje programu Azure PowerShell nie są przeznaczone do zmodyfikowania. Zobacz [jak zainstalować i skonfigurować program Azure PowerShell](/powershell/azure/overview).

### <a name="json-configuration-file"></a>Plik JSON konfiguracji

Plik JSON jest tworzony w **konfiguracje** folder i zawiera dane konfiguracji, który określa dokładnie które zasoby należy wdrożyć na platformie Azure. Nazwa pliku, który generuje programie Visual Studio jest projektu name-WAWS-dev.json Jeśli podczas tworzenia witryny sieci Web lub projektu Nazwa-maszyny Wirtualnej — dev.json, jeśli utworzono maszynę wirtualną. Oto przykład z pliku konfiguracji JSON, który jest generowany podczas tworzenia witryny sieci Web. Większość wartości jest oczywista. Nazwa witryny sieci Web jest generowany przez platformę Azure, dzięki czemu mogą być niezgodne Nazwa projektu.

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

Podczas tworzenia maszyny wirtualnej, pliku konfiguracji JSON wygląda podobnie do poniższego. Usługa w chmurze jest tworzona jako kontener dla maszyny wirtualnej. Maszyna wirtualna zawiera zwykły punktów końcowych na potrzeby dostępu do sieci web za pośrednictwem protokołów HTTP i HTTPS, a także punkty końcowe dla narzędzia Web Deploy, który umożliwia publikowanie witryny sieci Web z komputera lokalnego, Pulpit zdalny i programu Windows PowerShell.

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

Można edytować konfiguracji JSON można zmienić, co się stanie po uruchomieniu skryptów publikowania. `cloudService` i `virtualMachine` sekcje są wymagane, ale możesz usunąć `databases` sekcji, jeśli nie są potrzebne. Właściwości, które są puste w programie Visual Studio generuje domyślny plik konfiguracji jest opcjonalna. te właściwości, które mają wartości w domyślnym pliku konfiguracji są wymagane.

Jeśli masz witrynę internetową, która zawiera wiele środowisk wdrażania (nazywanych miejscami) zamiast lokacji pojedynczego produkcyjnych na platformie Azure może zawierać nazwę witryny sieci Web z nazwą miejsca w pliku konfiguracji JSON. Na przykład, jeśli masz witrynę internetową, która nosi nazwę **mysite** i miejsce dla niego o nazwie **test** , a następnie identyfikator URI jest `mysite-test.cloudapp.net`, ale mysite(test) poprawną nazwę do użycia w pliku konfiguracji. Można zrobić tylko to, jeśli witryna sieci Web i gniazd już istnieją w Twojej subskrypcji. Jeśli nie istnieją, należy utworzyć witrynę sieci Web przez uruchomienie skryptu bez określania gniazda, a następnie utwórz miejsce w [witryny Azure portal](https://portal.azure.com/), a następnie uruchom skrypt o nazwie zmodyfikowanej witryny sieci Web. Aby uzyskać więcej informacji na temat miejsc wdrożenia dla aplikacji sieci web, zobacz [Konfigurowanie środowiska tymczasowego dla aplikacji sieci web w usłudze Azure App Service](/azure/app-service/web-sites-staged-publishing).

## <a name="how-to-run-the-publish-scripts"></a>Sposób uruchamiania skryptów publikowania

Jeśli nigdy nie uruchomiono skrypt programu Windows PowerShell przed, należy najpierw ustawić zasady wykonywania, aby umożliwić uruchamianie skryptów. Zasady jest to funkcja zabezpieczeń, aby uniemożliwić użytkownikom uruchamianie skryptów programu Windows PowerShell, jeśli są one podatne na przed złośliwym oprogramowaniem i wirusami, które obejmują wykonywania skryptów.

### <a name="run-the-script"></a>Uruchamianie skryptu

1. Utwórz pakiet Web Deploy dla Twojego projektu. Pakiet Web Deploy jest skompresowane archiwum (plik zip), który zawiera pliki, które ma zostać skopiowany do witryny sieci Web lub maszyny wirtualnej. Pakiety programu Web Deploy w programie Visual Studio można utworzyć dla dowolnej aplikacji sieci web.

   ![Tworzenie sieci Web wdrażanie pakietu](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   Aby uzyskać więcej informacji, zobacz [jak: Utwórz pakiet wdrażania sieci Web w programie Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx). Możesz też zautomatyzować tworzenie pakietu Narzędzia Web Deploy, zgodnie z opisem w [dostosowywanie i rozszerzanie skryptów publikowania](#customizing-and-extending-the-publish-scripts).

1. W **Eksploratora rozwiązań**, otwórz menu kontekstowe dla skryptu, a następnie wybierz **Otwórz za pomocą programu PowerShell ISE**.
1. Jeśli uruchamianie skryptów programu Windows PowerShell na tym komputerze po raz pierwszy, Otwórz okno wiersza polecenia z uprawnieniami administratora i wpisz następujące polecenie:

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. Zaloguj się na platformie Azure przy użyciu następującego polecenia.

    ```powershell
    Add-AzureAccount
    ```

    Po wyświetleniu monitu podaj nazwę użytkownika i hasło.

    Należy pamiętać, że podczas automatyzacji skryptu tej metody udostępniania poświadczeń platformy Azure nie działa. Zamiast tego należy używać `.publishsettings` pliku o podanie poświadczeń. Jeden raz, możesz użyć polecenia **Get AzurePublishSettingsFile** można pobrać plik z platformy Azure, a następnie użyć **AzurePublishSettingsFile importu** Aby zaimportować plik. Aby uzyskać szczegółowe instrukcje, zobacz [jak zainstalować i skonfigurować program Azure PowerShell](/powershell/azure/overview).

1. (Opcjonalnie) Jeśli chcesz tworzyć zasoby platformy Azure, takie jak maszyny wirtualne, bazy danych i witryny sieci Web bez publikowania aplikacji sieci web używają **WebApplication.ps1 Publikuj** polecenia **-konfiguracji**argument wartość do pliku konfiguracji JSON. Ten wiersz polecenia korzysta z pliku konfiguracji JSON do określenia, które zasoby do utworzenia. Ponieważ używa ona domyślne ustawienia dla innych argumentów wiersza poleceń, tworzy zasoby, ale nie publikować aplikację sieci web. Verbose opcja umożliwia dowiedzieć się więcej o tym, co się dzieje.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. Użyj **WebApplication.ps1 Publikuj** polecenia, jak pokazano w jednej z poniższych przykładów, które wywołuje skrypt i opublikować aplikację sieci web. Jeśli zachodzi potrzeba zastępują ustawienia domyślne dla wszystkich innych argumentów, takie jak nazwa subskrypcji, publikowanie, nazwy pakietu, poświadczenia maszyny wirtualnej lub poświadczenia serwera bazy danych, można określić tych parametrów. Użyj **— pełne** opcje, aby wyświetlić więcej informacji na temat postępu procesu publikowania.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    Jeśli tworzysz maszynę wirtualną, polecenie wygląda podobnie do poniższego. W tym przykładzie przedstawiono również sposób podania poświadczeń dla wielu baz danych. Dla maszyn wirtualnych tworzonych przez te skrypty certyfikat SSL nie pochodzi z zaufanego głównego urzędu certyfikacji. W związku z tym, należy użyć **— AllowUntrusted** opcji.

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

    Skrypt można tworzyć bazy danych, ale nie tworzy, serwerów baz danych. Jeśli chcesz utworzyć serwer bazy danych, możesz użyć **New AzureSqlDatabaseServer** funkcja w module platformy Azure.

## <a name="customizing-and-extending-the-publish-scripts"></a>Dostosowywanie i rozszerzanie skryptów publikowania

Można dostosować skrypt publikowania i pliku konfiguracji JSON. Funkcje w module Windows PowerShell **AzureWebAppPublishModule.psm1** nie są przeznaczone do zmodyfikowania. Jeśli chcesz określić inną bazę danych lub zmienić niektóre właściwości maszyny wirtualnej, należy edytować plik konfiguracji JSON. Jeśli chcesz rozszerzyć funkcjonalność skryptu, aby zautomatyzować tworzenie i testowanie projektu, można zaimplementować wycinki funkcji w **WebApplication.ps1 Publikuj**.

Aby zautomatyzować tworzenie projektu, Dodaj kod, który wywołuje program MSBuild `New-WebDeployPackage` jak pokazano w poniższym przykładzie kodu. Ścieżka do polecenia MSBuild różni się zależnie od wersji programu Visual Studio zostały zainstalowane. Aby uzyskać prawidłowej ścieżki, można użyć funkcji **Get MSBuildCmd**, jak pokazano w poniższym przykładzie.

### <a name="to-automate-building-your-project"></a>Aby zautomatyzować tworzenie projektu

1. Dodaj `$ProjectFile` parametru w sekcji parametrów globalnych.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. Copy — funkcja `Get-MSBuildCmd` do pliku skryptu.

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

1. Zastąp `New-WebDeployPackage` z następującym kodem i zastąp symbole zastępcze w wywołaniach konstruowanie wiersza `$msbuildCmd`. Ten kod jest dla programu Visual Studio 2015. Jeśli używasz programu Visual Studio 2017, zmień **VisualStudioVersion** właściwości `15.0` (`12.0` dla programu Visual Studio 2013).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Aby utworzyć aplikację sieci web, należy użyć MsBuild.exe. Aby uzyskać pomoc zobacz informacje wiersza polecenia programu MSBuild na: [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>Rozpocznij wykonywanie polecenia kompilacji

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

1. Wywołaj `New-WebDeployPackage` funkcja zanim ten wiersz: `$Config = Read-ConfigFile $Configuration` dla aplikacji sieci web lub `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)` dla maszyn wirtualnych.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. Wywoływanie niestandardowych skryptów z wiersza polecenia przy użyciu przekazywania `$Project` argumentu, jak w poniższym przykładzie:

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    Aby zautomatyzować testowanie aplikacji, Dodaj kod, aby `Test-WebApplication`. Należy koniecznie Usuń komentarz wiersze **WebApplication.ps1 Publikuj** gdzie te funkcje są wywoływane. Jeśli nie zapewniają implementacji, można ręcznie utworzyć projektu za pomocą programu Visual Studio, a następnie uruchom skrypt publish do publikowania na platformie Azure.

## <a name="publishing-function-summary"></a>Podsumowanie funkcji publikowania
Aby uzyskać pomoc dotyczącą funkcji, można użyć w wierszu polecenia programu Windows PowerShell, użyj polecenia `Get-Help function-name`. Pomoc zawiera pomocy do parametrów i przykłady. Ten sam tekst pomocy jest również w plikach źródłowych skryptów **AzureWebAppPublishModule.psm1** i **WebApplication.ps1 Publikuj**. Skrypt i pomocy są zlokalizowane w języku Visual Studio.

**AzureWebAppPublishModule**

| Nazwa funkcji | Opis |
| --- | --- |
| Add-AzureSQLDatabase |Tworzy nową bazę danych Azure SQL. |
| Add-AzureSQLDatabases |Tworzy bazy danych Azure SQL na podstawie wartości w pliku konfiguracji JSON, który generuje programie Visual Studio. |
| Add-AzureVM |Tworzy maszynę wirtualną platformy Azure i zwraca adres URL wdrożonej maszyny Wirtualnej. Funkcja konfiguruje wymagania wstępne, a następnie wywołuje **New-AzureVM** funkcji (moduł platformy Azure), aby utworzyć nową maszynę wirtualną. |
| Add-AzureVMEndpoints |Dodaje nowy wejściowe punkty końcowe do maszyny wirtualnej i przywraca maszynę wirtualną przy użyciu nowego punktu końcowego. |
| Add-AzureVMStorage |Tworzy nowe konto usługi Azure storage w bieżącej subskrypcji. Nazwa konta rozpoczyna się od "devtest", po której następuje unikatowy ciąg alfanumeryczny. Funkcja zwraca nazwę nowego konta magazynu. Określ lokalizację lub grupę koligacji dla nowego konta magazynu. |
| Add-AzureWebsite |Tworzy witrynę sieci Web o określonej nazwie i lokalizacji. Ta funkcja wywołuje **New-AzureWebsite** funkcja w module platformy Azure. Jeśli subskrypcja nie zawiera jeszcze witryny sieci Web przy użyciu określonej nazwy, ta funkcja tworzy witryny sieci Web i zwraca obiekt witryny sieci Web. W przeciwnym razie zwraca `$null`. |
| Backup-Subscription |Zapisuje bieżąca subskrypcja platformy Azure w `$Script:originalSubscription` zmiennej w zakresie skryptu. Ta funkcja zapisuje bieżąca subskrypcja platformy Azure (uzyskanych przez `Get-AzureSubscription -Current`) i jego konta magazynu i subskrypcję, która zostanie zmieniony przez ten skrypt (przechowywany w zmiennej `$UserSpecifiedSubscription`) i jego konto magazynu, w zakresie skryptu. Po zapisaniu wartości, można użyć funkcji, takich jak `Restore-Subscription`, aby przywrócić oryginalny bieżącego konta subskrypcji i magazynu na bieżący stan, jeśli bieżący stan został zmieniony. |
| Find-AzureVM |Pobiera określonej maszyny wirtualnej platformy Azure. |
| Format-DevTestMessageWithTime |Dołącza datę i godzinę na komunikat. Ta funkcja jest przeznaczona dla komunikatów zapisanych strumieni błędów i pełne. |
| Get-AzureSQLDatabaseConnectionString |Zbierane parametry połączenia, aby nawiązać połączenie z bazą danych Azure SQL database. |
| Get-AzureVMStorage |Zwraca nazwę pierwszego konta magazynu przy użyciu wzorca nazwy "devtest *" (wielkich liter) w określonej lokalizacji lub grupy koligacji. Jeśli "devtest*" konto magazynu nie jest zgodny, lokalizacja lub grupa koligacji, funkcja je ignoruje. Określ grupę koligacji lub lokalizację. |
| Get-MSDeployCmd |Zwraca polecenie, aby uruchomić narzędzie MsDeploy.exe. |
| New-AzureVMEnvironment |Znajduje lub tworzy maszynę wirtualną w subskrypcji, który odpowiada wartości w pliku konfiguracji JSON. |
| Publish-WebPackage |Zastosowań MsDeploy.exe i sieci web można opublikować pakietu. Plik zip do wdrażania zasobów w witrynie sieci Web. Ta funkcja nie generuje żadnych danych wyjściowych. Jeśli wywołanie MSDeploy.exe zakończy się niepowodzeniem, funkcja zgłasza wyjątek. Aby uzyskać bardziej szczegółowe dane wyjściowe, użyj **-Verbose** opcji. |
| Publish-WebPackageToVM |Weryfikuje wartości parametrów, a następnie wywołuje **Publish-WebPackage** funkcji. |
| Read-ConfigFile |Sprawdza poprawność pliku konfiguracji JSON i zwraca tabelę mieszania, wybranych wartości. |
| Restore-Subscription |Resetuje bieżącej subskrypcji do pierwotnej subskrypcji. |
| Test-AzureModule |Zwraca `$true` Jeśli wersja zainstalowanego modułu platformy Azure jest 0.7.4 lub nowszej. Zwraca `$false` Jeśli moduł nie jest zainstalowany lub jest starsza wersja. Ta funkcja nie ma parametrów. |
| Test-AzureModuleVersion |Zwraca `$true` Jeśli wersja modułu platformy Azure jest 0.7.4 lub nowszej. Zwraca `$false` Jeśli moduł nie jest zainstalowany lub jest starsza wersja. Ta funkcja nie ma parametrów. |
| Test-HttpsUrl |Konwertuje wejściowego adresu URL obiektu System.Uri. Zwraca `$True` Jeśli adres URL jest bezwzględny, a jego schemat jest typu https. Zwraca `$false` adres URL jest względny, jego schematu nie protokołu HTTPS, czy ciąg wejściowy nie można przekonwertować na adres URL. |
| Test-Member |Zwraca `$true` Jeśli właściwość lub metoda jest elementem członkowskim obiektu. W przeciwnym razie zwraca `$false`. |
| Write-ErrorWithTime |Zapisuje komunikat o błędzie prefiksem bieżący czas. Wywołuje tę funkcję, **Format DevTestMessageWithTime** funkcji dołączana czas przed zapisaniem komunikat strumienia błędów. |
| Write-HostWithTime |Zapisuje komunikat do hosta program (**Write-Host**) poprzedzony znakiem bieżący czas. Różni się efekt zapisywania program hosta. Większość programów hostujących środowiska Windows PowerShell zapisać te komunikaty do wyjścia standardowego. |
| Write-VerboseWithTime |Zapisuje komunikat trybu informacji pełnej, prefiks z bieżącym czasem. Ponieważ wywołuje **Write-Verbose**, komunikat jest wyświetlany tylko wtedy, gdy skrypt jest uruchamiany z **pełne** parametr lub jeśli **VerbosePreference** preferencji jest ustawiona na  **Kontynuuj**. |

**Publish-WebApplication**

| Nazwa funkcji | Opis |
| --- | --- |
| New-AzureWebApplicationEnvironment |Tworzy zasoby platformy Azure, takich jak witryny sieci Web lub maszyny wirtualnej. |
| New-WebDeployPackage |Ta funkcja nie jest zaimplementowana. W tej funkcji do kompilowania projektu można dodać polecenia. |
| Publish-AzureWebApplication |Publikuje aplikacji sieci web na platformie Azure. |
| Publish-WebApplication |Służy do tworzenia i wdrażania aplikacji sieci Web, maszyn wirtualnych, baz danych SQL Database i konta magazynu dla projektu sieci web programu Visual Studio. |
| Test-WebApplication |Ta funkcja nie jest zaimplementowana. W tej funkcji, aby przetestować aplikację, można dodać polecenia. |

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej na temat skryptów środowiska PowerShell, czytając [skryptów za pomocą programu Windows PowerShell](https://technet.microsoft.com/library/bb978526.aspx) i zobaczyć inne skrypty programu Azure PowerShell w [Centrum skryptów](https://azure.microsoft.com/documentation/scripts/).
