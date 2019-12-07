---
title: Sprawdzanie zmiennych - okien zmiennych automatycznych i zmiennych lokalnych | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 10/18/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b159f631534135ac568fb03dbffa46ae0360fc47
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904106"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych w oknach zmiennych automatycznych i zmiennych lokalnych

**Autos** i **lokalne** systemu windows umożliwia wyświetlanie wartości zmiennych podczas debugowania. Systemu windows są dostępne tylko podczas sesji debugowania. **Autos** okno wyświetla zmienne używane wokół bieżącego punktu przerwania. **Lokalne** okno wyświetla zmienne zdefiniowane w zakresie lokalnym, zwykle jest to bieżąca funkcja lub metoda. Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

 **Autos** oknie jest dostępna dla C#, kodu języka Visual Basic, C++ i Python, ale nie dla języka JavaScript lub F#.

Aby otworzyć **automatyczne** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **Autos**, lub naciśnij **Ctrl**+**Alt**+**V** > **A**.

Aby otworzyć **zmiennych lokalnych** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **lokalne**, lub naciśnij **Alt**+**4**.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [wizualizacje danych w programie Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Używanie okien zmiennych automatycznych i zmiennych lokalnych

Tablice i obiektów pokazano w **Autos** i **lokalne** systemu windows jako kontrolki drzewa. Wybierz strzałkę w lewo nazwę zmiennej, aby rozszerzyć widok, aby wyświetlić pola i właściwości. Oto przykład <xref:System.IO.FileStream?displayProperty=fullName> obiektu **lokalne** okna:

![Elementy lokalne — FileStream](../debugger/media/locals-filestream.png "Elementy lokalne — FileStream")

Wartość czerwonego w **lokalne** lub **Autos** okno oznacza, że wartość została zmieniona od czasu ostatniego obliczania. Zmiana może pochodzić z poprzedniej sesji debugowania lub zostały zmienione wartości w oknie.

Domyślny format liczbowy w oknach debugera jest liczbą dziesiętną. Aby zmienić ją na wartość szesnastkową, kliknij prawym przyciskiem myszy **lokalne** lub **Autos** okna, a następnie wybierz pozycję **wyświetlanie szesnastkowe**. Ta zmiana ma wpływ na wszystkie okna debugera.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Edytuj wartości zmiennej w oknie Autos lub zmiennych lokalnych

Aby edytować wartości większość zmiennych w **Autos** lub **lokalne** systemu windows, kliknij dwukrotnie wartość i wprowadź nową wartość.

Można wprowadzić wyrażenie dla wartości, na przykład `a + b`. Debuger akceptuje większość prawidłowych wyrażeń języka.

W kodzie natywnym języku C++ masz może być zakwalifikowanie kontekstu nazwy zmiennej. Aby uzyskać więcej informacji, zobacz [operator kontekstu (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Upewnij się, że rozumiesz konsekwencje, zanim będzie można zmienić wartości i wyrażeń. Niektóre problemy są:
>
>- Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub inaczej wpłynąć na stan programu. Na przykład oceny `var1 = ++var2` zmienia wartość obu `var1` i `var2`. Wyrażenia te są określane jako mają [efekty uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne może spowodować nieoczekiwane wyniki, jeśli nie masz pewności, z nich.
>
>- Edytowanie wartości zmiennoprzecinkowych może spowodować pomocnicza niezgodnościami z powodu konwersji dziesiętnych do pliku binarnego części ułamkowe. Nawet pozornie nieszkodliwe edycji może spowodować zmiany do niektórych bitów w zmiennej zmiennoprzecinkowych.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Wyszukaj w oknie elementy Autokorekty lub lokalne

Słowa kluczowe można wyszukiwać w kolumnach Nazwa, wartość i **typ okna zmienne lub** **Ustawienia lokalne** przy użyciu paska wyszukiwania powyżej każdego okna. Naciśnij klawisz ENTER lub wybierz jedną ze strzałek, aby wykonać wyszukiwanie. Aby anulować bieżące wyszukiwanie, wybierz ikonę "x" na pasku wyszukiwania.

Użyj strzałek w lewo i w prawo (odpowiednio Shift + F3 i F3), aby poruszać się między znalezionymi dopasowaniami.

![Wyszukaj w oknie zmiennych lokalnych](../debugger/media/ee-search-locals.png "Wyszukaj w oknie zmiennych lokalnych")

Aby przeszukać więcej lub mniej szczegółowych informacji, Użyj listy rozwijanej **Szukaj** z głębokością w górnej części okna **autostarty** lub **lokalne** , aby wybrać liczbę poziomów, które mają być przeszukiwane w zagnieżdżonych obiektach. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Przypnij właściwości w oknie samochody lub zmienne lokalne

> [!NOTE]
> Ta funkcja jest obsługiwana w przypadku platformy .NET Core 3,0 lub nowszej.

Możesz szybko sprawdzać obiekty według ich właściwości w oknach Autostart i zmienne lokalne przy użyciu narzędzia **Pinnable Properties** .  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz ikonę pinezki, która jest wyświetlana, lub kliknij prawym przyciskiem myszy i wybierz opcję **Przypnij element członkowski jako ulubiony** w menu kontekstowym.  Powoduje to **odfiltrowanie** tej właściwości do górnej części listy właściwości obiektu, a nazwa właściwości i wartość jest wyświetlana w kolumnie wartość.  Aby odpiąć właściwość, wybierz ponownie ikonę pinezki lub wybierz opcję **Odepnij członka jako ulubioną** w menu kontekstowym.

![Przypnij właściwości w oknie zmiennych lokalnych](../debugger/media/basic-pin.gif "Przypnij właściwości w oknie zmiennych lokalnych")

Można również przełączać nazwy właściwości i odfiltrować przypięte właściwości podczas wyświetlania listy właściwości obiektu w oknach zmiennych lub lokalnych.  Możesz uzyskać dostęp do każdej opcji, wybierając przyciski na pasku narzędzi powyżej okien zmiennych lub lokalnych.

![Filtruj Ulubione właściwości](../debugger/media/filter-pinned-properties-locals.png "Filtrowanie właściwości ulubionych")
![Przełącz nazwy właściwości](../debugger/media/toggle-property-names.gif "Przełącz nazwy właściwości")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Zmienianie kontekstu dla okna zmiennych automatycznych i zmiennych lokalnych

Możesz użyć **Lokalizacja debugowania** narzędzi, wybierz odpowiednią funkcję, wątek lub proces, który zmienia kontekst dla **Autos** i **lokalne** systemu windows.

Aby włączyć **Lokalizacja debugowania** narzędzi, kliknij przycisk w pustej części obszaru narzędzi i wybierz **Lokalizacja debugowania** z listy rozwijanej lub wybierz **widoku**  >   **Paski narzędzi** > **Lokalizacja debugowania**.

Ustaw punkt przerwania, a następnie rozpocząć debugowanie. Po osiągnięciu punktu przerwania wstrzymuje wykonywanie, aby sprawdzić lokalizację w **Lokalizacja debugowania** paska narzędzi.

![Pasek narzędzi lokalizacji debugowania](../debugger/media/debuglocationtoolbar.png "Lokalizacja debugowania, pasek narzędzi")

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

   ![Samochody — CSharp](../debugger/media/autos-csharp.png "Samochody — CSharp")

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

    ![AutomatyczneC++](../debugger/media/autos-cplus.png "AutomatyczneC++")

    Zmienna `e` została zainicjowana, ponieważ wiersz `e = 5` nie zostało jeszcze wykonane.

## <a name="bkmk_returnValue"></a> Wyświetl wartości zwracane wywołania metody
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

  ![Wartości zwracane przez funkcję AutokorektyC#](../debugger/media/autosreturnvaluecsharp2.png "Wartości zwracane przez funkcję AutokorektyC#")

## <a name="see-also"></a>Zobacz także

- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Techniki i narzędzia debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na profilowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
