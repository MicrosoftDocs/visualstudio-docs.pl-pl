---
title: Publikowanie WebApplicationVM | Dokumentacja firmy Microsoft
description: Dowiedz się, jak wdrożyć aplikację sieci web, do maszyny wirtualnej. Ten skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.
services: visual-studio-online
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 11/11/2016
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: 8b4b7a05de87ab8b70046b51fe9f256f05d3aee5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572288"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (skrypt programu Windows PowerShell)
Wdraża aplikację sieci web do maszyny wirtualnej. Skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.

```
Publish-WebApplicationVM
-Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Konfiguracja
Ścieżka do pliku konfiguracji JSON opisujące szczegóły wdrożenia.

| Aliasy | brak |
| --- | --- |
| Wymagany? |true |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="subscriptionname"></a>SubscriptionName
Nazwa subskrypcji platformy Azure, w której chcesz utworzyć maszynę wirtualną.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |Używa pierwszej subskrypcji w pliku subskrypcji |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="webdeploypackage"></a>WebDeployPackage
Ścieżka do pakietu wdrożeniowego sieci web do publikowania do maszyny wirtualnej. Ten pakiet jest tworzony za pomocą kreatora Publikowanie w sieci Web w programie Visual Studio. Zobacz [jak: Utwórz pakiet wdrażania sieci Web w programie Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx).

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="allowuntrusted"></a>AllowUntrusted
Jeśli PRAWDA, Zezwalaj na korzystanie z certyfikatów, które nie są podpisane przez zaufanego głównego urzędu certyfikacji.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |false |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="vmpassword"></a>VMPassword
Poświadczenia dla konta maszyny wirtualnej. Przykład: - VMPassword @{nazwa = "admin"; Hasło = "password"}

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Poświadczenia bazy danych SQL na platformie Azure. Przykład: - DatabaseServerPassword @{nazwa = "admin"; Hasło = "password"}

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
W przypadku opcji true drukowania komunikatów ze skryptu do strumienia wyjściowego.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |false |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="remarks"></a>Uwagi
Aby uzyskać pełne wyjaśnienie sposobu użyć skryptu, aby utworzyć środowiska deweloperskie i testowe, zobacz [za pomocą skryptów programu PowerShell Windows Publikuj deweloperskim i testowym](vs-azure-tools-publishing-using-powershell-scripts.md).

Plik konfiguracji JSON określa szczegóły co ma zostać wdrożony. Zawiera informacje, które zostały określone podczas tworzenia projektu, takie jak nazwa grupy koligacji, obraz wirtualnego dysku twardego i rozmiar maszyny wirtualnej. Ponadto zawiera punkty końcowe na maszynie wirtualnej, baz danych, aby zainicjować obsługę, jeśli istnieje i sieci web parametrów wdrożenia. Poniższy kod przedstawia przykładowy plik konfiguracji JSON:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "China North",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
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
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

Można edytować plik JSON konfiguracji do zmiany, co jest aprowizowana. Maszyny wirtualne i usługi w chmurze są wymagane, ale sekcja bazy danych jest opcjonalna.


<!-- Update_Description: update metedata properties -->