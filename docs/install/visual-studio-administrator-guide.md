---
title: Podręcznik administratora programu Visual Studio
titleSuffix: ''
description: Dowiedz się więcej o sposobie wdrażania programu Visual Studio w środowisku przedsiębiorstwa.
ms.date: 07/29/2020
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7687aea6cd7bd1f4a71723c0eadfe36743ca8f71
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211355"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio

W środowiskach korporacyjnych Administratorzy systemu zwykle wdrażają instalacje do użytkowników końcowych z udziału sieciowego lub oprogramowania do zarządzania systemami. Aparat instalacyjny programu Visual Studio został zaprojektowany w celu obsługi wdrażania w przedsiębiorstwie, umożliwiając administratorom systemu Tworzenie lokalizacji instalacji sieciowej, wstępne skonfigurowanie ustawień domyślnych instalacji, wdrożenie kluczy produktu podczas procesu instalacji oraz zarządzanie aktualizacjami produktów po pomyślnym wdrożeniu.

Ten przewodnik administratora zawiera wskazówki dotyczące scenariusza wdrożenia przedsiębiorstwa w środowiskach sieciowych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed wdrożeniem programu Visual Studio w całej organizacji należy wykonać kilka decyzji i wykonać zadania:

::: moniker range="vs-2019"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](/visualstudio/releases/2019/system-requirements/).

* Zdecyduj na potrzeby obsługi.

  Jeśli firma musi pozostać w zestawie funkcji dłużej, ale nadal chce uzyskać regularne aktualizacje obsługi, należy zaplanować użycie podstawy obsługi. Aby uzyskać więcej informacji, zobacz sekcję ***Opcje pomocy technicznej dla klientów w wersji Enterprise i Professional*** na stronie [cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) , a także [Aktualizowanie programu Visual Studio na stronie odniesienia obsługi](update-servicing-baseline.md) .

  Jeśli planujesz zastosować aktualizacje obsługi razem z aktualizacjami funkcji zbiorczych, możesz wybrać najnowsze bity.

* Wybierz model aktualizacji.

  Gdzie poszczególne komputery klienckie mają pobierać aktualizacje? W celu zadecydowania, czy chcesz otrzymywać aktualizacje z Internetu, czy z udziału lokalnego w całej firmie. Następnie, jeśli zdecydujesz się użyć udziału lokalnego, zdecyduj, czy indywidualni użytkownicy mogą zaktualizować swoich klientów, czy chcesz programowo aktualizować klientów.

  Istnieje możliwość aktualizowania układu instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktu, dzięki czemu można go użyć jako punktu instalacji najnowszej aktualizacji programu Visual Studio, a także w celu utrzymania instalacji, które są już wdrożone na stacjach roboczych klienta. Aby uzyskać więcej informacji, zobacz temat [Aktualizowanie instalacji sieciowej programu Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  W przypadku komputerów, które nie są połączone z Internetem, tworzenie minimalnego układu jest najłatwiejszym i najszybszym sposobem na aktualizację wystąpień programu Visual Studio w trybie offline. Aby uzyskać więcej informacji, zobacz [Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline](update-minimal-layout.md).

* Decydowanie o [obciążeniach i składnikach](workload-and-component-ids.md?view=vs-2019) potrzebnych przez firmę.

* Zdecyduj, czy chcesz użyć [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019) (który upraszcza zarządzanie szczegółami w pliku skryptu).

* Zdecyduj, czy chcesz włączyć zasady grupy, a jeśli chcesz skonfigurować program Visual Studio do wyłączania opinii klientów na poszczególnych komputerach.

::: moniker-end

::: moniker range="vs-2017"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania dotyczące instalacji](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Zdecyduj na potrzeby obsługi.

  Jeśli firma musi pozostać w zestawie funkcji dłużej, ale nadal chce uzyskać regularne aktualizacje obsługi, należy zaplanować użycie podstawy obsługi. Aby uzyskać więcej informacji, zobacz sekcję ***Obsługa starszych wersji programu Visual Studio*** na stronie [cykl życia produktu Visual Studio, a](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) także [Aktualizowanie programu Visual Studio na stronie odniesienia obsługi](update-servicing-baseline.md) .

  Jeśli planujesz zastosować aktualizacje obsługi razem z aktualizacjami funkcji zbiorczych, możesz wybrać najnowsze bity.

* Wybierz model aktualizacji.

  Gdzie poszczególne komputery klienckie mają pobierać aktualizacje? W celu zadecydowania, czy chcesz otrzymywać aktualizacje z Internetu, czy z udziału lokalnego w całej firmie. Następnie, jeśli zdecydujesz się użyć udziału lokalnego, zdecyduj, czy indywidualni użytkownicy mogą zaktualizować swoich klientów, czy chcesz programowo aktualizować klientów.

  Istnieje możliwość aktualizowania układu instalacji sieciowej programu Visual Studio przy użyciu najnowszych aktualizacji produktu, dzięki czemu można go użyć jako punktu instalacji najnowszej aktualizacji programu Visual Studio, a także w celu utrzymania instalacji, które są już wdrożone na stacjach roboczych klienta. Aby uzyskać więcej informacji, zobacz temat [Aktualizowanie instalacji sieciowej programu Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  W przypadku komputerów, które nie są połączone z Internetem, tworzenie minimalnego układu jest najłatwiejszym i najszybszym sposobem na aktualizację wystąpień programu Visual Studio w trybie offline. Aby uzyskać więcej informacji, zobacz [Aktualizowanie programu Visual Studio przy użyciu minimalnego układu offline](update-minimal-layout.md).

* Decydowanie o [obciążeniach i składnikach](workload-and-component-ids.md?view=vs-2017&preserve-view=true) potrzebnych przez firmę.

* Zdecyduj, czy chcesz użyć [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (który upraszcza zarządzanie szczegółami w pliku skryptu).

* Zdecyduj, czy chcesz włączyć zasady grupy, a jeśli chcesz skonfigurować program Visual Studio do wyłączania opinii klientów na poszczególnych komputerach.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1. Pobieranie plików produktu Visual Studio

* [Wybierz obciążenia i składniki](workload-and-component-ids.md?view=vs-2019) , które chcesz zainstalować.

* [Utwórz udział sieciowy dla plików produktu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Krok 2. Kompilowanie skryptu instalacji

* Utwórz skrypt instalacyjny, który używa [parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) do kontrolowania instalacji.

  >[!NOTE]
  > Skrypty można uprościć przy użyciu [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019). Upewnij się, że utworzono plik odpowiedzi zawierający domyślną opcję instalacji.

* Obowiązkowe [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) w ramach skryptu instalacji, aby użytkownicy nie musieli osobno aktywować oprogramowania.

* Obowiązkowe Zaktualizuj układ sieci, aby [kontrolować czas i miejsce, w którym aktualizacje produktu są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* Obowiązkowe Ustaw zasady rejestru mające wpływ na wdrożenie programu Visual Studio, takie jak miejsce, w którym są zainstalowane pewne pakiety, które są udostępniane z innymi wersjami lub wystąpieniami, w [których są buforowane pakiety](set-defaults-for-enterprise-deployments.md?view=vs-2019) lub [czy pakiety są buforowane](disable-or-move-the-package-cache.md?view=vs-2019).

* Obowiązkowe Ustaw zasady grupy. Możesz również [skonfigurować program Visual Studio, aby wyłączyć Opinie klientów](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy"></a>Krok 3. wdrażanie

* Użyj wybranej technologii wdrażania, aby wykonać swój skrypt na docelowych stacjach roboczych deweloperów.

## <a name="step-4---deploy-updates"></a>Krok 4 — wdrażanie aktualizacji

* [Odśwież lokalizację sieciową przy użyciu najnowszych aktualizacji](update-a-network-installation-of-visual-studio.md?view=vs-2019) programu Visual Studio, uruchamiając polecenie użyte w kroku 1 w regularnych odstępach czasu w celu dodania zaktualizowanych składników.

  Program Visual Studio można zaktualizować za pomocą skryptu aktualizacji. Aby to zrobić, użyj [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) parametru wiersza polecenia.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 — (opcjonalnie) korzystanie z narzędzi Visual Studio Tools

Dostępne są kilka narzędzi, które ułatwiają [wykrywanie zainstalowanych wystąpień programu Visual Studio i zarządzanie nimi](tools-for-managing-visual-studio-instances.md?view=vs-2019) na komputerach klienckich.

## <a name="advanced-configuration"></a>Konfiguracja zaawansowana

Domyślnie instalacja programu Visual Studio umożliwia dołączanie typów niestandardowych do wyszukiwania w usłudze Bing z listy błędów F1 i kodu. Można skonfigurować program Visual Studio, aby wyłączyć mechanizm wyszukiwania z uwzględnieniem dowolnych niestandardowych typów użytkowników, zmieniając wartość następującego klucza rejestru przez zasady:

**"PutCustomTypeInBingSearch" DWORD 0**

Rejestr znajduje się w katalogu * Software\Microsoft\VisualStudio\16.0_ {InstanceId} \ Roslyn\Internal\Diagnostics \* gałęzi rejestru prywatnego. Aby uzyskać instrukcje dotyczące sposobu otwierania gałęzi rejestru, zobacz [Edytowanie rejestru dla wystąpienia programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1. Pobieranie plików produktu Visual Studio

* [Wybierz obciążenia i składniki](workload-and-component-ids.md?view=vs-2017&preserve-view=true) , które chcesz zainstalować.

* [Utwórz udział sieciowy dla plików produktu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Krok 2. Kompilowanie skryptu instalacji

* Utwórz skrypt instalacyjny, który używa [parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) do kontrolowania instalacji.

  >[!NOTE]
  > Skrypty można uprościć przy użyciu [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Upewnij się, że utworzono plik odpowiedzi zawierający domyślną opcję instalacji.

* Obowiązkowe [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) w ramach skryptu instalacji, aby użytkownicy nie musieli osobno aktywować oprogramowania.

* Obowiązkowe Zaktualizuj układ sieci, aby [kontrolować czas i miejsce, w którym aktualizacje produktu są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* Obowiązkowe Ustaw zasady rejestru mające wpływ na wdrożenie programu Visual Studio, takie jak miejsce, w którym są zainstalowane pewne pakiety, które są udostępniane z innymi wersjami lub wystąpieniami, w [których są buforowane pakiety](set-defaults-for-enterprise-deployments.md?view=vs-2019) lub [czy pakiety są buforowane](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true).

* Obowiązkowe Ustaw zasady grupy. Możesz również [skonfigurować program Visual Studio, aby wyłączyć Opinie klientów](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy"></a>Krok 3. wdrażanie

* Użyj wybranej technologii wdrażania, aby wykonać swój skrypt na docelowych stacjach roboczych deweloperów.

## <a name="step-4---deploy-updates"></a>Krok 4 — wdrażanie aktualizacji

* [Odśwież lokalizację sieciową przy użyciu najnowszych aktualizacji](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) programu Visual Studio, uruchamiając polecenie użyte w kroku 1 w regularnych odstępach czasu w celu dodania zaktualizowanych składników.

  Program Visual Studio można zaktualizować za pomocą skryptu aktualizacji. Aby to zrobić, użyj [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) parametru wiersza polecenia.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 — (opcjonalnie) korzystanie z narzędzi Visual Studio Tools

Dostępne są kilka narzędzi, które ułatwiają [wykrywanie zainstalowanych wystąpień programu Visual Studio i zarządzanie nimi](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) na komputerach klienckich.

## <a name="advanced-configuration"></a>Konfiguracja zaawansowana

Domyślnie instalacja programu Visual Studio umożliwia dołączanie typów niestandardowych do wyszukiwania w usłudze Bing z listy błędów F1 i kodu. Można skonfigurować program Visual Studio, aby wyłączyć mechanizm wyszukiwania z uwzględnieniem dowolnych niestandardowych typów użytkowników, zmieniając wartość następującego klucza rejestru przez zasady:

**"PutCustomTypeInBingSearch" DWORD 0**

Rejestr znajduje się w katalogu * Software\Microsoft\VisualStudio\15.0_ {InstanceId} \ Roslyn\Internal\Diagnostics \* gałęzi rejestru prywatnego. Aby uzyskać instrukcje dotyczące sposobu otwierania gałęzi rejestru, zobacz [Edytowanie rejestru dla wystąpienia programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Zainstaluj certyfikaty wymagane do instalacji w trybie offline programu Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importowanie lub eksportowanie konfiguracji instalacji](import-export-installation-configurations.md)
* [Archiwa Instalatora programu Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Cykl życia produktu Visual Studio i obsługa](/visualstudio/releases/2019/servicing/)
* [Synchroniczne ustawienia autoładowania](../extensibility/synchronously-autoloaded-extensions.md)
