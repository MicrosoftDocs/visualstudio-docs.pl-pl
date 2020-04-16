---
title: Analizatory Roslyn i biblioteka z uwzględnieniem kodu dla ImmutableArrays | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2076bc9fe3cabbfef8d3f3fb0248724835fa83f5
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444573"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizatory Roslyn i biblioteka z uwzględnieniem kodu dla NiezmienneArrays

[Platforma kompilatora .NET](https://github.com/dotnet/roslyn) ("Roslyn") ułatwia tworzenie bibliotek obsługujących kod. Biblioteka z uwzględnieniem kodu zapewnia funkcje, których można używać i narzędzi (analizatory Roslyn), aby ułatwić korzystanie z biblioteki w najlepszy sposób lub uniknąć błędów. W tym temacie pokazano, jak utworzyć analizator Roslyn w świecie rzeczywistym, aby złapać typowe błędy podczas korzystania z [pakietu System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet. W przykładzie pokazano również, jak podać poprawkę kodu dla problemu z kodem znalezionych przez analizatora. Użytkownicy widzą poprawki kodu w interfejsie żarówki programu Visual Studio i można zastosować poprawkę dla kodu automatycznie.

## <a name="get-started"></a>Wprowadzenie

Aby utworzyć ten przykład, potrzebujesz następujących elementów:

* Visual Studio 2015 (nie Express Edition) lub nowszej wersji. Można korzystać z bezpłatnego [programu Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Można również podczas instalowania programu Visual Studio, sprawdź **Visual Studio Narzędzia rozszerzalności** w obszarze **wspólne narzędzia,** aby zainstalować zestaw SDK w tym samym czasie. Jeśli program Visual Studio został już zainstalowany, można również zainstalować ten zestaw SDK, przechodząc do menu głównego **Plik** > **nowego** > **projektu,** wybierając **C#** w lewym okienku nawigacji, a następnie wybierając **opcję Rozszerzalność**. Po wybraniu szablonu projektu **"Zainstaluj narzędzia rozszerzalności programu Visual Studio"** monituje o pobranie i zainstalowanie zestawu SDK.
* [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). Można również zainstalować ten zestaw SDK, przechodząc do menu głównego **Plik** > **nowego** > **projektu,** wybierając **C#** w lewym okienku nawigacji, a następnie wybierając **opcję Rozszerzalność**. Po wybraniu szablonu projektu "Pobierz zestaw**SDK platformy kompilatora .NET"** monituje o pobranie i zainstalowanie pakietu SDK. Ten zestaw SDK zawiera [wizualizator składni Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). To przydatne narzędzie pomaga dowiedzieć się, jakie typy modeli kodu należy szukać w analizatorze. Infrastruktura analizatora wywołuje do kodu dla określonych typów modelu kodu, więc kod jest wykonywany tylko wtedy, gdy jest to konieczne i można skupić się tylko na analizowaniu odpowiedniego kodu.

## <a name="whats-the-problem"></a>W czym tkwi problem?

Wyobraź sobie, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>że udostępniasz bibliotekę z obsługą NiezmiennejArray (na przykład). Deweloperzy języka C# mają duże doświadczenie z macierzami .NET. Jednak ze względu na charakter NiezmienneArrays i technik optymalizacji stosowanych w implementacji, intuicja dewelopera języka C# spowodować użytkowników biblioteki do pisania uszkodzony kod, jak wyjaśniono poniżej. Ponadto użytkownicy nie widzą ich błędy do czasu wykonywania, który nie jest środowisko jakości, które są używane w programie Visual Studio z .NET.

Użytkownicy są zaznajomieni z pisaniem kodu, jak następujące:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Tworzenie pustych tablic do wypełnienia z kolejnych wierszy kodu i przy użyciu składni inicjatora kolekcji są znane deweloperom języka C#. Jednak pisanie tego samego kodu dla NiezmienneArray ulega awarii w czasie wykonywania:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Pierwszy błąd jest ze względu na implementacji NiezmienneArray przy użyciu struktury do zawijania magazynu danych źródłowych. Struktury muszą mieć konstruktory bez `default(T)` parametrów, aby wyrażenia mogły zwracać struktury ze wszystkimi elementami elementów członkowskich zero lub null. Gdy kod uzyskuje `b1.Length`dostęp, występuje błąd wyłudania czasu wykonywania null, ponieważ nie ma podstawowej tablicy magazynu w impstruktorze ImmutableArray. Właściwym sposobem utworzenia pustej NiezmiennejArray jest `ImmutableArray<int>.Empty`.

Błąd z inicjatorów kolekcji `ImmutableArray.Add` dzieje, ponieważ metoda zwraca nowe wystąpienia za każdym razem, gdy go wywołasz. Ponieważ NiezmienneArrays nigdy się nie zmienia, po dodaniu nowego elementu, można odzyskać nowy Obiekt NiezmienneArray (który może współużytkowania magazynu ze względu na wydajność z wcześniej istniejących ImmutableArray). Ponieważ `b2` wskazuje na pierwszy ImmutableArray przed wywołaniem `Add()` pięć razy, `b2` jest domyślny ImmutableArray. Wywołanie Length na nim również ulega awarii z błędem wyłuskania null. Prawidłowym sposobem zainicjowania NiezmienneArray bez ręcznego wywoływania Add jest użycie `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Znajdowanie odpowiednich typów węzłów składni w celu wyzwolenia analizatora

 Aby rozpocząć tworzenie analizatora, najpierw dowiedzieć się, jakiego typu SyntaxNode trzeba szukać. Uruchom **wizualizator syntaksu** z menu **Wyświetl** > inny**wizualizator składni roslyn****systemu Windows** > .

Umieść opiekunę redaktora w wierszu, `b1`który deklaruje . Zobaczysz Wizualizator składni pokazuje, że `LocalDeclarationStatement` znajdujesz się w węźle drzewa składni. Ten węzeł `VariableDeclaration`ma , który `VariableDeclarator`z kolei ma `EqualsValueClause`, który z kolei `ObjectCreationExpression`ma , i wreszcie jest . Po kliknięciu w drzewie wizualizatora składni węzłów, składnia w oknie edytora podświetla się, aby pokazać kod reprezentowany przez ten węzeł. Nazwy typów podrzędnych SyntaxNode są zgodne z nazwami używanymi w gramatyki języka C#.

## <a name="create-the-analyzer-project"></a>Tworzenie projektu analizatora

Z menu głównego wybierz polecenie **Plik** > **nowego** > **projektu**. W oknie dialogowym **Nowy projekt** w obszarze Projekty **języka C#** na lewym pasku nawigacyjnym wybierz pozycję **Rozszerzalność**, a w prawym okienku wybierz szablon projektu **Analizator z poprawką kodu.** Wprowadź nazwę i potwierdź okno dialogowe.

Szablon otworzy plik *DiagnosticAnalyzer.cs.* Wybierz tę kartę buforu edytora. Ten plik ma klasę analizatora (utworzona na podstawie nazwy `DiagnosticAnalyzer` nadanej projektowi), która pochodzi od (typ interfejsu API Roslyn). Nowa klasa ma `DiagnosticAnalyzerAttribute` deklarując analizatora jest istotne dla języka C#, dzięki czemu kompilator odnajduje i ładuje analizatora.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Można zaimplementować analizatora przy użyciu języka Visual Basic, który jest przeznaczony dla kodu C# i na odwrót. Jest ważniejsze w DiagnosticAnalyzerAttribute, aby wybrać, czy analizator jest przeznaczony dla jednego języka lub obu. Bardziej zaawansowane analizatory, które wymagają szczegółowego modelowania języka, mogą być kierowane tylko na jeden język. Jeśli analizator, na przykład tylko sprawdza nazwy typów lub nazwy elementów członkowskich publicznych, może być możliwe użycie modelu języka wspólnego Roslyn oferuje w języku Visual Basic i C#. Na przykład FxCop ostrzega, że <xref:System.Runtime.Serialization.ISerializable>klasa implementuje , <xref:System.SerializableAttribute> ale klasa nie ma atrybutu jest niezależny od języka i działa zarówno dla kodu języka Visual Basic i C#.

## <a name="initialize-the-analyzer"></a>Inicjowanie analizatora

 Przewiń w `DiagnosticAnalyzer` dół trochę `Initialize` w klasie, aby zobaczyć metodę. Kompilator wywołuje tę metodę podczas aktywacji analizatora. Metoda przyjmuje `AnalysisContext` obiekt, który umożliwia analizatorowi uzyskanie informacji kontekstowych i rejestrowanie wywołań zwrotnych dla zdarzeń dla rodzajów kodu, który chcesz przeanalizować.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Otwórz nowy wiersz w tej metodzie i wpisz "context". , aby wyświetlić listę uzupełnień IntelliSense. Na liście uzupełnień znajduje się `Register...` wiele metod obsługi różnego rodzaju zdarzeń. Na przykład pierwszy z `RegisterCodeBlockAction`nich , wywołuje z powrotem do kodu dla bloku, który jest zwykle kod między nawiasami klamrowymi. Rejestrowanie bloku również wywołuje z powrotem do kodu dla inicjatora pola, wartość nadana atrybutowi lub wartość parametru opcjonalnego.

Jako inny `RegisterCompilationStartAction`przykład , wywołuje z powrotem do kodu na początku kompilacji, co jest przydatne, gdy trzeba zebrać stan w wielu lokalizacjach. Można utworzyć strukturę danych, powiedzmy, aby zebrać wszystkie używane symbole, a za każdym razem, gdy analizator jest wywoływany z powrotem dla jakiejś składni lub symbolu, można zapisać informacje o każdej lokalizacji w strukturze danych. Po wywołaniu z powodu zakończenia kompilacji, można analizować wszystkie lokalizacje, które zostały zapisane, na przykład, `using` aby zgłosić, jakie symbole kod używa z każdej instrukcji.

Za pomocą **wizualizatora syntaksu,** dowiedziałeś się, że chcesz być wywoływane, gdy kompilator przetwarza ObjectCreationExpression. Ten kod służy do konfigurowania wywołania zwrotnego:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Rejestrujesz węzeł składni i filtr tylko dla węzłów składni tworzenia obiektów. Zgodnie z konwencją autorzy analizatora używają lambda podczas rejestrowania akcji, co pomaga zachować analizatory bezstanowe. Aby utworzyć `AnalyzeObjectCreation` metodę, można użyć funkcji Visual Studio **Generate From Usage.** Spowoduje to wygenerowanie odpowiedniego typu parametru kontekstu.

## <a name="set-properties-for-users-of-your-analyzer"></a>Ustawianie właściwości dla użytkowników analizatora

Aby analizator pojawił się w programie Visual Studio UI odpowiednio, poszukaj i zmodyfikuj następujący wiersz kodu, aby zidentyfikować analizatora:

```csharp
internal const string Category = "Naming";
```

Zmień `"Naming"` `"API Guidance"`na .

Następnie znajdź i otwórz plik *Resources.resx* w projekcie za pomocą **Eksploratora rozwiązań**. Możesz umieścić w opisie analizatora, tytułu itp. Można teraz zmienić wartość dla `"Don't use ImmutableArray<T> constructor"` wszystkich tych. Argumenty formatowania ciągów można umieścić{0} {1}w ciągu ( , itp.), a później podczas wywoływania `Diagnostic.Create()`można podać tablicę `params` argumentów, które mają być przekazane.

## <a name="analyze-an-object-creation-expression"></a>Analizowanie wyrażenia tworzenia obiektu

Metoda `AnalyzeObjectCreation` przyjmuje inny typ kontekstu dostarczanego przez platformę analizatora kodu. Metoda `Initialize` `AnalysisContext` umożliwia rejestrowanie wywołań zwrotnych akcji w celu skonfigurowania analizatora. Na `SyntaxNodeAnalysisContext`przykład `CancellationToken` ma, że można przejść wokół. Jeśli użytkownik rozpocznie wpisywanie w edytorze, Roslyn anuluje uruchomione analizatory, aby zapisać pracę i zwiększyć wydajność. Jako inny przykład ten kontekst ma Node właściwość, która zwraca węzeł składni tworzenia obiektu.

Pobierz węzeł, który można założyć, jest typem, dla którego filtrowane działania węzła składni:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Uruchamianie programu Visual Studio za pomocą analizatora za pierwszym razem

Uruchom program Visual Studio, tworząc i wykonując analizator (naciśnij klawisz **F5**). Ponieważ projekt uruchamiania w **Eksploratorze rozwiązań** jest projektem VSIX, uruchomienie kodu tworzy kod i VSIX, a następnie uruchamia program Visual Studio z zainstalowanym programem VSIX. Po uruchomieniu programu Visual Studio w ten sposób uruchamia się z gałęzi rejestru odrębne, dzięki czemu główne użycie programu Visual Studio nie będzie miało wpływu na wystąpienia testowania podczas tworzenia analizatorów. Przy pierwszym uruchomieniu w ten sposób program Visual Studio wykonuje kilka inicjalizacji podobnych do po raz pierwszy uruchomiony program Visual Studio po zainstalowaniu go.

Utwórz projekt konsoli, a następnie wprowadź kod tablicy w aplikacjach konsoli Główna metoda:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Wiersze kodu `ImmutableArray` z mają squiggles, ponieważ trzeba uzyskać niezmienne Pakiet `using` NuGet i dodać instrukcję do kodu. Naciśnij prawy przycisk wskaźnika w węźle projektu w **Eksploratorze rozwiązań** i wybierz pozycję **Zarządzaj pakietami NuGet**. W menedżerze NuGet wpisz "Niezmienne" w polu wyszukiwania i wybierz element **System.Collections.Immutable** (nie należy wybierać **Microsoft.Bcl.Immutable)** w lewym okienku i naciśnij przycisk **Zainstaluj** w prawym okienku. Instalowanie pakietu dodaje odwołanie do odwołań do projektu.

Nadal widzisz czerwone falisty `ImmutableArray`pod , więc umieść cieszę w tym identyfikatorze i naciśnij **klawisz Ctrl**+**.** (kropka), aby przywołać sugerowane menu poprawek `using` i dodać odpowiednią instrukcję.

**Zapisz wszystkie i zamknij** drugie wystąpienie programu Visual Studio na razie, aby umieścić cię w stanie czystym, aby kontynuować.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Kończenie analizatora przy użyciu funkcji edytuj i kontynuować

W pierwszym wystąpieniu programu Visual Studio ustaw punkt `AnalyzeObjectCreation` przerwania na początku metody, naciskając **klawisz F9** z opiekuchą w pierwszym wierszu.

Uruchom analizator ponownie za pomocą **F5**, a w drugim wystąpieniu programu Visual Studio ponownie otwórz aplikację konsoli utworzoną ostatnio.

Powrót do pierwszego wystąpienia programu Visual Studio w punkcie przerwania, ponieważ kompilator Roslyn zobaczył wyrażenie tworzenia obiektu i wywoływane w analizatorze.

**Pobierz węzeł tworzenia obiektu.** Krok nad wierszem, `objectCreation` który ustawia zmienną, naciskając **klawisz F10,** a w **oknie bezpośrednim** oceń wyrażenie `"objectCreation.ToString()"`. Widać, że węzeł składni, na który `"new ImmutableArray<int>()"`wskazuje zmienna, to kod , tylko to, czego szukasz.

**Pobierz Obiekt Typu<T.\>** Należy sprawdzić, czy tworzony typ jest ImmutableArray. Najpierw zostanie znaleziony obiekt reprezentujący ten typ. Sprawdzasz typy przy użyciu modelu semantycznego, aby upewnić się, że masz `ToString()`dokładnie odpowiedni typ i nie porównujesz ciągu z programu . Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Typy ogólne są wyznaczane w metadanych z backticks (') i liczba parametrów ogólnych. Dlatego nie widzisz "... ImmutableArray\<T>" w nazwie metadanych.

Model semantyczny ma wiele przydatnych rzeczy, które pozwalają zadawać pytania dotyczące symboli, przepływu danych, zmiennego okresu istnienia itp. Roslyn oddziela węzły składni od modelu semantycznego z różnych powodów inżynieryjnych (wydajność, modelowanie błędnego kodu itp.). Chcesz, aby model kompilacji wyszukywał informacje zawarte w odwołaniach do dokładnego porównania.

Żółty wskaźnik wykonania można przeciągnąć po lewej stronie okna edytora. Przeciągnij go do linii, `objectCreation` która ustawia zmienną i krok nad nowym wierszu kodu za pomocą **F10**. Po najechaniu wskaźnikiem `immutableArrayOfType`myszy na zmienną, zobaczysz, że znaleźliśmy dokładny typ w modelu semantycznym.

**Pobierz typ wyrażenia tworzenia obiektu.** "Typ" jest używany na kilka sposobów w tym artykule, ale oznacza to, że jeśli masz wyrażenie "nowe Foo", musisz uzyskać model Foo. Należy uzyskać typ wyrażenia tworzenia obiektu, aby sprawdzić, czy jest\<to typ> NiezmiennegoArray T. Ponownie użyj modelu semantycznego, aby uzyskać informacje o symbolu typu (ImmutableArray) w wyrażeniu tworzenia obiektu. Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Ponieważ analizator musi obsługiwać niekompletny lub niepoprawny kod w buforach edytora (na przykład brakuje `using` instrukcji), należy sprawdzić, `symbolInfo` czy jest `null`. Aby zakończyć analizę, należy uzyskać nazwany typ (INamedTypeSymbol) z obiektu informacji o symbolu.

**Porównaj typy.** Ponieważ istnieje otwarty typ ogólny T, którego szukamy, a typ w kodzie jest konkretnym typem ogólnym, należy zbadać informacje o symbolu, `immutableArrayOfTType`z którego typ jest skonstruowany (otwarty typ ogólny) i porównać ten wynik z programem . Na końcu metody należy wprowadzić następujące elementy:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Zgłoś diagnostykę.** Raportowanie diagnostyki jest dość łatwe. Reguła utworzona dla ciebie w szablonie projektu, która jest zdefiniowana przed inicjuj metody. Ponieważ ta sytuacja w kodzie jest błędem, można zmienić `DiagnosticSeverity.Warning` wiersz, który zainicjował regułę, aby zastąpić (zielony squiggle) z `DiagnosticSeverity.Error` (czerwony squiggle). Pozostała część reguły inicjuje z zasobów edytowanych na początku instruktażu. Należy również zgłosić lokalizację squiggle, która jest lokalizacją specyfikacji typu wyrażenia tworzenia obiektu. Wprowadź ten kod `if` w bloku:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Twoja funkcja powinna wyglądać tak (być może sformatowana inaczej):

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

Usuń punkt przerwania, dzięki czemu można wyświetlić analizatora pracy (i zatrzymać powrót do pierwszego wystąpienia programu Visual Studio). Przeciągnij wskaźnik wykonania na początek metody i naciśnij **klawisz F5,** aby kontynuować wykonywanie. Po przełączeniu z powrotem do drugiego wystąpienia programu Visual Studio kompilator rozpocznie badanie kodu ponownie i wywoła do analizatora. Możesz zobaczyć squiggle `ImmutableType<int>`pod .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Dodawanie "Poprawki kodu" dla problemu z kodem

Przed rozpoczęciem zamknij drugie wystąpienie programu Visual Studio i zatrzymaj debugowanie w pierwszej instancji programu Visual Studio (w którym tworzysz analizator).

**Dodaj nową klasę.** Użyj menu skrótów (prawy przycisk wskaźnika) w węźle projektu w **Eksploratorze rozwiązań** i wybierz opcję dodania nowego elementu. Dodaj klasę `BuildCodeFixProvider`o nazwie . Ta klasa musi pochodzić `CodeFixProvider`od , i trzeba będzie użyć **Ctrl**+**.** (okres), aby wywołać poprawkę kodu, `using` która dodaje poprawną instrukcję. Ta klasa również musi być `ExportCodeFixProvider` adnotacjami z atrybutem `using` i należy `LanguageNames` dodać instrukcję, aby rozwiązać wyliczenia. Powinien mieć plik klasy z następującym kodem:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Wycinek od elementów pochodnych.** Teraz umieść opiekunę `CodeFixProvider` redaktora w identyfikatorze i naciśnij klawisz **Ctrl**+**.** (okres), aby wycinek implementacji dla tej abstrakcyjnej klasy podstawowej. To generuje właściwość i metodę dla Ciebie.

**Zaimplementuj właściwość.** Wypełnij `FixableDiagnosticIds` `get` treść obiektu następującym kodem:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn łączy diagnostykę i poprawki, dopasowując te identyfikatory, które są tylko ciągami. Szablon projektu wygenerował identyfikator diagnostyczny dla Ciebie i możesz go zmienić. Kod we właściwości po prostu zwraca identyfikator z klasy analizatora.

**RegisterCodeFixAsync Metoda przyjmuje kontekst.** Kontekst jest ważne, ponieważ poprawka kodu można zastosować do wielu diagnostyki lub może być więcej niż jeden problem w wierszu kodu. Jeśli wpiszesz "kontekst". w treści metody, lista ukończenia IntelliSense pokaże kilka przydatnych członków. Istnieje cancelToken członka, który można sprawdzić, czy coś chce anulować poprawkę. Istnieje element członkowski dokumentu, który ma wiele przydatnych elementów członkowskich i umożliwia przejście do obiektów modelu projektu i rozwiązania. Istnieje Span element członkowski, który jest początek i koniec lokalizacji kodu określone podczas zgłaszania diagnostyki.

**Sprawiają, że metoda być asynchroniczne.** Pierwszą rzeczą, którą musisz zrobić, to naprawić `async` deklarację wygenerowanej metody jako metodę. Poprawka kodu dla stubbing się implementacji klasy abstrakcyjnej `async` nie zawiera słowa `Task`kluczowego, mimo że metoda zwraca .

**Pobierz katalog główny drzewa składni.** Aby zmodyfikować kod, należy utworzyć nowe drzewo składni ze zmianami, które wprowadza poprawka kodu. Potrzebujesz z `Document` kontekstu, `GetSyntaxRootAsync`aby wywołać . Jest to metoda asynchroniowa, ponieważ istnieje nieznana praca, aby uzyskać drzewo składni, ewentualnie w tym uzyskanie pliku z dysku, analizowanie go i tworzenie modelu kodu Roslyn dla niego. Interfejs użytkownika programu Visual Studio powinien być `async` responsywny w tym czasie, który przy użyciu włącza. Zastąp wiersz kodu w metodzie na następujące:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Znajdź węzeł z problemem.** Przekazać w zakresie kontekstu, ale węzeł, który można znaleźć może nie być kod, który należy zmienić. Zgłoszona diagnostyka tylko pod warunkiem, że zakres dla identyfikatora typu (gdzie squiggle należał), `new` ale należy zastąpić całe wyrażenie tworzenia obiektu, w tym słowa kluczowego na początku i nawiasy na końcu. Dodaj następujący kod do swojej metody (i użyj **ctrl**+**.** , aby `using` dodać `ObjectCreationExpressionSyntax`instrukcję dla):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Zarejestruj poprawkę kodu dla interfejsu żarówki.** Po zarejestrowaniu poprawki kodu Roslyn automatycznie podłącza się do interfejsu żarówki programu Visual Studio. Użytkownicy końcowi zobaczą, że mogą korzystać z **ctrl**+**.** (okres), gdy analizator squiggles `ImmutableArray<T>` złe użycie konstruktora. Ponieważ dostawca poprawki kodu jest wykonywany tylko wtedy, gdy występuje problem, można założyć, że masz wyrażenie tworzenia obiektu, którego szukasz. Z parametru kontekstu można zarejestrować nową poprawkę kodu, dodając `RegisterCodeFixAsync` następujący kod na końcu metody:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Należy umieścić opiekunę redaktora w identyfikatorze, `CodeAction`a następnie użyć **klawisza Ctrl**+**.** (okres), aby dodać `using` odpowiednie oświadczenie dla tego typu.

Następnie umieść opiekunę redaktora `ChangeToImmutableArrayEmpty` w identyfikatorze i użyj **klawisza Ctrl**+**.** ponownie, aby wygenerować tę metodę.

Ten ostatni fragment kodu, który został dodany rejestruje `CodeAction` poprawkę kodu, przekazując identyfikator diagnostyczny i identyfikator diagnostyczny dla rodzaju znalezionego problemu. W tym przykładzie istnieje tylko jeden identyfikator diagnostyczny, który ten kod zawiera poprawki, dzięki czemu można po prostu przekazać pierwszy element tablicy identyfikatorów diagnostycznych. Podczas tworzenia `CodeAction`programu , należy przekazać w tekście, który żarówki interfejsu użytkownika należy użyć jako opis poprawki kodu. Należy również przekazać w funkcji, która przyjmuje CancellationToken i zwraca nowy dokument. Nowy dokument zawiera nowe drzewo składni, które zawiera `ImmutableArray.Empty`poprawiony kod, który wywołuje . Ten fragment kodu używa lambda, dzięki czemu można zamknąć za pomocą węzła objectCreation i dokumentu kontekstu.

**Skonstruuj nowe drzewo składni.** W `ChangeToImmutableArrayEmpty` metodzie, której skrót został wygenerowany `ImmutableArray<int>.Empty;`wcześniej, wprowadź wiersz kodu: . Jeśli ponownie wyświetlisz okno narzędzia **Wizualizator składni,** zobaczysz, że ta składnia jest węzłem SimpleMemberAccessExpression. To, co ta metoda musi skonstruować i zwrócić w nowym dokumencie.

Pierwszą zmianą `ChangeToImmutableArrayEmpty` jest `async` `Task<Document>` dodanie wcześniej, ponieważ generatory kodu nie można przyjąć, że metoda powinna być async.

Wypełnij treść następującym kodem, aby metoda wyglądała podobnie do następującej:

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

Trzeba będzie umieścić dasznik edytora `SyntaxGenerator` w identyfikatorze i użyć **Ctrl**+**.** (okres), aby dodać `using` odpowiednie oświadczenie dla tego typu.

Ten kod `SyntaxGenerator`używa , który jest przydatnym typem do konstruowania nowego kodu. Po uzyskaniu generatora dla dokumentu, który `ChangeToImmutableArrayEmpty` `MemberAccessExpression`ma problem z kodem, wywołuje , przekazując typ, który ma element członkowski, który chcemy uzyskać dostęp i przekazywanie nazwy elementu członkowskiego jako ciąg.

Następnie metoda pobiera katalog główny dokumentu, a ponieważ może to obejmować dowolną pracę w ogólnym przypadku, kod oczekuje na to wywołanie i przekazuje token anulowania. Modele kodu Roslyn są niezmienne, takie jak praca z ciągiem .NET; po zaktualizowaniu ciągu, otrzymasz nowy obiekt ciągu w zamian. Po wywołaniu `ReplaceNode`, można odzyskać nowy węzeł główny. Większość drzewa składni jest współużytkowana (ponieważ jest `objectCreation` niezmienna), `memberAccess` ale węzeł jest zastępowany węzłem, a także wszystkimi węzłami nadrzędnymi do katalogu głównego drzewa składni.

## <a name="try-your-code-fix"></a>Wypróbuj poprawkę kodu

Teraz można nacisnąć **klawisz F5,** aby wykonać analizator w drugim wystąpieniu programu Visual Studio. Otwórz projekt konsoli, który był wcześniej używany. Teraz powinieneś zobaczyć żarówkę pojawiają się, `ImmutableArray<int>`gdzie nowe wyrażenie tworzenia obiektu jest dla . Po naciśnięciu **klawisza Ctrl**+**.** (kropka), wtedy zobaczysz poprawkę kodu, a zobaczysz automatycznie wygenerowany podgląd różnicy kodu w interfejsie użytkownika żarówki. Roslyn tworzy to dla Ciebie.

**Porada pro:** Jeśli uruchomisz drugie wystąpienie programu Visual Studio i nie zobaczysz żarówki z poprawką kodu, może być konieczne wyczyszczenie pamięci podręcznej składnika programu Visual Studio. Wyczyszczenie pamięci podręcznej wymusza visual studio do ponownego zbadania składników, więc Visual Studio należy następnie odebrać najnowszy składnik. Najpierw zamknij drugie wystąpienie programu Visual Studio. Następnie w **Eksploratorze Windows**przejdź do *pozycji %LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn\\*. ("16.0" zmienia się z wersji na wersję z programem Visual Studio.) Usuń podkatalog *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Dyskusja wideo i zakończyć projekt kodu

Możesz zobaczyć ten przykład opracowany i omówione dalej w [tej rozmowie](https://channel9.msdn.com/events/Build/2015/3-725). Rozmowa pokazuje analizator pracy i prowadzi cię przez budowanie go.

Możesz zobaczyć cały gotowy kod [tutaj](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Podfolderów *DoNotUseImmutableArrayCollectionInitializer* i *DoNotUseImmutableArrayCtor* każdy ma plik C# do znajdowania problemów i plik C#, który implementuje poprawki kodu, które pojawiają się w ui żarówki programu Visual Studio. Uwaga: gotowy kod ma trochę więcej abstrakcji, aby uniknąć\<pobierania ImmutableArray T> typu obiektu w kółko. Używa zagnieżdżonych zarejestrowanych akcji do zapisania obiektu typu w kontekście, który jest dostępny za każdym razem, gdy wykonywane są akcje podrzędne (analizowanie tworzenia obiektów i analizowanie inicjacji kolekcji).

## <a name="see-also"></a>Zobacz też

* [\\\Dyskusja Kompilacja 2015](https://channel9.msdn.com/events/Build/2015/3-725)
* [Ukończony kod w gitHubie](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Kilka przykładów na GitHub, pogrupowane w trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Inne dokumenty w witrynie gitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Reguły FxCop zaimplementowane za pomocą analizatorów Roslyn na GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
