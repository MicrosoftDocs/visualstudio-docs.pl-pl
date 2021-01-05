---
title: Debugowanie kodu zarządzanego | Microsoft Docs
description: Zobacz typowe problemy z debugowaniem i techniki w programie Visual Studio dla aplikacji zarządzanych lub aplikacje w językach przeznaczonych dla środowiska uruchomieniowego języka wspólnego.
ms.custom: SEO-VS-2020
ms.date: 09/23/2019
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e7dadfbc6a02382165b623aeff9d866e9edc975a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727024"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Debuguj kod zarządzany (C#, Visual Basic, F #, C++/CLI)

W tej sekcji opisano typowe problemy z debugowaniem i techniki dla aplikacji zarządzanych lub aplikacje w językach przeznaczonych dla środowiska uruchomieniowego języka wspólnego, takie jak Visual Basic, C# i C++/CLI. Opisane poniżej techniki są technikami wysokiego poziomu. [Najpierw Spójrz na debuger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>W tej sekcji

[Komunikaty diagnostyczne w Okno Dane wyjściowe](../debugger/diagnostic-messages-in-the-output-window.md)\
Opisuje <xref:System.Diagnostics.Debug> klasy i <xref:System.Diagnostics.Trace> , za pomocą których można zapisywać komunikaty w czasie wykonywania w oknie **danych wyjściowych** . Te klasy obejmują metody wyjściowe, które umożliwiają włączenie informacji wyjściowych bez przerywania wykonywania i informacji wyjściowych, które również przerywają wykonywanie w przypadku niepowodzenia określonego warunku.

[Potwierdzenia w kodzie zarządzanym](../debugger/assertions-in-managed-code.md)\
Opisuje potwierdzenia w kodzie zarządzanym, które warunki testowe należy określić jako argumenty `Assert` metod. Ponadto w tym temacie przedstawiono przykładowy kod, informacje na temat używania <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> metod klasy, zagadnienia dotyczące debugowania i wydań wersji kodu, efektów ubocznych, argumentów potwierdzenia, dostosowywania zachowania potwierdzenia i plików konfiguracji.

[Instrukcje stop w Visual Basic](../debugger/stop-statements-in-visual-basic.md)\
Zawiera opis `Stop` instrukcji, która stanowi alternatywę dla ustawienia punktu przerwania. Podano również przykładowy kod wraz z porównaniami między `Stop` instrukcją i `End` instrukcją, a także między `Stop` i `Assert` instrukcją.

[Przewodnik: debugowanie formularza systemu Windows](../debugger/walkthrough-debugging-a-windows-form.md)\
Zawiera instrukcje krok po kroku dotyczące tworzenia formularza systemu Windows i debugowania tego formularza. Formularz systemu Windows, standardowy składnik zarządzanej aplikacji systemu Windows, jest jednym z najczęściej używanych aplikacji zarządzanych. W tym instruktażu wykorzystano Visual C# i Visual Basic, ale techniki tworzenia formularza systemu Windows za pomocą języka C++ są zwykle podobne.

[Debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md)\
Zawiera przykłady kodu, które umożliwiają debugowanie `OnStart` metody zarządzanej usługi systemu Windows. Aby debugować `OnStart` metodę usługi systemu Windows, należy dodać kilka wierszy kodu w celu symulowania usługi.

[Debugowanie w trybie mieszanym](../debugger/debugging-mixed-mode-applications.md)\
Omawia debugowanie aplikacji w trybie mieszanym. Oznacza to, że wszystkie aplikacje łączące kod natywny z kodem zarządzanym.

[Błąd: debugowanie nie jest możliwe, ponieważ w systemie jest włączony debuger jądra](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
Opisuje komunikat o błędzie, który występuje w przypadku próby debugowania kodu zarządzanego w systemie,, [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] lub systemu Windows NT, który został uruchomiony w trybie debugowania.

[Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md)\
Opisuje skutki optymalizacji JIT podczas debugowania.

[Debugowanie LINQ i DLINQ](../debugger/debugging-linq.md)\
Omawia techniki debugowania zapytań LINQ.

[Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md)\
Opisuje sposób używania okienek **zadań równoległych** i **stosów równoległych** do debugowania aplikacji równoległej.

## <a name="related-sections"></a>Sekcje pokrewne

[IntelliTrace](../debugger/intellitrace.md)\
Wykrywaj błędy szybciej i łatwiej, rejestrując historię wykonywania aplikacji za pomocą IntelliTrace. Przechodzenie do tyłu i do przodu przez zarejestrowane zdarzenia i wywołania w celu sprawdzenia stanu aplikacji w czasie. Debuguj kod bez ustawiania wielu punktów przerwania lub ponownego uruchamiania aplikacji. Wymaga Visual Studio Enterprise.

[Śledzenie i Instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
Opisuje śledzenie, sposób monitorowania wykonywania aplikacji podczas jej działania oraz instrumentacji, która polega na umieszczeniu instrukcji Trace w strategicznych lokalizacjach w kodzie. Ten temat zawiera również linki do wprowadzenia do Instrumentacji i śledzenia, przełączników śledzenia, detektorów śledzenia, kodu śledzenia w aplikacji, dodawania instrukcji śledzenia do kodu aplikacji i kompilowania warunkowo z <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace> .

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
Opisuje opcję konsolidatora, która dodaje <xref:System.Diagnostics.DebuggableAttribute> do kodu pisanego przy użyciu języka C++. Ten atrybut jest wymagany do korzystania z funkcji debugowania, takich jak Attach with C++.

[Debugowanie aplikacji usługi systemu Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Zawiera informacje dotyczące debugowania aplikacji usługi systemu Windows, w tym konfigurowania, dołączania do procesu, debugowania kodu w `OnStart` metodzie usługi i kodu w metodzie Main, ustawiania punktów przerwania i korzystania z Menedżera sterowania usługami do uruchamiania, zatrzymywania, wstrzymywania i kontynuowania usługi.

[Debugowanie i profilowanie](/dotnet/framework/debug-trace-profile/index)\
W tym artykule omówiono debugowanie aplikacji .NET i wymagania dotyczące konfiguracji.

[Debugowanie skryptów i aplikacji sieci Web](how-to-enable-debugging-for-aspnet-applications.md)\
Opisuje typowe problemy z debugowaniem i techniki, które można napotkać podczas debugowania skryptów i aplikacji sieci Web.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)