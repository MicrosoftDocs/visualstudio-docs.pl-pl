---
title: Ustawianie ustawień domyślnych dla wdrożeń przedsiębiorstw
description: Dowiedz się więcej o zasadach domeny i innych operacjach konfiguracji dla wdrożeń programu Visual Studio w przedsiębiorstwie.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114283"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Ustawianie wartości domyślnych dla wdrożeń programu Visual Studio w przedsiębiorstwie

Można ustawić zasady rejestru, które mają wpływ na wdrożenie programu Visual Studio. Te zasady mają charakter globalny dla nowego instalatora i mają wpływ na:

- Gdzie niektóre pakiety udostępnione innym wersjom lub wystąpieniom są zainstalowane
- Gdzie pakiety są buforowane
- Czy wszystkie pakiety są buforowane

Niektóre z tych zasad można ustawić za pomocą [opcji wiersza polecenia,](use-command-line-parameters-to-install-visual-studio.md)ustawić wartości rejestru na komputerze, a nawet rozpowszechniać je przy użyciu zasad grupy w całej organizacji.

## <a name="registry-keys"></a>Klucze rejestru

Istnieje kilka lokalizacji, w których można ustawić domyślne ustawienia przedsiębiorstwa, aby włączyć ich kontrolę za pośrednictwem zasad grupy lub bezpośrednio w rejestrze. Visual Studio wygląda sekwencyjnie, aby sprawdzić, czy zostały ustawione zasady przedsiębiorstwa; jak tylko wartość zasad zostanie wykryta w poniższej kolejności, pozostałe klucze są ignorowane.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup`(w 64-bitowych systemach operacyjnych)

> [!IMPORTANT]
> Jeśli nie ustawisz klucza `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` i zamiast tego ustawisz jeden z innych kluczy, należy ustawić oba inne klucze w 64-bitowych systemach operacyjnych. Ten problem został rozwiązany w przyszłej aktualizacji produktu.

Niektóre wartości rejestru są ustawiane automatycznie przy pierwszym użyciu, jeśli nie są już ustawione. Ta praktyka gwarantuje, że kolejne instalacje używają tych samych wartości. Wartości te są przechowywane w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`drugim kluczu rejestru, .

Można ustawić następujące wartości rejestru:

| **Nazwa** | **Typ** | **Domyślny** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w którym są przechowywane manifesty pakietu i opcjonalnie ładunki. Aby uzyskać więcej informacji, zobacz [wyłączanie lub przenoszenie pamięci podręcznej pakietu.](disable-or-move-the-package-cache.md) |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachowaj ładunki pakietów nawet po ich zainstalowaniu. Wartość można zmienić w dowolnym momencie. Wyłączenie zasad usuwa wszystkie ładunki buforowanego pakietu dla wystąpienia, które naprawiasz lub modyfikujesz. Aby uzyskać więcej informacji, zobacz [wyłączanie lub przenoszenie pamięci podręcznej pakietu.](disable-or-move-the-package-cache.md) |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Udostępnione | Katalog, w którym są instalowane niektóre pakiety współużytkowane przez wersje wystąpień programu Visual Studio. Wartość można zmienić w dowolnym momencie, ale będzie miała wpływ tylko na przyszłe instalacje. Nie wolno przenosić żadnych produktów już zainstalowanych w starej lokalizacji lub mogą one nie działać poprawnie. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Uniemożliwić instalatorowi automatyczne pobieranie aktualizacji dla wszystkich zainstalowanych produktów programu Visual Studio. Wartość można zmienić w dowolnym momencie. |

> [!IMPORTANT]
> Jeśli zmienisz `CachePath` zasady rejestru po każdej instalacji, należy przenieść istniejącą pamięć podręczną pakietu `SYSTEM` `Administrators` do nowej lokalizacji `Everyone` i upewnij się, że jest zabezpieczony tak, że i pełna kontrola i który ma dostęp do odczytu.
> Nieprzeprowadzenie istniejącej pamięci podręcznej lub jej zabezpieczenie może spowodować problemy z przyszłymi instalacjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

- [Instalacja programu Visual Studio](install-visual-studio.md)
- [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
- [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
