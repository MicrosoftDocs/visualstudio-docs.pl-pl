---
title: Konwencje nazewnictwa .NET dla plików EditorConfig
ms.date: 08/07/2019
ms.topic: reference
helpviewer_keywords:
- naming conventions [EditorConfig]
- EditorConfig naming conventions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5c4115f4d63456e105fb4a6770fd1650938770d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588606"
---
# <a name="net-naming-conventions-for-editorconfig"></a>Konwencje nazewnictwa platformy .NET dla EditorConfig

Konwencje nazewnictwa dotyczą nazewnictwa elementów kodu, takich jak klasy, właściwości i metody. Można na przykład określić, że elementy członkowskie publiczne muszą `_`być kapitalizowane lub że pola prywatne muszą zaczynać się od . Reguły te można wymusić, określając je w [pliku .editorconfig](../ide/create-portable-custom-editor-options.md). Naruszenia reguł nazewnictwa są wyświetlane na **liście błędów** lub jako sugestia pod nazwą, w zależności od ważności, którą wybierzesz dla reguły. Nie ma potrzeby tworzenia projektu, aby zobaczyć naruszenia.

Dla każdej konwencji nazewnictwa należy określić symbole, które stosuje się do, styl nazewnictwa i ważność wymuszania konwencji, przy użyciu właściwości opisanych poniżej. Kolejność właściwości nie jest ważna.

Aby rozpocząć, wybierz tytuł reguły nazewnictwa, która będzie używana w każdej z właściwości, które są potrzebne do pełnego opisania reguły. Na przykład `public_members_must_be_capitalized` jest dobrą, opisową nazwą reguły nazewnictwa. Ta strona będzie odnosić się do tytułu wybranego jako **<nazewnictwaRuleTitle\> ** w kolejnych sekcjach.

## <a name="symbols"></a>Symbole

Najpierw zidentyfikuj grupę symboli, do które ma być stosowana reguła nazewnictwa. Ta właściwość ma następujący format:

`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`

Nadaj nazwę grupie symboli, zastępując **<\> symbolNacię** napisu na przykład `public_symbols`. Symbol **<SymbolTitle\> ** użyjesz w trzech nazwach właściwości, które opisują, do których symboli jest stosowana reguła (rodzaje symboli, poziomów ułatwień dostępu i modyfikatorów).

### <a name="kinds-of-symbols"></a>Rodzaje symboli

Aby opisać rodzaj symboli, do jakich ma być stosowana reguła nazewnictwa, należy określić właściwość w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = <values>`

Na poniższej liście przedstawiono dopuszczalne wartości i można określić wiele wartości, oddzielając je przecinkiem.

- \*(Użyj tej wartości, aby określić wszystkie symbole)
- przestrzeń nazw
- class
- struktura 
- interface
- enum
- property
- method
- pole
- event
- delegate
- parametr
- type_parameter
- local
- local_function

### <a name="accessibility-levels-of-symbols"></a>Poziomy ułatwień dostępu symboli

Aby opisać poziomy ułatwień dostępu symboli, do których ma być stosowana reguła nazewnictwa, określ nazwę właściwości w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = <values>`

Na poniższej liście przedstawiono dopuszczalne wartości i można określić wiele wartości, oddzielając je przecinkiem.

- \*(Użyj tej wartości, aby określić wszystkie poziomy ułatwień dostępu)
- public
- wewnętrzny lub przyjaciel
- private
- protected
- chronione\_wewnętrzne lub protected_friend
- prywatne\_chronione
- local

   Poziom `local` ułatwień dostępu ma zastosowanie do symboli zdefiniowanych w ramach metody. Jest to przydatne do definiowania konwencji nazewnictwa dla symboli, których dostępność nie może być określona w kodzie. Na przykład jeśli `applicable_accessibilities = local` określisz w konwencji nazewnictwa dla stałych (`required_modifiers = const`), reguła ma zastosowanie tylko do stałych zdefiniowanych w ramach metody, a nie zdefiniowanych w typie.

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

Aby opisać modyfikatory symboli, do których ma być stosowana reguła nazewnictwa, określ nazwę właściwości w następującym formacie:

`dotnet_naming_symbols.<symbolTitle>.required_modifiers = <values>`

Na poniższej liście przedstawiono dopuszczalne wartości (oddzielenie wielu wartości przecinkiem):

- `abstract` lub `must_inherit`
- `async`
- `const`
- `readonly`
- `static` lub `shared`

   > [!NOTE]
   > Jeśli masz regułę nazewnictwa `static` lub `shared` symbole, jest `const` ona również stosowana do symboli, ponieważ są one niejawnie statyczne. Jeśli nie chcesz, `static` aby reguła nazewnictwa była stosowana do `const` symboli, utwórz osobną regułę nazewnictwa symboli. `const`

Reguła nazewnictwa dopasowuje podpisy, `required_modifiers`które mają *wszystkie* modyfikatory określone w pliku . Jeśli ta właściwość zostanie pominięta, używana jest domyślna wartość pustej listy, oznacza to, że dla dopasowania nie są wymagane żadne określone modyfikatory. Oznacza to, że modyfikatory symbolu nie mają wpływu na to, czy ta reguła jest stosowana.

> [!TIP]
> Nie należy określać `*` `required_modifiers`wartości dla . Zamiast tego po prostu `required_modifiers` całkowicie pomiń właściwość, a reguła nazewnictwa będzie miała zastosowanie do dowolnego rodzaju modyfikatora.

## <a name="style"></a>Styl

Po zidentyfikowaniu grupy symboli, do której chcesz zastosować regułę nazewnictwa, możesz opisać styl nazewnictwa. Styl może być taki, że nazwa ma określony prefiks lub określony sufiks lub że poszczególne wyrazy w nazwie są oddzielone określonym znakiem. Można również określić styl wielkich liter. Właściwość style ma następujący format:

`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`

Nadaj stylowi nazwę, zastępując **<\> styleTwartość** napisem, na `first_word_upper_case_style`przykład . Użyjesz **<styleTytut\> ** w nazwach właściwości opisujących styl nazewnictwa (prefiks, sufiks, znak separatora wyrazów i wielkość liter). Użyj co najmniej jednej z tych właściwości, aby opisać swój styl.

### <a name="require-a-prefix"></a>Wymagaj prefiksu

Aby określić, że nazwy symboli muszą zaczynać się od określonych znaków, należy użyć tej właściwości:

`dotnet_naming_style.<styleTitle>.required_prefix = <prefix>`

### <a name="require-a-suffix"></a>Wymagaj przyrostka

Aby określić, że nazwy symboli muszą kończyć się określonymi znakami, należy użyć tej właściwości:

`dotnet_naming_style.<styleTitle>.required_suffix = <suffix>`

### <a name="require-a-certain-word-separator"></a>Wymagaj określonego separatora wyrazów

Aby określić, że poszczególne wyrazy w nazwach symboli muszą być oddzielone określonym znakiem, należy użyć tej właściwości:

`dotnet_naming_style.<styleTitle>.word_separator = <separator character>`

### <a name="require-a-capitalization-style"></a>Wymagaj stylu wielkich liter

Aby określić określony styl wielkich liter dla nazw symboli, należy użyć tej właściwości:

`dotnet_naming_style.<styleTitle>.capitalization = <value>`

Dopuszczalne wartości dla tej właściwości to:

- pascal_case
- camel_case
- pierwsze\_word_upper
- wszystkie\_górne
- all_lower

> [!NOTE]
> Styl wielkich liter należy określić jako część stylu nazewnictwa, w przeciwnym razie styl nazewnictwa może zostać zignorowany.

## <a name="severity"></a>Ważność

Aby opisać ważność naruszenia reguły nazewnictwa, określ właściwość w następującym formacie:

`dotnet_naming_rule.<namingRuleTitle>.severity = <value>`

W poniższej tabeli przedstawiono dopuszczalne wartości ważności i ich znaczenie:

Ważność | Efekt
------------ | -------------
brak | Reguła jest całkowicie wygaszone.
refaktoryzowanie lub milczenie | Jeśli ten styl nie jest przestrzegany, nie pokazuj niczego użytkownikowi; jednak automatycznie wygenerowany kod jest zgodny z tym stylem.
Sugestia | Gdy ten styl nie jest przestrzegany, pokaż go użytkownikowi jako sugestię, jako podstawowe kropki na pierwszych dwóch znakach. Nie ma wpływu w czasie kompilacji.
ostrzeżenie | Jeśli ten styl nie jest przestrzegany, pokaż ostrzeżenie kompilatora na **liście błędów**.
error | Jeśli ten styl nie jest przestrzegany, pokaż błąd kompilatora na **liście błędów**.

> [!NOTE]
> Nie trzeba tworzyć projektu, aby zobaczyć naruszenia reguł nazewnictwa. Są one wyświetlane jako kod jest edytowany, albo na **liście błędów** lub jako sugestia.

## <a name="rule-order"></a>Kolejność reguł

::: moniker range="vs-2017"

Konwencje nazewnictwa powinny być uporządkowane od najbardziej specyficznych do najmniej specyficznych w editorconfig pliku. Pierwsza napotkana reguła, która może być stosowana, jest jedyną regułą, która jest stosowana. Jeśli jednak istnieje wiele *właściwości reguły* o tej samej nazwie, pierwszeństwo ma ostatnio znaleziona właściwość o tej nazwie. Aby uzyskać więcej informacji, zobacz [Hierarchia plików i pierwszeństwo](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

::: moniker range=">=vs-2019"

Począwszy od programu Visual Studio 2019 w wersji 16.2 kolejność, w której reguły nazewnictwa są zdefiniowane w pliku EditorConfig nie ma znaczenia. Zamiast tego Visual Studio porządkuuje reguły nazewnictwa automatycznie zgodnie z definicją samych reguł. [EditorConfig Language Service rozszerzenie](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) można analizować EditorConfig pliku i zgłaszać przypadki, w których reguła kolejność w pliku różni się od tego, co kompilator będzie używać w czasie wykonywania.

Jeśli używasz wcześniejszej wersji programu Visual Studio, konwencje nazewnictwa powinny być uporządkowane od najbardziej specyficznych do najmniej specyficznych w editorconfig pliku. Pierwsza napotkana reguła, która może być stosowana, jest jedyną regułą, która jest stosowana. Jeśli jednak istnieje wiele *właściwości reguły* o tej samej nazwie, pierwszeństwo ma ostatnio znaleziona właściwość o tej nazwie. Aby uzyskać więcej informacji, zobacz [Hierarchia plików i pierwszeństwo](create-portable-custom-editor-options.md#file-hierarchy-and-precedence).

::: moniker-end

## <a name="default-naming-styles"></a>Domyślne style nazewnictwa

Jeśli nie określisz żadnych niestandardowych reguł nazewnictwa, program Visual Studio używa następujących stylów domyślnych:

- W przypadku klas, struktur, wyliczenia, właściwości `public`i `private` `internal`zdarzeń `protected`z `protected_internal` , , , , lub dostępności, domyślny styl nazewnictwa jest przypadek Pascala.

- W przypadku `public`interfejsów `internal` `protected`z `protected_internal` , `private`, , lub dostępności, domyślnym stylem nazewnictwa jest przypadek Pascala z wymaganym prefiksem **I**.

## <a name="example"></a>Przykład

Poniższy plik *.editorconfig* zawiera konwencję nazewnictwa, która określa, że właściwości publiczne, metody, pola, zdarzenia i delegatów muszą być kapitalizowane. Należy zauważyć, że ta konwencja nazewnictwa określa wiele rodzajów symbolu, do których należy zastosować regułę, używając przecinka do oddzielenia wartości.

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

Poniższy zrzut ekranu przedstawia efekt tej konwencji nazewnictwa w edytorze. Dwie zmienne publiczne zostały nazwane bez wielkich liter pierwszej litery. Jednym z `const`nich jest `readonly`, a drugim jest . Ponieważ reguła nazewnictwa `readonly` ma zastosowanie tylko `readonly` do symboli, tylko zmienna pokazuje sugestię reguły nazewnictwa.

![Sugestia reguły nazewnictwa](media/editorconfig-naming-rule-suggestion.png)

Teraz zmieńmy powagę naruszenia `warning`na:

```ini
dotnet_naming_rule.public_members_must_be_capitalized.severity = warning
```

Jeśli zamkniesz i ponownie otworzysz plik kodu, zamiast sugestii pod naruszeniem nazwy, na liście błędów pojawi się zielony falista i ostrzeżenie:

![Ostrzeżenie o regułach nazewnictwa](media/editorconfig-naming-rule-warning.png)

## <a name="see-also"></a>Zobacz też

- [Konwencje języka](editorconfig-language-conventions.md)
- [Konwencje formatowania](editorconfig-formatting-conventions.md)
- [Konwencje nazewnictwa Roslyn](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [Tworzenie przenośnych opcji edytora niestandardowego](../ide/create-portable-custom-editor-options.md)
- [Ustawienia konwencji kodowania .NET dla EditorConfig](editorconfig-code-style-settings-reference.md)
