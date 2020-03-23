---
title: Start | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: df3ccda9730be02bafb7f7d069a26193a4528d1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778274"
---
# <a name="start"></a>Rozpoczęcie
**Start** Opcja jest *vsPerfCmd.exe* opcja, która inicjuje profiler do określonej metody profilowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `Method`Musi być jednym z następujących słów kluczowych:

- **TRACE** - Określa metodę instrumentacji.

- **PRZYKŁAD —** określa metodę pobierania próbek.

- **POKRYCIE** — określa pokrycie kodu.

- **WSPÓŁBIEŻNOŚĆ** — określa metodę rywalizacji o zasoby.

## <a name="required-options"></a>Wymagane opcje
 Opcja **Wyjście** musi być określona, gdy w wierszu polecenia jest określony **przycisk Start.**

 **Dane wyjściowe:** `filename` Określa nazwę pliku wyjściowego.

## <a name="exclusive-options"></a>Opcje ekskluzywne
 Poniższych opcji można używać tylko z opcją **Start** w wierszu polecenia.

 **CrossSession**&#124;**CS** Umożliwia profilowanie międzyprocesowe. Obsługiwane są nazwy opcji **CrossSession** i **CS.**

 **Użytkownik:**`domain\`[`username` ] Umożliwia klientowi dostęp do monitora z określonego konta.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** określa licznik wydajności systemu Windows, który należy uwzględnić jako znak w pliku danych profilowania. **AutoMark** określa interwał w milisekundach między kolekcjami pliku danych.

## <a name="invalid-options"></a>Nieprawidłowe opcje
 Następujących opcji nie można używać z opcją **Start** w wierszu polecenia.

 **Stan** **ma** zastosowanie do tych procesów, które są profilowane. Wyświetla listę procesów i wątków oraz ich bieżącego stanu profilu (On/Off). Na przykład jeśli proces zostanie zatrzymany, **Stan** nie wskaże tego w raporcie. **Stan** pokaże, że proces jest profilowany lub nie.

 **Zamknięcie**[**:**`Timeout`] Wyłącza profiler.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, jak za pomocą *vsPerfCmd.exe* **Start** opcja zainicjować profiler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
