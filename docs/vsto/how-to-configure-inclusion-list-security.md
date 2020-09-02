---
title: 'Instrukcje: Konfigurowanie zabezpieczeń listy dołączania'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 459cf3f33197939a916a5f11a94bbaf09e8142e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541638"
---
# <a name="how-to-configure-inclusion-list-security"></a>Instrukcje: Konfigurowanie zabezpieczeń listy dołączania
  Jeśli masz uprawnienia administratora, możesz skonfigurować [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] monit zaufania, aby kontrolować, czy użytkownicy końcowi mają możliwość instalacji rozwiązań pakietu Office, zapisując decyzję zaufania do listy dołączania. Aby uzyskać informacje na temat list dołączanych, zobacz [zaufanie do rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 W przypadku rozwiązań w każdej z pięciu stref można ustawić następujące opcje:

- Włącz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klucz monitu zaufania i listę dołączania. Można zezwolić użytkownikom końcowym na udzielanie zaufania do rozwiązań pakietu Office, które są podpisane przy użyciu dowolnego certyfikatu.

- Ogranicz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klucz monitu zaufania i listę dołączania. Można zezwolić użytkownikom końcowym na instalowanie rozwiązań pakietu Office, które są podpisane przy użyciu certyfikatu, który identyfikuje wydawcę, ale nie jest to jeszcze zaufane.

- Wyłącz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] klucz monitu zaufania i listę dołączania. Można uniemożliwić użytkownikom końcowym Instalowanie dowolnych rozwiązań pakietu Office, które nie są podpisane przy użyciu jawnie zaufanego certyfikatu.

## <a name="enable-the-inclusion-list"></a>Włączanie listy dołączania
 Włącz listę dołączania dla strefy, gdy chcesz, aby użytkownicy końcowi mogli korzystać z opcji instalowania i uruchamiania dowolnych rozwiązań pakietu Office pochodzących z tej strefy.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Aby włączyć listę dołączania za pomocą edytora rejestru

1. Otwórz edytor rejestru: 

    1. Kliknij przycisk **Start**, a następnie kliknij polecenie **Uruchom**.

    2. W polu **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklucze jako **wartość ciągu**, jeśli jeszcze nie istnieją, ze skojarzonymi wartościami.

    |Podklucz wartości ciągu|Wartość|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Wyłączone**|
    |**MójKomputer**|**Włączone**|
    |**LocalIntranet**|**Włączone**|
    |**TrustedSites**|**Włączone**|

     Domyślnie **Internet** ma wartość **AuthenticodeRequired** , a **UntrustedSites** ma wartość **Disabled**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Aby programowo włączyć listę dołączania

1. Utwórz aplikację konsolową Visual Basic lub Visual C#.

2. Otwórz plik *program. vb* lub *program.cs* do edycji i Dodaj następujący kod.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
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

## <a name="restrict-the-inclusion-list"></a>Ograniczanie listy dołączania
 Ogranicz listę dołączania tak, aby rozwiązania musiały być podpisane przy użyciu certyfikatów Authenticode, które mają znaną tożsamość przed wyświetleniem monitu o decyzję zaufania.

### <a name="to-restrict-the-inclusion-list"></a>Aby ograniczyć listę dołączania

1. Otwórz edytor rejestru: 

    1. Kliknij przycisk **Start**, a następnie kliknij polecenie **Uruchom**.

    2. W polu **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, utwórz go.

3. Dodaj następujące podklucze jako **wartość ciągu**, jeśli jeszcze nie istnieją, ze skojarzonymi wartościami.

    |Podklucz wartości ciągu|Wartość|
    |-------------------------|-----------|
    |**UntrustedSites**|**Wyłączone**|
    |**Internet**|**AuthenticodeRequired**|
    |**MójKomputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Domyślnie **Internet** ma wartość **AuthenticodeRequired** , a **UntrustedSites** ma wartość **Disabled**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Aby programowo ograniczyć listę dołączania

1. Utwórz aplikację konsolową Visual Basic lub Visual C#.

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

## <a name="disable-the-inclusion-list"></a>Wyłącz listę dołączania
 Można wyłączyć listę dołączania tak, aby użytkownicy końcowi mogli tylko instalować rozwiązania podpisane przy użyciu zaufanego i znanego certyfikatu.

### <a name="to-disable-the-inclusion-list"></a>Aby wyłączyć listę dołączania

1. Otwórz edytor rejestru: 

    1. Kliknij przycisk **Start**, a następnie kliknij polecenie **Uruchom**.

    2. W polu **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.

2. Utwórz następujący klucz rejestru, jeśli ten jeszcze nie istnieje:

     **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT \\ . NETFramework\Security\TrustManager\PromptingLevel**

3. Dodaj następujące podklucze jako **wartość ciągu**, jeśli jeszcze nie istnieją, ze skojarzonymi wartościami.

    |Podklucz wartości ciągu|Wartość|
    |-------------------------|-----------|
    |**UntrustedSites**|**Wyłączone**|
    |**Internet**|**Wyłączone**|
    |**MójKomputer**|**Wyłączone**|
    |**LocalIntranet**|**Wyłączone**|
    |**TrustedSites**|**Wyłączone**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Aby programowo wyłączyć listę dołączania

1. Utwórz aplikację konsolową Visual Basic lub Visual C#.

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
- [Ufanie rozwiązaniom pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
