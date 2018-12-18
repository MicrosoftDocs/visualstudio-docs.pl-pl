---
title: Określanie ścieżki do profilowania narzędzia wiersza polecenia narzędzia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 886c035ddcc14b43200b13d789e59430cf090fdf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731270"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Określanie ścieżki do narzędzi wiersza polecenia narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ścieżka [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza poleceń Profiling Tools nie została dodana do zmiennej środowiskowej PATH. Na komputerach z 32-bitowe narzędzia znajdują się w jednym katalogu. Istnieje 32-bitowych i 64-bitowe wersje narzędzi profilowania na komputerach 64-bitowych.  
  
## <a name="32-bit-computers"></a>32-bitowych komputerów  
 Na komputerach 32-bitowych jest domyślny katalog narzędzia profiler *dysku*\Program Files\Microsoft 11.0\Team programu Visual Studio Tools narzędzia.  
  
## <a name="64-bit-computers"></a>Komputery 64-bitowe  
 Na komputerach 64-bitowych Określ ścieżkę zależnie od platformy docelowej profilowanej aplikacji.  
  
-   Dla 32-bitowych aplikacji domyślny katalog narzędzia profiler jest:  
  
     *Dysk*\Program pliki (x86) \Microsoft Visual Studio 11.0\Team narzędzia Tools  
  
-   Dla aplikacji 64-bitowych jest domyślny katalog narzędzi profilera:  
  
     *Dysk*\Program pliki (x86) \Microsoft Visual Studio 11.0\Team narzędzia Tools\x64



