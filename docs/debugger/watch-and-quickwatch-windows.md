---
title: Ustawianie zegarka dla zmiennych | Microsoft Docs
description: Podczas debugowania zobacz zmienne i wyrażenia w wyrażeniach Watch i QuickWatch. Czujka może wyświetlać kilka zmiennych, QuickWatch tylko jedną i tylko w przerwie.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: how-to
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 246f82b2d55e8e15bb5a56afba846a8b5dc8f245
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924906"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Obserwowanie zmiennych w oknach watch i QuickWatch

Podczas debugowania można używać  okien wyrażeń i funkcji **QuickWatch** do obserwowania zmiennych i wyrażeń. Okna są dostępne tylko podczas sesji debugowania.

**Okna** czujki mogą wyświetlać kilka zmiennych jednocześnie podczas debugowania. W oknie dialogowym **QuickWatch** jest wyświetlana pojedyncza zmienna na raz i należy ją zamknąć, aby można było kontynuować debugowanie.

> [!NOTE]
> Jeśli po raz pierwszy próbujesz debugować kod, przed przeczytaniem tego artykułu [](../debugger/write-better-code-with-visual-studio.md) warto przeczytać artykuł Debugowanie dla bezwzględnych początkujących oraz Techniki i narzędzia debugowania. [](../debugger/debugging-absolute-beginners.md)

## <a name="observe-variables-with-a-watch-window"></a>Obserwowanie zmiennych za pomocą okno wyrażeń kontrolnych

Możesz otworzyć więcej niż jedno **okno Czujka** i obserwować więcej niż jedną zmienną w **oknie Czujka.**

Aby na przykład ustawić zegarek dla wartości `a` , i w poniższym `b` `c` kodzie:

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

1. Ustaw punkt przerwania w wierszu, klikając lewy margines, wybierając `c = a + b;` pozycję   >  **Debuguj Przełącz** punkt przerwania lub naciskając **klawisz F9**.

1. Rozpocznij debugowanie, wybierając zieloną **strzałkę Start** lub **pozycję Debuguj** rozpocznij  >  **debugowanie** lub naciśnij klawisz **F5.** Wykonywanie jest wstrzymywane w punkcie przerwania.

1. Otwórz okno **Czujka,** wybierając pozycję **Debuguj**  >  **system Windows**  >  **Watch**  >  **1** lub naciskając klawisze **Ctrl** + **Alt** + **W**  >  **1**.

   Możesz otworzyć dodatkowe okna **czujki,** wybierając pozycję Windows **2,** **3** lub **4.**

1. W **oknie Czujka** wybierz pusty wiersz i wpisz zmienną `a` . Wykonaj to samo dla `b` i `c` .

   ![Wyrażenia kontrolne zmiennych](../debugger/media/watchvariables.png "WatchVariables")

1. Kontynuuj debugowanie, wybierając pozycję   >  **Debuguj krok do** lub naciskając **klawisz F11 w** razie potrzeby, aby przejść dalej. Wartości zmiennych w oknie **Czujka** zmieniają się podczas iteru w `for` pętli.

>[!NOTE]
>Tylko w przypadku języka C++
>- Może być konieczne kwalifikowanie kontekstu nazwy zmiennej lub wyrażenia, które używa nazwy zmiennej. Kontekstem jest funkcja, plik źródłowy lub moduł, w którym znajduje się zmienna. Jeśli musisz zakwalifikować kontekst, użyj składni [operatora kontekstu (C++)](../debugger/context-operator-cpp.md) w **nazwie** w oknie **Czujka.**
>
>- Możesz dodać nazwy rejestrów i nazwy zmiennych przy użyciu polecenia lub do **$\<register&nbsp;name>** **@\<register&nbsp;name>** **nazwy** w **oknie Czujka.** Aby uzyskać więcej informacji, zobacz [Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Używanie wyrażeń w okno wyrażeń kontrolnych

W oknie Wyrażenie czujki można obserwować dowolne prawidłowe wyrażenie rozpoznawane przez **debuger.**

Na przykład dla kodu w poprzedniej sekcji można uzyskać średnią z trzech wartości, wprowadzając `(a + b + c) / 3` w oknie **Czujka:**

![Wyrażenie czujki](../debugger/media/watchexpression.png "Wyrażenie czujki")

Reguły oceny wyrażeń w oknie **Wyrażenie** czujki są zwykle takie same jak reguły oceny wyrażeń w języku kodu. Jeśli wyrażenie ma błąd składniowy, należy oczekiwać tego samego błędu kompilatora, co w edytorze kodu. Na przykład literówka w powyższym wyrażeniu generuje ten błąd w oknie **Wyrażenie** czujki:

![Błąd wyrażenia wyrażeń obserwowanych](../debugger/media/watchexpressionerror.png "Błąd wyrażenia wyrażeń obserwowanych")

W oknie **Czujka** może pojawić się okrąg z dwiema liniami falistych. Ta ikona oznacza, że debuger nie ocenia wyrażenia ze względu na potencjalną zależność międzywątkową. Ocena kodu wymaga tymczasowego uruchomienia innych wątków w aplikacji, ale ponieważ jesteś w trybie przerwania, wszystkie wątki w aplikacji są zwykle zatrzymywane. Zezwolenie na tymczasowe uruchamianie innych wątków może mieć nieoczekiwany wpływ na stan aplikacji, a debuger może ignorować zdarzenia, takie jak punkty przerwania i wyjątki w tych wątkach.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Wyszukiwanie w okno wyrażeń kontrolnych

Słowa kluczowe można wyszukiwać w kolumnach Nazwa, Wartość i Typ w oknie **Czujka** przy użyciu paska wyszukiwania nad każdym oknem. Naciśnij klawisz ENTER lub wybierz jedną ze strzałek, aby wykonać wyszukiwanie. Aby anulować trwające wyszukiwanie, wybierz ikonę "x" na pasku wyszukiwania.

Użyj strzałek w lewo i w prawo (odpowiednio Shift+F3 i F3), aby przechodzić między znalezionymi dopasowaniami.

![Wyszukiwanie w oknie Czujka](../debugger/media/ee-search-watch.png "Wyszukiwanie w oknie Czujka")

Aby wyszukiwanie było bardziej lub mniej  dokładne, użyj listy rozwijanej Wyszukaj głębiej w górnej części okna **Czujka,** aby wybrać poziom głębokości, na którym chcesz wyszukać zagnieżdżone obiekty. 

## <a name="pin-properties-in-the-watch-window"></a>Przypinanie właściwości w okno wyrażeń kontrolnych

>[!NOTE]
> Ta funkcja jest obsługiwana w programie .NET Core 3.0 lub wyższym.

Możesz szybko sprawdzić obiekty według ich właściwości w okno wyrażeń kontrolnych przy użyciu narzędzia **Pinnable Properties.**  Aby użyć tego narzędzia, umieść kursor nad właściwością i wybierz wyświetloną ikonę pinezki lub kliknij prawym przyciskiem myszy i wybierz opcję Przypnij element **członkowski** jako ulubiony w wyświetlonym menu kontekstowym.  Ta właściwość jest wyświetlana na początku listy właściwości obiektu, a nazwa i wartość właściwości są wyświetlane w **kolumnie** Wartość.  Aby odpiąć właściwość, wybierz ponownie ikonę pinezki lub wybierz opcję Odepnij element **członkowski** jako ulubiony w menu kontekstowym.

![Przypinanie właściwości w okno wyrażeń kontrolnych](../debugger/media/basic-pin-watch.gif "Przypinanie właściwości w okno wyrażeń kontrolnych")

Można również przełączać nazwy właściwości i filtrować nie przypięte właściwości podczas wyświetlania listy właściwości obiektu w okno wyrażeń kontrolnych.  Dostęp do obu opcji można uzyskać, wybierając przyciski na pasku narzędzi nad oknem zegarka.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> Odśwież wartości zegarka

Ikona odświeżania (okrężna strzałka) może pojawić się w oknie **Czujka** podczas oceniania wyrażenia. Ikona odświeżania wskazuje błąd lub wartość, która jest przejaśliwie wyświetlana.

Aby odświeżyć wartość, wybierz ikonę odświeżania lub naciśnij spację. Debuger próbuje ponownie wartościować wyrażenie. Jednak możesz nie chcieć lub nie być w stanie ponownie ocenić wyrażenia, w zależności od tego, dlaczego wartość nie została oceniona.

Umieść kursor na ikonie odświeżania lub zobacz **kolumnę Wartość** z powodu, dla którego wyrażenie nie było oceniane. Przyczyny są następujące:

- Wystąpił błąd podczas oceniania wyrażenia, tak jak w poprzednim przykładzie. Może wystąpić limit czasu lub zmienna może być poza zakresem.

- Wyrażenie ma wywołanie funkcji, które może wyzwolić efekt uboczny w aplikacji. Zobacz [Efekty uboczne wyrażenia](#bkmk_sideEffects).

- Automatyczna ocena właściwości i niejawnych wywołań funkcji jest wyłączona.

Jeśli ikona odświeżania jest wyświetlana, ponieważ automatyczna ocena właściwości i  niejawnych wywołań funkcji jest wyłączona, możesz ją włączyć, wybierając pozycję Włącz ocenę właściwości i inne niejawne wywołania funkcji w oknie Narzędzia  >  **Opcje**  >  **Debugowanie**  >  **Ogólne.**

Aby zademonstrować użycie ikony odświeżania:

1. W **oknie**  >  **Narzędzia Opcje**  >    >  **debugowania Ogólne** wyczyść **pole wyboru Włącz ocenę właściwości i inne niejawne wywołania** funkcji.

1. Wprowadź następujący kod i w oknie **Czujka** ustaw dla właściwości `list.Count` zegarek.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Uruchom debugowanie. W **oknie** Czujka zostanie wyświetlony komunikat podobny do następującego:

   ![Odśwież zegarek](../debugger/media/refreshwatch.png "Odśwież zegarek")

1. Aby odświeżyć wartość, wybierz ikonę odświeżania lub naciśnij spację. Debuger ponownie wartościuje wyrażenie.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> Efekty uboczne wyrażenia

Ocena niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan aplikacji. Na przykład ocena następującego wyrażenia zmienia wartość `var1` :

```csharp
var1 = var2
```

Ten kod może powodować [efekt uboczny](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne mogą utrudnić debugowanie przez zmianę sposobu działania aplikacji.

Wyrażenie z efektami ubocznymi jest oceniane tylko raz, przy pierwszym wprowadzeniu. Po tym wyrażeniu w oknie  wyrażenie będzie wyszarowane, a dalsze oceny będą wyłączone. Etykietka narzędzia lub **kolumna Value** wyjaśnia, że wyrażenie powoduje efekt uboczny. Możesz wymusić ponowną wartość, wybierając ikonę odświeżania wyświetlaną obok wartości.

Jednym ze sposobów zapobiegania oznaczeniu efektów ubocznych jest wyłączenie automatycznej oceny funkcji. W **menu Opcje** narzędzi  >    >    >  **Debugowanie ogólne** usuń zaznaczenie **opcji Włącz ocenę właściwości i innych niejawnych wywołań funkcji**.

Tylko w przypadku języka C#, gdy ocena właściwości lub niejawnych wywołań funkcji jest wyłączona, można wymusić ocenę, dodając modyfikator formatu **ac** do zmiennej **Name** w oknie **Czujka.** Zobacz [Specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Używanie identyfikatorów obiektów w okno wyrażeń kontrolnych (C# i Visual Basic)

Czasami chcesz obserwować zachowanie określonego obiektu. Na przykład możesz chcieć śledzić obiekt, do którego odnosi się zmienna lokalna, po tym, jak ta zmienna wyszła poza zakres. W językach C# i Visual Basic można tworzyć identyfikatory obiektów dla określonych wystąpień  typów referencyjnych i używać ich w oknie Czujka i w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) i skojarzony z obiektem .

> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania, które nie uniemożliwiają odśmiecania obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.

W poniższym kodzie metoda `MakePerson()` tworzy przy użyciu zmiennej `Person` lokalnej:

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

Aby dowiedzieć się, jaka jest nazwa obiektu w metodzie , możesz dodać odwołanie do `Person` `DoSomething()` identyfikatora obiektu w `Person` **oknie Czujka.**

1. Ustaw punkt przerwania w kodzie po `Person` utworzeniu obiektu.

1. Uruchom debugowanie.

1. Po wstrzymaniu wykonywania w punkcie przerwania otwórz okno **Locals** (Lokalne), wybierając polecenie   >  **Debuguj lokalne systemy Windows**  >  .

1. W **oknie Zmienne** lokalne kliknij prawym przyciskiem myszy `Person` zmienną i wybierz polecenie **Make Object ID (Określ identyfikator obiektu).**

   W oknie Locals (Lokalne) powinien zostać wyświetlony znak dolara () plus **$** liczba, która jest identyfikatorem obiektu. 

1. Dodaj identyfikator obiektu do okna **Czujka,** klikając prawym przyciskiem myszy identyfikator obiektu i wybierając polecenie **Dodaj czujki**.

1. Ustaw inny punkt przerwania w `DoSomething()` metodzie .

1. Kontynuuj debugowanie. Po wstrzymaniu wykonywania `DoSomething()` w metodzie w **oknie Czujka** zostanie wyświetlony `Person` obiekt .

   > [!NOTE]
   > Jeśli chcesz wyświetlić właściwości obiektu, takie jak , musisz włączyć ocenę właściwości, wybierając pozycję Narzędzia Opcje Debugowanie Ogólne Włącz ocenę właściwości i inne `Person.Name`   >    >    >    >  **niejawne wywołania funkcji**.

## <a name="dynamic-view-and-the-watch-window"></a>Widok dynamiczny i okno wyrażeń kontrolnych

Niektóre języki skryptowe (na przykład JavaScript lub [](https://en.wikipedia.org/wiki/Duck_typing) Python) używają dynamicznego wpisywania typu "orzeł", a program .NET w wersji 4.0 lub nowszej obsługuje obiekty trudne do obserwowania w normalnych oknach debugowania.

W **oknie** Czujka te obiekty są wyświetlane jako obiekty dynamiczne, które są tworzone na podstawie typów, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> interfejs. Węzły obiektów dynamicznych pokazują dynamiczne elementy członkowskie obiektów dynamicznych, ale nie umożliwiają edytowania wartości elementów członkowskich.

Aby **odświeżyć wartości widoku** dynamicznego, wybierz ikonę [odświeżania](#bkmk_refreshWatch) obok węzła obiektu dynamicznego.

Aby wyświetlić tylko **widok dynamiczny** dla  obiektu, dodaj specyfikator formatu dynamicznego po nazwie obiektu dynamicznego w **oknie Czujka:**

- W przypadku języka C#: `ObjectName, dynamic`
- Na Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- Debuger języka C# nie automatycznie ponownie ceni wartości  w widoku dynamicznym podczas kroku do następnego wiersza kodu.
>- Debuger Visual Basic automatycznie odświeża wyrażenia dodane za pośrednictwem widoku **dynamicznego**.
>- Ocenianie elementów członkowskich widoku **dynamicznego może** mieć [skutki uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Aby wstawić nową zmienną czujki rzutowania obiektu na obiekt dynamiczny:**

1. Kliknij prawym przyciskiem myszy dowolny podrzędny widok **dynamiczny.**
1. Wybierz pozycję **Dodaj zegarek.** Zostanie `object.name` on wyświetlony w nowym `((dynamic) object).name` **oknie Czujka.**

Debuger dodaje również **węzeł podrzędny widoku** dynamicznego obiektu do okna **Automatyczne.** Aby otworzyć okno **Automatyczne,** podczas debugowania wybierz pozycję **Debuguj**  >  **automatyczne systemy Windows.**  >  

**Widok dynamiczny** usprawnia również debugowanie obiektów COM. Gdy debuger pobiera obiekt COM opakowany w System.__ComObject **,** dodaje **węzeł** widoku dynamicznego dla obiektu .

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Obserwowanie pojedynczej zmiennej lub wyrażenia za pomocą quickwatch

Możesz użyć funkcji **QuickWatch,** aby obserwować pojedynczą zmienną.

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

1. Wybierz **pozycję**  >  **Debuguj quickwatch,** **naciśnij klawisz Shift** F9 lub kliknij prawym przyciskiem myszy i wybierz pozycję +  **QuickWatch.**

   Zostanie **wyświetlone okno dialogowe QuickWatch.** Zmienna `a` znajduje się w polu **Wyrażenie** z **wartością** **1**.

   ![Zmienna QuickWatch](../debugger/media/quickwatchvariable.png "Zmienna QuickWatch")

1. Aby oszacować wyrażenie przy użyciu zmiennej, wpisz wyrażenie, takie jak w polu Wyrażenie, i wybierz pozycję `a + b` **Ponownie oceń**. 

   ![Wyrażenie QuickWatch](../debugger/media/quickwatchexpression.png "Wyrażenie QuickWatch")

1. Aby dodać zmienną lub wyrażenie z **aplikacji QuickWatch** do okna **Wyrażenie** czujki, wybierz pozycję **Dodaj wyrażenie czujki**.

1. Wybierz **pozycję Zamknij,** aby zamknąć **okno QuickWatch.** **(QuickWatch** to modalne okno dialogowe, więc nie można kontynuować debugowania, dopóki jest otwarte).

1. Kontynuuj debugowanie. Zmienną można obserwować w **oknie Czujka.**

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
