---
title: Włączanie aktualizacji administratora do Visual Studio z Microsoft Endpoint Configuration Manager
titleSuffix: ''
description: Dowiedz się więcej na temat sposobu wdrażania aktualizacji administratora w Visual Studio.
ms.date: 04/06/2021
ms.custom: ''
ms.topic: overview
ms.assetid: 546fbad6-f12b-49cf-bccc-f2e63e051a18
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: affb5a0c78c1ad1e230c571485385d9f55fc2bec
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307456"
---
# <a name="enabling-administrator-updates-to-visual-studio-with-microsoft-endpoint-configuration-manager"></a>Włączanie aktualizacji administratora do Visual Studio z Microsoft Endpoint Configuration Manager

Program Microsoft Endpoint Configuration Manager (SCCM) może zarządzać aktualizacjami Visual Studio 2017 i Visual Studio 2019 przy użyciu przepływu pracy zarządzania aktualizacjami oprogramowania.

> [!NOTE]
> Dla uproszczenia dokumentacji zawartość poniżej będzie zbiorczo odnosić się do produktów z Visual Studio 2017, Visual Studio 2019 i Visual Studio 2022 jako "Visual Studio".

Gdy firma Microsoft opublikuje nową Visual Studio aktualizacji usługi Content Delivery Network (CDN), firma Microsoft jednocześnie opublikuje odpowiedni pakiet aktualizacji administratora na Microsoft Update serwerach. Umożliwi to administratorowi dystrybucję aktualizacji Visual Studio za [](https://www.catalog.update.microsoft.com/Home.aspx) pośrednictwem katalogu Microsoft Update (MUC) [lub Windows Server Update Services](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) (WSUS). Menedżer konfiguracji można skonfigurować do synchronizowania aktualizacji administratora programu Visual Studio z katalogu programu WSUS z serwerem lokacji, a następnie pobrać aktualizację i rozpowszechnić ją na maszynach klienckich Visual Studio w całej organizacji. Aby uzyskać więcej informacji o poprawkach, które są obecne w poszczególnych wersjach Visual Studio, zobacz informacje [o wersji](/visualstudio/releases/2019/release-notes).

Aby dystrybuować Visual Studio administratorów za pośrednictwem Menedżer konfiguracji, należy wykonać następujące dwa początkowe kroki przygotowania:
1. Włącz Menedżer konfiguracji, aby otrzymywać Visual Studio aktualizacji administratora. 
2. Włącz lub wyłącz maszyny klienckie, aby otrzymywać Visual Studio administratorów z Menedżer konfiguracji.

Po wykonanie tych kroków można użyć funkcji zarządzania aktualizacjami oprogramowania usługi Menedżer konfiguracji w celu wdrożenia aktualizacji Visual Studio administratora. Różne typy i cechy aktualizacji Visual Studio są opisane w te tematach Stosowanie aktualizacji administratora [,](../install/applying-administrator-updates.md)który zawiera wskazówki dotyczące tego, jak i kiedy powinny być dystrybuowane w całej organizacji. Aby uzyskać więcej informacji o Menedżer konfiguracji i opcjach, zobacz [Wdrażanie aktualizacji oprogramowania w programie Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/deploy-use/deploy-software-updates).

## <a name="enable-configuration-manager-to-receive-visual-studio-administrator-update-notifications"></a>Włącz Menedżer konfiguracji, aby otrzymywać Visual Studio aktualizacji administratora

Aby umożliwić Menedżer konfiguracji zarządzania Visual Studio aktualizacjami administratora, potrzebne są:

* Bieżąca licencjonowana wersja systemu Windows Server z systemem Microsoft Endpoint Configuration Manager (Current Branch) i Windows Server Update Services (WSUS). Do wdrażania tych aktualizacji nie można używać samego programu WSUS; Należy go używać w połączeniu z Menedżer konfiguracji.

* Serwer usług WSUS najwyższego poziomu hierarchii i serwer lokacji najwyższego poziomu Menedżer konfiguracji muszą mieć dostęp do adresów URL i portów Visual Studio wymienionych tutaj: Instalowanie i używanie usług Visual Studio i usług platformy Azure za zaporą lub serwerem [proxy.](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)  

* Serwer Microsoft Endpoint Configuration Manager musi być skonfigurowany do odbierania powiadomień, Visual Studio są dostępne pakiety aktualizacji administratora.  Aby to zrobić, wykonaj poniższe kroki i aby uzyskać więcej informacji, zobacz Wprowadzenie do [aktualizacji oprogramowania w programie Microsoft Endpoint Configuration Manager](/mem/configmgr/sum/understand/software-updates-introduction).

  1. W konsoli Menedżer konfiguracji wybierz pozycję Administracja **(w** lewym dolnym rogu), a następnie wybierz pozycję Konfiguracja lokacji **(w** lewym środkowym rogu), a następnie pozycję Lokacje **i** wybierz serwer lokacji.

  2. Na **wstążce** karty Narzędzia główne w górnej części **przycisku** grupy Ustawienia wybierz pozycję Konfiguruj składniki lokacji, a następnie wybierz pozycję Punkt aktualizacji **oprogramowania.**

  3. W **oknie dialogowym Właściwości składnika punktu** aktualizacji oprogramowania:

        * Na karcie **Produkty** w **hierarchii Narzędzia deweloperskie,** środowiska uruchomieniowe i redystrybucyjne wybierz wersje Visual Studio, które chcesz zsynchronizować.

        * Na karcie **Klasyfikacje** upewnij się, że wybrano opcje "Aktualizacje zabezpieczeń", "Pakiety funkcji" i "Aktualizacje".

  4. Następnie zsynchronizuj aktualizacje oprogramowania z serwerem WSUS, wybierając pozycję  Biblioteka oprogramowania **(w** lewym dolnym rogu), a następnie na wstążce karty Narzędzia główne u góry wybierz przycisk **Synchronizuj aktualizacje** oprogramowania. Synchronizowanie aktualizacji oprogramowania spowoduje, że Visual Studio aktualizacje administratora będą widoczne w konsoli programu i będzie można je wdrożyć z Menedżer konfiguracji oprogramowania.

## <a name="enable-or-disable-client-machines-ability-to-receive-visual-studio-administrator-updates-from-configuration-manager"></a>Włącz (lub wyłącz) możliwość otrzymywania aktualizacji Visual Studio administratora z Menedżer konfiguracji

Aby umożliwić komputerowi klienckiemu akceptowanie aktualizacji administratora programu Visual Studio, należy się upewnić, że narzędzie do wykrywania klienta programu Visual Studio jest poprawnie zainstalowane, a następnie należy ustawić klucz rejestru, aby umożliwić klientowi otrzymywanie aktualizacji administratora.  

### <a name="visual-studio-client-detector-utility"></a>Visual Studio narzędzia do wykrywania klienta

Aby [aktualizacje Visual Studio](https://support.microsoft.com/help/5001148) zostały prawidłowo rozpoznane i odebrane, na komputerach klienckich musi być zainstalowane narzędzie do wykrywania klienta. To narzędzie zostało dołączone do wszystkich aktualizacji produktów z wersji Visual Studio 2017 i Visual Studio 2019, które zostały wydane 12 maja 2020 r. lub później, jest ono dołączone jako wymaganie wstępne ze wszystkimi aktualizacjami administratora programu Visual Studio i jest również dostępne w wykazie usług [Microsoft Update](https://catalog.update.microsoft.com) do niezależnej instalacji.

### <a name="encoding-administrator-intent-on-the-client-machines"></a>Intencja administratora kodowania na maszynach klienckich

Komputery klienckie muszą być włączone, aby otrzymywać aktualizacje administratora. Ten krok jest niezbędny, aby upewnić się, że aktualizacje nie zostaną przypadkowo lub przypadkowo wypchnąć do nieświadomych komputerów klienckich.

Klucz **AdministratorUpdatesEnabled** jest przeznaczony dla administratora w celu kodowania   intencji administratora. Ten klucz może być w dowolnej standardowej lokalizacji Visual Studio zgodnie z opisem w dokumentacji ustawianie wartości domyślnych dla wdrożeń w [przedsiębiorstwie Visual Studio](/visualstudio/install/set-defaults-for-enterprise-deployments) aplikacji. Aby utworzyć i ustawić wartość tego klucza, wymagany jest dostęp administratora na komputerze klienckim.

* Aby skonfigurować komputer kliencki do akceptowania aktualizacji administratora, ustaw dla ustawienia **AdministratorUpdatesEnabled**   REG_DWORD wartość **1**.
* Jeśli brakuje klucza REG_DWORD **AdministratorUpdatesEnabled** lub ustawiono wartość 0, aktualizacje administratora będą blokowane na   komputerze klienckim. 

## <a name="feedback-and-support"></a>Opinie i pomoc techniczna

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

Za pomocą następujących metod można przekazać opinię na temat aktualizacji Visual Studio administratorów lub zgłaszania problemów, które mają wpływ na aktualizacje:

* Zapoznaj się ze [wskazówkami Visual Studio rozwiązywanie problemów z instalacją i uaktualnianiem.](../install/troubleshooting-installation-issues.md)
* Ask questions to the community at the [Visual Studio Setup Q&A Forum](/answers/topics/vs-setup.html).
* Przejdź do strony [Visual Studio pomocy technicznej](https://visualstudio.microsoft.com/vs/support/)i sprawdź, czy problem znajduje się na liście często zadawanych pytań.  Możesz również wybrać przycisk [Link do pomocy technicznej,](https://visualstudio.microsoft.com/vs/support/#talktous) aby uzyskać pomoc w czacie.
* [Przekazać opinię na temat](https://aka.ms/vs/wsus/feedback) funkcji lub zgłosić problem Visual Studio dotyczące tego doświadczenia podczas włączania aktualizacji administratora.
* Skontaktuj się z menedżerem ds. technicznych kont w organizacji firmy Microsoft.

## <a name="see-also"></a>Zobacz też

* [Stosowanie aktualizacji administratora](../install/applying-administrator-updates.md)
* [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)
* [Cykl życia produktu i obsługa techniczna programu Visual Studio](/visualstudio/productinfo/vs-servicing-vs)
* [Informacje o wersji programu Visual Studio 2019](/visualstudio/releases/2019/release-notes)
* [Informacje o wersji programu Visual Studio 2017](/visualstudio/releasenotes/vs2017-relnotes)
* [Instalowanie programu Visual Studio](../install/install-visual-studio.md)
* [Katalog Microsoft Update — często zadawane pytania](https://www.catalog.update.microsoft.com/faq.aspx)
* [Microsoft Endpoint Configuration Manager (SCCM)](/mem/configmgr)
* [Importowanie aktualizacji z wykazu firmy Microsoft do Menedżer konfiguracji](/mem/configmgr/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)
* [Windows Server Update Services (WSUS)](/windows-server/administration/windows-server-update-services/get-started-windows-server-update-services-wsus)
