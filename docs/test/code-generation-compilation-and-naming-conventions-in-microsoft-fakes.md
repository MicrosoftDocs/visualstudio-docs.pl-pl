---
title: 'Microsoft Fakes: Generowanie kodu & kompilacji; konwencje nazewnictwa'
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 155caf50e82f56c1db0b0b0a65a640f252f44063
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589334"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes

W tym artykule omówiono opcje i problemy w generowania i kompilacji kodu podróbki i opisano konwencje nazewnictwa dla fałszywych typów generowanych typów, członków i parametrów.

**Wymagania**

- Visual Studio Enterprise
- Projekt .NET Framework

> [!NOTE]
> Projekty .NET Standard nie są obsługiwane.

## <a name="code-generation-and-compilation"></a>Generowanie i kompilacja kodu

### <a name="configure-code-generation-of-stubs"></a>Konfigurowanie generowania wycinków

Generowanie typów skrótowych jest skonfigurowane w pliku XML z rozszerzeniem pliku *.fakes.* Struktura Podróbki integruje się w procesie kompilacji za pośrednictwem niestandardowych zadań MSBuild i wykrywa te pliki w czasie kompilacji. Generator kodu Fakes kompiluje typy skrótowe do zestawu i dodaje odwołanie do projektu.

Poniższy przykład ilustruje typy skrótowe zdefiniowane w *pliku FileSystem.dll:*

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>
```

### <a name="type-filtering"></a>Filtrowanie typów

Filtry można ustawić w pliku *.fakes,* aby ograniczyć typy, które powinny być wycinkowe. Można dodać nieograniczoną liczbę Clear, Add, Remove elementów w obszarze StubGeneration element do tworzenia listy wybranych typów.

Na przykład następujący plik *.fakes* generuje wycinki dla typów w obszarze System i System.IO przestrzenie nazw, ale wyklucza dowolny typ zawierający "Dojście" w systemie:

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

Ciągi filtru używają prostej gramatyki, aby zdefiniować sposób dopasowywania:

- Filtry są domyślnie niewrażliwe na wielkości liter; filtry wykonać dopasowanie podciąg:

     `el`pasuje do "hello"

- Dodanie `!` na końcu filtru sprawia, że jest to dokładne dopasowanie z uwzględnieniem wielkości liter:

     `el!`nie pasuje do "hello"

     `hello!`pasuje do "hello"

- Dodanie `*` na końcu filtru sprawia, że pasuje do prefiksu ciągu:

     `el*`nie pasuje do "hello"

     `he*`pasuje do "hello"

- Wiele filtrów na liście oddzielonych średnikami jest łączonych jako rozłączenie:

     `el;wo`pasuje do "hello" i "world"

### <a name="stub-concrete-classes-and-virtual-methods"></a>Klasy betonu skrótowego i metody wirtualne

Domyślnie typy skrótowe są generowane dla wszystkich klas nieuszczelnionych. Istnieje możliwość ograniczenia typów skrótowych do klas abstrakcyjnych za pośrednictwem pliku konfiguracyjnego *.fakes:*

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

Generator kodu Podróbki generuje typy podkładki i typy skrótowe dla typów, które są widoczne dla wygenerowanego zestawu Podróbki. Aby wewnętrzne typy shimmed zestawu widoczne podróbki i <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> zestawu testowego, dodać atrybuty do shimmed kod zestawu, który daje wgląd do wygenerowanego zestawu Fakes i zestawu testowego. Oto przykład:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

**Typy wewnętrzne w zestawach o silnie nazwanych nazwach**

Jeśli zestaw shimmed jest silnie nazwany i chcesz uzyskać dostęp do wewnętrznych typów zestawu:

- Zarówno zestaw testowy, jak i zestaw Podróbki muszą być silnie nazwane.

- Dodaj klucze publiczne testu i podróbki zestawu do **InternalsVisibleToAttribute** atrybutów w shimmed zestawów. Oto jak atrybuty przykład w shimmed kod zestawu będzie wyglądać, gdy shimmed zestaw jest silnie nazwany:

    ```csharp
    // FileSystem\AssemblyInfo.cs
    [assembly: InternalsVisibleTo("FileSystem.Fakes",
        PublicKey=<Fakes_assembly_public_key>)]
    [assembly: InternalsVisibleTo("FileSystem.Tests",
        PublicKey=<Test_assembly_public_key>)]
    ```

Jeśli shimmed zestaw jest silnie nazwany, Fakes framework automatycznie silnie podpisuje wygenerowane Fakes zestawu. Musisz mocno podpisać zestaw testowy. Zobacz [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies).

Fakes framework używa tego samego klucza do podpisania wszystkich wygenerowanych zestawów, dzięki czemu można użyć tego fragmentu jako punktu wyjścia, aby dodać **InternalsVisibleTo** atrybut dla zestawu podróbek do kodu zestawu shimmed.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

Można określić inny klucz publiczny dla zestawu Podróbki, taki jak klucz utworzony dla zestawu shimmed, określając pełną ścieżkę do pliku *.snk,* który zawiera klucz alternatywny jako wartość `KeyFile` atrybutu `Fakes` \\ `Compilation` w elemencie pliku *.fakes.* Przykład:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>
```

Następnie należy użyć klucza publicznego alternatywnego pliku *.snk* jako drugiego parametru internalvisibleto atrybut dla fakes zestawu w shimmed kod zestawu:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

W powyższym przykładzie `Alternate_public_key` wartości `Test_assembly_public_key` i mogą być takie same.

### <a name="optimize-build-times"></a>Optymalizacja czasów kompilacji

Kompilacja fałszywych zestawów może znacznie zwiększyć czas kompilacji. Można zminimalizować czas kompilacji, generując fakes zestawy dla .NET zestawy systemowe i zestawy innych firm w oddzielnym scentralizowanym projekcie. Ponieważ takie zestawy rzadko zmieniają się na komputerze, można ponownie użyć wygenerowanych fałszywych zestawów w innych projektach.

Z projektów testów jednostkowych dodaj odwołanie do skompilowanych zestawów Fakes, które są umieszczane w obszarze FakesAssemblies w folderze projektu.

1. Utwórz nową bibliotekę klas z wersją środowiska uruchomieniowego platformy .NET dopasowaną do projektów testowych. Nazwijmy to Fakes.Prebuild. Usuń *plik class1.cs* z projektu, nie jest potrzebny.

2. Dodaj odwołanie do wszystkich zestawów systemowych i innych firm, do których potrzebujesz podróbek.

3. Dodaj plik *.fakes* dla każdego z zestawów i kompilacji.

4. Z projektu testowego

    - Upewnij się, że masz odwołanie do biblioteki DLL środowiska wykonawczego Fakes:

         *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll*

    - Dla każdego zestawu, dla którego utworzono podróbki, dodaj odwołanie do odpowiedniego pliku DLL w folderze *Fakes.Prebuild\FakesAssemblies* projektu.

### <a name="avoid-assembly-name-clashing"></a>Unikaj kolizji nazw zestawu

W środowisku kompilacji zespołu wszystkie dane wyjściowe kompilacji są scalane w jeden katalog. Jeśli wiele projektów używać podróbki, może się zdarzyć, że podróbki zestawów z różnych wersji zastąpić siebie. Na przykład TestProject1 podróbki *mscorlib.dll* z .NET Framework 2.0 i TestProject2 podróbki *mscorlib.dll* dla .NET Framework 4 będzie zarówno wydajność *mscorlib. Fakes.dll* Podróbki montaż.

Aby uniknąć tego problemu, Podróbki należy automatycznie utworzyć wersję kwalifikowanych fakes nazwy zestawów dla odwołań innych niż projekt podczas dodawania *plików .fakes.* Nazwa zestawu Fakes z kwalifikem wersji osadza numer wersji podczas tworzenia nazwy zestawu Podróbki:

Biorąc pod uwagę zespół MyAssembly i wersja 1.2.3.4, nazwa zestawu Podróbki jest MyAssembly.1.2.3.4.Fakes.

Tę wersję można zmienić lub usunąć, edytując atrybut Version elementu Assembly w *pliku .fakes:*

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>
```

## <a name="fakes-naming-conventions"></a>Podróbki konwencji nazewnictwa

### <a name="shim-type-and-stub-type-naming-conventions"></a>Konwencje nazewnictwa typu podkładki i typu skrótowego

**Przestrzenie nazw**

- . Sufiks podróbek jest dodawany do obszaru nazw.

   Na przykład `System.Fakes` obszar nazw zawiera typy podkładek systemowych obszaru nazw.

- Global.Fakes zawiera typ podkładki pustej przestrzeni nazw.

  **Nazwy typów**

- Prefiks podkładki jest dodawany do nazwy typu, aby utworzyć nazwę typu podkładki.

   Na przykład ShimExample jest typem podkładki typu Przykład.

- Prefiks skrótowy jest dodawany do nazwy typu, aby utworzyć nazwę typu skrótowego.

   Na przykład StubIExample jest typem skrótu typu IExample.

  **Typ argumenty i struktury typów zagnieżdżonych**

- Argumenty typu ogólnego są kopiowane.

- Struktura typu zagnieżdżonego jest kopiowana dla typów podkładek.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a>Shim delegować właściwości lub skrótowe pole delegata konwencji

**Podstawowe reguły** nazewnictwa pól, zaczynając od pustej nazwy:

- Nazwa metody jest dołączana.

- Jeśli nazwa metody jest jawną implementacją interfejsu, kropki są usuwane.

- Jeśli metoda jest `Of`ogólna, *n* jest dołączany, gdzie *n* jest liczbą argumentów metody rodzajowej.

  **Specjalne nazwy metod,** takie jak metody ustawiania właściwości lub ustawianie, są traktowane w sposób opisany w poniższej tabeli:

|Jeśli metoda jest...|Przykład|Nazwa metody dołączona|
|-|-|-|
|**Konstruktor**|`.ctor`|`Constructor`|
|**Konstruktor** statyczny|`.cctor`|`StaticConstructor`|
|**Akcesor** o nazwie metody składający się z dwóch części oddzielonych "_" (takich jak metody wyzysku właściwości)|*kind_name* (wspólny przypadek, ale nie egzekwowane przez ECMA)|*NameKind*, gdzie obie części zostały skapitalizowane i zamienione|
||Getter nieruchomości`Prop`|`PropGet`|
||Ustawiacz właściwości`Prop`|`PropSet`|
||Dodatek zdarzeń|`Add`|
||Usuwania zdarzeń|`Remove`|
|**Operator** składający się z dwóch części|`op_name`|`NameOp`|
|Na przykład: + operator|`op_Add`|`AddOp`|
|W przypadku **operatora konwersji**dołączany jest typ zwracany.|`T op_Implicit`|`ImplicitOpT`|

> [!NOTE]
> - **Getters i ustawiacze indeksatorów** są traktowane podobnie do właściwości. Domyślną nazwą indeksatora `Item`jest .
> - Nazwy **typów parametrów** są przekształcane i łączone.
> - **Typ zwracany** jest ignorowany, chyba że istnieje niejednoznaczność przeciążenia. Jeśli istnieje amiguity przeciążenia, typ zwracany jest dołączany na końcu nazwy.

### <a name="parameter-type-naming-conventions"></a>Konwencje nazewnictwa typów parametrów

|Podane|Dołączony ciąg jest...|
|-|-|
|**Typ**`T`|T<br /><br /> Obszar nazw, zagnieżdżona struktura i ogólne tiki są usuwane.|
|**Parametr out**`out T`|`TOut`|
|**Parametr ref**`ref T`|`TRef`|
|**Typ tablicy**`T[]`|`TArray`|
|**Wielowymiarowy** typ tablicy`T[ , , ]`|`T3`|
|Typ **wskaźnika**`T*`|`TPtr`|
|**Typ ogólny**`T<R1, ...>`|`TOfR1`|
|**Ogólny argument** `!i` typu typu`C<TType>`|`Ti`|
|**Argument metody** `!!i` ogólnej metody`M<MMethod>`|`Mi`|
|**Typ zagnieżdżony**`N.T`|`N`jest dołączany, a następnie`T`|

### <a name="recursive-rules"></a>Reguły cykliczne

Następujące reguły są stosowane rekursywnie:

- Ponieważ Podróbki używa C# do generowania fakes zestawów, każdy znak, któryprodukuje nieprawidłowy token C# jest zmieniony do "_" (podkreślenia).

- Jeśli wynikowa nazwa jest zderzająca się z dowolnym elementem członkowskim typu deklarującego, schemat numeracji jest używany przez dołączenie licznika dwucyfrowego, począwszy od 01.

## <a name="see-also"></a>Zobacz też

- [Izolowanie kodu w teście z Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
