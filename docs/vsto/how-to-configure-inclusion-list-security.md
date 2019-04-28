---
title: 'Instrukcje: Konfigurowanie zabezpieczeń listy dołączania'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: ef4d25088e56f2223cb392dbc00c8454e1a291ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826382"
---
# <a name="how-to-configure-inclusion-list-security"></a>Instrukcje: Konfigurowanie zabezpieczeń listy dołączania
  Jeśli masz uprawnienia administratora, można skonfigurować [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufany monit formant czy użytkownicy końcowi otrzymają możliwość instalowania rozwiązań pakietu Office, zapisując decyzji dotyczącej zaufania do listy dołączania. Aby uzyskać informacje o listach dołączania, zobacz [zaufania rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Dla rozwiązania, które znajdują się w każdej z pięciu strefy można ustawić następujące opcje:

- Włącz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania monitu klucz i lista dołączania. Możesz zezwolić użytkownikom końcowym udzielenia zaufania do rozwiązań pakietu Office, które są podpisane za pomocą każdego certyfikatu.

- Ogranicz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania monitu klucz i lista dołączania. Można zezwolić użytkownikom końcowym zainstalować rozwiązań pakietu Office, które są podpisane za pomocą certyfikatu, który identyfikuje wydawcy, ale który nie jest zaufany.

- Wyłącz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] zaufania monitu klucz i lista dołączania. Aby uniemożliwić użytkownikom instalowanie dowolnego rozwiązania pakietu Office, który nie jest podpisany za pomocą jawnego zaufanego certyfikatu.

## <a name="enable-the-inclusion-list"></a>Włączanie listy dołączania
 Włącz lista dołączania dla strefy, jeśli chcesz, aby użytkownicy końcowi będą prezentowane za pomocą opcji instalowania i uruchamiania żadne rozwiązanie Office, który pochodzi z tej strefy.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Aby włączyć lista dołączania za pomocą Edytora rejestru

1. Otwórz Edytor rejestru:

    1. Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.

    2. W **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, należy go utworzyć.

3. Dodaj poniższe podklucze jako **wartość ciągu**, jeśli ich jeszcze nie istnieje, z powiązanymi wartościami.

    |Ciąg wartość podklucza|Wartość|
    |-------------------------|-----------|
    |**Internet**|**AuthenticodeRequired**|
    |**UntrustedSites**|**Disabled (Wyłączone)**|
    |**MyComputer**|**Włączone**|
    |**LocalIntranet**|**Włączone**|
    |**TrustedSites**|**Włączone**|

     Domyślnie **Internet** ma wartość **AuthenticodeRequired** i **UntrustedSites** ma wartość **wyłączone**.

### <a name="to-enable-the-inclusion-list-programmatically"></a>Aby programowo włączyć lista dołączania

1. Tworzenie języka Visual Basic lub Visual C# aplikacji konsoli.

2. Otwórz *Program.vb* lub *Program.cs* plik do edycji i Dodaj następujący kod.

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

## <a name="restrict-the-inclusion-list"></a>Ograniczenia listy dołączania
 Ograniczyć lista dołączania rozwiązania muszą być podpisane za pomocą jeszcze opracowywana tożsamość, zanim użytkownicy będą monitowani o decyzji dotyczącej zaufania certyfikatom Authenticode.

### <a name="to-restrict-the-inclusion-list"></a>Aby ograniczyć lista dołączania

1. Otwórz Edytor rejestru:

    1. Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.

    2. W **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.

2. Znajdź następujący klucz rejestru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Jeśli klucz nie istnieje, należy go utworzyć.

3. Dodaj poniższe podklucze jako **wartość ciągu**, jeśli ich jeszcze nie istnieje, z powiązanymi wartościami.

    |Ciąg wartość podklucza|Wartość|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabled (Wyłączone)**|
    |**Internet**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**TrustedSites**|**AuthenticodeRequired**|

     Domyślnie **Internet** ma wartość **AuthenticodeRequired** i **UntrustedSites** ma wartość **wyłączone**.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>Aby programowo ograniczyć lista dołączania

1. Tworzenie języka Visual Basic lub Visual C# aplikacji konsoli.

2. Otwórz *Program.vb* lub *Program.cs* plik do edycji i Dodaj następujący kod.

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

## <a name="disable-the-inclusion-list"></a>Wyłącz lista dołączania
 Tak, aby użytkownicy końcowi tylko można zainstalować rozwiązania, które są podpisane za pomocą certyfikatu zaufanego i znanego, można wyłączyć lista dołączania.

### <a name="to-disable-the-inclusion-list"></a>Aby wyłączyć lista dołączania

1. Otwórz Edytor rejestru:

    1. Kliknij przycisk **Start**, a następnie kliknij przycisk **Uruchom**.

    2. W **Otwórz** wpisz **regedt32.exe**, a następnie kliknij przycisk **OK**.

2. Jeśli to nie istnieje, utwórz następujący klucz rejestru:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. Dodaj poniższe podklucze jako **wartość ciągu**, jeśli ich jeszcze nie istnieje, z powiązanymi wartościami.

    |Ciąg wartość podklucza|Wartość|
    |-------------------------|-----------|
    |**UntrustedSites**|**Disabled (Wyłączone)**|
    |**Internet**|**Disabled (Wyłączone)**|
    |**MyComputer**|**Disabled (Wyłączone)**|
    |**LocalIntranet**|**Disabled (Wyłączone)**|
    |**TrustedSites**|**Disabled (Wyłączone)**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>Aby wyłączyć programowo lista dołączania

1. Tworzenie języka Visual Basic lub Visual C# aplikacji konsoli.

2. Otwórz *Program.vb* lub *Program.cs* plik do edycji i Dodaj następujący kod.

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

## <a name="see-also"></a>Zobacz także
- [Zaufanie rozwiązań pakietu Office przy użyciu list dołączania](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
