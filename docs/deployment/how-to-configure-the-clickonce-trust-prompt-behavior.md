---
title: 'Jak: Konfigurowanie zachowania monitu zaufania ClickOnce | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649153"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Jak: Konfigurowanie zachowania monitu zaufania ClickOnce
Można skonfigurować monit zaufania ClickOnce, aby kontrolować, czy użytkownicy końcowi mają możliwość instalowania aplikacji ClickOnce, takich jak aplikacje Windows Forms, aplikacje Windows Presentation Foundation, aplikacje konsoli, aplikacje przeglądarki WPF i rozwiązania pakietu Office. Wiersz zaufania można skonfigurować, ustawiając klucze rejestru na komputerze każdego użytkownika końcowego.

 W poniższej tabeli przedstawiono opcje konfiguracji, które można zastosować do każdej z pięciu stref (Internet, UntrustedSites, MyComputer, LocalIntranet i TrustedSites).

|Opcja|Wartość ustawienia rejestru|Opis|
|------------|----------------------------|-----------------|
|Włącz monit zaufania.|`Enabled`|ClickOnce zaufania monit jest wyświetlany, dzięki czemu użytkownicy końcowi mogą udzielić zaufania do aplikacji ClickOnce.|
|Ogranicz monit zaufania.|`AuthenticodeRequired`|Monit zaufania ClickOnce jest wyświetlany tylko wtedy, gdy aplikacje ClickOnce są podpisane za pomocą certyfikatu identyfikującego wydawcę.|
|Wyłącz monit zaufania.|`Disabled`|Monit zaufania ClickOnce nie jest wyświetlany dla żadnych aplikacji ClickOnce, które nie są podpisane za pomocą jawnie zaufanego certyfikatu.|

 W poniższej tabeli przedstawiono domyślne zachowanie dla każdej strefy. Kolumna Aplikacje odnosi się do aplikacji Windows Forms, Windows Presentation Foundation, aplikacji przeglądarki WPF i aplikacji konsoli.

|Strefa|Aplikacje|rozwiązania pakietu Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Można zastąpić te ustawienia, włączając, ograniczając lub wyłączając monit zaufania ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Włączanie monitu zaufania ClickOnce
 Włącz monit zaufania dla strefy, jeśli chcesz, aby użytkownicy końcowi mają być prezentowane z opcją instalowania i uruchamiania dowolnej aplikacji ClickOnce, która pochodzi z tej strefy.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby włączyć monit zaufania ClickOnce przy użyciu edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij **przycisk Start**, a następnie kliknij przycisk **Uruchom**.

    2. W polu **Otwórz** `regedit`wpisz , a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklu skróty jako **wartość ciągu**, jeśli jeszcze nie istnieją, z skojarzonymi wartościami pokazanymi w poniższej tabeli.

    |Podklucz wartość ciągu|Wartość|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     W przypadku rozwiązań pakietu `Internet` `AuthenticodeRequired` Office `UntrustedSites` ma `Disabled`wartość domyślną i wartość . Dla wszystkich `Internet` innych, ma `Enabled`wartość domyślną .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Aby programowo włączyć monit zaufania ClickOnce

1. Tworzenie aplikacji konsoli Visual Basic lub Visual C# w programie Visual Studio.

2. Otwórz plik *Program.vb* lub *Program.cs* do edycji i dodaj następujący kod.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Skompiluj i uruchom aplikację.

## <a name="restrict-the-clickonce-trust-prompt"></a>Ogranicz monit zaufania ClickOnce
 Ogranicz monit zaufania, aby rozwiązania muszą być podpisane za pomocą certyfikatów Authenticode, które znały tożsamość, zanim użytkownicy zostaną poproszeni o decyzję o zaufaniu.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby ograniczyć monit zaufania ClickOnce przy użyciu edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij **przycisk Start**, a następnie kliknij przycisk **Uruchom**.

    2. W polu **Otwórz** `regedit`wpisz , a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklu skróty jako **wartość ciągu**, jeśli jeszcze nie istnieją, z skojarzonymi wartościami pokazanymi w poniższej tabeli.

    |Podklucz wartość ciągu|Wartość|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Aby programowo ograniczyć monit zaufania ClickOnce

1. Tworzenie aplikacji konsoli Visual Basic lub Visual C# w programie Visual Studio.

2. Otwórz plik *Program.vb* lub *Program.cs* do edycji i dodaj następujący kod.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Skompiluj i uruchom aplikację.

## <a name="disable-the-clickonce-trust-prompt"></a>Wyłączanie monitu zaufania ClickOnce
 Można wyłączyć monit zaufania, aby użytkownicy końcowi nie mieli możliwości instalowania rozwiązań, które nie są jeszcze zaufane w swoich zasadach zabezpieczeń.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby wyłączyć monit zaufania ClickOnce przy użyciu edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij **przycisk Start**, a następnie kliknij przycisk **Uruchom**.

    2. W polu **Otwórz** `regedit`wpisz , a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklu skróty jako **wartość ciągu**, jeśli jeszcze nie istnieją, z skojarzonymi wartościami pokazanymi w poniższej tabeli.

    |Podklucz wartość ciągu|Wartość|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Aby programowo wyłączyć monit zaufania ClickOnce

1. Tworzenie aplikacji konsoli Visual Basic lub Visual C# w programie Visual Studio.

2. Otwórz plik *Program.vb* lub *Program.cs* do edycji i dodaj następujący kod.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Skompiluj i uruchom aplikację.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Jak: Włącz ustawienia zabezpieczeń ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Jak: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Jak: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Jak: Ponowne podpisywanie manifestów aplikacji i wdrażania](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
