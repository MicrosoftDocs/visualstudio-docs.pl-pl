---
title: Podręcznik administratora programu Visual Studio
titleSuffix: ''
description: Dowiedz się więcej na temat wdrażania Visual Studio w środowisku przedsiębiorstwa.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ba41c545c2af2e0490ef0410fde7849706123940
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306712"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio

W środowiskach przedsiębiorstwa administratorzy systemu zwykle wdrażają instalacje dla użytkowników końcowych z udziału sieciowego lub przy użyciu oprogramowania do zarządzania systemami. Zaprojektowaliśmy aparat konfiguracji usługi Visual Studio do obsługi wdrażania w przedsiębiorstwie, zapewniając administratorom systemu możliwość tworzenia lokalizacji instalacji sieciowej, wstępnego konfigurowania wartości domyślnych instalacji, wdrażania kluczy produktów podczas procesu instalacji oraz zarządzania aktualizacjami produktów po pomyślnym wdrożeniu.

Ten przewodnik administratora zawiera oparte na scenariuszach wskazówki dotyczące wdrażania w przedsiębiorstwie w środowiskach sieciowych.

## <a name="before-you-begin"></a>Zanim rozpoczniesz

Przed wdrożeniem Visual Studio w całej organizacji należy podjąć kilka decyzji i wykonać zadania:

::: moniker range=">=vs-2019"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji.](/visualstudio/releases/2019/system-requirements/)

::: moniker-end

::: moniker range="vs-2017"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji.](/visualstudio/productinfo/vs2017-system-requirements-vs/)

::: moniker-end

* Podejmij decyzję o potrzebach obsługi.

  Jeśli firma musi pozostać na zestawie funkcji dłużej, ale nadal chce regularnie korzystać z aktualizacji obsługi, zaplanuj korzystanie z planu bazowego obsługi. Aby uzyskać więcej informacji, zobacz sekcję Opcje pomocy technicznej dla klientów w wersji Enterprise i ***Professional*** na stronie cyklu życia i obsługi technicznej produktu [Visual Studio,](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) a także na stronie Update Visual Studio while on [a servicing baseline](update-servicing-baseline.md) (Cykl życia produktu i obsługa techniczna w wersji Visual Studio na stronie planu bazowego obsługi).

* Wybierz model aktualizacji.

  Skąd mają pochodzić poszczególne maszyny klienckie, z których mają być dostępne aktualizacje produktu? W szczególności zdecyduj, czy klient ma uzyskać aktualizacje z Internetu, czy z udziału lokalnego całej firmy. Następnie, jeśli zdecydujesz się używać udziału lokalnego, zdecyduj, czy poszczegnieni użytkownicy mogą aktualizować własnych klientów, czy też administrator ma programowo aktualizować klientów. Najlepiej, jeśli te decyzje zostały podjęte przed pierwotną instalacją na komputerze klienckim. Aby uzyskać więcej informacji, [zobacz Create a network-based installation of Visual Studio](../install/create-a-network-installation-of-visual-studio.md)( Tworzenie instalacji sieciowej Visual Studio .

  Istnieje możliwość zaktualizowania układu instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktu, aby można było go używać zarówno jako punktu instalacji najnowszej aktualizacji programu Visual Studio, jak i do obsługi instalacji, które zostały już wdrożone na klienckich stacjach roboczych. Aby uzyskać więcej informacji, [zobacz Aktualizowanie instalacji sieciowej programu Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Organizacje, które korzystają z narzędzi wdrażania w przedsiębiorstwie, mogą skorzystać z faktu, że Visual Studio aktualizacje są dostępne w katalogu Microsoft Update i Windows Server Update Services. Aby uzyskać więcej informacji, zobacz [Włączanie aktualizacji administratora i](../install/enabling-administrator-updates.md) Stosowanie aktualizacji [administratora.](../install/applying-administrator-updates.md)

  W przypadku komputerów, które nie są połączone z Internetem, utworzenie minimalnego układu jest najprostszym i najszybszym sposobem aktualizowania wystąpień Visual Studio offline. Aby uzyskać więcej informacji, zobacz Update Visual Studio using a minimal offline layout (Aktualizowanie usługi przy [użyciu minimalnego układu w trybie offline).](update-minimal-layout.md)

::: moniker range=">=vs-2019"

* Zdecyduj, [których obciążeń i składników](workload-and-component-ids.md?view=vs-2019&preserve-view=true) potrzebuje Twoja firma.

* Zdecyduj, czy użyć [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (co upraszcza zarządzanie szczegółami w pliku skryptu).

::: moniker-end

::: moniker range="vs-2017"

* Zdecyduj, [których obciążeń i składników](workload-and-component-ids.md?view=vs-2017&preserve-view=true) potrzebuje Twoja firma.

* Zdecyduj, czy użyć [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (co upraszcza zarządzanie szczegółami w pliku skryptu).

::: moniker-end

* Zdecyduj, czy chcesz włączyć zasady grupy, czy chcesz skonfigurować usługę Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach.

::: moniker range=">=vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1. Pobieranie Visual Studio produktu

* [Wybierz obciążenia i składniki,](workload-and-component-ids.md?view=vs-2019&preserve-view=true) które chcesz zainstalować.

* [Utwórz udział sieciowy dla plików Visual Studio produktu](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Krok 2. Tworzenie skryptu instalacji

* Skompilowanie skryptu instalacji, który używa [parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) do kontrolowania instalacji.

  >[!NOTE]
  > Skrypty można uprościć przy użyciu [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Pamiętaj, aby utworzyć plik odpowiedzi zawierający domyślną opcję instalacji.

* (Opcjonalnie) [Zastosuj klucz produktu licencji woluminu](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) jako część skryptu instalacji, aby użytkownicy nie musieli oddzielnie aktywować oprogramowania.

* (Opcjonalnie) Zaktualizuj układ sieci, aby [kontrolować, kiedy](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true)i z którego aktualizacje produktów są dostarczane do użytkowników końcowych.

* (Opcjonalnie) Ustaw zasady rejestru, które mają wpływ na wdrożenie usługi Visual Studio na przykład miejsce instalacji [](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) niektórych pakietów współużytkowanych z innymi wersjami lub wystąpieniami, gdzie pakiety są buforowane lub czy pakiety są [buforowane.](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true)

* (Opcjonalnie) Ustaw zasady grupy. Można również skonfigurować [Visual Studio, aby wyłączyć opinie klientów](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy-updates"></a>Krok 3. Wdrażanie aktualizacji

Użyj wybranej technologii wdrażania, aby wykonać skrypt na docelowych stacjach roboczych dewelopera.

* [Odśwież lokalizację sieciową przy](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) użyciu najnowszych aktualizacji Visual Studio, uruchamiając polecenie używane w kroku 1 w regularnych odstępach czasu w celu dodania zaktualizowanych składników.

  Możesz zaktualizować Visual Studio za pomocą skryptu aktualizacji. Aby to zrobić, użyj [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) parametru wiersza polecenia.

  Możesz wdrażać Visual Studio z katalogu Windows Server Update Services lub katalogu Microsoft Update za pomocą narzędzi, takich jak System Center Menedżer konfiguracji.  Aby uzyskać więcej informacji, zobacz [Stosowanie](applying-administrator-updates.md) aktualizacji administratora. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Krok 4. (Opcjonalnie) Weryfikowanie instalacji za pomocą Visual Studio narzędzi

Dostępnych jest kilka narzędzi, które ułatwiają wykrywanie [zainstalowanych wystąpień](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) Visual Studio na maszynach klienckich i zarządzanie nimi.

## <a name="advanced-configuration"></a>Konfiguracja zaawansowana

Domyślnie instalacja aplikacji Visual Studio uwzględnianie typów niestandardowych w wyszukiwaniach Bing z listy błędów F1 i linków kodu. Można skonfigurować Visual Studio, aby wyłączyć mechanizm wyszukiwania z uwzględnieniem typów użytkowników niestandardowych, zmieniając wartość następującego klucza rejestru według zasad:

**"PutCustomTypeInBingSearch" DWORD 0**

Rejestr znajduje się w katalogu *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics gałęzi rejestru \* prywatnego. Aby uzyskać instrukcje dotyczące sposobu otwierania gałęzi rejestru, zobacz edytowanie rejestru [dla Visual Studio rejestru](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1. Pobieranie Visual Studio produktu

* [Wybierz obciążenia i składniki,](workload-and-component-ids.md?view=vs-2017&preserve-view=true) które chcesz zainstalować.

* [Utwórz udział sieciowy dla plików Visual Studio produktu](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Krok 2. Tworzenie skryptu instalacji

* Skompilowanie skryptu instalacji, który używa [parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) do kontrolowania instalacji.

  >[!NOTE]
  > Skrypty można uprościć przy użyciu [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Pamiętaj, aby utworzyć plik odpowiedzi zawierający domyślną opcję instalacji.

* (Opcjonalnie) [Zastosuj klucz produktu licencji woluminu](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) jako część skryptu instalacji, aby użytkownicy nie musieli oddzielnie aktywować oprogramowania.

* (Opcjonalnie) Zaktualizuj układ sieci, aby [kontrolować, kiedy](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true)i z którego aktualizacje produktów są dostarczane do użytkowników końcowych.

* (Opcjonalnie) Ustaw zasady rejestru, które mają wpływ na wdrożenie usługi Visual Studio na przykład miejsce instalacji [](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) niektórych pakietów współużytkowanych z innymi wersjami lub wystąpieniami, gdzie pakiety są buforowane lub czy pakiety są [buforowane.](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true)

* (Opcjonalnie) Ustaw zasady grupy. Można również skonfigurować [Visual Studio, aby wyłączyć opinie klientów](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy-updates"></a>Krok 3. Wdrażanie aktualizacji

Użyj wybranej technologii wdrażania, aby wykonać skrypt na docelowych stacjach roboczych dewelopera.

* [Odśwież lokalizację sieciową przy](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) użyciu najnowszych aktualizacji Visual Studio, uruchamiając polecenie używane w kroku 1 w regularnych odstępach czasu w celu dodania zaktualizowanych składników.

  Możesz zaktualizować Visual Studio za pomocą skryptu aktualizacji. Aby to zrobić, użyj [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) parametru wiersza polecenia.

  Możesz wdrażać Visual Studio z katalogu Windows Server Update Services lub katalogu Microsoft Update za pomocą narzędzi, takich jak System Center Menedżer konfiguracji. Aby uzyskać więcej informacji, zobacz [Stosowanie aktualizacji administratora](applying-administrator-updates.md).

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Krok 4. (Opcjonalnie) Weryfikowanie instalacji za pomocą Visual Studio narzędzi

Dostępnych jest kilka narzędzi, które ułatwiają wykrywanie [zainstalowanych wystąpień](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) Visual Studio na maszynach klienckich i zarządzanie nimi.

## <a name="advanced-configuration"></a>Konfiguracja zaawansowana

Domyślnie instalacja aplikacji Visual Studio uwzględnianie typów niestandardowych w wyszukiwaniach Bing z listy błędów F1 i linków kodu. Można skonfigurować Visual Studio, aby wyłączyć mechanizm wyszukiwania z uwzględnieniem typów użytkowników niestandardowych, zmieniając wartość następującego klucza rejestru według zasad:

**"PutCustomTypeInBingSearch" DWORD 0**

Rejestr znajduje się w katalogu `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` gałęzi rejestru prywatnego. Aby uzyskać instrukcje dotyczące sposobu otwierania gałęzi rejestru, zobacz edytowanie rejestru [dla Visual Studio rejestru](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Włączanie aktualizacji administratora](enabling-administrator-updates.md)
* [Stosowanie aktualizacji administratora](applying-administrator-updates.md)
* [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Instalowanie certyfikatów wymaganych do instalacji Visual Studio offline](install-certificates-for-visual-studio-offline.md)
* [Importowanie lub eksportowanie konfiguracji instalacji](import-export-installation-configurations.md)
* [Visual Studio instalatora archiwów](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio produktu i jego obsługa](/visualstudio/releases/2019/servicing/)
* [Ustawienia automatycznego ładowania synchronicznego](../extensibility/synchronously-autoloaded-extensions.md)
