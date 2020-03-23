---
title: Dołącz | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 634169607a7d581de1b1332d78e8d5abde1a722e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773742"
---
# <a name="attach"></a>Attach
Opcja *VSPerfCmd.exe* **Dołącz** rozpoczyna profilowanie próbek uruchomionego procesu określonego przez identyfikator procesu (PID).

 Aby użyć opcji **Dołącz,** należy określić **metodę Sample** w opcji Start.

> [!NOTE]
> Jeśli opcja **Start** została określona za pomocą opcji **Crosssession,** wszystkie wywołania **vsperfcmd /Attach** lub **VSPerfCmd /Detach** muszą również określać **crosssession**.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametry
 `ProcessID`Identyfikator procesu (PID) uruchomionego procesu. Identyfikator PID uruchomionego procesu jest wyświetlany na karcie Procesy Menedżera zadań systemu Windows.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje **VSPerfCmd** można łączyć z opcją **Dołącz** w jednym wierszu polecenia.

 **Crosssession (krzyżyk)** Umożliwia profilowanie aplikacji w sesjach innych niż sesja logowania. Wymagane, jeśli opcja **Start** została określona za pomocą opcji **Crosssession.**

 **Start:** `Method` Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **TargetCLR (DocelowyCLR)** Określa wersję programu .NET Framework Common Language Runtime (CLR) do profilu, gdy więcej niż jedna wersja jest ładowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.

 **GlobalOn GlobalOff** Wznawia **(GlobalOn)** lub wstrzymuje profilowanie **(GlobalOff),** ale nie kończy sesji profilowania.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Resumes **(ProcessOn**) lub wstrzymuje **(ProcessOff)** profilowanie dla określonego procesu.

## <a name="interval-options"></a>Opcje interwałów
 W wierszu polecenia Dołącz można określić jedną z następujących opcji interwału próbkowania. Domyślny interwał próbkowania wynosi 10 000 000 cykli zegara procesora.

 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**`FriendlyName`[<strong>:</strong>Zdarzenia]**Licznik**[**:**`Name`,`Reload`] Określa liczbę i typ interwału próbkowania.

- **Timer** — próbki `Cycles` każdego zegara procesora. Jeśli `Cycles` nie zostanie określony, używane są 10 000 000 cykli.

- **PF** - Próbki `Events` co strona błędów. Jeśli `Events` nie zostanie określony, 10-stronicowe błędy są używane.

- **Sys** — przykłady wszystkich `Events` wywołań do systemu operacyjnego. Jeśli `Events` nie zostanie określony, 10 wywołań systemowych są używane.

- **Licznik** — przykłada każdą `Reload` liczbę licznika `Name`wydajności procesora określonego przez . Opcjonalnie `FriendlyName` można określić ciąg do użycia jako nagłówek kolumny w raportach profilera.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak dołączyć do uruchomionego wystąpienia aplikacji o identyfikatorze procesu 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
