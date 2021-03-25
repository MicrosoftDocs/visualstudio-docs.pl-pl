---
title: Użyj kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak używać kontekstowych interfejsów użytkownika opartych na regułach, które umożliwiają autorom rozszerzeń Definiowanie warunków w przypadku aktywowania kontekstu interfejsu użytkownika i ładowania pakietów VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: leslierichardson95
ms.author: lerich
ms.workload:
- vssdk
ms.openlocfilehash: 0ce09edd20c0c46a6b93ace77808fdfc7d5d1c5d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057367"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Instrukcje: używanie kontekstu interfejsu użytkownika opartego na regułach dla rozszerzeń programu Visual Studio

Program Visual Studio umożliwia ładowanie pakietów VSPackage, gdy są aktywowane pewne dobrze znane <xref:Microsoft.VisualStudio.Shell.UIContext> elementy s. Jednak te konteksty interfejsu użytkownika nie są bardziej ziarniste, co pozostawia autorów rozszerzeń bez wyboru, ale do wybierania dostępnego kontekstu interfejsu użytkownika, który jest uaktywniany przed punktem, na który naprawdę chciał pakietu VSPackage. Aby zapoznać się z listą dobrze znanych kontekstów interfejsu użytkownika, zobacz <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

Ładowanie pakietów może mieć wpływ na wydajność i ładowanie ich wcześniej, niż jest to konieczne, nie jest najlepszym rozwiązaniem. W programie Visual Studio 2015 wprowadzono koncepcję kontekstów interfejsu użytkownika opartych na regułach, mechanizm, który umożliwia autorom rozszerzeń Definiowanie precyzyjnych warunków, w których kontekst interfejsu użytkownika jest aktywowany i są ładowane skojarzone pakietów VSPackage.

## <a name="rule-based-ui-context"></a>Kontekst interfejsu użytkownika oparty na regułach

"Reguła" składa się z nowego kontekstu interfejsu użytkownika (GUID) i wyrażenia logicznego, które odwołuje się do co najmniej jednego "pojęcia" połączonego z logicznymi operacjami "i", "lub", "nie". "Warunki" są oceniane dynamicznie w czasie wykonywania, a wyrażenie jest przeszacowana po każdej zmianie jego warunków. Gdy wyrażenie daje w wyniku wartość true, uaktywniany jest skojarzony kontekst interfejsu użytkownika. W przeciwnym razie kontekst interfejsu użytkownika jest dezaktywowany.

Kontekst interfejsu użytkownika oparty na regułach może być używany na różne sposoby:

1. Określ ograniczenia widoczności dla okien poleceń i narzędzi. Okna poleceń/narzędzi można ukryć do momentu spełnienia reguły kontekstu interfejsu użytkownika.

2. Jako ograniczenia automatyczne ładowania: automatyczne ładowanie pakietów tylko po spełnieniu reguły.

3. Jako zadanie opóźnione: Opóźnij ładowanie do określonego interwału, a reguła jest nadal spełniona.

   Mechanizm może być używany przez dowolne rozszerzenie programu Visual Studio.

## <a name="create-a-rule-based-ui-context"></a>Tworzenie kontekstu interfejsu użytkownika opartego na regułach
 Załóżmy, że masz rozszerzenie o nazwie TestPackage, które oferuje polecenie menu, które ma zastosowanie tylko do plików z rozszerzeniem *. config* . Przed programu VS2015 najlepszym rozwiązaniem jest załadowanie TestPackage <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> kontekstu interfejsu użytkownika. Ładowanie TestPackage w ten sposób nie jest wydajne, ponieważ załadowane rozwiązanie może nie zawierać nawet pliku *. config* . W tych krokach pokazano, jak kontekstu interfejsu użytkownika opartego na regułach można użyć do aktywowania kontekstu interfejsu użytkownika tylko wtedy, gdy wybrano plik z rozszerzeniem *. config* , a następnie Ładuj TestPackage podczas aktywowania kontekstu interfejsu użytkownika.

1. Zdefiniuj nowy identyfikator GUID UIContext i dodaj go do klasy pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> .

    Załóżmy na przykład, że zostanie dodany nowy UIContext "UIContextGuid". Utworzony identyfikator GUID (można utworzyć identyfikator GUID, klikając pozycję **Narzędzia**  >  **Utwórz GUID**) to "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Następnie należy dodać następującą deklarację wewnątrz klasy pakietu:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Dla atrybutów Dodaj następujące wartości: (szczegóły tych atrybutów zostaną wyjaśnione później)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Te metadane definiują nowy identyfikator GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) i wyrażenie odwołujące się do pojedynczego okresu "DotConfig". Termin "DotConfig" daje w wyniku wartość true, gdy bieżący wybór w aktywnej hierarchii ma nazwę zgodną z wzorcem wyrażenia regularnego " \\ . config $" (kończy się rozszerzeniem *. config*). Wartość (wartość domyślna) definiuje opcjonalną nazwę reguły przydatną dla debugowania.

    Wartości atrybutu są dodawane do pkgdef generowanego w czasie kompilacji.

2. W pliku VSCT dla poleceń TestPackage Dodaj flagę "DynamicVisibility" do odpowiednich poleceń:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. W sekcji widoczności w VSCT należy powiązać odpowiednie polecenia z nowym identyfikatorem GUID UIContext zdefiniowanym w #1:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. W sekcji symbole Dodaj definicję UIContext:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Teraz polecenia menu kontekstowego dla plików *\* . config* będą widoczne tylko wtedy, gdy wybrany element w Eksploratorze rozwiązań jest plikiem *. config* , a pakiet nie zostanie załadowany do momentu wybrania jednego z tych poleceń.

   Następnie użyj debugera, aby potwierdzić, że pakiet ładuje się tylko wtedy, gdy oczekiwano. Aby debugować TestPackage:

5. Ustaw punkt przerwania w <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodzie.

6. Kompiluj TestPackage i Rozpocznij debugowanie.

7. Utwórz projekt lub Otwórz go.

8. Wybierz dowolny plik z rozszerzeniem innym niż *. config*. Punkt przerwania nie powinien być trafiony.

9. Wybierz plik *App.Config* .

   TestPackage ładuje i zatrzyma się w punkcie przerwania.

## <a name="add-more-rules-for-ui-context"></a>Dodaj więcej reguł dla kontekstu interfejsu użytkownika
 Ponieważ reguły kontekstu interfejsu użytkownika są wyrażeniami logicznymi, można dodać bardziej ograniczone reguły dla kontekstu interfejsu użytkownika. Na przykład w powyższym kontekście interfejsu użytkownika można określić, że reguła ma zastosowanie tylko w przypadku załadowania rozwiązania z projektem. W ten sposób polecenia nie będą wyświetlane, jeśli otworzysz plik *. config* jako plik autonomiczny, a nie jako część projektu.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Teraz wyrażenie odwołuje się do trzech warunków. Pierwsze dwa warunki, "SingleProject" i "MultipleProjects", odnoszą się do innych dobrze znanych kontekstów interfejsu użytkownika (według ich identyfikatorów GUID). Trzeci termin "DotConfig" to kontekst interfejsu użytkownika oparty na regułach zdefiniowany wcześniej w tym artykule.

## <a name="delayed-activation"></a>Opóźniona aktywacja
 Reguły mogą mieć opcjonalne "opóźnienie". Opóźnienie jest określone w milisekundach. Jeśli jest obecny, opóźnienie powoduje, że aktywacja lub dezaktywacja kontekstu interfejsu użytkownika reguły zostanie opóźnione o ten interwał czasu. Jeśli reguła zmieni się z powrotem przed interwałem opóźnienia, nic się nie dzieje. Ten mechanizm może służyć do "rozłożenia" operacji inicjowania, szczególnie jednorazowe Inicjowanie bez polegania na czasomierzach lub rejestracji w przypadku bezczynnych powiadomień.

 Na przykład można określić regułę ładowania testowego z opóźnieniem 100 milisekund:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Typy terminów

Poniżej przedstawiono różne typy warunków, które są obsługiwane:

|Okres|Opis|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identyfikator GUID odwołuje się do kontekstu interfejsu użytkownika. Termin będzie prawdziwy, gdy kontekst interfejsu użytkownika jest aktywny i w przeciwnym razie ma wartość false.|
|HierSingleSelectionName:\<pattern>|Termin będzie prawdziwy, gdy wybór w aktywnej hierarchii jest pojedynczym elementem, a nazwa wybranego elementu jest zgodna z wyrażeniem regularnym programu .NET podanym przez "wzorzec".|
|UserSettingsStoreQuery:\<query>|"Query" reprezentuje pełną ścieżkę do magazynu ustawień użytkownika, który musi mieć wartość różną od zera. Zapytanie jest podzielone na "kolekcje" i "propertyName" na ostatnim ukośniku.|
|ConfigSettingsStoreQuery:\<query>|"zapytanie" reprezentuje pełną ścieżkę do magazynu ustawień konfiguracji, który musi mieć wartość różną od zera. Zapytanie jest podzielone na "kolekcje" i "propertyName" na ostatnim ukośniku.|
|ActiveProjectFlavor:\<projectTypeGuid>|Termin będzie spełniony, gdy aktualnie wybrany projekt jest w wersji (zagregowany) i ma wersję pasującą do danego identyfikatora GUID typu projektu.|
|ActiveEditorContentType:\<contentType>|Termin będzie prawdziwy, gdy wybrany dokument jest edytorem tekstu o danym typie zawartości. Uwaga: po zmianie nazwy wybranego dokumentu ten termin nie jest odświeżany, dopóki plik nie zostanie zamknięty i ponownie otwarty.|
|ActiveProjectCapability:\<Expression>|Warunek ma wartość true, jeśli aktywne funkcje projektu pasują do podanego wyrażenia. Wyrażenie może być takie jak VB &#124; CSharp.|
|SolutionHasProjectCapability:\<Expression>|Podobnie jak powyżej, ale termin ma wartość true, jeśli rozwiązanie zawiera każdy załadowany projekt, który jest zgodny z wyrażeniem.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Termin będzie spełniony, gdy rozwiązanie ma projekt, który jest w wersji (zagregowany) i ma wersję pasującą do danego identyfikatora GUID typu projektu.|
|ProjectAddedItem:\<pattern>| Termin ma wartość true, gdy plik zgodny ze specyfikatorem "wzorzec" zostanie dodany do projektu w otwartym soluion.|
|ActiveProjectOutputType:\<outputType>|Warunek ma wartość true, jeśli typ danych wyjściowych dla aktywnego projektu jest zgodny.  Element OutputType może być liczbą całkowitą lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> typem.|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|Warunek ma wartość PRAWDA, jeśli aktywny projekt ma określoną właściwość kompilacji i wartość właściwości jest zgodna z podanym filtrem wyrażeń regularnych. Zapoznaj się z [utrwalaniem danych w plikach projektów programu MSBuild](internals/persisting-data-in-the-msbuild-project-file.md) , aby uzyskać więcej szczegółowych informacji na temat właściwości kompilacji.|
|SolutionHasProjectBuildProperty:\<buildProperty>=\<regex>|Termin ma wartość true, jeśli rozwiązanie ma załadowany projekt z określoną właściwością kompilacji i wartością właściwości jest zgodny z podanym filtrem wyrażeń regularnych.|

## <a name="compatibility-with-cross-version-extension"></a>Zgodność z rozszerzeniem między wersjami

Konteksty interfejsu użytkownika oparte na regułach to nowa funkcja w programie Visual Studio 2015 i nie można jej przenieść do wcześniejszych wersji. Nie można przenieść do wcześniejszych wersji tworzy problem z rozszerzeniami/pakietami przeznaczonymi dla wielu wersji programu Visual Studio. Te wersje będą musiały być ładowane do Visual Studio 2013 i wcześniej, ale mogą korzystać z kontekstów interfejsu użytkownika opartych na regułach, aby uniemożliwić ich ładowanie do programu Visual Studio 2015.

W celu obsługi takich pakietów wpisy AutoLoadPackages w rejestrze mogą teraz podawać flagę w polu wartość, aby wskazać, że wpis powinien zostać pominięty w programie Visual Studio 2015 lub nowszym. Można to zrobić, dodając opcję flags do <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . Pakietów VSPackage może teraz dodać do swojego atrybutu opcję **SkipWhenUIContextRulesActive** <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> , aby wskazać, że wpis ma być ignorowany w programie Visual Studio 2015 i nowszych.
## <a name="extensible-ui-context-rules"></a>Rozszerzalne reguły kontekstu interfejsu użytkownika

Czasami pakiety nie mogą używać statycznych reguł kontekstu interfejsu użytkownika. Załóżmy na przykład, że masz pakiet obsługujący rozszerzalność, w taki sposób, że stan polecenia jest oparty na typach edytorów, które są obsługiwane przez zaimportowanych dostawców MEF. Polecenie jest włączone, jeśli istnieje rozszerzenie obsługujące bieżący typ edycji. W takich przypadkach pakiet nie może korzystać z statycznej reguły kontekstu interfejsu użytkownika, ponieważ terminy zmieniają się w zależności od tego, które rozszerzenia MEF są dostępne.

Aby można było obsługiwać takie pakiety, konteksty interfejsu użytkownika oparte na regułach obsługują wyrażenie stałe "*", które wskazuje, że wszystkie poniższe warunki zostaną dołączone do lub. Dzięki temu pakiet główny może zdefiniować znany kontekst interfejsu użytkownika oparty na regułach i powiązać jego stan poleceń z tym kontekstem. Następnie wszystkie rozszerzenia MEF przeznaczone dla pakietu głównego mogą dodać swoje warunki dla edytorów, które obsługuje bez wpływu na inne warunki lub wyrażenie główne.

Dokumentacja konstruktora <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> zawiera składnię dla reguł kontekstu rozszerzalnego interfejsu użytkownika.
