---
title: Analizatory Roslyn i Biblioteka obsługująca kod dla tablic Immutablearray | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2af6141ae3b7a61805b2515f11f72f164389949
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821386"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizatory Roslyn i Biblioteka obsługująca kod dla tablic Immutablearray

[Platformie kompilatora .NET](https://github.com/dotnet/roslyn) ("Roslyn") pomaga w tworzeniu bibliotek kodu aware. Biblioteka obsługująca kod zawiera funkcje, których można użyć i narzędzi (analizatorów Roslyn), aby ułatwić korzystanie z biblioteki w najlepszy sposób, lub aby uniknąć błędów. W tym temacie dowiesz się, jak tworzyć Roslyn rzeczywistych analizator catch typowych błędów, korzystając z [System.Collections.Immutable](https://www.nuget.org/packages/System.Collections.Immutable) pakietu NuGet. W przykładzie pokazano również sposób udostępniania poprawki kodu dla kodu problemu wykrytego przez analizator. Użytkownicy widzą poprawki kodu w Visual Studio żarówki interfejsu użytkownika i automatycznie stosować poprawki dla kodu.

## <a name="get-started"></a>Wprowadzenie

Potrzebne są następujące polecenie, aby skompilować ten przykład:

* Visual Studio 2015 (nie Express Edition) lub nowszej wersji. Można korzystać z BEZPŁATNEJ [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Możesz również podczas instalowania programu Visual Studio, sprawdzić **Visual Studio Extensibility Tools** w obszarze **popularnych narzędzi do** zainstalować zestaw SDK, w tym samym czasie. Jeśli zainstalowano już program Visual Studio, możesz także zainstalować zestaw SDK, przechodząc do menu głównego **pliku** > **New** > **projektu**, Wybieranie **C#** w okienku nawigacji po lewej stronie, a następnie wybierając **rozszerzalności**. Po wybraniu "**instalacji programu Visual Studio Extensibility Tools**" łączy do stron nadrzędnych szablonu projektu, monituje o pobranie i zainstalowanie zestawu SDK.
* [Platforma kompilatora .NET ("Roslyn") zestawu SDK](http://aka.ms/roslynsdktemplates). Można także zainstalować zestaw SDK, przechodząc do menu głównego **pliku** > **New** > **projektu**, wybierając **C#** w okienku nawigacji po lewej stronie, a następnie wybierając **rozszerzalności**. Po wybraniu "**Pobierz zestaw SDK platformy kompilatora .NET**" łączy do stron nadrzędnych szablonu projektu, monituje o pobranie i zainstalowanie zestawu SDK. Ten zestaw SDK zawiera [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Ułatwia to przydatne narzędzie zorientować się, jakie typy modelu kodu należy szukać w analizatorze usługi. Połączenia infrastruktury analizator kodu dla typów modelu konkretnego kodu, dzięki czemu kod tylko wykonuje, gdy jest to konieczne i skoncentrować się tylko na analizowanie odpowiedni kod.

## <a name="whats-the-problem"></a>Na czym polega problem?

Wyobraź sobie, możesz zapewnić bibliotekę element ImmutableArray (na przykład <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) pomocy technicznej. Deweloperzy języka C# mają doświadczenia z tablic platformy .NET. Jednak ze względu na charakter technik tablic Immutablearray i optymalizacji używany w implementacji intuitions dla deweloperów języka C#, że użytkownicy biblioteki do pisania kodu w uszkodzona jak wyjaśniono poniżej. Ponadto użytkownicy nie widzą ich błędy czasu wykonywania, nie jest środowisko jakości, które są używane do programu Visual Studio przy użyciu platformy .NET.

Użytkownicy zapoznali się z pisania kodu, jak pokazano poniżej:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Tworzenie pustego tablic do wypełnienia za pomocą kolejnych wierszy kodu i przy użyciu składni inicjatora kolekcji są znane C# deweloperów. Jednak kod element ImmutableArray pisania takie same ulega awarii w czasie wykonywania:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Pierwszy błąd wynika z implementacji element ImmutableArray przy użyciu struktury do opakowania podstawowego magazynu danych. Struktury muszą mieć konstruktory bez parametrów, aby `default(T)` wyrażeń może zwrócić struktury, ze wszystkimi zero lub elementów członkowskich o wartości null. Gdy kod uzyskuje dostęp do `b1.Length`, ma wartość null w czasie wykonywania wyłuskania błąd, ponieważ nie istnieje żadna bazowego macierz magazynowa w strukturze element ImmutableArray. Jest prawidłowym sposobem, aby utworzyć pusty element ImmutableArray `ImmutableArray<int>.Empty`.

Błąd za pomocą inicjatory kolekcji wynika `ImmutableArray.Add` metoda zwraca nowe wystąpienia każdorazowo, należy wywołać. Ponieważ tablic Immutablearray nigdy nie ulegną zmianie, po dodaniu nowego elementu, można odzyskać nowy obiekt element ImmutableArray, (które mogą udostępniać magazynu ze względu na wydajność wcześniej istniejący element ImmutableArray). Ponieważ `b2` wskazuje na pierwszy element ImmutableArray przed wywołaniem `Add()` pięć razy `b2` jest domyślny element ImmutableArray. Podczas wywoływania długości w nim również awarie z wartością null wyłuskania błąd. Prawidłowy sposób, aby zainicjować element ImmutableArray bez wywoływania ręcznie dodaj to użycie `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Znajdź typy węzłów do wyzwolenia usługi analizatora składni odpowiednie

 Aby rozpocząć tworzenie analizatora, najpierw zorientować się, jakiego rodzaju SyntaxNode należy do wyszukania. Uruchom **Syntax Visualizer** z menu **widoku** > **Windows inne** > **Roslyn Syntax Visualizer**.

Umieść karetka edytora w wierszu, który deklaruje `b1`. Zobaczysz Syntax Visualizer zawiera znajdują się w `LocalDeclarationStatement` węzła drzewa składni. Ten węzeł zawiera `VariableDeclaration`, który z kolei ma `VariableDeclarator`, który z kolei ma `EqualsValueClause`, a na koniec istnieje `ObjectCreationExpression`. Kliknij w drzewie Syntax Visualizer węzłów składni w oknie Edytor wyróżnia się Wam kod reprezentowany przez ten węzeł. Nazwy typów sub SyntaxNode dopasowania nazw używanych w gramatyki języka C#.

## <a name="create-the-analyzer-project"></a>Utwórz projekt analizatora

W menu głównym wybierz **pliku** > **New** > **projektu**. W **nowy projekt** okna dialogowego, w obszarze **C#** projekty na pasku nawigacyjnym po lewej stronie wybierz **rozszerzalności**, a w okienku po prawej stronie wybierz **Analyzer z Poprawka kodu** szablonu projektu. Wprowadź nazwę i upewnij się, okno dialogowe.

Szablon zostanie otwarty *DiagnosticAnalyzer.cs* pliku. Wybierz tego edytora kartę buforu. Ten plik zawiera klasę analyzer (sformułowany niż nazwa nadana projektu) który pochodzi od klasy `DiagnosticAnalyzer` (typ interfejsu API Roslyn). Nowej klasie ma `DiagnosticAnalyzerAttribute` deklarowanie analizatora użytkownika dotyczy języka C#, aby kompilator wykrywa i ładuje Twoje analizatora.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

Możesz zaimplementować analizator w języku Visual Basic, który jest przeznaczony dla kodu C# i na odwrót. Jest to niezwykle ważne w DiagnosticAnalyzerAttribute, aby wybrać, czy Twoje Analizator jest przeznaczony dla jednego języka lub obu. Analizatory bardziej zaawansowanych, wymagających szczegółowe modelowania języka, można kierować tylko jeden język. Twoje analizatora, na przykład sprawdza tylko nazwy typu lub członka publicznego, może być możliwe użycie wspólnego modelu języka oferowanych na platformie Roslyn w Visual Basic i C#. Na przykład programu FxCop ostrzega, że klasa implementuje <xref:System.Runtime.Serialization.ISerializable>, ale nie ma klasy <xref:System.SerializableAttribute> atrybut jest niezależny od języka i działa dla kodu Visual Basic i C#.

## <a name="initialize-the-analyzer"></a>Inicjowanie analizatora

 Przewiń w dół nieco w `DiagnosticAnalyzer` klasy, aby zobaczyć `Initialize` metody. Kompilator wywołuje tę metodę, gdy aktywacja analizatora. Ta metoda przyjmuje `AnalysisContext` obiekt, który umożliwia Twojej analizatora, uzyskać informacje o kontekście i rejestrowanie wywołań zwrotnych dla zdarzeń dla rodzaje kodu, które mają być analizowane.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Otwórz nowy wiersz w tej metody i typu "kontekstu." Aby zobaczyć listy uzupełniania IntelliSense. Widoczne na liście uzupełniania jest wiele `Register...` metod do obsługi różnych typów zdarzeń. Na przykład, pierwszy z nich, `RegisterCodeBlockAction`, wywołania z powrotem do kodu w bloku, który zazwyczaj znajduje się kod między nawiasy klamrowe. Rejestrowanie w bloku również ponownie wywołuje kodu dla inicjatora pola, wartość atrybutu lub wartość parametru opcjonalnego.

Inny przykład `RegisterCompilationStartAction`, wywołania z powrotem do kodu na początku kompilacji, co jest przydatne w przypadku konieczności gromadzenia stanów w wielu lokalizacjach. Można utworzyć struktury danych, powiedz, aby zbierać wszystkie symbole używane, i każdym razem, gdy Twoje Analizator jest wywołanie zwrotne dla niektórych składni lub symbol, można zapisać informacji o każdej lokalizacji w strukturze danych. Kiedy jest ponownie wywoływana ze względu na zakończenie kompilacji, można analizować wszystkie lokalizacje, które zostały zapisane, na przykład do zgłaszania jakie symbole w kodzie za pomocą każdego z nich `using` instrukcji.

Za pomocą **Syntax Visualizer**, wiesz, że chcesz wywoływana, gdy kompilator przetwarza ObjectCreationExpression. Aby zdefiniować wywołanie zwrotne należy użyć następującego kodu:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Możesz zarejestrować węzeł składni i filtrowania tylko tworzenia składni węzły obiektów. Zgodnie z Konwencją autorzy analizatora użyć wyrażenia lambda, podczas rejestrowania akcji, które pomaga w zabezpieczeniu analizatory bezstanowe. Funkcja Visual Studio **Generowanie z użycia** utworzyć `AnalyzeObjectCreation` metody. Spowoduje to wygenerowanie poprawnego typu parametru kontekstowego dla Ciebie zbyt.

## <a name="set-properties-for-users-of-your-analyzer"></a>Ustaw właściwości dla użytkowników usługi analizatora

Tak, aby Twoje analizatora zostaną wyświetlone w interfejsie użytkownika Visual Studio odpowiednio, poszukaj i zmodyfikuj następujący wiersz kodu w celu identyfikowania sieci analizatora:

```csharp
internal const string Category = "Naming";
```

Zmiana `"Naming"` do `"API Guidance"`.

Następnie znajdź i Otwórz *Resources.resx* pliku w projekcie za pomocą **Eksploratora rozwiązań**. Możesz umieścić w opisie usługi analizatora, tytuł, itp. Możesz zmienić wartość dla wszystkich tych zasobów w celu `"Don't use ImmutableArray<T> constructor"` teraz. Możesz umieścić ciąg formatowania argumentów w ciągu ({0}, {1}, itp.) i później, po wywołaniu `Diagnostic.Create()`, możesz podać `params` tablica argumentów do przekazania.

## <a name="analyze-an-object-creation-expression"></a>Analizowanie wyrażenie tworzenia obiektu

`AnalyzeObjectCreation` Metoda przyjmuje innego typu kontekstu dostarczone przez platformę, analizator kodu. `Initialize` Metody `AnalysisContext` umożliwia rejestrowanie akcji wywołań zwrotnych, aby skonfigurować swoje analizatora. `SyntaxNodeAnalysisContext`, Na przykład `CancellationToken` , którą można przekazać wokół. Jeśli użytkownik uruchamia, wpisując w edytorze, Roslyn spowoduje anulowanie uruchomionych analizatorów, aby zapisać pracę i zwiększyć wydajność. Inny przykład ten kontekst ma właściwość węzła, która zwraca węzeł składni tworzenia obiektu.

Pobierz węzła, który można założyć, jest to typ, dla którego jest filtrowana Akcja węzła składni:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Uruchom program Visual Studio za pomocą analizatora sieci po raz pierwszy

Uruchom program Visual Studio, tworząc i wykonywanie Twojego analyzer (naciśnij klawisz **F5**). Ponieważ uruchamianie projektu w **Eksploratora rozwiązań** jest projektu VSIX, systemem kompilacji kodu, Twój kod i VSIX, a następnie uruchamia program Visual Studio z tym VSIX zainstalowane. Po uruchomieniu programu Visual Studio w ten sposób uruchomi z gałęzi rejestru unikatowych tak, aby główny korzystanie z programu Visual Studio nie dotyczy wystąpień testowania podczas kompilowania analizatory. Przy pierwszym uruchomieniu w ten sposób kilka inicjalizacje, podobnie jak podczas pierwszych uruchomiono program Visual Studio po zainstalowaniu program Visual Studio.

Utwórz projekt konsoli, a następnie wprowadź kod tablicy do Twojej metody Main aplikacji konsoli:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Wiersze kodu za pomocą `ImmutableArray` mają faliste linie, ponieważ trzeba uzyskać niemodyfikowalny pakiet NuGet i Dodaj `using` instrukcji w kodzie. Naciśnij przycisk prawo wskaźnika na węzeł projektu w **Eksploratora rozwiązań** i wybierz polecenie **Zarządzaj pakietami NuGet**. W Menedżerze NuGet wpisz "Klasa Immutable" w polu wyszukiwania, a następnie wybierz element **System.Collections.Immutable** (nie należy wybierać **Microsoft.Bcl.Immutable**) w okienku po lewej stronie i naciśnij klawisz  **Zainstaluj** przycisku w okienku po prawej stronie. Instalowanie pakietu dodaje odwołania do odwołań projektu.

Nadal pojawi się czerwone faliste linie w obszarze `ImmutableArray`, więc umieść karetkę w tym identyfikator i naciśnij klawisz **Ctrl**+**.** (okres), aby wyświetlić menu sugerowanej poprawki i dodasz odpowiednie `using` instrukcji.

**Zapisz wszystko i Zamknij** drugiego wystąpienia programu Visual Studio teraz, aby spowodować straty stanu czystego, aby kontynuować.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Zakończ analizatora, używanie funkcji Edytuj i Kontynuuj

W pierwszym wystąpieniu programu Visual Studio, należy ustawić punkt przerwania na początku swoje `AnalyzeObjectCreation` metody, naciskając klawisz **F9** z daszek w pierwszym wierszu.

Uruchamianie usługi analizatora ponownie, używając **F5**, a w drugim wystąpieniu programu Visual Studio, otwórz ponownie aplikację konsoli utworzona czas ostatniego.

Następuje powrót do pierwszego wystąpienia programu Visual Studio w punkcie przerwania, ponieważ kompilator Roslyn dostrzegła wyrażenie tworzenia obiektu, a o nazwie do analizatora sieci.

**Pobierz węzeł tworzenia obiektu.** Przekrocz nad wierszu, który ustawia `objectCreation` zmiennej, naciskając klawisz **F10**, a następnie w **bezpośrednim** obliczenia wyrażenia `"objectCreation.ToString()"`. Możesz sprawdzić, czy węzeł składni wskazuje zmienną kod `"new ImmutableArray<int>()"`, po prostu czego szukasz.

**Pobierz element ImmutableArray < T\> typu obiektu.** Należy sprawdzić, czy typ tworzony jest element ImmutableArray. Najpierw pobierz jest obiekt, który reprezentuje tego typu. Sprawdzanie typów przy użyciu semantycznego modelu analizy biznesowej, aby upewnić się, masz właściwego typu, a nie porównywania ciągów z `ToString()`. Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Należy wyznaczyć typów ogólnych w metadanych w znaki grawisu (') i liczby parametrów ogólnych. Dlatego nie widzisz "menu... Element ImmutableArray\<T > "w nazwie metadanych.

Model semantyczny znajdują się różne przydatne, dzięki którym możesz zadawać pytania dotyczące symboli, przepływ danych, okres istnienia zmiennych itd. Roslyn oddziela składni węzłów z modelu semantycznego z różnych powodów engineering (wydajności, modelowania błędnego kodu itp.). Chcesz, aby model kompilacji, aby wyszukać informacje zawarte w odwołaniach do dokładnego porównywania.

Można przeciągnąć wskaźnik wykonania żółty po lewej stronie okna edytora. Przeciągnij go do wiersza, który ustawia `objectCreation` zmienną i Przekrocz nowego wiersza kodu za pomocą **F10**. Jeśli umieszczeniu wskaźnika myszy na zmiennej `immutableArrayOfType`, zobaczysz, że możemy znaleźć dokładnie tego samego typu w modelu semantycznego.

**Pobranie typu wyrażenie tworzenia obiektu.** "Type" jest używany na kilka sposobów, w tym artykule, ale oznacza to, czy masz "nowe Foo" wyrażenie, musisz pobrać model Foo. Należy uzyskać typ wyrażenie tworzenia obiektu, aby sprawdzić, czy jest element ImmutableArray\<T > typu. Ponownie użyć semantycznego modelu analizy biznesowej, aby uzyskać informacje o symbolach dla typu symbolu (element ImmutableArray) w wyrażeniu tworzenia obiektów. Wprowadź następujący wiersz kodu na końcu funkcji:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Ponieważ Twoje analizator musi obsługiwać niepełną lub nieprawidłową kodu w edytorze buforów (na przykład, jest Brak `using` instrukcji), należy sprawdzić, `symbolInfo` trwa `null`. Należy uzyskać typ nazwany (INamedTypeSymbol) z obiektu informacji o symbolu na zakończenie analizy.

**Porównanie typów.** Ponieważ jest to otwarty typ ogólny, t, które firma Microsoft szuka, a typ w kodzie jest konkretny typ ogólny, kwerendy informacji o symbolach, dla jakiego typu jest zbudowany z (to otwarty typ ogólny) i porównać wynik z `immutableArrayOfTType`. Wprowadź na końcu metody następujących:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Należy sporządzić raport diagnostyczne.** Raportowanie diagnostyczne jest całkiem proste. Używasz reguły utworzone w szablonie projektu, która jest zdefiniowana przed metoda inicjowania. Ponieważ ta sytuacja, w kodzie występuje błąd, możesz zmienić wiersza, który zainicjowany zasadę, aby zastąpić `DiagnosticSeverity.Warning` (zielony wężyk) przy użyciu `DiagnosticSeverity.Error` (czerwona fala). Inicjuje reszty regułę z zasoby, które można edytować na początku tego przewodnika. Należy również zgłosić lokalizację wężyk, która jest lokalizacją specyfikacji typu wyrażenie tworzenia obiektu. Wprowadź ten kod w `if` bloku:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

Funkcja powinna wyglądać następująco (może być sformatowane inaczej):

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

Usuń punkt przerwania, dzięki czemu mogą zobaczyć pracy analizator (i zatrzymać, wracając do pierwszego wystąpienia programu Visual Studio). Przeciągnij wskaźnik wykonania na początku metody i naciśnij klawisz **F5** do kontynuowania wykonywania. Po przełączeniu się do drugiego wystąpienia programu Visual Studio, kompilator rozpocznie się ponownie sprawdzić kod i będą wywoływać usługi analizatora. Możesz zobaczyć wężyk w obszarze `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Dodawanie "Poprawki kodu" dotyczącej problemu z kodu

Przed przystąpieniem do wykonywania, zamknij drugie wystąpienie programu Visual Studio i zatrzymywanie debugowania w pierwszego wystąpienia programu Visual Studio (na którym jest tworzona analizatora).

**Dodaj nową klasę.** Użyj menu skrótów (wskaźnik myszy w prawy przycisk) na węzeł projektu w **Eksploratora rozwiązań** i wybierz opcję Dodaj nowy element. Dodaj klasę o nazwie `BuildCodeFixProvider`. Ta klasa musi pochodzić od `CodeFixProvider`, i będą musieli używać **Ctrl**+**.** (okres), aby wywołać poprawki kodu, który dodaje poprawny `using` instrukcji. Ta klasa musi również być oznaczona przy użyciu `ExportCodeFixProvider` atrybutu i konieczne będzie dodanie `using` instrukcję, aby rozwiązać `LanguageNames` wyliczenia. Musisz mieć plik klasy w nim następującym kodem:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Klasy zastępczej się pochodzić elementy członkowskie.** Teraz umieść karetka edytora w identyfikatorze `CodeFixProvider` i naciśnij klawisz **Ctrl**+**.** (okres), aby zastąpić klasą zastępczą out to implementacja to abstrakcyjna klasa bazowa. Spowoduje to wygenerowanie właściwości i metody dla Ciebie.

**Implementuje właściwość.** Wypełnij `FixableDiagnosticIds` właściwości `get` treść następującym kodem:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn łączy diagnostyki i poprawki, dopasowując te identyfikatory, które są tylko ciągi. Szablon projektu automatycznie wygenerowanego Identyfikatora diagnostycznego i mogą je zmienić. Kodu we właściwości po prostu zwraca identyfikator po klasie analizatora.

**Metoda RegisterCodeFixAsync pobierającej kontekst.** Kontekst jest ważne, ponieważ poprawki kodu można zastosować do wielu diagnostyki lub może być problem z więcej niż jeden na wiersz kodu. Jeśli wpiszesz "kontekst". w treści metody na liście uzupełniania IntelliSense opisano niektóre przydatne elementy członkowskie. Istnieje element członkowski token anulowania, który można sprawdzić, aby zobaczyć, jeśli coś, co chce, aby anulować poprawki. Istnieje element członkowski dokumentu, który ma wiele elementów członkowskich przydatne i pozwala uzyskać dostęp do obiekty modelu projektu i rozwiązania. Brak zakresu członka, który jest początek i koniec lokalizacji kodu określić, kiedy są zgłaszane diagnostyczne.

**Utwórz metodę być asynchroniczny.** Pierwszą rzeczą, którą należy wykonać to naprawić deklaracji wygenerowana metoda jako `async` metody. Nie obejmuje poprawki kodu dla zastępowanie klasami zastępczymi się implementacją klasy abstrakcyjnej `async` — słowo kluczowe nawet wtedy, gdy metoda ta zwraca `Task`.

**Uzyskaj katalogu głównego drzewa składni.** Aby zmodyfikować kod, musisz utworzyć nowe drzewo składni ze zmianami poprawkę kodu sprawia, że. Potrzebujesz `Document` z kontekstu do wywołania `GetSyntaxRootAsync`. Jest to metoda asynchroniczna, ponieważ ma nieznany pracy w celu drzewo składni, prawdopodobnie w tym pobierania pliku z dysku, jego analizowanie i budowanie modelu kodu platformy Roslyn dla niego. Interfejsie użytkownika programu Visual Studio powinien odpowiadać w tym czasie, które przy użyciu `async` umożliwia. Zastąp wiersz kodu w metodzie następujących czynności:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Znajdź węzeł o problem.** Są przekazywane w kontekście zakresu, ale węzeł, w którym możesz znaleźć, może nie być kod, który trzeba wprowadzać zmian. Zgłoszona Diagnostyka tylko podać zakres identyfikatora typu (gdzie wężyk należały), ale musisz zastąpić wyrażenie tworzenia cały obiekt, w tym `new` — słowo kluczowe na początku i nawiasy na końcu. Dodaj następujący kod do metody (i użyj **Ctrl**+**.** Aby dodać `using` poufności informacji dotyczące `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Zarejestruj swoje poprawki kodu dla żarówki interfejsu użytkownika.** Podczas rejestrowania poprawkę kodu Roslyn podłącza się do programu Visual Studio żarówki interfejsu użytkownika automatycznie. Użytkownicy końcowi będą widzieli, mogą używać **Ctrl**+**.** (kropka), gdy Twoje analizatora squiggles zły `ImmutableArray<T>` Użyj konstruktora. Ponieważ dostawcą poprawki kodu jest wykonywana tylko wtedy, gdy występuje problem, można założyć, że masz wyrażenie tworzenia obiektu, którego szukasz. Z parametru kontekstowego można zarejestrować nowe poprawki kodu, dodając następujący kod na końcu `RegisterCodeFixAsync` metody:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

Należy umieścić karetka edytora w identyfikatorze, `CodeAction`, następnie za pomocą **Ctrl**+**.** (okres), aby dodać odpowiednią `using` instrukcji dla tego typu.

Następnie umieść karetkę edytora w `ChangeToImmutableArrayEmpty` identyfikator i użyj **Ctrl**+**.** ponownie, aby wygenerować ten szkieletu metody dla Ciebie.

Ten ostatni fragment kodu, który został dodany rejestruje poprawki kodu przez przekazanie `CodeAction` i Identyfikator diagnostyczny dla rodzaju znalezione problemy. W tym przykładzie istnieje tylko jeden identyfikator diagnostycznych, który zawiera ten kod poprawki, dzięki czemu można po prostu Przekaż pierwszy element tablicy identyfikatorów diagnostycznych. Po utworzeniu `CodeAction`, są przekazywane w tekst, który żarówki interfejsu użytkownika należy używać jako Opis poprawki kodu. Możesz też przekazać funkcję, która przyjmuje CancellationToken i zwraca nowy dokument. Nowy dokument ma nowe drzewo składni, obejmującą kodzie poprawionego, który wywołuje `ImmutableArray.Empty`. Ten fragment kodu użyto wyrażenia lambda, dzięki czemu można zamknąć za pośrednictwem węzła objectCreation i kontekstu dokumentu.

**Konstruować nowego drzewa składni.** W `ChangeToImmutableArrayEmpty` metody, których wycinka wcześniej wygenerowany wprowadź wiersz kodu: `ImmutableArray<int>.Empty;`. Jeśli wyświetlisz **Syntax Visualizer** okna narzędzi, możesz zobaczyć tej składni jest węzłem SimpleMemberAccessExpression. To jest ta metoda wymaga do konstruowania, a następnie wróć do nowego dokumentu.

Zmiany pierwszego `ChangeToImmutableArrayEmpty` jest dodanie `async` przed `Task<Document>` ponieważ generatorów kodu nie można zakładać, metoda powinna być asynchroniczne.

Wprowadź treść następującym kodem, aby wybrać metodę wygląda podobnie do następującego:

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

Konieczne będzie umieszczenie karetka edytora w `SyntaxGenerator` identyfikator i użyj **Ctrl**+**.** (okres), aby dodać odpowiednią `using` instrukcji dla tego typu.

Ten kod używa `SyntaxGenerator`, który jest typem przydatne do tworzenia nowego kodu. Po wprowadzenie generator dla dokumentu, który ma problem z kodem `ChangeToImmutableArrayEmpty` wywołania `MemberAccessExpression`, przekazując typ, który ma chcemy, aby uzyskać dostęp do elementu członkowskiego i przekazanie nazwy elementu członkowskiego jako ciąg.

Następnie metoda pobiera głównego dokumentu, a ponieważ może to obejmować dowolną pracy w przypadku ogólnych, kod czeka na to wywołanie, a następnie przekazuje token anulowania. Modele kodu Roslyn są niezmienne, tak jak w przypadku ciąg .NET. Podczas aktualizacji ciągu uzyskasz nowy obiekt ciągu w zamian. Gdy wywołujesz `ReplaceNode`, wrócić nowego węzła głównego. Większość drzewa składni jest udostępniana (ponieważ jest on niezmienny), ale `objectCreation` węzła jest zastępowany `memberAccess` węzeł, a także wszystkie węzły nadrzędne do katalogu głównego drzewa składni.

## <a name="try-your-code-fix"></a>Spróbuj poprawkę kodu

Teraz można nacisnąć klawisz **F5** do wykonania swojej analizator w drugim wystąpieniu programu Visual Studio. Otwórz projekt konsoli, używane przed. Powinien zostać wyświetlony żarówki, są wyświetlane, gdy nowe wyrażenie tworzenia obiektu dotyczy `ImmutableArray<int>`. Jeśli użytkownik naciśnie klawisz **Ctrl**+**.** (kropka) zostanie wyświetlone naprawić kod. wyświetlony zostanie automatycznie wygenerowany kod różnica (wersja zapoznawcza) w żarówki interfejsu użytkownika. Roslyn tworzy to dla Ciebie.

**Porada Pro:** Jeśli Uruchom drugie wystąpienie programu Visual Studio i nie widzisz żarówki przy użyciu kodu rozwiązanie problemu, a następnie może być konieczne wyczyszczenie pamięci podręcznej składnika programu Visual Studio. Wyczyszczenie pamięci podręcznej wymusza ponownej analizy składników, aby umożliwić programu Visual Studio należy następnie najnowsze składnika programu Visual Studio. Po pierwsze Zamknij drugie wystąpienie programu Visual Studio. Następnie w **Eksplorator Windows**, przejdź do *%LOCALAPPDATA%\Microsoft\VisualStudio\15.0Roslyn\\*. ("15.0" zmienia się od wersji programu Visual Studio). Usuń podkatalogu *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Rozmowy wideo i Zakończ projektu kodu

Widać, w tym przykładzie rozwinięte i omówione w dalszych [tej dyskusji](https://channel9.msdn.com/events/Build/2015/3-725). Rozmowa pokazuje analizatora pracy i przeprowadzi Cię przez tworzenie go.

Gotowy kod jest widoczne [tutaj](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Podfoldery *DoNotUseImmutableArrayCollectionInitializer* i *DoNotUseImmutableArrayCtor* o plik języka C# służące do znajdowania problemów, a plik języka C#, która implementuje kodu przedstawiające rozwiązuje w Visual Studio żarówki interfejsu użytkownika. Uwaga: kod zakończenia ma nieco więcej abstrakcji, aby uniknąć pobierania element ImmutableArray\<T > wpisz obiektów wiele razy. Używa zagnieżdżonych zarejestrowane akcje można zapisać obiektu typu w kontekście, który jest dostępny zawsze, gdy akcji podrzędnej (analizowanie tworzenia obiektów i analizowanie inicjowania kolekcji) wykonywania.

## <a name="see-also"></a>Zobacz także

* [\\Rozmowa \Build 2015](https://channel9.msdn.com/events/Build/2015/3-725)
* [Kompletny kod w serwisie GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Kilka przykładów w witrynie GitHub, pogrupowane według trzy rodzaje analizatorów](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Inne dokumenty w witrynie GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Reguł programu FxCop implementowane za pomocą analizatorów Roslyn w witrynie GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
