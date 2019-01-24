---
title: 'Instrukcje: Konfigurowanie monitowania technologii ClickOnce zaufania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 41767546902e131f46230c5ee4e2e3085b1ff8a5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54773412"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Instrukcje: Konfigurowanie funkcji zaufanego monitowania technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Monit o udzielenie zaufania ClickOnce do kontroli można skonfigurować, czy użytkownicy końcowi otrzymają możliwość instalowania aplikacji ClickOnce, takich jak aplikacje Windows Presentation Foundation, aplikacji konsoli, przeglądarki WPF w aplikacjach Windows Forms aplikacje i rozwiązania dla pakietu Office. Możesz skonfigurować monit o udzielenie zaufania poprzez ustawienie kluczy rejestru na komputerze użytkownika końcowego.  
  
 W poniższej tabeli przedstawiono opcje konfiguracji, które mogą być stosowane do każdej z pięciu strefy (Internet, UntrustedSites, Mój komputer, LocalIntranet i TrustedSites:).  
  
|Opcja|Wartość ustawienia rejestru|Opis|  
|------------|----------------------------|-----------------|  
|Włącz monit o udzielenie zaufania.|`Enabled`|Monit o udzielenie zaufania ClickOnce jest wyświetlana tak, aby użytkownicy końcowi mogą udzielić zaufania dla aplikacji ClickOnce.|  
|Ogranicz monit o udzielenie zaufania.|`AuthenticodeRequired`|Monit o udzielenie zaufania ClickOnce jest wyświetlana tylko w sytuacji, gdy aplikacji ClickOnce są podpisane za pomocą certyfikatu, który identyfikuje wydawcy.|  
|Wyłącz monit o udzielenie zaufania.|`Disabled`|Monit o udzielenie zaufania ClickOnce jest wyświetlana tylko dla dowolnej aplikacji ClickOnce, które nie są podpisane za pomocą jawnego zaufanego certyfikatu.|  
  
 W poniższej tabeli przedstawiono domyślne zachowanie dla każdej strefy. Kolumna aplikacji odwołuje się do aplikacji Windows Forms, aplikacji Windows Presentation Foundation, aplikacje przeglądarki WPF i aplikacji konsoli.  
  
|Strefy|Aplikacje|rozwiązania pakietu Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 Możesz zastąpić te ustawienia, włączając, ograniczenie lub wyłączając monit o udzielenie zaufania ClickOnce.  
  
## <a name="enabling-the-clickonce-trust-prompt"></a>Włączanie monitowania technologii ClickOnce zaufania  
 Włącz monit o udzielenie zaufania strefie, jeśli chcesz, aby użytkownicy końcowi będą prezentowane za pomocą opcji instalowania i uruchamiania dowolnej aplikacji ClickOnce, która pochodzi z tej strefy.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby włączyć monit o udzielenie zaufania ClickOnce za pomocą Edytora rejestru  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz `regedit32`, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli ich jeszcze nie istnieje, z powiązanymi wartościami, które są wyświetlane w poniższej tabeli.  
  
    |Ciąg wartość podklucza|Wartość|  
    |-------------------------|-----------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Dla rozwiązań pakietu Office `Internet` ma wartości domyślnej `AuthenticodeRequired` i `UntrustedSites` ma wartość `Disabled`. Dla wszystkich innych `Internet` ma wartości domyślnej `Enabled`.  
  
#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Aby programowo włączyć monit o udzielenie zaufania ClickOnce  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C# w programie Visual Studio.  
  
2.  Otwórz plik Program.vb lub pliku Program.cs do edycji i Dodaj następujący kod.  
  
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
  
3.  Skompiluj i uruchom aplikację.  
  
## <a name="restricting-the-clickonce-trust-prompt"></a>Ograniczanie monit o udzielenie zaufania ClickOnce  
 Ograniczyć monit o udzielenie zaufania rozwiązania muszą być podpisane za pomocą jeszcze opracowywana tożsamość, zanim użytkownicy będą monitowani o decyzji dotyczącej zaufania certyfikatom Authenticode.  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby ograniczyć monit o udzielenie zaufania ClickOnce za pomocą Edytora rejestru  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz `regedit`, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli ich jeszcze nie istnieje, z powiązanymi wartościami, które są wyświetlane w poniższej tabeli.  
  
    |Ciąg wartość podklucza|Wartość|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Aby ograniczyć programowo monit o udzielenie zaufania ClickOnce  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C# w programie Visual Studio.  
  
2.  Otwórz plik Program.vb lub pliku Program.cs do edycji i Dodaj następujący kod.  
  
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
  
3.  Skompiluj i uruchom aplikację.  
  
## <a name="disabling-the-clickonce-trust-prompt"></a>Wyłączenie wiersza zaufania ClickOnce  
 Monit o udzielenie zaufania można wyłączyć, tak aby użytkownicy końcowi nie otrzymują możliwość zainstalowania rozwiązania, które nie są już zaufane w swoich zasad zabezpieczeń.  
  
#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Aby wyłączyć monit o udzielenie zaufania ClickOnce za pomocą Edytora rejestru  
  
1.  Otwórz Edytor rejestru:  
  
    1.  Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.  
  
    2.  W **Otwórz** wpisz `regedit`, a następnie kliknij przycisk **OK**.  
  
2.  Znajdź następujący klucz rejestru:  
  
     \HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel  
  
     Jeśli klucz nie istnieje, należy go utworzyć.  
  
3.  Dodaj poniższe podklucze jako **wartość ciągu**, jeśli ich jeszcze nie istnieje, z powiązanymi wartościami, które są wyświetlane w poniższej tabeli.  
  
    |Ciąg wartość podklucza|Wartość|  
    |-------------------------|-----------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Aby wyłączyć programowo monit o udzielenie zaufania ClickOnce  
  
1.  Utwórz aplikację konsoli języka Visual Basic lub Visual C# w programie Visual Studio.  
  
2.  Otwórz plik Program.vb lub pliku Program.cs do edycji i Dodaj następujący kod.  
  
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
  
3.  Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Instrukcje: Włączenie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Instrukcje: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Instrukcje: Ponowne podpisywanie manifestów wdrożenia i aplikacji](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
