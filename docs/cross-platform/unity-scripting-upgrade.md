---
title: Używanie platformy .NET 4.x w aparacie Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 5fb521ff1769f1d742dc1ce67080e98aecb417ad
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75944234"
---
# <a name="using-net-4x-in-unity"></a>Używanie platformy .NET 4.x w aparacie Unity

C# i .NET, technologie leżące u podstaw skryptów Unity, nadal otrzymywać aktualizacje, ponieważ firma Microsoft pierwotnie wydała je w 2002 roku. Ale deweloperzy Unity może nie być świadomi stały strumień nowych funkcji dodanych do języka C# i .NET Framework. To dlatego, że przed Unity 2017.1, Unity używa środowiska uruchomieniowego skryptów równoważne .NET 3.5, brakujące lata aktualizacji.

Wraz z wydaniem Unity 2017.1 unity wprowadził eksperymentalną wersję swojego środowiska uruchomieniowego skryptów uaktualnioną do wersji zgodnej z .NET 4.6, C# 6. W Unity 2018.1 równoważne środowisko uruchomieniowe .NET 4.x nie jest już uważane za eksperymentalne, podczas gdy starsze środowisko uruchomieniowe równoważne .NET 3.5 jest teraz uważane za starszą wersję. Wraz z wydaniem Unity 2018.3 Unity przewiduje, że uaktualniony środowisko uruchomieniowe skryptów stanie się domyślnym wyborem i zaktualizować go jeszcze dalej do języka C# 7. Aby uzyskać więcej informacji i najnowsze aktualizacje na temat tego planu, przeczytaj [blogu](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) Unity lub odwiedź ich [Experimental Scripting Previews forum](https://forum.unity.com/forums/experimental-scripting-previews.107/). W międzyczasie zapoznaj się z poniższymi sekcjami, aby dowiedzieć się więcej o nowych funkcjach dostępnych teraz w czasie wykonywania skryptów .NET 4.x.

## <a name="prerequisites"></a>Wymagania wstępne

* [Unity 2017.1 lub nowszy](https://unity3d.com/) (2018.2 zalecane)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Włączanie środowiska uruchomieniowego skryptów .NET 4.x w ucho.

Aby włączyć środowisko uruchomieniowe skryptów .NET 4.x, należy wykonać następujące kroki:

1. Otwórz ustawienia playersettings w Inspektorze jedności, wybierając **pozycję Edytuj > ustawienia projektu > player**.

1. W nagłówku **Konfiguracja** kliknij pozycję **rozwijaną Wersja środowiska wykonawczego skryptów** i wybierz pozycję **.NET 4.x Equivalent**. Zostanie wyświetlony monit o ponowne uruchomienie unity.

![Wybierz odpowiednik .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Wybór między profilami .NET 4.x i .NET Standard 2.0

Po przełączeniu się do środowiska uruchomieniowego skryptów równoważnych .NET 4.x można określić **poziom zgodności interfejsu API** za pomocą menu rozwijanego w menu PlayerSettings **(Edytuj > ustawienia projektu > Player**). Dostępne są dwie opcje:

* **.NET Standard 2.0**. Ten profil jest zgodny z [profilem .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) opublikowanym przez fundację .NET Foundation. Unity zaleca .NET Standard 2.0 dla nowych projektów. Jest mniejszy niż .NET 4.x, co jest korzystne dla platform o ograniczonym rozmiarze. Ponadto Unity zobowiązała się do wspierania tego profilu na wszystkich platformach, które obsługuje Unity.

* **.NET 4.x**. Ten profil zapewnia dostęp do najnowszego interfejsu API platformy .NET 4. Zawiera cały kod dostępny w bibliotekach klas .NET Framework i obsługuje również profile .NET Standard 2.0. Użyj profilu .NET 4.x, jeśli projekt wymaga części interfejsu API nieuwzględnianej w profilu .NET Standard 2.0. Jednak niektóre części tego interfejsu API mogą nie być obsługiwane na wszystkich platformach Unity.

Możesz przeczytać więcej o tych opcjach w [blogu](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Dodawanie odwołań do zestawu podczas korzystania z poziomu zgodności interfejsu API .NET 4.x

W przypadku korzystania z ustawienia .NET Standard 2.0 w liście rozwijanej **Poziom zgodności interfejsu API** wszystkie zestawy w profilu interfejsu API są przywoływanye i użyteczne. Jednak podczas korzystania z większego profilu .NET 4.x, niektóre zestawy, które unity jest dostarczany z nie są domyślnie odwoływane. Aby użyć tych interfejsów API, należy ręcznie dodać odwołanie do złożenia. Można wyświetlić zestawy Unity statków z w **Katalogu MonoBleedingEdge/lib/mono** instalacji edytora Unity:

![Katalog MonoBleedingEdge](media/vstu_monobleedingedge.png)

Na przykład, jeśli używasz profilu .NET 4.x `HttpClient`i chcesz użyć , należy dodać odwołanie do zestawu dla pliku System.Net.Http.dll. Bez niego kompilator będzie narzekać, że brakuje odwołania do zestawu:

![brak odwołania do złożenia](media/vstu_missing-reference.png)

Visual Studio regeneruje pliki csproj i .sln dla projektów Unity za każdym razem, gdy są one otwierane. W rezultacie nie można dodać odwołania do zestawu bezpośrednio w programie Visual Studio, ponieważ zostaną one utracone po ponownym otwarciu projektu. Zamiast tego należy użyć specjalnego pliku tekstowego o nazwie **mcs.rsp:**

1. Utwórz nowy plik tekstowy o nazwie **mcs.rsp** w katalogu **zasobów** głównych projektu Unity.

1. W pierwszym wierszu w pustym `-r:System.Net.Http.dll` pliku tekstowym wprowadź: a następnie zapisz plik. "System.Net.Http.dll" można zastąpić dowolnym dołączonym zestawem, którego może brakować odwołania.

1. Uruchom ponownie edytor Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Korzystanie ze zgodności z programem .NET

Oprócz nowych funkcji składni i języka języka C#środowisko wykonywania skryptów .NET 4.x daje użytkownikom unity dostęp do ogromnej biblioteki pakietów platformy .NET, które są niezgodne ze starszym czasem wykonywania skryptów platformy .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Dodawanie pakietów z NuGet do projektu Unity

[NuGet](https://www.nuget.org/) jest menedżerem pakietów dla platformy .NET. NuGet jest zintegrowany z programem Visual Studio. Jednak projekty Unity wymagają specjalnego procesu, aby dodać pakiety NuGet. Dzieje się tak, ponieważ po otwarciu projektu w unity, jego pliki projektu Visual Studio są generowane ponownie, cofanie niezbędne konfiguracje. Aby dodać pakiet z NuGet do projektu Unity wykonaj następujące czynności:

1. Przeglądaj nuget, aby znaleźć zgodny pakiet, który chcesz dodać (.NET Standard 2.0 lub .NET 4.x). W tym przykładzie zostanie zademonstrowane dodawanie [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), popularny pakiet do pracy z JSON, do projektu .NET Standard 2.0.

1. Kliknij przycisk **Pobierz:**

    ![przycisk pobierz](media/vstu_nuget-download.png)

1. Znajdź pobrany plik i zmień rozszerzenie z **.nupkg** na **.zip**.

1. W pliku zip przejdź do katalogu **lib/netstandard2.0** i skopiuj plik **Newtonsoft.Json.dll.**

1. W głównym folderze **Zasoby projektu** Unity utwórz nowy folder o nazwie **Wtyczki**. Wtyczki to specjalna nazwa folderu w Unity. Zobacz [dokumentację Unity,](https://docs.unity3d.com/Manual/Plugins.html) aby uzyskać więcej informacji.

1. Wklej plik **Newtonsoft.Json.dll** do katalogu **wtyczek** projektu Unity.

1. Utwórz plik o nazwie **link.xml** w katalogu **Zasoby** projektu Unity i dodaj następujący kod XML.  Zapewni to, że proces usuwania kodu bajtowego Unity nie usunie niezbędnych danych podczas eksportowania do platformy IL2CPP.  Ten krok jest specyficzny dla tej biblioteki, ale mogą wystąpić problemy z innymi bibliotekami, które używają odbicia w podobny sposób.  Aby uzyskać więcej informacji, zobacz [dokumenty Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) na ten temat.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Mając wszystko na swoim miejscu, możesz teraz korzystać z pakietu Json.NET.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Jest to prosty przykład przy użyciu biblioteki, która nie ma zależności. Gdy pakiety NuGet opierają się na innych pakietach NuGet, należy ręcznie pobrać te zależności i dodać je do projektu w taki sam sposób.

## <a name="new-syntax-and-language-features"></a>Nowe funkcje składni i języka

Za pomocą zaktualizowanego środowiska wykonawczego skryptów daje deweloperom Unity dostęp do języka C# 6 i wiele nowych funkcji języka i składni.

### <a name="auto-property-initializers"></a>Inicjatory właściwości automatycznych

W czasie wykonywania skryptów .NET 3.5 unity's, składnia właściwości automatycznych ułatwia szybkie definiowanie niezainicjowanych właściwości, ale inicjowanie musi nastąpić w innym miejscu w skrypcie. Teraz w czasie wykonywania .NET 4.x możliwe jest zainicjowanie właściwości automatycznych w tym samym wierszu:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolacja ciągów

W starszym czasie wykonywania .NET 3.5 łączenie ciągów wymagało niezręcznej składni. Teraz w czasie wykonywania .NET 4.x funkcja [ `$` interpolacji ciągów](/dotnet/csharp/language-reference/tokens/interpolated) umożliwia wstawianie wyrażeń do ciągów w bardziej bezpośredniej i czytelnej składni:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Składowe z wyrażeniem w treści

Dzięki nowszej składni języka C# dostępnej w czasie wykonywania .NET 4.x [wyrażenia lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) mogą zastąpić treść funkcji, aby uczynić je bardziej zwięzłymi:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Można również użyć elementów członkowskich zabudowanych wyrażeniami we właściwościach tylko do odczytu:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Wzorzec asynchroniczny oparty na zadaniach (TAP)

[Programowanie asynchroniczne](/dotnet/csharp/async) umożliwia czasochłonne operacje odbywać się bez powodowania aplikacji przestać odpowiadać. Ta funkcja umożliwia również kod czekać na czasochłonne operacje, aby zakończyć przed kontynuowaniem kodu, który zależy od wyników tych operacji. Na przykład można poczekać na załadowanie pliku lub zakończenie operacji sieciowej.

W Unity programowanie asynchroniczne jest zazwyczaj realizowane za pomocą [coroutines](https://docs.unity3d.com/Manual/Coroutines.html). Jednak od C# 5 preferowaną metodą programowania asynchronicznego w programie .NET jest [wzorzec asynchroniczne oparte na zadaniach (TAP)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) przy użyciu `async` słów kluczowych i `await` słów kluczowych z [System.Threading.Task](/dotnet/api/system.threading.tasks.task). Podsumowując, w `async` funkcji można `await` zakończyć zadanie bez blokowania pozostałych aplikacji z aktualizacji:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP jest złożonym tematem, z niuansami specyficznymi dla Unity, które deweloperzy powinni wziąć pod uwagę. W rezultacie TAP nie jest uniwersalnym zamiennikiem coroutines w Unity; jest to jednak kolejne narzędzie do wykorzystania. Zakres tej funkcji wykracza poza ten artykuł, ale poniżej przedstawiono kilka ogólnych najlepszych rozwiązań i wskazówek.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Wprowadzenie do informacji o tap with Unity

Te wskazówki mogą pomóc ci rozpocząć pracę z TAP w unity:

* Funkcje asynchroniczne przeznaczone do oczekiwania powinny [`Task`](/dotnet/api/system.threading.tasks.task) [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1)mieć typ zwracany lub .
* Funkcje asynchroniczne zwracające zadanie powinny mieć sufiks **"Async"** do ich nazw. Sufiks "Async" pomaga wskazać, że funkcja powinna być zawsze oczekiwana.
* Użyj zwracanego `async void` typu tylko dla funkcji, które odpalają funkcje asynchroniczne z tradycyjnego kodu synchroniczowego. Takie funkcje nie mogą być oczekiwane i nie powinny mieć sufiks "Async" w ich nazwach.
* Unity używa UnitySynchronizationContext, aby zapewnić, że funkcje asynchronowe są domyślnie uruchamiane w wątku głównym. Interfejs API unity nie jest dostępny poza wątkiem głównym.
* Możliwe jest uruchamianie zadań w wątkach [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) w [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx)tle za pomocą metod takich jak i . Ta technika jest przydatna do odciążania kosztownych operacji z wątku głównego w celu zwiększenia wydajności. Jednak za pomocą wątków w tle może prowadzić do problemów, które są trudne do debugowania, takich jak [warunki wyścigu.](https://wikipedia.org/wiki/Race_condition)
* Interfejs API unity nie jest dostępny poza wątkiem głównym.
* Zadania, które używają wątków nie są obsługiwane w kompilacjach Unity WebGL.

#### <a name="differences-between-coroutines-and-tap"></a>Różnice między coroutines i TAP

Istnieją pewne ważne różnice między coroutines i TAP / asynchronii await:

* Coroutines nie może `Task<TResult>` zwracać wartości, ale może.
* Nie można `yield` umieścić w try-catch instrukcji, co utrudnia obsługę błędów z coroutines. Jednak try-catch działa z TAP.
* Funkcja coroutine unity nie jest dostępna w klasach, które nie pochodzą z MonoBehaviour. TAP doskonale nadaje się do programowania asynchroniiowego w takich klasach.
* W tym momencie Unity nie sugeruje TAP jako hurtowego zamiennika coroutines. Profilowanie to jedyny sposób na poznanie konkretnych wyników jednego podejścia względem innych dla danego projektu.

> [!NOTE]
> Od stanu Unity 2018.2 debugowanie metod asynchronii z break pointami nie jest w pełni obsługiwane; jednak [ta funkcjonalność jest oczekiwana w Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof, operator

Operator `nameof` pobiera nazwę ciągu zmiennej, typu lub elementu członkowskiego. W niektórych przypadkach, gdy `nameof` się przydaje, są błędy rejestrowania i uzyskiwanie nazwy ciągu wyliczenia:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Atrybuty informacji o dzwoniącym

[Atrybuty informacji o wywołującym](/dotnet/csharp/programming-guide/concepts/caller-information) zawierają informacje o wywołującym metodę. Dla każdego parametru, którego chcesz używać, należy podać wartość domyślną dla każdego parametru, którego chcesz użyć z atrybutem Informacje o dzwoniącym:

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Korzystanie ze statycznych

[Za pomocą statyczne](/dotnet/csharp/language-reference/keywords/using-static) umożliwia korzystanie z funkcji statycznych bez wpisywania jego nazwę klasy. Za pomocą statyczne, można zaoszczędzić miejsce i czas, jeśli trzeba użyć kilku funkcji statycznych z tej samej klasy:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Uwagi dotyczące IL2CPP

Podczas eksportowania gry do platform, takich jak iOS, Unity użyje swojego aparatu IL2CPP do "transpile" IL do kodu C++, który jest następnie kompilowany przy użyciu natywnego kompilatora platformy docelowej. W tym scenariuszu istnieje kilka funkcji platformy .NET, które nie są obsługiwane, takich jak części odbicia i użycie `dynamic` słowa kluczowego. Chociaż można kontrolować za pomocą tych funkcji w kodzie własnym, może wystąpić problemy przy użyciu bibliotek DLL innych firm i SDK, które nie zostały napisane z Unity i IL2CPP na uwadze. Aby uzyskać więcej informacji na ten temat, zobacz dokumenty [ograniczenia skryptów](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) w witrynie Unity.

Ponadto, jak wspomniano w Json.NET przykładzie powyżej, Unity podejmie próbę usunięcie nieużytego kodu podczas procesu eksportowania IL2CPP.  Chociaż zazwyczaj nie jest to problem, z bibliotek, które używają odbicia, może przypadkowo usunąć właściwości lub metody, które będą wywoływane w czasie wykonywania, które nie mogą być określone w czasie eksportu.  Aby rozwiązać te problemy, dodaj plik **link.xml** do projektu, który zawiera listę zestawów i obszarów nazw, aby nie uruchamiać procesu usuwania.  Aby uzyskać szczegółowe informacje, zobacz [dokumenty Unity dotyczące usuwania kodu bajtowego](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Przykładowy projekt Unity .NET 4.x

Przykład zawiera przykłady kilku funkcji .NET 4.x. Możesz pobrać projekt lub wyświetlić kod źródłowy na [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Zasoby dodatkowe

* [Unity Blog — ulepszenia środowiska uruchomieniowego skryptów w unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Historia C #](/dotnet/csharp/whats-new/csharp-version-history)
* [Co nowego w języku C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Programowanie asynchroniczne w Unity, Korzystanie Coroutine i TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Async-Await zamiast Coroutines w Jedności 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Unity Forum - Eksperymentalne podglądy skryptów](https://forum.unity.com/forums/experimental-scripting-previews.107/)
