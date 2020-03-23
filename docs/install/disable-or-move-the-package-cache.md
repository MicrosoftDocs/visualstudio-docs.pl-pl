---
title: Wyłączanie lub przenoszenie pamięci podręcznej pakietów
description: Dowiedz się, jak wyłączyć, włączyć lub przenieść pamięć podręczną pakietów dla wdrożeń programu Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3f38757931cb22e9072571d96b015f37882dd500
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114790"
---
# <a name="disable-or-move-the-package-cache"></a>Wyłączanie lub przenoszenie pamięci podręcznej pakietów

Pamięć podręczna pakietów udostępnia źródło zainstalowanych pakietów w przypadku konieczności naprawy programu Visual Studio lub innych powiązanych produktów w przypadkach, gdy nie masz połączenia z Internetem. W przypadku niektórych dysków lub skonfigurowanych systemów możesz jednak nie chcieć przechowywać wszystkich tych pakietów.
Instalator pobierze je w razie potrzeby, więc jeśli chcesz zapisać lub odzyskać miejsce na dysku, możesz wyłączyć lub przenieść pamięć podręczną pakietu.

## <a name="disable-the-package-cache"></a>Wyłączanie pamięci podręcznej pakietu

Przed zainstalowaniem, zmodyfikowaniem lub naprawą programu Visual Studio lub innych produktów za `--nocache` pomocą nowego instalatora można uruchomić instalatora za pomocą przełącznika do instalatora.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Każda operacja, którą wykonasz na dowolnym produkcie, usunie istniejące pakiety dla tego produktu i uniknie zapisywania pakietów po ich zainstalowaniu. Jeśli zmodyfikujesz lub naprawisz program Visual Studio i pakiety są wymagane, zostaną one pobrane automatycznie i usunięte po ich zainstalowaniu.

Jeśli chcesz ponownie włączyć pamięć podręczną, przekaż `--cache` zamiast tego. Tylko pakiety, które są wymagane będą buforowane, więc jeśli trzeba przywrócić wszystkie pakiety, należy naprawić visual studio przed odłączeniem od sieci.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Można również ustawić `KeepDownloadedPayloads` [zasady rejestru,](set-defaults-for-enterprise-deployments.md) aby wyłączyć pamięć podręczną przed zainstalowaniem, zmodyfikowaniem lub naprawą programu Visual Studio.

## <a name="move-the-package-cache"></a>Przenoszenie pamięci podręcznej pakietu

Wspólna konfiguracja systemu polega na zainstalowaniu systemu Windows na dysku SSD z większym dyskiem twardym (lub większym) w celu zaspokojenia potrzeb programisty, takich jak kod źródłowy, pliki binarne programu i inne. Jeśli chcesz pracować w trybie offline, możesz przenieść pamięć podręczną pakietu.

Obecnie można to zrobić tylko wtedy, `CachePath` gdy [zasady rejestru](set-defaults-for-enterprise-deployments.md) zostaną ustawione przed zainstalowaniem, zmodyfikowaniem lub naprawą programu Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Ustawianie ustawień domyślnych dla wdrożeń przedsiębiorstw](set-defaults-for-enterprise-deployments.md)
* [Instalowanie programu Visual Studio za pomocą parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md)
