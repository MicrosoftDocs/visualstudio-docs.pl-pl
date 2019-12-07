---
title: Ustawianie wyrażenia kontrolnego na zmiennych | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904053"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Obserwuj zmienne, za pomocą okna czujki i QuickWatch

Podczas debugowania, można użyć **Obejrzyj** systemu windows i **QuickWatch** obejrzeć zmiennych i wyrażeń. Systemu windows są dostępne tylko podczas sesji debugowania.

**Obejrzyj** systemu windows można wyświetlić wiele zmiennych podczas debugowania. **QuickWatch** okno dialogowe Wyświetla pojedynczą zmienną w czasie i muszą zostać zamknięte przed kontynuowaniem debugowania.

Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="observe-variables-with-a-watch-window"></a>Obserwuj zmienne okno czujki

Możesz otworzyć więcej niż jeden **Obejrzyj** okna i sprawdź, czy więcej niż jednej zmiennej w **Obejrzyj** okna.

Na przykład Ustaw wyrażenie kontrolne na wartościach `a`, `b`, i `c` w poniższym kodzie:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Ustaw punkt przerwania na `c = a + b;` wiersza, klikając w lewy margines, wybierając **debugowania** > **Przełącz punkt przerwania**, lub naciskając **F9**.

1. Rozpocznij debugowanie wybierając na zielony wskaźnik **Start** strzałkę lub **debugowania** > **Rozpocznij debugowanie**, lub naciśnij **F5**. Wstrzymuje wykonywanie w punkcie przerwania.

1. Otwórz **Obejrzyj** okna, wybierając **debugowania** > **Windows** > **Obejrzyj**  >   **Obejrzyj 1**, lub naciskając **Ctrl**+**Alt**+**W** > **1**.

   Możesz otworzyć dodatkowe **Obejrzyj** systemu windows, wybierając pozycję windows **2**, **3**, lub **4**.

1. W **Obejrzyj** okna, wybierz pusty wiersz, a zmienna typu `a`. Tym samym `b` i `c`.

   ![Obserwuj zmienne](../debugger/media/watchvariables.png "WatchVariables")

1. Kontynuuj debugowanie wybierając **debugowania** > **Step Into** lub naciskając **F11** stosownie do potrzeb w celu przechodzenia. Zmienna wartości w **Obejrzyj** okna zmienić iteracyjne przeglądanie `for` pętli.

>[!NOTE]
>Aby uzyskać tylko w języku C++
>- Konieczne może być zakwalifikowanie kontekstu nazwy zmiennej lub wyrażenia, który używa nazwy zmiennej. Kontekst jest funkcja, plik źródłowy lub moduł, w którym znajduje się zmienna. Jeśli ma być zakwalifikowanie kontekstu, użyj [operator kontekstu (C++)](../debugger/context-operator-cpp.md) składni **nazwa** w **Obejrzyj** okna.
>
>- Można dodać rejestru nazwy i nazwy zmiennych, przy użyciu  **$ \<zarejestrować&nbsp;nazwa >** lub  **@ \<zarejestrować&nbsp;name >** do **nazwa** w **Obejrzyj** okna. Aby uzyskać więcej informacji, zobacz [Pseudozmienne](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Korzystanie z wyrażeń w oknie czujki

Możesz obserwować dowolnym prawidłowym wyrażeniem rozpoznawanym przez debuger w **Obejrzyj** okna.

Na przykład w przypadku kodu w poprzedniej sekcji, wprowadzając można pobierać średnią z trzech wartości `(a + b + c) / 3` w **Obejrzyj** okna:

![Wyrażenie czujki](../debugger/media/watchexpression.png "Wyrażenie czujki")

Reguły dotyczące oceny wyrażenia w **Obejrzyj** są generalnie takie same jak reguły dotyczące wyrażeń języka kodu. Jeśli wyrażenie zawiera błąd składniowy, oczekiwać, że ten sam błąd kompilatora, tak jak w edytorze kodu. Na przykład błąd pisowni w poprzednim wyrażeniu generuje ten błąd wystąpił w **Obejrzyj** okna:

![Błąd wyrażenia czujki](../debugger/media/watchexpressionerror.png "Błąd wyrażenia czujki")

Koło z ikoną dwóch falistych linii może występować w **Obejrzyj** okna. Ta ikona oznacza, że debuger nie szacuje wyrażenia ze względu na potencjalne zależności między wątkami. Obliczenie kodu wymaga innych wątków w aplikacji do tymczasowego uruchomienia, ale ponieważ jesteś w trybie przerwania, zwykle zatrzymuje wszystkie wątki w swojej aplikacji. Zezwolenie tymczasowego uruchomienia innych wątków może mieć nieoczekiwane działanie dotyczące stanu aplikacji, a debuger może zignorować zdarzenia, takie jak punkty przerwania i wyjątków na te wątki.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Wyszukaj w okno wyrażeń kontrolnych

Słowa kluczowe można wyszukiwać w kolumnach Nazwa, wartość i typ okna **czujka** przy użyciu paska wyszukiwania powyżej każdego okna. Naciśnij klawisz ENTER lub wybierz jedną ze strzałek, aby wykonać wyszukiwanie. Aby anulować bieżące wyszukiwanie, wybierz ikonę "x" na pasku wyszukiwania.

Użyj strzałek w lewo i w prawo (odpowiednio Shift + F3 i F3), aby poruszać się między znalezionymi dopasowaniami.

![Wyszukaj w oknie czujki](../debugger/media/ee-search-watch.png "Wyszukaj w oknie czujki")

Aby przeszukać więcej lub mniej szczegółowych informacji, Użyj listy rozwijanej **Szukaj z dokładniejszą** w górnej części okna **czujka** , aby wybrać liczbę poziomów, które mają być przeszukiwane w zagnieżdżonych obiektach. 

## <a name="pin-properties-in-the-watch-window"></a>Przypnij właściwości w okno wyrażeń kontrolnych

>[!NOTE]
> Ta funkcja jest obsługiwana w programie .NET Core 3,0 lub nowszym.

Możesz szybko sprawdzić obiekty według ich właściwości w okno wyrażeń kontrolnych za pomocą narzędzia **Pinnable Properties** .  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz ikonę pinezki, która jest wyświetlana, lub kliknij prawym przyciskiem myszy i wybierz opcję **Przypnij element członkowski jako ulubiony** w menu kontekstowym.  Powoduje to **odfiltrowanie** tej właściwości do górnej części listy właściwości obiektu, a nazwa właściwości i wartość jest wyświetlana w kolumnie wartość.  Aby odpiąć właściwość, wybierz ponownie ikonę pinezki lub wybierz opcję **Odepnij członka jako ulubioną** w menu kontekstowym.

![Przypnij właściwości w okno wyrażeń kontrolnych](../debugger/media/basic-pin-watch.gif "Przypnij właściwości w okno wyrażeń kontrolnych")

Można również przełączać nazwy właściwości i odfiltrować przypięte właściwości podczas wyświetlania listy właściwości obiektu w okno wyrażeń kontrolnych.  Dostęp do obu opcji można uzyskać, wybierając przyciski na pasku narzędzi powyżej okna Czujka.

::: moniker-end

### <a name="bkmk_refreshWatch"></a> Odświeżanie wartości czujki

Ikona odświeżania (strzałkę kolistą) mogą być wyświetlane w **Obejrzyj** okna, gdy wyrażenie jest obliczane. Ikona odświeżania wskazuje błąd lub wartość, która jest nieaktualna.

Aby odświeżyć wartości, wybierz ikonę odświeżania lub naciśnij klawisz spacji. Debuger próbuje ponownie oceń wyrażenie. Może nie ma lub być w stanie ponownie oceń wyrażenie, w zależności od tego, dlaczego nie można obliczyć wartość.

Umieść kursor nad ikonę odświeżania lub zobacz **wartość** kolumny z powodu nie można obliczyć wyrażenia. Przyczyny:

- Wystąpił błąd, ponieważ został Trwa obliczanie wyrażenia co w poprzednim przykładzie. Przekroczono limit czasu może wystąpić lub zmiennej może być poza zakres tej asysty.

- Wyrażenie zawiera wywołanie funkcji, które mogą wyzwalać opcję efekt uboczny, w aplikacji. Zobacz [efekty uboczne wyrażenie](#bkmk_sideEffects).

- Automatycznej oceny właściwości i niejawne wywołania funkcji jest wyłączone.

Jeśli ikona odświeżania pojawia się, ponieważ automatycznej oceny właściwości i niejawne wywołania funkcji jest wyłączone, możesz je włączyć, wybierając **Włącz obliczanie właściwości i inne niejawne wywołania funkcji** w **narzędzia**   >  **Opcje** > **debugowania** > **ogólne**.

Aby zademonstrować, za pomocą ikony odświeżania:

1. W **narzędzia** > **opcje** > **debugowanie** > **ogólne**, wyczyść **Włącz obliczanie właściwości i inne niejawne wywołania funkcji** pole wyboru.

1. Wprowadź następujący kod, a następnie w **Obejrzyj** okna, ustaw wyrażenie kontrolne na `list.Count` właściwości.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Rozpocznij debugowanie. **Obejrzyj** okno przedstawia podobny do następującego komunikatu:

   ![Odśwież czujkę](../debugger/media/refreshwatch.png "Odśwież czujkę")

1. Aby odświeżyć wartości, wybierz ikonę odświeżania lub naciśnij klawisz spacji. Debuger reevaluates wyrażenia.

### <a name="bkmk_sideEffects"></a> Wyrażenie efektów ubocznych

Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub inaczej wpłynąć na stan aplikacji. Na przykład obliczenie następującego wyrażenia zmienia wartość `var1`:

```csharp
var1 = var2
```

Ten kod może spowodować, że [efekt uboczny](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne może utrudnić debugowanie bardziej poprzez zmianę sposobu, w których działa aplikacja.

Wyrażenie z efektami ubocznymi jest oceniane tylko raz, po przejściu go. Po tym, znajduje się wyrażenie wygaszone w **Obejrzyj** okna i dalsze oceny są wyłączone. Etykietka narzędzia lub **wartość** kolumny wyjaśniono, że wyrażenie powoduje, że efekt uboczny. Możesz wymusić ponowne oszacowanie, wybierając ikonę odświeżania, który pojawia się obok wartości.

Jednym ze sposobów, aby uniknąć oznaczenia efekty uboczne jest, aby wyłączyć funkcję automatycznej oceny. W **narzędzia** > **opcje** > **debugowanie** > **ogólne**, usuń zaznaczenie opcji **Włącz obliczanie właściwości i inne niejawne wywołania funkcji**.

Dla C# tylko wtedy, gdy oceny właściwości i niejawne wywołania funkcji jest wyłączone, możesz wymusić oceny, dodając **ac** modyfikator formatu do zmiennej **nazwa** w **wyrażenie kontrolne**  okna. Zobacz [Specyfikatory w języku C# formatu](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> Użyj identyfikatorów obiektów w oknie czujki (C# i Visual Basic)

Czasami chcesz obserwować zachowanie określonego obiektu. Na przykład można śledzić obiekt określony przez zmienną lokalną przeszedł do tej zmiennej poza zakres tej asysty. W C# i Visual Basic można tworzyć identyfikatory obiektów dla konkretnych wystąpień typów referencyjnych i używać ich w **Obejrzyj** okna w warunków punktu przerwania. Identyfikator obiektu jest generowany przez środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług i powiązane z obiektem.

> [!NOTE]
> Identyfikatory obiektów Utwórz uszkodzonymi odwołaniami, które nie uniemożliwiają jako elementu bezużytecznego zbierane przez obiekt. Są one prawidłowe tylko dla bieżącej sesji debugowania.

W poniższym kodzie `MakePerson()` metoda tworzy `Person` przy użyciu zmiennej lokalnej:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

Aby dowiedzieć się, nazwa `Person` w `DoSomething()` metody, można dodać odwołania do `Person` Identyfikatora obiektu w **Obejrzyj** okna.

1. Ustaw punkt przerwania w kodzie po `Person` obiekt został utworzony.

1. Rozpocznij debugowanie.

1. Wstrzymuje wykonywanie w punkcie przerwania, otwarcie **lokalne** okna, wybierając **debugowania** > **Windows** > **zmiennychlokalnych**.

1. W **lokalne** okna, kliknij prawym przyciskiem myszy `Person` zmiennych i wybierz pozycję **wprowadzić identyfikator obiektu**.

   Powinien zostać wyświetlony znak dolara ( **$** ) oraz liczbą **lokalne** okno, które jest identyfikatora obiektu.

1. Dodaj identyfikator obiektu do **Obejrzyj** okna, kliknij prawym przyciskiem myszy identyfikator obiektu i wybierając **Dodaj czujkę**.

1. Ustaw kolejny punkt przerwania w `DoSomething()` metody.

1. Kontynuuj, debugowanie. Podczas wykonywania przerw w `DoSomething()` metody **Obejrzyj** jest wyświetlana w oknie `Person` obiektu.

   > [!NOTE]
   > Jeśli chcesz wyświetlić właściwości tego obiektu, takie jak `Person.Name`, należy włączyć oceny właściwości, wybierając **narzędzia** > **opcje**  >   **Debugowanie** > **ogólne** > **Włącz obliczanie właściwości i inne niejawne wywołania funkcji**.

## <a name="dynamic-view-and-the-watch-window"></a>Dynamiczny widok i w oknie czujki

Niektóre języki skryptów (na przykład, JavaScript lub Python) Użyj dynamicznych lub [kaczka](https://en.wikipedia.org/wiki/Duck_typing) wpisując i platformy .NET w wersji 4.0 lub nowszy obsługuje obiekty, które są trudne do obserwowania normalne debugowania systemu Windows.

**Obejrzyj** wyświetlana w oknie te obiekty jako obiekty dynamiczne, które są tworzone na podstawie typów implementujących <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejsu. Węzły obiektów dynamicznych Pokaż dynamiczne elementy członkowskie obiektów dynamicznych, ale nie zezwalaj na edytowanie wartości elementów członkowskich.

Aby odświeżyć **dynamiczny widok** wartości, wybierz opcję [ikonę odświeżania](#bkmk_refreshWatch) obok węzła obiekt dynamiczny.

Mają być wyświetlane tylko **dynamiczny widok** dla obiektu, Dodaj **dynamiczne** specyfikatora formatu po nazwie obiekt dynamiczny **Obejrzyj** okna:

- Dla języka C#: `ObjectName, dynamic`
- Dla języka Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- C# Debugera nie automatycznie Oblicz ponownie wartości w **dynamiczny widok** po kroku do następnego wiersza kodu.
>- Debuger programu Visual Basic automatycznie odświeża dodane za pomocą wyrażenia **dynamiczny widok**.
>- Ocena członków **dynamiczny widok** może mieć [efekty uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Aby wstawić nowe wyrażenie kontrolne zmiennej, rzutuje obiekt dynamiczny obiektu:**

1. Kliknij prawym przyciskiem myszy dowolnego podrzędnym **dynamiczny widok**.
1. Wybierz **Dodaj wyrażenie kontrolne**. `object.name` Staje się `((dynamic) object).name` i pojawia się w nowym **Obejrzyj** okna.

Dodaje także debugera **dynamiczny widok** węzeł podrzędny obiektu **Autos** okna. Aby otworzyć **automatyczne** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **Autos**.

**Widok dynamiczny** również zwiększa debugowania dla obiektów COM. Gdy debuger pobiera zapakowane w obiekt COM **.__ComObject**, dodaje **dynamiczny widok** węzła dla obiektu.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Obserwuj pojedynczej zmiennej lub wyrażenia w QuickWatch

Możesz użyć **QuickWatch** do obserwowania pojedynczej zmiennej.

Na przykład następujący kod:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

Aby obserwować `a` zmiennej

1. Ustaw punkt przerwania na `a = a + b;` wiersza.

1. Rozpocznij debugowanie. Wstrzymuje wykonywanie w punkcie przerwania.

1. Wybierz zmienną `a` w kodzie.

1. Wybierz **debugowania** > **QuickWatch**, naciśnij klawisz **Shift**+**F9**, lub kliknij prawym przyciskiem myszy i wybierz polecenie **QuickWatch**.

   **QuickWatch** zostanie wyświetlone okno dialogowe. `a` Zmiennej znajduje się w **wyrażenie** polu z **wartość** z **1**.

   ![Zmienna QuickWatch](../debugger/media/quickwatchvariable.png "Zmienna QuickWatch")

1. Aby szacować wyrażenia za pomocą zmiennej, wpisz wyrażenie takich jak `a + b` w **wyrażenie** i zaznacz **to ponowne ocenienie**.

   ![Wyrażenie QuickWatch](../debugger/media/quickwatchexpression.png "Wyrażenie QuickWatch")

1. Aby dodać zmiennej lub wyrażenia z **QuickWatch** do **Obejrzyj** wybierz **Dodaj wyrażenie kontrolne**.

1. Wybierz **Zamknij** zamknąć **QuickWatch** okna. (**QuickWatch** jest modalne okno dialogowe, więc nie można kontynuować debugowanie tak długo, jak jest otwarty.)

1. Kontynuuj, debugowanie. Możesz obserwować zmiennej w **Obejrzyj** okna.

## <a name="see-also"></a>Zobacz także
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Techniki i narzędzia debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na profilowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
