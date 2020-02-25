---
title: 'Instrukcje: Instalowanie autonomicznego profilera | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ec0f211db3d9906d83d9bcf7c7a0ab79ec3e1b7f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557827"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Instrukcje: Instalowanie autonomicznego profilera
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] udostępnia autonomiczny profiler oparty na wierszu polecenia, który można uruchomić bez instalowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Taka sytuacja występuje, gdy komputer nie ma zainstalowanego środowiska deweloperskiego. Na przykład nie należy instalować środowiska deweloperskiego na produkcyjnym serwerze sieci Web.

> [!NOTE]
> Gdy korzystasz z autonomicznego profilera do zbierania danych wydajności dla witryny sieci Web ASP.NET, narzędzie wiersza [VSPerfASPNETCmd](../profiling/vsperfaspnetcmd.md) jest zalecane za pośrednictwem narzędzia [VSPerfCmd](../profiling/vsperfcmd.md) .

### <a name="to-install-the-stand-alone-profiler"></a>Aby zainstalować autonomiczny profiler

1. Pobierz [Narzędzia do oceny wydajności dla programu Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Zlokalizuj Instalatora profilu autonomicznego (*vs_standaloneprofiler. exe*), do którego pobrano narzędzia do oceny wydajności i uruchom go.

2. Dodaj ścieżkę do pliku *VSInstr. exe* do ścieżki systemowej.

   > [!NOTE]
   > Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

3. W wierszu polecenia wpisz **VSInstr**.

   > [!NOTE]
   > Jeśli zostanie wyświetlone informacje o użyciu programu VSInstr. exe, wszystko jest poprawnie skonfigurowane. Jeśli zostanie wyświetlony komunikat o błędzie z informacją, że nie można odnaleźć VSInstr. exe lub jednej z jego zależności, upewnij się, że ścieżki zostały skonfigurowane prawidłowo, zgodnie z opisem w sekcji Krok 2.

4. Skonfiguruj serwer symboli, ustawiając zmienną **_NT_SYMBOL_PATH** na **symsrv\*symsrv. dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols**

5. Po skonfigurowaniu serwera symboli przy użyciu zmiennych środowiskowych systemu Uruchom narzędzia profilera wiersza polecenia w nowym wierszu polecenia. Pozwala to zastosować nowe zmienne środowiskowe. W oknie wiersza polecenia wpisz następujące polecenie:

    **Uruchom% wywołana%**

   > [!NOTE]
   > Aby uzyskać szczegółowe instrukcje dotyczące sposobu konfigurowania pakietu serwera symboli, zobacz [How to: Reference informacje o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md).

6. Użyj narzędzia [VSPerfReport](../profiling/vsperfreport.md) , aby serializować symbole do pliku danych profilowania (. vsp). Użyj **VSPerfReport/Summary: wszystkie przełączniki/PACKSYMBOLS** . Jeśli nie masz symboli wstawionych do pliku danych, upewnij się, że masz ustawioną zmienną środowiskową _NT_SYMBOL_PATH.

## <a name="see-also"></a>Zobacz też
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Przewodnik: profilowanie wiersza polecenia przy użyciu metody instrumentacji](command-line-profiling-of-stand-alone-applications.md)
- [Instrukcje: odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
