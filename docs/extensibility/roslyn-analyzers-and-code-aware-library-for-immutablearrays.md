---
title: Analizatory Roslyn i Biblioteka obsługująca kod ImmutableArrays | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8665a37e4afd387ff4f77a8bdb5da430d773ae1d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848716"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizatory Roslyn i Biblioteka obsługująca kod ImmutableArrays

[.NET compiler platform](https://github.com/dotnet/roslyn) ("Roslyn") ułatwia tworzenie bibliotek obsługujących kod. Biblioteka obsługująca kod udostępnia funkcje, których można używać i narzędzi (analizatory Roslyn), aby ułatwić korzystanie z biblioteki w najlepszy sposób lub w celu uniknięcia błędów. W tym temacie pokazano, jak utworzyć prawdziwą Roslyn Analizator do przechwytywania typowych błędów podczas korzystania z pakietu NuGet [System. Collections. niezmienna](https://www.nuget.org/packages/System.Collections.Immutable) . W przykładzie pokazano również, jak podać poprawkę kodu dla problemu z kodem znalezionym przez analizator. Użytkownicy widzą poprawki kodu w interfejsie użytkownika programu Visual Studio Light żarówki i mogą zastosować poprawkę dla kodu automatycznie.

## <a name="get-started"></a>Wprowadzenie

Aby skompilować ten przykład, potrzebne są następujące elementy:

* Visual Studio 2015 (nie wersja Express) ani nowsza. Możesz użyć bezpłatnej [wersji programu Visual Studio Community](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Podczas instalowania programu Visual Studio można także sprawdzić, **Visual Studio Extensibility Tools** w obszarze **popularne narzędzia** , aby zainstalować zestaw SDK w tym samym czasie. Jeśli zainstalowano już program Visual Studio, można również zainstalować ten zestaw SDK, przechodząc do **pliku** menu głównego ** > nowym** > **projektu**, **C#** wybierając w lewym okienku nawigacji, a następnie wybierając **rozszerzalność**. Po wybraniu szablonu projektu z łączami "**zainstaluj Visual Studio Extensibility Tools**" zostanie wyświetlony komunikat z prośbą o pobranie i zainstalowanie zestawu SDK.
* [.NET compiler platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Możesz również zainstalować ten zestaw SDK, przechodząc do **pliku** menu głównego > **nowym** > **projektu**, wybierając **C#** w lewym okienku nawigacji, a następnie wybierając **rozszerzalność**. Po wybraniu opcji "Pobierz szablon projektu z łączami **.NET COMPILER Platform SDK**" zostanie wyświetlony komunikat z prośbą o pobranie i zainstalowanie zestawu SDK. Ten zestaw SDK zawiera [Syntax Visualizer Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). To przydatne narzędzie pomaga ustalić, jakie typy modeli kodu należy wyszukać w analizatorze. Infrastruktura analizatora wywołuje kod dla określonych typów modelu kodu, więc kod jest wykonywany tylko w razie potrzeby i może skupić się tylko na analizie odpowiedniego kodu.

## <a name="whats-the-problem"></a>Jaki jest problem?

Załóżmy, że udostępniasz bibliotekę z obsługą element ImmutableArray (na przykład <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>). C#Deweloperzy mają wiele doświadczeń z tablicami .NET. Jednak ze względu na charakter ImmutableArrays i technik optymalizacji używanych w implementacji, programista C# intuitions może spowodować, że użytkownicy biblioteki piszą uszkodzony kod, jak wyjaśniono poniżej. Ponadto użytkownicy nie widzą swoich błędów do czasu uruchomienia, który nie jest obsługiwany przez program w programie Visual Studio z platformą .NET.

Użytkownicy znają pisanie kodu w następujący sposób:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Tworzenie pustych tablic do wypełnienia przy użyciu kolejnych wierszy kodu i użycie składni inicjatora kolekcji jest znane C# deweloperom. Jednak zapisanie tego samego kodu dla element ImmutableArray awarii w czasie wykonywania:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Pierwszy błąd jest spowodowany implementacją element ImmutableArray przy użyciu struktury do zawijania bazowego magazynu danych. Struktury muszą mieć konstruktory bez parametrów, aby wyrażenia `default(T)` mogły zwracać struktury ze wszystkimi elementami członkowskimi zero lub null. Gdy kod uzyskuje dostęp do `b1.Length`, występuje błąd wypełniania wartości null w czasie wykonywania, ponieważ nie istnieje bazowa tablica magazynowa w strukturze element ImmutableArray. Prawidłowy sposób tworzenia pustej element ImmutableArray jest `ImmutableArray<int>.Empty`.

Błąd z inicjatorami kolekcji jest spowodowany tym, że metoda `ImmutableArray.Add` zwraca nowe wystąpienia przy każdym wywołaniu go. Ponieważ ImmutableArrays nigdy nie zmienia się, podczas dodawania nowego elementu otrzymujesz nowy obiekt element ImmutableArray (co może współdzielić magazyn ze względu na wydajność przy użyciu wcześniej istniejącego element ImmutableArray). Ponieważ `b2` wskazuje na pierwszy element ImmutableArray przed wywołaniem `Add()` pięć razy, `b2` jest domyślną element ImmutableArray. Wywoływanie długości na nim również ulega awarii z powodu błędu dereferencji o wartości null. Prawidłowym sposobem na zainicjowanie element ImmutableArray bez ręcznego wywoływania elementu Add jest użycie `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Znajdź odpowiednie typy węzłów składni, aby wyzwolić Analizator

 Aby rozpocząć Kompilowanie analizatora, należy najpierw ustalić, jakiego typu SyntaxNode należy szukać. Uruchom **Syntax Visualizer** z **widoku** menu, > **inne Roslyn systemu Windows** > **Syntax Visualizer**.

Umieść karetkę edytora w wierszu, który deklaruje `b1`. Zobaczysz, że Syntax Visualizer pokazuje, że znajdujesz się w węźle `LocalDeclarationStatement` drzewa składni. Ten węzeł ma `VariableDeclaration`, która z kolei ma `VariableDeclarator`, która z kolei ma `EqualsValueClause`, a na koniec istnieje `ObjectCreationExpression`. Po kliknięciu w drzewie Syntax Visualizer węzłów, składnia w oknie edytora podświetla się, aby wyświetlić kod reprezentowany przez ten węzeł. Nazwy podtypów SyntaxNode są zgodne z nazwami używanymi w C# gramatyce.

## <a name="create-the-analyzer-project"></a>Utwórz projekt analizatora

Z menu głównego wybierz kolejno pozycje **plik** > **Nowy** > **projekt**. W oknie dialogowym **Nowy projekt** w obszarze **C#** projekty na lewym pasku nawigacyjnym wybierz pozycję **rozszerzalność**, a następnie w prawym okienku wybierz szablon projektu **poprawka kodu** . Wprowadź nazwę i Potwierdź okno dialogowe.

Szablon otwiera plik *DiagnosticAnalyzer.cs* . Wybierz kartę bufor edytora. Ten plik ma klasę analizatora (utworzoną na podstawie nazwy utworzonego projektu), która pochodzi od `DiagnosticAnalyzer` (typ interfejsu API Roslyn). Nowa klasa ma `DiagnosticAnalyzerAttribute` deklarujących analizatora jest istotna dla C# języka, dzięki czemu kompilator odnajduje i ładuje Analizator.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Można zaimplementować Analizator przy użyciu Visual Basic, który jest C# obiektem docelowym i na odwrót. Jest to ważniejsze w DiagnosticAnalyzerAttribute, aby określić, czy analizator jest przeznaczony dla jednego języka, czy do obu tych elementów. Bardziej zaawansowane analizatory wymagające szczegółowego modelowania języka mogą dotyczyć tylko jednego języka. Jeśli na przykład Analizator sprawdza tylko nazwy typów lub publiczne nazwy składowe, może być możliwe użycie Roslyn z modelami języka wspólnego w różnych Visual Basic i C#. Na przykład FxCop ostrzega, że klasa implementuje <xref:System.Runtime.Serialization.ISerializable>, ale Klasa nie ma atrybutu <xref:System.SerializableAttribute> nie jest zależna od języka i działa zarówno dla Visual Basic jak i C# kodu.

## <a name="initialize-the-analyzer"></a>Inicjowanie analizatora

 Przewiń w dół do klasy `DiagnosticAnalyzer`, aby wyświetlić metodę `Initialize`. Kompilator wywołuje tę metodę podczas aktywowania analizatora. Metoda przyjmuje `AnalysisContext` obiektu, który umożliwia analizatorowi uzyskiwanie informacji o kontekście i rejestrowanie wywołań zwrotnych dla zdarzeń dla rodzaju kodu, który ma zostać przeanalizowany.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Otwórz nowy wiersz w tej metodzie i wpisz "context". Aby wyświetlić listę uzupełniania IntelliSense. Na liście uzupełniania można zobaczyć wiele metod `Register...` do obsługi różnych rodzajów zdarzeń. Na przykład pierwszy `RegisterCodeBlockAction`, wywołuje z powrotem do kodu dla bloku, który zazwyczaj jest kodem między nawiasami klamrowymi. Rejestracja dla bloku powoduje także wywołanie zwrotne do kodu dla inicjatora pola, wartość podaną dla atrybutu lub wartość parametru opcjonalnego.

Innym przykładem jest `RegisterCompilationStartAction`, wywołania zwrotne do kodu na początku kompilacji, co jest przydatne, gdy konieczne jest zebranie stanu w wielu lokalizacjach. Można utworzyć strukturę danych, na przykład w celu zebrania wszystkich używanych symboli, a przy każdym wywołaniu analizatora z powrotem dla określonej składni lub symbolu można zapisać informacje o każdej lokalizacji w strukturze danych. Po wywołaniu z powrotem z powodu zakończenia kompilacji można analizować wszystkie zapisane lokalizacje, na przykład, aby zgłosić symbole używane przez kod z każdej instrukcji `using`.

Korzystając z **Syntax Visualizer**, wiesz, że chcesz wywołać, gdy kompilator przetwarza ObjectCreationExpression. Ten kod służy do konfigurowania wywołania zwrotnego:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Rejestrujesz dla węzła składni i Filtruj tylko dla węzłów składni tworzenia obiektów. Zgodnie z Konwencją, autorzy analizatorów używają wyrażenia lambda podczas rejestrowania akcji, co pomaga w utrzymaniu analizatorów bezstanowych. Korzystając z funkcji programu Visual Studio, **można utworzyć metodę** `AnalyzeObjectCreation`. Spowoduje to wygenerowanie poprawnego typu parametru kontekstowego.

## <a name="set-properties-for-users-of-your-analyzer"></a>Ustawianie właściwości dla użytkowników analizatora

Aby analizator został odpowiednio wyświetlony w interfejsie użytkownika programu Visual Studio, należy poszukać i zmodyfikować następujący wiersz kodu, aby zidentyfikować analizator:

```csharp
internal const string Category = "Naming";
```

Zmiana `"Naming"` do `"API Guidance"`.

Następnie Znajdź i Otwórz plik *resources. resx* w projekcie przy użyciu **Eksplorator rozwiązań**. Możesz umieścić w opisie analizatora, tytuł itd. Możesz zmienić wartość dla wszystkich tych elementów, aby `"Don't use ImmutableArray<T> constructor"` teraz. Argumenty formatowania ciągu można umieścić w ciągu ({0}, {1}itp.), a następnie po wywołaniu `Diagnostic.Create()`można podać `params` tablicę argumentów do przekazania.

## <a name="analyze-an-object-creation-expression"></a>Analizowanie wyrażenia tworzenia obiektu

Metoda `AnalyzeObjectCreation` przyjmuje inny typ kontekstu dostarczany przez strukturę analizatora kodu. `AnalysisContext` metody `Initialize` umożliwia zarejestrowanie wywołań zwrotnych akcji w celu skonfigurowania analizatora. Na przykład `SyntaxNodeAnalysisContext`ma `CancellationToken`, które można przekazać. Jeśli użytkownik zacznie pisać w edytorze, Roslyn będzie anulować uruchamianie analizatorów, aby zaoszczędzić pracę i zwiększyć wydajność. Innym przykładem jest to, że ten kontekst ma właściwość węzła, która zwraca węzeł składnia tworzenia obiektów.

Pobierz węzeł, który można założyć jako typ, dla którego przefiltrowany zostanie akcja węzła składni:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Uruchamiaj program Visual Studio przy użyciu analizatora po raz pierwszy

Uruchom program Visual Studio, kompilując i wykonując analizator (naciśnij klawisz **F5**). Ponieważ projekt startowy w **Eksplorator rozwiązań** jest projektem VSIX, uruchomienie kodu kompiluje kod i VSIX, a następnie uruchamia program Visual Studio z zainstalowanym tym VSIX. Gdy uruchamiasz program Visual Studio w ten sposób, zostanie on uruchomiony z odrębną gałęzią rejestru, dzięki czemu Twoje wystąpienia testowania nie będą miały wpływu na główne użycie programu Visual Studio podczas tworzenia analizatorów. Przy pierwszym uruchomieniu w ten sposób program Visual Studio wykonuje kilka inicjalizacji podobne do momentu pierwszego uruchomienia programu Visual Studio po jego zainstalowaniu.

Utwórz projekt konsoli, a następnie wprowadź kod tablicy w metodzie głównej aplikacji konsolowej:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Wiersze kodu z `ImmutableArray` są podkreślane, ponieważ trzeba uzyskać niezmienny pakiet NuGet i dodać instrukcję `using` do kodu. Naciśnij przycisk prawy wskaźnik w węźle projektu w **Eksplorator rozwiązań** i wybierz polecenie **Zarządzaj pakietami NuGet**. W Menedżerze NuGet wpisz "niezmienne" w polu wyszukiwania, a następnie wybierz element **System. Collections.** unBcld (nie wybieraj **Microsoft..** und) w okienku po lewej stronie, a następnie naciśnij przycisk **Instaluj** w okienku po prawej stronie. Zainstalowanie pakietu dodaje odwołanie do odwołania do projektu.

Nadal widzisz czerwoną zygzaki w obszarze `ImmutableArray`, więc Umieść karetkę w tym identyfikatorze i naciśnij klawisz **Ctrl**+ **.** (okres), aby wyświetlić menu sugerowane rozwiązanie i wybrać opcję dodania odpowiedniej instrukcji `using`.

**Zapisz wszystko i Zamknij** drugie wystąpienie programu Visual Studio, aby teraz zapewnić czysty stan, aby kontynuować.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Kończenie analizatora przy użyciu funkcji Edytuj i Kontynuuj

W pierwszym wystąpieniu programu Visual Studio Ustaw punkt przerwania na początku metody `AnalyzeObjectCreation`, naciskając klawisz **F9** z karetką w pierwszym wierszu.

Ponownie uruchom Analizator przy użyciu klawisza **F5**i w drugim wystąpieniu programu Visual Studio ponownie otwórz utworzoną przez siebie aplikację konsolową.

Powrócisz do pierwszego wystąpienia programu Visual Studio w punkcie przerwania, ponieważ kompilator Roslyn napotkał wyrażenie tworzenia obiektu i wywołało je do analizatora.

**Pobierz węzeł tworzenia obiektów.** Przejdź nad wierszem, który ustawia zmienną `objectCreation`, naciskając klawisz **F10**, a w **oknie bezpośrednim** Oceń wyrażenie `"objectCreation.ToString()"`. Zobaczysz, że składnia węzła zmienna wskazuje, że jest to kod `"new ImmutableArray<int>()"`, tylko to, czego szukasz.

**Pobierz obiekt typu element ImmutableArray < T\>.** Należy sprawdzić, czy tworzony typ to element ImmutableArray. Najpierw uzyskuje się obiekt, który reprezentuje ten typ. Sprawdzasz typy przy użyciu modelu semantycznego, aby upewnić się, że masz dokładnie właściwy typ i nie porównasz ciągu z `ToString()`. Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Typy ogólne można wyznaczyć w metadanych przy użyciu znaczników kreskowych (") i liczby parametrów ogólnych. Dlatego nie widzisz "... Element ImmutableArray\<T > "w nazwie metadanych.

Model semantyczny ma wiele przydatnych elementów, które umożliwiają zadawanie pytań dotyczących symboli, przepływu danych, zmiennego okresu istnienia itd. Roslyn oddziela węzły składni od modelu semantycznego dla różnych powodów inżynieryjnych (wydajności, modelowania kodu, itp.). Chcesz, aby model kompilacji wyszukał informacje zawarte w odwołaniach dla dokładnego porównania.

Żółty wskaźnik wykonywania można przeciągnąć po lewej stronie okna edytora. Przeciągnij go do wiersza, który ustawia zmienną `objectCreation` i przekroczy swój nowy wiersz kodu przy użyciu klawisza **F10**. Jeśli umieścisz wskaźnik myszy nad zmienną `immutableArrayOfType`, zobaczysz, że znaleźliśmy dokładny typ w modelu semantycznym.

**Pobierz typ wyrażenia tworzenia obiektu.** "Typ" jest używany na kilka sposobów w tym artykule, ale oznacza to, że jeśli masz wyrażenie "New foo", musisz uzyskać model foo. Musisz uzyskać typ wyrażenia tworzenia obiektów, aby zobaczyć, czy jest to element ImmutableArray\<T > typu. Użyj ponownie modelu semantycznego, aby uzyskać informacje o symbolach dla symbolu typu (element ImmutableArray) w wyrażeniu tworzenia obiektu. Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Ponieważ analizator musi obsłużyć niekompletny lub niepoprawny kod w buforach edytora (na przykład brak instrukcji `using`), należy sprawdzić `symbolInfo` `null`. Aby zakończyć analizę, należy uzyskać nazwany typ (INamedTypeSymbol) z obiektu informacji o symbolach.

**Porównaj typy.** Ponieważ istnieje otwarty typ ogólny T, którego szukasz, a typ w kodzie jest konkretnym typem ogólnym, należy zbadać informacje o symbolach, z których jest tworzony typ (otwarty typ ogólny) i porównać ten wynik z `immutableArrayOfTType`. Wprowadź następujące na końcu metody:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Zgłoś diagnostykę.** Raportowanie diagnostyki jest bardzo proste. Używasz utworzonej dla Ciebie reguły w szablonie projektu, która jest zdefiniowana przed zainicjowaniem metody. Ponieważ ta sytuacja w kodzie jest błędem, można zmienić wiersz, w którym reguła została zainicjowana, aby zastąpić `DiagnosticSeverity.Warning` (zielony zygzak) `DiagnosticSeverity.Error` (czerwona zygzakowata). Pozostała część reguły jest inicjowana z zasobów edytowanych na początku przewodnika. Należy również zgłosić lokalizację zygzaka, czyli lokalizację specyfikacji typu wyrażenia tworzenia obiektów. Wprowadź ten kod w bloku `if`:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Twoja funkcja powinna wyglądać następująco (prawdopodobnie sformatowana inaczej):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Usuń punkt przerwania, aby zobaczyć, że analizator działa (i Zatrzymaj powrót do pierwszego wystąpienia programu Visual Studio). Przeciągnij wskaźnik wykonania na początek metody, a następnie naciśnij klawisz **F5** , aby kontynuować wykonywanie. Po przełączeniu się z powrotem do drugiego wystąpienia programu Visual Studio kompilator rozpocznie ponowne sprawdzenie kodu i nastąpi wywołanie do analizatora. Możesz zobaczyć zygzak w obszarze `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Dodawanie "poprawki kodu" dla problemu z kodem

Przed rozpoczęciem Zamknij drugie wystąpienie programu Visual Studio i Zatrzymaj debugowanie w pierwszym wystąpieniu programu Visual Studio (gdzie tworzysz Analizator).

**Dodaj nową klasę.** Użyj menu skrótów (przycisk prawy wskaźnik) w węźle projektu w **Eksplorator rozwiązań** i wybierz polecenie Dodaj nowy element. Dodaj klasę o nazwie `BuildCodeFixProvider`. Ta klasa musi pochodzić od `CodeFixProvider`i należy użyć **klawisza Ctrl**+ **.** (okres) do wywołania poprawki kodu, która dodaje poprawną instrukcję `using`. Do tej klasy należy również dodać adnotację przy użyciu atrybutu `ExportCodeFixProvider`, a w celu rozpoznania `LanguageNames` enum konieczne będzie dodanie instrukcji `using`. Powinien istnieć plik klasy z następującym kodem:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Wyprowadzanie pochodnych elementów członkowskich.** Teraz umieść karetkę edytora w identyfikatorze `CodeFixProvider` i naciśnij klawisz **Ctrl**+ **.** (okres) do wypróbowania wdrożenia dla tej abstrakcyjnej klasy bazowej. Spowoduje to wygenerowanie właściwości i metody.

**Zaimplementuj właściwość.** Wypełnij treść `get` właściwości `FixableDiagnosticIds` następującym kodem:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn łączy diagnostykę i poprawki, dopasowując te identyfikatory, które są tylko ciągami. Szablon projektu wygenerował identyfikator diagnostyczny i możesz go zmienić. Kod w właściwości po prostu zwraca identyfikator z klasy analizatora.

**Metoda RegisterCodeFixAsync przyjmuje kontekst.** Kontekst jest ważny, ponieważ poprawka kodu może być stosowana do wielu diagnostyki lub może istnieć więcej niż jeden problem w wierszu kodu. Jeśli wpiszesz "context". w treści metody na liście uzupełniania IntelliSense zostaną wyświetlone przydatne elementy członkowskie. Istnieje element CancellationToken, który można sprawdzić, aby sprawdzić, czy nie chce anulować poprawki. Istnieje członek dokumentu, który ma wiele użytecznych elementów członkowskich i pozwala uzyskać dostęp do obiektów modelu projektu i rozwiązania. Istnieje element członkowski zakresu, który jest początkiem i końcem lokalizacji kodu określonej podczas zgłaszania diagnostyki.

**Ustaw metodę jako asynchroniczną.** Pierwszym krokiem, który należy wykonać, jest poprawienie wygenerowanej deklaracji metody jako metody `async`. Poprawka kodu zastępowanie klasami zastępczymi out klasy abstrakcyjnej nie zawiera słowa kluczowego `async`, mimo że metoda zwraca `Task`.

**Pobierz katalog główny drzewa składni.** Aby zmodyfikować kod potrzebny do utworzenia nowego drzewa składni z zmianami wprowadzanymi przez poprawkę kodu. Potrzebujesz `Document` z kontekstu, aby wywołać `GetSyntaxRootAsync`. Jest to Metoda asynchroniczna ze względu na to, że nie masz nieznanej pracy, aby uzyskać drzewo składni, prawdopodobnie dołączając plik z dysku, analizowanie go i kompilowanie modelu kodu Roslyn. Interfejs użytkownika programu Visual Studio powinien odpowiadać w tym czasie, co umożliwia `async`. Zastąp wiersz kodu w metodzie następującym:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Znajdź węzeł z problemem.** Należy przekazać zakres kontekstu, ale znaleziony węzeł nie może być kodem, który trzeba zmienić. Raportowana Diagnostyka przekazała tylko zakres dla identyfikatora typu (w którym jest to zygzakowata), ale musisz zastąpić całe wyrażenie tworzenia obiektów, w tym słowa kluczowego `new` na początku i w nawiasach na końcu. Dodaj następujący kod do metody (i Użyj **klawiszy Ctrl**+ **.** Aby dodać instrukcję `using` dla `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Zarejestruj poprawkę kodu dla interfejsu użytkownika żarówki.** Po zarejestrowaniu poprawki kodu program Roslyn automatycznie podłącza się do interfejsu użytkownika programu Visual Studio Light żarówk. Użytkownicy końcowi będą mogli korzystać z **kombinacji klawiszy Ctrl**+ **.** (kropka), gdy analizator zazygzaka nieprawidłowego użycia konstruktora `ImmutableArray<T>`. Ponieważ kod naprawił dostawcę jest wykonywany tylko w przypadku wystąpienia problemu, możesz założyć, że masz wyrażenie tworzenia obiektów, którego szukasz. Z parametru context można zarejestrować nową poprawkę kodu, dodając następujący kod na końcu `RegisterCodeFixAsync` metody:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Należy umieścić karetkę edytora w identyfikatorze, `CodeAction`, a następnie użyć **klawiszy Ctrl**+ **.** (kropka), aby dodać odpowiednią instrukcję `using` dla tego typu.

Następnie umieść karetkę edytora w identyfikatorze `ChangeToImmutableArrayEmpty` i Użyj **klawiszy Ctrl**+ **.** ponownie Wygeneruj tę procedurę tworzenia tej metody.

W tym ostatnim fragmencie kodu zarejestrowano poprawkę kodu przez przekazanie `CodeAction` i identyfikatora diagnostyki dla rodzaju znalezionego problemu. W tym przykładzie istnieje tylko jeden identyfikator diagnostyczny, dla którego ten kod udostępnia poprawki, więc można po prostu przekazać pierwszy element tablicy identyfikatorów diagnostycznych. Po utworzeniu `CodeAction`przekazujesz tekst, który powinien być używany przez interfejs użytkownika żarówki jako opis poprawki kodu. Należy również przekazać funkcję, która pobiera CancellationToken i zwraca nowy dokument. Nowy dokument zawiera nowe drzewo składni zawierające używany przez Ciebie kod, który wywołuje `ImmutableArray.Empty`. Ten fragment kodu używa wyrażenia lambda, aby można było zamknąć węzeł objectCreation i dokument kontekstu.

**Utwórz nowe drzewo składni.** W `ChangeToImmutableArrayEmpty` metodzie, której wygenerowałeś wcześniej, Wprowadź wiersz kodu: `ImmutableArray<int>.Empty;`. Po ponownym wyświetleniu okna narzędzia **Syntax Visualizer** można zobaczyć, że ta składnia jest węzłem SimpleMemberAccessExpression. To właśnie Metoda musi być skonstruowana i zwrócona w nowym dokumencie.

Pierwsza zmiana w `ChangeToImmutableArrayEmpty` polega na dodaniu `async` przed `Task<Document>`, ponieważ generatory kodu nie mogą przyjąć metody asynchronicznej.

Wypełnij treść przy użyciu poniższego kodu, aby Metoda wyglądała podobnie do następującej:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

Należy umieścić karetkę edytora w identyfikatorze `SyntaxGenerator` i użyć **klawiszy Ctrl**+ **.** (kropka), aby dodać odpowiednią instrukcję `using` dla tego typu.

Ten kod używa `SyntaxGenerator`, który jest użytecznym typem służącym do konstruowania nowego kodu. Po uzyskaniu generatora dokumentu, który ma problem z kodem, `ChangeToImmutableArrayEmpty` wywołuje `MemberAccessExpression`, przekazując typ, do którego należy uzyskać dostęp, i przekazując nazwę elementu członkowskiego jako ciąg.

Następnie Metoda pobiera element główny dokumentu i ponieważ może to dotyczyć dowolnej pracy w przypadku ogólnego przypadku, kod oczekuje na to wywołanie i przekazuje token anulowania. Modele kodu Roslyn są niezmienne, podobnie jak praca z ciągiem .NET; Po zaktualizowaniu ciągu otrzymujesz nowy obiekt ciągu w zwracaniu. Po wywołaniu `ReplaceNode`otrzymujesz nowy węzeł główny. Większość drzewa składni jest współdzielona (ponieważ jest niezmienna), ale węzeł `objectCreation` jest zastępowany węzłem `memberAccess`, a także wszystkie węzły nadrzędne do katalogu głównego drzewa składni.

## <a name="try-your-code-fix"></a>Wypróbuj poprawkę kodu

Teraz możesz nacisnąć klawisz **F5** , aby uruchomić analizator w drugim wystąpieniu programu Visual Studio. Otwórz projekt konsoli, który był wcześniej używany. Teraz powinna zostać wyświetlona Żarówka, w której nowe wyrażenie tworzenia obiektów ma `ImmutableArray<int>`. Po naciśnięciu **klawiszy Ctrl**+ **.** (kropka), a następnie zobaczysz poprawkę kodu i zobaczysz automatycznie wygenerowaną różnicę kodu w interfejsie użytkownika żarówki. Roslyn tworzy to za Ciebie.

**Porada pakietu Pro:** Jeśli uruchomisz drugie wystąpienie programu Visual Studio i nie zobaczysz żarówki z poprawkami kodu, może być konieczne wyczyszczenie pamięci podręcznej składnika programu Visual Studio. Wyczyszczenie pamięci podręcznej wymusza, aby program Visual Studio ponownie przebadał składniki, więc program Visual Studio powinien następnie pobrać najnowszy składnik. Najpierw zamknij drugie wystąpienie programu Visual Studio. Następnie w **Eksploratorze Windows**przejdź do *%LocalAppData%\Microsoft\VisualStudio\16.0Roslyn\\* . ("16,0" zmiany z wersji do wersji za pomocą programu Visual Studio). Usuń podkatalog *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Porozmawiaj z projektem wideo i Zakończ kod

Ten przykład został opracowany i omówiony w [tym](https://channel9.msdn.com/events/Build/2015/3-725)scenariuszu. Porozmawiaj z analizatorem pracy i przeprowadzi Cię przez proces tworzenia.

Cały ukończony kod można zobaczyć [tutaj](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Podfoldery *DoNotUseImmutableArrayCollectionInitializer* i *DoNotUseImmutableArrayCtor* każdy z nich C# ma plik do znajdowania problemów C# i plik implementujący poprawki kodu, które są wyświetlane w interfejsie użytkownika programu Visual Studio Light żarówki. Należy zauważyć, że ukończony kod ma nieco bardziej abstrakcję, aby uniknąć pobierania element ImmutableArray\<T > typ obiektu w tryb failover. Używa zagnieżdżonych zarejestrowanej akcji do zapisania obiektu typu w kontekście, który jest dostępny przy każdym akcji podrzędnej (analiza tworzenia obiektów i analiza inicjalizacji kolekcji).

## <a name="see-also"></a>Zobacz także

* [\\\Build 2015](https://channel9.msdn.com/events/Build/2015/3-725)
* [Ukończony kod w usłudze GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Kilka przykładów w witrynie GitHub pogrupowanych na trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Inne dokumenty z witryny usługi GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Reguły FxCop zaimplementowane przy użyciu analizatorów Roslyn w witrynie GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
