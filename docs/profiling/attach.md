---
title: Dołącz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 482b3e80bce796910860cb7eab1e5a0066854238
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329868"
---
# <a name="attach"></a>Dołącz
Opcja *VSPerfCmd.exe* **dołączania**VSPerfCmd.exerozpoczyna przykładowe profilowanie uruchomionego procesu określonego przez identyfikator procesu (PID).

 Aby użyć opcji **Attach** , należy określić **przykładową** metodę w opcji Start.

> [!NOTE]
> Jeśli opcja **Start** została określona przy użyciu opcji **CrossSession** , wszystkie wywołania **VSPerfCmd/Attach** lub **VSPerfCmd/detach** muszą również określać **CrossSession**.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametry
 `ProcessID` Identyfikator procesu (PID) uruchomionego procesu. Identyfikator PID uruchomionego procesu jest wyświetlany na karcie procesy w Menedżerze zadań systemu Windows.

## <a name="valid-options"></a>Prawidłowe opcje
 Następujące opcje **VSPerfCmd** można łączyć z opcją **Attach** w pojedynczym wierszu polecenia.

 **CrossSession** Włącza Profilowanie aplikacji w sesjach innych niż sesja logowania. Wymagane, jeśli opcja **Start** została określona z opcją **CrossSession** .

 **Rozpocznij:** `Method` Inicjuje sesję profilera wiersza polecenia i ustawia określoną metodę profilowania.

 **TargetCLR** Określa wersję .NET Framework środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja zostanie załadowana w sesji profilowania. Domyślnie pierwsza załadowana wersja jest profilowana.

 **GlobalOn GlobalOff** Wznawia (**GlobalOn**) lub wstrzymuje (**GlobalOff**) profilowanie, ale nie kończy sesji profilowania.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Wznawia (**ProcessOn**) lub wstrzymuje (**ProcessOff**) profilowania dla określonego procesu.

## <a name="interval-options"></a>Opcje interwału
 Jedną z następujących opcji interwału próbkowania można określić w wierszu polecenia Attach. Domyślny interwał próbkowania to 10 000 000 cykli zegara procesora.

 **Czasomierz**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[<strong>:</strong>Events]**licznik**[**:** `Name` , `Reload` `FriendlyName` ] określa liczbę i typ interwału próbkowania.

- **Czasomierz** — przykłady dla każdego `Cycles` cyklu zegara procesora. Jeśli `Cycles` nie jest określona, używane są 10 000 000 cykli.

- **PF** — przykłady `Events` błędów każdej strony. Jeśli `Events` nie jest określony, używane są 10 błędów stron.

- **Sys** -przykłady każdego `Events` wywołania systemu operacyjnego. Jeśli `Events` nie jest określony, używane są 10 wywołań systemowych.

- **Licznik** próbek każdej `Reload` liczby liczników wydajności procesora CPU określonych przez `Name` . Opcjonalnie `FriendlyName` można określić ciąg, który ma być używany jako nagłówek kolumny w raportach profilera.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak dołączyć do uruchomionego wystąpienia aplikacji z IDENTYFIKATORem procesu 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
