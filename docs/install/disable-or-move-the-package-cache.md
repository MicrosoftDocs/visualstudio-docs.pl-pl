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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114790"
---
# <a name="disable-or-move-the-package-cache"></a>Wyłączanie lub przenoszenie pamięci podręcznej pakietów

Pamięć podręczna pakietu zapewnia Źródło zainstalowanych pakietów, jeśli trzeba naprawić program Visual Studio lub inne powiązane produkty w przypadkach, gdy nie masz połączenia z Internetem. Niemniej jednak w przypadku niektórych dysków lub zestawu systemowego może nie być konieczne zachowywanie wszystkich pakietów.
Instalator pobierze je w razie potrzeby, więc jeśli chcesz zapisać lub odzyskać miejsce na dysku, możesz wyłączyć lub przenieść pamięć podręczną pakietu.

## <a name="disable-the-package-cache"></a>Wyłącz pamięć podręczną pakietu

Przed zainstalowaniem, modyfikowaniem lub naprawianiem programu Visual Studio lub innych produktów z nowym instalatorem można uruchomić Instalatora, `--nocache` przełączając się do Instalatora.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Każda operacja na dowolnym produkcie spowoduje usunięcie wszelkich istniejących pakietów dla tego produktu i uniemożliwi zapisanie wszystkich pakietów po ich zainstalowaniu. Jeśli zmodyfikujesz lub naprawisz program Visual Studio, a pakiety są wymagane, zostaną pobrane automatycznie i usunięte po zainstalowaniu.

Jeśli chcesz ponownie włączyć pamięć podręczną, przekaż ją `--cache` . Tylko wymagane pakiety będą przechowywane w pamięci podręcznej, więc jeśli trzeba przywrócić wszystkie pakiety, należy naprawić program Visual Studio przed rozłączeniem z siecią.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Można również ustawić `KeepDownloadedPayloads` [zasady rejestru](set-defaults-for-enterprise-deployments.md) , aby wyłączyć pamięć podręczną przed instalacją, modyfikacją lub naprawianiem programu Visual Studio.

## <a name="move-the-package-cache"></a>Przenoszenie pamięci podręcznej pakietów

Wspólna konfiguracja systemu polega na tym, że system Windows jest zainstalowany na dysku SSD z większym dyskiem twardym (lub więcej) na potrzeby programowania, takich jak kod źródłowy, pliki binarne programu i inne. Jeśli chcesz, aby działał w trybie offline, możesz zamiast tego przenieść pamięć podręczną pakietu.

Obecnie można to zrobić tylko w przypadku ustawienia `CachePath` [zasad rejestru](set-defaults-for-enterprise-deployments.md) przed instalacją, modyfikacją lub naprawą programu Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Ustawianie wartości domyślnych dla wdrożeń w przedsiębiorstwie](set-defaults-for-enterprise-deployments.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
