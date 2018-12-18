---
title: 'Porady: debugowanie z projektu DLL | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 61ccfc1fbf97dc36ed0625f95f998f9b154fd68c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796262"
---
# <a name="how-to-debug-from-a-dll-project"></a>Porady: debugowanie z projektu DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby rozpocząć debugowanie z projektu DLL, należy określić aplikacji wywołującej we właściwościach projektu. Strony właściwości C++ różnią się układ i zawartość w języku C# i Visual Basic strony właściwości.  
  
 Jeśli zarządzana biblioteka DLL jest wywoływana przez kod macierzysty i chcesz debugować oba, należy to określić, we właściwościach projektu. Aby uzyskać więcej informacji, zobacz [porady: debugowanie w trybie mieszanym](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
>  Nie można określić zewnętrznej aplikacji wywołującej, w wersjach Express programu Visual Studio. Zamiast tego możesz należy dodać projekt wykonywalny do rozwiązania, jest ustawiony jako projekt startowy i wywoływać metody w bibliotece DLL z projektu pliku wykonywalnego.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Aby określić aplikacji wywołującej w projekcie C++.  
  
1.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Przejdź do **debugowania** kartę.  
  
2.  Upewnij się, że **konfiguracji** polu w górnej części okna jest ustawiana **debugowania**.  
  
3.  Przejdź do **właściwości konfiguracji / debugowanie**.  
  
4.  W **debuger do uruchomienia** wybierz **lokalny debuger Windows** lub **zdalny debuger Windows**.  
  
5.  W **polecenia** lub **polecenia zdalnego** Dodaj nazwę w pełni kwalifikowaną ścieżkę aplikacji.  
  
6.  Dodaj argumenty programu niezbędne do **argumenty wiersza polecenia** pole.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Aby określić aplikacji wywołującej w projekcie języka C# lub Visual Basic  
  
1.  Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierz **właściwości**. Przejdź do **debugowania** kartę.  
  
     Wybierz **uruchomienia programu zewnętrznego**i Dodaj nazwę w pełni kwalifikowaną ścieżkę program do uruchomienia.  
  
     Jeśli musisz dodać argumenty wiersza polecenia programu zewnętrznego, dodaj je w **argumenty wiersza polecenia** pola.  
  
2.  Można również wywołać aplikacji jako adres URL. (Można to zrobić, Jeśli debugujesz zarządzaną bibliotekę DLL używane przez lokalnej aplikacji ASP.NET.)  
  
     W obszarze **Akcja uruchamiania**, wybierz opcję **uruchamiania przeglądarki w adresie URL:** przycisk radiowy, a następnie wypełnij adresu URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Aby rozpocząć debugowanie z projektu DLL  
  
1.  Ustaw punkty przerwania, zgodnie z potrzebami.  
  
2.  Rozpocznij debugowanie (naciśnij klawisz F5, kliknij zieloną strzałkę lub kliknij **debugowania / uruchamiania debugowania**).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie projektów DLL](../debugger/debugging-dll-projects.md)   
 [Ustawienia projektu dla języka C# konfiguracji debugowania](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Ustawienia projektu dla języka Visual Basic konfiguracji debugowania](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Ustawienia projektu dla konfiguracji debugowania w języku C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)



