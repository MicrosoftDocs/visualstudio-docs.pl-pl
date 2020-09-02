---
title: Określanie ścieżki do narzędzi wiersza polecenia narzędzia profilowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fadcff84c4b927a7718d7d4ad1311918ae0f18a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199775"
---
# <a name="specifying-the-path-to-profiling-tools-command-line-tools"></a>Określanie ścieżki do narzędzi wiersza polecenia narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ścieżka [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do narzędzia profilowania narzędzi wiersza polecenia nie jest dodawana do zmiennej środowiskowej PATH. Na komputerach 32-bitowych narzędzia znajdują się w jednym katalogu. Na komputerach 64-bitowych istnieją 32-bitowe i 64-bitowe wersje narzędzi profilowania.  
  
## <a name="32-bit-computers"></a>32-bitowe komputery  
 Na komputerach 32-bitowych domyślnym katalogiem narzędzi profilera jest *dysk*\Program Files\Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools.  
  
## <a name="64-bit-computers"></a>Komputery 64-bitowe  
 Na komputerach 64-bitowych określ ścieżkę zgodną z platformą docelową profilowanej aplikacji.  
  
- W przypadku aplikacji 32-bitowych domyślnym katalogiem narzędzi profilera jest:  
  
     *Dysk*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools  
  
- W przypadku aplikacji 64-bitowych domyślnym katalogiem narzędzi profilera jest:  
  
     *Dysk*\Program Files (x86) \Microsoft Visual Studio 11.0 \ Team Tools\Performance Tools\x64
