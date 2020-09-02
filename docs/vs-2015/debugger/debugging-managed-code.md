---
title: Debugowanie kodu zarządzanego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39076459f684aafce4e800ecad6341d120aac480
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691446"
---
# <a name="debugging-managed-code"></a>Debugowanie zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji opisano typowe problemy z debugowaniem i techniki dla aplikacji zarządzanych lub aplikacje w językach przeznaczonych dla środowiska uruchomieniowego języka wspólnego, takie jak Visual Basic, C# i C++. Opisane poniżej techniki są technikami wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [Korzystanie z debugera](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Komunikaty diagnostyczne w oknie danych wyjściowych](../debugger/diagnostic-messages-in-the-output-window.md)  
 Opisuje <xref:System.Diagnostics.Debug> klasy i <xref:System.Diagnostics.Trace> , za pomocą których można zapisywać komunikaty w czasie wykonywania w oknie **danych wyjściowych** . Te klasy obejmują metody wyjściowe, które umożliwiają włączenie informacji wyjściowych bez przerywania wykonywania i informacji wyjściowych, które również przerywają wykonywanie w przypadku niepowodzenia określonego warunku.  
  
 [Potwierdzenia w zarządzanym kodzie](../debugger/assertions-in-managed-code.md)  
 Opisuje potwierdzenia w kodzie zarządzanym, które warunki testowe należy określić jako argumenty `Assert` metod. Ponadto w tym temacie przedstawiono przykładowy kod, informacje na temat używania <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> metod klasy, zagadnienia dotyczące debugowania i wydań wersji kodu, efektów ubocznych, argumentów potwierdzenia, dostosowywania zachowania potwierdzenia i plików konfiguracji.  
  
 [Instrukcje stop w Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Zawiera opis `Stop` instrukcji, która stanowi alternatywę dla ustawienia punktu przerwania. Podano również przykładowy kod wraz z porównaniami między `Stop` instrukcją i `End` instrukcją, a także między `Stop` i `Assert` instrukcją.  
  
 [Przewodnik: Debugowanie formularza Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)  
 Zawiera instrukcje krok po kroku dotyczące tworzenia formularza systemu Windows i debugowania tego formularza. Formularz systemu Windows, standardowy składnik zarządzanej aplikacji systemu Windows, jest jednym z najczęściej używanych aplikacji zarządzanych. W tym instruktażu wykorzystano Visual C# i Visual Basic, ale techniki tworzenia formularza systemu Windows za pomocą języka C++ są zwykle podobne.  
  
 [Debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md)  
 Zawiera przykłady kodu, które umożliwiają debugowanie `OnStart` metody zarządzanej usługi systemu Windows. Aby debugować `OnStart` metodę usługi systemu Windows, należy dodać kilka wierszy kodu w celu symulowania usługi.  
  
 [Debugowanie w trybie mieszanym](../debugger/debugging-mixed-mode-applications.md)  
 Omawia debugowanie aplikacji w trybie mieszanym. Oznacza to, że wszystkie aplikacje łączące kod natywny z kodem zarządzanym.  
  
 [Błąd: debugowanie nie jest możliwe, ponieważ w systemie jest włączony debuger jądra](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Opisuje komunikat o błędzie, który występuje w przypadku próby debugowania kodu zarządzanego w systemie,, [!INCLUDE[win7](../includes/win7-md.md)] [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] [!INCLUDE[winxp](../includes/winxp-md.md)] , [!INCLUDE[Win2kFamily](../includes/win2kfamily-md.md)] lub systemu Windows NT, który został uruchomiony w trybie debugowania.  
  
 [Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md)  
 Opisuje skutki optymalizacji JIT podczas debugowania.  
  
 [Debugowanie LINQ i DLINQ](../debugger/debugging-linq.md)  
 Omawia techniki debugowania zapytań LINQ.  
  
 [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Opisuje sposób używania okienek **zadań równoległych** i **stosów równoległych** do debugowania aplikacji równoległej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [IntelliTrace](../debugger/intellitrace.md)  
 Wykrywaj błędy szybciej i łatwiej, rejestrując historię wykonywania aplikacji za pomocą IntelliTrace. Przechodzenie do tyłu i do przodu przez zarejestrowane zdarzenia i wywołania w celu sprawdzenia stanu aplikacji w czasie. Debuguj kod bez ustawiania wielu punktów przerwania lub ponownego uruchamiania aplikacji. Wymaga Visual Studio Ultimate.  
  
 [Śledzenie i instrumentowanie aplikacji](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)  
 Opisuje śledzenie, sposób monitorowania wykonywania aplikacji podczas jej działania oraz instrumentacji, która polega na umieszczeniu instrukcji Trace w strategicznych lokalizacjach w kodzie. Ten temat zawiera również linki do wprowadzenia do Instrumentacji i śledzenia, przełączników śledzenia, detektorów śledzenia, kodu śledzenia w aplikacji, dodawania instrukcji śledzenia do kodu aplikacji i kompilowania warunkowo z <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> .  
  
 [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982)  
 Opisuje opcję konsolidatora, która dodaje <xref:System.Diagnostics.DebuggableAttribute> do kodu pisanego przy użyciu języka C++. Ten atrybut jest wymagany do korzystania z funkcji debugowania, takich jak Attach with C++.  
  
 [Debugowanie aplikacji usługi systemu Windows](https://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2)  
 Zawiera informacje dotyczące debugowania aplikacji usługi systemu Windows, w tym konfigurowania, dołączania do procesu, debugowania kodu w `OnStart` metodzie usługi i kodu w metodzie Main, ustawiania punktów przerwania i korzystania z Menedżera sterowania usługami do uruchamiania, zatrzymywania, wstrzymywania i kontynuowania usługi.  
  
 [Debugowanie i profilowanie](https://msdn.microsoft.com/library/4a04863e-2475-46f4-bc3f-3c11510c2a4b)  
 W tym artykule omówiono debugowanie .NET Framework aplikacji i wymagania dotyczące konfiguracji.  
  
 [Debugowanie skryptów i aplikacji sieci Web](../debugger/debugging-web-applications-and-script.md)  
 Opisuje typowe problemy z debugowaniem i techniki, które można napotkać podczas debugowania skryptów i aplikacji sieci Web.  
 Opis nowych funkcji debugowania dodanych w tej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Strona główna debugowania](../debugger/debugging-in-visual-studio.md)  
 Zawiera łącza do większych sekcji dokumentacji debugowania. Informacje obejmują nowości w debugerze, ustawienia i przygotowania, punkty przerwania, obsługa wyjątków, edytowanie i kontynuowanie, debugowanie kodu zarządzanego, debugowanie Visual C++ projektów, debugowanie obiektów COM i ActiveX, debugowanie bibliotek DLL, debugowanie SQL i odwołania do interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](https://msdn.microsoft.com/library/1fd83ccd-3798-42fc-85a3-6cba99467387)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie w Visual Studio](../debugger/debugging-in-visual-studio.md)
