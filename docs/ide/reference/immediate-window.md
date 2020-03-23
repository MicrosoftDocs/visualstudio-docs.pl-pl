---
title: Okno bezpośrednie
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b21cdb9136abe1e960e5b74bbf09e7d1694519d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568961"
---
# <a name="immediate-window"></a>Okno bezpośrednie

Okno **Natychmiastowe** służy do debugowania i oceny wyrażeń, wykonywania instrukcji i drukowania wartości zmiennych. Okno **Natychmiastowe** ocenia wyrażenia według tworzenia i używania aktualnie wybranego projektu.

Aby wyświetlić okno **Natychmiastowe,** otwórz projekt do edycji, a następnie wybierz polecenie **Debugowanie** > **systemu Windows** > **Immediate** lub naciśnij klawisz **Ctrl**+**Alt**+**I**. Można również wprowadzić **Debug.Immediate** w oknie **polecenia.**

Okno **Natychmiastowe** obsługuje technologię IntelliSense.

## <a name="display-the-values-of-variables"></a>Wyświetlanie wartości zmiennych

**Natychmiastowe** okno jest szczególnie przydatne podczas debugowania aplikacji. Na przykład, aby sprawdzić wartość `varA`zmiennej, można użyć [polecenia Drukuj:](../../ide/reference/print-command.md)

```cmd
>Debug.Print varA
```

Znak zapytania (?) jest aliasem dla `Debug.Print`, więc to polecenie może być również napisane:

```cmd
? varA
```

Obie wersje tego polecenia zwracają wartość `varA`zmiennej .

> [!TIP]
> Aby wydać polecenie programu Visual Studio w oknie **bezpośrednim,** należy poprzedzać polecenie znakiem większym niż (>). Aby wprowadzić wiele poleceń, przełącz się do [okna Polecenia](command-window.md).

## <a name="design-time-expression-evaluation"></a>Ocena wyrażenia w czasie projektowania

Za pomocą okna **Natychmiastowe** można wykonać funkcję lub podprocedury w czasie projektowania.

### <a name="execute-a-function-at-design-time"></a>Wykonywanie funkcji w czasie projektowania

1. Skopiuj następujący kod do aplikacji konsoli Visual Basic:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. W menu **Debugowania** wybierz polecenie**Natychmiastowy** **system Windows** > .

3. Wpisz `?MyFunction(2)` okno **Natychmiastowe** i naciśnij klawisz **Enter**.

    Okno **Natychmiastowe** jest uruchamiane `MyFunction` i wyświetlane `4`.

Jeśli funkcja lub podprocedura zawiera punkt przerwania, Visual Studio przerywa wykonanie w odpowiednim punkcie. Następnie można użyć okien debugera, aby sprawdzić stan programu. Aby uzyskać więcej informacji, zobacz [Instruktaż: Debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md).

Nie można używać oceny wyrażenia w czasie projektowania w typach projektów, które wymagają uruchomienia środowiska wykonywania, w tym Visual Studio Tools dla projektów pakietu Office, projektów sieci web, projektów urządzeń inteligentnych i projektów SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Ocena ekspresji w czasie projektowania w rozwiązaniach wieloprojektowych

Podczas ustanawiania kontekstu dla oceny wyrażenia w czasie projektowania visual studio odwołuje się do aktualnie wybranego projektu w Eksploratorze rozwiązań. Jeśli w Eksploratorze rozwiązań nie wybrano żadnego projektu, program Visual Studio podejmie próbę oceny funkcji względem projektu startowego. Jeśli funkcja nie może być oceniona w bieżącym kontekście, zostanie wyświetlony komunikat o błędzie. Jeśli próbujesz ocenić funkcję w projekcie, który nie jest projektem startowym dla rozwiązania i pojawia się błąd, spróbuj wybrać projekt w Eksploratorze rozwiązań i spróbuj ponownie ocenić.

## <a name="enter-commands"></a>Wprowadzanie poleceń

Wprowadź znak większy niż (>) podczas wydawania poleceń programu Visual Studio w oknie **Bezpośrednim.** Użyj **klawiszy strzałek w górę** i **strzałek w dół,** aby przewijać wcześniej używane polecenia.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Oceń wyrażenie.|Przedmową wyrażenie znakiem zapytania (?).|`? a+b`|
|Tymczasowo przejść do trybu dowodzenia w trybie natychmiastowym (aby wykonać jedno polecenie).|Wprowadź polecenie, wstępnie wstępne go znakiem większym niż znak (>).|`>alias`|
|Przełącz się do okna polecenia.|Wprowadź `cmd` do okna, prefacing go z większym niż znak (>).|`>cmd`|
|Przełącz się z powrotem do okna natychmiastowego.|Wprowadź `immed` do okna bez znaku większego niż (>).|`immed`|

## <a name="mark-mode"></a>Tryb oznaczania

Po kliknięciu dowolnego poprzedniego **wiersza** w oknie Natychmiastowy automatycznie przełączasz się w tryb oznaczania. Umożliwia to zaznaczanie, edytowanie i kopiowanie tekstu poprzednich poleceń, tak jak w dowolnym edytorze tekstu, i wklejania ich do bieżącego wiersza.

## <a name="examples"></a>Przykłady

W poniższym przykładzie przedstawiono cztery wyrażenia i ich wynik w **bezpośrednim** oknie dla projektu Języka Visual Basic.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>Powiadomienia o wyjątkach pierwszej szansy

W niektórych konfiguracjach ustawień powiadomienia o wyjątkach pierwszej szansy są wyświetlane w oknie **Natychmiastowy.**

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Przełączanie powiadomień o wyjątkach pierwszej szansy w oknie Natychmiastowy

1. W menu **Widok** kliknij polecenie **Inne okna**, a następnie kliknij polecenie **Dane wyjściowe**.

2. Kliknij prawym przyciskiem myszy obszar tekstowy okna **Dane wyjściowe,** a następnie zaznacz lub usuń **zaznaczenie opcji Komunikaty wyjątków**.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie za pomocą debugera](../../debugger/navigating-through-code-with-the-debugger.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Przewodnik: Debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Używanie wyrażeń regularnych w programie Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
