---
title: Włączanie aktualizacji administratorów do programu Visual Studio przy użyciu programu Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Dowiedz się więcej o sposobie wdrażania aktualizacji administratorów w programie Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9ca14e1f4e84777fd1781249dd54a6646fb2c72a
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547482"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Włączanie aktualizacji administratorów do programu Visual Studio przy użyciu programu Microsoft Endpoint Configuration Manager

Program Microsoft Endpoint Configuration Manager (SCCM) może zarządzać aktualizacjami programu Visual Studio 2017 i programu Visual Studio 2019 za pomocą przepływu pracy zarządzania aktualizacjami oprogramowania.

> [!NOTE]
> W celu uproszczenia dokumentacji zawartość poniżej będzie odnosić się do produktów Visual Studio 2017 i Visual Studio 2019 w sposób zbiorczy jako "Visual Studio".

Gdy firma Microsoft opublikuje nową aktualizację programu Visual Studio w usłudze Content Delivery Network (CDN), firma Microsoft jednocześnie opublikuje odpowiedni pakiet aktualizacji administratora na serwerach Microsoft Update. Następnie umożliwi to administratorowi dystrybucję aktualizacji programu Visual Studio za pośrednictwem [wykazu Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) (MUC) lub [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Configuration Manager można skonfigurować w celu synchronizowania aktualizacji administratora programu Visual Studio z wykazu usług WSUS z serwerem lokacji, a następnie pobrania aktualizacji i rozesłania ich do komputerów klienckich programu Visual Studio w całej organizacji. Aby uzyskać więcej informacji na temat poprawek dostępnych w poszczególnych wersjach programu Visual Studio, zobacz [Informacje o wersji](https://docs.microsoft.com/visualstudio/releases/2019/release-notes). 

Aby dystrybuować aktualizacje administratorów programu Visual Studio za poorednictwem Configuration Manager, należy wykonać następujące dwa kroki wstępnego przygotowania: 
1. Włącz Configuration Manager otrzymywanie powiadomień o aktualizacjach administratora programu Visual Studio. 
2. Włącz (lub Wyłącz) komputery klienckie, aby otrzymywać aktualizacje administratorów programu Visual Studio z programu Configuration Manager.

Po wykonaniu tych kroków można użyć funkcji zarządzania aktualizacjami oprogramowania Configuration Manager, aby wdrożyć aktualizacje administratorów programu Visual Studio. Różne typy i cechy aktualizacji administratora programu Visual Studio zostały opisane w artykule [stosowanie aktualizacji administratorów](../install/applying-administrator-updates.md), które udostępniają wskazówki dotyczące sposobu i czasu, w którym powinny być dystrybuowane w całej organizacji. Aby uzyskać więcej informacji na temat funkcji i opcji Configuration Manager, zobacz [wdrażanie aktualizacji oprogramowania w programie Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/deploy-use/deploy-software-updates). 

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Włącz Configuration Manager otrzymywanie powiadomień o aktualizacjach administratora programu Visual Studio 

Aby umożliwić Configuration Manager zarządzania aktualizacjami administratora programu Visual Studio, potrzebne są następujące elementy: 

* Bieżąca licencjonowana wersja systemu Windows Server z uruchomionym programem Microsoft Endpoint Configuration Manager (Current Branch) i Windows Server Update Services (WSUS). Nie można użyć programu WSUS do wdrożenia tych aktualizacji; musi być używana w połączeniu z Configuration Manager. 

* Serwer WSUS najwyższego poziomu hierarchii i serwer lokacji najwyższego poziomu Configuration Manager muszą mieć dostęp do adresów URL i portów programu Visual Studio wymienionych tutaj: [Instalowanie i używanie usług programu Visual Studio i platformy Azure za zaporą lub serwerem proxy](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md).  

* Program Microsoft Endpoint Configuration Manager musi być skonfigurowany do odbierania powiadomień, gdy dostępne są pakiety aktualizacji administratora programu Visual Studio.  Aby to zrobić, wykonaj następujące czynności i aby uzyskać więcej informacji, zobacz [wprowadzenie do aktualizacji oprogramowania w programie Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/understand/software-updates-introduction).

  1. W konsoli Configuration Manager wybierz pozycję **Administracja** (w lewym dolnym rogu), a następnie wybierz pozycję **Konfiguracja lokacji** (z lewej strony), a następnie pozycję **Lokacje**, a następnie wybierz serwer lokacji. 

  2. Na karcie **Narzędzia główne** w górnej **części okna wybierz** pozycję **Konfiguruj składniki lokacji**, a następnie wybierz pozycję **punkt aktualizacji oprogramowania**. 

  3. W oknie dialogowym **właściwości składnika punktu aktualizacji oprogramowania** : 

        * Na karcie **produkty** w hierarchii **Narzędzia deweloperskie, środowiska uruchomieniowe i redystrybucyjne** wybierz wersje programu Visual Studio, które chcesz synchronizować.   

        * Na karcie **klasyfikacje** upewnij się, że są zaznaczone pozycje "aktualizacje zabezpieczeń", "pakiety funkcji" i "aktualizacje".   

  4. Następnie zsynchronizuj aktualizacje oprogramowania z serwerem WSUS, wybierając pozycję **Biblioteka oprogramowania** (z lewej strony), a następnie na karcie **Narzędzia główne** w górnej części ekranu wybierz przycisk **Synchronizuj aktualizacje oprogramowania** . Synchronizowanie aktualizacji oprogramowania spowoduje, że dostępne aktualizacje administratora programu Visual Studio będą widoczne w programie i można je wdrożyć z poziomu konsoli Configuration Manager.   

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Włącz (lub Wyłącz) możliwość odbierania aktualizacji administratorów programu Visual Studio z programu Configuration Manager

Aby umożliwić komputerowi klienckiemu akceptowanie aktualizacji administratora programu Visual Studio, należy się upewnić, że narzędzie wykrywania klienta programu Visual Studio jest prawidłowo zainstalowane i należy ustawić klucz rejestru, aby umożliwić klientowi otrzymywanie aktualizacji administratora.  

### <a name="visual-studio-client-detector-utility"></a>Narzędzie wykrywania klienta programu Visual Studio 

[Narzędzie do wykrywania klienta programu Visual Studio](https://support.microsoft.com/help/5001148) musi być zainstalowane na komputerach klienckich, aby administrator mógł prawidłowo rozpoznać i odebrać aktualizacje. To narzędzie zostało dołączone do wszystkich aktualizacji produktu Visual Studio 2017 i Visual Studio 2019, które zostały wydane od 12 maja 2020, a także dostępne w [katalogu Microsoft Update](https://catalog.update.microsoft.com) w celu samodzielnego zainstalowania go w programie. 

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Zamiar administratora kodowania na komputerach klienckich 

Komputery klienckie muszą być włączone, aby otrzymywać aktualizacje administratora. Ten krok jest niezbędny, aby upewnić się, że aktualizacje nie są przypadkowo ani przypadkowe wypchnięcie do komputerów klienckich. 

Klucz **AdministratorUpdatesEnabled**   został zaprojektowany z myślą o zakodowaniu zamiaru administratora przez administratora. Ten klucz może znajdować się w dowolnej standardowej lokalizacji programu Visual Studio, zgodnie z opisem w temacie ustawienia [domyślne dla wdrożeń w przedsiębiorstwie](https://docs.microsoft.com/visualstudio/install/set-defaults-for-enterprise-deployments) w dokumentacji programu Visual Studio. Do utworzenia i ustawienia wartości tego klucza wymagany jest dostęp administratora na komputerze klienckim. 

* Aby skonfigurować komputer kliencki do akceptowania aktualizacji administratorów, ustaw ****   klucz REG_DWORD AdministratorUpdatesEnabled na **1**. 
* Jeśli  ****   brakuje klucza REG_DWORD AdministratorUpdatesEnabled **lub ustawiono wartość 0**, aktualizacje administratorów będą blokowane przed zastosowaniem do komputera klienckiego. 

## <a name="feedback-and-support"></a>Opinie i pomoc techniczna
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Poniższe metody umożliwiają przesłanie opinii na temat aktualizacji administratora programu Visual Studio lub raportów dotyczących problemów, które mają wpływ na aktualizacje:
* Zapoznaj się ze wskazówkami dotyczącymi [rozwiązywania problemów dotyczących instalacji i uaktualniania programu Visual Studio](../install/troubleshooting-installation-issues.md) .
* Zadawaj pytania do społeczności w witrynie [Visual Studio Setup Q&forum](https://docs.microsoft.com/answers/topics/vs-setup.html).
* Przejdź do [strony pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/vs/support/)i sprawdź, czy Twój problem znajduje się na liście często zadawanych pytań.  Można również wybrać przycisk [link do pomocy technicznej](https://visualstudio.microsoft.com/vs/support/#talktous) , aby uzyskać pomoc dotyczącą rozmowy.
* [Podaj opinię dotyczącą funkcji lub Zgłoś problem](https://aka.ms/vs/wsus/feedback) do zespołu programu Visual Studio, który dotyczy tego środowiska, włączając aktualizacje administratorów.
* Skontaktuj się z kierownikiem ds. klientów firmy Microsoft.

## <a name="see-also"></a>Zobacz też
* [Stosowanie aktualizacji administratorów](../install/applying-administrator-updates.md)
* [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)
* [Cykl życia produktu i obsługa techniczna programu Visual Studio](https://docs.microsoft.com/visualstudio/productinfo/vs-servicing-vs)
* [Informacje o wersji programu Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/release-notes)
* [Informacje o wersji programu Visual Studio 2017](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes)
* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Wykaz Microsoft Update — często zadawane pytania](https://www.catalog.update.microsoft.com/faq.aspx)
* [Dokumentacja programu Microsoft Endpoint Configuration Manager (SCCM)](https://docs.microsoft.com/mem/configmgr)
* [Importuj aktualizacje z usługi Microsoft Catalog do Configuration Manager](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Dokumentacja programu Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
