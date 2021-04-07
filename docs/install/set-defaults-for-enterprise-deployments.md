---
title: Ustawianie wartości domyślnych dla wdrożeń w przedsiębiorstwie
description: Dowiedz się więcej na temat zasad domeny i innych operacji konfiguracji dla wdrożeń w przedsiębiorstwie programu Visual Studio.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9d3d6f658e3d24f3c82737c0c457323b9d4eb4b6
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547469"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Ustawianie wartości domyślnych dla wdrożeń programu Visual Studio w przedsiębiorstwie

Można ustawić zasady rejestru mające wpływ na wdrożenie programu Visual Studio. Te zasady są globalne dla nowego Instalatora i mają wpływ na:

- Gdzie są zainstalowane niektóre pakiety udostępniane z innymi wersjami lub wystąpieniami
- Gdzie są buforowane pakiety
- Czy wszystkie pakiety są buforowane

Niektóre z tych zasad można ustawiać przy użyciu [opcji wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md), ustawiać wartości rejestru na komputerze, a nawet rozpowszechniać je przy użyciu zasady grupy w całej organizacji.

## <a name="registry-keys"></a>Klucze rejestru

Istnieje kilka lokalizacji, w których można ustawić wartości domyślne przedsiębiorstwa, aby włączyć ich kontrolę przez zasady grupy lub bezpośrednio w rejestrze. Program Visual Studio sprawdza się sekwencyjnie, aby sprawdzić, czy zostały ustawione jakieś zasady przedsiębiorstwa. gdy tylko zostanie wykryta wartość zasad w poniższej kolejności, pozostałe klucze zostaną zignorowane.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (w 64-bitowych systemach operacyjnych)

> [!IMPORTANT]
> Jeśli nie ustawisz `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` klucza i zamiast tego ustawisz jeden z pozostałych kluczy, należy ustawić obydwa klucze w 64-bitowych systemach operacyjnych. Ten problem został rozwiązany w przyszłej aktualizacji produktu.

Niektóre wartości rejestru są ustawiane automatycznie przy pierwszym użyciu, jeśli nie zostały jeszcze ustawione. Ta metoda zapewnia, że w przypadku kolejnych instalacji są używane te same wartości. Te wartości są przechowywane w drugim kluczu rejestru, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` .

Można ustawić następujące wartości rejestru:

::: moniker range="vs-2017"
| **Nazwa** | **Typ** | **Wartooć** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym są przechowywane manifesty pakietów i, opcjonalnie, ładunki. Aby uzyskać więcej informacji, zobacz temat [wyłączanie lub przenoszenie strony pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Przechowuj ładunki pakietów nawet po ich zainstalowaniu. Wartość można zmienić w dowolnym momencie. Wyłączenie zasad usuwa wszystkie buforowane ładunki pakietów dla wystąpienia, które należy naprawić lub zmodyfikować. Aby uzyskać więcej informacji, zobacz temat [wyłączanie lub przenoszenie strony pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared | Katalog, w którym są zainstalowane pewne pakiety udostępniane między wersjami wystąpień programu Visual Studio. Możesz zmienić wartość w dowolnym momencie, ale będzie to miało wpływ tylko na przyszłe instalacje. Wszelkie produkty już zainstalowane w starej lokalizacji nie mogą być przenoszone lub mogą nie działać prawidłowo. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Zapobiegaj automatycznym pobieraniu aktualizacji przez Instalatora dla wszystkich zainstalowanych produktów programu Visual Studio. Wartość można zmienić w dowolnym momencie. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 1 | Zezwala na stosowanie aktualizacji administratorów do komputera klienckiego. Jeśli ta wartość jest brakująca lub jest ustawiona na 0, aktualizacje administratorów zostaną zablokowane. Ta wartość jest używana do użytku administracyjnego. Aby uzyskać więcej informacji, zobacz [Włączanie aktualizacji administratora](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 1 | Oznacza, że użytkownik nie chce otrzymywać aktualizacji administratorów do programu Visual Studio. Brak wartości rejestru lub ustawiona wartość 0 oznacza, że użytkownik programu Visual Studio chce otrzymywać aktualizacje administratorów do programu Visual Studio. Jest to przeznaczone dla użytkowników deweloperów (jeśli mają uprawnienia administratora na komputerze klienckim). Aby uzyskać więcej informacji, zobacz [stosowanie aktualizacji administratora](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` lub `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | Ścieżka pliku służąca do konfigurowania aktualizacji administracyjnych. Aby uzyskać więcej informacji, zobacz [metody konfigurowania aktualizacji administratora](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
::: moniker-end

::: moniker range="vs-2019"
| **Nazwa** | **Typ** | **Wartooć** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym są przechowywane manifesty pakietów i, opcjonalnie, ładunki. Aby uzyskać więcej informacji, zobacz temat [wyłączanie lub przenoszenie strony pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Przechowuj ładunki pakietów nawet po ich zainstalowaniu. Wartość można zmienić w dowolnym momencie. Wyłączenie zasad usuwa wszystkie buforowane ładunki pakietów dla wystąpienia, które należy naprawić lub zmodyfikować. Aby uzyskać więcej informacji, zobacz temat [wyłączanie lub przenoszenie strony pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared | Katalog, w którym są zainstalowane pewne pakiety udostępniane między wersjami wystąpień programu Visual Studio. Możesz zmienić wartość w dowolnym momencie, ale będzie to miało wpływ tylko na przyszłe instalacje. Wszelkie produkty już zainstalowane w starej lokalizacji nie mogą być przenoszone lub mogą nie działać prawidłowo. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Zapobiegaj automatycznym pobieraniu aktualizacji przez Instalatora dla wszystkich zainstalowanych produktów programu Visual Studio. Wartość można zmienić w dowolnym momencie. |
| `AdministratorUpdatesEnabled` | `REG_DWORD` | 1 | Zezwala na stosowanie aktualizacji administratorów do komputera klienckiego. Jeśli ta wartość jest brakująca lub jest ustawiona na 0, aktualizacje administratorów zostaną zablokowane. Ta wartość jest używana do użytku administracyjnego. Aby uzyskać więcej informacji, zobacz [Włączanie aktualizacji administratora](enabling-administrator-updates.md). | 
| `AdministratorUpdatesOptOut` | `REG_DWORD` | 1 | Oznacza, że użytkownik nie chce otrzymywać aktualizacji administratorów do programu Visual Studio. Brak wartości rejestru lub ustawiona wartość 0 oznacza, że użytkownik programu Visual Studio chce otrzymywać aktualizacje administratorów do programu Visual Studio. Jest to przeznaczone dla użytkowników deweloperów (jeśli mają uprawnienia administratora na komputerze klienckim). Aby uzyskać więcej informacji, zobacz [stosowanie aktualizacji administratora](../install/applying-administrator-updates.md#understanding-configuration-options). | 
| `UpdateConfigurationFile` | `REG_SZ` lub `REG_EXPAND_SZ` | % ProgramData% \Microsoft\VisualStudio\updates.config | Ścieżka pliku służąca do konfigurowania aktualizacji administracyjnych. Aby uzyskać więcej informacji, zobacz [metody konfigurowania aktualizacji administratora](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update). | 
| `BaselineStickinessVersions2019` | `REG_SZ` lub `REG_EXPAND_SZ` | `ALL` lub `16.4.0,16.7.0,16.9.0` | Wersje autoryzują aktualizacje pozostające w określonych punktach odniesienia obsługi. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [stosowania aktualizacji administratora](../install/applying-administrator-updates.md#understanding-configuration-options) . | 
::: moniker-end

> [!IMPORTANT]
> W przypadku zmiany `CachePath` zasad rejestru po dowolnych instalacjach należy przenieść istniejącą pamięć podręczną pakietu do nowej lokalizacji i upewnić się, że jest zabezpieczona, tak aby `SYSTEM` `Administrators` miała pełną kontrolę i `Everyone` ma dostęp do odczytu.
> Niepowodzenie przenoszenia istniejącej pamięci podręcznej lub jej zabezpieczenia może spowodować problemy z przyszłymi instalacjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](install-visual-studio.md)
- [Podręcznik administratora programu Visual Studio](visual-studio-administrator-guide.md)
- [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
