---
title: Debuger użytkownika debugera (XSLT) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d35ec92a76c9ecbf933256229b64ce06a03a4fc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670986"
---
# <a name="debugger-user-interface-xslt"></a>Interfejs użytkownika debugera (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano okna debugera i okna dialogowe. Omawia tylko elementy interfejsu użytkownika, które mają zachowanie debugowania specyficznego dla XSLT.

 Aby uzyskać więcej informacji, zobacz [debugowanie informacji o interfejsie użytkownika](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>Okno zmiennych lokalnych
 Okno zmienne lokalne wyświetla informacje o zmiennych zdefiniowanych w arkuszu stylów. Okno lokalne zawiera trzy kolumny informacji:

 **Nazwa** Ta kolumna zawiera nazwy wszystkich zmiennych lokalnych w bieżącym zakresie. Zestawy węzłów mają formant drzewa, który można przechodzenie do szczegółów w celu wyświetlenia jego podfolderów.

 **Wartość** W tej kolumnie jest wyświetlana wartość zawartej w każdej zmiennej. W przypadku atrybutów, instrukcji przetwarzania, komentarzy, tekstu i CData wyświetlana jest wartość tekstowa węzła. Węzły przestrzeni nazw wyświetlają identyfikator URI przestrzeni nazw.

 **Typ** Ta kolumna określa typ danych każdej zmiennej wymienionej w kolumnie **Nazwa** .

 W oknie Ustawienia lokalne są również wyświetlane wstępnie zdefiniowane zmienne kontekstowe, które śledzą kontekst transformacji XSLT. W poniższej tabeli opisano wstępnie zdefiniowane zmienne kontekstowe używane przez debuger XSLT.

|Nazwa|Opis|
|----------|-----------------|
|`last()`|Rozmiar kontekstu.|
|`position()`|Pozycja lub numer indeksu węzła kontekstu względem rozmiaru kontekstu.|
|`self::node()`|Wartość węzła kontekstu.|

 Aby uzyskać więcej informacji, zobacz [How to: Change the Debugger Context](https://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).

## <a name="output-window"></a>Okno wyniku
 W oknie dane wyjściowe są wyświetlane wszystkie komunikaty o błędach lub wyjątki zabezpieczeń, które występują podczas debugowania.

 Debuger XSLT używa oddzielnego okna do wyświetlania danych wyjściowych debugera. Jest to to samo okno używane do wyświetlania danych wyjściowych z polecenia **Pokaż dane wyjściowe XSL** .

## <a name="task-list"></a>Lista zadań
 Lista zadań wyświetla wszystkie błędy kompilacji w arkuszu stylów. Dwukrotne kliknięcie tego błędu spowoduje przejście kursora do wiersza z błędem.

 Lista zadań zawiera wszystkie błędy występujące w blokach skryptu w pliku XSLT.

> [!NOTE]
> Debuger XSLT nie ma ostrzeżeń, więc nigdy nie pojawiają się w Lista zadań.

## <a name="breakpoints-window"></a>Okno punktów przerwania
 W oknie punkty przerwania są wyświetlane wszystkie punkty przerwania ustawione w bieżącym projekcie. Jeśli punkt przerwania zostanie dodany podczas wyświetlania okna, okno zostanie automatycznie zaktualizowane, aby pokazać nowy punkt przerwania.

 Okno punktów przerwania powinno zachowywać się tak samo jak w przypadku innych debugerów programu Visual Studio.

## <a name="command-windowimmediate-window"></a>Okno polecenia/okno bezpośrednie
 Nie zaimplementowane w tej wersji debugera XSLT.

## <a name="watch-window"></a>Okno czujka
 Okno wyrażeń kontrolnych służy do obliczania zmiennych. Możesz również zmienić wartości zmiennych.

 Zmienne wyświetlane w okno wyrażeń kontrolnych są dla bieżącego kontekstu (najwyższego elementu w stosie wywołań). W przypadku zmiany kontekstu okno czujki aktualizuje i wyświetli zmienne ustawione dla tego kontekstu.

## <a name="call-stack-window"></a>Okno stosu wywołań
 Okno stos wywołań służy do wyświetlania nazw funkcji w stosie wywołań, typach parametrów i wartościach parametrów. Informacje stosu wywołań są wyświetlane tylko wtedy, gdy debugowany program jest w stanie przerwania.

 Stos wywołań reprezentuje różne konteksty wykonywane przez wykonanie XSLT. Na przykład jeśli istnieje wywołanie z szablonu "a" do szablonu "b", szablon "a" i szablon "b" pojawiają się w oknie stosu wywołań z bieżącym kontekstem w bardzo górnej części listy. Użytkownik może zobaczyć aktualnie wykonywane zapytanie.

 Jeśli szablony nie mają nazwy w pliku XSLT, są używane nazwy generowane przez procesor XSLT.

 Kliknięcie elementu poza nim znajdującego się w górnej części listy wskazuje Podgląd, w którym wystąpiła gałąź wykonywania XSLT, przy użyciu standardowego, wyróżniania i zielona strzałek.

## <a name="quickwatch-dialog-box"></a>QuickWatch — okno dialogowe
 Okno dialogowe **QuickWatch** służy do obliczania wyrażeń XPath 1,0. Węzeł kontekstu (węzeł `self::node()` z okna lokalnego) zawiera kontekst wykonywania wyrażenia XPath. W okno wyrażeń kontrolnych zostanie wyświetlony wynik wykonywania wyrażenia XPath.

 Na poniższej liście opisano niektóre ograniczenia dotyczące oceny wyrażenia XPath.

- Dozwolone są tylko wbudowane funkcje XPath.

- Wbudowane funkcje XSLT, takie jak `document()`, `key()` i tak dalej, są niedozwolone.

- Funkcje zdefiniowane przez użytkownika są niedozwolone.

  Aby uzyskać więcej informacji, zobacz [jak: oszacować wyrażenie XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Okno demontażu
 Okno demontaż pokazuje kod zestawu, który jest generowany przez kompilator XSLT. To okno może być używane w taki sam sposób, jak wszystkie inne okna rozasemblera programu Visual Studio.

 Aby uzyskać więcej informacji, w [jaki sposób: użyć okna demontażu](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Zobacz też
 [](../xml-tools/debugging-xslt.md) [Podstawowe informacje](../debugger/debugger-basics.md) o [zmiennej](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e) debugowania debugera XSLT
