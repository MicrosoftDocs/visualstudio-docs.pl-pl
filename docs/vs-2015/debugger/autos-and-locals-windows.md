---
title: Elementy Autotekstu i okna lokalne | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161736"
---
# <a name="autos-and-locals-windows"></a>Okna zmiennych automatycznych i zmiennych lokalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **Autokorekty** (podczas debugowania, **Ctrl + Alt + V, a**lub **debugowania/Windows/autostarts**) i okna **zmiennych lokalnych** (podczas debugowania, **Ctrl + Alt + V, L**lub **Debug/Windows/locales**) jest bardzo przydatne, gdy chcesz zobaczyć wartości zmiennych podczas debugowania. W oknie **Ustawienia lokalne** są wyświetlane zmienne, które są zdefiniowane w zakresie lokalnym, zazwyczaj jest to funkcja lub metoda, która jest obecnie wykonywana. W oknie **samochody** są wyświetlane zmienne używane wokół bieżącego wiersza (miejsce, w którym debuger jest zatrzymany). Dokładne zmienne, które są wyświetlane, różnią się w różnych językach. Zobaczyć, jakie zmienne są wyświetlane w oknie samochody? poniżej.  
  
 Jeśli potrzebujesz więcej informacji na temat debugowania podstawowego, zobacz [wprowadzenie z debugerem](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Przeglądanie obiektów w oknach Autostart i zmienne lokalne  
 Tablice i obiekty są wyświetlane w oknach autostarty i lokalne jako kontrolki drzewa. Kliknij strzałkę po lewej stronie nazwy zmiennej, aby rozwinąć widok, aby wyświetlić pola i właściwości. Oto przykład <xref:System.IO.FileStream> obiektu w oknie **zmiennych lokalnych** :  
  
 ![Elementy lokalne&#45;FileStream](../debugger/media/locals-filestream.png "Elementy lokalne — FileStream")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Jakie zmienne pojawiają się w oknie samochody?  
 Można użyć okna **Autokorekty** w języku C#, Visual Basic i kodzie C++. Okno **autouzupełniania** nie obsługuje języka JavaScript ani języka F #.  
  
 W językach C# i Visual Basic okno **autostarts** wyświetla dowolną zmienną używaną w bieżącym lub poprzednim wierszu. Na przykład, Jeśli zadeklarujesz cztery zmienne i ustawisz je w następujący sposób:  
  
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
  
 Jeśli ustawisz punkt przerwania w wierszu, `c = 3` a następnie uruchomisz debuger, gdy wykonywanie zatrzyma się, okno **samochody** będzie wyglądać następująco:  
  
 ![&#45;CSharp](../debugger/media/autos-csharp.png "Samochody — CSharp")  
  
 Należy zauważyć, że wartość `c` jest równa 0, ponieważ wiersz `c = 3` nie został jeszcze wykonany.  
  
 W języku C++ okno **samochody** wyświetla zmienne używane co najmniej trzy wiersze przed bieżącym wierszem (wiersz, w którym wykonywanie jest zatrzymane). Jeśli deklarujesz sześć zmiennych:  
  
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
  
 Jeśli ustawisz punkt przerwania w wierszu `e = 5;` i uruchomisz debuger, gdy wykonywanie zostanie zatrzymane, okno **samochody** będzie wyglądać następująco:  
  
 ![&#45;cplus](../debugger/media/autos-cplus.png "Samochody — cplus")  
  
 Należy zauważyć, że zmienna e jest niezainicjowana, ponieważ kod w wierszu `e = 5;` nie został jeszcze wykonany.  
  
 W pewnych okolicznościach można także zobaczyć wartości zwracane w funkcjach i metodach. Zobacz [Wyświetlanie zwracanych wartości wywołań metod](#bkmk_returnValue) poniżej.  
  
## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Wyświetl wartości zwracane wywołań metod  
 W kodzie .NET i C++ można sprawdzić wartości zwracane podczas przekroczenia lub z wywołania metody. Ta funkcja jest przydatna, gdy wynik wywołania metody nie jest przechowywany w zmiennej lokalnej, na przykład wtedy, gdy metoda jest używana jako parametr lub wartość zwracana przez inną metodę.  
  
 Poniższy kod w języku C# dodaje wartości zwracane przez dwie funkcje:  
  
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
  
 Ustaw punkt przerwania w `x = sumVars(a, b) + subtractVars(c, d);` wierszu int.  
  
 Rozpocznij debugowanie i kiedy wykonywanie jest przerywane przy pierwszym punkcie przerwania, naciśnij klawisz **F10 (** Przekrocz). W oknie **samochody** powinny zostać wyświetlone następujące elementy:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Dlaczego wartości zmiennych czasami są czerwone w lokalnych i oknach systemu Windows?  
 Można zauważyć, że wartość zmiennej jest czasami czerwona w oknach **zmiennych lokalnych** i **Autotekstu** . Są to zmienne wartości, które zostały zmienione od czasu ostatniej oceny. Ta zmiana może pochodzić z poprzedniej sesji debugowania lub wartość została zmieniona w oknie.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Zmiana formatu liczbowego okna zmiennych  
 Domyślny format liczbowy jest dziesiętny, ale można go zmienić na szesnastkowy. Kliknij prawym przyciskiem myszy wewnątrz okna wartości **lokalne** lub **Autostart** , a następnie wybierz pozycję **Wyświetlanie w formacie szesnastkowym**. Zmiana ma wpływ na wszystkie okna debugera.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Edytowanie wartości w oknie zmiennych  
 Można edytować wartości większości zmiennych, które są wyświetlane w oknach **Autokorekty**, **lokalne**, **czujka**i **QuickWatch** . Aby uzyskać informacje na temat **oglądania** i **QuickWatch** systemu Windows, zobacz [Watch i QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md). Wystarczy dwukrotnie kliknąć wartość, którą chcesz zmienić, a następnie dodać nową wartość.  
  
 Możesz na przykład wprowadzić wyrażenie dla wartości `a + b` . Debuger akceptuje większość prawidłowych wyrażeń języka.  
  
 W kodzie natywnym języka C++ może być konieczne zakwalifikowanie kontekstu nazwy zmiennej. Aby uzyskać więcej informacji, zobacz [operator kontekstu (C++)](../debugger/context-operator-cpp.md).  
  
 Należy jednak zachować ostrożność podczas zmieniania wartości. Oto niektóre potencjalne problemy:  
  
- Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan programu. Na przykład Ocena `var1 = ++var2` zmienia wartość `var1` i `var2` .  
  
     Wyrażenia, które zmieniają dane, mają [wpływ na efekty uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)), które mogą dawać nieoczekiwane wyniki, jeśli nie są one świadome. Upewnij się, że rozumiesz konsekwencje takiej zmiany przed jej wprowadzeniem.  
  
- Edytowanie wartości zmiennoprzecinkowych może spowodować powstanie nieścisłych niedokładności z powodu konwersji dziesiętnej na binarną składników ułamkowych. Nawet pozornie nieszkodliwe edytowanie może spowodować zmiany w niektórych najmniej znaczących bitach w zmiennej zmiennoprzecinkowej.  
  
## <a name="debug-location-toolbar"></a>Lokalizacja debugowania, pasek narzędzi  
 Możesz użyć paska narzędzi **Lokalizacja debugowania** , aby wybrać żądaną funkcję, wątek lub proces. Ustaw punkt przerwania i Rozpocznij debugowanie. (Jeśli nie widzisz tego paska narzędzi, możesz go włączyć, klikając w pustej części obszaru paska narzędzi. Powinna zostać wyświetlona lista pasków narzędzi. Wybierz **lokalizację debugowania**). Po trafieniu punktu przerwania wykonywanie zostaje zatrzymane i zobaczysz pasek narzędzi Lokalizacja debugowania, który jest dolnym wierszem poniższej ilustracji:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Można również zmienić kontekst na różne wywołania funkcji, wątki lub procesy przez dwukrotne kliknięcie elementu w oknie **stosu wywołań** , oknie **wątki** lub w oknie **procesy** .  
  
## <a name="see-also"></a>Zobacz też  
 [Okna debugera](../debugger/debugger-windows.md)
