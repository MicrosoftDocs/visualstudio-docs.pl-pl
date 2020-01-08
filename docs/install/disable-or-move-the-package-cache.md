---
title: Wyłączanie lub przenoszenie pamięci podręcznej pakietów
description: Dowiedz się, jak wyłączyć, włączyć lub Przenieś pamięć podręczną pakietów dla wdrożeń programu Visual Studio.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 276eff442891f70b9eea76e9167b07f798af2d6a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591466"
---
# <a name="disable-or-move-the-package-cache"></a>Wyłączanie lub przenoszenie pamięci podręcznej pakietów

Pamięć podręczną pakietów zapewnia źródło pakietów zainstalowanych, w przypadku, gdy zajdzie potrzeba naprawy programu Visual Studio lub inne powiązane produkty w przypadkach, gdy mają Brak połączenia internetowego. Niemniej jednak w przypadku niektórych dysków lub zestawu systemowego może nie być konieczne zachowywanie wszystkich pakietów.
Instalator pobierze je w razie potrzeby, więc jeśli chcesz zapisać lub odzyskać miejsce na dysku, możesz wyłączyć lub przenieść pamięć podręczną pakietu.

## <a name="disable-the-package-cache"></a>Wyłącz pamięć podręczną pakietów

Przed zainstalowaniem, modyfikowania lub naprawy programu Visual Studio lub innych produktów z nowym Instalatorem można uruchomić Instalatora z `--nocache` przełączyć się do Instalatora.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Wszelkich operacji wykonywanych na dowolny produkt usunie wszystkie istniejące pakiety dla tego produktu i zapobiegnie zapisywania wszelkich pakietów, które po ich zainstalowaniu. Jeśli zmodyfikujesz lub naprawy programu Visual Studio i pakiety są wymagane, ich zostanie pobrana automatycznie i usunięte po ich zainstalowaniu.

Jeśli chcesz ponownie włączyć pamięć podręczną, należy przekazać `--cache` zamiast tego. Tylko wymagane pakiety będą przechowywane w pamięci podręcznej, więc jeśli trzeba przywrócić wszystkie pakiety, należy naprawić program Visual Studio przed rozłączeniem z siecią.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Można również ustawić `KeepDownloadedPayloads` [zasad rejestru](set-defaults-for-enterprise-deployments.md) wyłączenie pamięci podręcznej, zanim instalowania, modyfikowania lub naprawy programu Visual Studio.

## <a name="move-the-package-cache"></a>Przenieś pamięć podręczną pakietów

Typowa konfiguracja systemu jest zapewnienie Windows zainstalowana na dysk SSD o większych dysku twardego (lub więcej) do tworzenia aplikacji musi, takie jak kod źródłowy, pliki binarne programu i nie tylko. Jeśli chcesz, aby działał w trybie offline, możesz zamiast tego przenieść pamięć podręczną pakietu.

Obecnie można to zrobić tylko w przypadku ustawienia [zasad rejestru](set-defaults-for-enterprise-deployments.md) `CachePath` przed instalacją, modyfikacją lub naprawą programu Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Ustawianie wartości domyślnych w przypadku wdrożeń w przedsiębiorstwach](set-defaults-for-enterprise-deployments.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
