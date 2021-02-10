---
title: Okno wyniku
description: Informacje o oknie danych wyjściowych i sposobie wyświetlania komunikatów o stanie dla różnych funkcji w środowisku IDE.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bdbaf79a3700a1ba1c0574e345093af25608e39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932049"
---
# <a name="output-window"></a>Okno wyniku

W oknie **dane wyjściowe** są wyświetlane komunikaty o stanie dla różnych funkcji w zintegrowanym środowisku programistycznym (IDE). Aby otworzyć okno **dane wyjściowe** , na pasku menu wybierz polecenie **Wyświetl**  >  **dane wyjściowe** lub naciśnij **klawisze CTRL** + **Alt** + **O**.

## <a name="toolbar"></a>Pasek narzędzi

Następujące kontrolki są wyświetlane na pasku narzędzi okna **dane wyjściowe** .

### <a name="show-output-from"></a>Pokaż dane wyjściowe z

Wyświetla co najmniej jedno okienko danych wyjściowych do wyświetlenia. Kilka okienek informacji może być dostępnych w zależności od tego, które narzędzia w IDE używały okna **danych wyjściowych** do dostarczania komunikatów do użytkownika.

### <a name="find-message-in-code"></a>Znajdź komunikat w kodzie

Przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera wybrany błąd kompilacji.

### <a name="go-to-previous-message"></a>Przejdź do poprzedniego komunikatu

Zmienia fokus w oknie **danych wyjściowych** na poprzedni błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd kompilacji.

### <a name="go-to-next-message"></a>Przejdź do następnego komunikatu

Zmienia fokus w oknie **danych wyjściowych** na następny błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd kompilacji.

### <a name="clear-all"></a>Wyczyść wszystkie

Czyści cały tekst w okienku **danych wyjściowych** .

### <a name="toggle-word-wrap"></a>Przełącz Zawijanie wierszy

Włącza i wyłącza funkcję zawijania wyrazów w okienku **danych wyjściowych** . Gdy zawijanie wyrazów jest włączone, tekst w dłuższych wpisach wykraczających poza obszar wyświetlania jest wyświetlany w następującym wierszu.

## <a name="output-pane"></a>Okienko danych wyjściowych

W okienku **dane** wyjściowe wybrane na liście **Pokaż dane wyjściowe z** wskazanego źródła danych zostaną wyświetlone dane wyjściowe.

## <a name="route-messages-to-the-output-window"></a>Kierowanie komunikatów do okna danych wyjściowych

Aby wyświetlić okno **danych wyjściowych** za każdym razem, gdy kompilujesz projekt, w oknie dialogowym **Opcje** na stronie Ogólne **projekty i rozwiązania**  >   wybierz pozycję **Pokaż okno dane wyjściowe po rozpoczęciu kompilacji**. Następnie przy otwartym pliku kodu do edycji wybierz pozycję **Przejdź do następnej wiadomości** i **Przejdź do poprzedniej wiadomości** na pasku narzędzi okna **danych wyjściowych** , aby wybrać pozycje w okienku **dane wyjściowe** . W takim przypadku punkt wstawiania w edytorze kodu przechodzi do wiersza kodu, w którym występuje wybrany problem.

Niektóre funkcje i polecenia środowiska IDE wywoływane w [okno polecenie](../../ide/reference/command-window.md) dostarczają dane wyjściowe do okna **danych wyjściowych** . Dane wyjściowe z zewnętrznych narzędzi, takich jak pliki *bat* i *. com* , które są zwykle wyświetlane w oknie poleceń, są kierowane do okienka **danych wyjściowych** po wybraniu opcji **Użyj okno dane wyjściowe** w obszarze [Zarządzaj narzędziami zewnętrznymi](../../ide/managing-external-tools.md). Wiele innych rodzajów komunikatów można również wyświetlać w okienkach **danych wyjściowych** . Na przykład, gdy składnia Transact-SQL w procedurze składowanej jest sprawdzana względem docelowej bazy danych, wyniki są wyświetlane w oknie **dane wyjściowe** .

Możesz również zaprogramować własne aplikacje w celu zapisywania komunikatów diagnostycznych w czasie wykonywania w okienku **danych wyjściowych** . W tym celu należy użyć elementów członkowskich <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy w <xref:System.Diagnostics> przestrzeni nazw interfejsu API platformy .NET. Elementy członkowskie <xref:System.Diagnostics.Debug> klasy wyświetlają dane wyjściowe podczas tworzenia konfiguracji debugowania rozwiązania lub projektu; elementy członkowskie <xref:System.Diagnostics.Trace> klasy wyświetlają dane wyjściowe podczas kompilowania konfiguracji debugowania lub wersji. Aby uzyskać więcej informacji, zobacz [komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md).

W języku C++ można utworzyć niestandardowe kroki kompilacji i zdarzenia kompilacji, których ostrzeżenia i błędy są wyświetlane i zliczane w okienku **danych wyjściowych** . Naciskając klawisz **F1** w wierszu danych wyjściowych, można wyświetlić odpowiedni temat pomocy. Aby uzyskać więcej informacji, zobacz [Formatowanie danych wyjściowych niestandardowego kroku kompilacji](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Zachowanie przewijania

Jeśli używasz autoprzewijania w oknie **danych wyjściowych** , a następnie nawiguj za pomocą klawiszy myszy lub strzałek, Autoprzewijanie zostanie zatrzymane. Aby wznowić Autoprzewijanie, naciśnij **klawisze CTRL** + .

## <a name="see-also"></a>Zobacz też

- [Komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Instrukcje: kontrolowanie okna danych wyjściowych](/previous-versions/ht6z4e28(v=vs.140))
- [Kompilowanie i tworzenie kompilacji](../../ide/compiling-and-building-in-visual-studio.md)
- [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
- [Omówienie biblioteki klas](/dotnet/standard/class-library-overview)