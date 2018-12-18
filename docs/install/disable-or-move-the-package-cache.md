---
title: Wyłączanie lub przenoszenie pamięci podręcznej pakietów
description: Dowiedz się, jak wyłączyć, włączyć lub Przenieś pamięć podręczną pakietów dla wdrożeń programu Visual Studio.
ms.date: 04/14/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 006e7112a2b6c7b990fb412c6a9a2c458bc9e8b2
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159545"
---
# <a name="disable-or-move-the-package-cache"></a>Wyłączanie lub przenoszenie pamięci podręcznej pakietów

Pamięć podręczną pakietów zapewnia źródło pakietów zainstalowanych, w przypadku, gdy zajdzie potrzeba naprawy programu Visual Studio lub inne powiązane produkty w przypadkach, gdy mają Brak połączenia internetowego. W przypadku niektórych dysków lub system ustawiać ups, jednak może nie chcesz zachować te pakiety wokół.
Instalator pobierze je w razie potrzeby, dlatego jeśli chcesz zapisać lub odzyskać miejsce na dysku zostanie wyłączone lub przenoszenie pamięci podręcznej pakietu.

## <a name="disable-the-package-cache"></a>Wyłącz pamięć podręczną pakietów

Przed zainstalowaniem, modyfikowania lub naprawy programu Visual Studio lub innych produktów z nowym Instalatorem można uruchomić Instalatora z `--nocache` przełączyć się do Instalatora.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Wszelkich operacji wykonywanych na dowolny produkt usunie wszystkie istniejące pakiety dla tego produktu i zapobiegnie zapisywania wszelkich pakietów, które po ich zainstalowaniu. Jeśli zmodyfikujesz lub naprawy programu Visual Studio i pakiety są wymagane, ich zostanie pobrana automatycznie i usunięte po ich zainstalowaniu.

Jeśli chcesz ponownie włączyć pamięć podręczną, należy przekazać `--cache` zamiast tego. Tylko pakiety, które są wymagane będą buforowane, więc należy przywrócić wszystkie pakiety należy naprawić program Visual Studio przed odłączeniem z sieci.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Można również ustawić `KeepDownloadedPayloads` [zasad rejestru](set-defaults-for-enterprise-deployments.md) wyłączenie pamięci podręcznej, zanim instalowania, modyfikowania lub naprawy programu Visual Studio.

## <a name="move-the-package-cache"></a>Przenieś pamięć podręczną pakietów

Typowa konfiguracja systemu jest zapewnienie Windows zainstalowana na dysk SSD o większych dysku twardego (lub więcej) do tworzenia aplikacji musi, takie jak kod źródłowy, pliki binarne programu i nie tylko. Jeśli chcesz pracować w trybie offline zamiast tego można przenieść pamięci podręcznej pakietu.

Obecnie można to zrobić tylko po ustawieniu `CachePath` [zasad rejestru](set-defaults-for-enterprise-deployments.md) przed zainstalowaniem, modyfikowania lub naprawy programu Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Ustawianie wartości domyślnych w przypadku wdrożeń w przedsiębiorstwach](set-defaults-for-enterprise-deployments.md)
* [Korzystanie z parametrów wiersza polecenia do zainstalowania programu Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
