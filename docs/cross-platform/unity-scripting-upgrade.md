---
title: Przy użyciu platformy .NET 4.x na platformie Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: conceptual
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 0fb4560a196404687c60ce67f39b9c0754a24769
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253142"
---
# <a name="using-net-4x-in-unity"></a>Przy użyciu platformy .NET 4.x na platformie Unity

C# i .NET, technologii podstawowych skryptów Unity, nadal otrzymywać aktualizacje, ponieważ program Microsoft pierwotnie udostępnionego im w 2002 roku. Ale deweloperów Unity mogą nie być świadomy nieprzerwany strumień nowych funkcji dodanych do języka C# i .NET Framework. Wynika to z przed środowisku Unity 2017.1 Unity używał .NET 3.5 równoważne skryptów środowiska uruchomieniowego, brak lat aktualizacji.

Wydanej w środowisku Unity 2017.1 Unity wprowadzona wersja eksperymentalna jego skryptów środowiska uruchomieniowego, uaktualnienie do platformy .NET 4.6, C# 6 zgodnej wersji. W Unity 2018.1 4.x równoważne środowiska uruchomieniowego .NET przestaje być uważany za eksperymentalnych, podczas starsze równoważne środowiska uruchomieniowego jest teraz uważany za starszą wersją .NET 3.5. A wraz z wydaniem Unity 2018.3 Unity jest projekcji się uaktualniony skryptów środowiska uruchomieniowego wybór domyślny i zaktualizować nawet w przypadku języka C# 7. Więcej informacji oraz najświeższe informacje na ten harmonogram działania dla odczytu mechanizmu Unity [wpis w blogu](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) lub odwiedź ich [forum eksperymentalne podglądy skryptów](https://forum.unity.com/forums/experimental-scripting-previews.107/). W międzyczasie zapoznaj się z sekcje poniżej, aby dowiedzieć się więcej o nowych funkcjach, teraz dostępna do platformy .NET 4.x skryptów aparatu plików wykonywalnych.

## <a name="prerequisites"></a>Wymagania wstępne

* [Środowisku Unity 2017.1 lub nowszej](https://unity3d.com/) (2018.2 zalecane)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Włączanie 4.x skryptów środowiska uruchomieniowego .NET na platformie Unity

Aby włączyć 4.x skryptów środowiska uruchomieniowego .NET, wykonaj następujące czynności:

1. Otwórz PlayerSettings w Inspektorze Unity, wybierając **Edytuj > Ustawienia projektu > Player**.

1. W obszarze **konfiguracji** nagłówek, kliknij przycisk **skryptów wersji środowiska uruchomieniowego** listy rozwijanej i wybierz **.NET 4.x odpowiednik**. Zostanie wyświetlony monit ponownego uruchomienia aparatu Unity.

![Wybierz pozycję .NET 4.x równoważne](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Wybieranie między .NET 4.x i profilów platformy .NET Standard 2.0

Po przełączeniu się do platformy .NET 4.x równoważne skryptów środowiska uruchomieniowego, można określić **poziom zgodności Api** przy użyciu menu rozwijane w PlayerSettings (**Edytuj > Ustawienia projektu > Player**). Dostępne są dwie opcje:

* **.NET standard 2.0**. Ten profil jest zgodny z [profilu .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) opublikowanych przez .NET Foundation. Unity zaleca .NET Standard 2.0 dla nowych projektów. Jest mniejsze niż .NET 4.x, co jest korzystna dla platform ograniczony rozmiar. Ponadto Unity została zatwierdzona do obsługi tego profilu na wszystkich platformach, które obsługuje platformy Unity.

* **.NET 4.x**. Ten profil umożliwia dostęp do najnowszych 4 interfejsu API programu .NET. Ona obejmuje wszystkie dostępne kod w bibliotekach klas .NET Framework i obsługuje także profile .NET Standard 2.0. Jeśli Twój projekt wymaga częścią interfejsu API, które nie są uwzględnione w profilu .NET Standard 2.0, należy użyć profilu platformy .NET 4.x. Jednak niektóre elementy tego interfejsu API nie może być obsługiwane na wszystkich platformach firmy Unity.

Możesz przeczytać więcej na temat tych opcji na liście mechanizmu Unity [wpis w blogu](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/).

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Dodawanie odwołania do zestawów, korzystając z programu .NET 4.x poziom zgodności interfejsu Api

Korzystając z ustawienia .NET Standard 2.0 w **poziom zgodności interfejsu Api** listy rozwijanej, wszystkie zestawy w profilu interfejsu API są odwołania i użyteczne. Jednak podczas korzystania z większych profilu platformy .NET w 4.x, niektóre zestawy, które Unity jest dostarczany z nie są określone przez domyślny. Aby korzystać z tych interfejsów API, należy ręcznie dodać odwołania do zestawu. Możesz wyświetlić zestawy Unity jest dostarczany z programem w **MonoBleedingEdge/lib/mono** katalogu instalacji programu Unity editor:

![Katalog MonoBleedingEdge](media/vstu_monobleedingedge.png)

Na przykład, jeśli używasz profilu platformy .NET 4.x i chcesz używać `HttpClient`, należy dodać odwołanie do zestawu System.Net.Http.dll. Bez tego kompilator będzie reklamację, że masz brakuje odwołania do zestawu:

![Brak odwołania do zestawu](media/vstu_missing-reference.png)

Program Visual Studio generuje pliki .csproj i .sln dla projektów aparatu Unity, każdym razem, gdy są one otwarte. W rezultacie nie można dodać odwołania do zestawu bezpośrednio w programie Visual Studio, ponieważ były one utracone po ponownym otwarciu projektu. Zamiast tego, o nazwie pliku tekstowego specjalne **mcs.rsp** należy użyć:

1. Utwórz nowy plik tekstowy o nazwie **mcs.rsp** w swoim projekcie aparatu Unity w katalogu głównym **zasoby** katalogu.

1. W pierwszym wierszu w pliku tekstowym pusty, wprowadź: `-r:System.Net.Http.dll` , a następnie zapisz plik. Możesz zastąpić "System.Net.Http.dll" dołączony zestawów, które być może brakuje odwołania.

1. Ponowne uruchomienie programu Unity editor.

## <a name="taking-advantage-of-net-compatibility"></a>Korzystając z zalet zgodność z platformą .NET

Oprócz nowych funkcji C# składni i język 4.x skryptów środowiska uruchomieniowego .NET umożliwia Unity użytkownikom dostęp do ogromnej biblioteki .NET pakietów, które nie są zgodne ze środowiskiem uruchomieniowym starszej wersji skryptu .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Dodaj pakiety z pakietów NuGet do projektu środowiska Unity

[NuGet](https://www.nuget.org/) to Menedżer pakietów dla platformy .NET. NuGet jest zintegrowana w programie Visual Studio. Jednak projekty Unity wymagają specjalnej procedury do dodawania pakietów NuGet. Jest to spowodowane po otwarciu projektu na platformie Unity jego pliki projektu programu Visual Studio są generowane, cofnięcie wymagane opcje. Aby dodać pakiet z pakietów NuGet do Twojego projektu środowiska Unity wykonaj następujące czynności:

1. Przeglądaj pakietu NuGet, aby zlokalizować pakiet zgodne, czy chcesz dodać (.NET Standard 2.0 i .NET 4.x). W tym przykładzie przedstawiono dodawanie [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), popularnego pakietu do pracy z formatu JSON, do projektu .NET Standard 2.0.

1. Kliknij przycisk **Pobierz** przycisku:

    ![przycisk Pobierz](media/vstu_nuget-download.png)

1. Znajdź pobrany plik i zmień rozszerzenie z **.nupkg** do **zip**.

1. W pliku zip, przejdź do **lib/netstandard2.0** katalogu i skopiuj **pliku Newtonsoft.Json.dll** pliku.

1. W swoim projekcie aparatu Unity w katalogu głównym **zasoby** folderu, Utwórz nowy folder o nazwie **wtyczek**. Wtyczki to nazwa folderu specjalnego na platformie Unity. Zobacz [dokumentacja aparatu Unity](https://docs.unity3d.com/Manual/Plugins.html) Aby uzyskać więcej informacji.

1. Wklej **pliku Newtonsoft.Json.dll** plik do projektu środowiska Unity **wtyczek** katalogu.

1. Utwórz plik o nazwie **link.xml** w swoim projekcie aparatu Unity **zasoby** katalogu i Dodaj następujący kod XML.  Pozwoli to zagwarantować, że proces oddzielającego kodu bajtowego mechanizmu Unity nie powoduje usunięcia niezbędnych danych, podczas eksportowania platformę IL2CPP.  Ten krok jest specyficzne dla tej biblioteki, mogą występować problemy z innych bibliotek, które używają odbicia w podobny sposób.  Aby uzyskać więcej informacji, zobacz [docs mechanizmu Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) na ten temat.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

Wszystko w miejscu można teraz użyć pakietu struktury Json.NET.

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

Jest to prosty przykład za pomocą biblioteki, która nie ma zależności. Gdy pakiety NuGet zależą inne pakiety NuGet, należy ręcznie pobrać te zależności, i dodaj je do projektu w taki sam sposób.

## <a name="new-syntax-and-language-features"></a>Nowe funkcje składni i języka

Przy użyciu zaktualizowanych skryptów środowiska uruchomieniowego udostępnia Unity deweloperów C# 6 i hostem nowe funkcje języka i składni.

### <a name="auto-property-initializers"></a>Inicjatory właściwości automatycznej

Firmy Unity .NET 3.5 skryptów środowiska wykonawczego składni właściwości automatycznej można łatwo szybko zdefiniować niezainicjowanych właściwości, ale inicjowania ma mieć miejsce w innych miejscach w skrypcie. Teraz ze środowiskiem uruchomieniowym .NET 4.x, możliwe jest do zainicjowania właściwości auto w tym samym wierszu:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolacja ciągów

Za pomocą starsze środowisko uruchomieniowe .NET 3.5 ciągów wymagane składni niewygodna. Teraz za pomocą środowiska uruchomieniowego .NET 4.x [ `$` Interpolacja ciągów](https://docs.microsoft.com/dotnet/csharp/language-reference/tokens/interpolated) funkcja umożliwia wyrażeń, które ma zostać wstawiony do ciągów, w składni bardziej bezpośrednie i możliwych do odczytu:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Elementy członkowskie z wyrażeniem

Przy użyciu nowszej C# składni dostępnych w środowisku uruchomieniowym .NET 4.x [wyrażeń lambda](https://docs.microsoft.com/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) można zastąpić treści funkcji, aby były one bardziej zwięzłą:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

Elementy członkowskie z wyrażeniem można również użyć właściwości tylko do odczytu:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Wzorzec asynchroniczny oparty na zadaniach (TAP)

[Programowanie asynchroniczne](https://docs.microsoft.com/dotnet/csharp/async) umożliwia wykonywanie operacji czasochłonne została wykonana bez powodowania aplikacja przestanie odpowiadać. Ta funkcja umożliwia także swój kod, aby czekać na operacje dużo czasu na zakończenie przed kontynuowaniem kod, który jest zależny od wyniki tych operacji. Można na przykład trzeba odczekać pliku do obciążenia lub na zakończenie operacji sieciowych.

Na platformie Unity, programowanie asynchroniczne zwykle odbywa się za pomocą [koprocedury](https://docs.unity3d.com/Manual/Coroutines.html). Jednak od C# 5, preferowaną metodą programowania asynchronicznego w .NET development został [opartego na zadaniach asynchronicznej wzorca (TAP)](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) przy użyciu `async` i `await` słowa kluczowe w [ System.Threading.Task](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task). Podsumowując w `async` funkcji możesz `await` ukończenia zadań bez blokowania pozostałych aplikacji z aktualizacji:

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

Wzorzec TAP jest złożonym zagadnieniem, za pomocą niuanse specyficzne dla aparatu Unity, które należy wziąć pod uwagę deweloperów. W wyniku wzorca TAP nie jest uniwersalny zastępuje koprocedury na platformie Unity; jest jednak inne narzędzie, aby wykorzystać. Zakres tej funkcji jest wyższy niż w tym artykule, ale niektóre najważniejsze wskazówki i porady, które są przedstawione poniżej.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Pobieranie odwołania wprowadzenie wzorca TAP przy użyciu aparatu Unity

Poniższe wskazówki mogą pomóc Ci rozpocząć pracę z wzorca TAP na platformie Unity:

* Funkcje asynchroniczne, które mają być oczekiwana powinien mieć typ zwracany [ `Task` ](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task) lub [ `Task<TResult>` ](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task-1).
* Funkcje asynchroniczne, które zwracają zadania powinny mieć sufiks **"Async"** dołączany do ich nazw. Przyrostku "Async" pomaga wskazać funkcji zawsze należy oczekiwane.
* Używaj tylko `async void` zwracany typ dla funkcji, które szybko włączyć funkcje asynchroniczne z tradycyjnego kodu synchronicznego. Takie funkcje, nie może się być oczekiwana i nie powinny mieć przyrostku "Async" w nazwach.
* Unity używa UnitySynchronizationContext, aby upewnić się, że funkcje asynchroniczne domyślnie uruchamiane w wątku głównym. Interfejs API aparatu Unity nie jest niedostępny poza wątku głównego.
* Umożliwia uruchamianie zadań na wątkach w tle za pomocą metod, takich jak [ `Task.Run` ](https://msdn.microsoft.com/library/hh195051.aspx) i [ `Task.ConfigureAwait(false)` ](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Ta technika jest przydatny przy przekazywaniu kosztownych operacji z wątku głównego w celu zwiększenia wydajności. Jednak za pomocą wątków w tle może prowadzić do problemów, które są trudne do debugowania, takie jak [wyścigu](https://wikipedia.org/wiki/Race_condition).
* Interfejs API aparatu Unity nie jest dostępny na zewnątrz głównego wątku.
* Tworzy zadania, użyj wątki nie są obsługiwane w WebGL aparatu Unity.

#### <a name="differences-between-coroutines-and-tap"></a>Różnice w koprocedury i naciśnij pozycję

Istnieją pewne ważne różnice między w koprocedury i naciśnij pozycję / async-await:

* Koprocedury nie może zwracać wartości, ale `Task<TResult>` może.
* Nie można umieścić `yield` w instrukcji try-catch, utrudniając koprocedur obsługi błędów. Try-catch — działa jednak naciśnięciem.
* Unity w koprocedury funkcja jest niedostępna w klasach, które nie pochodzą z obiekt MonoBehaviour. NACIŚNIJ to idealne narzędzie do programowania asynchronicznego w tych grupach.
* W tym momencie Unity nie sugerują wzorca TAP jako całościowego zastąpienia procedur wspólnych. Profilowanie jest jedynym sposobem ustalenia określone wyniki z jednej metody, a drugi dla każdego projektu w serwisie.

> [!NOTE]
> Począwszy od Unity 2018.2 debugowanie metod asynchronicznych za pomocą punktów przerwania w pełni nie jest obsługiwane; jednak [ta funkcja jest oczekiwany w Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof operator

`nameof` Operator pobiera nazwę ciągu zmiennej, typu lub składowej. Niektórych przypadków, gdy `nameof` przydatność rejestrowanie błędów i uzyskiwania informacji o nazwę ciągu elementu wyliczenia:

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

### <a name="caller-info-attributes"></a>Caller — atrybuty informacji

[Caller — atrybuty informacji](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/caller-information) zawierają informacje o obiekcie wywołującym metodę. Należy podać wartość domyślną dla każdego parametru, który chcesz korzystać z atrybutem informacji o obiekcie wywołującym:

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

### <a name="using-static"></a>Przy użyciu statycznej

[Przy użyciu statycznej](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/using-static) pozwala na używanie statycznych funkcji bez wpisywania nazwy klasy. Przy użyciu statycznych, można zapisać czas i miejsce, jeśli musisz użyć kilku statyczne funkcje z tej samej klasy:

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

## <a name="il2cpp-considerations"></a>Zagadnienia dotyczące IL2CPP

Podczas eksportowania swoją grę do platform, takich jak iOS, Unity użyje jej aparat IL2CPP "transpiluj" IL dla kodu C++, który następnie jest kompilowany przy użyciu natywnego kompilatora platformę docelową. W tym scenariuszu istnieje kilka funkcji .NET, które nie są obsługiwane, takich jak części odbicia i użycie `dynamic` — słowo kluczowe. Podczas korzystania z tych funkcji we własnym kodzie można kontrolować, mogą występować problemy z używaniem 3rd dll innych firm i zestawy SDK, które nie zostały zapisane za pomocą aparatu Unity i IL2CPP na uwadze. Aby uzyskać więcej informacji na ten temat, zobacz [skryptów ograniczenia](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) dokumentacja w witrynie firmy Unity.

Ponadto jak wspomniano w powyższym przykładzie na składnik Json.NET, Unity będzie podejmować próby odłączenia nieużywany kod w procesie IL2CPP eksportu.  Chociaż zwykle nie jest to problem, z bibliotekami, które używają odbicia, może przypadkowo oddzielić właściwości lub metody, które będą wywoływane w czasie wykonywania, których nie można określić w czasie eksportowania.  Aby rozwiązać te problemy, należy dodać **link.xml** plik do projektu, który zawiera listę zestawy i przestrzenie nazw, aby nie uruchamiać oddzielającego procesu przed.  Aby uzyskać szczegółowe informacje, zobacz [dokumentów firmy Unity w obcięcie kodu bajtowego](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Programu .NET 4.x przykładowego projektu aparatu Unity

Przykład zawiera przykłady niektórych funkcji programu .NET 4.x. Można pobrać projektu lub wyświetlić kod źródłowy na [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Blog platformy Unity — skryptów środowiska uruchomieniowego poprawę 2018.2 aparatu Unity](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Historia języka C#](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-version-history)
* [Co nowego w języku C# 6](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-6)
* [Programowanie Unity i Koprocedury za pomocą wzorca TAP asynchroniczne](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Async-Await, zamiast w Koprocedury w 2017 aparatu Unity](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Forum aparatu Unity — eksperymentalne podglądy skryptów](https://forum.unity.com/forums/experimental-scripting-previews.107/)