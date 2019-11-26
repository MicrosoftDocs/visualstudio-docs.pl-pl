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
ms.openlocfilehash: 01363ab1588507f31dc74800c85b159039c9bab6
ms.sourcegitcommit: 9c7d8693108ecd2042a70c04cebe3c44af657baf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74239434"
---
# <a name="using-net-4x-in-unity"></a>Przy użyciu platformy .NET 4.x na platformie Unity

C# i .NET, technologii podstawowych skryptów Unity, nadal otrzymywać aktualizacje, ponieważ program Microsoft pierwotnie udostępnionego im w 2002 roku. Ale deweloperów Unity mogą nie być świadomy nieprzerwany strumień nowych funkcji dodanych do języka C# i .NET Framework. Wynika to z przed środowisku Unity 2017.1 Unity używał .NET 3.5 równoważne skryptów środowiska uruchomieniowego, brak lat aktualizacji.

Wydanej w środowisku Unity 2017.1 Unity wprowadzona wersja eksperymentalna jego skryptów środowiska uruchomieniowego, uaktualnienie do platformy .NET 4.6, C# 6 zgodnej wersji. W Unity 2018.1 4.x równoważne środowiska uruchomieniowego .NET przestaje być uważany za eksperymentalnych, podczas starsze równoważne środowiska uruchomieniowego jest teraz uważany za starszą wersją .NET 3.5. A wraz z wydaniem Unity 2018.3 Unity jest projekcji się uaktualniony skryptów środowiska uruchomieniowego wybór domyślny i zaktualizować nawet w przypadku języka C# 7. Aby uzyskać więcej informacji i najnowsze aktualizacje dotyczące tego przewodnika, Przeczytaj [wpis w blogu](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) aparatu Unity lub odwiedź [forum wglądu w skrypty eksperymentalne](https://forum.unity.com/forums/experimental-scripting-previews.107/). W międzyczasie zapoznaj się z sekcje poniżej, aby dowiedzieć się więcej o nowych funkcjach, teraz dostępna do platformy .NET 4.x skryptów aparatu plików wykonywalnych.

## <a name="prerequisites"></a>Wymagania wstępne

* [Unity 2017,1 lub nowszy](https://unity3d.com/) (zalecane jest 2018,2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Włączanie 4.x skryptów środowiska uruchomieniowego .NET na platformie Unity

Aby włączyć 4.x skryptów środowiska uruchomieniowego .NET, wykonaj następujące czynności:

1. Otwórz PlayerSettings w Inspektorze Unity, wybierając **edytuj > ustawienia projektu > Player**.

1. Pod nagłówkiem **Konfiguracja** kliknij listę rozwijaną **wersja środowiska uruchomieniowego tworzenia skryptów** i wybierz **odpowiedniki .NET 4. x**. Zostanie wyświetlony monit ponownego uruchomienia aparatu Unity.

![Wybierz pozycję .NET 4.x równoważne](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Wybieranie między .NET 4.x i profilów platformy .NET Standard 2.0

Po przełączeniu się do środowiska uruchomieniowego skryptów programu .NET 4. x można określić **poziom zgodności interfejsu API** za pomocą menu rozwijanego w PlayerSettings (**edytuj ustawienia projektu > > Player**). Dostępne są dwie opcje:

* **.NET Standard 2,0**. Ten profil jest zgodny z [profilem .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) opublikowanym przez platformę .NET Foundation. Unity zaleca .NET Standard 2.0 dla nowych projektów. Jest mniejsze niż .NET 4.x, co jest korzystna dla platform ograniczony rozmiar. Ponadto Unity została zatwierdzona do obsługi tego profilu na wszystkich platformach, które obsługuje platformy Unity.

* **.NET 4. x**. Ten profil umożliwia dostęp do najnowszych 4 interfejsu API programu .NET. Ona obejmuje wszystkie dostępne kod w bibliotekach klas .NET Framework i obsługuje także profile .NET Standard 2.0. Jeśli Twój projekt wymaga częścią interfejsu API, które nie są uwzględnione w profilu .NET Standard 2.0, należy użyć profilu platformy .NET 4.x. Jednak niektóre elementy tego interfejsu API nie może być obsługiwane na wszystkich platformach firmy Unity.

Więcej informacji na temat tych opcji można znaleźć w [wpisie w blogu](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)aparatu Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Dodawanie odwołania do zestawów, korzystając z programu .NET 4.x poziom zgodności interfejsu Api

W przypadku używania ustawienia .NET Standard 2,0 na liście rozwijanej **poziomu zgodności interfejsu API** wszystkie zestawy w profilu interfejsu API są przywoływane i mogą być używane. Jednak podczas korzystania z większych profilu platformy .NET w 4.x, niektóre zestawy, które Unity jest dostarczany z nie są określone przez domyślny. Aby korzystać z tych interfejsów API, należy ręcznie dodać odwołania do zestawu. Zestawy Unity można wyświetlić w katalogu **MonoBleedingEdge/lib/mono** instalacji edytora Unity:

![Katalog MonoBleedingEdge](media/vstu_monobleedingedge.png)

Na przykład, jeśli używasz profilu .NET 4. x i chcesz używać `HttpClient`, musisz dodać odwołanie do zestawu dla elementu System. NET. http. dll. Bez tego kompilator będzie reklamację, że masz brakuje odwołania do zestawu:

![Brak odwołania do zestawu](media/vstu_missing-reference.png)

Program Visual Studio generuje pliki .csproj i .sln dla projektów aparatu Unity, każdym razem, gdy są one otwarte. W rezultacie nie można dodać odwołania do zestawu bezpośrednio w programie Visual Studio, ponieważ były one utracone po ponownym otwarciu projektu. Zamiast tego należy użyć specjalnego pliku tekstowego o nazwie **MCS. rsp** :

1. Utwórz nowy plik tekstowy o nazwie **MCS. rsp** w katalogu głównych **zasobów** projektu środowiska Unity.

1. W pierwszym wierszu pustego pliku tekstowego wpisz: `-r:System.Net.Http.dll` a następnie Zapisz plik. Możesz zastąpić "System.Net.Http.dll" dołączony zestawów, które być może brakuje odwołania.

1. Ponowne uruchomienie programu Unity editor.

## <a name="taking-advantage-of-net-compatibility"></a>Korzystając z zalet zgodność z platformą .NET

Oprócz nowych funkcji C# składni i język 4.x skryptów środowiska uruchomieniowego .NET umożliwia Unity użytkownikom dostęp do ogromnej biblioteki .NET pakietów, które nie są zgodne ze środowiskiem uruchomieniowym starszej wersji skryptu .NET 3.5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Dodaj pakiety z pakietów NuGet do projektu środowiska Unity

Pakiet [NuGet](https://www.nuget.org/) jest menedżerem pakietów dla platformy .NET. NuGet jest zintegrowana w programie Visual Studio. Jednak projekty Unity wymagają specjalnej procedury do dodawania pakietów NuGet. Jest to spowodowane po otwarciu projektu na platformie Unity jego pliki projektu programu Visual Studio są generowane, cofnięcie wymagane opcje. Aby dodać pakiet z pakietów NuGet do Twojego projektu środowiska Unity wykonaj następujące czynności:

1. Przeglądaj pakietu NuGet, aby zlokalizować pakiet zgodne, czy chcesz dodać (.NET Standard 2.0 i .NET 4.x). W tym przykładzie przedstawiono dodawanie [JSON.NET](https://www.nuget.org/packages/Newtonsoft.Json/), popularnego pakietu do pracy z JSON, do projektu .NET Standard 2,0.

1. Kliknij przycisk **Pobierz** :

    ![przycisk Pobierz](media/vstu_nuget-download.png)

1. Znajdź pobrany plik i Zmień rozszerzenie z **. nupkg** na **. zip**.

1. W pliku zip przejdź do katalogu **lib/Standard 2.0** i skopiuj plik **Newtonsoft. JSON. dll** .

1. W folderze głównych **zasobów** projektu środowiska Unity Utwórz nowy folder o nazwie **wtyczki**. Wtyczki to nazwa folderu specjalnego na platformie Unity. Aby uzyskać więcej informacji, zobacz [dokumentację aparatu Unity](https://docs.unity3d.com/Manual/Plugins.html) .

1. Wklej plik **Newtonsoft. JSON. dll** do katalogu **wtyczek** projektu aparatu Unity.

1. Utwórz plik o nazwie **link. XML** w katalogu **zasobów** projektu Unity i Dodaj następujący kod XML.  Pozwoli to zagwarantować, że proces oddzielającego kodu bajtowego mechanizmu Unity nie powoduje usunięcia niezbędnych danych, podczas eksportowania platformę IL2CPP.  Ten krok jest specyficzne dla tej biblioteki, mogą występować problemy z innych bibliotek, które używają odbicia w podobny sposób.  Aby uzyskać więcej informacji, zobacz dokumentację [aparatu Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) w tym temacie.

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

Za pomocą starsze środowisko uruchomieniowe .NET 3.5 ciągów wymagane składni niewygodna. Teraz przy użyciu środowiska uruchomieniowego .NET 4. x funkcja [interpolacji ciągu`$`](https://docs.microsoft.com/dotnet/csharp/language-reference/tokens/interpolated) umożliwia wstawianie wyrażeń do ciągów w bardziej bezpośrednie i czytelnej składni:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Elementy członkowskie z wyrażeniem

Mając nowszą C# składnię dostępną w środowisku uruchomieniowym .NET 4. x, [wyrażenia lambda](https://docs.microsoft.com/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) mogą zastąpić treść funkcji, aby były bardziej zwięzłe:

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

[Programowanie asynchroniczne](https://docs.microsoft.com/dotnet/csharp/async) umożliwia czasochłonne operacje bez powodowania, że aplikacja przestanie odpowiadać. Ta funkcja umożliwia także swój kod, aby czekać na operacje dużo czasu na zakończenie przed kontynuowaniem kod, który jest zależny od wyniki tych operacji. Można na przykład trzeba odczekać pliku do obciążenia lub na zakończenie operacji sieciowych.

W środowisku Unity programowanie asynchroniczne jest zwykle realizowane przy użyciu [procedur wspólnych](https://docs.unity3d.com/Manual/Coroutines.html). Jednak od C# 5, preferowana metoda programowania asynchronicznego w środowisku programowania .NET była [oparta na zadaniach wzorca asynchronicznego (TAP)](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) przy użyciu słów kluczowych `async` i `await` z obiektem [System. Threading. Task](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task). Podsumowując, w funkcji `async` można `await` ukończenie zadania bez blokowania pozostałej części aplikacji przed aktualizacją:

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

* Funkcje asynchroniczne przeznaczone do oczekiwania powinny mieć typ zwracany [`Task`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task) lub [`Task<TResult>`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task-1).
* Funkcje asynchroniczne, które zwracają zadanie, powinny mieć sufiks **"Async"** dołączony do ich nazw. Przyrostku "Async" pomaga wskazać funkcji zawsze należy oczekiwane.
* Użyj `async void` zwracanego typu dla funkcji, które wyłączają funkcje asynchroniczne z tradycyjnego kodu synchronicznego. Takie funkcje, nie może się być oczekiwana i nie powinny mieć przyrostku "Async" w nazwach.
* Unity używa UnitySynchronizationContext, aby upewnić się, że funkcje asynchroniczne domyślnie uruchamiane w wątku głównym. Interfejs API aparatu Unity nie jest niedostępny poza wątku głównego.
* Istnieje możliwość uruchamiania zadań w wątkach w tle z metodami takimi jak [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) i [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Ta technika jest przydatny przy przekazywaniu kosztownych operacji z wątku głównego w celu zwiększenia wydajności. Korzystanie z wątków w tle może jednak prowadzić do problemów, które są trudne do debugowania, takich jak sytuacje [wyścigu](https://wikipedia.org/wiki/Race_condition).
* Interfejs API aparatu Unity nie jest dostępny na zewnątrz głównego wątku.
* Tworzy zadania, użyj wątki nie są obsługiwane w WebGL aparatu Unity.

#### <a name="differences-between-coroutines-and-tap"></a>Różnice w koprocedury i naciśnij pozycję

Istnieją pewne ważne różnice między w koprocedury i naciśnij pozycję / async-await:

* Współprocedury nie mogą zwracać wartości, ale `Task<TResult>` mogą.
* Nie można umieścić `yield` w instrukcji try-catch, co sprawia, że obsługa błędów jest trudna z procedurami. Try-catch — działa jednak naciśnięciem.
* Unity w koprocedury funkcja jest niedostępna w klasach, które nie pochodzą z obiekt MonoBehaviour. NACIŚNIJ to idealne narzędzie do programowania asynchronicznego w tych grupach.
* W tym momencie Unity nie sugerują wzorca TAP jako całościowego zastąpienia procedur wspólnych. Profilowanie jest jedynym sposobem ustalenia określone wyniki z jednej metody, a drugi dla każdego projektu w serwisie.

> [!NOTE]
> W przypadku aparatu Unity 2018,2 debugowanie metod asynchronicznych za pomocą punktów przerwania nie jest w pełni obsługiwane. jednak [Ta funkcja jest oczekiwana w środowisku Unity 2018,3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof operator

Operator `nameof` Pobiera nazwę ciągu zmiennej, typu lub składowej. Niektóre przypadki, w których `nameof` są przydatne, są błędy rejestrowania i pobieranie nazwy ciągu wyliczenia:

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

[Atrybuty informacji o wywołującym](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/caller-information) zawierają informacje o wywołującym metodę. Należy podać wartość domyślną dla każdego parametru, który chcesz korzystać z atrybutem informacji o obiekcie wywołującym:

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

[Użycie static](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/using-static) umożliwia korzystanie z funkcji statycznych bez wpisywania nazwy klasy. Przy użyciu statycznych, można zapisać czas i miejsce, jeśli musisz użyć kilku statyczne funkcje z tej samej klasy:

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

Podczas eksportowania swoją grę do platform, takich jak iOS, Unity użyje jej aparat IL2CPP "transpiluj" IL dla kodu C++, który następnie jest kompilowany przy użyciu natywnego kompilatora platformę docelową. W tym scenariuszu istnieje kilka funkcji platformy .NET, które nie są obsługiwane, takie jak części odbicia i użycie słowa kluczowego `dynamic`. Podczas korzystania z tych funkcji we własnym kodzie można kontrolować, mogą występować problemy z używaniem 3rd dll innych firm i zestawy SDK, które nie zostały zapisane za pomocą aparatu Unity i IL2CPP na uwadze. Więcej informacji na ten temat można znaleźć w dokumentacji dotyczącej [ograniczeń skryptów](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) w witrynie aparatu Unity.

Ponadto jak wspomniano w powyższym przykładzie na składnik Json.NET, Unity będzie podejmować próby odłączenia nieużywany kod w procesie IL2CPP eksportu.  Chociaż zwykle nie jest to problem, z bibliotekami, które używają odbicia, może przypadkowo oddzielić właściwości lub metody, które będą wywoływane w czasie wykonywania, których nie można określić w czasie eksportowania.  Aby rozwiązać te problemy, Dodaj plik **link. XML** do projektu, który zawiera listę zestawów i przestrzenie nazw, dla których nie ma zostać uruchomiony proces usuwania.  Aby uzyskać szczegółowe informacje, zobacz [dokumenty aparatu Unity dotyczące rozdzielania kodu bajtowego](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Programu .NET 4.x przykładowego projektu aparatu Unity

Przykład zawiera przykłady niektórych funkcji programu .NET 4.x. Możesz pobrać projekt lub wyświetlić kod źródłowy w serwisie [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Blog aparatu Unity — ulepszenia środowiska uruchomieniowego skryptów w środowisku Unity 2018,2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [HistoriaC#](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-version-history)
* [Co nowego w C# 6](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-6)
* [Programowanie asynchroniczne w aparacie Unity przy użyciu wspólnej procedury i naciśnij](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Metoda async-await zamiast procedur wspólnych w środowisku Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Forum aparatu Unity — eksperymentalne podglądy skryptów](https://forum.unity.com/forums/experimental-scripting-previews.107/)
