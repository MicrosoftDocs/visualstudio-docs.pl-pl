---
title: Sprawdzanie zmiennych w oknach zmiennych automatycznych i zmiennych lokalnych | Dokumentacja firmy Microsoft
ms.custom: H1Hack27Feb2017
ms.date: 10/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e94c520ca01a92b65ba05a4ff91aaa4c01e7b8d
ms.sourcegitcommit: a811f6a194ccd40d844e74e618d847df87c85c16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/29/2018
ms.locfileid: "52621474"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych w oknach zmiennych automatycznych i zmiennych lokalnych

**Autos** i **lokalne** systemu windows umożliwia wyświetlanie wartości zmiennych podczas debugowania. Systemu windows są dostępne tylko podczas sesji debugowania. **Autos** okno wyświetla zmienne używane wokół bieżącego punktu przerwania. **Lokalne** okno wyświetla zmienne zdefiniowane w zakresie lokalnym, zwykle jest to bieżąca funkcja lub metoda. Jeśli po raz pierwszy, próbujących przeprowadzić debugowania kodu, warto przeczytać [naprawiania błędów, pisząc lepiej C# kodu](../debugger/write-better-code-with-visual-studio.md) i [debugowania dla początkujących](../debugger/debugging-absolute-beginners.md) przed przejściem w tym artykule.

 **Autos** oknie jest dostępna dla C#, kodu języka Visual Basic, C++ i Python, ale nie dla języka JavaScript lub F#.
  
Aby otworzyć **automatyczne** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **Autos**, lub naciśnij **Ctrl**+**Alt**+**V** > **A**.  

Aby otworzyć **zmiennych lokalnych** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **lokalne**, lub naciśnij **Alt**+**4**.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [wizualizacje danych w programie Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Używanie okien zmiennych automatycznych i zmiennych lokalnych

Tablice i obiektów pokazano w **Autos** i **lokalne** systemu windows jako kontrolki drzewa. Wybierz strzałkę w lewo nazwę zmiennej, aby rozszerzyć widok, aby wyświetlić pola i właściwości. Oto przykład <xref:System.IO.FileStream?displayProperty=fullName> obiektu **lokalne** okna:

![Zmienne lokalne FileStream](../debugger/media/locals-filestream.png "FileStream zmiennych lokalnych")

Wartość czerwonego w **lokalne** lub **Autos** okno oznacza, że wartość została zmieniona od czasu ostatniego obliczania. Zmiana może pochodzić z poprzedniej sesji debugowania lub zostały zmienione wartości w oknie.

Domyślny format liczbowy w oknach debugera jest liczbą dziesiętną. Aby zmienić ją na wartość szesnastkową, kliknij prawym przyciskiem myszy **lokalne** lub **Autos** okna, a następnie wybierz pozycję **wyświetlanie szesnastkowe**. Ta zmiana ma wpływ na wszystkie okna debugera.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Edytuj wartości zmiennej w oknie Autos lub zmiennych lokalnych

Aby edytować wartości większość zmiennych w **Autos** lub **lokalne** systemu windows, kliknij dwukrotnie wartość i wprowadź nową wartość.

Można wprowadzić wyrażenie dla wartości, na przykład `a + b`. Debuger akceptuje większość prawidłowych wyrażeń języka.

W kodzie natywnym języku C++ masz może być zakwalifikowanie kontekstu nazwy zmiennej. Aby uzyskać więcej informacji, zobacz [operator kontekstu (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Upewnij się, że rozumiesz konsekwencje, zanim będzie można zmienić wartości i wyrażeń. Niektóre problemy są:
>
>-   Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub inaczej wpłynąć na stan programu. Na przykład oceny `var1 = ++var2` zmienia wartość obu `var1` i `var2`. Wyrażenia te są określane jako mają [efekty uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne może spowodować nieoczekiwane wyniki, jeśli nie masz pewności, z nich.
>
>-   Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza niezgodnościami z powodu konwersji dziesiętnych do pliku binarnego części ułamkowe. Nawet pozornie nieszkodliwe edycji może spowodować zmiany do niektórych bitów w zmiennej zmiennoprzecinkowych.

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Zmienianie kontekstu dla okna zmiennych automatycznych i zmiennych lokalnych

Możesz użyć **Lokalizacja debugowania** narzędzi, wybierz odpowiednią funkcję, wątek lub proces, który zmienia kontekst dla **Autos** i **lokalne** systemu windows.

Aby włączyć **Lokalizacja debugowania** narzędzi, kliknij przycisk w pustej części obszaru narzędzi i wybierz **Lokalizacja debugowania** z listy rozwijanej lub wybierz **widoku**  >   **Paski narzędzi** > **Lokalizacja debugowania**.

Ustaw punkt przerwania, a następnie rozpocząć debugowanie. Po osiągnięciu punktu przerwania wstrzymuje wykonywanie, aby sprawdzić lokalizację w **Lokalizacja debugowania** paska narzędzi.

![Pasek narzędzi lokalizacji debugowania](../debugger/media/debuglocationtoolbar.png "narzędzi debugowania lokalizacji")

## <a name="bkmk_whatvariables"></a> Zmienne w oknie Autos (C#, języka Python w języku C++, Visual Basic)

 Inny kod języków wyświetlać różne zmienne w **Autos** okna.

 - W C# i Visual Basic **Autos** dowolnej zmiennej w wierszu bieżącej lub poprzedniej stosowany jest wyświetlana w oknie. Na przykład w C# lub Visual Basic kod, Zadeklaruj cztery następujące zmienne:

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

   Ustaw punkt przerwania w wierszu `c = 3;`, i uruchomić debuger. Podczas wykonywania jest wstrzymana, **Autos** oknie będą wyświetlane:

   ![Automatyczne CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")

   Wartość `c` ma wartość 0, ponieważ wiersz `c = 3` nie zostało jeszcze wykonane.

 - W języku C++ **Autos** jest wyświetlana w oknie zmiennych używanych w co najmniej trzy wiersze przed bieżącego wiersza, w której wykonywanie jest wstrzymane. Na przykład w przypadku kodu C++ należy deklarować zmienne sześć:

   ```C++
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

    Ustaw punkt przerwania w wierszu `e = 5;` i uruchom debuger. Po zatrzymaniu wykonywania **Autos** oknie będą wyświetlane:

    ![Automatyczne C++](../debugger/media/autos-cplus.png "Autos C++")

    Zmienna `e` została zainicjowana, ponieważ wiersz `e = 5` nie zostało jeszcze wykonane.

##  <a name="bkmk_returnValue"></a> Wyświetl wartości zwracane wywołania metody
 W kodzie .NET i C++, można zbadać wartości zwracane w **Autos** okna, gdy wychodzisz nad lub poza wywołanie metody. Wywołanie metody wyświetlania zwracanych wartości mogą być przydatne, gdy nie są przechowywane w zmiennych lokalnych. Metoda może służyć jako parametr lub jako wartość zwracaną przez inną metodę.

 Na przykład następująca C# kod dodaje wartości zwrócone przez dwie funkcje:

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

Aby wyświetlić wartości zwracanych metody `sumVars()` i `subtractVars()` wywołania metod w oknie Autos:

1. Ustaw punkt przerwania na `int x = sumVars(a, b) + subtractVars(c, d);` wiersza.  
   
1. Rozpocznij debugowanie, a po wstrzymuje wykonywanie w punkcie przerwania, wybierz **Step Over** lub naciśnij **F10**. Powinien zostać wyświetlony następujący wartości zwracane w **Autos** okna:  
   
  ![Wartość zwracana przez automatyczne C# ](../debugger/media/autosreturnvaluecsharp2.png "Autos zwracają wartośćC#")  
  
## <a name="see-also"></a>Zobacz także  
 [Co to jest debugowanie?](../debugger/what-is-debugging.md)  
 [Usuwanie usterek, pisząc lepiej C# kodu](../debugger/write-better-code-with-visual-studio.md)  
 [Pierwsze spojrzenie na profilowanie](../debugger/debugger-feature-tour.md) [okna debugera](../debugger/debugger-windows.md)
