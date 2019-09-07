---
title: Publish-WebApplicationVM | Microsoft Docs
description: Dowiedz się, jak wdrożyć aplikację sieci Web na maszynie wirtualnej. Ten skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.
author: ghogen
manager: jillfra
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e35f5decee2a908a9d1075ff3f6365a1d358c7b2
ms.sourcegitcommit: dae5dfd626277b58ebd7b21a75757f683f1eacc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739321"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (skrypt programu Windows PowerShell)
Wdraża aplikację sieci Web na maszynie wirtualnej. Skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.

```
Publish-WebApplicationVM
–Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Konfiguracja
Ścieżka do pliku konfiguracji JSON opisującego Szczegóły wdrożenia.

| Aliasy | brak |
| --- | --- |
| Wymagany? |true |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="subscriptionname"></a>SubscriptionName
Nazwa subskrypcji platformy Azure, w której chcesz utworzyć maszynę wirtualną.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |Używa pierwszej subskrypcji w pliku subskrypcji |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="webdeploypackage"></a>WebDeployPackage
Ścieżka do pakietu wdrożeniowego sieci Web, która ma zostać opublikowana na maszynie wirtualnej. Ten pakiet można utworzyć przy użyciu Kreatora publikacji w sieci Web w programie Visual Studio. Zobacz [How to: Utwórz pakiet wdrożeniowy sieci Web w programie](https://msdn.microsoft.com/library/dd465323.aspx)Visual Studio.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="allowuntrusted"></a>AllowUntrusted
W przypadku wartości true Zezwalaj na korzystanie z certyfikatów, które nie są podpisane przez zaufany główny urząd certyfikacji.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |false |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="vmpassword"></a>VMPassword
Poświadczenia dla konta maszyny wirtualnej. Przykład:-VMPassword @ {Name = "admin"; Hasło = "hasło"}

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Poświadczenia dla bazy danych SQL na platformie Azure. Przykład:-DatabaseServerPassword @ {Name = "admin"; Hasło = "hasło"}

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Jeśli wartość jest równa true, Wydrukuj komunikaty ze skryptu do strumienia wyjściowego.

| Aliasy | brak |
| --- | --- |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |false |
| Akceptujesz dane wejściowe potoku? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="remarks"></a>Uwagi
Aby uzyskać pełne wyjaśnienie, jak używać skryptu do tworzenia środowisk deweloperskich i testowych, zobacz [Używanie skryptów programu Windows PowerShell do publikowania w środowiskach deweloperskich i testowych](vs-azure-tools-publishing-using-powershell-scripts.md).

Plik konfiguracji JSON określa szczegóły dotyczące tego, co ma zostać wdrożone. Zawiera informacje, które zostały określone podczas tworzenia projektu, takie jak nazwa, grupa koligacji, obraz VHD i rozmiar maszyny wirtualnej. Obejmuje również punkty końcowe maszyny wirtualnej, bazy danych do aprowizacji, jeśli istnieją i parametry wdrażania w sieci Web. Poniższy kod przedstawia przykładowy plik konfiguracji JSON:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "West US",
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

Plik konfiguracji JSON można edytować, aby zmienić zainicjowaną zawartość. Wymagana jest maszyna wirtualna i usługa w chmurze, ale sekcja bazy danych jest opcjonalna.
