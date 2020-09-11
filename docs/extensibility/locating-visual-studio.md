---
title: Lokalizowanie programu Visual Studio | Microsoft Docs
ms.date: 08/21/2017
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93a6f39a9240002cd8008c9368799e10ab63b78d
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012480"
---
# <a name="locate-visual-studio"></a>Znajdowanie programu Visual Studio

Począwszy od programu Visual Studio 2017, można zainstalować wiele wystąpień tej samej wersji lub nawet wersji. Jest to przydatne, gdy chcesz wyświetlić podgląd nowej funkcjonalności na podstawowej maszynie deweloperskiej przy zachowaniu poprzedniej instalacji. Ze względu na te zmiany nie istnieje pojedyncza zmienna środowiskowa ani wartość rejestru, której można użyć do lokalizowania wystąpienia. Zamiast tego można użyć [interfejsu API zapytania com](/dotnet/api/microsoft.visualstudio.setup.configuration) , aby znaleźć wystąpienia na podstawie kryteriów związanych z danym rozszerzeniem.

Jest to szybki interfejs API tylko do odczytu z pakietami NuGet dostępnymi dla kodu natywnego i zarządzanego.

| Kod | Pakiet |
| ---- | --- |
| Natywna | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Zarządzany | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Można zlokalizować pojedyncze wystąpienie z daną ścieżką lub bieżącym procesem lub wyliczyć wszystkie wystąpienia. Zapoznaj się z [naszymi](https://github.com/Microsoft/vs-setup-samples) przykładami, aby uzyskać pełne Przykłady sposobu lokalizowania programu Visual Studio.

## <a name="tools"></a>narzędzia

Aby znaleźć program Visual Studio i inne narzędzia w środowiskach kompilacji, skryptach programu PowerShell, instalatorach i więcej scenariuszach, istnieje wiele narzędzi typu "open source", których można używać bezpośrednio lub ponownie rozpowszechniać wraz z własnymi skryptami.

| Projekt | Opis |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Natywny plik wykonywalny w jednym pliku do lokalizowania wystąpień, takich jak wydanie lub wersja wstępna, produkt, który jest instalowany, i które obciążenia są instalowane. Program obsługuje również znajdowanie programu Visual Studio w wersji 2010 lub nowszej, ale do programu Visual Studio 2017 i nowszego są zwracane mniej informacji. Przykłady można znaleźć w [witrynie typu wiki](https://github.com/Microsoft/vswhere/wiki) . |
| [Polecenia cmdlet VSSetup](https://github.com/Microsoft/vssetup.powershell) | Polecenia cmdlet programu PowerShell obsługują 2,0 i nowsze, które zwracają rozbudowane informacje jako obiekty, których można użyć do znajdowania wystąpień na podstawie tych samych kryteriów co _vswhere_ i odnajdywania jeszcze większej liczby właściwości dotyczących wystąpień. Przykłady można znaleźć w [witrynie typu wiki](https://github.com/Microsoft/vssetup.powershell/wiki) . |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Automatycznie lokalizuje _Instalator VSIX_ i przekazuje wiersz polecenia, aby zainstalować plik **. vsix* . Ta funkcja może być przydatna w instalatorach, które nie mają bezpośredniej pomocy technicznej dla interfejsów API zapytań. Przykłady można znaleźć w [witrynie typu wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) . |

## <a name="see-also"></a>Zobacz także

* [Zmiany w konfiguracji programu Visual Studio 2017](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup/)
* [Uruchamianie programu Visual Studio przy użyciu DTE](launch-visual-studio-dte.md)