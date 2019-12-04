---
title: Uruchom | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9834c10c58fb343de0707fa0b805586a6cdebcb3
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778612"
---
# <a name="launch"></a>Uruchom
Opcja **uruchamiania** uruchamia Profiler przy użyciu metody próbkowania i uruchamia również określoną aplikację.

 Aby użyć opcji **uruchamiania** , należy określić **przykładową** metodę w opcji **Start** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametry
 `AppName` nazwę aplikacji do uruchomienia. Obsługiwane są pełne i częściowe ścieżki z bieżącego katalogu.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje VSPerfCmd można łączyć z opcją **uruchamiania** w pojedynczym wierszu polecenia.

 **Rozpoczęcie:** `Method` inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **GlobalOn** i **GlobalOff** wznawia (**GlobalOn**) lub wstrzymuje (**GlobalOff**) profilowanie, ale nie kończy sesji profilowania.

 **ProcessOn:** `PID` i **ProcessOff**:`PID` wznawiania (**ProcessOn**) lub wstrzymywania (**ProcessOff**) profilowania dla określonego procesu.

 **TargetCLR** Określa wersję .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja zostanie załadowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.

## <a name="exclusive-options"></a>Opcje wyłączności
 Następujących opcji można używać tylko z opcją **uruchamiania** .

 **Konsola** programu Uruchamia określoną aplikację wiersza polecenia w nowym oknie.

 **Argumenty:** `ArgList` określa listę argumentów do przekazania do aplikacji.

 **LineOff** Wyłącza zbieranie danych profilowania na poziomie wiersza.

## <a name="sampling-options"></a>Opcje próbkowania
 Jedną z następujących opcji interwału próbkowania można określić w wierszu polecenia **uruchamiania** . Domyślny interwał próbkowania to 10 000 000 cykli zegara procesora.

 **Timer**[ **:** `Cycles`]**PF**[ **:** `Events`]**sys**[ **:** `Events`]**licznik**[ **:** `Name`,`Reload`,`FriendlyName`]**GC**[:&#124;**okres istnienia**przydziału] określa liczbę i typ interwału próbkowania.

- **Czasomierz** — przykłady co `Cycles` niezatrzymane cykle zegara procesora. Jeśli nie określono `Cycles`, używane są cykle 10 000 000.

- **PF** -przykłady każdej `Events` błędów stron. Jeśli nie określono `Events`, 10 błędów stron.

- **Sys** -Samples każdy `Events` wywołań do systemu operacyjnego. Jeśli nie określono `Events`, używane są 10 wywołań systemowych.

- **Licznik** próbek każdej `Reload` liczbę liczników wydajności procesora CPU określonych przez `Name`. Opcjonalnie `FriendlyName` może określić ciąg, który ma być używany jako nagłówek kolumny w raportach profilera.

- **GC** — zbiera dane pamięci platformy .NET. Domyślnie (**alokacja**) dane są zbierane przy każdym zdarzeniu przydziału pamięci. Gdy określono parametr **okresu istnienia** , dane są również zbierane przy każdym zdarzeniu odzyskiwania pamięci.

## <a name="example"></a>Przykład
 Ten przykład ilustruje użycie **uruchomienia** do uruchomienia aplikacji.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
