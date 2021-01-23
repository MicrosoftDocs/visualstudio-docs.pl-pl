---
title: Oznacz | Microsoft Docs
description: Dowiedz się, jak opcja oznaczania VSPerfCmd.exe wstawia określone informacje do pliku danych profilowania.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4554a994fe790d5e0ec46762e830576181b312dd
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722142"
---
# <a name="mark"></a>Znacznik
Opcja  **Oznacz** VSPerfCmd.exewstawia określone informacje do pliku danych profilowania. Znacznik może być wyświetlany w osobnym raporcie VSPerfReport lub w widoku raportu w interfejsie użytkownika profilera. **Znacznik** może służyć do określania punktów początkowych i końcowych w raportach i widokach filtrów.

 Opcja **Oznacz** musi być jedyną opcją określoną w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametry
 `MarkID` Zdefiniowana przez użytkownika liczba całkowita, która jest wyświetlana jako identyfikator znacznika w widokach i raportach profilera. `MarkID` nie musi być unikatowy.

 `MarkName` Obowiązkowe Zdefiniowany przez użytkownika ciąg, który jest wyświetlany jako nazwa znacznika w widokach i raportach profilera. Jeśli `MarkName` nie jest określony, pole nazwa znacznika listy znaczników jest puste. Ujmij ciągi zawierające spacje lub ukośniki ("/") w cudzysłowie.

## <a name="example"></a>Przykład
 Ten przykład Wstawia znacznik o IDENTYFIKATORze 123 i nazwie znacznika "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
