---
title: Oznacz | Microsoft Docs
description: Dowiedz się, jak opcja oznaczania VSPerfCmd.exe wstawia określone informacje do pliku danych profilowania.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 33a343be010a5bf9cc0d9ba3e4251d92fd720656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917814"
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

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
