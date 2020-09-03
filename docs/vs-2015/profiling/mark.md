---
title: Oznacz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d7902ec588af2687b048639a930847ec02b3fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155789"
---
# <a name="mark"></a>Znacznik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opcja **oznacz** VSPerfCmd.exe wstawia określone informacje do pliku danych profilowania. Znacznik może być wyświetlany w osobnym raporcie VSPerfReport lub w widoku raportu w interfejsie użytkownika profilera. **Znacznik** może służyć do określania punktów początkowych i końcowych w raportach i widokach filtrów.  
  
 Opcja **Oznacz** musi być jedyną opcją określoną w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Zdefiniowana przez użytkownika liczba całkowita, która jest wyświetlana jako identyfikator znacznika w widokach i raportach profilera. `MarkID` nie musi być unikatowy.  
  
 `MarkName`  
 Obowiązkowe Zdefiniowany przez użytkownika ciąg, który jest wyświetlany jako nazwa znacznika w widokach i raportach profilera. Jeśli `MarkName` nie jest określony, pole nazwa znacznika listy znaczników jest puste. Ujmij ciągi zawierające spacje lub ukośniki ("/") w cudzysłowie.  
  
## <a name="example"></a>Przykład  
 Ten przykład Wstawia znacznik o IDENTYFIKATORze 123 i nazwie znacznika "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowania aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
