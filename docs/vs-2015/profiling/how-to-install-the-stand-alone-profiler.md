---
title: 'Porady: Instalowanie autonomiczny Profiler | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d387a9f085b8cf755bfb8efb8ddd056c16cca4e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817168"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Porady: instalowanie autonomiczny profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] udostępnia w wierszu polecenia zależności autonomicznym programem profilującym, które mogą być uruchamiane bez konieczności instalowania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Ta sytuacja występuje, gdy komputer nie obsługuje lub nie może mieć zainstalowane środowisko programistyczne. Na przykład nie należy instalować Środowisko deweloperskie na serwerze sieci Web w środowisku produkcyjnym.  
  
> [!NOTE]
>  Podczas korzystania z autonomicznego profilera do zbierania danych wydajności dla witryny sieci Web ASP.NET [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) narzędzie wiersza są zalecane przez [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Aby zainstalować autonomiczny profilera  
  
1.  Zlokalizuj Instalator autonomiczny profilu (vs_profiler.exe) na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nośniku instalacyjnym w katalogu, który zawiera ścieżkę Profiler \Standalone i uruchomimy ją.  
  
2.  Dodaj ścieżki vsintr.exe i msdis150.dll do ścieżki systemowej.  
  
    > [!NOTE]
    >  W domyślnej instalacji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vsinstr.exe i msdis150.dll znajdują się w \Program Files\Visual Studio 10\Team narzędzia Tools.  
  
3.  W wierszu polecenia wpisz **VSInstr**.  
  
    > [!NOTE]
    >  Jeśli zostanie wyświetlone informacje o użyciu dla vsinstr.exe, wszystko jest poprawnie skonfigurowany. Jeśli zostanie wyświetlony komunikat o błędzie informujący vsinstr.exe lub jednej z jego zależności nie zostanie znaleziony, upewnij się, że Twoje ścieżki poprawnie skonfigurowane zgodnie z opisem w kroku 2.  
  
4.  Skonfigurować serwer symboli, ustawiając swoje **_NT_SYMBOL_PATH** zmienną **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5.  Po skonfigurowaniu serwera symboli za pomocą zmiennych środowiskowych systemu, uruchom profilera z wiersza polecenia narzędzia w nowym wierszu polecenia. Dzięki temu nowe zmienne środowiskowe zaczęły obowiązywać. W oknie wiersza polecenia wpisz następujące polecenie:  
  
     **Rozpocznij COMSPEC %**  
  
    > [!NOTE]
    >  Aby uzyskać szczegółowe instrukcje dotyczące sposobu konfigurowania pakietu serwera symboli, zobacz [jak: informacje o symbolach Windows odwołanie](../profiling/how-to-reference-windows-symbol-information.md).  
  
6.  Użyj [VSPerfReport](../profiling/vsperfreport.md) narzędzie do wykonywania serializacji symboli do pliku danych (Vsp) profilowania. Użyj **packsymbols której VSPerfReport** przełączników. Jeśli nie masz symboli wstawione w pliku danych, upewnij się, że masz zestaw zmiennych środowiskowych _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Wskazówki: Profilowanie wiersza polecenia przy użyciu metody próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Wskazówki: Profilowanie wiersza polecenia przy użyciu metody Instrumentacji](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Porady: odwoływać się do informacji o symbolach Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



