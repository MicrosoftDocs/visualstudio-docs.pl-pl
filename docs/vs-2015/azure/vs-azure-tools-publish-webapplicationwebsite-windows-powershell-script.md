---
title: Publikowanie WebApplicationWebSite (skrypt programu Windows PowerShell) | Dokumentacja firmy Microsoft
description: Dowiedz się, jak opublikować projekt sieci web do witryny sieci Web platformy Azure. Ten skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.
author: ghogen
manager: jillfra
assetId: 63cfaa2d-f04d-40dc-8677-345385c278d5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: daf3e22176ef950177ebdb22ae6a9e36bcb5dd83
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771560"
---
# <a name="publish-webapplicationwebsite-windows-powershell-script"></a>Publish-WebApplicationWebSite (skrypt programu Windows PowerShell)
## <a name="syntax"></a>Składnia
Publikuje projektu sieci web do witryny sieci Web platformy Azure. Skrypt tworzy wymagane zasoby w subskrypcji platformy Azure, jeśli nie istnieją.

    Publish-WebApplicationWebSite
    –Configuration <configuration>
    -SubscriptionName <subscriptionName>
    -WebDeployPackage <packageName>
    -DatabaseServerPassword @{Name = "name"; Password = "password"}
    -SendHostMessagesToOutput
    -Verbose


## <a name="configuration"></a>Konfiguracja
Ścieżka do pliku konfiguracji JSON opisujące szczegóły wdrożenia.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagany? |true |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="subscriptionname"></a>SubscriptionName
Nazwa subskrypcji platformy Azure, który chcesz utworzyć witrynę sieci Web w.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="webdeploypackage"></a>WebDeployPackage
Ścieżka do pakietu wdrożeniowego sieci web, aby opublikować w witrynie sieci Web. Ten pakiet jest tworzony za pomocą kreatora Publikowanie w sieci Web w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [rozpoczęcie korzystania z usług Azure Cloud Services i platformy ASP.NET](http://go.microsoft.com/fwlink/p/?LinkID=623089).

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="databaseserverpassword"></a>DatabaseServerPassword
Nazwa użytkownika i hasło dla bazy danych SQL na platformie Azure.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |brak |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
W przypadku opcji true drukowania komunikatów ze skryptu do strumienia wyjściowego.

| Parametr | Wartość domyślna |
| --- | --- |
| Aliasy |brak |
| Wymagany? |false |
| Pozycja |nazwane |
| Wartość domyślna |false |
| Akceptować wejście potokowe? |false |
| Akceptować symbole wieloznaczne? |false |

## <a name="remarks"></a>Uwagi
Aby uzyskać pełne wyjaśnienie sposobu użyć skryptu, aby utworzyć środowiska deweloperskie i testowe, zobacz [za pomocą skryptów programu PowerShell Windows Publikuj deweloperskim i testowym](vs-azure-tools-publishing-using-powershell-scripts.md).

Plik konfiguracji JSON określa szczegóły co ma zostać wdrożony. Zawiera informacje, określone podczas tworzenia projektu, takie jak nazwa i nazwa użytkownika dla witryny sieci Web. Obejmuje również bazę danych do aprowizacji, jeśli istnieje. Poniższy kod przedstawia przykładowy plik konfiguracji JSON:

    {
        "environmentSettings": {
            "webSite": {
                "name": "WebApplication10554",
                "location": "West US"
            },
            "databases": [
                {
                    "connectionStringName": "DefaultConnection",
                    "databaseName": "WebApplication10554_db",
                    "serverName": "iss00brc88",
                    "user": "sqluser2",
                    "password": "",
                    "edition": "",
                    "size": "",
                    "collation": "",
                    "location": "West US"
                }
            ]
        }
    }

Można edytować plik JSON konfiguracji do zmiany, co jest wdrażana. Sekcja witryny sieci Web jest wymagana, ale sekcja bazy danych jest opcjonalna.

## <a name="next-steps"></a>Następne kroki
Aby uzyskać więcej informacji, zobacz [Publish-WebApplicationVM (skrypt programu Windows PowerShell)](vs-azure-tools-publish-webapplicationvm.md)
