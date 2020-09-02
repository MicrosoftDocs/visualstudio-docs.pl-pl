---
title: 'Instrukcje: debugowanie z projektu DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819169"
---
# <a name="how-to-debug-from-a-dll-project"></a>Porady: debugowanie z projektu DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby rozpocząć debugowanie projektu DLL, należy określić aplikację wywołującą we właściwościach projektu. Strony właściwości języka C++ różnią się w układ i zawartość ze stron właściwości C# i Visual Basic.  
  
 Jeśli zarządzana Biblioteka DLL jest wywoływana przez kod natywny i chcesz debugować obie te elementy, możesz określić ją we właściwościach projektu. Aby uzyskać więcej informacji, zobacz [jak: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> Nie można określić zewnętrznej aplikacji wywołującej w wersjach Express programu Visual Studio. Zamiast tego należy dodać projekt wykonywalny do rozwiązania, ustawić go jako projekt startowy i wywołać metody w bibliotece DLL z projektu wykonywalnego.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Aby określić aplikację wywołującą w projekcie języka C++  
  
1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Przejdź do karty **debugowanie** .  
  
2. Upewnij się, że pole **konfiguracji** w górnej części okna ma wartość **Debuguj**.  
  
3. Przejdź do pozycji **Właściwości konfiguracji/debugowanie**.  
  
4. Na liście **debuger do uruchomienia** wybierz **lokalny debuger systemu Windows** lub **zdalny debuger systemu Windows**.  
  
5. W oknie **polecenie** lub **polecenie zdalne** Dodaj w pełni kwalifikowaną nazwę ścieżki aplikacji.  
  
6. Dodaj wszelkie niezbędne argumenty programu do pola **argumenty polecenia** .  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Aby określić aplikację wywołującą w projekcie C# lub Visual Basic  
  
1. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Przejdź do karty **debugowanie** .  
  
     Wybierz pozycję **Uruchom program zewnętrzny**i Dodaj w pełni kwalifikowaną nazwę ścieżki programu do uruchomienia.  
  
     Jeśli musisz dodać argumenty wiersza polecenia programu zewnętrznego, Dodaj je w polu **argumenty wiersza polecenia** .  
  
2. Możesz również wywołać aplikację jako adres URL. (Możesz to zrobić w przypadku debugowania zarządzanej biblioteki DLL używanej przez lokalną aplikację ASP.NET).  
  
     W obszarze **Akcja początkowa**wybierz przycisk radiowy **Uruchom przeglądarkę w adresie URL:** , a następnie wprowadź adres URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Aby rozpocząć debugowanie z projektu DLL  
  
1. Ustaw punkty przerwania zgodnie z wymaganiami.  
  
2. Rozpocznij debugowanie (naciśnij klawisz F5, kliknij zieloną strzałkę lub kliknij pozycję **Debuguj/Rozpocznij debugowanie**).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Ustawienia projektu dla konfiguracji debugowania w C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
