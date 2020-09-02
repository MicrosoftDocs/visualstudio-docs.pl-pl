---
title: Okno bezpośrednie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3177c92713f6fdeb9b9b8a47a0da38608714174d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651287"
---
# <a name="immediate-window"></a>Okno bezpośrednie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno **bezpośrednie** służy do debugowania i szacowania wyrażeń, wykonywania instrukcji, drukowania wartości zmiennych itd. Umożliwia wprowadzanie wyrażeń, które mają być oceniane lub wykonywane przez język programistyczny podczas debugowania. Aby wyświetlić okno **bezpośrednie** , Otwórz projekt do edycji, a następnie wybierz pozycję **Windows** z menu **Debuguj** i wybierz pozycję **natychmiastowe**lub naciśnij klawisze Ctrl + Alt + I.

 To okno służy do wydawania poszczególnych [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poleceń. Dostępne polecenia to `EvaluateStatement` , które mogą być używane do przypisywania wartości do zmiennych. Okno **bezpośrednie** obsługuje również funkcję IntelliSense.

## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych
 To okno może być szczególnie przydatne podczas debugowania aplikacji. Na przykład, aby sprawdzić wartość zmiennej `varA` , można użyć [polecenia Print](../../ide/reference/print-command.md):

```
>Debug.Print varA
```

 Znak zapytania (?) jest aliasem dla `Debug.Print` , więc można także napisać to polecenie:

```
>? varA
```

 Obie wersje tego polecenia zwróci wartość zmiennej `varA` .

> [!NOTE]
> Aby wydać [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenie w oknie **bezpośrednim** , należy poprzedzić polecenie znakiem większości (>). Aby wprowadzić wiele poleceń, przełącz się do okna **poleceń** .

## <a name="design-time-expression-evaluation"></a>Obliczanie wyrażenia czasu projektowania
 Za pomocą okna **bezpośredniego** można wykonać funkcję lub procedurę podprocedury w czasie projektowania.

#### <a name="to-execute-a-function-at-design-time"></a>Aby wykonać funkcję w czasie projektowania

1. Skopiuj następujący kod do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] aplikacji konsolowej:

   ```
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. W menu **debugowanie** kliknij pozycję **Windows**, a następnie kliknij pozycję **natychmiastowe**.

3. Wpisz `?MyFunction(2)` w oknie **bezpośrednim** , a następnie naciśnij klawisz ENTER.

    Okno **bezpośrednie** zostanie uruchomione `MyFunction` i wyświetlone `4` .

   Jeśli funkcja lub podprocedura zawiera punkt przerwania, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spowoduje przerwanie wykonywania w odpowiednim punkcie. Można następnie użyć okien debugera do sprawdzenia stanu programu. Aby uzyskać więcej informacji, zobacz [Przewodnik: debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md).

   Nie można użyć oceny wyrażenia czasu projektowania w typach projektów, które wymagają uruchomienia środowiska wykonawczego, w tym [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)] projektów, projektów sieci Web, projektów urządzeń inteligentnych i projektów SQL.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Obliczanie wyrażenia czasu projektowania w rozwiązaniach z obsługą kilku projektów
 Podczas ustanawiania kontekstu oceny wyrażenia czasu projektowania program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] odwołuje się do aktualnie wybranego projektu w Eksplorator rozwiązań. Jeśli nie wybrano projektu w Eksplorator rozwiązań, program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] próbuje oszacować funkcję względem projektu startowego. Jeśli funkcja nie może być oceniona w bieżącym kontekście, zostanie wyświetlony komunikat o błędzie. Jeśli próbujesz ocenić funkcję w projekcie, który nie jest projektem startowym rozwiązania i wystąpi błąd, spróbuj wybrać projekt w Eksplorator rozwiązań i ponownie spróbować wykonać próbę.

## <a name="entering-commands"></a>Wprowadzanie poleceń
 Należy wprowadzić znak większości (>) podczas wystawiania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poleceń w oknie **bezpośrednim** . Użyj klawiszy Strzałka w górę i Strzałka w dół, aby przewijać wcześniej wystawione polecenia.

|Zadanie|Rozwiązanie|Przykład|
|----------|--------------|-------------|
|Oceń wyrażenie.|Oznacz wyrażenie znakiem zapytania (?).|`? a+b`|
|Tymczasowe wprowadzanie trybu polecenia w trybie bezpośrednim (aby wykonać pojedyncze polecenie).|Wprowadź polecenie, umieszczając je na znaku większości (>).|`>alias`|
|Przełącz się do okno Polecenie.|Wprowadź `cmd` do okna, umieszczając go na znaku większości (>).|`>cmd`|
|Przełącz się z powrotem do okna bezpośredniego.|Wprowadź `immed` do okna bez znaku większości (>).|`immed`|

## <a name="mark-mode"></a>Tryb oznaczania
 Po kliknięciu dowolnego poprzedniego wiersza w oknie **bezpośrednim** zostanie ono automatycznie przesunięte do trybu oznaczania. Dzięki temu można wybrać, edytować i skopiować tekst poprzednich poleceń tak samo jak w dowolnym edytorze tekstów i wkleić je do bieżącego wiersza.

## <a name="the-equals--sign"></a>Znak równości (=)
 Okno używane do wprowadzania `EvaluateStatement` polecenia określa, czy znak równości (=) jest interpretowany jako operator porównania, czy jako operator przypisania.

 W oknie **bezpośrednim** znak równości (=) jest interpretowany jako operator przypisania. Tak więc, na przykład, polecenie

```
>Debug.EvaluateStatement(varA=varB)
```

 przypisze do zmiennej `varA` wartość zmiennej `varB` .

 W oknie **polecenia** , z przeciwieństwem, znak równości (=) jest interpretowany jako operator porównania. Nie można używać operacji przypisania w oknie **poleceń** . Tak więc, na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, polecenie

```
>Debug.EvaluateStatement(varA=varB)
```

 zwróci wartość `False` .

## <a name="first-chance-exception-notifications"></a>Powiadomienia o wyjątkach pierwszej szansy
 W niektórych konfiguracjach ustawień powiadomienia o wyjątkach pierwszej szansy są wyświetlane w oknie **bezpośrednim** .

#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Aby włączyć powiadomienia o wyjątkach pierwszej szansy w oknie bezpośrednim

1. W menu **Widok** kliknij pozycję **inne okna**, a następnie kliknij pozycję **dane wyjściowe**.

2. Kliknij prawym przyciskiem myszy obszar tekstu okna **dane wyjściowe** , a następnie wybierz lub usuń zaznaczenie **komunikatów o wyjątkach**.

## <a name="see-also"></a>Zobacz też
 [Nawigowanie po kodzie za pomocą](../../debugger/navigating-through-code-with-the-debugger.md) debugowania [okna poleceń](../../ide/reference/command-window.md) debugera [w Visual Studio](../../debugger/debugging-in-visual-studio.md) [— Przewodnik podstawy](../../debugger/debugger-basics.md) [: debugowanie w czasie projektowania](../../debugger/walkthrough-debugging-at-design-time.md) [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md) [Używanie wyrażeń regularnych w programie Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)
