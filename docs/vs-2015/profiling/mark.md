---
title: Oznacz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff40ac5db35927fad0fe28fe3c86c5411b5f5255
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769088"
---
# <a name="mark"></a>Znacznik
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **znacznik** Opcja wstawia określone informacje w pliku danych profilowania. Oznacz można wystawić w osobny raport VSPerfReport lub w widoku raportu znacznik programu profilującego interfejsu użytkownika. **Oznacz** może służyć do określania punkt początkowy i końcowy w filtry raportu i widok.  
  
 **Znacznik** opcja musi być jedyną opcją, określone w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametry  
 `MarkID`  
 Zdefiniowane przez użytkownika liczba całkowita, która jest wymieniony jako identyfikator znacznika w raportach i widokach profilera. `MarkID` nie muszą być unikatowe.  
  
 `MarkName`  
 (Opcjonalnie) Ciąg zdefiniowany przez użytkownika, który jest wyświetlany jako nazwa znacznika w raportach i widokach profilera. Jeśli `MarkName` nie zostanie określony, pola Nazwa znacznika listy znak jest pusty. Należy ująć ciągów, które zawierają spacje lub kreski ułamkowe ("/") w znaki cudzysłowu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wstawia znacznik identyfikator równą 123, i nazwę znacznika "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)



