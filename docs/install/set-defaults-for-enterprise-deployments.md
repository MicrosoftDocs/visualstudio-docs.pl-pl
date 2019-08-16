---
title: Ustawianie wartości domyślnych w przypadku wdrożeń w przedsiębiorstwach
description: Dowiedz się więcej o zasadach domeny i inne operacje konfiguracji dla wdrożeń programu Visual Studio w przedsiębiorstwie.
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
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f1ddb1f1d39255c14e03d114891145c8f2dece5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551188"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Ustawianie wartości domyślnych dla wdrożeń programu Visual Studio w przedsiębiorstwie

Można ustawić zasady rejestru, które wpływają na wdrażanie programu Visual Studio. Te zasady są globalne dla nowego Instalatora i wpływać na:

- Gdzie instalowane są niektóre pakiety współużytkowane z innymi wersjami lub wystąpień
- Gdy pakiety są buforowane.
- Czy wszystkie pakiety są buforowane

Możesz ustawić niektóre z tych zasad za pomocą [opcje wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md), ustawić wartości rejestru na komputerze lub nawet rozpowszechniaj je za pomocą zasad grupy w całej organizacji.

## <a name="registry-keys"></a>Klucze rejestru

Istnieje kilka lokalizacji, w którym można ustawić domyślne enterprise, aby umożliwić ich sterowania za pomocą zasad grupy lub bezpośrednio w rejestrze. Visual Studio sprawdza kolejno jeśli zostały ustawione żadnymi zasadami przedsiębiorstwa; jak najszybciej po odnalezieniu wartość zasad poniżej kolejności pozostałe klucze są ignorowane.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (na 64-bitowych systemach operacyjnych)

> [!IMPORTANT]
> Jeśli nie ustawisz `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` kluczy i zamiast tego ustawić jedną z innych kluczy, należy skonfigurować zarówno innych kluczy na 64-bitowych systemach operacyjnych. Ten problem został rozwiązany w przyszłej aktualizacji.

Niektóre wartości rejestru są ustawiane automatycznie po raz pierwszy one są używane, jeśli nie już skonfigurowane. Daje to gwarancję, że kolejne instaluje używać tych samych wartości. Te wartości są przechowywane w kluczu rejestru drugi `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Można ustawić następujące wartości rejestru:

| **Nazwa** | **Typ** | **Default** | **Opis** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w której pakiet manifesty i, opcjonalnie, ładunki są przechowywane. Aby uzyskać więcej informacji, zobacz stronę [wyłączanie lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachowaj ładunków pakietu, nawet w przypadku, po ich zainstalowaniu. Możesz zmienić wartość dowolnym czasie. Wyłączanie zasad usuwa wszelkie ładunków pamięci podręcznej pakietu dla wystąpienia, napraw lub zmodyfikować. Aby uzyskać więcej informacji, zobacz stronę [wyłączanie lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) . |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Katalog, w którym są zainstalowane niektórych pakietów współużytkowane przez wersje wystąpienia programu Visual Studio. Wartość można zmienić w dowolnym momencie, ale będzie to miało wpływ tylko na przyszłe instalacje. Wszelkie produkty już zainstalowane w starej lokalizacji nie mogą być przenoszone lub mogą nie działać prawidłowo. |
| `BackgroundDownloadDisabled` |`REG_DWORD` | 1 | Zapobiegaj automatycznym pobieraniu aktualizacji przez Instalatora dla wszystkich zainstalowanych produktów programu Visual Studio. Możesz zmienić wartość dowolnym czasie. |

> [!IMPORTANT]
> W `CachePath` przypadku zmiany zasad rejestru po dowolnych instalacjach należy przenieść istniejącą pamięć podręczną pakietu do nowej lokalizacji i upewnić się, że jest zabezpieczona `SYSTEM` , `Administrators` tak aby miała pełną kontrolę `Everyone` i ma dostęp do odczytu.
> Niepowodzenie przenoszenia istniejącej pamięci podręcznej lub jej zabezpieczenia może spowodować problemy z przyszłymi instalacjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

- [Instalowanie programu Visual Studio](install-visual-studio.md)
- [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
- [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
