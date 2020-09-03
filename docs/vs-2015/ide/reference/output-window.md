---
title: Okno Dane wyjściowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f17b91cc462b6f628100ffbf370fcdec2eb9888d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662194"
---
# <a name="output-window"></a>Okno wyniku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno **dane wyjściowe** może wyświetlać komunikaty o stanie dla różnych funkcji w zintegrowanym środowisku programistycznym (IDE). Aby otworzyć okno **dane wyjściowe** , na pasku menu wybierz polecenie **Widok/wyjście** (lub kliknij przycisk CTRL + ALT + O).

> [!WARNING]
> Okno dane wyjściowe nie pojawia się w menu Widok w wersjach Visual Studio Express. Aby je wyświetlić, użyj klawisza skrótu CTRL + ALT + O.

## <a name="toolbar"></a>Pasek narzędzi
 **Pokaż dane wyjściowe z** Wyświetla co najmniej jedno okienko danych wyjściowych do wyświetlenia. Kilka okienek informacji może być dostępnych w zależności od tego, które narzędzia w IDE używały okna **danych wyjściowych** do dostarczania komunikatów do użytkownika.

 **Znajdź komunikat w kodzie** Przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera wybrany błąd kompilacji.

 **Przejdź do poprzedniego komunikatu** Zmienia fokus w oknie **danych wyjściowych** na poprzedni błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd kompilacji.

 **Przejdź do następnego komunikatu** Zmienia fokus w oknie **danych wyjściowych** na następny błąd kompilacji i przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd kompilacji.

 **Wyczyść wszystko** Czyści cały tekst w okienku **danych wyjściowych** .

 **Przełącz Zawijanie wierszy** Włącza i wyłącza funkcję zawijania wyrazów w okienku **danych wyjściowych** . Gdy zawijanie wyrazów jest włączone, tekst w dłuższych wpisach wykraczających poza obszar wyświetlania jest wyświetlany w następującym wierszu.

## <a name="output-pane"></a>Okienko danych wyjściowych
 W okienku **dane** wyjściowe wybrane na liście **Pokaż dane wyjściowe z** wskazanego źródła danych zostaną wyświetlone dane wyjściowe.

## <a name="routing-messages-to-the-output-window"></a>Kierowanie komunikatów do Okno Dane wyjściowe
 Aby wyświetlić okno **danych wyjściowych** za każdym razem, gdy kompilujesz projekt, w oknie dialogowym **Ogólne, projekty i rozwiązania,** wybierz opcję **Pokaż okno dane wyjściowe po rozpoczęciu kompilacji**. Następnie przy otwartym pliku kodu do edycji wybierz przyciski **Przejdź do następnej wiadomości** i **Przejdź do poprzedniego komunikatu** na pasku narzędzi okna **danych wyjściowych** , aby wybrać pozycje w okienku **dane wyjściowe** . W takim przypadku punkt wstawiania w edytorze kodu przechodzi do wiersza kodu, w którym występuje wybrany problem.

 Niektóre funkcje i polecenia środowiska IDE wywoływane w [oknie poleceń](../../ide/reference/command-window.md) dostarczają ich dane wyjściowe do okna **danych wyjściowych** . Dane wyjściowe z zewnętrznych narzędzi, takich jak pliki bat i. com, które są zwykle wyświetlane w oknie wiersza polecenia, są kierowane do okienka **danych wyjściowych** po wybraniu opcji **Użyj okno dane wyjściowe** w obszarze [Zarządzanie narzędziami zewnętrznymi](../../ide/managing-external-tools.md). Wiele innych rodzajów komunikatów można również wyświetlać w okienkach **danych wyjściowych** . Na przykład, gdy składnia Transact-SQL w procedurze składowanej jest sprawdzana względem docelowej bazy danych, wyniki są wyświetlane w oknie **dane wyjściowe** .

 Możesz również zaprogramować własne aplikacje w celu zapisywania komunikatów diagnostycznych w czasie wykonywania w okienku **danych wyjściowych** . W tym celu należy użyć elementów członkowskich <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy w <xref:System.Diagnostics> przestrzeni nazw biblioteki klas .NET Framework. Elementy członkowskie <xref:System.Diagnostics.Debug> klasy wyświetlają dane wyjściowe podczas tworzenia konfiguracji debugowania rozwiązania lub projektu; elementy członkowskie <xref:System.Diagnostics.Trace> klasy wyświetlają dane wyjściowe podczas kompilowania konfiguracji debugowania lub wersji. Aby uzyskać więcej informacji, zobacz [komunikaty diagnostyczne w okno dane wyjściowe](../../debugger/diagnostic-messages-in-the-output-window.md).

 W programie [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] można tworzyć niestandardowe kroki kompilacji i zdarzenia kompilacji, których ostrzeżenia i błędy są wyświetlane i zliczane w okienku **danych wyjściowych** . Naciskając klawisz F1 w wierszu danych wyjściowych, można wyświetlić odpowiedni temat pomocy. Aby uzyskać więcej informacji, zobacz [Formatowanie danych wyjściowych niestandardowego kroku kompilacji lub zdarzenia kompilacji](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).

## <a name="scrolling-behavior"></a>Zachowanie przewijania
 Jeśli używasz autoprzewijania w oknie danych wyjściowych, a następnie nawiguj za pomocą klawiszy myszy lub strzałek, Autoprzewijanie zostanie zatrzymane. Aby wznowić Autoprzewijanie, naciśnij klawisze CTRL + END.

## <a name="see-also"></a>Zobacz też
 [Komunikaty diagnostyczne w okno dane wyjściowe](../../debugger/diagnostic-messages-in-the-output-window.md) [instrukcje: kontrolowanie okno dane wyjściowe](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858) [kompilowania i kompilowania](../../ide/compiling-and-building-in-visual-studio.md) [informacji o bibliotece klas](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157) [konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
