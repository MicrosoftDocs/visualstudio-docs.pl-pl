---
title: Okno wyniku
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be028af8ab9f458c1fadad6f8b2fcbd6aaa49a04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567986"
---
# <a name="output-window"></a>Okno danych wyjściowych

Okno **Dane wyjściowe** wyświetla komunikaty o stanie dla różnych funkcji w zintegrowanym środowisku programistycznym (IDE). Aby otworzyć okno **Dane wyjściowe,** na pasku menu wybierz pozycję **Wyświetl** > **dane wyjściowe**lub naciśnij klawisz **Ctrl**+**Alt**+**O**.

## <a name="toolbar"></a>Pasek narzędzi

Następujące formanty są wyświetlane na pasku narzędzi okna **Dane wyjściowe.**

### <a name="show-output-from"></a>Pokaż dane wyjściowe z

Wyświetla co najmniej jedno okienka danych wyjściowych do wyświetlenia. Kilka okienek informacji może być dostępnych, w zależności od tego, które narzędzia w IDE użyły **output** okna do dostarczania wiadomości do użytkownika.

### <a name="find-message-in-code"></a>Znajdź wiadomość w kodzie

Przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd kompilacji.

### <a name="go-to-previous-message"></a>Przejdź do poprzedniej wiadomości

Zmienia fokus w oknie **Dane wyjściowe** na poprzedni błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera ten błąd kompilacji.

### <a name="go-to-next-message"></a>Przejdź do następnej wiadomości

Zmienia fokus w oknie **Dane wyjściowe** do następnego błędu kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera ten błąd kompilacji.

### <a name="clear-all"></a>Wyczyść wszystko

Czyści cały tekst z okienka **Dane wyjściowe.**

### <a name="toggle-word-wrap"></a>Przełączanie zawijanie wyrazów

Włącza i wyłącza funkcję Zawijanie wyrazów w okienku **Dane wyjściowe.** Gdy zawijanie wyrazu jest włączone, tekst w dłuższych wpisach, który wykracza poza obszar wyświetlania, jest wyświetlany w następującym wierszu.

## <a name="output-pane"></a>Okienko wyjścia

Okienko **Dane wyjściowe** wybrane na liście **Pokaż dane wyjściowe z** wyświetla dane wyjściowe ze wskazanego źródła.

## <a name="route-messages-to-the-output-window"></a>Rozsyłanie wiadomości do okna Wyjście

Aby wyświetlić okno **Dane wyjściowe** przy każdym utworzeniu projektu, w oknie dialogowym **Opcje** na stronie**Ogólne** projekty i rozwiązania wybierz okno Pokaż dane **wyjściowe** >  **podczas rozpoczynania kompilacji**. Następnie po otwarciu pliku kodu do edycji wybierz pozycję **Przejdź do następnej wiadomości** i Przejdź do poprzedniej **wiadomości** na pasku narzędzi okno **Dane wyjściowe,** aby wybrać wpisy w okienku **Dane wyjściowe.** Jak to zrobić, punkt wstawiania w edytorze kodu przeskakuje do wiersza kodu, w którym występuje wybrany problem.

Niektóre funkcje IDE i polecenia wywoływane w [oknie polecenia](../../ide/reference/command-window.md) dostarczają swoje dane wyjściowe do okna **Dane wyjściowe.** Dane wyjściowe z narzędzi zewnętrznych, takich jak pliki *bat* i *.com,* które są zazwyczaj wyświetlane w oknie polecenia, są kierowane do okienka **Wyjście** po wybraniu opcji Użyj **okna wyjściowego** w obszarze Zarządzanie [narzędziami zewnętrznymi](../../ide/managing-external-tools.md). Wiele innych rodzajów komunikatów mogą być wyświetlane w **okienkach danych wyjściowych,** jak również. Na przykład gdy składnia Transact-SQL w procedurze składowanej jest sprawdzana w docelowej bazie danych, wyniki są wyświetlane w oknie **Dane wyjściowe.**

Można również zaprogramować własne aplikacje do pisania komunikatów diagnostycznych w czasie wykonywania do okienka **dane wyjściowe.** Aby to zrobić, należy <xref:System.Diagnostics.Debug> użyć <xref:System.Diagnostics.Trace> członków <xref:System.Diagnostics> klasy lub klasy w obszarze nazw interfejsu API platformy .NET. Elementy wyjściowe wyświetlania <xref:System.Diagnostics.Debug> klasy podczas tworzenia konfiguracji debugowania rozwiązania lub projektu; elementy wyjściowe wyświetlania <xref:System.Diagnostics.Trace> klasy podczas tworzenia konfiguracji debugowania lub wydania. Aby uzyskać więcej informacji, zobacz [Komunikaty diagnostyczne w oknie Dane wyjściowe](../../debugger/diagnostic-messages-in-the-output-window.md).

W języku C++ można tworzyć kroki kompilacji niestandardowej i tworzyć zdarzenia, których ostrzeżenia i błędy są wyświetlane i liczone w okienku **dane wyjściowe.** Naciskając **klawisz F1** na linii wyjściowej, można wyświetlić odpowiedni temat pomocy. Aby uzyskać więcej informacji, zobacz [Formatowanie danych wyjściowych niestandardowego kroku kompilacji](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Zachowanie przewijania

Jeśli używasz automatycznego przewlecowania w oknie **Dane wyjściowe,** a następnie nawigujesz za pomocą myszy lub klawiszy strzałek, automatyczne przewijanie zatrzymuje się. Aby wznowić automatyczne przewiszanie, naciśnij klawisz **Ctrl**+**End**.

## <a name="see-also"></a>Zobacz też

- [Komunikaty diagnostyczne w oknie Dane wyjściowe](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Jak: Sterowanie oknem Wyjście](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)
- [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
- [Omówienie biblioteki klas](/dotnet/standard/class-library-overview)
