---
title: Okno bezpośrednie
description: Dowiedz się, jak używać okna bezpośredniego do debugowania i obliczania wyrażeń, wykonywania instrukcji i drukowania wartości zmiennych.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73d3d2cc42e958c59ef058a1f69921145ea18475
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852482"
---
# <a name="immediate-window"></a>Okno bezpośrednie

Użyj okna **bezpośredniego** do debugowania i szacowania wyrażeń, wykonywania instrukcji i drukowania wartości zmiennych. Okno **bezpośrednie** szacuje wyrażenia przez skompilowanie i użycie aktualnie wybranego projektu.

Aby wyświetlić okno **bezpośrednie** , Otwórz projekt do edycji, a następnie wybierz polecenie **Debuguj**  >  **okna**  >  **natychmiast** lub naciśnij **klawisze CTRL** + **Alt** + **I**. Możesz również wprowadzić **Debug. Immediate** w oknie **poleceń** .

Okno **bezpośrednie** obsługuje funkcję IntelliSense.

## <a name="display-the-values-of-variables"></a>Wyświetlanie wartości zmiennych

Okno **bezpośrednie** jest szczególnie przydatne podczas debugowania aplikacji. Na przykład, aby sprawdzić wartość zmiennej `varA` , można użyć [polecenia Print](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Znak zapytania (?) jest aliasem dla `Debug.Print` , więc można także napisać to polecenie:

```cmd
? varA
```

Obie wersje tego polecenia zwracają wartość zmiennej `varA` .

> [!TIP]
> Aby wydać polecenie programu Visual Studio w oknie **bezpośrednim** , należy poprzedzić polecenie znakiem większości (>). Aby wprowadzić wiele poleceń, przełącz się do [okno polecenie](command-window.md).

## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażeń czasu projektowania

Za pomocą okna **bezpośredniego** można wykonać funkcję lub procedurę podprocedury w czasie projektowania.

### <a name="execute-a-function-at-design-time"></a>Wykonaj funkcję w czasie projektowania

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

2. W menu **Debuguj** wybierz pozycję **Windows**  >  **natychmiastowe**.

3. Wpisz `?MyFunction(2)` w oknie **bezpośrednim** , a następnie naciśnij klawisz **Enter**.

    Okno **natychmiastowe** uruchamia `MyFunction` i wyświetla `4` .

Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio przerywa wykonywanie w odpowiednim punkcie. Można następnie użyć okien debugera do sprawdzenia stanu programu. Aby uzyskać więcej informacji, zobacz [Przewodnik: debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md).

Nie można użyć oceny wyrażenia czasu projektowania w typach projektów, które wymagają uruchomienia środowiska wykonawczego, w tym Visual Studio Tools dla projektów pakietu Office, projektów sieci Web, projektów urządzeń inteligentnych i projektów SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Obliczanie wyrażeń w czasie projektowania w rozwiązaniach z obsługą kilku projektów

Podczas ustanawiania kontekstu oceny wyrażenia czasu projektowania program Visual Studio odwołuje się do aktualnie wybranego projektu w Eksplorator rozwiązań. Jeśli nie wybrano projektu w Eksplorator rozwiązań, program Visual Studio próbuje oszacować funkcję względem projektu startowego. Jeśli funkcja nie może być oceniona w bieżącym kontekście, zostanie wyświetlony komunikat o błędzie. Jeśli próbujesz ocenić funkcję w projekcie, który nie jest projektem startowym rozwiązania i wystąpi błąd, spróbuj wybrać projekt w Eksplorator rozwiązań i ponownie spróbować wykonać próbę.

## <a name="enter-commands"></a>Wprowadź polecenia

Wprowadź znak większości (>) podczas wydawania poleceń programu Visual Studio w oknie **bezpośrednim** . Użyj klawiszy Strzałka w **górę** i **Strzałka w dół** , aby przewijać wcześniej użyte polecenia.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Oceń wyrażenie.|Oznacz wyrażenie znakiem zapytania (?).|`? a+b`|
|Tymczasowe wprowadzanie trybu polecenia w trybie bezpośrednim (aby wykonać pojedyncze polecenie).|Wprowadź polecenie, umieszczając je na znaku większości (>).|`>alias`|
|Przełącz się do okno Polecenie.|Wprowadź `cmd` do okna, umieszczając go na znaku większości (>).|`>cmd`|
|Przełącz się z powrotem do okna bezpośredniego.|Wprowadź `immed` do okna bez znaku większości (>).|`immed`|

## <a name="mark-mode"></a>Tryb oznaczania

Po kliknięciu dowolnego poprzedniego wiersza w oknie **bezpośrednim** zostanie ono automatycznie przesunięte do trybu oznaczania. Dzięki temu można wybrać, edytować i skopiować tekst poprzednich poleceń tak samo jak w dowolnym edytorze tekstów i wkleić je do bieżącego wiersza.

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje cztery wyrażenia i ich wyniki w oknie **bezpośrednim** dla projektu Visual Basic.

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

W niektórych konfiguracjach ustawień powiadomienia o wyjątkach pierwszej szansy są wyświetlane w oknie **bezpośrednim** .

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Przełącz powiadomienia o wyjątkach pierwszej szansy w oknie bezpośrednim

1. W menu **Widok** kliknij pozycję **inne okna**, a następnie kliknij pozycję **dane wyjściowe**.

2. Kliknij prawym przyciskiem myszy obszar tekstu okna **dane wyjściowe** , a następnie wybierz lub usuń zaznaczenie **komunikatów o wyjątkach**.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie po kodzie za pomocą debugera](../../debugger/navigating-through-code-with-the-debugger.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pierwsze spojrzenie na debugera](../../debugger/debugger-feature-tour.md)
- [Przewodnik: debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
- [Używanie wyrażeń regularnych w programie Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
