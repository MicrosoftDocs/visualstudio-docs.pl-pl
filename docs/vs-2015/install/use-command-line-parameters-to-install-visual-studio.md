---
title: Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio 2015 | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: e81e9f7fad5976ad853254e04289d89d09b87ac6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922186"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [Użyj parametrów wiersza polecenia, aby zainstalować program Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Po zainstalowaniu programu Visual Studio 2015 w wierszu polecenia można użyć poniższych parametrów wiersza polecenia (nazywanych również przełącznikami).

> [!NOTE]
>  Upewnij się, że Instalator rzeczywiste, a nie pliku inicjującego. Na przykład, upewnij się, że używasz **`vs_enterprise.exe`** zamiast vs_enterprise_*GUID*.exe. Możesz pobrać Instalator [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Lista parametrów wiersza polecenia
 Parametrach wiersza polecenia programu Visual Studio nie jest rozróżniana wielkość liter.

|Parametr|Opis|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/ h**|Wyświetla parametry wiersza polecenia|
|**/ AddRemoveFeatures**|Określa, które funkcje mają być dodawane lub usuwane z zainstalowanego produktu.|
|**/ AdminFile** *AdminDeployment.xml*|Instaluje Visual Studio przy użyciu pliku danych określonego dla instalacji administracyjnej.|
|**/ ChainingPackage** *BundleName*|Określa, który pakiet jest powiązany z danym pakietem. Można również określić kohortę programu poprawy jakości obsługi klienta.|
|**/ CreateAdminFile \<nazwa pliku >**|Określa lokalizację utworzenia pliku kontrolnego, który może być używany z parametrem/adminfile.|
|**/ CustomInstallPath** *InstallationDirectory*|Instaluje wszystkie pakiety przeznaczone do zmiany platformy docelowej w katalogu określonym przez użytkownika.|
|**/ ForceRestart**|Zawsze ponownie uruchamia komputer po zakończeniu instalacji.|
|**/ pełne**|Instaluje wszystkie funkcje produktu.|
|**/ InstallSelectableItems \<nazwa elementu 1 > [;\< Nazwa elementu 2 >]**|Lista elementów drzewa wyboru można zaznaczyć na ekranie wyboru kreatora instalacji.|
|**/l**<br /><br /> **/ Dziennika** *nazwy pliku*|Określa lokalizację pliku dziennika.|
|**/ Layout** *katalogu*|Kopiuje pliki z nośnika instalacyjnego do katalogu określonego przez użytkownika.|
|**/ NoCacheOnlyMode**|Zapobiega wstępnemu zapełnianiu pamięci podręcznej pakietu.|
|**/ NoRefresh**|Zapobiega sprawdzaniu dostępności nowych wersji tego produktu dla wymaganych lub zalecanych zaktualizowanych wersji.|
|**/ norestart /**|Zapobiega ponownemu uruchomieniu komputera przez aplikację instalacji w trakcie lub po zakończeniu instalacji. Zobacz sekcję kody powrotne [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md) poznać kody powrotne do wyszukania.|
|**/ noweb**|Uniemożliwia instalację z Internetu.|
|**/ OverrideFeedUri \<ścieżkę do pliku źródła danych >**|Ścieżka do lokalnego lub zewnętrznego źródła danych opisującego elementy oprogramowania.|
|**/ ProductKey**<br /><br /> *Klucz produktu*|Ustawia niestandardowy klucz produktu, który nie zawiera łączników i nie więcej niż 25 znaków.|
|**/ PromptRestart**|Monituje użytkownika przed ponownym uruchomieniem komputera.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|Pomija interfejs użytkownika (UI) dla instalacji aplikacji. Jeśli jest już zainstalowany program Visual Studio i nie określono żadnych parametrów oprócz tego jednego, aplikacja instalacji działa w trybie konserwacji.|
|**/qb**<br /><br /> **/ passive**|Wyświetla postęp, ale nie czeka na dane wejściowe użytkownika.|
|**/ Repair**|Naprawia program Visual Studio.|
|**/ SuppressRefreshPrompt**|Zapobiega wyświetlaniu dostępne okno dialogowe aktualizacji w Kreatorze instalacji, w związku z tym, Kreator instalacji automatycznie zaakceptuje wszystkie wymagane lub zalecane zaktualizowane wersje.|
|**/u**<br /><br /> **/ Uninstall**|Odinstalowuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/ Uninstall/Force**<br /><br /> **/u/Force**|Odinstalowuje program Visual Studio i wszystkie funkcje, które są współużytkowane z innymi produktami. **Ostrzeżenie:**  Jeśli użyto tego parametru, inne produkty zainstalowane na tym samym komputerze mogą nie działać poprawnie.|

## <a name="see-also"></a>Zobacz też
 [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)