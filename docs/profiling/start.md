---
title: Uruchom | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778274"
---
# <a name="start"></a>Początek
Opcja **Start** jest opcją *VSPerfCmd. exe* , która inicjuje profiler do określonej metody profilowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `Method` musi być jednym z następujących słów kluczowych:

- **Trace** — określa metodę Instrumentacji.

- **Przykład** — określa metodę próbkowania.

- **Pokrycie** — określa pokrycie kodu.

- **Współbieżność** — określa metodę rywalizacji o zasoby.

## <a name="required-options"></a>Wymagane opcje
 Opcja **Output** musi być określona, jeśli w wierszu polecenia określono wartość **Start** .

 **Dane wyjściowe:** `filename` określa nazwę pliku wyjściowego.

## <a name="exclusive-options"></a>Opcje wyłączności
 Następujących opcji można używać tylko z opcją **Start** w wierszu polecenia.

 **CrossSession**&#124;**CS** umożliwia profilowanie między procesami. Nazwy opcji **CrossSession** i **CS** są obsługiwane.

 **Użytkownik:** [`domain\`]`username` umożliwia dostęp klienta do monitora z określonego konta.

 **WinCounter:** `Path` [**automark**:`n`] **WinCounter** Określa licznik wydajności systemu Windows, który ma zostać uwzględniony jako znacznik w pliku danych profilowania. **Autoznacznik** określa interwał w milisekundach między kolekcjami pliku danych.

## <a name="invalid-options"></a>Nieprawidłowe opcje
 Następujących opcji nie można używać z opcją **Start** w wierszu polecenia.

 **Stan** stanu dotyczy tych procesów, które są profilowane. Wyświetla listę procesów i wątków oraz ich bieżący stan profilu (włączone/wyłączone). Na przykład jeśli proces został zatrzymany, **status** nie będzie wskazywać tego w raporcie. **Stan** będzie wskazywać, że proces jest profilowany lub nie.

 **Shutdown**[ **:** `Timeout`] wyłącza Profiler.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje sposób użycia opcji **Start** *VSPerfCmd. exe* w celu zainicjowania profilera.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
