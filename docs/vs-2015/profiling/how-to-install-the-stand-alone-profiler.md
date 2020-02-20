---
title: 'Instrukcje: Instalowanie autonomicznego profilera | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 026162a2c8334c7163f9c7853d2de30e58e5939a
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476785"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Porady: instalowanie autonomiczny profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia autonomiczny profiler oparty na wierszu polecenia, który można uruchomić bez instalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Taka sytuacja występuje, gdy komputer nie ma zainstalowanego środowiska deweloperskiego. Na przykład nie należy instalować środowiska deweloperskiego na produkcyjnym serwerze sieci Web.  
  
> [!NOTE]
> Gdy korzystasz z autonomicznego profilera do zbierania danych wydajności dla witryny sieci Web ASP.NET, narzędzie wiersza [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) jest zalecane za pośrednictwem narzędzia [VSPerfCmd](../profiling/vsperfcmd.md) .  
  
### <a name="to-install-the-stand-alone-profiler"></a>Aby zainstalować autonomiczny profiler  
  
1. Zlokalizuj Instalatora profilu autonomicznego (vs_profiler. exe) na nośniku instalacyjnym programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] w katalogu zawierającym ścieżkę profilera \Standalone i uruchom go.  
  
2. Dodaj ścieżki dla vsintr. exe i msdis150. dll do ścieżki systemowej.  
  
    > [!NOTE]
    > W domyślnej instalacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], VSInstr. exe i msdis150. dll znajdują się w folderze \Program Files\Visual Studio 10 \ Team Tools\Performance Tools.  
  
3. W wierszu polecenia wpisz **VSInstr**.  
  
    > [!NOTE]
    > Jeśli zostanie wyświetlone informacje o użyciu programu VSInstr. exe, wszystko jest poprawnie skonfigurowane. Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że nie można odnaleźć VSInstr. exe lub jednej z jego zależności, upewnij się, że ścieżki zostały skonfigurowane prawidłowo, zgodnie z opisem w sekcji Krok 2.  
  
4. Skonfiguruj serwer symboli, ustawiając zmienną **_NT_SYMBOL_PATH** na `symsrv*symsrv.dll*c:\localcache* https://msdl.microsoft.com/download/symbols`  
  
5. Po skonfigurowaniu serwera symboli przy użyciu zmiennych środowiskowych systemu Uruchom narzędzia profilera wiersza polecenia w nowym wierszu polecenia. Pozwala to zastosować nowe zmienne środowiskowe. W oknie wiersza polecenia wpisz następujące polecenie:  
  
     **Uruchom% wywołana%**  
  
    > [!NOTE]
    > Aby uzyskać szczegółowe instrukcje dotyczące sposobu konfigurowania pakietu serwera symboli, zobacz [How to: Reference informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Użyj narzędzia [VSPerfReport](../profiling/vsperfreport.md) , aby serializować symbole do pliku danych profilowania (. vsp). Użyj **VSPerfReport/Summary: wszystkie przełączniki/PACKSYMBOLS** . Jeśli nie masz symboli wstawionych do pliku danych, upewnij się, że masz ustawioną zmienną środowiskową _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie z  wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)  
 [Przewodnik: Profilowanie wiersza polecenia przy użyciu  próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)  
 [Przewodnik: Profilowanie wiersza polecenia przy użyciu instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Instrukcje: odwołanie do  informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)  
 [VSPerfReport](../profiling/vsperfreport.md)
