---
title: Skonfiguruj zachowanie monitu zaufania ClickOnce | Microsoft Docs
description: Dowiedz się, jak skonfigurować monit zaufania ClickOnce, aby kontrolować, czy użytkownicy końcowi mają opcję instalowania aplikacji ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 68d39bed64ff1392c83d6fc2be0de936ac1b00d2
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350065"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Instrukcje: Konfigurowanie zachowania monitowania zaufania ClickOnce
Można skonfigurować monit zaufania ClickOnce, aby określić, czy użytkownicy końcowi mogą instalować aplikacje ClickOnce, takie jak aplikacje Windows Forms, aplikacje Windows Presentation Foundation, aplikacje konsolowe, aplikacje przeglądarki WPF i rozwiązania pakietu Office. Aby skonfigurować monit zaufania, należy ustawić klucze rejestru na komputerze użytkownika końcowego.

 W poniższej tabeli przedstawiono opcje konfiguracji, które można zastosować do każdej z pięciu stref (Internet, UntrustedSites, mójkomputer, LocalIntranet i TrustedSites).

|Opcja|Wartość ustawienia rejestru|Opis|
|------------|----------------------------|-----------------|
|Włącz monit zaufania.|`Enabled`|Zostanie wyświetlony monit zaufania ClickOnce, aby użytkownicy końcowi mogli udzielić zaufania aplikacjom ClickOnce.|
|Ogranicz monit zaufania.|`AuthenticodeRequired`|Monit zaufania ClickOnce jest wyświetlany tylko wtedy, gdy aplikacje ClickOnce są podpisane przy użyciu certyfikatu, który identyfikuje wydawcę.|
|Wyłącz monit zaufania.|`Disabled`|Monit zaufania ClickOnce nie jest wyświetlany dla żadnych aplikacji ClickOnce, które nie są podpisane przy użyciu jawnie zaufanego certyfikatu.|

 W poniższej tabeli przedstawiono zachowanie domyślne dla każdej strefy. Kolumna aplikacje odnosi się do Windows Forms aplikacji, aplikacji Windows Presentation Foundation, aplikacji przeglądarki WPF i aplikacji konsolowych.

|Strefa|Aplikacje|rozwiązania pakietu Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Te ustawienia można zastąpić, włączając, ograniczając lub wyłączając monit zaufania ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Włączanie monitu zaufania ClickOnce
 Włącz monit zaufania dla strefy, gdy chcesz, aby użytkownicy końcowi mogli korzystać z opcji instalowania i uruchamiania dowolnej aplikacji ClickOnce pochodzącej z tej strefy.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby włączyć monit zaufania ClickOnce przy użyciu Edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij przycisk **Start** , a następnie kliknij polecenie **Uruchom**.

    2. W polu **Otwórz** wpisz `regedit` , a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklucze jako **wartość ciągu** , jeśli jeszcze nie istnieją, ze skojarzonymi wartościami podanymi w poniższej tabeli.

    |Podklucz wartości ciągu|Wartość|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Dla rozwiązań pakietu Office `Internet` ma wartość domyślną `AuthenticodeRequired` i `UntrustedSites` ma wartość `Disabled` . Dla wszystkich innych, `Internet` ma wartość domyślną `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Aby programowo włączyć monit zaufania ClickOnce

1. Utwórz aplikację konsolową Visual Basic lub Visual C# w programie Visual Studio.

2. Otwórz plik *program. vb* lub *program.cs* do edycji i Dodaj następujący kod.

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

## <a name="restrict-the-clickonce-trust-prompt"></a>Ograniczanie monitu zaufania ClickOnce
 Ogranicz monit zaufania, aby rozwiązania musiały być podpisane przy użyciu certyfikatów Authenticode, które mają znaną tożsamość przed wyświetleniem monitu o decyzję zaufania.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby ograniczyć monit zaufania ClickOnce przy użyciu Edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij przycisk **Start** , a następnie kliknij polecenie **Uruchom**.

    2. W polu **Otwórz** wpisz `regedit` , a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklucze jako **wartość ciągu** , jeśli jeszcze nie istnieją, ze skojarzonymi wartościami podanymi w poniższej tabeli.

    |Podklucz wartości ciągu|Wartość|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Aby programowo ograniczyć monit zaufania ClickOnce

1. Utwórz aplikację konsolową Visual Basic lub Visual C# w programie Visual Studio.

2. Otwórz plik *program. vb* lub *program.cs* do edycji i Dodaj następujący kod.

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

## <a name="disable-the-clickonce-trust-prompt"></a>Wyłącz monit zaufania ClickOnce
 Możesz wyłączyć monit zaufania, aby użytkownicy końcowi nie mieli możliwości instalacji rozwiązań, które nie są jeszcze zaufane w zasadach zabezpieczeń.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby wyłączyć monit zaufania ClickOnce przy użyciu Edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij przycisk **Start** , a następnie kliknij polecenie **Uruchom**.

    2. W polu **Otwórz** wpisz `regedit` , a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\ HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\ . NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklucze jako **wartość ciągu** , jeśli jeszcze nie istnieją, ze skojarzonymi wartościami podanymi w poniższej tabeli.

    |Podklucz wartości ciągu|Wartość|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Aby programowo wyłączyć monit zaufania ClickOnce

1. Utwórz aplikację konsolową Visual Basic lub Visual C# w programie Visual Studio.

2. Otwórz plik *program. vb* lub *program.cs* do edycji i Dodaj następujący kod.

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
- [Instrukcje: Włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Instrukcje: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
