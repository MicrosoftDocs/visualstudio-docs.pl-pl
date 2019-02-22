---
title: Mark | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 440401f8c46a3920fce6c8e0d29f630a24103f65
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625130"
---
# <a name="mark"></a>Znacznik
*VSPerfCmd.exe* **znacznik** Opcja wstawia określone informacje w pliku danych profilowania. Oznacz można wystawić w osobny raport VSPerfReport lub w widoku raportu znacznik programu profilującego interfejsu użytkownika. **Oznacz** może służyć do określania punkt początkowy i końcowy w filtry raportu i widok.

 **Znacznik** opcja musi być jedyną opcją, określone w wierszu polecenia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametry
 `MarkID` Zdefiniowane przez użytkownika liczba całkowita, która jest wymieniony jako identyfikator znacznika w raportach i widokach profilera. `MarkID` nie muszą być unikatowe.

 `MarkName` (Opcjonalnie) Ciąg zdefiniowany przez użytkownika, który jest wyświetlany jako nazwa znacznika w raportach i widokach profilera. Jeśli `MarkName` nie zostanie określony, pola Nazwa znacznika listy znak jest pusty. Należy ująć ciągów, które zawierają spacje lub kreski ułamkowe ("/") w znaki cudzysłowu.

## <a name="example"></a>Przykład
 W tym przykładzie wstawia znacznik identyfikator równą 123, i nazwę znacznika "TestMark".

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)