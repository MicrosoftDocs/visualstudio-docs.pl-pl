---
title: Premiera | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778612"
---
# <a name="launch"></a>Uruchom
Uruchom **Launch** opcja uruchamia profiler przy użyciu metody próbkowania i uruchamia również określoną aplikację.

 Aby użyć opcji **Uruchom,** należy określić **metodę Sample** w opcji **Start.**

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametry
 `AppName`Nazwa aplikacji do uruchomienia. Obsługiwane są pełne i częściowe ścieżki z bieżącego katalogu.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje VSPerfCmd można połączyć z opcją **Uruchom** w jednym wierszu polecenia.

 **Start:** `Method` Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **GlobalOn** i **GlobalOff** wznawia **(GlobalOn**) lub wstrzymuje **(GlobalOff**) profilowania, ale nie kończy sesji profilowania.

 **ProcessOn:** `PID` i **ProcessOff:**`PID` Wznawia **(ProcessOn**) lub wstrzymuje **(ProcessOff**) profilowanie dla określonego procesu.

 **TargetCLR (DocelowyCLR)** Określa wersję programu .NET Framework Common Language Runtime (CLR) do profilu, gdy więcej niż jedna wersja jest ładowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.

## <a name="exclusive-options"></a>Opcje ekskluzywne
 Z opcją **Uruchom** można używać następujących opcji.

 **Konsola** Uruchamia określoną aplikację wiersza polecenia w nowym oknie.

 **Args:** `ArgList` Określa listę argumentów, które mają być przesuwane do aplikacji.

 **Linia Odwł.,** Wyłącza zbieranie danych profilowania na poziomie wiersza.

## <a name="sampling-options"></a>Opcje próbkowania
 W wierszu polecenia **Uruchom** można określić jedną z następujących opcji interwału próbkowania. Domyślny interwał próbkowania wynosi 10 000 000 cykli zegara procesora.

 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Licznik**[**:**`Name``Reload`,`FriendlyName`], ]**GC**[:**alokacja**&#124;**okres istnienia**] Określa liczbę i typ interwału próbkowania.

- **Timer** — próbki `Cycles` co cykle zegara procesora niezatrzymowane. Jeśli `Cycles` nie zostanie określony, używane są 10 000 000 cykli.

- **PF** - Próbki `Events` co strona błędów. Jeśli `Events` nie zostanie określony, 10-stronicowe błędy.

- **Sys** — przykłady wszystkich `Events` wywołań do systemu operacyjnego. Jeśli `Events` nie zostanie określony, 10 wywołań systemowych są używane.

- **Licznik** — przykłada każdą `Reload` liczbę licznika `Name`wydajności procesora określonego przez . Opcjonalnie `FriendlyName` można określić ciąg do użycia jako nagłówek kolumny w raportach profilera.

- **GC** — zbiera dane pamięci .NET. Domyślnie **(alokacja)** dane są zbierane przy każdym zdarzeniu alokacji pamięci. Po określeniu parametru **lifetime** dane są również zbierane w każdym przypadku wyrzucania elementów bezużytecznych.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano użycie **Uruchom** do uruchomienia aplikacji.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
