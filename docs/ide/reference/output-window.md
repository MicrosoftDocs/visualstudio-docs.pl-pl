---
title: Okno wyniku
description: Dowiedz się więcej o oknie Dane wyjściowe i o tym, jak są wyświetlane komunikaty o stanie dla różnych funkcji w idee IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bbc6f33c439a812d7153f48d7f20d7e1d9dd3cb1
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925166"
---
# <a name="output-window"></a>Okno wyniku

W **oknie** Dane wyjściowe są wyświetlane komunikaty o stanie dla różnych funkcji w zintegrowanym środowisku projektowym (IDE). Aby otworzyć okno **Dane wyjściowe,** na pasku menu wybierz pozycję **Wyświetl** dane  >  **wyjściowe** lub naciśnij **klawisze Ctrl** + **Alt** + **O**.

## <a name="toolbar"></a>Pasek narzędzi

Poniższe kontrolki są wyświetlane na pasku narzędzi okna **Dane** wyjściowe.

### <a name="show-output-from"></a>Pokaż dane wyjściowe z

Wyświetla co najmniej jedno okienko danych wyjściowych do wyświetlenia. W zależności od tego, które narzędzia w idee użyły okna Dane wyjściowe do dostarczania komunikatów do użytkownika, może być dostępnych kilka okienek informacji. 

### <a name="find-message-in-code"></a>Znajdowanie komunikatu w kodzie

Przenosi punkt wstawiania w edytorze kodu do wiersza zawierającego wybrany błąd kompilacji.

### <a name="go-to-previous-message"></a>Przejdź do poprzedniej wiadomości

Zmienia fokus w oknie **Dane** wyjściowe na poprzedni błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza zawierającego ten błąd kompilacji.

### <a name="go-to-next-message"></a>Przejdź do następnego komunikatu

Zmienia fokus w oknie **Dane** wyjściowe na następny błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza zawierającego ten błąd kompilacji.

### <a name="clear-all"></a>Wyczyść wszystkie

Czyszczy cały tekst z **okienka** Dane wyjściowe.

### <a name="toggle-word-wrap"></a>Przełączanie zawijania wyrazów

Włącza i wyłącza funkcję zawijania wyrazów w **okienku** Dane wyjściowe. Gdy zawijanie wyrazów jest wł., tekst w dłuższych wpisach, który wykracza poza obszar wyświetlania, jest wyświetlany w poniższym wierszu.

## <a name="output-pane"></a>Okienko danych wyjściowych

Okienko **Dane** wyjściowe wybrane na liście **Pokaż dane wyjściowe z** wyświetla dane wyjściowe ze wskazanego źródła.

## <a name="route-messages-to-the-output-window"></a>Przekieruj komunikaty do okna Danych wyjściowych

Aby wyświetlić okno **Dane wyjściowe** przy każdej  kompilacji projektu, w oknie dialogowym Opcje na stronie Ogólne projekty i rozwiązania wybierz pozycję Pokaż okno Dane wyjściowe  >   podczas **uruchamiania kompilacji.** Następnie po otwarciu pliku kodu do edycji wybierz  pozycję **Przejdź** do  następnego komunikatu i przejdź do poprzedniej wiadomości na pasku narzędzi okna Dane wyjściowe, aby wybrać wpisy w **okienku Dane** wyjściowe. Gdy to zrobisz, punkt wstawiania w edytorze kodu przeskoczy do wiersza kodu, w którym występuje wybrany problem.

Niektóre funkcje i polecenia środowiska IDE wywoływane w okno Polecenie [dostarczają](../../ide/reference/command-window.md) dane wyjściowe do **okna Dane** wyjściowe. Dane wyjściowe z narzędzi zewnętrznych, takich jak *pliki.bat* i *.com,* które są zwykle  wyświetlane w oknie polecenia, są kierowane do okienka Dane wyjściowe po wybraniu opcji **Użyj** Okno Dane wyjściowe w oknie Zarządzanie narzędziami [zewnętrznymi.](../../ide/managing-external-tools.md) Wiele innych rodzajów komunikatów może być również **wyświetlanych** w okienkach danych wyjściowych. Na przykład gdy składnia języka Transact-SQL w procedurze składowanej jest sprawdzana względem docelowej bazy danych, wyniki są wyświetlane w **oknie Dane** wyjściowe.

Możesz również zaprogramować własne aplikacje, aby zapisywać komunikaty diagnostyczne w czasie uruchamiania w **okienku Dane** wyjściowe. W tym celu należy użyć składowych klasy <xref:System.Diagnostics.Debug> lub klasy w przestrzeni nazw <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> interfejsu API platformy .NET. Składowe klasy wyświetlają dane wyjściowe podczas kompilowania konfiguracji debugowania rozwiązania lub projektu; składowe klasy wyświetlają dane wyjściowe podczas kompilowania konfiguracji <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> debugowania lub wydania. Aby uzyskać więcej informacji, zobacz [Komunikaty diagnostyczne w oknie Dane wyjściowe](../../debugger/diagnostic-messages-in-the-output-window.md).

W języku C++ można tworzyć niestandardowe kroki kompilacji i zdarzenia kompilacji, których ostrzeżenia i błędy są wyświetlane i zliczane w **okienku Dane** wyjściowe. Naciskając **klawisz F1** w wierszu danych wyjściowych, można wyświetlić odpowiedni temat pomocy. Aby uzyskać więcej informacji, zobacz [Formatowanie danych wyjściowych niestandardowego kroku kompilacji](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Zachowanie przewijania

Jeśli używasz automatycznego wscrollowania w oknie Dane wyjściowe, a następnie nawiguj za pomocą myszy lub klawiszy strzałek, autoscrolling zatrzyma się.  Aby wznowić autoscrolling, naciśnij **klawisz Ctrl** + **End**.

## <a name="see-also"></a>Zobacz też

- [Komunikaty diagnostyczne w oknie Dane wyjściowe](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Jak kontrolować okno danych wyjściowych](/previous-versions/ht6z4e28(v=vs.140))
- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)
- [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
- [Omówienie biblioteki klas](/dotnet/standard/class-library-overview)