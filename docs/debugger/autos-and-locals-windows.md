---
title: Inspekcja zmiennych — autostarts i okien lokalnych | Microsoft Docs
description: Podczas debugowania w programie Visual Studio Sprawdź zmienne w oknach autostarts i Locals. Okna zmiennych i zmienne lokalne wyświetlają wartości zmiennej podczas debugowania.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 61378b697b8cf2d50851926bb9f9b64b50878a59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857945"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Inspekcja zmiennych w oknach autouzupełniania i lokalnych

Okna **zmiennych i** zmienne **lokalne** wyświetlają wartości zmiennej podczas debugowania. System Windows jest dostępny tylko podczas sesji debugowania. W oknie **samochody** są wyświetlane zmienne używane wokół bieżącego punktu przerwania. Okno zmiennych **lokalnych** zawiera zmienne zdefiniowane w zakresie lokalnym, które zwykle jest bieżącą funkcją lub metodą.

> [!NOTE]
> Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

 Okno **samochody** jest dostępne dla kodu C#, Visual Basic, C++ i Python, ale nie dla języka JavaScript lub F #.

Aby otworzyć okno **autostarty** , podczas debugowania zaznacz opcję **Debuguj**  >    >  **autostarty** systemu Windows lub naciśnij **klawisze CTRL** + **Alt** + **V**  >  **A**.

Aby otworzyć okno zmienne **lokalne** , podczas debugowania wybierz opcję **Debuguj**  >  Ustawienia lokalne **systemu Windows**  >  lub naciśnij klawisze **Alt** + **4**.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [wizualizacje danych w programie Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Korzystanie z okien zmiennych i ustawień regionalnych

Tablice i obiekty są wyświetlane w oknach **Autostarty** i **lokalne** jako kontrolki drzewa. Wybierz strzałkę po lewej stronie nazwy zmiennej, aby rozwinąć widok, aby wyświetlić pola i właściwości. Oto przykład <xref:System.IO.FileStream?displayProperty=fullName> obiektu w oknie **zmiennych lokalnych** :

![Zrzut ekranu okna zmiennych lokalnych z ustawionym ustawieniem File na wartość System. IO. FileStream.](../debugger/media/locals-filestream.png)

Czerwona wartość w oknie zmienne **lokalne** **lub** autozmienne oznacza, że wartość została zmieniona od czasu ostatniej oceny. Zmiana może być z poprzedniej sesji debugowania lub zmieniono wartość w oknie.

Domyślny format liczbowy w oknach debugera jest dziesiętny. Aby zmienić wartość na szesnastkową, kliknij prawym przyciskiem myszy w oknie wartości **lokalne** lub **Autostart** i wybierz pozycję **Wyświetlanie w formacie szesnastkowym**. Ta zmiana ma wpływ na wszystkie okna debugera.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Edytuj wartości zmiennych w oknie elementy Autokorekty lub lokalne

Aby edytować wartości większości zmiennych w oknach zmiennych **autolub** **lokalnych** , kliknij dwukrotnie wartość i wprowadź nową wartość.

Możesz na przykład wprowadzić wyrażenie dla wartości `a + b` . Debuger akceptuje większość prawidłowych wyrażeń języka.

W kodzie natywnym języka C++ może być konieczne zakwalifikowanie kontekstu nazwy zmiennej. Aby uzyskać więcej informacji, zobacz [operator kontekstu (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Upewnij się, że rozumiesz konsekwencje przed zmianą wartości i wyrażeń. Możliwe są następujące problemy:
>
>- Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan programu. Na przykład Ocena `var1 = ++var2` zmienia wartość obu `var1` i `var2` . Wyrażenia te mają [wpływ na skutki uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne mogą spowodować nieoczekiwane wyniki, jeśli nie są one świadome.
>
>- Edytowanie wartości zmiennoprzecinkowych może spowodować powstanie nieścisłych niedokładności z powodu konwersji dziesiętnej na binarną składników ułamkowych. Nawet pozornie nieszkodliwe edytowanie może spowodować zmiany w niektórych bitach w zmiennej zmiennoprzecinkowej.

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

![Filtrowanie właściwości ulubionych](../debugger/media/filter-pinned-properties-locals.png "Filtrowanie właściwości ulubionych") 
 ![Przełącz nazwy właściwości](../debugger/media/toggle-property-names.gif "Przełącz nazwy właściwości")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Zmień kontekst okna autostarts lub locale

Możesz użyć paska narzędzi **Lokalizacja debugowania** , aby wybrać żądaną funkcję, wątek lub proces, co powoduje zmianę kontekstu okien zmiennych i  **lokalnych** .

Aby włączyć pasek narzędzi **Lokalizacja debugowania** , kliknij w pustej części obszaru paska narzędzi, a następnie wybierz opcję **Lokalizacja debugowania** z listy rozwijanej lub wybierz pozycję **Wyświetl**  >  **paski zadań**  >  .

Ustaw punkt przerwania i Rozpocznij debugowanie. Po trafieniu punktu przerwania wykonywanie jest wstrzymywane i będzie można zobaczyć lokalizację na pasku narzędzi **Lokalizacja debugowania** .

![Lokalizacja debugowania, pasek narzędzi](../debugger/media/debuglocationtoolbar.png "Lokalizacja debugowania, pasek narzędzi")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Zmienne w oknie samochody (C#, C++, Visual Basic, Python)

Różne języki kodu wyświetlają różne zmienne w oknie **samochody** .

- W językach C# i Visual Basic okno **autostarts** wyświetla dowolną zmienną używaną w bieżącym lub poprzednim wierszu. Na przykład w języku C# lub Visual Basic kodzie Zadeklaruj następujące cztery zmienne:

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

   Ustaw punkt przerwania w wierszu `c = 3;` i uruchom debuger. Po wstrzymaniu wykonywania zostanie wyświetlone okno **samochody** :

   ![Zrzut ekranu przedstawiający okno samochody z wartością c ustawioną na 0.](../debugger/media/autos-csharp.png)

   Wartość `c` jest równa 0, ponieważ wiersz `c = 3` nie został jeszcze wykonany.

- W języku C++ okno **samochody** wyświetla zmienne używane w co najmniej trzech wierszach przed bieżącym wierszem, w którym wykonywanie zostało wstrzymane. Na przykład w kodzie C++ Zadeklaruj sześć zmiennych:

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

    Ustaw punkt przerwania w wierszu `e = 5;` i uruchom debuger. Po zatrzymaniu zostanie wyświetlone okno **samochody** :

    ![Zrzut ekranu okna autostarts z wyróżnionym wierszem, który pokazuje int c o wartości 3.](../debugger/media/autos-cplus.png)

    Zmienna `e` nie została zainicjowana, ponieważ wiersz `e = 5` nie został jeszcze wykonany.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Wyświetl wartości zwracane wywołań metod
 W kodzie .NET i C++ można sprawdzić wartości zwracane w oknie **samochody** , gdy przekroczy lub wywołaj metodę. Wyświetlanie wartości zwracanych przez wywołanie metody może być przydatne, gdy nie są one przechowywane w zmiennych lokalnych. Metoda może być używana jako parametr lub jako wartość zwracana przez inną metodę.

 Na przykład poniższy kod w języku C# dodaje wartości zwracane przez dwie funkcje:

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

Aby wyświetlić zwracane wartości `sumVars()` `subtractVars()` wywołań metod i w oknie samochody:

1. Ustaw punkt przerwania w `int x = sumVars(a, b) + subtractVars(c, d);` wierszu.

1. Rozpocznij debugowanie i kiedy wykonywanie jest wstrzymywane w punkcie przerwania, wybierz pozycję **Przekrocz** lub naciśnij klawisz **F10**. W oknie **samochody** powinny być widoczne następujące wartości zwracane:

  ![Wartości zwracane przez funkcję autouzupełniania C #](../debugger/media/autosreturnvaluecsharp2.png "Wartości zwracane przez funkcję autouzupełniania C #")

## <a name="see-also"></a>Zobacz też

- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Najpierw Spójrz na Debugowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
