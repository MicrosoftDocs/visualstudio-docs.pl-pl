---
title: Uruchom | Microsoft Docs
description: Dowiedz się, jak opcja uruchamiania uruchamia Profiler przy użyciu metody próbkowania i uruchamia również określoną aplikację.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bec7ebd26cc0522852276627d2c59161b51c809b
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721428"
---
# <a name="launch"></a>Uruchom
Opcja **uruchamiania** uruchamia Profiler przy użyciu metody próbkowania i uruchamia również określoną aplikację.

 Aby użyć opcji **uruchamiania** , należy określić **przykładową** metodę w opcji **Start** .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametry
 `AppName` Nazwa aplikacji do uruchomienia. Obsługiwane są pełne i częściowe ścieżki z bieżącego katalogu.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje VSPerfCmd można łączyć z opcją **uruchamiania** w pojedynczym wierszu polecenia.

 **Rozpocznij:** `Method` Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **GlobalOn** i **GlobalOff** wznawia (**GlobalOn**) lub wstrzymuje (**GlobalOff**) profilowanie, ale nie kończy sesji profilowania.

 **ProcessOn:** `PID` i **ProcessOff**: `PID` wznawia (**ProcessOn**) lub wstrzymuje (**ProcessOff**) profilowania dla określonego procesu.

 **TargetCLR** Określa wersję .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja zostanie załadowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.

## <a name="exclusive-options"></a>Opcje wyłączności
 Następujących opcji można używać tylko z opcją **uruchamiania** .

 **Konsola** programu Uruchamia określoną aplikację wiersza polecenia w nowym oknie.

 **Argumenty:** `ArgList` Określa listę argumentów do przekazania do aplikacji.

 **LineOff** Wyłącza zbieranie danych profilowania na poziomie wiersza.

## <a name="sampling-options"></a>Opcje próbkowania
 Jedną z następujących opcji interwału próbkowania można określić w wierszu polecenia **uruchamiania** . Domyślny interwał próbkowania to 10 000 000 cykli zegara procesora.

 **Czasomierz**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[**:** `Events` ]**licznik**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[:**alokacja**&#124;**okres istnienia**] określa liczbę i typ interwału próbkowania.

- **Czasomierz** — przykłady wszystkich `Cycles` niezatrzymanych cykli zegara procesora. Jeśli `Cycles` nie jest określona, używane są 10 000 000 cykli.

- **PF** — przykłady `Events` błędów każdej strony. Jeśli `Events` nie jest określony, 10 błędów stron.

- **Sys** -przykłady każdego `Events` wywołania systemu operacyjnego. Jeśli `Events` nie jest określony, używane są 10 wywołań systemowych.

- **Licznik** próbek każdej `Reload` liczby liczników wydajności procesora CPU określonych przez `Name` . Opcjonalnie `FriendlyName` można określić ciąg, który ma być używany jako nagłówek kolumny w raportach profilera.

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
