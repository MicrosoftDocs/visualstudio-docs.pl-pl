---
title: Podręcznik administratora programu Visual Studio
titleSuffix: ''
description: Dowiedz się więcej o sposobie wdrażania programu Visual Studio w środowisku przedsiębiorstwa.
ms.date: 06/02/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9a586a0ab0d6b7a3ab34ef581e2ba6f5348232c2
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328793"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio

W środowiskach przedsiębiorstw Administratorzy systemu zazwyczaj wdrożyć instalacje do użytkowników końcowych z udziału sieciowego lub za pomocą oprogramowania do zarządzania systemami. Zaprojektowaliśmy aparat Instalatora programu Visual Studio do obsługi wdrożenia w przedsiębiorstwie, zapewniając możliwość tworzenia lokalizacji instalacji sieciowej, można wstępnie skonfigurować domyślne ustawienia instalacji, aby wdrożyć kluczy produktów podczas procesu instalacji administratorzy systemu i do zarządzania aktualizacjami produktu po pomyślne wdrożenie.

Ten Przewodnik administratora wskazówki oparte na scenariuszach dotyczące wdrażania w przedsiębiorstwie w środowiskach sieciowych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed wdrożeniem programu Visual Studio w organizacji istnieją pewne decyzje i zadania do wykonania:

::: moniker range="vs-2019"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](/visualstudio/releases/2019/system-requirements/).

* Zdecyduj, na potrzeby obsługi.

  Jeśli Twoja firma wymaga pozostać na funkcję, ale nadal jest już ustawiona chce otrzymywać regularne aktualizacje obsługi, planuje użyć obsługi linii bazowej. Aby uzyskać więcej informacji, zobacz ***opcje pomocy technicznej dla klientów, Enterprise i Professional*** części [cyklu życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) stronie, jak również [jak: Aktualizacja programu Visual Studio znajduje się w linię bazową obsługi](update-servicing-baseline.md) strony.

  Jeśli użytkownik chce zastosować aktualizacje obsługi wraz z aktualizacji zbiorczej funkcji, można wybrać najnowsze elementy.

* Decyduje o model aktualizacji.

  Gdzie chcesz komputery klienckie indywidualnych, aby pobrać aktualizacje? W szczególności zdecyduj, czy użytkownik chce uzyskać aktualizacji z Internetu lub udziału lokalnego całej firmy. Następnie Jeśli zdecydujesz się użyć lokalnego udziału, zdecyduj, czy poszczególnych użytkowników można zaktualizować ich własnych klientów lub jeśli chcesz, aby administrator programowo zaktualizować klientów.

* Zdecyduj, które [obciążenia i składniki](workload-and-component-ids.md?view=vs-2019) potrzebami firmy.

* Zdecyduj, czy ma być używany [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019) (który upraszcza zarządzanie szczegóły w pliku skryptu).

* Zdecyduj, jeśli chcesz włączyć zasad grupy, jeśli chcesz skonfigurować program Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach.

::: moniker-end

::: moniker range="vs-2017"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Zdecyduj, na potrzeby obsługi.

  Jeśli Twoja firma wymaga pozostać na funkcję, ale nadal jest już ustawiona chce otrzymywać regularne aktualizacje obsługi, planuje użyć obsługi linii bazowej. Aby uzyskać więcej informacji, zobacz ***obsługę starszych wersji programu Visual Studio*** części [cyklu życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) stronie, jak również [jak: Aktualizacja programu Visual Studio znajduje się w linię bazową obsługi](update-servicing-baseline.md) strony.

  Jeśli użytkownik chce zastosować aktualizacje obsługi wraz z aktualizacji zbiorczej funkcji, można wybrać najnowsze elementy.

* Decyduje o model aktualizacji.

  Gdzie chcesz komputery klienckie indywidualnych, aby pobrać aktualizacje? W szczególności zdecyduj, czy użytkownik chce uzyskać aktualizacji z Internetu lub udziału lokalnego całej firmy. Następnie Jeśli zdecydujesz się użyć lokalnego udziału, zdecyduj, czy poszczególnych użytkowników można zaktualizować ich własnych klientów lub jeśli chcesz, aby administrator programowo zaktualizować klientów.

* Zdecyduj, które [obciążenia i składniki](workload-and-component-ids.md?view=vs-2017) potrzebami firmy.

* Zdecyduj, czy ma być używany [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017) (który upraszcza zarządzanie szczegóły w pliku skryptu).

* Zdecyduj, jeśli chcesz włączyć zasad grupy, jeśli chcesz skonfigurować program Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 — pobieranie plików produktu Visual Studio

* [Wybieranie obciążenia i składniki](workload-and-component-ids.md?view=vs-2019) , którą chcesz zainstalować.

* [Utwórz udział sieciowy plików produktu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Krok 2 — budowanie skrypt instalacyjny

* Tworzenie skryptu instalacji, który używa [parametry wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) użytkownikom kontrolowania instalacji.

  >[!NOTE]
  > Skrypty można uprościć za pomocą [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019). Upewnij się utworzyć plik odpowiedzi, który zawiera Twoje domyślną opcją instalacji.

* (Opcjonalnie) [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) jako część instalacji skryptu, aby użytkownicy nie musieli aktywować oprogramowania oddzielnie.

* (Opcjonalnie) Aktualizowanie układu sieci, aby [kontrolowania, kiedy i gdzie w produkcie aktualizacje są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* (Opcjonalnie) Ustawienia zasad rejestru, które wpływają na wdrażanie programu Visual Studio, takie jak zainstalowanym niektórych pakietów współużytkowane z innymi wersjami lub wystąpienia, [której pakiety są buforowane](set-defaults-for-enterprise-deployments.md?view=vs-2019) lub [tego, czy pakiety są buforowane](disable-or-move-the-package-cache.md?view=vs-2019).

* (Opcjonalnie) Ustawianie zasad grupy. Możesz również [Konfigurowanie programu Visual Studio, aby wyłączyć opinie](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy"></a>Krok 3 — wdrażanie

* Użyj wybranej technologii wdrażania w celu wykonania skryptu na docelowych stacjach roboczych dla deweloperów.

## <a name="step-4---deploy-updates"></a>Krok 4 — wdrażanie aktualizacji

* [Odśwież lokalizacji sieciowej, z najnowszymi aktualizacjami](update-a-network-installation-of-visual-studio.md?view=vs-2019) do programu Visual Studio za pomocą polecenia używane w kroku 1 w regularnych odstępach czasu, aby dodać zaktualizowane składniki.

  Należy zaktualizować program Visual Studio przy użyciu skryptu aktualizacji. Aby to zrobić, należy użyć [ `update` ](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) parametru wiersza polecenia.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 — (opcjonalnie) za pomocą Visual Studio tools

Mamy kilka narzędzi, które ułatwiają [wykrywania wystąpień i zarządzanie nimi zainstalowanego programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019) na maszynach klienckich.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 — pobieranie plików produktu Visual Studio

* [Wybieranie obciążenia i składniki](workload-and-component-ids.md?view=vs-2017) , którą chcesz zainstalować.

* [Utwórz udział sieciowy plików produktu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Krok 2 — budowanie skrypt instalacyjny

* Tworzenie skryptu instalacji, który używa [parametry wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) użytkownikom kontrolowania instalacji.

  >[!NOTE]
  > Skrypty można uprościć za pomocą [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017). Upewnij się utworzyć plik odpowiedzi, który zawiera Twoje domyślną opcją instalacji.

* (Opcjonalnie) [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) jako część instalacji skryptu, aby użytkownicy nie musieli aktywować oprogramowania oddzielnie.

* (Opcjonalnie) Aktualizowanie układu sieci, aby [kontrolowania, kiedy i gdzie w produkcie aktualizacje są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* (Opcjonalnie) Ustawienia zasad rejestru, które wpływają na wdrażanie programu Visual Studio, takie jak zainstalowanym niektórych pakietów współużytkowane z innymi wersjami lub wystąpienia, [której pakiety są buforowane](set-defaults-for-enterprise-deployments.md?view=vs-2019) lub [tego, czy pakiety są buforowane](disable-or-move-the-package-cache.md?view=vs-2017).

* (Opcjonalnie) Ustawianie zasad grupy. Możesz również [Konfigurowanie programu Visual Studio, aby wyłączyć opinie](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy"></a>Krok 3 — wdrażanie

* Użyj wybranej technologii wdrażania w celu wykonania skryptu na docelowych stacjach roboczych dla deweloperów.

## <a name="step-4---deploy-updates"></a>Krok 4 — wdrażanie aktualizacji

* [Odśwież lokalizacji sieciowej, z najnowszymi aktualizacjami](update-a-network-installation-of-visual-studio.md?view=vs-2017) do programu Visual Studio za pomocą polecenia używane w kroku 1 w regularnych odstępach czasu, aby dodać zaktualizowane składniki.

  Należy zaktualizować program Visual Studio przy użyciu skryptu aktualizacji. Aby to zrobić, należy użyć [ `update` ](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) parametru wiersza polecenia.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 — (opcjonalnie) za pomocą Visual Studio tools

Mamy kilka narzędzi, które ułatwiają [wykrywania wystąpień i zarządzanie nimi zainstalowanego programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017) na maszynach klienckich.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Instalowanie certyfikatów wymaganych do instalacji w trybie offline programu Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importowanie lub eksportowanie konfiguracji instalacji](import-export-installation-configurations.md)
* [Archiwa Instalatora programu Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Cyklu życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
* [Ustawienia Załaduj synchroniczne](../extensibility/synchronously-autoloaded-extensions.md)
