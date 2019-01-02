---
title: Oznacz | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3eec6ba541144628bf08afd79afb0bd691d1dbd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934813"
---
# <a name="mark"></a>Znacznik
*VSPerfCmd.exe* **znacznik** Opcja wstawia określone informacje w pliku danych profilowania. Oznacz można wystawić w osobny raport VSPerfReport lub w widoku raportu znacznik programu profilującego interfejsu użytkownika. **Oznacz** może służyć do określania punkt początkowy i końcowy w filtry raportu i widok.  
  
 **Znacznik** opcja musi być jedyną opcją, określone w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Zdefiniowane przez użytkownika liczba całkowita, która jest wymieniony jako identyfikator znacznika w raportach i widokach profilera. `MarkID` nie muszą być unikatowe.  
  
 `MarkName`  
 (Opcjonalnie) Ciąg zdefiniowany przez użytkownika, który jest wyświetlany jako nazwa znacznika w raportach i widokach profilera. Jeśli `MarkName` nie zostanie określony, pola Nazwa znacznika listy znak jest pusty. Należy ująć ciągów, które zawierają spacje lub kreski ułamkowe ("/") w znaki cudzysłowu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wstawia znacznik identyfikator równą 123, i nazwę znacznika "TestMark".  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)