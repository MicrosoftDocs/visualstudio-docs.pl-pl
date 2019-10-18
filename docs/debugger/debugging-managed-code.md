---
title: Debugowanie kodu zarządzanego | Microsoft Docs
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
ms.openlocfilehash: f6dd305b55e1ff7dd11b46f023906a8422b5504f
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72536050"
---
# <a name="debug-managed-code-c-visual-basic-f-ccli"></a>Debuguj kod zarządzany (C#, Visual Basic, F#, C++/CLI)

W tej sekcji opisano typowe problemy z debugowaniem i techniki dla aplikacji zarządzanych lub aplikacje w językach przeznaczonych dla środowiska uruchomieniowego języka wspólnego, takie C#jak Visual Basic C++, i/CLI. Opisane poniżej techniki są technikami wysokiego poziomu. [Najpierw Spójrz na debuger](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>W tej sekcji

[Komunikaty diagnostyczne w Okno Dane wyjściowe](../debugger/diagnostic-messages-in-the-output-window.md) \
Opisuje klasy <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace>, za pomocą których można zapisywać komunikaty w czasie wykonywania w oknie **danych wyjściowych** . Te klasy obejmują metody wyjściowe, które umożliwiają włączenie informacji wyjściowych bez przerywania wykonywania i informacji wyjściowych, które również przerywają wykonywanie w przypadku niepowodzenia określonego warunku.

[Potwierdzenia w kodzie zarządzanym](../debugger/assertions-in-managed-code.md) \
Opisuje potwierdzenia w kodzie zarządzanym, które warunki testowe należy określić jako argumenty metod `Assert`. Ponadto w tym temacie przedstawiono przykładowy kod, informacje o używaniu metod klasy <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace>, zagadnienia dotyczące debugowania i wydań wersji kodu, efektów ubocznych, argumentów potwierdzenia, dostosowywania zachowania potwierdzenia i plików konfiguracji.

[Instrukcje zatrzymania w Visual Basic](../debugger/stop-statements-in-visual-basic.md) \
Opisuje instrukcję `Stop`, która stanowi alternatywę dla ustawienia punktu przerwania. Podano również przykładowy kod wraz z porównaniami między instrukcją `Stop` a instrukcją `End`, jak również między `Stop` i `Assert` instrukcji.

[Przewodnik: debugowanie \ formularza systemu Windows](../debugger/walkthrough-debugging-a-windows-form.md)
Zawiera instrukcje krok po kroku dotyczące tworzenia formularza systemu Windows i debugowania tego formularza. Formularz systemu Windows, standardowy składnik zarządzanej aplikacji systemu Windows, jest jednym z najczęściej używanych aplikacji zarządzanych. W tym instruktażu C# są stosowane wizualizacje i Visual Basic, ale techniki tworzenia formularzy systemu C++ Windows za pomocą są zwykle podobne.

[Debugowanie metody OnStart](../debugger/how-to-debug-the-onstart-method.md) \
Zawiera przykłady kodu, które umożliwiają debugowanie metody `OnStart` zarządzanej usługi systemu Windows. Aby debugować metodę `OnStart` usługi systemu Windows, należy dodać kilka wierszy kodu w celu symulowania usługi.

[Debugowanie w trybie mieszanym](../debugger/debugging-mixed-mode-applications.md) \
Omawia debugowanie aplikacji w trybie mieszanym. Oznacza to, że wszystkie aplikacje łączące kod natywny z kodem zarządzanym.

[Błąd: debugowanie nie jest możliwe, ponieważ debuger jądra jest włączony w systemie](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) \
Opisuje komunikat o błędzie, który występuje w przypadku próby debugowania kodu zarządzanego na [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] lub systemu Windows NT, który został uruchomiony w trybie debugowania.

[Optymalizacja i debugowanie JIT](../debugger/jit-optimization-and-debugging.md) \
Opisuje skutki optymalizacji JIT podczas debugowania.

[Debugowanie \ LINQ i DLINQ](../debugger/debugging-linq.md)
Omawia techniki debugowania zapytań LINQ.

[Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md) \
Opisuje sposób używania okienek **zadań równoległych** i **stosów równoległych** do debugowania aplikacji równoległej.

## <a name="related-sections"></a>Sekcje pokrewne

[IntelliTrace](../debugger/intellitrace.md) \
Wykrywaj błędy szybciej i łatwiej, rejestrując historię wykonywania aplikacji za pomocą IntelliTrace. Przechodzenie do tyłu i do przodu przez zarejestrowane zdarzenia i wywołania w celu sprawdzenia stanu aplikacji w czasie. Debuguj kod bez ustawiania wielu punktów przerwania lub ponownego uruchamiania aplikacji. Wymaga Visual Studio Enterprise.

[Śledzenie i Instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) \
Opisuje śledzenie, sposób monitorowania wykonywania aplikacji podczas jej działania oraz instrumentacji, która polega na umieszczeniu instrukcji Trace w strategicznych lokalizacjach w kodzie. Ten temat zawiera również linki do wprowadzenia do Instrumentacji i śledzenia, przełączników śledzenia, detektorów śledzenia, śledzenia kodu w aplikacji, dodawania instrukcji śledzenia do kodu aplikacji i kompilowania warunku przy użyciu <xref:System.Diagnostics.Debug> i <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) \
Opisuje opcję konsolidatora, która dodaje <xref:System.Diagnostics.DebuggableAttribute> do kodu pisanego C++przy użyciu. Ten atrybut jest wymagany do korzystania z C++funkcji debugowania, takich jak Attach.

[Debugowanie aplikacji usługi systemu Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) \
Zawiera zagadnienia dotyczące debugowania aplikacji usługi systemu Windows, w tym konfigurowania, dołączania do procesu, debugowania kodu w metodzie `OnStart` usługi i kodu w metodzie Main, ustawiania punktów przerwania i korzystania z menedżera kontroli usług Uruchamianie, zatrzymywanie, wstrzymywanie i kontynuowanie usługi.

[Debugowanie i profilowanie](/dotnet/framework/debug-trace-profile/index) \
W tym artykule omówiono debugowanie aplikacji .NET i wymagania dotyczące konfiguracji.

[Debugowanie skryptów i aplikacji sieci Web](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) \
Opisuje typowe problemy z debugowaniem i techniki, które można napotkać podczas debugowania skryptów i aplikacji sieci Web.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)