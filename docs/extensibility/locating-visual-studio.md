---
title: Lokalizowanie Visual Studio | Microsoft Docs
description: Można zainstalować wiele wystąpień tej samej wersji Visual Studio. Dowiedz się, jak za pomocą interfejsu API zapytań COM znaleźć wystąpienie, którego potrzebujesz.
ms.custom: SEO-VS-2020
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: cd0fcd294983d6a6567676f06703b4bd1dd376c4
ms.sourcegitcommit: b4cc3dee59421f7089112becf128a369acadaf61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2021
ms.locfileid: "112990509"
---
# <a name="locate-visual-studio"></a>Znajdowanie programu Visual Studio

Począwszy od Visual Studio 2017 r., można zainstalować wiele wystąpień w tej samej wersji, a nawet wersji. Jest to przydatne, gdy chcesz wyświetlić podgląd nowych funkcji na podstawowej maszynie dewelopera przy zachowaniu poprzedniej instalacji. Z powodu tych zmian nie ma pojedynczej zmiennej środowiskowej ani wartości rejestru, których można użyć do zlokalizowania wystąpienia. Zamiast tego można użyć interfejsu [API zapytań COM do](/dotnet/api/microsoft.visualstudio.setup.configuration) znalezienia wystąpień na podstawie kryteriów odpowiednich dla danego rozszerzenia.

Jest to szybki, tylko do odczytu interfejs API z pakietami NuGet dostępnymi dla kodu natywnego i zarządzanego.

| Kod | Pakiet |
| ---- | --- |
| Natywna | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Zarządzanie | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Możesz zlokalizować pojedyncze wystąpienie na podanej ścieżce lub w bieżącym procesie albo wyliczyć wszystkie wystąpienia. Zobacz [nasze przykłady,](https://github.com/Microsoft/vs-setup-samples) aby uzyskać pełne przykłady lokalizowania Visual Studio.

## <a name="tools"></a>narzędzia

Aby znaleźć Visual Studio i inne narzędzia w środowiskach kompilacji, skryptach programu PowerShell, instalatorach i innych scenariuszach, istnieje wiele narzędzi typu open source, których można używać bezpośrednio lub redystrybuować wraz z własnymi skryptami.

| Projekt | Opis |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Natywny plik wykonywalny z jednym plikiem do lokalizowania wystąpień, które spełniają kryteria, takie jak wersja lub wersja wstępna, jaki produkt jest zainstalowany i które obciążenia są instalowane. Obsługuje również znajdowanie Visual Studio 2010 r. i nowsze, chociaż zwracanych jest mniej informacji niż w Visual Studio 2017 i nowszej. Aby uzyskać [przykłady, zobacz witrynę typu wiki.](https://github.com/Microsoft/vswhere/wiki) |
| [Polecenia cmdlet programu VSSetup](https://github.com/Microsoft/vssetup.powershell) | Polecenia cmdlet programu PowerShell obsługuje program 2.0 i nowsze, które zwracają rozbudowane informacje jako obiekty, których można używać do wyszukiwania wystąpień na podstawie tych samych kryteriów co program _vswhere_ i odnajdywania jeszcze większej liczby właściwości dotyczących wystąpień. Aby uzyskać [przykłady, zobacz witrynę typu wiki.](https://github.com/Microsoft/vssetup.powershell/wiki) |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Automatycznie lokalizuje _program VSIXInstaller_ i przekazuje wiersz polecenia w celu zainstalowania pliku **.vsix.* Ta funkcja może być przydatna w instalatorach, które nie mają bezpośredniej obsługi interfejsów API zapytań. Aby uzyskać [przykłady, zobacz witrynę typu wiki.](https://github.com/Microsoft/vsixbootstrapper/wiki) |

## <a name="see-also"></a>Zobacz też

* [Zmiany w konfiguracji Visual Studio 2017 r.](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Uruchamianie programu Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)
