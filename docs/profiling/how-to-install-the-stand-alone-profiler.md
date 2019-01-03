---
title: 'Instrukcje: Instalowanie autonomiczny Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f5068ff6b167e9cfda14799f799a397a322ff3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987119"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Instrukcje: Instalowanie autonomicznego profilera
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] udostępnia w wierszu polecenia zależności autonomicznym programem profilującym, które mogą być uruchamiane bez konieczności instalowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Ta sytuacja występuje, gdy komputer nie obsługuje lub nie może mieć zainstalowane środowisko programistyczne. Na przykład nie należy instalować Środowisko deweloperskie na serwerze sieci web w środowisku produkcyjnym.  
  
> [!NOTE]
>  Podczas korzystania z autonomicznego profilera do zbierania danych wydajności dla witryny sieci web ASP.NET, [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) narzędzie wiersza są zalecane przez [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia.  
  
### <a name="to-install-the-stand-alone-profiler"></a>Aby zainstalować autonomiczny profilera  

1. Pobierz [Performance Tools for Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio-2017).

1. Znajdź Instalator autonomiczny profilu (*vs_standaloneprofiler.exe*) którego pobrano performance tools i uruchom go.
  
2. Dodaj ścieżki dla *vsintr.exe* i *msdis150.dll* do ścieżki systemowej.  
  
   > [!NOTE]
   >  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. 
  
3. W wierszu polecenia wpisz **VSInstr**.  
  
   > [!NOTE]
   >  Jeśli zostanie wyświetlone informacje o użyciu dla vsinstr.exe, wszystko jest poprawnie skonfigurowany. Jeśli zostanie wyświetlony komunikat o błędzie informujący vsinstr.exe lub jednej z jego zależności nie zostanie znaleziony, upewnij się, że Twoje ścieżki poprawnie skonfigurowane zgodnie z opisem w kroku 2.  
  
4. Skonfigurować serwer symboli, ustawiając swoje **_NT_SYMBOL_PATH** zmienną **symsrv\*symsrv.dll\*c:\localcache\*http://msdl.microsoft.com/download/symbols**  
  
5. Po skonfigurowaniu serwera symboli za pomocą zmiennych środowiskowych systemu, uruchom profilera z wiersza polecenia narzędzia w nowym wierszu polecenia. Dzięki temu nowe zmienne środowiskowe zaczęły obowiązywać. W oknie wiersza polecenia wpisz następujące polecenie:  
  
    **Rozpocznij COMSPEC %**  
  
   > [!NOTE]
   >  Aby uzyskać szczegółowe instrukcje dotyczące sposobu konfigurowania pakietu serwera symboli, zobacz [jak: Odwoływać się do informacji o symbolach Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Użyj [VSPerfReport](../profiling/vsperfreport.md) narzędzie do wykonywania serializacji symboli do pliku danych (Vsp) profilowania. Użyj **packsymbols której VSPerfReport** przełączników. Jeśli nie masz symboli wstawione w pliku danych, upewnij się, że masz zestaw zmiennych środowiskowych _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Zobacz także  
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Przewodnik: Wiersza polecenia, profilowania przy użyciu metody próbkowania](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Przewodnik: Wiersza polecenia, profilowania przy użyciu metody Instrumentacji](/visualstudio/profiling/command-line-profiling-of-stand-alone-applications)   
 [Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)