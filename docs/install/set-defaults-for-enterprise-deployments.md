---
title: Ustawianie wartości domyślnych dla wdrożeń w przedsiębiorstwie
description: Dowiedz się więcej na temat zasad domeny i innych operacji konfiguracji dla wdrożeń w przedsiębiorstwie programu Visual Studio.
ms.date: 03/30/2019
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
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d03912eecd7b3cfa3563fc095453fee3ddf9b163
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114283"
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

| **Nazwa** | **Typ** | **Wartooć** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym są przechowywane manifesty pakietów i, opcjonalnie, ładunki. Aby uzyskać więcej informacji, zobacz stronę [wyłączanie lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Przechowuj ładunki pakietów nawet po ich zainstalowaniu. Wartość można zmienić w dowolnym momencie. Wyłączenie zasad usuwa wszystkie buforowane ładunki pakietów dla wystąpienia, które należy naprawić lub zmodyfikować. Aby uzyskać więcej informacji, zobacz stronę [wyłączanie lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared | Katalog, w którym są zainstalowane pewne pakiety udostępniane między wersjami wystąpień programu Visual Studio. Wartość można zmienić w dowolnym momencie, ale będzie to miało wpływ tylko na przyszłe instalacje. Wszelkie produkty już zainstalowane w starej lokalizacji nie mogą być przenoszone lub mogą nie działać prawidłowo. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Zapobiegaj automatycznym pobieraniu aktualizacji przez Instalatora dla wszystkich zainstalowanych produktów programu Visual Studio. Wartość można zmienić w dowolnym momencie. |

> [!IMPORTANT]
> W przypadku zmiany `CachePath` zasad rejestru po dowolnych instalacjach należy przenieść istniejącą pamięć podręczną pakietu do nowej lokalizacji i upewnić się, że jest zabezpieczona, tak aby `SYSTEM` `Administrators` miała pełną kontrolę i `Everyone` ma dostęp do odczytu.
> Niepowodzenie przenoszenia istniejącej pamięci podręcznej lub jej zabezpieczenia może spowodować problemy z przyszłymi instalacjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu Visual Studio](install-visual-studio.md)
- [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
