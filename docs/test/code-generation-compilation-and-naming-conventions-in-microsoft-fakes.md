---
title: 'Sztuczne firmy Microsoft: generowanie kodu kompilacji & Konwencje nazewnictwa'
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: e29b0b05b836dd4072b704bfd48cfb85cde50927
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665248"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes

W tym artykule omówiono opcje i problemy związane z generowaniem kodu i kompilacjami oraz opisano konwencje nazewnictwa dla typów wygenerowanych, elementów członkowskich i parametrów.

**Requirements**

- Visual Studio Enterprise
- Projekt .NET Framework

> [!NOTE]
> Projekty .NET Standard nie są obsługiwane.

## <a name="code-generation-and-compilation"></a>Generowanie i kompilowanie kodu

### <a name="configure-code-generation-of-stubs"></a>Konfigurowanie generowania kodu dla wycinków

Generowanie typów zastępczych jest konfigurowane w pliku XML, który ma rozszerzenie pliku *.* Struktura sztuczna integruje się w procesie kompilacji za pomocą niestandardowych zadań programu MSBuild i wykrywa te pliki w czasie kompilacji. Generator kodu sztucznego kompiluje typy zastępcze do zestawu i dodaje odwołanie do projektu.

Poniższy przykład ilustruje typy zastępcze zdefiniowane w *systemie plików. dll*:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtrowanie typów

Filtry można ustawić w pliku *.* sztuczne, aby ograniczyć typy, które powinny być użyto metod zastępczych. Można dodać niepowiązaną liczbę elementów Clear, Add, Remove w elemencie StubGeneration, aby skompilować listę wybranych typów.

Na przykład, poniższe *.* elementy sztuczne generują wycinki dla typów w przestrzeni nazw system i system.IO, ale nie zawierają żadnego typu zawierającego "dojście" w systemie:

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

Ciągi filtru używają prostej gramatyki do definiowania sposobu, w jaki należy wykonać dopasowanie:

- Domyślnie w filtrach jest rozróżniana wielkość liter. Filtry wykonują Dopasowywanie podciągów:

     `el` pasuje do "Hello"

- Dodanie `!` na koniec filtru sprawia, że jest to precyzyjne dopasowanie uwzględniające wielkość liter:

     `el!` nie pasuje do "Hello"

     `hello!` pasuje do "Hello"

- Dodanie `*` na koniec filtru sprawia, że pasuje do prefiksu ciągu:

     `el*` nie pasuje do "Hello"

     `he*` pasuje do "Hello"

- Wiele filtrów na liście rozdzielanej średnikami jest połączone jako rozłączenie:

     `el;wo` pasuje do "Hello" i "World"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Klasy konkretnych klas zastępczych i metody wirtualne

Domyślnie typy zastępcze są generowane dla wszystkich niezapieczętowanych klas. Istnieje możliwość ograniczenia typów zastępczych do klas abstrakcyjnych za pomocą pliku *konfiguracji elementów* sztucznych:

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

Generator kodu sztucznego generuje typy podkładek i typy zastępcze dla typów, które są widoczne dla wygenerowanego zestawu elementów sztucznych. Aby zapewnić, że typy wewnętrzne zestawu zastąpionym podkładką były widoczne dla elementów sztucznych i zestawu testowego, Dodaj <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybuty do kodu zestawu zastąpionym podkładką, który zapewnia widoczność wygenerowanego zestawu elementów sztucznych i zestawu testowego. Oto przykład:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Typy wewnętrzne w zestawach silnie nazwanych**

Jeśli zestaw zastąpionym podkładką ma silną nazwę i chcesz uzyskać dostęp do wewnętrznych typów zestawu:

- Zestaw testowy i zestaw elementów sztucznych muszą mieć silną nazwę.

- Dodaj klucze publiczne testu i elementów sztucznych do atrybutów **InternalsVisibleToAttribute** w zestawach zastąpionym podkładką. Poniżej przedstawiono sposób, w jaki przykładowe atrybuty kodu zestawu zastąpionym podkładką będą wyglądały, gdy zestaw zastąpionym podkładką ma silną nazwę:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Jeśli zestaw zastąpionym podkładką ma silną nazwę, struktura sztuczna automatycznie silnie naśladuje wygenerowanego zestawu elementów sztucznych. Musisz mieć silny podpis zestawu testowego. Zobacz [zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies).

Struktura elementów sztucznych używa tego samego klucza do podpisywania wszystkich wygenerowanych zestawów, dlatego można użyć tego fragmentu jako punktu wyjścia do dodania atrybutu **InternalsVisibleTo** dla zestawu elementów sztucznych do kodu zestawu zastąpionym podkładką.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Możesz określić inny klucz publiczny dla zestawu elementów sztucznych, taki jak klucz utworzony dla zestawu zastąpionym podkładką, określając pełną ścieżkę do pliku *. snk* , który zawiera klucz alternatywny jako wartość atrybutu `KeyFile` w \\ `Fakes` @no__t_ 4 element pliku *.* Na przykład:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Następnie należy użyć klucza publicznego alternatywnego pliku *SNK* jako drugiego parametru atrybutu InternalVisibleTo dla zestawu elementów sztucznych w kodzie zestawu zastąpionym podkładką:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

W powyższym przykładzie wartości `Alternate_public_key` i `Test_assembly_public_key` mogą być takie same.

### <a name="optimize-build-times"></a>Optymalizuj czasy kompilacji

Kompilacja elementów sztucznych może znacząco zwiększyć czas kompilacji. Możesz zminimalizować czas kompilacji, generując zestawy sztuczne dla zestawów systemu .NET i zestawów innych firm w oddzielnym, scentralizowanym projekcie. Ponieważ takie zestawy rzadko zmieniają się na komputerze, można ponownie użyć wygenerowanych zestawów elementów sztucznych w innych projektach.

Z projektów testów jednostkowych Dodaj odwołanie do skompilowanych zestawów elementów sztucznych, które są umieszczane w obszarze FakesAssemblies w folderze projektu.

1. Utwórz nową bibliotekę klas z wersją środowiska uruchomieniowego .NET zgodną z projektami testowymi. Wywołajmy go jako fałszywe. prekompilowanie. Usuń plik *Class1.cs* z projektu, niezbędny.

2. Dodaj odwołanie do wszystkich zestawów system i innych firm, dla których potrzebujesz fałszywych informacji.

3. Dodaj plik *. sfałszowany* dla każdego zestawu i kompilacji.

4. Z projektu testowego

    - Upewnij się, że masz odwołanie do biblioteki DLL środowiska uruchomieniowego elementów sztucznych:

         *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Dla każdego zestawu, który utworzył elementy sztuczne dla, Dodaj odwołanie do odpowiedniego pliku DLL w folderze *Prebuild\FakesAssemblies.*

### <a name="avoid-assembly-name-clashing"></a>Unikaj kolizji nazw zestawów

W środowisku kompilacji zespołu wszystkie dane wyjściowe kompilacji są scalane w pojedynczy katalog. Jeśli wiele projektów korzysta z elementów sztucznych, może się zdarzyć, że elementy sztuczne z różnych wersji zastępują siebie nawzajem. Na przykład TestProject1 sztuczne *biblioteki mscorlib. dll* z .NET Framework 2,0 i TestProject2, które są sztuczne *mscorlib. dll* dla .NET Framework 4, byłyby do *biblioteki mscorlib.* Elementy sztuczne. dll.

Aby uniknąć tego problemu, elementy sztuczne powinny automatycznie tworzyć kwalifikowane nazwy elementów sztucznych w wersji dla odwołań nienależących do *projektu podczas dodawania plików* sztucznych. Nazwa zestawu elementów sztucznych z kwalifikowaną wersją osadza numer wersji podczas tworzenia nazwy zestawu elementów sztucznych:

W przypadku zestawu asemblera i wersji 1.2.3.4, nazwa zestawu elementów sztucznych to asembler. 1.2.3.4. sztuczne.

Możesz zmienić lub usunąć tę wersję, edytując atrybut Version elementu Assembly w *.* sztuczne:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Konwencje nazewnictwa elementów sztucznych

### <a name="shim-type-and-stub-type-naming-conventions"></a>Konwencje nazewnictwa typów i typów podkładki

**Przestrzenie nazw**

- . Sufiks elementów sztucznych jest dodawany do przestrzeni nazw.

   Na przykład `System.Fakes` przestrzeń nazw zawiera typy podkładki przestrzeni nazw System.

- Global. sztuczne zawiera typ podkładki pustej przestrzeni nazw.

  **Nazwy typów**

- Prefiks podkładki jest dodawany do nazwy typu, aby zbudować nazwę typu podkładki.

   Na przykład ShimExample jest typem podkładek typu przykład.

- Prefiks zastępczy jest dodawany do nazwy typu, aby zbudować nazwę typu szczątkowego.

   Na przykład StubIExample jest typem zastępczym typu IExample.

  **Argumenty typu i struktury typów zagnieżdżonych**

- Argumenty typu ogólnego zostały skopiowane.

- Struktura typu zagnieżdżonego jest kopiowana dla typów podkładki.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Właściwość delegata podkładki lub konwencje nazewnictwa pól delegata

**Podstawowe reguły** nazewnictwa pól, rozpoczynając od pustej nazwy:

- Nazwa metody jest dołączana.

- Jeśli nazwa metody jest jawną implementacją interfejsu, kropki są usuwane.

- Jeśli metoda jest ogólna, dołączany jest `Of`*n* , gdzie *n* jest liczbą argumentów metody ogólnej.

  **Specjalne nazwy metod** , takie jak metody pobierającej właściwości lub Setters, są traktowane jak opisano w poniższej tabeli:

|Jeśli metoda to...|Przykład|Dołączona nazwa metody|
|-|-|-|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statyczny **Konstruktor**|`.cctor`|`StaticConstructor`|
|Metoda **dostępu** o nazwie metody składająca się z dwóch części oddzielonych znakami "_" (takich jak metody pobierające właściwości)|*kind_name* (przypadek typowy, ale nie wymuszony przez ECMA)|*NameKind*, gdzie obie części są pisane wielkimi literami i wymieniane|
||Metoda pobierająca `Prop` właściwości|`PropGet`|
||Metoda ustawiająca `Prop` właściwości|`PropSet`|
||Rozszerzanie zdarzeń|`Add`|
||Usuwanie zdarzenia|`Remove`|
|**Operator** składający się z dwóch części|`op_name`|`NameOp`|
|Przykład: + — operator|`op_Add`|`AddOp`|
|Dla **operatora konwersji**dołączany jest typ zwracany.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Metody pobierające i metody ustawiające indeksatory** są traktowane podobnie do właściwości. Domyślna nazwa indeksatora jest `Item`.
> - Nazwy **typów parametrów** są przekształcane i łączone.
> - **Zwracany typ** jest ignorowany, chyba że istnieje niejednoznaczność przeciążenia. Jeśli istnieje amiguity przeciążenia, zwracany typ jest dołączany na końcu nazwy.

### <a name="parameter-type-naming-conventions"></a>Konwencje nazewnictwa typów parametrów

|Umieszczone|Dołączony ciąg to...|
|-|-|
|**Typ** `T`|T<br /><br /> Przestrzeń nazw, struktura zagnieżdżona i ogólna Tiki są porzucane.|
|@No__t_1 **parametru out**|`TOut`|
|**Parametr ref** `ref T`|`TRef`|
|**Typ tablicy** `T[]`|`TArray`|
|Typ **tablicy wielowymiarowej** `T[ , , ]`|`T3`|
|Typ **wskaźnika** `T*`|`TPtr`|
|**Typ ogólny** `T<R1, ...>`|`TOfR1`|
|**Argument typu ogólnego** `!i` typu `C<TType>`|`Ti`|
|**Argument metody ogólnej** `!!i` metody `M<MMethod>`|`Mi`|
|**Zagnieżdżony typ** `N.T`|`N` jest dołączany, a następnie `T`|

### <a name="recursive-rules"></a>Reguły cykliczne

Następujące reguły są stosowane cyklicznie:

- Ponieważ elementy sztuczne C# używają do wygenerowania zestawów elementów sztucznych, każdy znak, który będzie C# generował nieprawidłowy token, zostanie zmieniony na "_" (podkreślenie).

- Jeśli wynikiem występuje konflikt nazw z dowolnym elementem członkowskim typu deklarującego, schemat numeracji jest używany przez dołączenie dwucyfrowego licznika, rozpoczynając od 01.

## <a name="see-also"></a>Zobacz także

- [Izolowanie testowanego kodu za pomocą elementów sztucznych firmy Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)
