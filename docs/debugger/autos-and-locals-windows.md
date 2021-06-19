---
title: Sprawdzanie zmiennych — okna zmiennych automatycznych i zmiennych | Microsoft Docs
description: Sprawdź zmienne w oknach Zmiennych automatycznych i Zmiennych lokalnych podczas debugowania w Visual Studio. W oknach Wartości automatyczne i Zmienne lokalne są wyświetlane wartości zmiennych podczas debugowania.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b5f1378f87ff8717b9bc9d9125b03c1b28c5007f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389803"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Sprawdzanie zmiennych w oknach zmiennych automatycznych i lokalnych

W **oknach Wartości** **automatyczne i Zmienne** lokalne są wyświetlane wartości zmiennych podczas debugowania. Okna są dostępne tylko podczas sesji debugowania. Okno **Automatyczne wyświetla** zmienne używane wokół bieżącego punktu przerwania. Okno **Zmienne lokalne** zawiera zmienne zdefiniowane w zakresie lokalnym, który jest zazwyczaj bieżącą funkcją lub metodą.

> [!NOTE]
> Jeśli po raz pierwszy próbujesz debugować kod, przed przeczytaniem tego artykułu [](../debugger/write-better-code-with-visual-studio.md) warto przeczytać artykuł Debugowanie dla bezwzględnych początkujących oraz Techniki i narzędzia debugowania. [](../debugger/debugging-absolute-beginners.md)

 Okno **Automatyczne jest** dostępne dla kodu C#, Visual Basic, C++ i Python, ale nie dla języka JavaScript lub F#.

Aby otworzyć okno **Automatyczne podczas debugowania,** wybierz pozycję **Debuguj** automatyczne funkcje  >  **systemu Windows** lub naciśnij klawisze  >   **Ctrl** + **Alt** + **V**  >  **A.**

Aby otworzyć okno **Locals (Lokalne) podczas** debugowania, wybierz **pozycję Debuguj** lokalne dane systemu  >  **Windows** lub naciśnij  >  klawisz **Alt** + **4**.

> [!NOTE]
> Ten temat dotyczy Visual Studio w systemie Windows. Aby Visual Studio dla komputerów Mac więcej informacji, [zobacz Wizualizacje danych w Visual Studio dla komputerów Mac](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Korzystanie z okien ustawienia automatycznego i lokalnego

Tablice i obiekty są wyświetlane w **oknach wartości automatycznych** i **lokalnych** jako kontrolki drzewa. Wybierz strzałkę z lewej strony nazwy zmiennej, aby rozwinąć widok, aby wyświetlić pola i właściwości. Oto przykład obiektu <xref:System.IO.FileStream?displayProperty=fullName> w **oknie Locals (Lokalne):**

![Zrzut ekranu przedstawiający okno Ustawienia lokalne z plikiem ustawionym na wartość System.IO.FileStream.](../debugger/media/locals-filestream.png)

Czerwona wartość w oknie **Ustawienia lokalne** lub **Automatyczne** oznacza, że wartość zmieniła się od czasu ostatniej oceny. Zmiana może pochodzić z poprzedniej sesji debugowania lub z powodu zmiany wartości w oknie.

Domyślny format liczbowy w oknach debugera to decimal (dziesiętny). Aby zmienić tę opcję na szesnastkową,  kliknij prawym  przyciskiem myszy w oknie Ustawienia lokalne lub Automatyczne i wybierz pozycję **Wyświetlanie szesnastowe.** Ta zmiana ma wpływ na wszystkie okna debugera.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Edytowanie wartości zmiennych w oknie Wartości automatyczne lub Zmienne lokalne

Aby edytować wartości większości zmiennych  w  oknach Zmiennych automatycznych lub Zmiennych lokalnych, kliknij dwukrotnie wartość i wprowadź nową wartość.

Możesz wprowadzić wyrażenie dla wartości, na przykład `a + b` . Debuger akceptuje większość prawidłowych wyrażeń językowych.

W natywnym kodzie C++ może być konieczne kwalifikowanie kontekstu nazwy zmiennej. Aby uzyskać więcej informacji, zobacz [Operator kontekstu (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Przed zmianą wartości i wyrażeń upewnij się, że rozumiesz konsekwencje. Niektóre możliwe problemy to:
>
>- Ocenianie niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan programu. Na przykład ocena `var1 = ++var2` zmienia wartość zarówno wartości , jak i `var1` `var2` . Te wyrażenia są mówi się, że mają [skutki uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne mogą powodować nieoczekiwane wyniki, jeśli nie są one świadome.
>
>- Edytowanie wartości zmiennoprzecinkowy może spowodować niewielkie niedokładności z powodu konwersji dziesiętnej na binarną składników ułamkowych. Nawet pozornie niegroźna edycja może spowodować zmiany niektórych bitów w zmiennej zmiennoprzecinkowej.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Wyszukiwanie w oknie Ustawienia automatyczne lub Ustawienia lokalne

Słowa kluczowe można wyszukiwać w kolumnach Nazwa,  Wartość  i Typ w oknie Wartości automatyczne lub Ustawienia lokalne, korzystając z paska wyszukiwania nad każdym oknem. Naciśnij klawisz ENTER lub wybierz jedną ze strzałek, aby wykonać wyszukiwanie. Aby anulować trwające wyszukiwanie, wybierz ikonę "x" na pasku wyszukiwania.

Użyj strzałek w lewo i w prawo (odpowiednio Shift+F3 i F3), aby przechodzić między znalezionymi dopasowaniami.

![Wyszukiwanie w oknie Locals (Lokalne)](../debugger/media/ee-search-locals.png "Wyszukiwanie w oknie Locals (Lokalne)")

Aby wyszukiwanie było bardziej lub mniej dokładne, użyj listy rozwijanej  Wyszukaj  głębiej w górnej części okna Ustawienia automatyczne lub Ustawienia lokalne, aby wybrać poziom głębokości, na którym chcesz wyszukać zagnieżdżone obiekty.  

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Przypinanie właściwości w oknie Ustawienia automatyczne lub Ustawienia lokalne

> [!NOTE]
> Ta funkcja jest obsługiwana w przypadku platform .NET Core 3.0 lub wyższych.

Za pomocą narzędzia **Pinnable Properties** można szybko sprawdzać obiekty według ich właściwości w oknach Ustawienia automatyczne i Ustawienia lokalne.  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz wyświetloną ikonę pinezki lub kliknij prawym przyciskiem myszy i wybierz opcję Przypnij element **członkowski** jako ulubiony w wyświetlonym menu kontekstowym.  Ta właściwość jest wyświetlana na początku listy właściwości obiektu, a nazwa i wartość właściwości są wyświetlane w **kolumnie** Wartość.  Aby odpiąć właściwość, wybierz ponownie ikonę pinezki lub wybierz opcję Odepnij element **członkowski** jako ulubiony w menu kontekstowym.

![Przypinanie właściwości w oknie Locals (Lokalne)](../debugger/media/basic-pin.gif "Przypinanie właściwości w oknie Locals (Lokalne)")

Możesz również przełączać nazwy właściwości i filtrować niepięte właściwości podczas wyświetlania listy właściwości obiektu w oknach Wartości automatyczne lub Lokalne.  Dostęp do każdej opcji można uzyskać, wybierając przyciski na pasku narzędzi nad oknami Ustawienia automatyczne lub Ustawienia lokalne.

![Filtrowanie ulubionych właściwości](../debugger/media/filter-pinned-properties-locals.png "Filtrowanie ulubionych właściwości") 
 ![Przełączanie nazw właściwości](../debugger/media/toggle-property-names.gif "Przełączanie nazw właściwości")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Zmienianie kontekstu okna Ustawienia automatyczne lub Ustawienia lokalne

Za pomocą paska narzędzi **Lokalizacja** debugowania możesz wybrać żądaną funkcję, wątek  lub proces, który zmienia kontekst okien Ustawienia automatyczne **i Ustawienia** lokalne.

Aby włączyć **pasek narzędzi Lokalizacja** debugowania, kliknij pustą część obszaru paska narzędzi i wybierz pozycję **Lokalizacja** debugowania z listy rozwijanej lub wybierz pozycję **Wyświetl** lokalizację  >    >  **debugowania pasków narzędzi.**

Ustaw punkt przerwania i rozpocznij debugowanie. Po trafieniu punktu przerwania wykonywanie jest wstrzymywane, a lokalizacja jest widać na pasku **narzędzi Lokalizacja debugowania.**

![Lokalizacja debugowania, pasek narzędzi](../debugger/media/debuglocationtoolbar.png "Lokalizacja debugowania, pasek narzędzi")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Zmienne w oknie Automatyczne (C#, C++, Visual Basic, Python)

Różne języki kodu wyświetlają różne zmienne w **oknie Automatyczne.**

- W języku C# Visual Basic w **oknie Automatyczne** są wyświetlane wszystkie zmienne używane w bieżącym lub poprzednim wierszu. Na przykład w języku C# lub Visual Basic zadeklaruj następujące cztery zmienne:

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

   Ustaw punkt przerwania w wierszu `c = 3;` i uruchom debuger. Po wstrzymaniu wykonywania **zostanie otwarte okno Automatyczne:**

   ![Zrzut ekranu przedstawiający okno Automatyczne z wartością c ustawioną na 0.](../debugger/media/autos-csharp.png)

   Wartość to `c` 0, ponieważ wiersz `c = 3` nie został jeszcze wykonany.

- W języku C++ **okno Automatyczne** wyświetla zmienne używane w co najmniej trzech wierszach przed bieżącym wierszem, w którym wstrzymano wykonywanie. Na przykład w kodzie języka C++ zadeklaruj sześć zmiennych:

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

    Ustaw punkt przerwania w wierszu i `e = 5;` uruchom debuger. Po zatrzymaniu wykonywania w **oknie Automatyczne będą** wyświetlane:

    ![Zrzut ekranu przedstawiający okno Automatyczne z wyróżnionym wierszem, który pokazuje int c z wartością 3.](../debugger/media/autos-cplus.png)

    Zmienna `e` jest niezainicjowana, ponieważ wiersz `e = 5` nie został jeszcze wykonany.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Wyświetlanie wartości zwracanych wywołań metod
 W kodzie .NET i C++ można zbadać wartości zwracane w oknie Automatyczne podczas wywrócenia lub wywrócenia metody.  Wyświetlanie wartości zwracanych wywołania metody może być przydatne, gdy nie są przechowywane w zmiennych lokalnych. Metoda może być używana jako parametr lub jako wartość zwracana innej metody.

 Na przykład poniższy kod w języku C# dodaje wartości zwracane dwóch funkcji:

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

Aby wyświetlić wartości zwracane `sumVars()` wywołań metod i `subtractVars()` w oknie Automatyczne wartości:

1. Ustaw punkt przerwania w `int x = sumVars(a, b) + subtractVars(c, d);` wierszu.

1. Rozpocznij debugowanie i po wstrzymaniu wykonywania w punkcie przerwania wybierz pozycję **Przek** o krok po kroku lub naciśnij **klawisz F10.** W oknie Automatyczne wartości powinny zostać **zwrócone następujące** wartości:

  ![Automatycznie zwracana wartość C #](../debugger/media/autosreturnvaluecsharp2.png "Automatycznie zwracana wartość C #")

## <a name="see-also"></a>Zobacz też

- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
