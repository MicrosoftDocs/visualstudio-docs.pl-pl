---
title: Określanie ścieżki do profilowania narzędzia wiersza polecenia narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ef2434cdea3183fc55ad72fafb36175a726c58e
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592901"
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