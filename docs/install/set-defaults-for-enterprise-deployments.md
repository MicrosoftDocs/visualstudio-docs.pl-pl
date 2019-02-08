---
title: Ustawianie wartości domyślnych w przypadku wdrożeń w przedsiębiorstwach
description: Dowiedz się więcej o zasadach domeny i inne operacje konfiguracji dla wdrożeń programu Visual Studio w przedsiębiorstwie.
ms.date: 05/05/2017
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
ms.openlocfilehash: f523aaa61e1908d0e947de4cf555ec95ad2d4306
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910821"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio-2017"></a>Ustawianie wartości domyślnych dla wdrożeń w przedsiębiorstwie programu Visual Studio 2017

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
| `CachePath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Katalog, w której pakiet manifesty i, opcjonalnie, ładunki są przechowywane. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Zachowaj ładunków pakietu, nawet w przypadku, po ich zainstalowaniu. Możesz zmienić wartość dowolnym czasie. Wyłączanie zasad usuwa wszelkie ładunków pamięci podręcznej pakietu dla wystąpienia, napraw lub zmodyfikować. Przeczytaj, jak do [wyłączone lub przenoszenie pamięci podręcznej pakietu](disable-or-move-the-package-cache.md) Aby uzyskać więcej informacji. |
| `SharedInstallationPath` | `REG_SZ` lub `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Katalog, w którym są zainstalowane niektórych pakietów współużytkowane przez wersje wystąpienia programu Visual Studio. Zmień wartość w dowolnym momencie, ale który mają wpływ tylko na przyszłe instalacji. Nie należy przenieść wszystkie produkty zainstalowane do poprzedniej lokalizacji lub mogą nie działać poprawnie. |

> [!IMPORTANT]
> Jeśli zmienisz `CachePath` zasad rejestru po dowolnej instalacji, należy przenieść istniejący pakiet do nowej lokalizacji w pamięci podręcznej i upewnić się, że jest zabezpieczony tak, aby `SYSTEM` i `Administrators` mają pełną kontrolę i `Everyone` ma dostęp do odczytu.
> Nie można przenieść istniejące pamięci podręcznej lub ich zabezpieczaniem go może spowodować problemy z instalacji w przyszłości.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

 * [Instalowanie programu Visual Studio](install-visual-studio.md)
 * [Wyłączanie lub przenoszenie pamięci podręcznej pakietów](disable-or-move-the-package-cache.md)
 * [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
