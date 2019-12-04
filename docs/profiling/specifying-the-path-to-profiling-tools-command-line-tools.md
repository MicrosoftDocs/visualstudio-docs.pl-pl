---
title: Określanie ścieżki do narzędzi wiersza polecenia narzędzia profilowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 087407f511c038a369694beca8a9fe4ecc2ff7b7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771584"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Określanie ścieżki do narzędzi wiersza polecenia narzędzi profilowania

Ścieżka do narzędzia profilowania narzędzi wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest dodawana do zmiennej środowiskowej PATH. Na komputerach 32-bitowych narzędzia znajdują się w jednym katalogu. Na komputerach 64-bitowych istnieją 32-bitowe i 64-bitowe wersje narzędzi profilowania.

## <a name="32-bit-computers"></a>32-bitowe komputery

::: moniker range="vs-2017"
 W przypadku kodu natywnego interfejsy API profilera programu Visual Studio znajdują się w *VSPerf. dll*. Plik nagłówkowy, *VSPerf. h*i Biblioteka Imports *VSPerf. lib*znajdują się w katalogu *programu Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* .
::: moniker-end

 W przypadku kodu zarządzanego interfejsy API profilera znajdują się w *pliku Microsoft. VisualStudio. Profiler. dll*. Ta biblioteka DLL znajduje się w katalogu *programu Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* .

## <a name="64-bit-computers"></a>Komputery 64-bitowe

Na komputerach 64-bitowych określ ścieżkę zgodną z platformą docelową profilowanej aplikacji.

::: moniker range="vs-2017"
- W przypadku aplikacji 32-bitowych domyślnym katalogiem narzędzi profilera jest:

     trybu *Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK* (Managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- W przypadku aplikacji 64-bitowych domyślnym katalogiem narzędzi profilera jest:

     trybu *Microsoft Visual Studio\2017\Team Tools\Performance Tools\x64\PerfSDK* (Managed) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
::: moniker-end
