---
title: Używanie parametrów wiersza polecenia do instalowania programu Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180251"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [Używanie parametrów wiersza polecenia do instalowania programu Visual Studio](/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Po zainstalowaniu programu Visual Studio 2015 z poziomu wiersza polecenia można użyć następujących parametrów wiersza polecenia (nazywanych również przełącznikami).

> [!NOTE]
> Upewnij się, że używasz rzeczywistego Instalatora, a nie pliku programu inicjującego. Na przykład upewnij się, że używasz **`vs_enterprise.exe`** zamiast Vs_enterprise_*GUID*. exe. Można pobrać Instalatora z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Lista parametrów wiersza polecenia

W parametrach wiersza polecenia programu Visual Studio nie jest rozróżniana wielkość liter.

|Parametr|Opis|
|---------------|-----------------|
|**/?**<br /><br /> **/Help**<br /><br /> **/h**|Wyświetla parametry wiersza polecenia|
|**/AddRemoveFeatures**|Określa, które funkcje mają być dodawane lub usuwane z zainstalowanego produktu.|
|**Parametrem/adminfile.** *AdminDeployment.xml*|Instaluje Visual Studio przy użyciu pliku danych określonego dla instalacji administracyjnej.|
|**/ChainingPackage** *BundleName*|Określa, który pakiet jest powiązany z danym pakietem. Można również użyć do określenia kohorta poprawy jakości obsługi klienta.|
|**/CreateAdminFile \<filename>**|Określa lokalizację, w której ma zostać utworzony plik kontrolny, który może być używany z parametrem/adminfile.|
|**/CustomInstallPath** *InstallationDirectory*|Instaluje wszystkie pakiety przeznaczone do zmiany platformy docelowej w katalogu określonym przez użytkownika.|
|**/ForceRestart**|Zawsze ponownie uruchamia komputer po zakończeniu instalacji.|
|**/full**|Instaluje wszystkie funkcje produktu.|
|**/InstallSelectableItems \<item name 1> [; \<item name 2> ]**|Lista elementów drzewa wyboru do sprawdzenia na ekranie wyboru kreatora instalacji.|
|**przełącznika**<br /><br /> **/Log** *Nazwa pliku* /log|Określa lokalizację pliku dziennika.|
|**/layout** *katalog* /layout|Kopiuje pliki z nośnika instalacyjnego do katalogu określonego przez użytkownika.|
|**/NoCacheOnlyMode**|Uniemożliwia wstępne wypełnianie pamięci podręcznej pakietu.|
|**/NoRefresh**|Zapobiega sprawdzaniu dostępności nowych wersji tego produktu dla wymaganych lub zalecanych zaktualizowanych wersji.|
|**/norestart**|Zapobiega ponownemu uruchomieniu komputera przez aplikację instalacji w trakcie lub po zakończeniu instalacji. Zobacz sekcję kody powrotne w [podręczniku administratora programu Visual Studio](../install/visual-studio-administrator-guide.md) , aby uzyskać kody powrotne do wyszukania.|
|**/noweb**|Uniemożliwia instalację z Internetu.|
|**/OverrideFeedUri \<path to feed file>**|Ścieżka do lokalnego, zewnętrznego źródła danych opisującego elementy oprogramowania|
|**/ProductKey**<br /><br /> *ProductKey (Klucz produktu)*|Ustawia niestandardowy klucz produktu, który nie zawiera kresek i nie więcej niż 25 znaków.|
|**/PromptRestart**|Monituje użytkownika przed ponownym uruchomieniem komputera.|
|**parametru**<br /><br /> **spowoduje**<br /><br /> **/s**<br /><br /> **/Silent**|Pomija interfejs użytkownika (UI) dla instalacji aplikacji. Jeśli jest już zainstalowany program Visual Studio i nie określono żadnych parametrów oprócz tego jednego, aplikacja instalacji działa w trybie konserwacji.|
|**/QB**<br /><br /> **/Passive**|Wyświetla postęp, ale nie czeka na dane wejściowe użytkownika.|
|**/Repair**|Naprawia program Visual Studio.|
|**/SuppressRefreshPrompt**|Zapobiega wyświetlaniu okna dialogowego aktualizacji dostępnych w Kreatorze instalacji, w związku z czym Kreator instalacji będzie akceptować automatyczne wszystkie wymagane lub zalecane zaktualizowane wersje.|
|**Określ**<br /><br /> **/Uninstall**|Odinstalowuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|
|**/Uninstall/Force**<br /><br /> **/u/Force**|Odinstalowuje program Visual Studio i wszystkie funkcje, które są współużytkowane z innymi produktami. **Ostrzeżenie:**  Jeśli użyjesz tego parametru, inne produkty zainstalowane na tym samym komputerze mogą przestać działać poprawnie.|

## <a name="see-also"></a>Zobacz też

- [Przewodnik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)