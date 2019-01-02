---
title: Okno wyniku
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5121053ebb88d3c6c5bcbedbb2798daff3ad07f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836494"
---
# <a name="output-window"></a>Okno wyniku

**Dane wyjściowe** okno wyświetla komunikaty o stanie dla różnych funkcji w zintegrowanym środowisku programistycznym (IDE). Aby otworzyć **dane wyjściowe** okna, na pasku menu wybierz **widoku** > **dane wyjściowe**, lub naciśnij **Ctrl** +  **ALT**+**O**.

## <a name="toolbar"></a>Pasek narzędzi

Następujące elementy sterujące są wyświetlane na pasku narzędzi **dane wyjściowe** okna.

### <a name="show-output-from"></a>Pokaż dane wyjściowe

Wyświetla jeden lub więcej okienka danych wyjściowych, aby wyświetlić. Kilku okienek informacji mogą być dostępne, w zależności od używanych narzędzi, które w środowisku IDE **dane wyjściowe** okna w celu dostarczenia komunikatu do użytkownika.

### <a name="find-message-in-code"></a>Wyszukaj komunikat w kodzie

Przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd wybranej kompilacji.

### <a name="go-to-previous-message"></a>Przejdź do poprzedniej wiadomości

Zmienia fokusu w **dane wyjściowe** okna poprzedni błąd kompilacji i przenosi punkt wstawiania w edytorze kodu, aby wiersz zawierający błąd kompilacji.

### <a name="go-to-next-message"></a>Przejdź do następnej wiadomości

Zmienia fokusu w **dane wyjściowe** okna na następny błąd kompilacji i przenosi punkt wstawiania w edytorze kodu, aby wiersz zawierający błąd kompilacji.

### <a name="clear-all"></a>Wyczyść wszystko

Usuwa cały tekst z **dane wyjściowe** okienka.

### <a name="toggle-word-wrap"></a>Przełącz zawijanie wierszy

Włącza lub wyłącza funkcję zawijanie wyrazów **dane wyjściowe** okienka. Gdy zawijanie wyrazów jest włączona, tekst we wpisach dłużej wykracza poza obszar wyświetlania jest wyświetlany w wierszu.

## <a name="output-pane"></a>Okienko danych wyjściowych

**Dane wyjściowe** wybranego w okienku **Pokaż dane wyjściowe z** liście zostaną wyświetlone dane wyjściowe ze źródła, wskazane.

## <a name="route-messages-to-the-output-window"></a>Routing komunikatów w oknie danych wyjściowych

Aby wyświetlić **dane wyjściowe** okna zawsze wtedy, gdy tworzysz projekt, w **opcje** dialogowego na **projekty i rozwiązania** > **ogólne**  wybierz opcję **okno Pokaż dane wyjściowe, gdy rozpoczyna się kompilacja**. Następnie kod plik otwarty do edycji, wybierz **przejdź do następnej wiadomości** i **przejdź do poprzedniego komunikatu** na **dane wyjściowe** okna narzędzi, aby wybrać wpisy w  **Dane wyjściowe** okienka. Jak to punktu wstawiania w przechodzi edytora kodu do wiersza kodu, w której występuje problem wybranego.

Niektóre funkcje środowiska IDE i polecenia wywoływanego w [okna polecenia](../../ide/reference/command-window.md) dostarczaj swoje dane wyjściowe do **dane wyjściowe** okna. Dane wyjściowe z zewnętrznego narzędzia, takie jak *.bat* i *.com* pliki, które zwykle są wyświetlane w oknie wiersza polecenia, jest kierowany do **dane wyjściowe** okienko po wybraniu  **Okno danych wyjściowych** opcji [Zarządzanie narzędziami zewnętrznymi](../../ide/managing-external-tools.md). Wiele innych rodzajów komunikaty mogą być wyświetlane w **dane wyjściowe** także okienka. Na przykład po składni języka Transact-SQL w procedurze składowanej jest sprawdzana względem docelowej bazy danych, wyniki są wyświetlane w **dane wyjściowe** okna.

Można również zaprogramować aplikacje do zapisywania komunikatów diagnostycznych w czasie wykonywania dla **dane wyjściowe** okienka. Aby to zrobić, należy użyć elementów członkowskich <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy w <xref:System.Diagnostics> przestrzeni nazw w bibliotece klas programu .NET Framework. Elementy członkowskie <xref:System.Diagnostics.Debug> klasy dane wyjściowe podczas tworzenia konfiguracji debugowania z rozwiązania lub projektu; członkowie <xref:System.Diagnostics.Trace> klasy, dane wyjściowe podczas kompilowania konfiguracji Debug i Release. Aby uzyskać więcej informacji, zobacz [komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md).

W języku C++, można tworzyć niestandardowych kroków kompilacji i zdarzenia kompilacji, którego ostrzeżenia i błędy są wyświetlane i uwzględniane w **dane wyjściowe** okienka. Naciskając **F1** w wierszu danych wyjściowych, możesz wyświetlić odpowiedniego tematu Pomocy. Aby uzyskać więcej informacji, zobacz [formatowania danych wyjściowych niestandardowego kroku kompilacji](/cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Zachowanie przewijania

Jeśli używasz autoscrolling w **dane wyjściowe** okna, a następnie przejdź przy użyciu myszy lub klawiszy strzałek, zatrzymuje autoscrolling. Aby wznowić autoscrolling, naciśnij klawisz **Ctrl**+**zakończenia**.

## <a name="see-also"></a>Zobacz także

- [Komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Instrukcje: Kontrolowanie okna danych wyjściowych](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)
- [O konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)
- [Przegląd biblioteki klas](/dotnet/standard/class-library-overview)