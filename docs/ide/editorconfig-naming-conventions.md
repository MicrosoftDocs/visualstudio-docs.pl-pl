---
title: Konwencje nazewnictwa platformy .NET dla plików EditorConfig
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab118197c29ef950907839e8c04d6e49a9843f1a
ms.sourcegitcommit: 6f3cf7a1bfc81a61f9a603461a1c34fd2221f100
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957428"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Konwencje nazewnictwa platformy .NET dla EditorConfig

Konwencje nazewnictwa dotyczą nazw elementów kodu, takich jak klasy, właściwości i metody. Na przykład można określić, że publiczne składowe muszą być pisane wielkimi literami lub że metody asynchroniczne muszą kończyć się "Async". Te reguły można wymusić, określając je w [pliku. editorconfig](../ide/create-portable-custom-editor-options.md). Naruszenia reguły nazewnictwa pojawiają się w **Lista błędów** lub jako sugestia pod nazwą, w zależności od ważności wybranej dla reguły. Nie ma potrzeby kompilowania projektu w celu wyświetlenia naruszeń.

Dla każdej konwencji nazewnictwa należy określić symbole, do których ma zastosowanie, styl nazewnictwa i ważność wymuszania Konwencji przy użyciu właściwości opisanych poniżej. Kolejność właściwości nie jest ważna.

Aby rozpocząć, wybierz tytuł reguły nazewnictwa, która będzie używana we wszystkich właściwościach, które są potrzebne do pełnego opisywania reguły. Na przykład `public_members_must_be_capitalized` jest dobrą, opisową nazwą Reguły nazewnictwa. Ta strona będzie odnosić się do tytułu wybranego jako **< namingRuleTitle\>**  w poniższych sekcjach.

## <a name="symbols"></a>Symbole

Najpierw Zidentyfikuj grupę symboli, do której ma zostać zastosowana reguła nazewnictwa. Ta właściwość ma następujący format:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Nadaj nazwę grupie symboli, zastępując **< wartość symbolTitle\>**  nazwą opisową, na przykład. `public_symbols` Wartość **< symbolTitle\>**  jest używana w trzech nazwach właściwości, które opisują, do których symboli stosowana jest reguła (rodzaje symboli, poziomy ułatwień dostępu i modyfikatory).

### <a name="kinds-of-symbols"></a>Rodzaje symboli

Aby opisać rodzaj symboli, do których ma zostać zastosowana reguła nazewnictwa, określ właściwość w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

Na poniższej liście przedstawiono dozwolone wartości i można określić wiele wartości, rozdzielając je przecinkami.

- \*(Użyj tej wartości, aby określić wszystkie symbole)
- — przestrzeń nazw
- class
- struktura
- interface
- enum
- property
- — metoda
- pole
- zdarzenie
- delegate
- parametr
- type_parameter
- local
- local_function

### <a name="accessibility-levels-of-symbols"></a>Poziomy ułatwień dostępu symboli

Aby opisać poziomy ułatwień dostępu do symboli, do których ma zastosowanie reguła nazewnictwa, określ nazwę właściwości w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

Na poniższej liście przedstawiono dozwolone wartości i można określić wiele wartości, rozdzielając je przecinkami.

- \*(Użyj tej wartości, aby określić wszystkie poziomy ułatwień dostępu)
- public
- wewnętrzny lub zaprzyjaźniony
- private
- protected
- chroniona\_wewnętrzna lub protected_friend
- prywatne\_chronione
- local

   Poziom `local` dostępności ma zastosowanie do symboli zdefiniowanych w ramach metody. Jest to przydatne w przypadku definiowania konwencji nazewnictwa dla symboli, których dostępność nie może być określona w kodzie. Na przykład, jeśli określisz `applicable_accessibilities = local` konwencję nazewnictwa dla stałych (`required_modifiers = const`), reguła dotyczy tylko stałych zdefiniowanych w ramach metody, a nie tych zdefiniowanych w typie.

   ```csharp
   class TypeName
   {
     // Constant defined in a type.
     const int X = 3;

     void Method()
     {
       // Constant defined in a method with "local" accessibility.
       const int Y = 4;
     }
   }
   ```

### <a name="symbol-modifiers-optional"></a>Modyfikatory symboli (opcjonalnie)

Aby opisać Modyfikatory symboli, do których ma zastosowanie reguła nazewnictwa, określ nazwę właściwości w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

Na poniższej liście przedstawiono dozwolone wartości (Rozdziel wiele wartości przecinkami):

- `abstract` lub `must_inherit`
- `async`
- `const`
- `readonly`
- `static` lub `shared`

   > [!NOTE]
   > Jeśli masz regułę nazewnictwa dla `static` symboli lub `shared` , są one również stosowane do `const` symboli, ponieważ są one niejawnie statyczne. Jeśli nie chcesz `static` , aby reguła nazewnictwa miała zastosowanie `const` do symboli, utwórz oddzielną regułę `const` nazewnictwa dla symboli.

Reguła nazewnictwa dopasowuje podpisy, które mają *wszystkie* Modyfikatory `required_modifiers`określone w. W przypadku pominięcia tej właściwości zostanie użyta wartość domyślna pustej listy, co oznacza, że dla dopasowania nie są wymagane określone modyfikatory. Oznacza to, że Modyfikatory symbolu nie mają wpływu na to, czy ta reguła jest stosowana.

> [!TIP]
> Nie określaj wartości `*` parametru for `required_modifiers`. Zamiast tego wystarczy pominąć `required_modifiers` Właściwość całkowicie i reguła nazewnictwa będzie stosowana do dowolnego rodzaju modyfikatora.

## <a name="style"></a>Styl

Teraz, po zidentyfikowaniu grupy symboli, do której ma zostać zastosowana reguła nazewnictwa, można opisać styl nazewnictwa. Styl może być, że nazwa ma określony prefiks lub określony sufiks lub że poszczególne wyrazy w nazwie są oddzielone określonym znakiem. Możesz również określić styl kapitalizacji. Właściwość Style ma następujący format:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Nadaj stylowi nazwę, zastępując < wartość **styleTitle\>**  nazwą opisową, na przykład. `first_word_upper_case_style` **< Wartość styleTitle\>**  w nazwach właściwości, które opisują styl nazewnictwa (prefiks, sufiks, znak separatora słów i wielkie litery). Aby opisać styl, Użyj co najmniej jednej z tych właściwości.

### <a name="require-a-prefix"></a>Wymagaj prefiksu

Aby określić, że nazwy symboli muszą zaczynać się od określonych znaków, Użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Wymagaj sufiksu

Aby określić, że nazwy symboli muszą kończyć się niektórymi znakami, Użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Wymagaj określonego separatora wyrazów

Aby określić, że poszczególne wyrazy w nazwach symboli muszą być oddzielone określonym znakiem, Użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Wymagaj stylu wielką literą

Aby określić określony styl wielką literą dla nazw symboli, Użyj tej właściwości:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Dozwolone wartości tej właściwości to:

- pascal_case
- camel_case
- pierwszy\_word_upper
- wszystkie\_wielkie litery
- all_lower

> [!NOTE]
> Należy określić styl kapitalizacji jako część stylu nazewnictwa. w przeciwnym razie styl nazewnictwa może zostać zignorowany.

## <a name="severity"></a>Ważność

Aby opisać ważność naruszenia reguły nazewnictwa, należy określić właściwość w następującym formacie:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

W poniższej tabeli przedstawiono dozwolone wartości ważności i znaczenie:

Ważność | Efekt
------------ | -------------
brak | Reguła została całkowicie pominięta.
Refaktoryzacja lub dyskretna | Gdy ten styl nie jest przestrzegany, nie pokazuj niczego użytkownikowi; jednak automatycznie wygenerowany kod jest zgodny z tym stylem.
Propozycje | Gdy ten styl nie jest przestrzegany, Pokaż go użytkownikowi jako sugestię, jako punkty bazowe na pierwszych dwóch znakach. Nie ma ona wpływu na czas kompilacji.
warning | Gdy ten styl nie jest przestrzegany, Pokaż Ostrzeżenie kompilatora w **Lista błędów**.
error | Gdy ten styl nie jest przestrzegany, Pokaż błąd kompilatora w **Lista błędów**.

> [!NOTE]
> Nie jest konieczne Kompilowanie projektu w celu wyświetlenia naruszeń reguły nazewnictwa. Są one wyświetlane jako kod jest edytowany w **Lista błędów** lub w formie sugestii.

## <a name="rule-order"></a>Kolejność reguł

::: moniker range="vs-2017"

Konwencje nazewnictwa powinny być uporządkowane z najbardziej specyficznych dla najmniej określonych w pliku EditorConfig. Pierwsza napotkana reguła jest jedyną zastosowanym regułą. Jeśli jednak istnieje wiele *Właściwości* reguł o tej samej nazwie, pierwszeństwo ma właściwość ostatnio znaleziona o tej nazwie. Aby uzyskać więcej informacji, zobacz [Hierarchia plików i pierwszeństwo](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

Począwszy od programu Visual Studio 2019 w wersji 16,2, kolejność, w której reguły nazewnictwa są zdefiniowane w pliku EditorConfig, nie ma znaczenia. Zamiast tego program Visual Studio automatycznie porządkuje reguły nazewnictwa zgodnie z definicją samych reguł. [Rozszerzenie usługi językowej EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) może analizować plik EditorConfig i zgłaszać przypadki, w których kolejność sortowania reguł w pliku różni się od tego, co kompilator będzie używać w czasie wykonywania.

Jeśli używasz wcześniejszej wersji programu Visual Studio, konwencje nazewnictwa powinny być uporządkowane z najbardziej specyficznych dla najmniej określonych w pliku EditorConfig. Pierwsza napotkana reguła jest jedyną zastosowanym regułą. Jeśli jednak istnieje wiele *Właściwości* reguł o tej samej nazwie, pierwszeństwo ma właściwość ostatnio znaleziona o tej nazwie. Aby uzyskać więcej informacji, zobacz [Hierarchia plików i pierwszeństwo](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Domyślne style nazewnictwa

Jeśli nie określisz żadnych niestandardowych reguł nazewnictwa, program Visual Studio używa następujących stylów domyślnych:

- W przypadku klas, struktur, wyliczeń, właściwości i zdarzeń z `public`, `private`, `internal`, `protected`, lub `protected_internal` dostępności, domyślny styl nazewnictwa to przypadek Pascal.

- W przypadku interfejsów `public`z `private`, `internal` `protected_internal` , `protected`,, lub dostępności, domyślny styl nazewnictwa jest przypadek Pascal z wymaganym prefiksem **I**.

## <a name="example"></a>Przykład

Następujący plik *. editorconfig* zawiera konwencję nazewnictwa, która określa, że właściwości publiczne, metody, pola, zdarzenia i Delegaty muszą być pisane wielkimi literami. Należy zauważyć, że ta konwencja nazewnictwa określa wiele rodzajów symboli, do których ma zostać zastosowana reguła, przy użyciu przecinka do oddzielenia wartości.

```ini
# Public members must be capitalized (public_members_must_be_capitalized)
[*.{cs,vb}]
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

Poniższy zrzut ekranu przedstawia efekt tej konwencji nazewnictwa w edytorze. Dwie zmienne publiczne zostały nazwane bez użycia wielkich liter. Jeden to a `const`, a jest. `readonly` Ponieważ reguła nazewnictwa dotyczy `readonly` tylko symboli, `readonly` tylko zmienna pokazuje sugestię reguły nazewnictwa.

![Sugestia reguły nazewnictwa](media/editorconfig-naming-rule-suggestion.png)

Teraz zmień ważność naruszenia na `warning`:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Jeśli zamkniesz i otworzysz ponownie plik kodu, a nie zobaczysz sugestii pod naruszeniem nazw, zobaczysz zieloną falistej oraz ostrzeżenie w **Lista błędów**:

![Ostrzeżenie reguły nazewnictwa](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Zobacz także

- [Konwencje językowe](editorconfig-language-conventions.md)
- [Konwencje formatowania](editorconfig-formatting-conventions.md)
- [Konwencje nazewnictwa Roslyn](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Tworzenie przenośnych opcji edytora niestandardowego](../ide/create-portable-custom-editor-options.md)
- [.NET coding convention ustawienia dla wtyczki EditorConfig](editorconfig-code-style-settings-reference.md)
