---
title: Ustawianie wartości domyślnych dla wdrożeń przedsiębiorstwa
description: Dowiedz się więcej o zasadach domeny i innych operacjach konfiguracji dla wdrożeń usługi Visual Studio.
ms.date: 04/13/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: b32c56e418631bfc8f5435d0eb113c9da2296ae9
ms.sourcegitcommit: 3985d0ae8d6332f4682c82a10897763173d52961
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2021
ms.locfileid: "107386011"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Ustawianie wartości domyślnych dla wdrożeń programu Visual Studio w przedsiębiorstwie

Można ustawić zasady rejestru, które mają wpływ na wdrażanie Visual Studio. Te zasady są globalne dla maszyny i mają wpływ na:

- Miejsce, w którym instalowane są niektóre pakiety udostępniane innym wersjiom lub wystąpieniom
- Gdzie i czy pakiety są buforowane
- Jak należy stosować aktualizacje administratora

Niektóre z tych zasad można ustawić przy użyciu opcji wiersza [polecenia,](use-command-line-parameters-to-install-visual-studio.md)ustawić wartości rejestru na maszynie, a nawet dystrybuować je przy użyciu zasady grupy w całej organizacji.

## <a name="registry-keys"></a>Klucze rejestru

Istnieje kilka lokalizacji, w których można ustawić wartości domyślne przedsiębiorstwa, aby umożliwić kontrolę za pośrednictwem zasady grupy lub bezpośrednio w rejestrze. Visual Studio sekwencyjnie, aby sprawdzić, czy ustawiono jakiekolwiek zasady przedsiębiorstwa; Gdy tylko wartość zasad zostanie odnaleziona w poniższej kolejności, pozostałe klucze zostaną zignorowane.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (w 64-bitowych systemach operacyjnych)

Niektóre wartości rejestru są ustawiane automatycznie przy pierwszym ich używać, jeśli nie zostały jeszcze ustawione. Dzięki temu kolejne instalacje będą używać tych samych wartości. Te wartości są przechowywane w drugim kluczu rejestru, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` .

Można ustawić następujące wartości rejestru:

::: moniker range="vs-2017"
| **Nazwa** | **Typ** | **Domyślny** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym są przechowywane manifesty pakietu i, opcjonalnie, ładunki. Aby uzyskać więcej informacji, zobacz [Wyłączanie lub przenoszenie strony pamięci podręcznej](disable-or-move-the-package-cache.md) pakietu. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachowaj ładunki pakietów nawet po ich zainstalowaniu. Wartość można zmienić w dowolnym momencie. Wyłączenie zasad powoduje usunięcie wszystkich buforowanych ładunków pakietów dla wystąpienia, które naprawiasz lub modyfikujesz. Aby uzyskać więcej informacji, zobacz [Wyłączanie lub przenoszenie strony pamięci podręcznej](disable-or-move-the-package-cache.md) pakietu. |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Katalog, w którym niektóre pakiety współużytkują różne wersje wystąpień Visual Studio są instalowane. Wartość można zmienić w dowolnym momencie, ale będzie ona mieć wpływ tylko na przyszłe instalacje. Nie można przenosić żadnych produktów zainstalowanych już w starej lokalizacji lub mogą one nie działać poprawnie. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 0 | Uniemożliwiaj instalatorowi automatyczne pobieranie aktualizacji dla wszystkich zainstalowanych Visual Studio produktów. Wartość można zmienić w dowolnym momencie. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 0 | Umożliwia zastosowanie aktualizacji administratora na komputerze klienckim. Jeśli brakuje tej wartości lub ustawiono wartość 0, aktualizacje administratora zostaną zablokowane. Ta wartość jest do użytku administracyjnego. Aby uzyskać więcej informacji, zobacz [Włączanie aktualizacji administratora](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 0 | Wskazuje, że użytkownik nie chce otrzymywać aktualizacji administratora Visual Studio. Brak wartości rejestru lub ustawiona wartość 0 oznacza, że użytkownik Visual Studio chce otrzymywać aktualizacje administratora Visual Studio. Dotyczy to użytkownika dewelopera (jeśli ma uprawnienia administratora na komputerze klienckim). Aby uzyskać więcej informacji, zobacz [Stosowanie aktualizacji administratora](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Ścieżka pliku do konfigurowania aktualizacji administracyjnych. Aby uzyskać więcej informacji, zobacz [Metody konfigurowania aktualizacji administratora](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
::: moniker-end

::: moniker range="vs-2019"
| **Nazwa** | **Typ** | **Domyślny** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym są przechowywane manifesty pakietu i, opcjonalnie, ładunki. Aby uzyskać więcej informacji, zobacz [Wyłączanie lub przenoszenie strony pamięci podręcznej](disable-or-move-the-package-cache.md) pakietu. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachowaj ładunki pakietów nawet po ich zainstalowaniu. Wartość można zmienić w dowolnym momencie. Wyłączenie zasad powoduje usunięcie wszystkich buforowanych ładunków pakietów dla wystąpienia, które naprawiasz lub modyfikujesz. Aby uzyskać więcej informacji, zobacz [Wyłączanie lub przenoszenie strony pamięci podręcznej](disable-or-move-the-package-cache.md) pakietu. |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Katalog, w którym instalowane są niektóre pakiety współdzielone przez Visual Studio wystąpień programu . Wartość można zmienić w dowolnym momencie, ale będzie ona mieć wpływ tylko na przyszłe instalacje. Nie można przenosić żadnych produktów zainstalowanych już w starej lokalizacji lub mogą one nie działać poprawnie. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 0 | Uniemożliwiaj instalatorowi automatyczne pobieranie aktualizacji dla wszystkich zainstalowanych Visual Studio produktów. Wartość można zmienić w dowolnym momencie. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 0 | Umożliwia zastosowanie aktualizacji administratora na komputerze klienckim. Jeśli brakuje tej wartości lub ustawiono wartość 0, aktualizacje administratora będą blokowane. Ta wartość jest do użytku administracyjnego. Aby uzyskać więcej informacji, zobacz [Włączanie aktualizacji administratora](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 0 | Wskazuje, że użytkownik nie chce otrzymywać aktualizacji administratora dla Visual Studio. Brak wartości rejestru lub ustawiona wartość 0 oznacza, że użytkownik Visual Studio chce otrzymywać aktualizacje administratora dla Visual Studio. Dotyczy to użytkownika dewelopera (jeśli ma uprawnienia administratora na komputerze klienckim). Aby uzyskać więcej informacji, zobacz [Stosowanie aktualizacji administratora](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\updates.config | Ścieżka pliku do konfigurowania aktualizacji administracyjnych. Aby uzyskać więcej informacji, zobacz [Metody konfigurowania aktualizacji administratora](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
| `BaselineStickinessVersions2019` | `REG_SZ` lub `REG_EXPAND_SZ` | `16.7.0` | Pomocnicza wersja planu bazowego obsługi, w przypadku których klient powinien pozostać. Aby uzyskać więcej informacji, zobacz [stronę Stosowanie aktualizacji administratora.](../install/applying-administrator-updates.md#understanding-configuration-options) | 
::: moniker-end

> [!IMPORTANT]
> Jeśli zmienisz zasady rejestru po każdej instalacji, musisz przenieść istniejącą pamięć podręczną pakietów do nowej lokalizacji i upewnić się, że jest ona zabezpieczona tak, aby mieć pełną kontrolę i mieć dostęp do `CachePath` `SYSTEM` `Administrators` `Everyone` odczytu.
> Nieudane przeniesienie istniejącej pamięci podręcznej lub zabezpieczenie jej może spowodować problemy z przyszłymi instalacjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](install-visual-studio.md)
- [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
- [Stosowanie aktualizacji administratora](applying-administrator-updates.md)
- [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
