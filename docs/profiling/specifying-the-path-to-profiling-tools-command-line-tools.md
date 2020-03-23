---
title: Określanie narzędzi wiersza wiersza ścieżki do narzędzi do profilowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f66ed17aec8c6e5303ea61741021dd25032fcb37
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75406300"
---
# <a name="specify-the-path-to-profiling-tools-command-line-tools"></a>Określanie ścieżki do narzędzi wiersza polecenia narzędzi narzędzi do profilowania

Ścieżka narzędzi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia Narzędzia profilowania nie jest dodawana do zmiennej środowiskowej PATH. Na komputerach 32-bitowych narzędzia znajdują się w jednym katalogu. Istnieją 32-bitowe i 64-bitowe wersje narzędzi profilowania na komputerach 64-bitowych.

## <a name="32-bit-computers"></a>Komputery 32-bitowe

Dla kodu macierzystego interfejsy API profilera programu Visual Studio znajdują się w pliku *VSPerf.dll*. Plik nagłówka *VSPerf.h*i biblioteka importu *VSPerf.lib*znajdują się w katalogu *programu Microsoft Visual Studio\2017\Team Tools\Performance Tools\PerfSDK.*

 W przypadku kodu zarządzanego interfejsy API profilera znajdują się w pliku *Microsoft.VisualStudio.Profiler.dll*. Ta biblioteka DLL znajduje się w katalogu *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools.*

## <a name="64-bit-computers"></a>Komputery 64-bitowe

Na komputerach 64-bitowych określ ścieżkę zgodnie z platformą docelową profilowanych aplikacji.

- W przypadku aplikacji 32-bitowych domyślny katalog narzędzi profilera to:

     (natywny) *Microsoft Visual Studio\2017\Narzędzia zespołu\Narzędzia wydajności\PerfSDK*
     
     (zarządzane) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools*

- W przypadku aplikacji 64-bitowych domyślny katalog narzędzi profilera to:

     (natywny) *Microsoft Visual Studio\2017\Narzędzia zespołu\Narzędzia wydajności\x64\PerfSDK*

     (zarządzane) *Microsoft Visual Studio\Shared\Common\VSPerfCollectionTools\x64*
