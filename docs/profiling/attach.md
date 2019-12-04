---
title: Dołącz | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773742"
---
# <a name="attach"></a>Dołącz
Opcja **dołączania** *VSPerfCmd. exe* rozpoczyna przykładowe profilowanie uruchomionego procesu określonego przez identyfikator procesu (PID).

 Aby użyć opcji **Attach** , należy określić **przykładową** metodę w opcji Start.

> [!NOTE]
> Jeśli opcja **Start** została określona przy użyciu opcji **CrossSession** , wszystkie wywołania **VSPerfCmd/Attach** lub **VSPerfCmd/detach** muszą również określać **CrossSession**.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametry
 `ProcessID` identyfikator procesu (PID) uruchomionego procesu. Identyfikator PID uruchomionego procesu jest wyświetlany na karcie procesy w Menedżerze zadań systemu Windows.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje **VSPerfCmd** można łączyć z opcją **Attach** w pojedynczym wierszu polecenia.

 **CrossSession** Włącza Profilowanie aplikacji w sesjach innych niż sesja logowania. Wymagane, jeśli opcja **Start** została określona z opcją **CrossSession** .

 **Rozpoczęcie:** `Method` inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **TargetCLR** Określa wersję .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja zostanie załadowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.

 **GlobalOn GlobalOff** Wznawia (**GlobalOn**) lub wstrzymuje (**GlobalOff**) profilowanie, ale nie kończy sesji profilowania.

 **ProcessOn:** `PID` **ProcessOff:** `PID` wznawiania (**ProcessOn**) lub wstrzymywania (**ProcessOff**) profilowania dla określonego procesu.

## <a name="interval-options"></a>Opcje interwału
 Jedną z następujących opcji interwału próbkowania można określić w wierszu polecenia Attach. Domyślny interwał próbkowania to 10 000 000 cykli zegara procesora.

 **Timer**[ **:** `Cycles`]**PF**[ **:** `Events`]**sys**[<strong>:</strong>Events]**licznik**[ **:** `Name`,`Reload`,`FriendlyName`] określa liczbę i typ interwału próbkowania.

- **Czasomierz** — przykłady dla każdego `Cycles` cykli zegara procesora. Jeśli nie określono `Cycles`, używane są cykle 10 000 000.

- **PF** -przykłady każdej `Events` błędów stron. Jeśli nie określono `Events`, używane są 10 błędów stron.

- **Sys** -Samples każdy `Events` wywołań do systemu operacyjnego. Jeśli nie określono `Events`, używane są 10 wywołań systemowych.

- **Licznik** próbek każdej `Reload` liczbę liczników wydajności procesora CPU określonych przez `Name`. Opcjonalnie `FriendlyName` może określić ciąg, który ma być używany jako nagłówek kolumny w raportach profilera.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak dołączyć do uruchomionego wystąpienia aplikacji z IDENTYFIKATORem procesu 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
