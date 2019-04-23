---
title: Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9685d1621f0e81adbbb034c250974b7bc9b36993
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064586"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes

W tym artykule omówiono opcje i kwestie w substytuty Generowanie i kompilacja kodu i opisano konwencje nazewnictwa dla typów, elementów członkowskich i parametrów pozornie wygenerowanych.

**Wymagania**

- Visual Studio Enterprise
- Projekt programu .NET Framework

> [!NOTE]
> Projekty .NET standard nie są obsługiwane.

## <a name="code-generation-and-compilation"></a>Generowanie i kompilacja kodu

### <a name="configure-code-generation-of-stubs"></a>Konfigurowanie generowania kodu odcinków

Generowanie typów namiastek jest skonfigurowany w pliku XML, który ma *.fakes* rozszerzenie pliku. Fakes framework integruje się w procesie kompilacji przez własne zadania MSBuild i wykrywa te pliki w czasie kompilacji. Generator kodu pozornego kompiluje typy namiastek w zestaw i dodaje odwołanie do projektu.

Poniższy przykład ilustruje typy namiastki zdefiniowane w *FileSystem.dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtrowanie typów

Można ustawić filtry *.fakes* plik, aby ograniczyć typy, które mają być generowane namiastki. Możesz dodać nieograniczoną liczbę elementów Clear, Add, Remove elementów elementu StubGeneration, aby zbudować listę wybranych typów.

Na przykład następująca *.fakes* pliku generuje namiastki dla typów w przestrzeni nazw System i System.IO, z wyłączeniem wszystkich typów zawierających "Handle" w systemie:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Clear />
    <Add Namespace="System!" />
    <Add Namespace="System.IO!"/>
    <Remove TypeName="Handle" />
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

Ciągi filtrów używają prostej gramatyki do zdefiniowania, jak dopasowywania powinna być podejmowana:

- Filtry domyślnie wielkość liter; filtry dopasowują podciąg:

     `el` pasuje do "hello"

- Dodawanie `!` do końca filtru sprawia, że dokładne dopasowanie uwzględniające:

     `el!` nie pasuje do "hello"

     `hello!` pasuje do "hello"

- Dodawanie `*` do końca filtru sprawia, że pasującym do przedrostka ciągu:

     `el*` nie pasuje do "hello"

     `he*` pasuje do "hello"

- Wiele filtrów na rozdzielonej średnikami liście zostanie połączonych jako alternatywa:

     `el;wo` pasuje do "hello" i "world"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Klasy zastępczej klas konkretnych i metod wirtualnych

Domyślnie typy namiastki są generowane dla wszystkich niezamkniętych klas. Umożliwia ograniczenie typów namiastki do klas abstrakcyjnych za pośrednictwem *.fakes* pliku konfiguracji:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
  <Assembly Name="mscorlib" />
  <!-- user code -->
  <StubGeneration>
    <Types>
      <Clear />
      <Add AbstractClasses="true"/>
    </Types>
  </StubGeneration>
  <!-- /user code -->
</Fakes>
```

### <a name="internal-types"></a>Typy wewnętrzne

Generator kodu pozornego wygeneruje typy zastępcze i typy namiastki dla typów, które są widoczne dla wygenerowanego zestawu pozornego. Aby typy wewnętrzne zestawu typu shim były widoczne dla elementów sztucznych i zestaw testowy, należy dodać <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybuty do kodu zestawu typu shim, który zwiększa widoczność w wygenerowanych zestawach fakes i zestawu testowego. Oto przykład:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Typy wewnętrzne w zestawach o silnej nazwie**

 Jeśli zestawu typu shim ma silnej nazwy, i chcesz uzyskać dostęp do wewnętrznych typów zestawu:

- Zarówno zestaw testowy i zestaw Pozorowany muszą posiadać silne nazwy.

- Dodaj klucze publiczne testu i podrobionego zestawu do **InternalsVisibleToAttribute** atrybutów w zestawach typu shim. Poniżej przedstawiono, jak będzie wyglądać przykładowe atrybuty w kodzie zestawu shimmed zestawu typu shim ma silnej nazwy:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Jeśli zestawu typu shim ma silnej nazwy, Fakes framework automatycznie podpisuje wygenerowanego zestawu pozornego. Masz silny podpis zestawu testowego. Zobacz [zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies).

Struktura Fakes używa tego samego klucza do podpisywania wszystkich generowanych zestawów, więc ten fragment kodu jako punktu wyjścia służy do dodawania **InternalsVisibleTo** atrybutu zestawu pozorowanego w kodzie zestawu typu shim.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Można określić inny klucz publiczny zestawu Pozorowanego, taki jak klucz utworzony dla zestawu typu shim, podając pełną ścieżkę do *.snk* pliku, który zawiera klucz alternatywny jako `KeyFile` wartość atrybutu `Fakes` \\ `Compilation` elementu *.fakes* pliku. Na przykład:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Następnie trzeba użyć klucza publicznego alternatywna *.snk* pliku jako drugiego parametru atrybutu InternalVisibleTo do zestawu Pozorowanego w kodzie zestawu shimmed:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

W przykładzie powyżej wartości `Alternate_public_key` i `Test_assembly_public_key` może być taki sam.

### <a name="optimize-build-times"></a>Optymalizuj czas kompilacji

Kompilacja zestawów pozornych może znacznie zwiększyć czas kompilacji. Generując zestawy pozorne dla zestawów .NET System i zestawów innych firm w osobnym scentralizowanym projekcie, można zminimalizować czas kompilacji. Ponieważ takie zestawy rzadko się zmieniają, można użyć ponownie wygenerowanych zestawów pozornych w innych projektach.

Z projektów testów jednostkowych Dodaj odwołanie do skompilowanych zestawów pozornych, które są umieszczone w FakesAssemblies w folderze projektu.

1. Utwórz nową bibliotekę klas z wersją środowiska uruchomieniowego .NET dopasowania Twoich projektów testów. Nazwijmy ją Fakes.Prebuild. Usuń *class1.cs* pliku z projektem, nie jest wymagane.

2. Dodaj odwołanie do wszystkich systemowych i zestawów innych firm, których potrzebujesz substytutów.

3. Dodaj *.fakes* pliku dla wszystkich zestawów i kompilacji.

4. Z projektu testów

    - Upewnij się, że masz odwołanie do środowiska uruchomieniowego podrobionych DLL:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Dla każdego zestawu, który utworzono substytuty, Dodaj odwołanie do odpowiedniego pliku DLL w *Fakes.Prebuild\FakesAssemblies* folderze projektu.

### <a name="avoid-assembly-name-clashing"></a>Uniknąć konfliktu nazw zestawów

W środowisku kompilacji zespołowej wszystkie dane wyjściowe kompilacji są scalane w jednym katalogu. Jeśli wiele projektów używa substytutów, może się zdarzyć, że zestawy pozorne z różnych wersji nadpiszą. Na przykład TestProject1 elementów sztucznych *mscorlib.dll* z .NET Framework 2.0 i TestProject2 elementów sztucznych *mscorlib.dll* dla programu .NET Framework 4 zarówno dałaby do *mscorlib. Fakes.dll* zestaw elementów sztucznych.

 Aby uniknąć tego problemu, substytuty powinny automatycznie tworzyć nazwy zestawów pozorowanych z wersją kwalifikowaną dla odwołań do projektu bez podczas dodawania *.fakes* plików. Nazwa zestawu Pozorowanego wersją kwalifikowaną dołącza numer wersji, podczas tworzenia nazwy zestawu elementów sztucznych:

 Biorąc pod uwagę zestaw MyAssembly i wersję 1.2.3.4 Nazwa zestawu Pozorowanego to MyAssembly.1.2.3.4.Fakes.

 Możesz zmienić lub usunąć tę wersję przez edycję atrybutu wersja elementu zestaw w *.fakes*:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Konwencje nazewnictwa substytutów

### <a name="shim-type-and-stub-type-naming-conventions"></a>Typ podkładek i klas zastępczych wpisz konwencje nazewnictwa

 **Przestrzenie nazw**

- . Substytuty sufiks jest dodawany do przestrzeni nazw.

   Na przykład `System.Fakes` przestrzeń nazw zawiera typy zastępcze z przestrzeni nazw System.

- Global.Fakes zawiera typ pustej przestrzeni nazw.

  **Nazwy typów**

- Przedrostek shim jest dodawany do nazwy typu, aby zbudować nazwę typu zastępczego.

   Na przykład ShimExample jest typem podkładki typu Example.

- Przedrostek stub jest dodawany do nazwy typu, aby zbudować nazwę typu namiastki.

   Na przykład StubIExample jest typem wycinka typu IExample.

  **Argumenty typu i struktury typu zagnieżdżonego**

- Argumenty typu ogólnego są kopiowane.

- Struktura typów zagnieżdżonych jest kopiowana dla typów zastępczych.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Właściwości delegata zastępczego lub konwencji nazewnictwa pól delegata namiastki

**Podstawowe zasady** dla nazewnictwa pól, zaczynając od pustej nazwy:

- Nazwa metody jest dołączana.

- Jeśli nazwa metody jest jawną implementacją interfejsu, kropki są usuwane.

- Jeśli metoda jest ogólna, `Of` *n* jest dołączana w przypadku gdy *n* jest to liczba argumentów metody ogólnej.

  **Specjalne nazwy metod** takie jak właściwości getter lub setter są traktowane zgodnie z opisem w poniższej tabeli:

|Jeśli metoda to...|Przykład|Dołączona nazwa metody|
|-|-|-|
|A **konstruktora**|`.ctor`|`Constructor`|
|Statyczna **konstruktora**|`.cctor`|`StaticConstructor`|
|**Akcesor** przy użyciu metody nazwą składającą się z dwóch części oddzielonych "_" (np. metody pobierające właściwości)|*kind_name* (common wielkość liter, ale nie wymuszona przez ECMA)|*NameKind*, gdzie obie części zostały napisane wielkimi literami i zamienione|
||Metoda pobierająca właściwości `Prop`|`PropGet`|
||Metoda ustawiająca właściwości `Prop`|`PropSet`|
||Akcesor dodający zdarzenie|`Add`|
||Akcesor usuwający zdarzenie|`Remove`|
|**Operator** składa się z dwóch części|`op_name`|`NameOp`|
|Na przykład: + — operator|`op_Add`|`AddOp`|
|Aby uzyskać **operatora konwersji**, dołączany jest typ zwracany.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Gettery i settery indeksatorów** traktuje się podobnie do właściwości. Domyślna nazwa indeksatora to `Item`.
> - **Typ parametru** nazwy są przekształcane i łączone.
> - **Zwracany typ** jest ignorowana, chyba że istnieje dwuznaczność przeciążenia. W przypadku amiguity przeciążenia, typ zwracany jest dołączany na końcu nazwy.

### <a name="parameter-type-naming-conventions"></a>Konwencje nazewnictwa typu parametru

|Biorąc pod uwagę|Dołączany ciąg to...|
|-|-|
|A **typu**`T`|T<br /><br /> Przestrzeń nazw, struktura zagnieżdżona i tiki ogólne, są opuszczane.|
|**Parametr wyjściowy**`out T`|`TOut`|
|A **parametr ref** `ref T`|`TRef`|
|**Typu tablicy**`T[]`|`TArray`|
|A **tablicy wielowymiarowej** typu `T[ , , ]`|`T3`|
|A **wskaźnik** typu `T*`|`TPtr`|
|A **typu ogólnego**`T<R1, ...>`|`TOfR1`|
|A **argument typu ogólnego** `!i` typu `C<TType>`|`Ti`|
|A **argument metody ogólnej** `!!i` metody `M<MMethod>`|`Mi`|
|A **zagnieżdżony typ**`N.T`|`N` jest dołączany, następnie `T`|

### <a name="recursive-rules"></a>Zasady cykliczne

Następujące reguły są stosowane cyklicznie:

- Ponieważ substytuty używają C# wygenerować zestawy pozorne, dowolny znak, który skutkowałby nieprawidłowym C# token jest zmieniany na "_" (podkreślenie).

- Jeśli nazwa wynikowa jest niezgodna z dowolnym elementem członkowskim typu deklarującego, schemat numerowania jest używany przez dołączenie dwóch cyfr licznika, począwszy od 01.

## <a name="see-also"></a>Zobacz także

- [Izolowanie testowanego kodu za pomocą Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
