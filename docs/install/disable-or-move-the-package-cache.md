---
title: Wyłączanie lub przenoszenie pamięci podręcznej pakietów
description: Dowiedz się, jak wyłączyć, włączyć lub przenieść pamięć podręczną pakietów Visual Studio wdrożeniach.
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
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0584673880a56bbde0ef44ad14c24acca252c5a2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307482"
---
# <a name="disable-or-move-the-package-cache"></a>Wyłączanie lub przenoszenie pamięci podręcznej pakietów

Pamięć podręczna pakietów udostępnia źródło zainstalowanych pakietów na wypadek, Visual Studio lub innych powiązanych produktów w przypadkach, gdy nie masz połączenia internetowego. Jednak w przypadku niektórych dysków lub zestawów systemowych może nie być konieczne zachowanie wszystkich tych pakietów.
Instalator pobierze je w razie potrzeby, więc jeśli chcesz zapisać lub odzyskać miejsce na dysku, możesz wyłączyć lub przenieść pamięć podręczną pakietu.

## <a name="disable-the-package-cache"></a>Wyłączanie pamięci podręcznej pakietów

Przed zainstalowaniem, zmodyfikowaniem lub naprawą Visual Studio lub innych produktów przy użyciu nowego instalatora możesz uruchomić instalatora, przełączać `--nocache` się na instalator.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Każda operacja w jakikolwiek produkt spowoduje usunięcie wszystkich istniejących pakietów dla tego produktu i zapobiegnie zapisywaniu jakichkolwiek pakietów po ich zainstalowaniu. Jeśli zmodyfikujesz lub naprawisz Visual Studio i pakiety są wymagane, zostaną one pobrane automatycznie i usunięte po zainstalowaniu.

Jeśli chcesz ponownie włączyć pamięć podręczną, zamiast tego `--cache` przekaż. Tylko wymagane pakiety będą buforowane, więc jeśli musisz przywrócić wszystkie pakiety, napraw Visual Studio przed rozłączeniem z siecią.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Można również ustawić zasady rejestru, aby wyłączyć pamięć podręczną przed `KeepDownloadedPayloads` [](set-defaults-for-enterprise-deployments.md) zainstalowaniem, zmodyfikowaniem lub naprawą Visual Studio.

## <a name="move-the-package-cache"></a>Przenoszenie pamięci podręcznej pakietów

Często spotykaną konfiguracją systemu jest zainstalowany system Windows na dysku SSD z większym dyskiem twardym (lub większym) na potrzeby opracowywania, na przykład kodu źródłowego, plików binarnych programu i innych. Jeśli chcesz pracować w trybie offline, możesz zamiast tego przenieść pamięć podręczną pakietów.

Obecnie można to zrobić tylko wtedy, gdy ustawisz zasady rejestru przed `CachePath` [](set-defaults-for-enterprise-deployments.md) zainstalowaniem, zmodyfikowaniem lub naprawą Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Ustawianie wartości domyślnych dla wdrożeń przedsiębiorstwa](set-defaults-for-enterprise-deployments.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
