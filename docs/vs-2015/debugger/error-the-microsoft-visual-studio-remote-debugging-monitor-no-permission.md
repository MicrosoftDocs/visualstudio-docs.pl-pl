---
title: 'Błąd: Program Microsoft Visual Studio zdalny Monitor debugowania programu na komputerze zdalnym nie ma uprawnień do łączenia się z tym komputerem | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3ebc483c581d3283e6c2bd640144aef7554905
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777919"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Błąd: Monitor debugera zdalnego Microsoft Visual Studio na komputerze zdalnym nie ma uprawnień do połączenia z tym komputerem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten błąd występuje, gdy użytkownik, który próbuje uruchomić zdalny Monitor debugowania Visual Studio (msvsmon) nie ma konta na komputerze lokalnym.  
  
### <a name="to-fix-this-problem"></a>Aby rozwiązać ten problem  
  
- Dodaj konto użytkownika do komputera hosta debugera programu Visual Studio, z taką samą nazwę i hasło jako konta użytkownika uruchamiającego polecenie msvsmon na komputerze zdalnym  
  
   \- lub —  
  
- Uruchom polecenie msvsmon jako użytkownik, który ma uprawnienia do wywołania na komputerze lokalnym. Oznacza to, że użytkownik musi być użytkownikiem domeny oraz administratorem na komputerze polecenia msvsmon. Można określić konto użytkownika, uruchom polecenie msvsmon w jeden z dwóch sposobów:  
  
  - Kliknij prawym przyciskiem myszy ikonę msvsmon, a następnie wybierz **Uruchom jako** menu skrótów  
  
    \- lub —  
  
  - W wierszu polecenia Uruchom `runas.exe`.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdalne debugowanie między domenami](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)



