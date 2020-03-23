---
title: Ustawianie zegarka na zmiennych | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302008"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Obserwuj zmienne za pomocą okien zegarka i zegarka QuickWatch

Podczas debugowania można używać **watch** windows i **QuickWatch** do oglądania zmiennych i wyrażeń. Okna są dostępne tylko podczas sesji debugowania.

**Okna zegarka** mogą wyświetlać kilka zmiennych naraz podczas debugowania. Okno dialogowe **QuickWatch** wyświetla pojedynczą zmienną naraz i musi zostać zamknięty, zanim debugowanie będzie można kontynuować.

Jeśli jest to pierwszy raz, który próbowałeś debugować kod, można przeczytać [debugowanie dla początkujących absolutnych](../debugger/debugging-absolute-beginners.md) i [debugowanie technik i narzędzi](../debugger/write-better-code-with-visual-studio.md) przed przejściem przez ten artykuł.

## <a name="observe-variables-with-a-watch-window"></a>Obserwowanie zmiennych za pomocą okna czujki

Można otworzyć więcej niż jedno okno **czujki** i obserwować więcej niż jedną zmienną w oknie **czujki.**

Na przykład, aby ustawić zegarek `a`na `b`wartości `c` , i w poniższym kodzie:

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

1. Ustaw punkt przerwania `c = a + b;` w wierszu, klikając lewy margines, wybierając **pozycję Debug** > **Toggle Breakpoint**lub naciskając **klawisz F9**.

1. Rozpocznij debugowanie, wybierając zieloną strzałkę **Start** lub **Debugowanie** > **startowe**lub naciśnij **klawisz F5**. Wykonywanie wstrzymuje się w punkcie przerwania.

1. Otwórz okno **Czujka,** wybierając **pozycję Debugowanie** > **zegarka** > **Windows** > Watch**1**lub **naciśnięcie klawisza Ctrl**+**Alt**+**W** > **1**.

   Dodatkowe okna **zegarka** można otworzyć, wybierając system Windows **2,** **3**lub **4**.

1. W oknie **Czujka** zaznacz pusty wiersz `a`i wpisz zmienną . Zrób to `b` samo `c`dla i .

   ![Wyrażenia kontrolne zmiennych](../debugger/media/watchvariables.png "WatchVariables (Odmiany zegarków)")

1. Kontynuuj debugowanie, wybierając **debugowanie** > **step into** lub naciskając klawisz **F11** w razie potrzeby, aby przejść. Wartości zmiennych w oknie **Czujka** zmieniają się `for` podczas iteracji w pętli.

>[!NOTE]
>Tylko w przypadku języka C++
>- Może być konieczne zakwalifikowanie kontekstu nazwy zmiennej lub wyrażenia, które używa nazwy zmiennej. Kontekstem jest funkcja, plik źródłowy lub moduł, w którym znajduje się zmienna. Jeśli musisz zakwalifikować kontekst, użyj składni [operatora kontekstu (C++)](../debugger/context-operator-cpp.md) w **oknie Nazwa** w oknie **Czujka.**
>
>- Nazwy rejestru i nazwy zmiennych można dodawać przy użyciu ** $ \<nazwy rejestru&nbsp;>** lub ** @ \<>nazwy rejestru&nbsp;** do **nazwy** w oknie **Czujka.** Aby uzyskać więcej informacji, zobacz [Pseudowariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Używanie wyrażeń w oknie czujki

Można zaobserwować dowolne prawidłowe wyrażenie rozpoznawane przez debuger w oknie **czujki.**

Na przykład dla kodu w poprzedniej sekcji można uzyskać średnią z trzech `(a + b + c) / 3` wartości, wprowadzając w **watch** okna:

![Wyrażenie zegarka](../debugger/media/watchexpression.png "Wyrażenie zegarka")

Reguły oceny wyrażeń w oknie **Czujki** są zazwyczaj takie same jak reguły oceny wyrażeń w języku kodu. Jeśli wyrażenie ma błąd składni, należy oczekiwać tego samego błędu kompilatora, jak w edytorze kodu. Na przykład literówka w poprzednim wyrażeniu powoduje ten błąd w oknie **Czujka:**

![Błąd wyrażenia obserwowanie](../debugger/media/watchexpressionerror.png "Błąd wyrażenia obserwowanie")

W oknie **Czujka** może pojawić się okrąg z ikoną dwóch falistych linii. Ta ikona oznacza, że debuger nie ocenia wyrażenia z powodu potencjalnej zależności między wątkami. Ocena kodu wymaga innych wątków w aplikacji, aby uruchomić tymczasowo, ale ponieważ jesteś w trybie przerwania, wszystkie wątki w aplikacji są zwykle zatrzymane. Zezwalając na tymczasowe uruchamianie innych wątków może mieć nieoczekiwany wpływ na stan aplikacji, a debuger może ignorować zdarzenia, takie jak punkty przerwania i wyjątki w tych wątkach.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Wyszukiwanie w oknie Czujka

Słowa kluczowe w kolumnach Nazwa, Wartość i Typ okna **Czujka** można wyszukiwać za pomocą paska wyszukiwania nad każdym oknem. Naciśnij klawisz ENTER lub wybierz jedną ze strzałek, aby przeprowadzić wyszukiwanie. Aby anulować trwające wyszukiwanie, wybierz ikonę "x" na pasku wyszukiwania.

Użyj strzałek w lewo i w prawo (Odpowiednio Shift+F3 i F3), aby poruszać się między znalezionymi dopasowaniami.

![Szukaj w oknie zegarka](../debugger/media/ee-search-watch.png "Szukaj w oknie zegarka")

Aby wyszukiwanie było mniej lub bardziej dokładne, użyj listy rozwijanej **Wyszukaj głębiej** w górnej części okna **Czujka,** aby wybrać liczbę poziomów głębokości, które chcesz przeszukać w obiektach zagnieżdżonych. 

## <a name="pin-properties-in-the-watch-window"></a>Właściwości pinów w oknie Czujka

>[!NOTE]
> Ta funkcja jest obsługiwana w pliku .NET Core 3.0 lub nowszym.

Za pomocą narzędzia **Właściwości pinnable** można szybko sprawdzić obiekty według ich właściwości w oknie Czujka.  Aby użyć tego narzędzia, umieść wskaźnik myszy na właściwości i wybierz ikonę pinezki, która się pojawi lub kliknij prawym przyciskiem myszy i wybierz opcję **Przypnij element członkowski jako ulubioną** w menu kontekstowym wynikowym.  Spowoduje to wyświetlenie tej właściwości na początku listy właściwości obiektu, a nazwa i wartość właściwości są wyświetlane w kolumnie **Wartość.**  Aby odpiąć właściwość, ponownie wybierz ikonę pinezki lub wybierz opcję **Odpnij element członkowski jako ulubioną** w menu kontekstowym.

![Właściwości pinów w oknie Czujka](../debugger/media/basic-pin-watch.gif "Właściwości pinów w oknie Czujka")

Podczas wyświetlania listy właściwości obiektu w oknie Czujka można również przełączać nazwy właściwości i odfiltrowywać właściwości nieprzypięte.  Dostęp do obu opcji można uzyskać, wybierając przyciski na pasku narzędzi nad oknem zegarka.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Odświeżanie wartości zegarka

Podczas oceny wyrażenia w oknie **czujki** może pojawić się ikona odświeżania (strzałka kołowa). Ikona odświeżania wskazuje błąd lub wartość, która jest nieaktualna.

Aby odświeżyć wartość, wybierz ikonę odświeżania lub naciśnij spację. Debuger próbuje ponownie ocenić wyrażenie. Jednak może nie chcesz lub być w stanie ponownie ocenić wyrażenie, w zależności od tego, dlaczego wartość nie została oceniona.

Umieść wskaźnik myszy na ikonie odświeżania lub zobacz kolumnę **Wartość** z powodu, dla którego wyrażenie nie zostało ocenione. Powody to:

- Wystąpił błąd podczas obliczania wyrażenia, tak jak w poprzednim przykładzie. Może wystąpić limit czasu lub zmienna może być poza zakresem.

- Wyrażenie ma wywołanie funkcji, które może wywołać efekt uboczny w aplikacji. Zobacz [Efekty uboczne ekspresji](#bkmk_sideEffects).

- Automatyczna ocena właściwości i wywołania funkcji niejawnych jest wyłączona.

Jeśli pojawi się ikona odświeżania, ponieważ automatyczna ocena właściwości i wywołań funkcji niejawnych jest wyłączona, można ją włączyć, wybierając **pozycję Włącz ocenę właściwości i inne wywołania funkcji niejawnych** w obszarze**Opcje** >  **narzędzia** > **Debugowanie** > **ogólne**.

Aby zademonstrować użycie ikony odświeżania:

1. W **obszarze** > **Opcje** > narzędzi**Debugowanie** > **ogólne**wyczyść pole wyboru Włącz ocenę właściwości i inne **wywołania funkcji niejawnych.**

1. Wprowadź następujący kod, a w oknie **Czujka** `list.Count` ustaw zegarek we właściwości.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Rozpocznij debugowanie. W oknie **Czujka** jest wyświetlany komunikat o następującej treści:

   ![Odświeżyć zegarek](../debugger/media/refreshwatch.png "Odświeżyć zegarek")

1. Aby odświeżyć wartość, wybierz ikonę odświeżania lub naciśnij spację. Debuger ponownie oceni wyrażenie.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Efekty uboczne ekspresji

Ocena niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan aplikacji. Na przykład ocena następującego wyrażenia zmienia `var1`wartość:

```csharp
var1 = var2
```

Ten kod może powodować [efekt uboczny](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Skutki uboczne mogą utrudnić debugowanie, zmieniając sposób działania aplikacji.

Wyrażenie z efektami ubocznymi jest oceniane tylko raz, przy pierwszym wprowadzeniu go. Następnie wyrażenie jest wyszarzone w oknie **czujki,** a dalsze oceny są wyłączone. Etykietka narzędzia lub **Wartość** kolumna wyjaśnia, że wyrażenie powoduje efekt uboczny. Można wymusić ponowną wycenę, wybierając ikonę odświeżania, która pojawia się obok wartości.

Jednym ze sposobów zapobiegania oznaczeniu skutków ubocznych jest wyłączenie automatycznej oceny funkcji. W **obszarze** > **Opcje** > narzędzi**Debugowanie** > **ogólne**usuń zaznaczenie opcji Włącz ocenę właściwości i inne **wywołania funkcji niejawnych**.

Tylko dla języka C#, gdy ocena właściwości lub wywołania funkcji niejawnych jest wyłączona, można wymusić ocenę, dodając modyfikator formatu **ac** do zmiennej **Name** w oknie **Czujka.** Zobacz [Formatowanie specyfikatorów w języku C#](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>Używanie identyfikatorów obiektów w oknie czujki (C# i Visual Basic)

Czasami chcesz obserwować zachowanie określonego obiektu. Na przykład można śledzić obiekt, do którego odwoływała się zmienna lokalna po tym, jak ta zmienna wyszła poza zakres. W językach C# i Visual Basic można tworzyć identyfikatory obiektów dla określonych wystąpień typów odwołań i używać ich w oknie **Czujka** i w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania wspólnego środowiska wykonawczego języka (CLR) i skojarzony z obiektem.

> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania, które nie uniemożliwiają śmietnika obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.

W poniższym kodzie `MakePerson()` metoda `Person` tworzy przy użyciu zmiennej lokalnej:

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

Aby dowiedzieć się `Person` nazwę `DoSomething()` w metodzie, można dodać `Person` odwołanie do identyfikatora obiektu w oknie **Czujka.**

1. Ustaw punkt przerwania w `Person` kodzie po utworzeniu obiektu.

1. Rozpocznij debugowanie.

1. Gdy wykonanie zostanie wstrzymane w punkcie przerwania, otwórz okno **Zmienne lokalne,** wybierając **pozycję Debugowanie** > **lokalnych miejscowych****systemu Windows** > .

1. W oknie **Zmienne lokalne** `Person` kliknij prawym przyciskiem myszy zmienną i wybierz polecenie **Make Object ID**.

   Powinien zostać wyświetlony znak**$** dolara ( ) plus liczba w oknie **Zmiennika,** który jest identyfikatorem obiektu.

1. Dodaj identyfikator obiektu do okna **Czujka,** klikając prawym przyciskiem myszy identyfikator obiektu i wybierając polecenie **Dodaj zegarek**.

1. Ustaw inny punkt `DoSomething()` przerwania w metodzie.

1. Kontynuuj debugowanie. Po wstrzymaniu wykonywania `DoSomething()` w metodzie **watch** okno wyświetla `Person` obiekt.

   > [!NOTE]
   > Jeśli chcesz zobaczyć właściwości obiektu, takie jak `Person.Name`, należy włączyć ocenę właściwości, wybierając opcję > **Opcje** > **debugowania** >  **narzędzia****Ogólne** > **włącz ocenę właściwości i inne wywołania funkcji niejawnych.**

## <a name="dynamic-view-and-the-watch-window"></a>Widok dynamiczny i okno Czujka

Niektóre języki skryptów (na przykład JavaScript lub Python) używają dynamicznego lub [pisania kaczek,](https://en.wikipedia.org/wiki/Duck_typing) a .NET w wersji 4.0 i nowszej obsługuje obiekty, które są trudne do zaobserwowania w normalnych oknach debugowania.

Okno **Czujka** wyświetla te obiekty jako obiekty dynamiczne, <xref:System.Dynamic.IDynamicMetaObjectProvider> które są tworzone z typów implementuujnych interfejsu. Dynamiczne węzły obiektów pokazują dynamiczne elementy członkowskie obiektów dynamicznych, ale nie zezwalają na edycję wartości elementów członkowskich.

Aby **odświeżyć** wartości widoku dynamicznego, zaznacz [ikonę odświeżania](#bkmk_refreshWatch) obok węzła obiektu dynamicznego.

Aby wyświetlić tylko **widok dynamiczny** obiektu, dodaj specyfikator formatu **dynamicznego** po nazwie obiektu dynamicznego w oknie **Czujka:**

- Dla języka C#:`ObjectName, dynamic`
- Dla visual basic:`$dynamic, ObjectName`

>[!NOTE]
>- Debuger języka C# nie automatycznie ponownie ocenić wartości w **widoku dynamicznym** po kroku do następnego wiersza kodu.
>- Debuger języka Visual Basic automatycznie odświeża wyrażenia dodane za pośrednictwem **widoku dynamicznego**.
>- Ocena członków widoku **dynamicznego** może mieć [skutki uboczne](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)).

**Aby wstawić nową zmienną zegarka, która rzutuje obiekt na obiekt dynamiczny:**

1. Kliknij prawym przyciskiem myszy dowolny podrzędny **widok dynamiczny**.
1. Wybierz **pozycję Dodaj zegarek**. Staje `object.name` `((dynamic) object).name` się i pojawia się w nowym oknie **czujki.**

Debuger dodaje również węzeł podrzędny **widoku dynamicznego** obiektu do okna **Autos.** Aby otworzyć okno **Autos,** podczas debugowania wybierz pozycję **Debugowanie** > **autos****systemu Windows** > .

**Widok dynamiczny** poprawia również debugowanie obiektów COM. Gdy debuger przechodzi do obiektu COM opakowanego w **system.__ComObject,** dodaje węzeł **widoku dynamicznego** dla obiektu.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Obserwowanie pojedynczej zmiennej lub wyrażenia za pomocą programu QuickWatch

Za pomocą programu **QuickWatch** można obserwować pojedynczą zmienną.

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

1. Ustaw punkt przerwania `a = a + b;` w wierszu.

1. Rozpocznij debugowanie. Wykonywanie wstrzymuje się w punkcie przerwania.

1. Wybierz zmienną `a` w kodzie.

1. Wybierz **pozycję Debugowanie** > **quickwatch**, naciśnij **klawisz Shift**+**F9**lub kliknij prawym przyciskiem myszy i wybierz szybki **zegarek**.

   Zostanie wyświetlone okno dialogowe **QuickWatch.** Zmienna `a` znajduje się w polu **Wyrażenie** o **wartości** **1**.

   ![Zmienna QuickWatch](../debugger/media/quickwatchvariable.png "Zmienna QuickWatch")

1. Aby ocenić wyrażenie przy użyciu zmiennej, wpisz wyrażenie, takie jak `a + b` w polu **Wyrażenie,** a następnie wybierz opcję Ponownie **oceniaj**.

   ![Wyrażenie QuickWatch](../debugger/media/quickwatchexpression.png "Wyrażenie QuickWatch")

1. Aby dodać zmienną lub wyrażenie z **szybkiego zegarka** do okna **czujki,** wybierz pozycję **Dodaj czujkę**.

1. Wybierz **przycisk Zamknij,** aby zamknąć okno **QuickWatch.** **(QuickWatch** jest modalne okno dialogowe, więc nie można kontynuować debugowania tak długo, jak jest otwarty.)

1. Kontynuuj debugowanie. Zmienną można obserwować w oknie **Czujka.**

## <a name="see-also"></a>Zobacz też
- [Co to jest debugowanie?](../debugger/what-is-debugging.md)
- [Narzędzia i techniki debugowania](../debugger/write-better-code-with-visual-studio.md)
- [Pierwsze spojrzenie na debugowanie](../debugger/debugger-feature-tour.md)
- [Okna debugera](../debugger/debugger-windows.md)
