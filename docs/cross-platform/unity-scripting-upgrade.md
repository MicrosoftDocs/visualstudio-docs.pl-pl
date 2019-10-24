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
ms.openlocfilehash: b1f10778c4866e67630fcac7af3b92b3de780aa5
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777741"
---
# <a name="using-net-4x-in-unity"></a>Używanie platformy .NET 4.x w aparacie Unity

C#i .NET, technologie bazowe skryptów środowiska Unity, nadal mogą otrzymywać aktualizacje, ponieważ firma Microsoft pierwotnie wydała je w 2002. Jednak deweloperzy środowiska Unity mogą nie wiedzieć o stałym strumieniu nowych funkcji dodanych do C# języka i .NET Framework. Jest to spowodowane tym, że przed Unity 2017,1 aparat Unity korzysta z programu .NET 3,5 równoważnego środowiska uruchomieniowego skryptów, w którym brakuje lat aktualizacji.

W wersji aparatu Unity 2017,1 środowisko Unity wprowadziło eksperymentalną wersję środowiska uruchomieniowego skryptów do wersji zgodnej z programem C# .NET 4,6, 6. W środowisku Unity 2018,1 środowisko uruchomieniowe programu .NET 4. x nie jest już uważane za eksperymentalne, natomiast starsze środowisko uruchomieniowe programu .NET 3,5 jest teraz uznawane za starszą wersję. Wraz z wydaniem aparatu Unity 2018,3, środowisko Unity jest projekcją w celu przeprowadzenia domyślnego wyboru środowiska uruchomieniowego skryptów i zaktualizowania jeszcze bardziej C# do 7. Aby uzyskać więcej informacji i najnowsze aktualizacje dotyczące tego przewodnika, Przeczytaj [wpis w blogu](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) aparatu Unity lub odwiedź [forum wglądu w skrypty eksperymentalne](https://forum.unity.com/forums/experimental-scripting-previews.107/). W międzyczasie zapoznaj się z poniższymi sekcjami, aby dowiedzieć się więcej o nowych funkcjach dostępnych teraz w środowisku uruchomieniowym obsługi skryptów .NET 4. x.

## <a name="prerequisites"></a>Wymagania wstępne

* [Unity 2017,1 lub nowszy](https://unity3d.com/) (zalecane jest 2018,2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Włączanie środowiska uruchomieniowego obsługi skryptów .NET 4. x w środowisku Unity

Aby włączyć środowisko uruchomieniowe skryptów .NET 4. x, wykonaj następujące czynności:

1. Otwórz PlayerSettings w Inspektorze Unity, wybierając **edytuj > ustawienia projektu > Player**.

1. Pod nagłówkiem **Konfiguracja** kliknij listę rozwijaną **wersja środowiska uruchomieniowego tworzenia skryptów** i wybierz **odpowiedniki .NET 4. x**. Zostanie wyświetlony monit o ponowne uruchomienie aparatu Unity.

![Wybierz odpowiednik .NET 4. x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Wybieranie między profilami .NET 4. x i .NET Standard 2,0

Po przełączeniu się do środowiska uruchomieniowego skryptów programu .NET 4. x można określić **poziom zgodności interfejsu API** za pomocą menu rozwijanego w PlayerSettings (**edytuj ustawienia projektu > > Player**). Dostępne są dwie opcje:

* **.NET Standard 2,0**. Ten profil jest zgodny z [profilem .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) opublikowanym przez platformę .NET Foundation. Środowisko Unity zaleca .NET Standard 2,0 dla nowych projektów. Jest to mniejsze niż .NET 4. x, co jest korzystne dla platform z ograniczoną wielkością. Ponadto aparat Unity zatwierdził obsługę tego profilu na wszystkich platformach obsługiwanych przez środowisko Unity.

* **.NET 4. x**. Ten profil zapewnia dostęp do najnowszego interfejsu API programu .NET 4. Obejmuje on cały kod dostępny w bibliotekach klas .NET Framework i obsługuje również profile .NET Standard 2,0. Użyj profilu .NET 4. x, jeśli projekt wymaga części interfejsu API, która nie jest uwzględniona w profilu .NET Standard 2,0. Niektóre części tego interfejsu API mogą jednak nie być obsługiwane na wszystkich platformach aparatu Unity.

Więcej informacji na temat tych opcji można znaleźć w [wpisie w blogu](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/)aparatu Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Dodawanie odwołań do zestawów w przypadku używania poziomu zgodności interfejsu API .NET 4. x

W przypadku używania ustawienia .NET Standard 2,0 na liście rozwijanej **poziomu zgodności interfejsu API** wszystkie zestawy w profilu interfejsu API są przywoływane i mogą być używane. Jednak w przypadku używania większego profilu platformy .NET 4. x niektóre zestawy, które są dostarczane z systemem Unity, nie są domyślnie przywoływane. Aby użyć tych interfejsów API, należy ręcznie dodać odwołanie do zestawu. Zestawy Unity można wyświetlić w katalogu **MonoBleedingEdge/lib/mono** instalacji edytora Unity:

![Katalog MonoBleedingEdge](media/vstu_monobleedingedge.png)

Na przykład, jeśli używasz profilu .NET 4. x i chcesz używać `HttpClient`, musisz dodać odwołanie do zestawu dla elementu System. NET. http. dll. Bez niej, kompilator będzie wnoszących skargę o brak odwołania do zestawu:

![Brak odwołania do zestawu](media/vstu_missing-reference.png)

Program Visual Studio generuje pliki. csproj i. sln dla projektów Unity przy każdym otwarciu. W związku z tym nie można dodać odwołań do zestawu bezpośrednio w programie Visual Studio, ponieważ zostaną one utracone po ponownym otwarciu projektu. Zamiast tego należy użyć specjalnego pliku tekstowego o nazwie **MCS. rsp** :

1. Utwórz nowy plik tekstowy o nazwie **MCS. rsp** w katalogu głównych **zasobów** projektu środowiska Unity.

1. W pierwszym wierszu pustego pliku tekstowego wpisz: `-r:System.Net.Http.dll` a następnie Zapisz plik. Plik "System. NET. http. dll" można zastąpić dowolnym zestawem dołączonym, w którym może brakować odwołania.

1. Uruchom ponownie edytor aparatu Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Korzystanie z zalet zgodności z platformą .NET

Oprócz nowych C# funkcji składni i języka środowisko uruchomieniowe skryptów .NET 4. x zapewnia użytkownikom Unity dostęp do ogromnej biblioteki pakietów .NET, które są niezgodne ze starszym środowiskiem obsługi skryptów .NET 3,5.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Dodawanie pakietów z narzędzia NuGet do projektu środowiska Unity

Pakiet [NuGet](https://www.nuget.org/) jest menedżerem pakietów dla platformy .NET. Pakiet NuGet jest zintegrowany z Visual Studio. Jednak projekty Unity wymagają specjalnego procesu dodawania pakietów NuGet. Jest to spowodowane tym, że po otwarciu projektu w aparacie Unity pliki projektu programu Visual Studio są ponownie generowane, cofają niezbędne konfiguracje. Aby dodać pakiet z programu NuGet do projektu środowiska Unity, wykonaj następujące czynności:

1. Przeglądaj program NuGet, aby zlokalizować zgodny pakiet, który chcesz dodać (.NET Standard 2,0 lub .NET 4. x). W tym przykładzie przedstawiono dodawanie [JSON.NET](https://www.nuget.org/packages/Newtonsoft.Json/), popularnego pakietu do pracy z JSON, do projektu .NET Standard 2,0.

1. Kliknij przycisk **Pobierz** :

    ![przycisk Pobierz](media/vstu_nuget-download.png)

1. Znajdź pobrany plik i Zmień rozszerzenie z **. nupkg** na **. zip**.

1. W pliku zip przejdź do katalogu **lib/Standard 2.0** i skopiuj plik **Newtonsoft. JSON. dll** .

1. W folderze głównych **zasobów** projektu środowiska Unity Utwórz nowy folder o nazwie **wtyczki**. Wtyczki to specjalna nazwa folderu w aparacie Unity. Aby uzyskać więcej informacji, zobacz [dokumentację aparatu Unity](https://docs.unity3d.com/Manual/Plugins.html) .

1. Wklej plik **Newtonsoft. JSON. dll** do katalogu **wtyczek** projektu aparatu Unity.

1. Utwórz plik o nazwie **link. XML** w katalogu **zasobów** projektu Unity i Dodaj następujący kod XML.  Zapewni to, że proces usuwania kodu bajtowego aparatu Unity nie spowoduje usunięcia niezbędnych danych podczas eksportowania na platformę IL2CPP.  Ten krok jest specyficzny dla tej biblioteki, ale może wystąpić problemy z innymi bibliotekami, które używają odbicia w podobny sposób.  Aby uzyskać więcej informacji, zobacz dokumentację [aparatu Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) w tym temacie.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

W przypadku wszystkich elementów na miejscu możesz teraz korzystać z pakietu Json.NET.

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

Jest to prosty przykład użycia biblioteki, która nie ma zależności. Gdy pakiety NuGet korzystają z innych pakietów NuGet, należy ręcznie pobrać te zależności i dodać je do projektu w taki sam sposób.

## <a name="new-syntax-and-language-features"></a>Nowe funkcje składni i języka

Za pomocą zaktualizowanego środowiska uruchomieniowego skryptów zapewnia deweloperom aparatu Unity dostęp do C# 6 i hosta nowych funkcji języka i składni.

### <a name="auto-property-initializers"></a>Inicjatory właściwości autoproperty

W środowisku uruchomieniowym skryptów .NET 3,5 aparatu Unity, składnia autowłaściwości ułatwia szybkie Definiowanie niezainicjowanych właściwości, ale Inicjalizacja musi być zawarta w innym miejscu skryptu. Teraz w przypadku środowiska uruchomieniowego .NET 4. x możliwe jest zainicjowanie autowłaściwości w tym samym wierszu:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolacja ciągów

W przypadku starszego środowiska uruchomieniowego programu .NET 3,5, łączenie ciągów wymagało składni niewygodna. Teraz przy użyciu środowiska uruchomieniowego .NET 4. x funkcja [interpolacji ciągu `$`](https://docs.microsoft.com/dotnet/csharp/language-reference/tokens/interpolated) umożliwia wstawianie wyrażeń do ciągów w bardziej bezpośrednie i czytelnej składni:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Składowe z wyrażeniem w treści

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

W właściwościach tylko do odczytu można również używać składowych wyrażeń w postaci:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Wzorzec asynchroniczny oparty na zadaniach (TAP)

[Programowanie asynchroniczne](https://docs.microsoft.com/dotnet/csharp/async) umożliwia czasochłonne operacje bez powodowania, że aplikacja przestanie odpowiadać. Ta funkcja umożliwia również kodowi oczekiwanie na zakończenie czasochłonnych operacji przed kontynuowaniem kodu, który zależy od wyników tych operacji. Na przykład możesz poczekać na załadowanie pliku lub zakończenie operacji sieciowej.

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

NACIŚNIĘCIe jest złożonym tematem, w przypadku których deweloperzy wszystkie szczegóły powinni wziąć pod uwagę. W związku z tym naciśnij pozycję nie jest uniwersalnym zastępowaniem wspólnych procedur w środowisku Unity; jest to jednak inne narzędzie do wykorzystania. Zakres tej funkcji wykracza poza ten artykuł, ale niektóre ogólne najlepsze rozwiązania i porady są podane poniżej.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Wprowadzenie do korzystania z programu TAP przy użyciu aparatu Unity

Te porady ułatwiają rozpoczęcie pracy z programem TAP w środowisku Unity:

* Funkcje asynchroniczne przeznaczone do oczekiwania powinny mieć typ zwracany [`Task`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task) lub [`Task<TResult>`](https://docs.microsoft.com/dotnet/api/system.threading.tasks.task-1).
* Funkcje asynchroniczne, które zwracają zadanie, powinny mieć sufiks **"Async"** dołączony do ich nazw. Sufiks "Async" pomaga wskazać, że funkcja powinna zawsze oczekiwać.
* Użyj `async void` zwracanego typu dla funkcji, które wyłączają funkcje asynchroniczne z tradycyjnego kodu synchronicznego. Takie funkcje nie mogą być oczekiwane i nie powinny mieć sufiksu "Async" w swoich nazwach.
* Środowisko Unity korzysta z UnitySynchronizationContext w celu zapewnienia domyślnego uruchamiania funkcji asynchronicznych w wątku głównym. Interfejs API Unity nie jest dostępny poza głównym wątkiem.
* Istnieje możliwość uruchamiania zadań w wątkach w tle z metodami takimi jak [`Task.Run`](https://msdn.microsoft.com/library/hh195051.aspx) i [`Task.ConfigureAwait(false)`](https://msdn.microsoft.com/library/system.threading.tasks.task.configureawait.aspx). Ta technika jest przydatna do odciążania kosztownych operacji z wątku głównego w celu zwiększenia wydajności. Korzystanie z wątków w tle może jednak prowadzić do problemów, które są trudne do debugowania, takich jak sytuacje [wyścigu](https://wikipedia.org/wiki/Race_condition).
* Interfejs API Unity nie jest dostępny poza głównym wątkiem.
* Zadania korzystające z wątków nie są obsługiwane w kompilacjach WebGL środowiska Unity.

#### <a name="differences-between-coroutines-and-tap"></a>Różnice między procedurami wspólną i NACIŚNIĘCIem

Istnieją pewne istotne różnice między procedurami wspólną i poleceniem TAP/Async-await:

* Współprocedury nie mogą zwracać wartości, ale `Task<TResult>` mogą.
* Nie można umieścić `yield` w instrukcji try-catch, co sprawia, że obsługa błędów jest trudna z procedurami. Jednak polecenie try-catch współpracuje z programem TAP.
* Funkcja wspólna aparatu Unity nie jest dostępna w klasach, które nie pochodzą od siebie. Program TAP jest doskonałym rozwiązaniem do programowania asynchronicznego w takich klasach.
* W tym momencie środowisko Unity nie sugeruje NACISKu na sprzedaż hurtową. Profilowanie jest jedynym sposobem, aby poznać konkretne wyniki jednego podejścia, a drugie dla każdego projektu.

> [!NOTE]
> W przypadku aparatu Unity 2018,2 debugowanie metod asynchronicznych za pomocą punktów przerwania nie jest w pełni obsługiwane. jednak [Ta funkcja jest oczekiwana w środowisku Unity 2018,3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>nameof, operator

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

### <a name="caller-info-attributes"></a>Atrybuty informacji o wywołującym

[Atrybuty informacji o wywołującym](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/caller-information) zawierają informacje o wywołującym metodę. Należy podać wartość domyślną dla każdego parametru, który ma być używany z atrybutem informacje o wywołującym:

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

### <a name="using-static"></a>Używanie static

[Użycie static](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/using-static) umożliwia korzystanie z funkcji statycznych bez wpisywania nazwy klasy. Korzystając ze statycznego, można zaoszczędzić miejsce i czas, jeśli trzeba użyć kilku funkcji statycznych z tej samej klasy:

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

Podczas eksportowania gry na platformy, takie jak iOS, środowisko Unity będzie używać aparatu IL2CPP do "transsterty" C++ Il do kodu, który jest następnie kompilowany przy użyciu natywnego kompilatora platformy docelowej. W tym scenariuszu istnieje kilka funkcji platformy .NET, które nie są obsługiwane, takie jak części odbicia i użycie słowa kluczowego `dynamic`. Chociaż możesz kontrolować korzystanie z tych funkcji w własnym kodzie, możesz wypróbować problemy przy użyciu bibliotek DLL innych firm i zestawów SDK, które nie zostały zapisaną przy użyciu aparatu Unity i IL2CPP. Więcej informacji na ten temat można znaleźć w dokumentacji dotyczącej [ograniczeń skryptów](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) w witrynie aparatu Unity.

Ponadto, jak wspomniano w powyższym przykładzie Json.NET, aparat Unity podejmie próbę odłożenia nieużywanego kodu podczas procesu eksportowania IL2CPP.  Chociaż zwykle nie jest to problem, z bibliotekami, które używają odbicia, może przypadkowo oddzielić właściwości lub metody, które będą wywoływane w czasie wykonywania, których nie można określić w czasie eksportowania.  Aby rozwiązać te problemy, Dodaj plik **link. XML** do projektu, który zawiera listę zestawów i przestrzenie nazw, dla których nie ma zostać uruchomiony proces usuwania.  Aby uzyskać szczegółowe informacje, zobacz [dokumenty aparatu Unity dotyczące rozdzielania kodu bajtowego](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Przykładowy projekt aparatu Unity dla programu .NET 4. x

Przykład zawiera przykłady kilku funkcji platformy .NET 4. x. Możesz pobrać projekt lub wyświetlić kod źródłowy w serwisie [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Blog aparatu Unity — ulepszenia środowiska uruchomieniowego skryptów w środowisku Unity 2018,2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [HistoriaC#](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-version-history)
* [Co nowego w C# 6](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-6)
* [Programowanie asynchroniczne w aparacie Unity przy użyciu wspólnej procedury i naciśnij](https://blogs.msdn.microsoft.com/appconsult/2017/09/01/unity-coroutine-tap)
* [Metoda async-await zamiast procedur wspólnych w środowisku Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Forum aparatu Unity — eksperymentalne podglądy skryptów](https://forum.unity.com/forums/experimental-scripting-previews.107/)
