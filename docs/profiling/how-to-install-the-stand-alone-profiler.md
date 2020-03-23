---
title: 'Jak: Zainstaluj profiler autonomiczny | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557827"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Jak: Zainstaluj samodzielny profiler
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zapewnia autonomiczny profiler oparty na wierszu polecenia, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] który można uruchomić bez instalowania IDE. Taka sytuacja występuje, gdy komputer nie ma lub nie może mieć zainstalowane środowisko programistyczne. Na przykład nie należy instalować środowiska programistycznego na produkcyjnym serwerze sieci web.

> [!NOTE]
> Podczas korzystania z autonomicznego profilera do zbierania danych o wydajności dla witryny sieci web ASP.NET narzędzie [linii VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) jest zalecane za pośrednictwem narzędzia [VSPerfCmd.](../profiling/vsperfcmd.md)

### <a name="to-install-the-stand-alone-profiler"></a>Aby zainstalować profiler autonomiczny

1. Pobierz [narzędzia wydajności dla programu Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Znajdź autonomiczny instalator profilu *(vs_standaloneprofiler.exe),* w którym pobrano narzędzia wydajności i uruchom go.

2. Dodaj ścieżkę *vsinstr.exe* do ścieżki systemowej.

   > [!NOTE]
   > Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

3. W wierszu polecenia wpisz **VSInstr**.

   > [!NOTE]
   > Jeśli zostaną wyświetlone informacje o użyciu vsinstr.exe, wszystko jest poprawnie skonfigurowane. Jeśli widzisz błąd, który stwierdza vsinstr.exe lub jeden z jego zależności nie został znaleziony, upewnij się, że ścieżki są poprawnie skonfigurowane zgodnie z opisem w kroku 2.

4. Konfigurowanie serwera symboli przez ustawienie **zmiennej _NT_SYMBOL_PATH** na **\*symsrv.dll\*c:\localcache\* **

5. Po skonfigurowaniu serwera symboli przy użyciu zmiennych środowiska systemowego uruchom narzędzia profilera wiersza polecenia w nowym wierszu polecenia. Dzięki temu nowe zmienne środowiskowe mogą wejść w życie. W oknie wiersza polecenia wpisz następujące polecenie:

    **start %COMSPEC%**

   > [!NOTE]
   > Aby uzyskać szczegółowe instrukcje dotyczące konfigurowania pakietu serwera symboli, zobacz [Jak: Odwoływanie się do informacji o symbolu systemu Windows](../profiling/how-to-reference-windows-symbol-information.md).

6. Narzędzie [VSPerfReport](../profiling/vsperfreport.md) służy do serializacji symboli w pliku danych profilowania (vsp). Użyj przełączników **VSPerfReport /summary:all /packsymbols.** Jeśli w pliku danych nie wstawiono symboli, upewnij się, że masz ustawiony _NT_SYMBOL_PATH zmiennej środowiskowej.

## <a name="see-also"></a>Zobacz też
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Przewodnik: profilowanie wiersza polecenia przy użyciu metody instrumentacji](command-line-profiling-of-stand-alone-applications.md)
- [Instrukcje: odwołania do informacji o symbolach w systemie Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
