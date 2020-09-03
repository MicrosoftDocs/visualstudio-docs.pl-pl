---
title: Konwencje generowania kodu, kompilacji i nazewnictwa w elementach sztucznych firmy Microsoft | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffcab2800168ab6d66426c2e7beb77a158ced1eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851832"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono opcje i problemy związane z generowaniem kodu i kompilacjami oraz opisano konwencje nazewnictwa dla wygenerowanych typów, elementów członkowskich i parametrów.

 **Wymagania**

- Visual Studio Enterprise

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [Generowanie i kompilowanie kodu](#BKMK_Code_generation_and_compilation)

- [Konfigurowanie generowania kodu dla wycinków](#BKMK_Configuring_code_generation_of_stubs) • [Filtrowanie typów](#BKMK_Type_filtering) • [zastępowanie klasami zastępczymi konkretne klasy i metody wirtualne](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [typy wewnętrzne](#BKMK_Internal_types) • [Optymalizacja czasów kompilacji](#BKMK_Optimizing_build_times) • [unikanie kolizji nazw zestawów](#BKMK_Avoiding_assembly_name_clashing)

  [Konwencje nazewnictwa elementów sztucznych](#BKMK_Fakes_naming_conventions)

- [Konwencje nazewnictwa typów i typów podkładki,](#BKMK_Shim_type_and_stub_type_naming_conventions) [Właściwości delegata podkładki lub konwencje nazewnictwa pól delegatów](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) , • konwencje nazewnictwa [typów parametrów](#BKMK_Parameter_type_naming_conventions) • [reguły cykliczne](#BKMK_Recursive_rules)

  [Zasoby zewnętrzne](#BKMK_External_resources)

- [Wskazówki](#BKMK_Guidance)

## <a name="code-generation-and-compilation"></a><a name="BKMK_Code_generation_and_compilation"></a> Generowanie i kompilowanie kodu

### <a name="configuring-code-generation-of-stubs"></a><a name="BKMK_Configuring_code_generation_of_stubs"></a> Konfigurowanie generowania kodu dla wycinków
 Generowanie typów zastępczych jest konfigurowane w pliku XML, który ma rozszerzenie pliku. Struktura sztuczna integruje się w procesie kompilacji za pomocą niestandardowych zadań programu MSBuild i wykrywa te pliki w czasie kompilacji. Generator kodu sztucznego kompiluje typy zastępcze do zestawu i dodaje odwołanie do projektu.

 Poniższy przykład ilustruje typy zastępcze zdefiniowane w FileSystem.dll:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>

```

### <a name="type-filtering"></a><a name="BKMK_Type_filtering"></a> Filtrowanie typów
 Filtry można ustawić w pliku. sztuczne, aby ograniczyć typy, które powinny być użyto metod zastępczych. Można dodać niepowiązaną liczbę elementów Clear, Add, Remove w elemencie StubGeneration, aby skompilować listę wybranych typów.

 Na przykład, plik sztuczny generuje klasy wycinków dla typów w przestrzeni nazw System i System.IO, ale wyklucza dowolny typ zawierający "uchwyt" w systemie:

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

- Dodanie `!` do końca filtru sprawia, że jest to dokładne dopasowanie uwzględniające wielkość liter:

     `el!` nie pasuje do "Hello"

     `hello!` pasuje do "Hello"

- Dodanie `*` do końca filtru spowoduje, że dopasowuje go do prefiksu ciągu:

     `el*` nie pasuje do "Hello"

     `he*` pasuje do "Hello"

- Wiele filtrów na liście rozdzielanej średnikami jest połączone jako rozłączenie:

     `el;wo` Dopasowuje "Hello" i "World"

### <a name="stubbing-concrete-classes-and-virtual-methods"></a><a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Zastępowanie klasami zastępczymi konkretne klasy i metody wirtualne
 Domyślnie typy zastępcze są generowane dla wszystkich niezapieczętowanych klas. Istnieje możliwość ograniczenia typów zastępczych do klas abstrakcyjnych za pomocą pliku konfiguracji elementów sztucznych:

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

### <a name="internal-types"></a><a name="BKMK_Internal_types"></a> Typy wewnętrzne
 Generator kodu sztucznego będzie generować typy podkładek i typy zastępcze dla typów, które są widoczne dla wygenerowanego zestawu elementów sztucznych. Aby zapewnić, że typy wewnętrzne zestawu zastąpionym podkładką były widoczne dla elementów sztucznych i zestawu testowego, Dodaj  <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybuty do kodu zestawu zastąpionym podkładką, który zapewnia widoczność wygenerowanego zestawu elementów sztucznych i zestawu testowego. Oto przykład:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Typy wewnętrzne w zestawach silnie nazwanych**

 Jeśli zestaw zastąpionym podkładką ma silną nazwę i chcesz uzyskać dostęp do wewnętrznych typów zestawu:

- Zestaw testowy i zestaw elementów sztucznych muszą mieć silną nazwę.

- Należy dodać klucze publiczne testu i elementów sztucznych do atrybutów **InternalsVisibleToAttribute** w zestawach zastąpionym podkładką. Oto, jak nasze przykładowe atrybuty kodu zestawu zastąpionym podkładką wyglądać, gdy zestaw zastąpionym podkładką ma silną nazwę:

  ```csharp
  // FileSystem\AssemblyInfo.cs
  [assembly: InternalsVisibleTo("FileSystem.Fakes",
      PublicKey=<Fakes_assembly_public_key>)]
  [assembly: InternalsVisibleTo("FileSystem.Tests",
      PublicKey=<Test_assembly_public_key>)]
  ```

  Jeśli zestaw zastąpionym podkładką ma silną nazwę, struktura sztuczna będzie automatycznie silnie podpisywać wygenerowanego zestawu elementów sztucznych. Musisz mieć silny podpis zestawu testowego. Zobacz [Tworzenie i używanie zestawów o silnych nazwach](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

  Struktura elementów sztucznych używa tego samego klucza do podpisywania wszystkich wygenerowanych zestawów, dlatego można użyć tego fragmentu jako punktu wyjścia do dodania atrybutu **InternalsVisibleTo** dla zestawu elementów sztucznych do kodu zestawu zastąpionym podkładką.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 Możesz określić inny klucz publiczny dla zestawu sztucznego, taki jak klucz utworzony dla zestawu zastąpionym podkładką, określając pełną ścieżkę do pliku **. snk** , który zawiera klucz alternatywny jako `KeyFile` wartość atrybutu w `Fakes` \\ `Compilation` elemencie pliku **.** repliks. Na przykład:

```xml
<-- FileSystem.Fakes.fakes -->
<Fakes ...>
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />
</Fakes>

```

 Następnie należy użyć klucza publicznego alternatywnego pliku **SNK** jako drugiego parametru atrybutu InternalVisibleTo dla zestawu elementów sztucznych w kodzie zestawu zastąpionym podkładką:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes",
    PublicKey=<Alternate_public_key>)]
[assembly: InternalsVisibleTo("FileSystem.Tests",
    PublicKey=<Test_assembly_public_key>)]
```

 W powyższym przykładzie wartości `Alternate_public_key` i `Test_assembly_public_key` mogą być takie same.

### <a name="optimizing-build-times"></a><a name="BKMK_Optimizing_build_times"></a> Optymalizowanie czasów kompilacji
 Kompilacja elementów sztucznych może znacząco zwiększyć czas kompilacji. Możesz zminimalizować czas kompilacji, generując zestawy sztuczne dla zestawów systemu .NET i zestawów innych firm w oddzielnym, scentralizowanym projekcie. Ponieważ takie zestawy rzadko zmieniają się na komputerze, można ponownie użyć wygenerowanych zestawów elementów sztucznych w innych projektach.

 Z projektów testów jednostkowych możesz po prostu przystąpić do skompilowanych zestawów elementów sztucznych umieszczonych pod FakesAssemblies w folderze projektu.

1. Utwórz nową bibliotekę klas z wersją środowiska uruchomieniowego .NET zgodną z projektami testowymi. Wywołajmy go jako fałszywe. prekompilowanie. Usuń plik class1.cs z projektu, niezbędny.

2. Dodaj odwołanie do wszystkich zestawów system i innych firm, dla których potrzebujesz fałszywych informacji.

3. Dodaj plik. sfałszowany dla każdego zestawu i kompilacji.

4. Z projektu testowego

    - Upewnij się, że masz odwołanie do biblioteki DLL środowiska uruchomieniowego elementów sztucznych:

         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll

    - Dla każdego zestawu, który utworzył elementy sztuczne dla, Dodaj odwołanie do odpowiedniego pliku DLL w folderze Prebuild\FakesAssemblies.

### <a name="avoiding-assembly-name-clashing"></a><a name="BKMK_Avoiding_assembly_name_clashing"></a> Unikanie kolizji nazw zestawów
 W środowisku kompilacji zespołu wszystkie dane wyjściowe kompilacji są scalane w pojedynczy katalog. W przypadku wielu projektów z wykorzystaniem elementów sztucznych może się zdarzyć, że elementy sztuczne z różnych wersji zastępują nawzajem. Na przykład, TestProject1 sztuczne mscorlib.dll od .NET Framework 2,0 i TestProject2 sztuczne mscorlib.dll dla .NET Framework 4 byłyby mscorlib.Fakes.dll do nich wynikiem.

 Aby uniknąć tego problemu, elementy sztuczne powinny automatycznie tworzyć kwalifikowane nazwy elementów sztucznych w wersji dla odwołań nienależących do projektu podczas dodawania plików sztucznych. Nazwa zestawu elementów sztucznych z kwalifikowaną wersją osadza numer wersji podczas tworzenia nazwy zestawu elementów sztucznych:

 W przypadku zestawu asemblera i wersji 1.2.3.4, nazwa zestawu elementów sztucznych to asembler. 1.2.3.4. sztuczne.

 Możesz zmienić lub usunąć tę wersję, edytując atrybut Version elementu Assembly w. sztuczne:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>

```

## <a name="fakes-naming-conventions"></a><a name="BKMK_Fakes_naming_conventions"></a> Konwencje nazewnictwa elementów sztucznych

### <a name="shim-type-and-stub-type-naming-conventions"></a><a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Konwencje nazewnictwa typów i typów podkładki
 **Przestrzenie nazw**

- . Sufiks elementów sztucznych jest dodawany do przestrzeni nazw.

   Na przykład `System.Fakes` przestrzeń nazw zawiera typy w przestrzeni nazw System.

- Global. sztuczne zawiera typ podkładki pustej przestrzeni nazw.

  **Nazwy typów**

- Prefiks podkładki jest dodawany do nazwy typu, aby zbudować nazwę typu podkładki.

   Na przykład ShimExample jest typem podkładek typu przykład.

- Prefiks zastępczy jest dodawany do nazwy typu, aby zbudować nazwę typu szczątkowego.

   Na przykład StubIExample jest typem zastępczym typu IExample.

  **Argumenty typu i struktury typów zagnieżdżonych**

- Argumenty typu ogólnego zostały skopiowane.

- Struktura typu zagnieżdżonego jest kopiowana dla typów podkładki.

### <a name="shim-delegate-property-or-stub-delegate-field-naming-conventions"></a><a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Właściwość delegata podkładki lub konwencje nazewnictwa pól delegata
 **Podstawowe reguły** nazewnictwa pól, rozpoczynając od pustej nazwy:

- Nazwa metody jest dołączana.

- Jeśli nazwa metody jest jawną implementacją interfejsu, kropki są usuwane.

- Jeśli metoda jest generyczna, `Of` dołączany jest *n* , gdzie *n* jest liczbą argumentów metody ogólnej.

  **Specjalne nazwy metod** , takie jak metody pobierającej właściwości lub Setters, są traktowane jak opisano w poniższej tabeli.

|Jeśli metoda to...|Przykład|Dołączona nazwa metody|
|-------------------|-------------|--------------------------|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statyczny **Konstruktor**|`.cctor`|`StaticConstructor`|
|Metoda **dostępu** o nazwie metody składająca się z dwóch części oddzielonych znakami "_" (takich jak metody pobierające właściwości)|*kind_name* (przypadek typowy, ale nie wymuszony przez ECMA)|*NameKind*, gdzie obie części są pisane wielkimi literami i wymieniane|
||Metoda pobierająca właściwości `Prop`|`PropGet`|
||Metoda ustawiająca właściwości `Prop`|`PropSet`|
||Rozszerzanie zdarzeń|`Add`|
||Usuwanie zdarzenia|`Remove`|
|**Operator** składający się z dwóch części|`op_name`|`NameOp`|
|Przykład: + — operator|`op_Add`|`AddOp`|
|Dla **operatora konwersji**dołączany jest typ zwracany.|`T op_Implicit`|`ImplicitOpT`|

 **Uwagi**

- **Metody pobierające i metody ustawiające indeksatory** są traktowane podobnie do właściwości. Domyślną nazwą indeksatora jest `Item` .

- Nazwy **typów parametrów** są przekształcane i łączone.

- **Zwracany typ** jest ignorowany, chyba że istnieje niejednoznaczność przeciążenia. W takim przypadku zwracany typ jest dołączany na końcu nazwy

### <a name="parameter-type-naming-conventions"></a><a name="BKMK_Parameter_type_naming_conventions"></a> Konwencje nazewnictwa typów parametrów

|Umieszczone|Dołączony ciąg to...|
|-----------|-------------------------|
|**Typ**`T`|T<br /><br /> Przestrzeń nazw, struktura zagnieżdżona i ogólna Tiki są porzucane.|
|**Parametr out**`out T`|`TOut`|
|**Parametr ref**`ref T`|`TRef`|
|**Typ tablicy**`T[]`|`TArray`|
|Typ **tablicy wielowymiarowej**`T[ , , ]`|`T3`|
|Typ **wskaźnika**`T*`|`TPtr`|
|**Typ ogólny**`T<R1, …>`|`TOfR1`|
|**Argument typu ogólnego** `!i` typu`C<TType>`|`Ti`|
|**Argument metody ogólnej** `!!i` metody`M<MMethod>`|`Mi`|
|**Typ zagnieżdżony**`N.T`|`N` jest dołączany, a następnie `T`|

### <a name="recursive-rules"></a><a name="BKMK_Recursive_rules"></a> Reguły cykliczne
 Następujące reguły są stosowane cyklicznie:

- Ponieważ elementy sztuczne używają języka C# do generowania zestawów elementów sztucznych, każdy znak, który będzie generował nieprawidłowy token C#, jest wyprowadzany do "_" (podkreślenie).

- Jeśli wynikiem występuje konflikt nazw z dowolnym elementem członkowskim typu deklarującego, schemat numeracji jest używany przez dołączenie dwucyfrowego licznika, rozpoczynając od 01.

## <a name="external-resources"></a><a name="BKMK_External_resources"></a> Zasoby zewnętrzne

### <a name="guidance"></a><a name="BKMK_Guidance"></a> Informator
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://msdn.microsoft.com/library/jj159340.aspx)

## <a name="see-also"></a>Zobacz też
 [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
