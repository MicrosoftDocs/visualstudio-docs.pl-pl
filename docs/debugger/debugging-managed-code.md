---
title: Debugowanie zarządzanego kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 92485f93bb4c2d1782f907acdb1e5252f611cdbe
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2018
ms.locfileid: "39179482"
---
# <a name="debugging-managed-code"></a>Debugowanie zarządzanego kodu

W tej sekcji omówiono typowe problemy z debugowania i technik dla zarządzanych aplikacji lub aplikacje napisane w językach przeznaczonych środowisko uruchomieniowe języka wspólnego, takich jak Visual Basic, C# i C++. Techniki opisane w tym miejscu są techniki wysokiego poziomu. Aby uzyskać więcej informacji, zobacz [za pomocą debugera](../debugger/getting-started-with-the-debugger.md).

## <a name="in-this-section"></a>W tej sekcji

[Komunikaty diagnostyczne w oknie danych wyjściowych](../debugger/diagnostic-messages-in-the-output-window.md)  
W tym artykule opisano <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> klas, za pomocą których można napisać komunikaty czasu wykonywania, aby **dane wyjściowe** okna. Te klasy zawierają metody danych wyjściowych, które umożliwiają informacji wyjściowych bez przerywania wynik wykonywania i informacje również przerywa wykonywanie, jeśli określony warunek zakończy się niepowodzeniem.

[Asercje w kodzie zarządzanym](../debugger/assertions-in-managed-code.md)  
W tym artykule opisano potwierdzenia w zarządzanym kodzie, których warunki, które określisz jako argumenty do badania `Assert` metody. Ponadto, ten temat zawiera przykładowy kod, informacje na temat korzystania z <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> metody klasy, zagadnienia dotyczące debugowania, jak i wydania wersji kodu, efekty uboczne assert argumentów, dostosowywanie assert zachowanie i plików konfiguracji.

[Instrukcje „Stop” w języku Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
W tym artykule opisano `Stop` instrukcji, co stanowi alternatywę dla ustawienie punktu przerwania. Przykładowy kod znajduje się również, wraz z porównania między `Stop` instrukcji i `End` instrukcji, jak również między `Stop` i `Assert` instrukcji.

[Przewodnik: debugowanie formularza Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)  
Zapewnia instrukcje krok po kroku dotyczące tworzenia formularzy Windows i debugowanie formularza. Formularz Windows, standardowy składnik zarządzanej aplikacji Windows, jest jednym z najczęściej używanych aplikacji zarządzanych. W tym instruktażu wykorzystano Visual C# i Visual Basic, ale techniki tworzenia formularzy Windows w języku C++ ogólnie wygląda podobnie.

[Debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md)  
Zawiera przykłady kodu, aby umożliwić debugowanie `OnStart` metody to zarządzana usługa Windows. Aby debugować `OnStart` metody usługi Windows, należy dodać kilka wierszy kodu, aby zasymulować usługi.

[Debugowanie w trybie mieszanym](../debugger/debugging-mixed-mode-applications.md)  
W tym artykule omówiono debugowanie aplikacji w trybie mieszanym. Oznacza to, każda aplikacja, która łączy kodu natywnego za pomocą kodu zarządzanego.

[Błąd: Debugowanie nie jest możliwe, ponieważ debuger jądra został wyłączony z poziomu systemu](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
W tym artykule opisano komunikat o błędzie występujący, jeśli zostanie podjęta próba debugowanie kodu zarządzanego na [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], lub systemu Windows NT, który został uruchomiony w trybie debugowania.

[Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md)  
Opisuje skutki optymalizację JIT na temat debugowania.

[Debugowanie LINQ i DLINQ](../debugger/debugging-linq.md)  
W tym artykule omówiono techniki debugowania zapytań LINQ.

[Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)  
Opisuje sposób używania **zadań równoległych** i **stosów równoległych** narzędzia systemu windows do debugowania aplikacji równoległej.

## <a name="related-sections"></a>Sekcje pokrewne

[IntelliTrace](../debugger/intellitrace.md) znajduj błędy szybciej i łatwiej, rejestrując historię wykonywania aplikacji za pomocą funkcji IntelliTrace. Krok do tyłu i przekazywać je za pośrednictwem zarejestrowane zdarzenia i wywołania, aby sprawdzić stan aplikacji w kluczowych punktach w czasie. Debugowanie kodu bez ustawiania wielu punktów przerwania lub ponownego uruchamiania aplikacji w taki sposób, jak często. Wymaga programu Visual Studio Enterprise.

[Śledzenie i instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
W tym artykule opisano, śledzenie, możesz monitorować wykonywanie aplikacji, gdy jest uruchomiona i instrumentacji, które obejmuje umieszczenie instrukcji śledzenia w lokalizacjach strategicznych w kodzie. Ten temat zawiera także łącza do wprowadzenie do Instrumentacji i śledzenia, przełączniki śledzenia, obiekty nasłuchujące śledzenia kodu w aplikacji, Dodawanie instrukcji śledzenia do kodu aplikacji i kompilowanie warunkowe ze śledzenia <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> .

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
Zawiera opis opcji konsolidatora, która dodaje <xref:System.Diagnostics.DebuggableAttribute> do kodu napisanego w języku C++. Ten atrybut jest potrzebnych do korzystania z debugowania funkcji, takich jak dołączanie przy użyciu języka C++.

[Debugowanie aplikacji usługi Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
Zawiera informacje dotyczące debugowania aplikacji usług Windows, w tym konfigurowania, dołączanie do procesu, debugowanie kodu w usłudze `OnStart` metodę i kod w metody Main, ustawiania punktów przerwania, a za pomocą kontroli usług Manager, aby uruchomić, zatrzymać, wstrzymać lub kontynuować usługę.

[Debugowanie i profilowanie](/dotnet/framework/debug-trace-profile/index)  
W tym artykule omówiono wymagania konfiguracji i debugowania aplikacji .NET Framework.

[Debugowanie skryptów i aplikacji sieci Web](../debugger/debugging-web-applications-and-script.md)  
Zawiera opis typowych problemów debugowania i technik, które można napotkać podczas debugowania skryptów i aplikacji sieci Web.

[Co nowego w debugerze programu Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
Opis nowych funkcji debugowania, dodane w tej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Debugowanie strony głównej](../debugger/debugger-feature-tour.md)  
Zawiera łącza do większych sekcji dokumentacji debugowania. Informacje dotyczące nowości w debugerze, ustawienia i przygotowania, punkty przerwania, obsługa wyjątków, Edytuj i Kontynuuj, debugowanie kodu zarządzanego, debugowania projektów Visual C++, debugowania modelu COM i ActiveX, debugowanie bibliotek DLL, debugowanie SQL, a użytkownik odwołania do interfejsu.

## <a name="see-also"></a>Zobacz także

[Wskazówki: Debugowanie niestandardowych Windows formantów formularzy w czasie projektowania](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[zabezpieczenia debugera](../debugger/debugger-security.md)
[debugowania w programie Visual Studio](../debugger/index.md) 
 [ Przewodnik po funkcjach debugera](../debugger/debugger-feature-tour.md)