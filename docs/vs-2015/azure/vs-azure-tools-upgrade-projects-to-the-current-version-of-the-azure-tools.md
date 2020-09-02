---
title: Jak uaktualnić projekty do bieżącej wersji narzędzi systemu Azure | Microsoft Docs
description: Dowiedz się, jak uaktualnić projekt platformy Azure w programie Visual Studio do bieżącej wersji narzędzi platformy Azure
author: ghogen
manager: jillfra
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 27ab6619a4d36fc105a3b8a668a31a33ae4c2a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62793737"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Jak uaktualniać projekty do bieżącej wersji narzędzi platformy Azure dla programu Visual Studio
## <a name="overview"></a>Omówienie
Po zainstalowaniu bieżącej wersji narzędzi platformy Azure (lub wcześniejszej wersji nowszej niż 1,6) wszystkie projekty, które zostały utworzone przy użyciu narzędzi platformy Azure przed 1,6 (listopad 2011), zostaną automatycznie uaktualnione zaraz po ich otwarciu. Jeśli utworzono projekty przy użyciu wersji 1,6 (listopad 2011) tych narzędzi i nadal masz zainstalowaną wersję, możesz otworzyć te projekty w starszej wersji i zdecydować, czy mają zostać uaktualnione.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Sposób zmiany projektu podczas jego uaktualniania
Jeśli projekt jest automatycznie uaktualniany lub określono, że chcesz go uaktualnić, projekt zostanie zmodyfikowany w celu pracy z bieżącymi wersjami niektórych zestawów, a niektóre właściwości są również zmieniane w tej sekcji. Jeśli projekt wymaga innych zmian do zgodności z nowszą wersją narzędzi, należy wprowadzić te zmiany ręcznie.

* Plik web.config dla ról sieci Web i plik app.config dla ról procesów roboczych są aktualizowane w celu odwoływania się do nowszej wersji programu Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll.
* Zestawy Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll i Microsoft.WindowsAzure.ServiceRuntime.dll są uaktualnione do nowych wersji.
* Profile publikowania, które były przechowywane w pliku projektu platformy Azure (. ccproj), są przenoszone do oddzielnego pliku z rozszerzeniem. azurePubXml w podkatalogu **publikowania** .
* Niektóre właściwości w profilu publikowania zostały zaktualizowane w celu obsługi nowych i zmienionych funkcji. **AllowUpgrade** jest zastępowana przez **DeploymentReplacementMethod** , ponieważ można aktualizować wdrożoną usługę w chmurze jednocześnie lub przyrostowo.
* Właściwość **UseIISExpressByDefault** jest dodawana i ustawiona na wartość false, aby serwer sieci Web używany do debugowania nie zmienił się automatycznie z Internet Information Services (IIS) na IIS Express. IIS Express jest domyślnym serwerem sieci Web dla projektów utworzonych przy użyciu nowszych wersji narzędzi.
* Jeśli buforowanie platformy Azure jest hostowane w co najmniej jednej z ról projektu, niektóre właściwości w konfiguracji usługi (pliku cscfg) i definicji usługi (plik. csdef) są zmieniane po uaktualnieniu projektu. Jeśli projekt używa pakietu NuGet buforowania platformy Azure, projekt zostanie uaktualniony do najnowszej wersji pakietu. Należy otworzyć plik web.config i sprawdzić, czy konfiguracja klienta była prawidłowo obsługiwana podczas procesu uaktualniania. Po dodaniu odwołań do zestawów klienta buforowania platformy Azure bez użycia pakietu NuGet te zestawy nie zostaną zaktualizowane; należy ręcznie zaktualizować te odwołania do nowych wersji.

> [!IMPORTANT]
> W przypadku projektów języka F # należy ręcznie zaktualizować odwołania do zestawów platformy Azure, aby odwoływać się do nowszych wersji tych zestawów.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Jak uaktualnić projekt platformy Azure do bieżącej wersji
1. Zainstaluj bieżącą wersję narzędzi platformy Azure w instalacji programu Visual Studio, której chcesz użyć dla uaktualnionego projektu, a następnie otwórz projekt, który chcesz uaktualnić. Jeśli projekt został utworzony za pomocą narzędzia platformy Azure przed 1,6 (listopad 2011), projekt zostanie automatycznie uaktualniony do bieżącej wersji. Jeśli projekt został utworzony z wydaniem listopad 2011, a wersja jest nadal zainstalowana, projekt zostanie otwarty w tej wersji.
2. W Eksplorator rozwiązań otwórz menu skrótów dla węzła projektu, wybierz **Właściwości**, a następnie wybierz kartę **aplikacja** w wyświetlonym oknie dialogowym.
   
    Na karcie **aplikacja** zostanie wyświetlona wersja narzędzi, która jest skojarzona z projektem. Jeśli zostanie wyświetlona bieżąca wersja narzędzi platformy Azure, projekt został już uaktualniony. Jeśli zainstalowano nowszą wersję narzędzi niż wyświetlana na karcie, pojawia się przycisk **Uaktualnij** .
3. Wybierz przycisk **Uaktualnij** , aby uaktualnić projekt do bieżącej wersji narzędzi.
4. Skompiluj projekt, a następnie rozwiąż wszelkie błędy wynikające ze zmian interfejsu API. Informacje o sposobach modyfikowania kodu dla nowej wersji znajdują się w dokumentacji dotyczącej konkretnego interfejsu API.
