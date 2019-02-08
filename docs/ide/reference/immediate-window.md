---
title: Okno bezpośrednie
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3947c2f16be4e5c0d8054e48a46981aa22475423
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931952"
---
# <a name="immediate-window"></a>Okno bezpośrednie

**Bezpośrednie** okno służy do debugowania i obliczać wyrażeń, wykonywania instrukcji, drukowania wartości zmiennych i tak dalej. Umożliwia wprowadzenie wyrażenia, aby je ocenić lub wykonać przy pomocy języka programowania podczas debugowania.

Aby wyświetlić **bezpośrednie** okna, otwórz projekt do edycji, a następnie wybierz **debugowania** > **Windows** > **bezpośrednie**  lub naciśnij **Ctrl**+**Alt**+**I**. Możesz też wprowadzić **Debug.Immediate** w **polecenia** okna.

Możesz użyć **bezpośrednie** okna, aby wydawać indywidualne polecenia programu Visual Studio. Dostępne polecenia obejmują `EvaluateStatement`, który może służyć do przypisywania wartości do zmiennych. **Bezpośrednie** okna obsługuje również technologię IntelliSense.

## <a name="display-the-values-of-variables"></a>Wyświetlanie wartości zmiennych

**Bezpośrednie** okno może być szczególnie przydatne podczas debugowania aplikacji. Na przykład, aby sprawdzić wartość zmiennej `varA`, możesz użyć [polecenie Drukuj](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Znak zapytania (?) jest aliasem `Debug.Print`, dlatego to polecenie można również zapisać:

```cmd
>? varA
```

Obie wersje to polecenie zwraca wartość zmiennej `varA`.

> [!TIP]
> Aby wydać polecenie program Visual Studio w **bezpośrednie** okna, należy poprzedzić polecenie a znak większości (>). Aby wprowadzić kilka poleceń, przełącz się do **polecenia** okna.

## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania

Możesz użyć **bezpośrednie** okna do wykonania funkcji lub podprocedury w czasie projektowania.

### <a name="execute-a-function-at-design-time"></a>Wykonać funkcję w czasie projektowania

1. Skopiuj następujący kod do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] konsoli aplikacji:

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

2. Na **debugowania** menu, kliknij przycisk **Windows**, a następnie kliknij przycisk **bezpośrednie**.

3. Typ `?MyFunction(2)` w **bezpośrednie** okna, a następnie naciśnij klawisz **Enter**.

    **Bezpośrednie** okno uruchamia `MyFunction` i wyświetla `4`.

Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio przerywa wykonywanie we właściwym miejscu. Można następnie użyć okien debugera do sprawdzenia stanu programu. Aby uzyskać więcej informacji, zobacz [instruktażu: Debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md).

Nie można użyć obliczenia wyrażenia czasu projektowania w typach projektów, które wymagają uruchamiania środowiska wykonawczego, w tym [!INCLUDE[trprVSTOshort](../../ide/reference/includes/trprvstoshort_md.md)] projektów, projektów sieci web, projektów urządzeń inteligentnych i projektów SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Obliczanie wyrażenia czasu projektowania w rozwiązaniach dotyczących wielu projektów

Podczas ustanawiania kontekstu oceny wyrażenia czasu projektowania, w programie Visual Studio odwołuje się do aktualnie wybranego projektu w Eksploratorze rozwiązań. Jeśli projekt nie jest zaznaczony w oknie Eksploratora rozwiązań, program Visual Studio próbuje obliczyć funkcję względu projektu startowego. Jeśli nie można obliczyć funkcji w bieżącym kontekście, otrzymasz komunikat o błędzie. Jeśli próbujesz obliczyć wartości funkcji w projekcie, który nie jest projektem startowym rozwiązania, a otrzymasz komunikat o błędzie, spróbuj wybrać projekt w Eksploratorze rozwiązań i ponownie dokonać obliczenia.

## <a name="enter-commands"></a>Wprowadzanie poleceń

Wprowadź znak większości (>) przy wydawaniu poleceń programu Visual Studio w **bezpośrednie** okna. Użyj **Strzałka w górę** i **Strzałka w dół** klucze do przewijania wcześniej wydanych poleceń.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Ocena wyrażenia.|Należy poprzedzić wyrażenie znakiem zapytania (?).|`? a+b`|
|Tymczasowo przejdź do trybu poleceń, będąc w trybie bezpośrednim (Aby wykonać jedno polecenie).|Wprowadź polecenie prefacing go o rozmiarze większym niż znak większości (>).|`>alias`|
|Przełącz do okna wiersza polecenia.|Wprowadź `cmd` prefacing go w oknie o rozmiarze większym niż znak większości (>).|`>cmd`|
|Przejdź z powrotem do okna bezpośredniego.|Wprowadź `immed` do okna bez znaku większości (>).|`immed`|

## <a name="mark-mode"></a>Tryb oznaczania

Po kliknięciu dowolnego poprzedniego wiersza w **bezpośrednie** okna, nastąpi automatyczne przejście w tryb oznaczania. Dzięki temu można wybrać, edytować i skopiować tekst z poprzedniego polecenia, ponieważ w dowolnym edytorze tekstów i wkleić je do bieżącego wiersza.

## <a name="the-equals-sign-"></a>Znak równości (=)

Okno służące do wprowadzania `EvaluateStatement` polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.

W **bezpośrednie** okna, znak równości (=) jest interpretowany jako operator przypisania. Tak na przykład polecenie

```cmd
>Debug.EvaluateStatement(varA=varB)
```

przypisuje wartość zmiennej `varB` do zmiennej `varA`.

W **polecenia** okna, z drugiej strony, znak równości (=) jest interpretowany jako operator porównania. Nie można użyć operacji przypisania w **polecenia** okna. Na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, a następnie polecenie

```cmd
>Debug.EvaluateStatement(varA=varB)
```

Zwraca wartość `False`.

## <a name="first-chance-exception-notifications"></a>Powiadomienia o wyjątkach pierwszej szansy

W niektórych konfiguracjach ustawień powiadomienia o wyjątkach pierwszej szansy są wyświetlane w **bezpośrednie** okna.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Przełącz powiadomień o wyjątkach pierwszej szansy w oknie bezpośrednim

1. Na **widoku** menu, kliknij przycisk **Windows inne**i kliknij przycisk **dane wyjściowe**.

2. Kliknij prawym przyciskiem myszy obszar tekstu **dane wyjściowe** okna, a następnie zaznacz lub odznacz opcję **komunikaty o wyjątkach**.

## <a name="see-also"></a>Zobacz także

- [Nawigowanie po kodzie za pomocą debugera](../../debugger/navigating-through-code-with-the-debugger.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Przewodnik: Debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Używanie wyrażeń regularnych w programie Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
