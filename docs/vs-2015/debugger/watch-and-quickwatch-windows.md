---
title: Obejrzyj i QuickWatch Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3f79e492440f98f733488afb241fa6f86e220b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780232"
---
# <a name="watch-and-quickwatch-windows"></a>Okna wyrażeń kontrolnych i szybkich wyrażeń kontrolnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **czujki** (**Debug/Windows/Watch/Watch (1, 2, 3, 4)**) i **QuickWatch** (kliknij prawym przyciskiem myszy pozycję zmienne/ **Debug/QuickWatch**), aby obejrzeć zmienne i wyrażenia podczas sesji debugowania.  Różnica polega na tym, że okno **czujki** może wyświetlać kilka zmiennych, podczas gdy okno **QuickWatch** Wyświetla pojedynczą zmienną jednocześnie.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Obserwowanie pojedynczej zmiennej za pomocą QuickWatch  
 Można użyć okna **QuickWatch** do obserwowania pojedynczej zmiennej. Na przykład, jeśli masz następujący kod:  
  
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
  
 Można obserwować zmienną w oknie QuickWatch w następujący sposób:  
  
1. Ustaw punkt przerwania w `a = a + b;` wierszu.  
  
2. Uruchom debugowanie. Wykonywanie jest zatrzymane w punkcie przerwania.  
  
3. Otwórz okno **QuickWatch** (kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Debuguj/QuickWatch**lub **SHIFT + F9**). Możesz otworzyć okno i dodać zmienną do okna **wyrażenia** , a następnie kliknąć przycisk **Oblicz**ponownie. Zmienna a powinna zostać wyświetlona w oknie **wartości** z wartością 2.  
  
4. Okno **QuickWatch** jest modalnym oknem okna dialogowego, dlatego nie można kontynuować debugowania o ile jest otwarte. Możesz dodać zmienną do okna **czujki** , klikając przycisk **Dodaj czujkę**.  
  
5. Zamknij okno **QuickWatch** . Teraz możesz kontynuować debugowanie, gdy zobaczysz wartość w oknie **czujka**  
  
## <a name="observing-variables-with-the-watch-window"></a>Obserwowanie zmiennych przy użyciu okno wyrażeń kontrolnych  
 Można obserwować wiele zmiennych przy użyciu okna **czujka** . Na przykład, jeśli masz następujący kod:  
  
```csharp  
static void Main(string[] args)  
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
}  
  
```  
  
 Dodaj wartości trzech zmiennych do okno wyrażeń kontrolnych w następujący sposób:  
  
1. Ustaw punkt przerwania w `c = a + b;` wierszu.  
  
2. Rozpocznij debugowanie (**F5**). Wykonywanie jest zatrzymane w punkcie przerwania.  
  
3. Otwórz okno wyrażeń kontrolnych (**Debuguj/Windows/Watch/Watch 1**lub **Ctrl + Alt + W, 1**).  
  
4. Dodaj `a` zmienną do pierwszego wiersza, `b` zmiennej do drugiego wiersza i `c` zmiennej do trzeciego wiersza.  
  
5. Kontynuuj debugowanie.  
  
   Wartości zmiennych powinny być zmieniane podczas iteracji przez `for` pętlę.  
  
   W przypadku programowania w kodzie natywnym może zajść konieczność zakwalifikowania kontekstu nazwy zmiennej lub wyrażenia zawierającego nazwę zmiennej. Kontekst jest funkcją, plikiem źródłowym i modułem, gdzie znajduje się zmienna. Jeśli trzeba to zrobić, można użyć składni operatora kontekstu. Aby uzyskać więcej informacji, zobacz wyrażenia w języku C++.  
  
## <a name="observing-expressions-with-the-watch-window"></a>Obserwowanie wyrażeń przy użyciu okno wyrażeń kontrolnych  
 Teraz Spróbujmy użyć wyrażenia zamiast tego. Można dodać dowolne prawidłowe wyrażenie rozpoznawane przez debuger.  
  
 Na przykład, jeśli masz kod wymieniony w poprzedniej sekcji, możesz uzyskać średnią z trzech wartości w następujący sposób:  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 Ogólnie rzecz biorąc, reguły szacowania wyrażeń w oknie **czujki** są takie same jak reguły oceniania wyrażeń w języku kodowania. Jeśli wyrażenie zawiera błąd składniowy, można oczekiwać tego samego błędu kompilatora, który zobaczysz w edytorze kodu. Oto przykład:  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
## <a name="refreshing-watch-values-that-are-out-of-date"></a><a name="bkmk_refreshWatch"></a> Odświeżanie wartości czujki, które są nieaktualne  
 W pewnych okolicznościach może zostać wyświetlona ikona odświeżania (okrąg z dwoma strzałkami lub okrąg z dwoma falistymi liniami), gdy wyrażenie jest oceniane w oknie **czujka** .  Na przykład jeśli wyłączono Obliczanie właściwości (**Narzędzia/Opcje/debugowanie/włączenie oceny właściwości i inne niejawne wywołania funkcji**), a masz następujący kod:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Jeśli ustawisz czujkę na `Count` Właściwości listy, zobaczysz coś podobne do następujących:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Wskazuje to na błąd lub wartość, która jest nieaktualna. Na ogół można odświeżyć wartość, klikając ikonę, ale w niektórych przypadkach może być preferowane, aby nie odświeżyć. Najpierw musisz wiedzieć, dlaczego wartość nie została oceniona.  
  
 Jeśli wskażesz ikonę, etykietka narzędzia zawiera informacje o tym, dlaczego wyrażenie nie zostało ocenione.  Jeśli pojawiają się strzałki krążące, wyrażenie nie zostało ocenione z jednego z następujących powodów:  
  
- • Wystąpił błąd podczas obliczania wyrażenia. Na przykład upłynął limit czasu lub zmienna może być poza zakresem.  
  
- • Wyrażenie zawiera wywołanie funkcji, które może wyzwolić efekt uboczny w aplikacji (zobacz [efekty uboczne i wyrażenia](#bkmk_sideEffects)).  
  
- Automatyczna Ocena właściwości i niejawne wywołania funkcji przez debuger jest wyłączone (**Narzędzia/Opcje/debugowanie/włączenie oceny właściwości i inne niejawne wywołania funkcji**), a następnie nie można automatycznie obliczyć wyrażenia.  
  
  Aby odświeżyć wartość, kliknij ikonę odświeżania lub naciśnij klawisz spacji. Debuger spróbuje ponownie obliczyć wyrażenie. Jeśli ikona odświeżania pojawiła się z powodu wyłączenia automatycznej oceny właściwości i niejawnych efektów ubocznych, można ocenić wyrażenie.  
  
  Jeśli zobaczysz ikonę, która jest kółkem zawierającym dwa faliste linie, które przypominają wątki, wyrażenie nie zostało ocenione ze względu na potencjalną zależność między wątkami. Innymi słowy, ocenianie kodu wymaga tymczasowego uruchomienia innych wątków w aplikacji. Gdy jesteś w trybie przerwania, wszystkie wątki w aplikacji są zwykle zatrzymane. Umożliwienie czasowego uruchamiania innych wątków może mieć nieoczekiwany wpływ na stan programu i powoduje, że debuger ignoruje zdarzenia, takie jak punkty przerwania i wyjątki zgłoszone w tych wątkach.  
  
## <a name="side-effects-and-expressions"></a><a name="bkmk_sideEffects"></a> Efekty uboczne i wyrażenia  
 Obliczenie niektórych wyrażeń może zmienić wartość zmiennej lub w inny sposób wpłynąć na stan programu. Na przykład Ocena następującego wyrażenia zmienia wartość `var1` :  
  
```  
var1 = var2  
```  
  
 Ta wartość jest nazywana [efektem ubocznym](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Efekty uboczne mogą utrudniać debugowanie, zmieniając sposób działania programu.  
  
 Wyrażenie, które jest znane z efektów ubocznych jest oceniane tylko raz, przy pierwszym wprowadzeniu go. Kolejne oceny są wyłączone. To zachowanie można zmienić ręcznie, klikając ikonę aktualizacji, która pojawia się obok wartości.  
  
 Jednym ze sposobów uniknięcia efektów ubocznych jest wyłączenie automatycznej oceny funkcji (**Narzędzia/Opcje/debugowanie/włączenie oceny właściwości i innych niejawnych wywołań funkcji**).  
  
 W przypadku wyłączenia oceny właściwości lub niejawnych wywołań funkcji można wymusić Obliczanie przy użyciu modyfikatora formatu **AC** (tylko w przypadku języka C#). Zobacz [specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>Korzystanie z identyfikatorów obiektów w okno wyrażeń kontrolnych (C# i Visual Basic)  
 Istnieją przypadki, w których chcesz obserwować zachowanie określonego obiektu; na przykład możesz chcieć śledzić obiekt, do którego odwołuje się zmienna lokalna po zakończeniu tej zmiennej. W językach C# i Visual Basic można tworzyć identyfikatory obiektów dla określonych wystąpień typów referencyjnych i używać ich w okno wyrażeń kontrolnych i w warunkach punktu przerwania. Identyfikator obiektu jest generowany przez usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) i skojarzone z obiektem.  
  
> [!NOTE]
> Identyfikatory obiektów tworzą słabe odwołania i nie uniemożliwiają odzyskiwania obiektu. Są one prawidłowe tylko dla bieżącej sesji debugowania.  
  
 W poniższym kodzie jedna metoda tworzy `Person` zmienną używającą lokalnej, ale chcesz dowiedzieć się, jaka `Person` jest nazwa w innej metodzie:  
  
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
    List<Person> _people = new List<Person>();  
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
  
 Można dodać odwołanie do tego `Person` obiektu w oknie **czujki** w następujący sposób:  
  
1. Ustaw punkt przerwania w kodzie jakiś czas po utworzeniu obiektu.  
  
2. Rozpocznij debugowanie i po zatrzymaniu wykonywania w punkcie przerwania Znajdź zmienną w oknie **zmiennych lokalnych** , kliknij ją prawym przyciskiem myszy, a następnie wybierz pozycję **Utwórz identyfikator obiektu**.  
  
3. Powinna zostać wyświetlona **$** Plus cyfra w oknie **zmiennych lokalnych** . To jest identyfikator obiektu.  
  
4. Dodaj identyfikator obiektu do okno wyrażeń kontrolnych.  
  
5. Ustaw punkt przerwania, w którym chcesz obserwować zachowanie obiektu.  W powyższym kodzie, który byłby w `DoSomething()` metodzie.  
  
6. Kontynuuj debugowanie i gdy wykonywanie zatrzyma się w tej `DoSomething()` metodzie, okno **czujki** wyświetla `Person` obiekt.  
  
> [!NOTE]
> Jeśli chcesz zobaczyć właściwości obiektu, takie jak `Person.Name` w powyższym przykładzie, należy włączyć ocenę właściwości.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Używanie rejestrów w okno wyrażeń kontrolnych (tylko C++)  
 Jeśli debugujesz kod natywny, możesz dodać nazwy rejestrów oraz nazwy zmiennych przy użyciu **$\<register name>** lub **@\<register name>** .  Aby uzyskać więcej informacji, zobacz [pseudozmiennych pokazanych](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>DynamicView i okno wyrażeń kontrolnych  
 Niektóre języki skryptów (np. JavaScript lub Python) używają tekstu dynamicznego lub [kaczego](https://en.wikipedia.org/wiki/Duck_typing), a Języki .NET (w wersji 4,0 i nowszych) obsługują obiekty, które trudno obserwować przy użyciu normalnego okna debugowania, ponieważ mogą one mieć właściwości i metody środowiska uruchomieniowego, których nie można wyświetlić.  
  
 Gdy okno wyrażeń kontrolnych wyświetla lub obiekt utworzony na podstawie typu, który implementuje <xref:System.Dynamic.IDynamicMetaObjectProvider> , debuger dodaje specjalny **dynamiczny węzeł widoku**  do wyświetlania **automatycznie** . Ten węzeł pokazuje dynamiczne elementy członkowskie obiektu dynamicznego, ale nie zezwala na edytowanie wartości elementów członkowskich.  
  
 Jeśli klikniesz prawym przyciskiem myszy dowolny element podrzędny **widoku dynamicznego** i wybierzesz polecenie **Dodaj czujki**, debuger wstawi nową zmienną czujki, która rzutuje obiekt na obiekt dynamiczny. Innymi słowy, **Nazwa obiektu** zmieni się (**obiekt dynamiczny). Nazwa**.  
  
 Ocenianie elementów członkowskich **widoku dynamicznego** może mieć skutki uboczne. Aby uzyskać wyjaśnienie skutków ubocznych, zobacz [efekty uboczne i wyrażenia](#bkmk_sideEffects). W języku C# debuger nie oblicza automatycznie wartości pokazywanych w **widoku dynamicznym** po przekroczeniu nowego wiersza kodu. W przypadku Visual Basic wyrażenia dodawane przez **Widok dynamiczny** są odświeżane automatycznie.  
  
 Aby uzyskać instrukcje dotyczące odświeżania wartości widoku dynamicznego, zobacz [odświeżanie wartości kontrolki, które są nieaktualne](#bkmk_refreshWatch).  
  
 Jeśli chcesz wyświetlić tylko **Widok dynamiczny** dla obiektu, możesz użyć specyfikatora formatu **dynamicznego** :  
  
- C#: **ObjectName, dynamiczny**  
  
- Visual Basic:: **$Dynamic, ObjectName**  
  
  **Widok dynamiczny** rozszerza również środowisko debugowania dla obiektów com. Gdy debuger napotka obiekt COM opakowany w **System. __ComObject**, dodaje **dynamiczny węzeł widoku** dla obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Okna debugera](../debugger/debugger-windows.md)
