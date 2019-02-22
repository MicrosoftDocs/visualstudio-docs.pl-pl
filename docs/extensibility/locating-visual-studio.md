---
title: Locating Visual Studio | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c13146d0d48dc176417040bcb756bf8069ad3c3e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683574"
---
# <a name="locate-visual-studio"></a>Locate Visual Studio

Począwszy od programu Visual Studio 2017 można zainstalować wiele wystąpień tej samej wersji lub nawet edition. Jest to przydatne, gdy chcesz wyświetlić podgląd nowych funkcji na komputerze deweloperskim głównej, przy jednoczesnym zachowaniu poprzedniej instalacji. Z powodu tych zmian nie ma jednego środowiska zmiennej i z rejestru wartości używane w celu zlokalizowania wystąpienia. Zamiast tego można użyć [kwerendy COM API](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) można znaleźć wystąpień na podstawie kryteriów, które dotyczą Twojego rozszerzenia.

Jest to szybkie, tylko do odczytu interfejsu API z pakietami NuGet, które są dostępne dla kodu natywnego i zarządzanego.

| Kod | Package |
| ---- | --- |
| Natywne | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Zarządzane | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Znajdź pojedyncze wystąpienie daną ścieżkę lub bieżący proces lub wyliczyć wszystkich wystąpień. Zobacz [nasze przykłady](https://github.com/Microsoft/vs-setup-samples) kompletne przykłady sposobu lokalizowania programu Visual Studio.

## <a name="tools"></a>Narzędzia

Aby znaleźć programu Visual Studio i innych narzędzi w środowiska kompilacji, skrypty programu PowerShell, instalatorów i scenariuszy, istnieje szereg narzędzi typu open source, można użyć bezpośrednio lub Ponowna dystrybucja wraz z własnych skryptów.

| Projekt | Opis |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Natywne pojedynczego pliku lub pliku wykonywalnego, aby zlokalizować wystąpienia, spełniające kryteria, takie jak wersja w wersji wstępnej, jakie produkty są zainstalowane i obciążeń, które są zainstalowane. Obsługuje także wyszukiwanie programu Visual Studio 2010 lub nowszej, jednak mniej informacji jest zwracany, który dla programu Visual Studio 2017 i nowszych. Zobacz [wiki](https://github.com/Microsoft/vswhere/wiki) przykłady. |
| [Polecenia cmdlet VSSetup](https://github.com/Microsoft/vssetup.powershell) | Obsługiwane polecenia cmdlet programu PowerShell 2.0 lub nowszym, które zwracają rozbudowane informacje jako obiekty, można użyć, aby znaleźć wystąpień, w oparciu o takich samych kryteriów jako _vswhere_ i aby odnaleźć właściwości jeszcze więcej o wystąpieniach. Zobacz [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) przykłady. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Automatycznie lokalizuje _Instalator VSIX_ i przekazuje od wiersza polecenia do zainstalowania **.vsix* pliku. Ta funkcja może być przydatne w pliki instalacyjne, które nie mają bezpośrednią obsługę interfejsami API zapytań. Zobacz [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) przykłady. |

## <a name="see-also"></a>Zobacz także

* [Zmiany w instalacji programu Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
