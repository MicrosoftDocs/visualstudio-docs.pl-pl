---
title: Znak | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4bf89469c4137052247b5a1fdfee7f8dc694fbcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773997"
---
# <a name="mark"></a>Znacznik
Opcja *VSPerfCmd.exe* **Mark** wstawia określone informacje do pliku danych profilowania. Oznaczyć może być wymieniony w osobnym raporcie VSPerfReport lub w widoku Mark Report interfejsu użytkownika profilera. **Znacznik** może służyć do określania punktów początkowych i końcowych w filtrach raportów i widoku.

 Opcja **Oznacz** musi być jedyną opcją określoną w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametry
 `MarkID`Zdefiniowana przez użytkownika liczba całkowita wymieniona jako identyfikator znaku w widokach i raportach profilera. `MarkID`nie musi być wyjątkowy.

 `MarkName`(Opcjonalnie) Ciąg zdefiniowany przez użytkownika, który jest wyświetlany jako Nazwa oznaczenia w widokach i raportach profilera. Jeśli `MarkName` nie zostanie określony, pole Oznacz nazwę listy znaczników jest puste. Łącz ciągi zawierające spacje lub ukośniki ("/") w cudzysłowie.

## <a name="example"></a>Przykład
 W tym przykładzie wstawia znacznik o identyfikatorze 123 i nazwę znaku "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
