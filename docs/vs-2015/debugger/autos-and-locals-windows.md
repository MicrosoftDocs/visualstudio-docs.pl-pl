---
title: Zmiennych automatycznych i zmiennych lokalnych Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 261c0c0bd8b48634c8d24d56ee4df7ea3bbcf135
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072854"
---
# <a name="autos-and-locals-windows"></a>Zmiennych automatycznych i zmiennych lokalnych Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Autos** okna (podczas debugowania, **CTRL + ALT + V, A**, lub **debugowanie / Windows / samochody**) i **lokalne** okna (podczas debugowania,  **CTRL + ALT + V, L**, lub **debugowanie / Windows / zmienne lokalne**) są bardzo przydatne, gdy użytkownik chce zobaczyć wartości zmiennych podczas debugowania. **Lokalne** jest wyświetlana w oknie zmiennych, które są zdefiniowane w zakresie lokalnym jest ogólnie funkcję lub metodę, która jest aktualnie wykonywane. **Autos** jest wyświetlana w oknie zmiennych używanych wokół bieżącego wiersza (miejsce, w której debuger został zatrzymany). Dokładnie wyświetlane zmienne, które różni się w różnych językach. Zobacz, jakie zmienne są wyświetlane w oknie Autos? poniżej.  
  
 Aby uzyskać więcej informacji dotyczących debugowania podstawowe zobacz [wprowadzenie do debugera](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Spojrzenie na obiektach w oknach zmiennych automatycznych i zmiennych lokalnych  
 Tablice i obiekty są wyświetlane w oknach zmiennych automatycznych i zmiennych lokalnych jako kontrolki drzewa. Kliknij strzałkę w lewo nazwę zmiennej, aby rozszerzyć widok, aby wyświetlić pola i właściwości. Oto przykład <xref:System.IO.FileStream> obiektu **lokalne** okna:  
  
 ![Locals&#45;FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Jakie zmienne są wyświetlane w oknie Autos?  
 Możesz użyć **Autos** okna w kodzie C#, Visual Basic i C++. **Autos** okno nie obsługuje języka JavaScript lub F#.  
  
 W języku C# i Visual Basic **Autos** dowolnej zmiennej w wierszu bieżącej lub poprzedniej stosowany jest wyświetlana w oknie. Na przykład, jeśli zadeklarujesz cztery zmienne i ustaw je w następujący sposób:  
  
```csharp  
public static void Main()  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
}  
```  
  
 Jeśli ustawisz punkt przerwania w wierszu `c = 3`; i uruchom debuger, gdy zatrzymuje wykonywanie **Autos** okno będzie wyglądać następująco:  
  
 ![Autos&#45;CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")  
  
 Należy pamiętać, że wartość `c` ma wartość 0, ponieważ wiersz `c = 3` nie zostało jeszcze wykonane.  
  
 W języku C++ **Autos** okna wyświetla zmienne używane co najmniej trzy wiersze przed bieżącego wiersza (wiersz, w którym wykonywanie zostało zatrzymane). Jeśli zadeklarujesz sześć zmiennych:  
  
```cpp  
void main() {  
    int a, b, c, d, e, f;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    e = 5;  
    f = 6;  
}  
```  
  
 Jeśli ustawisz punkt przerwania w wierszu `e = 5;` i uruchom debuger, gdy zatrzymuje wykonywanie **Autos** okno będzie wyglądać następująco:  
  
 ![Autos&#45;Cplus](../debugger/media/autos-cplus.png "Autos-Cplus")  
  
 Należy zauważyć, że zmienna e została zainicjowana, ponieważ kod w wierszu `e = 5;` nie zostało jeszcze wykonane.  
  
 Widać również wartości zwrócone przez funkcje i metody w pewnych okolicznościach. Zobacz [Wyświetl wartości zwracane wywołania metody](#bkmk_returnValue) poniżej.  
  
## <a name="bkmk_returnValue"></a> Wyświetl wartości zwracane wywołania metody  
 W kodzie .NET i C++ gdy wychodzisz nad lub poza wywołanie metody można sprawdzić wartości zwracanych. Ta funkcja jest przydatna, gdy wynik wywołania metody nie jest przechowywany w zmiennej lokalnej, na przykład gdy metoda ta jest używana jako parametr lub wartość zwracaną przez inną metodę.  
  
 Poniższy kod C#, dodaje wartości zwrócone przez dwie funkcje:  
  
```csharp  
static void Main(string[] args)  
{  
    int a, b, c, d;  
    a = 1;  
    b = 2;  
    c = 3;  
    d = 4;  
    int x = sumVars(a, b) + subtractVars(c, d);  
}  
  
private static int sumVars(int i, int j)  
{  
    return i + j;  
}  
  
private static int subtractVars(int i, int j)  
{  
    return j - i;  
}  
  
```  
  
 Ustaw punkt przerwania na int `x = sumVars(a, b) + subtractVars(c, d);` wiersza.  
  
 Rozpocznij debugowanie, a podczas wykonywania przerywa w pierwszym punkcie przerwania, naciśnij klawisz **F10 (Step Over)**. Powinien zostać wyświetlony następujący w **Autos** okna:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Dlaczego są wartości zmiennych czasami red w elementach lokalnych i automatycznych systemu windows?  
 Można tutaj zauważyć wartość zmiennej jest czasami w **lokalne** i **Autos** systemu windows. Są to wartości zmiennych, które zostały zmienione od czasu ostatniego obliczania. Zmiana może być z poprzedniej sesji debugowania, lub wartość została zmieniona w oknie.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Zmiana formatu numerycznego okna zmiennych  
 Domyślny format liczbowy jest liczbą dziesiętną, ale można ją zmienić na liczbę szesnastkową. Kliknij prawym przyciskiem myszy wewnątrz **lokalne** lub **Autos** okna, a następnie wybierz pozycję **wyświetlanie szesnastkowe**. Zmiana dotyczy wszystkich okien debugera.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Edytowanie wartości w oknie zmiennych  
 Możesz edytować wartości większość zmiennych, które pojawiają się w **Autos**, **lokalne**, **Obejrzyj**, i **QuickWatch** systemu windows. Aby uzyskać informacje o **Obejrzyj** i **QuickWatch** systemu windows, zobacz [wyrażenie kontrolne i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Po prostu dwukrotnie kliknąć wartość, którą chcesz zmienić i Dodaj nową wartość.  
  
 Można wprowadzić wyrażenie dla wartości, na przykład `a + b`. Debuger akceptuje większość prawidłowych wyrażeń języka.  
  
 W kodzie natywnym języku C++ masz może być zakwalifikowanie kontekstu nazwy zmiennej. Aby uzyskać więcej informacji, zobacz [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md).  
  
 Jednakże należy zachować ostrożność podczas zmiany wartości. Oto niektóre potencjalne problemy:  
  
- Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub inaczej wpłynąć na stan programu. Na przykład oceny `var1 = ++var2` zmienia wartość `var1` i `var2`.  
  
     Wyrażenia, które zmieniają dane są określane jako mają [efekty uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), które dają nieoczekiwane wyniki, jeśli nie masz pewności, z nich. Upewnij się, że rozumiesz konsekwencje tej zmiany przed jej wprowadzeniem.  
  
- Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza niezgodnościami z powodu konwersji dziesiętnych do pliku binarnego części ułamkowe. Nawet pozornie nieszkodliwe edycji może spowodować zmiany do niektórych najmniej znaczące bity w zmiennej zmiennoprzecinkowych.  
  
## <a name="debug-location-toolbar"></a>Lokalizacja debugowania, pasek narzędzi  
 Możesz użyć **Lokalizacja debugowania** narzędzi, aby wybrać żądaną funkcję, wątek lub procesu. Ustaw punkt przerwania, a następnie rozpocząć debugowanie. (Jeśli nie widzisz tego paska narzędzi, można włączyć ją, klikając w pustej części obszaru paska narzędzi. Powinien zostać wyświetlony lista pasków narzędzi; Wybierz **Lokalizacja debugowania**). Po osiągnięciu punktu przerwania zatrzymuje wykonywanie, aby sprawdzić narzędzi debugowania lokalizacji, czyli dolny wiersz poniższym rysunku:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Możesz również zmienić kontekst do wywołań różnych funkcji, wątki lub procesy, przez dwukrotne kliknięcie elementu w **stos wywołań** oknie **wątków** oknie lub **procesy** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Okna debugera](../debugger/debugger-windows.md)
