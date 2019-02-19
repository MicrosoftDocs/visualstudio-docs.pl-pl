---
title: Polecenie okna | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c7ec3911496c5106d53f90a281452df2c8a128f6
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54788350"
---
# <a name="command-window"></a>Okno polecenia
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Polecenia** okna jest używana do wykonywania poleceń ani aliasów bezpośrednio w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Można wykonać polecenia menu i poleceń, które nie są wyświetlane w żadnym menu. Aby wyświetlić **polecenia** okna, wybierz **Windows inne** z **widoku** menu, a następnie wybierz **okna polecenia**.  
  
## <a name="displaying-the-values-of-variables"></a>Wyświetlanie wartości zmiennych  
 Aby sprawdzić wartość zmiennej `varA`, użyj [polecenie Drukuj](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Znak zapytania (?) jest aliasem `Debug.Print`, dlatego to polecenie można również zapisać:  
  
```  
>? varA  
```  
  
 Obie wersje to polecenie zwróci wartość zmiennej `varA`.  
  
## <a name="entering-commands"></a>Wprowadzenie poleceń  
 Większa niż symbol (`>`) jest wyświetlana przy lewej krawędzi okna wiersza polecenia jako wiersza dla nowych wierszy. Użyj klawiszy Strzałka w górę i Strzałka w dół do przewijania wcześniej wydanych poleceń.  
  
|Zadanie|Rozwiązanie|Przykład|  
|----------|--------------|-------------|  
|Ocena wyrażenia.|Należy poprzedzić wyrażenie znakiem zapytania (`?`).|`? myvar`|  
|Przełącz do okna bezpośredniego.|Wprowadź `immed` do okna bez znaku większości (>)|`immed`|  
|Przejdź z powrotem do okna polecenia w oknie bezpośrednim.|Wprowadź `cmd` do okna.|`>cmd`|  
  
 Poniższe skróty pomóc w nawigowaniu w trybie polecenia.  
  
|Akcja|Lokalizacji kursora|Powiązanie klawiszy|  
|------------|---------------------|----------------|  
|Przechodzenie między listę poleceń podaną wcześniej.|Wiersz danych wejściowych|&AMP; STRZAŁKA W DÓŁ STRZAŁKA W GÓRĘ|  
|Przewiń w górę okna.|Zawartość okna polecenia|CTRL + STRZAŁKA W GÓRĘ|  
|Przewiń w dół okna.|Zawartość okna polecenia|Strzałka w dół lub CTRL + Strzałka w dół|  
  
> [!TIP]
>  Możesz skopiować całość lub część poprzednie polecenie do wiersza danych wejściowych przewijanie do niego, wyróżnianie całość lub część jej i następnie naciśnij klawisz ENTER.  
  
## <a name="mark-mode"></a>Tryb oznaczania  
 Po kliknięciu dowolnego poprzedniego wiersza w **polecenia** okna, nastąpi automatyczne przejście w tryb oznaczania. Dzięki temu można wybrać, edytować i skopiować tekst z poprzedniego polecenia, ponieważ w dowolnym edytorze tekstów i wkleić je do bieżącego wiersza.  
  
## <a name="the-equals--sign"></a>Znak równości (=)  
 Okno służące do wprowadzania `EvaluateStatement` polecenie Określa, czy znak równości (=) jest interpretowany jako operator porównania lub operator przypisania.  
  
 W **polecenia** okna, znak równości (=) jest interpretowany jako operator porównania. Nie można używać operatorów przypisania w **polecenia** okna. Na przykład, jeśli wartości zmiennych `varA` i `varB` są różne, a następnie polecenie  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 Zwraca wartość `False`.  
  
 W **bezpośrednie** okna, z drugiej strony, znak równości (=) jest interpretowany jako operator przypisania. Tak na przykład polecenie  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 przypiszą do zmiennej `varA` wartość zmiennej `varB`.  
  
## <a name="parameters-switches-and-values"></a>Parametry, przełączniki i wartości  
 Niektóre [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] polecenia mają wymagane i opcjonalne argumenty, przełączniki i wartości. Niektóre reguły stosuje się podczas pracy z tych poleceń. Oto przykład sformatowanego polecenie, aby wyjaśnić, terminologii.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 W tym przykładzie  
  
- `Edit.ReplaceInFiles` polecenie  
  
- `/case` i `/pattern:regex` parametry (poprzedzony znakiem ukośnika [/])  
  
- `regex` jest to wartość `/pattern` przełączyć; `/case` przełącznik nie ma wartości  
  
- `var[1-3]+` i `oldpar` parametrów  
  
  > [!NOTE]
  >  Polecenia, parametr, przełącznika lub wartość, która zawiera spacje, musi mieć podwójny cudzysłów po obu stronach.  
  
  Pozycja przełączników i parametry mogą być stosowane zamiennie za darmo w wierszu polecenia, z wyjątkiem produktów [powłoki](../../ide/reference/shell-command.md) polecenia, które wymaga jej przełączniki i parametry w określonej kolejności.  
  
  Prawie każdy przełącznik obsługiwanych przez polecenie ma dwie formy: krótka (jeden znak) i długich fragmentów. W grupie można łączyć wielu przełącznikach krótkiej postaci. Na przykład `/p /g /m` może też wyrażona jako `/pgm`.  
  
  Jeśli krótkich przełączniki są łączone w grupie, danej wartości tej wartości ma zastosowanie do każdego przełącznika. Na przykład `/pgm:123` jest równa `/p:123 /g:123 /m:123`. Błąd występuje, jeśli dowolny z przełączników w grupie nie akceptuje wartości.  
  
## <a name="escape-characters"></a>Znaki specjalne  
 W wierszu polecenia znak karetki (^) oznacza, że znak natychmiast po jego jest interpretowany dosłownie, a nie jako znak kontrolny. Może to służyć do osadzania prostych znaków cudzysłowu ("), spacji, ukośników wiodących, daszków lub innych znaków literałowych w wartości parametru lub przełącznika, z wyjątkiem nazw przełączników. Na przykład  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Daszek działa tak samo, czy wewnątrz lub poza znaki cudzysłowu. Jeśli znak daszka jest ostatnim znakiem w wierszu, jest on ignorowany. Tu przykładzie pokazano, jak wyszukać wzorzec "^ t".  
  
## <a name="use-quotes-for-path-names-with-spaces"></a>Użyj cudzysłowów dla nazwy ścieżki zawierające spacje  
 Jeśli na przykład chcesz otworzyć plik, który zawiera ścieżkę zawierającą spacje, należy umieścić podwójnego cudzysłowu wokół ścieżki lub segment ścieżki, która zawiera spacje: **C:\\"Pliki programów"** lub **"C:\Program Files"**.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
