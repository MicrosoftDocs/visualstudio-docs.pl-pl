---
title: Określanie ścieżki do profilowania narzędzia wiersza polecenia narzędzia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c89e741e4f854f0426a3b3908b896a8908325684
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634815"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Określ ścieżkę do narzędzia wiersza polecenia narzędzia profilowania
Ścieżka [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza poleceń Profiling Tools nie została dodana do zmiennej środowiskowej PATH. Na komputerach z 32-bitowe narzędzia znajdują się w jednym katalogu. Istnieje 32-bitowych i 64-bitowe wersje narzędzi profilowania na komputerach 64-bitowych.

## <a name="32-bit-computers"></a>32-bitowych komputerów
 Dla kodu natywnego programu Visual Studio profiler interfejsów API znajdują się w *VSPerf.dll*. Plik nagłówkowy *VSPerf.h*i bibliotekę importu *VSPerf.lib*, znajdują się w *programu Microsoft Visual Studio\2017\Team narzędzia Tools\PerfSDK* katalog.

 Dla kodu zarządzanego, program profilujący interfejsów API znajdują się w *Microsoft.VisualStudio.Profiler.dll*. Ta biblioteka DLL znajduje się w *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools* katalogu.

## <a name="64-bit-computers"></a>Komputery 64-bitowe
 Na komputerach 64-bitowych Określ ścieżkę zależnie od platformy docelowej profilowanej aplikacji.

-   Dla 32-bitowych aplikacji domyślny katalog narzędzia profiler jest:

     (natywna) *Programu Microsoft Visual Studio\2017\Team narzędzia Tools\PerfSDK* (zarządzane) *Studio\Shared\Common\VSPerfCollectionTools Visual firmy Microsoft*

-   Dla aplikacji 64-bitowych jest domyślny katalog narzędzi profilera:

     (natywna) *Programu Microsoft Visual Studio\2017\Team narzędzia Tools\x64\PerfSDK* (zarządzane) *Studio\Shared\Common\VSPerfCollectionTools\x64 Visual firmy Microsoft*