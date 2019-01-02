---
title: Uaktualnianie projektów do bieżącej wersji narzędzi platformy Azure | Dokumentacja firmy Microsoft
description: Dowiedz się, jak uaktualnić projekt platformy Azure w programie Visual Studio do bieżącej wersji narzędzi platformy Azure
author: ghogen
manager: douge
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.prod: visual-studio-dev15
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ddbc8a221cd883c3f30a583a1c1f03430c5f00ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825508"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Jak uaktualniać projekty do bieżącej wersji narzędzi platformy Azure dla programu Visual Studio
## <a name="overview"></a>Omówienie
Po zainstalowaniu bieżąca wersja narzędzi platformy Azure (lub poprzedniej wersji, która jest nowsza niż 1.6), wszystkie projekty, które zostały utworzone przy użyciu narzędzi Azure Zwolnij przed 1.6 (listopad 2011) zostaną automatycznie uaktualnione zaraz po ich otwarciu. Jeśli nadal masz tej wersji zainstalowane projekty są tworzone za pomocą wersji 1.6 (listopad 2011) wersję tych narzędzi, możesz otworzyć te projekty w starszej wersji i później zdecydować, czy należy uaktualnić ich.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Jak projekt zmienia się po uaktualnieniu
Jeśli projekt zostanie automatycznie uaktualniony lub określ, czy chcesz go uaktualnić, projekt zostanie zmodyfikowany na potrzeby pracy z bieżącymi wersjami określone zestawy, a niektóre właściwości również są zmieniane, zgodnie z opisem w tej sekcji. Jeśli Twój projekt wymaga innych zmian, aby był zgodny z nowszą wersją narzędzia, musisz wprowadzić te zmiany ręcznie.

* Plik web.config dla ról sieć web i w pliku app.config dla ról procesów roboczych zostaną zaktualizowane do odniesienia nowszą wersję Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitoirTraceListener.dll.
* Zestawy Microsoft.WindowsAzure.StorageClient.dll Microsoft.WindowsAzure.Diagnostics.dll i Microsoft.WindowsAzure.ServiceRuntime.dll są uaktualniane do nowych wersji.
* Profile publikowania, które były przechowywane w pliku projektu platformy Azure (ccproj) są przenoszone do osobnego pliku przy użyciu .azurePubXml rozszerzenia, w **Publikuj** podkatalogu.
* Niektóre właściwości w profilu publikowania są aktualizowane, aby obsługiwać nowe i zmienione funkcje. **AllowUpgrade** zastępuje **DeploymentReplacementMethod** ponieważ możesz zaktualizować wdrożonej usłudze w chmurze, jednocześnie lub przyrostowo.
* Właściwość **UseIISExpressByDefault** zostaną dodane i ustawiona na wartość false, aby serwer sieci web, która jest używana do debugowania zmienią się automatycznie z Internet Information Services (IIS) do usług IIS Express. Usługi IIS Express jest domyślny serwer sieci web dla projektów, które są tworzone przy użyciu nowszych wersjach narzędzi.
* Jeśli pamięć podręczna systemu Azure jest hostowana w co najmniej jednej z ról projektu, niektóre właściwości w definicji usługi (plik csdef) i usługi konfiguracji (plik cscfg) są zmieniane, gdy projekt zostanie uaktualniony. Jeśli projekt używa pakietu NuGet usługi pamięć podręczna Azure, projekt jest uaktualniony do najnowszej wersji pakietu. Należy otworzyć plik web.config i sprawdź, czy konfiguracja klienta została zachowana poprawnie podczas procesu uaktualniania. Jeśli dodano odwołania do zestawów klienta pamięci podręcznej systemu Azure bez przy użyciu pakietu NuGet, te zestawy nie będą aktualizowane; należy ręcznie zaktualizować te odwołania do nowych wersji.

> [!IMPORTANT]
> Aby uzyskać F# projektów, należy ręcznie zaktualizować odwołania do zestawów platformy Azure, dlatego, że odwołują się do nowszych wersji te zestawy.
> 
> 

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Jak uaktualnić projekt platformy Azure do bieżącej wersji
1. Zainstaluj bieżącą wersję narzędzi platformy Azure do instalacji programu Visual Studio, której chcesz użyć dla uaktualnionego projektu, a następnie otworzyć projekt, który chcesz uaktualnić. Jeśli projekt został utworzony za pomocą narzędzi Azure Zwolnij przed 1.6 (listopad 2011) projekt zostaje automatycznie uaktualnione do bieżącej wersji. Jeżeli projekt został utworzony za pomocą listopad 2011 wydania tej wersji jest nadal zainstalowany, projekt zostanie otwarty w tej wersji.
2. W Eksploratorze rozwiązań Otwórz menu skrótów dla węzła projektu, wybierz polecenie **właściwości**, a następnie wybierz **aplikacji** karty zostanie wyświetlone okno dialogowe.
   
    **Aplikacji** karta przedstawia wersja narzędzi, który jest skojarzony z projektem. Jeśli pojawi się bieżącą wersję narzędzia platformy Azure, projekt został już uaktualniony. Jeśli została zainstalowana nowsza wersja narzędzi niż pokazuje, jakie karty, **uaktualnienia** pojawi się przycisk.
3. Wybierz **uaktualnienia** przycisk, aby uaktualnić projekt do bieżącej wersji narzędzia.
4. Skompiluj projekt, a następnie adresować wszelkie błędy powstałe w wyniku zmiany interfejsu API. Aby dowiedzieć się, jak zmodyfikować kod do nowej wersji zobacz dokumentację dla określonego interfejsu API.
