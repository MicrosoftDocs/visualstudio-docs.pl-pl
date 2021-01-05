---
title: Ustaw czujkę na zmienne | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: how-to
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
ms.openlocfilehash: d7e2a05fe84b023a60ef75f0cb262a08fc02587a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727427"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Obejrzyj zmienne z oknami Watch i QuickWatch

Gdy debugujesz, możesz użyć okien kontrolnych **Watch** i **QuickWatch** , aby obejrzeć zmienne i wyrażenia. System Windows jest dostępny tylko podczas sesji debugowania.

Okna **czujki** mogą wyświetlać kilka zmiennych jednocześnie podczas debugowania. W oknie dialogowym **QuickWatch** jest wyświetlana pojedyncza zmienna i musi być ZAMKNIĘTA, zanim będzie można kontynuować debugowanie.

> [!NOTE]
> Jeśli po raz pierwszy podjęto próbę debugowania kodu, przed przeprowadzeniem tego artykułu warto przeczytać [debugowanie dla bezwzględnych](../debugger/debugging-absolute-beginners.md) [technik i narzędzi debugowania](../debugger/write-better-code-with-visual-studio.md) .

## <a name="observe-variables-with-a-watch-window"></a>Obserwuj zmienne z okno wyrażeń kontrolnych

Można otworzyć więcej niż jedno okno **czujki** i obserwować więcej niż jedną zmienną w oknie **czujki** .

Na przykład, aby ustawić czujkę na wartościach `a` , `b` i `c` w poniższym kodzie:

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

1. Ustaw punkt przerwania w `c = a + b;` wierszu, klikając na lewym marginesie pozycję **Debuguj**  >  **Przełącz punkt przerwania** lub naciskając klawisz **F9**.

1. Rozpocznij debugowanie, wybierając zieloną strzałkę **startową** lub **Debuguj**  >  **Rozpocznij debugowanie** lub naciśnij klawisz **F5**. Wykonywanie jest wstrzymywane w punkcie przerwania.

1. Otwórz okno **czujki** , wybierając **Debuguj**  >  **Windows**  >  **Watch**  >  **Watch 1** lub naciśnij **klawisze CTRL** + **Alt** + **W**  >  **1**.

   Możesz otworzyć dodatkowe okna **czujki** , wybierając pozycję Windows **2**, **3** lub **4**.

1. W oknie **czujka** zaznacz pusty wiersz i wpisz zmienna `a` . Wykonaj te same czynności dla `b` i `c` .

   ![Obserwowanie zmiennych](../debugger/media/watchvariables.png "WatchVariables")

1. Kontynuuj debugowanie, wybierając pozycję **Debuguj** do  >  **kroku** lub naciskając klawisz **F11** w razie potrzeby. Wartości zmiennych w oknie **czujki** zmieniają się podczas iteracji `for` pętli.

>[!NOTE]
>Tylko w języku C++
>- Może być konieczne zakwalifikowanie kontekstu nazwy zmiennej lub wyrażenia, które używa nazwy zmiennej. Kontekst jest funkcją, plikiem źródłowym lub modułem, gdzie znajduje się zmienna. Jeśli musisz zakwalifikować kontekst, użyj składni [operatora kontekstu (C++)](../debugger/context-operator-cpp.md) w **nazwie** w oknie **czujki** .
>
>- Nazwy rejestrów i nazw zmiennych można dodawać przy użyciu **$\<register&nbsp;name>** lub **@\<register&nbsp;name>** do **nazwy** w oknie **czujki** . Aby uzyskać więcej informacji, zobacz [pseudozmiennych pokazanych](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Używanie wyrażeń w okno wyrażeń kontrolnych

Można obserwować dowolne prawidłowe wyrażenie rozpoznawane przez debuger w oknie **czujki** .

Na przykład dla kodu w poprzedniej sekcji można uzyskać średnią z trzech wartości, wprowadzając `(a + b + c) / 3` w oknie **czujka** :

![Wyrażenie czujki](../debugger/media/watchexpression.png "Wyrażenie czujki")

Reguły oceniania wyrażeń w oknie **czujki** są generalnie takie same jak reguły oceniania wyrażeń w języku kodu. Jeśli wyrażenie ma błąd składniowy, oczekiwano tego samego błędu kompilatora jak w edytorze kodu. Na przykład literówka w powyższym wyrażeniu generuje ten błąd w oknie **czujka** :

![Błąd wyrażenia czujki](../debugger/media/watchexpressionerror.png "Błąd wyrażenia czujki")

W oknie **czujka** może pojawić się okrąg z dwiema falistymi liniami. Ta ikona oznacza, że debuger nie oblicza wyrażenia ze względu na potencjalną zależność między wątkami. Ocenianie kodu wymaga tymczasowego uruchomienia innych wątków w aplikacji, ale ponieważ jest w trybie przerwania, wszystkie wątki w aplikacji są zwykle zatrzymane. Umożliwienie tymczasowego uruchamiania innych wątków może mieć nieoczekiwany wpływ na stan aplikacji, a debuger może ignorować zdarzenia, takie jak punkty przerwania i wyjątki w tych wątkach.

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

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Odśwież wartości czujki

Ikona odświeżania (strzałka okrągła) może pojawić się w oknie **czujki** , gdy wyrażenie jest oceniane. Ikona odświeżania wskazuje błąd lub wartość, która jest nieaktualna.

Aby odświeżyć wartość, wybierz ikonę odświeżania lub naciśnij klawisz spacji. Debuger próbuje wykonać ponowną ocenę wyrażenia. Niemniej jednak użytkownik może nie chcieć lub być w stanie przeprowadzić ponowną ocenę wyrażenia, w zależności od tego, dlaczego wartość nie została oceniona.

Umieść kursor nad ikoną odświeżania lub Wyświetl kolumnę **wartość** , dla której ma zostać obliczone wyrażenie. Przyczyny:

- Wystąpił błąd podczas obliczania wyrażenia, jak w poprzednim przykładzie. Może wystąpić przekroczenie limitu czasu lub zmienna może być poza zakresem.

- Wyrażenie zawiera wywołanie funkcji, które może wyzwolić efekt uboczny w aplikacji. Zobacz [efekty uboczne wyrażenia](#bkmk_sideEffects).

- Automatyczna Ocena właściwości i niejawne wywołania funkcji jest wyłączona.

Jeśli zostanie wyświetlona ikona odświeżenia, ponieważ automatyczna Ocena właściwości i niejawne wywołania funkcji jest wyłączona, można ją włączyć, wybierając opcję **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji** w oknie **Narzędzia**  >  **Opcje**  >  **debugowania**  >  **Ogólne**.

Aby zademonstrować przy użyciu ikony odświeżania:

1. W obszarze **Narzędzia**  >  **Opcje**  >  **debugowania**  >  **Ogólne** wyczyść pole wyboru **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji** .

1. Wprowadź następujący kod, a następnie w oknie **czujki** Ustaw kontrolkę na `list.Count` właściwości.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Uruchom debugowanie. Okno **czujki** pokazuje podobny komunikat:

   ![Odśwież czujkę](../debugger/media/refreshwatch.png "Odśwież czujkę")

1. Aby odświeżyć wartość, wybierz ikonę odświeżania lub naciśnij klawisz spacji. Debuger przeszacuje wyrażenie.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Efekty uboczne wyrażenia

Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan aplikacji. Na przykład Ocena następującego wyrażenia zmienia wartość `var1` :

```csharp
var1 = var2
```

Ten kod może spowodować [efekt uboczny](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne mogą utrudniać debugowanie, zmieniając sposób działania aplikacji.

Wyrażenie z efektami ubocznymi jest oceniane tylko raz, po jego wprowadzeniu po raz pierwszy. Następnie wyrażenie pojawia się wyszarzone w oknie **czujki** , a dalsze oceny są wyłączone. Kolumna etykietka narzędzia lub **wartość** objaśnia, że wyrażenie powoduje efekt uboczny. Możesz wymusić ponowną ocenę, wybierając ikonę odświeżania, która pojawia się obok wartości.

Jednym ze sposobów zapobiegania wyznaczeniu efektów ubocznych jest wyłączenie automatycznej oceny funkcji. W obszarze **Narzędzia**  >  **Opcje**  >  **debugowania**  >  **Ogólne** wybierz opcję **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**.

Tylko w przypadku języka C#, gdy Ocena właściwości lub niejawne wywołania funkcji jest wyłączona, można wymusić Obliczanie przez dodanie modyfikatora w formacie **AC** do **nazwy** zmiennej w oknie **czujka** . Zobacz [specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Używanie identyfikatorów obiektów w okno wyrażeń kontrolnych (C# i Visual Basic)

Czasami chcesz obserwować zachowanie określonego obiektu. Na przykład możesz chcieć śledzić obiekt, do którego odwołuje się zmienna lokalna po zakończeniu tej zmiennej. W językach C# i Visual Basic można tworzyć identyfikatory obiektów dla określonych wystąpień typów referencyjnych i używać ich w oknie **czujki** i w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) i skojarzone z obiektem.

> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania, które nie uniemożliwiają odzyskiwania obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.

W poniższym kodzie `MakePerson()` Metoda tworzy `Person` przy użyciu zmiennej lokalnej:

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

Aby sprawdzić nazwę `Person` w `DoSomething()` metodzie, można dodać odwołanie do `Person` identyfikatora obiektu w oknie **czujki** .

1. Ustaw punkt przerwania w kodzie po `Person` utworzeniu obiektu.

1. Uruchom debugowanie.

1. Po wstrzymaniu wykonywania w punkcie przerwania Otwórz okno zmienne **lokalne** , wybierając pozycję **Debuguj**  >    >  **Ustawienia regionalne** systemu Windows.

1. W oknie zmiennych **lokalnych** kliknij prawym przyciskiem myszy `Person` zmienną i wybierz pozycję **Utwórz identyfikator obiektu**.

   Powinien zostać wyświetlony znak dolara ( **$** ) i numer w oknie **zmiennych lokalnych** , który jest identyfikatorem obiektu.

1. Aby dodać identyfikator obiektu do okna **czujki** , kliknij prawym przyciskiem myszy identyfikator obiektu i wybierz polecenie **Dodaj czujkę**.

1. Ustaw inny punkt przerwania w `DoSomething()` metodzie.

1. Kontynuuj debugowanie. Gdy wykonywanie jest wstrzymywane w `DoSomething()` metodzie, okno **czujki** wyświetla `Person` obiekt.

   > [!NOTE]
   > Jeśli chcesz zobaczyć właściwości obiektu, takie jak `Person.Name` , musisz włączyć obliczanie właściwości, wybierając opcje **Narzędzia**  >    >  **debugowanie**  >  **Ogólne**  >  **Włącz Obliczanie właściwości i inne niejawne wywołania funkcji**.

## <a name="dynamic-view-and-the-watch-window"></a>Widok dynamiczny i okno wyrażeń kontrolnych

Niektóre języki skryptów (na przykład JavaScript lub Python) używają tekstu dynamicznego lub [kaczego](https://en.wikipedia.org/wiki/Duck_typing) , a program .NET w wersji 4,0 lub nowszej obsługuje obiekty, które trudno obserwować w zwykłych oknach debugowania.

Okno **czujki** wyświetla te obiekty jako obiekty dynamiczne, które są tworzone na podstawie typów, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejs. Dynamiczne węzły obiektów wyświetlają dynamiczne elementy członkowskie obiektów dynamicznych, ale nie zezwalają na edytowanie wartości elementów członkowskich.

Aby odświeżyć **dynamiczne wartości widoku** , wybierz [ikonę odświeżania](#bkmk_refreshWatch) obok węzła obiektu dynamicznego.

Aby wyświetlić tylko **Widok dynamiczny** dla obiektu, należy dodać specyfikator formatu **dynamicznego** po nazwie obiektu dynamicznego w oknie **czujka** :

- Dla języka C#: `ObjectName, dynamic`
- Dla Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Debuger C# nie oblicza automatycznie wartości w **widoku dynamicznym** po przekroczeniu następnego wiersza kodu.
>- Debuger Visual Basic automatycznie odświeża wyrażenia dodawane przez **Widok dynamiczny**.
>- Ocenianie elementów członkowskich **widoku dynamicznego** może mieć [skutki uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Aby wstawić nową zmienną czujki, która rzutuje obiekt na obiekt dynamiczny:**

1. Kliknij prawym przyciskiem myszy dowolny element podrzędny **widoku dynamicznego**.
1. Wybierz pozycję **Dodaj czujkę**. Zostanie `object.name` `((dynamic) object).name` wyświetlona w nowym oknie **czujki** .

Debuger dodaje również węzeł podrzędny **widoku dynamicznego** obiektu do okna **automatycznie** . Aby otworzyć okno **autostarts** , podczas debugowania wybierz opcję **Debuguj**  >    >  **autostarty** systemu Windows.

**Widok dynamiczny** rozszerza również debugowanie obiektów com. Gdy debuger odzyskuje obiekt COM otoczony **System.__ComObject**, dodaje **dynamiczny węzeł widoku** dla obiektu.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Obserwuj pojedynczą zmienną lub wyrażenie z QuickWatch

Można użyć **QuickWatch** do obserwowania pojedynczej zmiennej.

Na przykład dla następującego kodu:

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

Aby obserwować `a` zmienną,

1. Ustaw punkt przerwania w `a = a + b;` wierszu.

1. Uruchom debugowanie. Wykonywanie jest wstrzymywane w punkcie przerwania.

1. Wybierz zmienną `a` w kodzie.

1. Wybierz pozycję **Debuguj**  >  **QuickWatch**, naciśnij klawisz **SHIFT** + **F9** lub kliknij prawym przyciskiem myszy, a następnie wybierz pozycję **QuickWatch**.

   Zostanie wyświetlone okno dialogowe **QuickWatch** . `a`Zmienna znajduje się w polu **wyrażenie** z **wartością** **1**.

   ![Zmienna QuickWatch](../debugger/media/quickwatchvariable.png "Zmienna QuickWatch")

1. Aby oszacować wyrażenie przy użyciu zmiennej, wpisz wyrażenie, takie jak `a + b` w polu **wyrażenie** , a następnie wybierz pozycję **Oblicz** ponownie.

   ![Wyrażenie QuickWatch](../debugger/media/quickwatchexpression.png "Wyrażenie QuickWatch")

1. Aby dodać zmienną lub wyrażenie z **QuickWatch** do okna **czujki** , wybierz pozycję **Dodaj czujkę**.

1. Wybierz pozycję **Zamknij** , aby zamknąć okno **QuickWatch** . (**QuickWatch** to modalne okno dialogowe, dlatego nie można kontynuować debugowania, dopóki jest otwarte).

1. Kontynuuj debugowanie. Można obserwować zmienną w oknie **czujki** .

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Najpierw Spójrz na Debugowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
