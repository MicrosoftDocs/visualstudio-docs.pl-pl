---
title: Okno danych wyjściowych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7173abd87a9e7345e7d7caee02d2bb333f507514
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696061"
---
# <a name="output-window"></a>Okno wyniku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Dane wyjściowe** można wyświetlić w oknie komunikatów o stanie dla różnych funkcji w zintegrowanym środowisku programistycznym (IDE). Aby otworzyć **dane wyjściowe** okna, na pasku menu wybierz **widok/Output** (lub kliknij CTRL + ALT + O).  
  
> [!WARNING]
> W oknie danych wyjściowych nie są wyświetlane w menu Widok w wersjach programu Visual Studio Express. Aby wyświetlić go, należy użyć klawisza skrótu CTRL + ALT + O.  
  
## <a name="toolbar"></a>Pasek narzędzi  
 **Pokaż dane wyjściowe**  
 Wyświetla jeden lub więcej okienka danych wyjściowych, aby wyświetlić. Kilku okienek informacji mogą być dostępne, w zależności od używanych narzędzi, które w środowisku IDE **dane wyjściowe** okna w celu dostarczenia komunikatu do użytkownika.  
  
 **Wyszukaj komunikat w kodzie**  
 Przenosi punkt wstawiania w edytorze kodu do wiersza, który zawiera błąd wybranej kompilacji.  
  
 **Przejdź do poprzedniej wiadomości**  
 Zmienia fokusu w **dane wyjściowe** okna poprzedni błąd kompilacji i przenosi punkt wstawiania w edytorze kodu, aby wiersz zawierający błąd kompilacji.  
  
 **Przejdź do następnej wiadomości**  
 Zmienia fokusu w **dane wyjściowe** okna na następny błąd kompilacji i przenosi punkt wstawiania w edytorze kodu, aby wiersz zawierający błąd kompilacji.  
  
 **Wyczyść wszystko**  
 Usuwa cały tekst z **dane wyjściowe** okienka.  
  
 **Przełącz zawijanie wierszy**  
 Włącza lub wyłącza funkcję zawijanie wyrazów **dane wyjściowe** okienka. Gdy zawijanie wyrazów jest włączona, tekst we wpisach dłużej wykracza poza obszar wyświetlania jest wyświetlany w wierszu.  
  
## <a name="output-pane"></a>Okienko danych wyjściowych  
 **Dane wyjściowe** wybranego w okienku **Pokaż dane wyjściowe z** liście zostaną wyświetlone dane wyjściowe ze źródła, wskazane.  
  
## <a name="routing-messages-to-the-output-window"></a>Routing wiadomości do okna danych wyjściowych  
 Aby wyświetlić **dane wyjściowe** okna zawsze wtedy, gdy tworzysz projekt, w **ogólne, projekty i rozwiązania, opcje** okno dialogowe, wybierz opcję **okno Pokaż dane wyjściowe, gdy rozpoczyna się kompilacja**. Następnie kod plik otwarty do edycji, wybierz **przejdź do następnej wiadomości** i **przejdź do poprzedniego komunikatu** przyciski na **dane wyjściowe** okna narzędzi, aby wybrać wpisy w  **Dane wyjściowe** okienka. Jak to punktu wstawiania w przechodzi edytora kodu do wiersza kodu, w której występuje problem wybranego.  
  
 Niektóre funkcje środowiska IDE i polecenia wywoływanego w [okna polecenia](../../ide/reference/command-window.md) dostarczaj swoje dane wyjściowe do **dane wyjściowe** okna. Dane wyjściowe z zewnętrznych narzędzi, takich jak pliki bat i COM, który zazwyczaj jest wyświetlany w oknie wiersza polecenia jest kierowany do **dane wyjściowe** okienko po wybraniu **oknie danych wyjściowych** opcji [Zarządzanie narzędziami zewnętrznymi](../../ide/managing-external-tools.md). Wiele innych rodzajów komunikaty mogą być wyświetlane w **dane wyjściowe** także okienka. Na przykład po składni języka Transact-SQL w procedurze składowanej jest sprawdzana względem docelowej bazy danych, wyniki są wyświetlane w **dane wyjściowe** okna.  
  
 Można również zaprogramować aplikacje do zapisywania komunikatów diagnostycznych w czasie wykonywania dla **dane wyjściowe** okienka. Aby to zrobić, należy użyć elementów członkowskich <xref:System.Diagnostics.Debug> klasy lub <xref:System.Diagnostics.Trace> klasy w <xref:System.Diagnostics> przestrzeni nazw w bibliotece klas programu .NET Framework. Elementy członkowskie <xref:System.Diagnostics.Debug> klasy dane wyjściowe podczas tworzenia konfiguracji debugowania z rozwiązania lub projektu; członkowie <xref:System.Diagnostics.Trace> klasy, dane wyjściowe podczas kompilowania konfiguracji Debug i Release. Aby uzyskać więcej informacji, zobacz [komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 W [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], można tworzyć niestandardowych kroków kompilacji i zdarzenia kompilacji, którego ostrzeżenia i błędy są wyświetlane i uwzględniane w **dane wyjściowe** okienka. Przez naciśnięcie klawisza F1 w wierszu danych wyjściowych, możesz wyświetlić odpowiedniego tematu Pomocy. Aby uzyskać więcej informacji, zobacz [formatowanie danych wyjściowych niestandardowy krok budowania lub zdarzenia kompilacji](https://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).  
  
## <a name="scrolling-behavior"></a>Zachowanie przewijania  
 Jeśli używasz autoscrolling w oknie danych wyjściowych i następnie Nawiguj przy użyciu myszy lub klawiszy strzałek, zatrzymuje autoscrolling. Aby wznowić autoscrolling, naciśnij klawisze CTRL + END.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty diagnostyczne w oknie danych wyjściowych](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Instrukcje: Kontrolowanie okna danych wyjściowych](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Kompilowanie i tworzenie](../../ide/compiling-and-building-in-visual-studio.md)   
 [Ogólne informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)   
 [Omówienie biblioteki klas](https://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)
