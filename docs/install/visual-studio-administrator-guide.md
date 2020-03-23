---
title: Podręcznik administratora programu Visual Studio
titleSuffix: ''
description: Dowiedz się więcej o wdrażaniu programu Visual Studio w środowisku przedsiębiorstwa.
ms.date: 03/09/2020
ms.custom: seodec18
ms.topic: conceptual
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
ms.openlocfilehash: bda9a73a7a1aabb2d288653ff4d7b20b1c40db8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79190275"
---
# <a name="visual-studio-administrator-guide"></a>Podręcznik administratora programu Visual Studio

W środowiskach korporacyjnych administratorzy systemów zazwyczaj wdrażają instalacje dla użytkowników końcowych z udziału sieciowego lub za pomocą oprogramowania do zarządzania systemami. Zaprojektowaliśmy aparat konfiguracji programu Visual Studio w celu obsługi wdrażania w przedsiębiorstwie, dając administratorom systemu możliwość tworzenia lokalizacji instalacji sieciowej, wstępnej konfiguracji ustawień domyślnych instalacji, wdrażania kluczy produktu podczas procesu instalacji oraz , aby zarządzać aktualizacjami produktów po pomyślnym wdrożeniu.

Ten przewodnik dla administratora zawiera wskazówki dotyczące wdrażania w przedsiębiorstwie w środowiskach sieciowych.

## <a name="before-you-begin"></a>Przed rozpoczęciem

Przed wdrożeniem programu Visual Studio w całej organizacji, istnieje kilka decyzji do wykonania i zadań do wykonania:

::: moniker range="vs-2019"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania instalacyjne](/visualstudio/releases/2019/system-requirements/).

* Zdecyduj o swoich potrzebach serwisowych.

  Jeśli twoja firma musi dłużej korzystać z zestawu funkcji, ale nadal chce otrzymywać regularne aktualizacje obsługi, należy zaplanować użycie planu bazowego obsługi. Aby uzyskać więcej informacji, zobacz ***opcje pomocy technicznej dla klientów w przedsiębiorstwach i profesjonalistach*** na stronie [cyklu życia produktu i obsługi programu Visual Studio,](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) a także stronę Jak: Aktualizuj program Visual Studio na stronie [planu bazowego obsługi.](update-servicing-baseline.md)

  Jeśli planujesz zastosować aktualizacje obsługi wraz z zbiorczymi aktualizacjami funkcji, możesz wybrać najnowsze bity.

* Zdecyduj się na model aktualizacji.

  Gdzie chcesz, aby poszczególne komputery klienckie były otrzymywać aktualizacje? W szczególności zdecyduj, czy chcesz otrzymywać aktualizacje z Internetu, czy z udziału lokalnego w całej firmie. Następnie, jeśli zdecydujesz się na użycie udziału lokalnego, zdecyduj, czy poszczególni użytkownicy mogą aktualizować własnych klientów, czy też chcesz, aby administrator programowo aktualizował klientów.

* Zdecyduj, jakich [obciążeń i składników](workload-and-component-ids.md?view=vs-2019) potrzebuje Twoja firma.

* Zdecyduj, czy ma być używany [plik odpowiedzi](automated-installation-with-response-file.md?view=vs-2019) (który upraszcza zarządzanie szczegółami w pliku skryptu).

* Zdecyduj, czy chcesz włączyć zasady grupy i czy chcesz skonfigurować program Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach.

::: moniker-end

::: moniker range="vs-2017"

* Upewnij się, że każdy komputer docelowy spełnia [minimalne wymagania instalacyjne](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Zdecyduj o swoich potrzebach serwisowych.

  Jeśli twoja firma musi dłużej korzystać z zestawu funkcji, ale nadal chce otrzymywać regularne aktualizacje obsługi, należy zaplanować użycie planu bazowego obsługi. Aby uzyskać więcej informacji, zobacz ***pomoc techniczną dla starszych wersji programu Visual Studio*** sekcji [cyklu życia produktu programu Visual Studio i strony obsługi,](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) a także [How to: Update Visual Studio podczas obsługi linii bazowej](update-servicing-baseline.md) strony.

  Jeśli planujesz zastosować aktualizacje obsługi wraz z zbiorczymi aktualizacjami funkcji, możesz wybrać najnowsze bity.

* Zdecyduj się na model aktualizacji.

  Gdzie chcesz, aby poszczególne komputery klienckie były otrzymywać aktualizacje? W szczególności zdecyduj, czy chcesz otrzymywać aktualizacje z Internetu, czy z udziału lokalnego w całej firmie. Następnie, jeśli zdecydujesz się na użycie udziału lokalnego, zdecyduj, czy poszczególni użytkownicy mogą aktualizować własnych klientów, czy też chcesz, aby administrator programowo aktualizował klientów.

* Zdecyduj, jakich [obciążeń i składników](workload-and-component-ids.md?view=vs-2017) potrzebuje Twoja firma.

* Zdecyduj, czy ma być używany [plik odpowiedzi](automated-installation-with-response-file.md?view=vs-2017) (który upraszcza zarządzanie szczegółami w pliku skryptu).

* Zdecyduj, czy chcesz włączyć zasady grupy i czy chcesz skonfigurować program Visual Studio, aby wyłączyć opinie klientów na poszczególnych komputerach.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 - Pobieranie plików produktów programu Visual Studio

* [Wybierz obciążenia i składniki,](workload-and-component-ids.md?view=vs-2019) które chcesz zainstalować.

* [Utwórz udział sieciowy dla plików produktów programu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Krok 2 - Tworzenie skryptu instalacyjnego

* Tworzenie skryptu instalacyjnego, który używa [parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) do sterowania instalacją.

  >[!NOTE]
  > Skrypty można uprościć za pomocą [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2019). Upewnij się, że utworzysz plik odpowiedzi zawierający domyślną opcję instalacji.

* (Opcjonalnie) [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) jako część skryptu instalacyjnego, aby użytkownicy nie musieli aktywować oprogramowania oddzielnie.

* (Opcjonalnie) Zaktualizuj układ sieci, aby [kontrolować, kiedy i z kiedy aktualizacje produktów są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* (Opcjonalnie) Ustaw zasady rejestru, które mają wpływ na wdrażanie programu Visual Studio, na przykład gdzie niektóre pakiety udostępnione innym wersjom lub wystąpieniom są zainstalowane, [gdzie pakiety są buforowane](set-defaults-for-enterprise-deployments.md?view=vs-2019) lub [czy pakiety są buforowane.](disable-or-move-the-package-cache.md?view=vs-2019)

* (Opcjonalnie) Ustaw zasady grupy. Można również [skonfigurować program Visual Studio, aby wyłączyć opinie klientów](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy"></a>Krok 3 - Wdrażanie

* Użyj wybranej technologii wdrażania, aby wykonać skrypt na docelowych stacjach roboczych deweloperów.

## <a name="step-4---deploy-updates"></a>Krok 4 — wdrażanie aktualizacji

* [Odśwież swoją lokalizację sieciową za pomocą najnowszych aktualizacji](update-a-network-installation-of-visual-studio.md?view=vs-2019) programu Visual Studio, uruchamiając regularnie polecenie używane w kroku 1 w celu dodawania zaktualizowanych składników.

  Program Visual Studio można zaktualizować przy użyciu skryptu aktualizacji. Aby to zrobić, [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) należy użyć parametru wiersza polecenia.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 - (Opcjonalnie) Korzystanie z narzędzi programu Visual Studio

Mamy kilka narzędzi dostępnych, aby ułatwić [wykrywanie i zarządzanie zainstalowanymi wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019) na komputerach klienckich.

## <a name="advanced-configuration"></a>Konfiguracja zaawansowana

Domyślnie instalacja programu Visual Studio umożliwia włączenie typu niestandardowego w bing wyszukiwania z listy błędów F1 i łącza kodu. Program Visual Studio można skonfigurować tak, aby wyłączył mechanizm wyszukiwania, dołączając dowolne niestandardowe typy użytkowników, zmieniając wartość następującego klucza rejestru według zasad:

**"PutCustomTypeInBingSearch" DWORD 0**

Rejestr znajduje się w katalogu *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* katalogu gałęzi rejestru prywatnego. Aby uzyskać instrukcje dotyczące otwierania gałęzi rejestru, zobacz [edytowanie rejestru dla wystąpienia programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 - Pobieranie plików produktów programu Visual Studio

* [Wybierz obciążenia i składniki,](workload-and-component-ids.md?view=vs-2017) które chcesz zainstalować.

* [Utwórz udział sieciowy dla plików produktów programu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Krok 2 - Tworzenie skryptu instalacyjnego

* Tworzenie skryptu instalacyjnego, który używa [parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) do sterowania instalacją.

  >[!NOTE]
  > Skrypty można uprościć za pomocą [pliku odpowiedzi](automated-installation-with-response-file.md?view=vs-2017). Upewnij się, że utworzysz plik odpowiedzi zawierający domyślną opcję instalacji.

* (Opcjonalnie) [Zastosuj klucz produktu licencji zbiorczej](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) jako część skryptu instalacyjnego, aby użytkownicy nie musieli aktywować oprogramowania oddzielnie.

* (Opcjonalnie) Zaktualizuj układ sieci, aby [kontrolować, kiedy i z kiedy aktualizacje produktów są dostarczane do użytkowników końcowych](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* (Opcjonalnie) Ustaw zasady rejestru, które mają wpływ na wdrażanie programu Visual Studio, na przykład gdzie niektóre pakiety udostępnione innym wersjom lub wystąpieniom są zainstalowane, [gdzie pakiety są buforowane](set-defaults-for-enterprise-deployments.md?view=vs-2019) lub [czy pakiety są buforowane.](disable-or-move-the-package-cache.md?view=vs-2017)

* (Opcjonalnie) Ustaw zasady grupy. Można również [skonfigurować program Visual Studio, aby wyłączyć opinie klientów](../ide/visual-studio-experience-improvement-program.md) na poszczególnych komputerach.

## <a name="step-3---deploy"></a>Krok 3 - Wdrażanie

* Użyj wybranej technologii wdrażania, aby wykonać skrypt na docelowych stacjach roboczych deweloperów.

## <a name="step-4---deploy-updates"></a>Krok 4 — wdrażanie aktualizacji

* [Odśwież swoją lokalizację sieciową za pomocą najnowszych aktualizacji](update-a-network-installation-of-visual-studio.md?view=vs-2017) programu Visual Studio, uruchamiając regularnie polecenie używane w kroku 1 w celu dodawania zaktualizowanych składników.

  Program Visual Studio można zaktualizować przy użyciu skryptu aktualizacji. Aby to zrobić, [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) należy użyć parametru wiersza polecenia.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 - (Opcjonalnie) Korzystanie z narzędzi programu Visual Studio

Mamy kilka narzędzi dostępnych, aby ułatwić [wykrywanie i zarządzanie zainstalowanymi wystąpieniami programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017) na komputerach klienckich.

## <a name="advanced-configuration"></a>Konfiguracja zaawansowana

Domyślnie instalacja programu Visual Studio umożliwia włączenie typu niestandardowego w bing wyszukiwania z listy błędów F1 i łącza kodu. Program Visual Studio można skonfigurować tak, aby wyłączył mechanizm wyszukiwania, dołączając dowolne niestandardowe typy użytkowników, zmieniając wartość następującego klucza rejestru według zasad:

**"PutCustomTypeInBingSearch" DWORD 0**

Rejestr znajduje się w katalogu *Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\* katalogu gałęzi rejestru prywatnego. Aby uzyskać instrukcje dotyczące otwierania gałęzi rejestru, zobacz [edytowanie rejestru dla wystąpienia programu Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Przykładowe parametry wiersza polecenia](command-line-parameter-examples.md)
* [Instalowanie certyfikatów wymaganych do instalacji programu Visual Studio w trybie offline](install-certificates-for-visual-studio-offline.md)
* [Importowanie lub eksportowanie konfiguracji instalacji](import-export-installation-configurations.md)
* [Archiwum instalacji programu Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Cykl życia produktu i serwis programu Visual Studio](/visualstudio/releases/2019/servicing/)
* [Synchroniczne ustawienia automatycznego ładowania](../extensibility/synchronously-autoloaded-extensions.md)
