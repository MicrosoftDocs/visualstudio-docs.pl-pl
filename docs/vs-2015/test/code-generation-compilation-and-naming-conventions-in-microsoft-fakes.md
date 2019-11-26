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
ms.openlocfilehash: 6ff1d953dc853beba8ef836b1eab03140ee0b1e0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300393"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono opcje i problemy związane z generowaniem kodu i kompilacjami oraz opisano konwencje nazewnictwa dla wygenerowanych typów, elementów członkowskich i parametrów.

 **Requirements**

- Visual Studio Enterprise

## <a name="BKMK_In_this_topic"></a>W tym temacie
 [Generowanie i kompilowanie kodu](#BKMK_Code_generation_and_compilation)

- [Konfigurowanie generowania kodu dla wycinków](#BKMK_Configuring_code_generation_of_stubs) • [Filtrowanie typów](#BKMK_Type_filtering) • [zastępowanie klasami zastępczymi konkretne klasy i metody wirtualne](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [typy wewnętrzne](#BKMK_Internal_types) • [Optymalizacja czasów kompilacji](#BKMK_Optimizing_build_times) • [unikanie kolizji nazw zestawów](#BKMK_Avoiding_assembly_name_clashing)

  [Konwencje nazewnictwa elementów sztucznych](#BKMK_Fakes_naming_conventions)

- [Konwencje nazewnictwa typów i typów podkładki,](#BKMK_Shim_type_and_stub_type_naming_conventions) [Właściwości delegata podkładki lub konwencje nazewnictwa pól delegatów](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) , • konwencje nazewnictwa [typów parametrów](#BKMK_Parameter_type_naming_conventions) • [reguły cykliczne](#BKMK_Recursive_rules)

  [Zasoby zewnętrzne](#BKMK_External_resources)

- [Wskazówki](#BKMK_Guidance)

## <a name="BKMK_Code_generation_and_compilation"></a>Generowanie i kompilowanie kodu

### <a name="BKMK_Configuring_code_generation_of_stubs"></a>Konfigurowanie generowania kodu dla wycinków
 Generowanie typów zastępczych jest konfigurowane w pliku XML, który ma rozszerzenie pliku. Fakes framework integruje się w procesie kompilacji przez własne zadania MSBuild i wykrywa te pliki w czasie kompilacji. Generator kodu pozornego kompiluje typy namiastek w zestaw i dodaje odwołanie do projektu.

 Poniższy przykład ilustruje typy zastępcze zdefiniowane w systemie plików. dll:

```xml
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">
    <Assembly Name="FileSystem"/>
</Fakes>

```

### <a name="BKMK_Type_filtering"></a>Filtrowanie typów
 Filtry można ustawić w pliku. sztuczne, aby ograniczyć typy, które powinny być użyto metod zastępczych. Możesz dodać nieograniczoną liczbę elementów Clear, Add, Remove elementów elementu StubGeneration, aby zbudować listę wybranych typów.

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

 Ciągi filtrów używają prostej gramatyki do zdefiniowania, jak dopasowywania powinna być podejmowana:

- Filtry domyślnie wielkość liter; filtry dopasowują podciąg:

     `el` pasuje do "Hello"

- Dodanie `!` na koniec filtru sprawia, że jest to precyzyjne dopasowanie uwzględniające wielkość liter:

     `el!` nie pasuje do "Hello"

     `hello!` pasuje do "Hello"

- Dodanie `*` na koniec filtru spowoduje, że pasuje do prefiksu ciągu:

     `el*` nie pasuje do "Hello"

     `he*` pasuje do "Hello"

- Wiele filtrów na rozdzielonej średnikami liście zostanie połączonych jako alternatywa:

     `el;wo` pasuje do "Hello" i "World"

### <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a>Zastępowanie klasami zastępczymi konkretne klasy i metody wirtualne
 Domyślnie typy namiastki są generowane dla wszystkich niezamkniętych klas. Istnieje możliwość ograniczenia typów zastępczych do klas abstrakcyjnych za pomocą pliku konfiguracji elementów sztucznych:

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

### <a name="BKMK_Internal_types"></a>Typy wewnętrzne
 Generator kodu sztucznego będzie generować typy podkładek i typy zastępcze dla typów, które są widoczne dla wygenerowanego zestawu elementów sztucznych. Aby zapewnić, że typy wewnętrzne zestawu zastąpionym podkładką były widoczne dla elementów sztucznych i zestawu testowego, Dodaj <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybuty do kodu zestawu zastąpionym podkładką, który zapewnia widoczność wygenerowanego zestawu elementów sztucznych i zestawu testowego. Oto przykład:

```csharp
// FileSystem\AssemblyInfo.cs
[assembly: InternalsVisibleTo("FileSystem.Fakes")]
[assembly: InternalsVisibleTo("FileSystem.Tests")]
```

 **Typy wewnętrzne w zestawach silnie nazwanych**

 Jeśli zestaw zastąpionym podkładką ma silną nazwę i chcesz uzyskać dostęp do wewnętrznych typów zestawu:

- Zarówno zestaw testowy i zestaw Pozorowany muszą posiadać silne nazwy.

- Należy dodać klucze publiczne testu i elementów sztucznych do atrybutów **InternalsVisibleToAttribute** w zestawach zastąpionym podkładką. Oto, jak nasze przykładowe atrybuty kodu zestawu zastąpionym podkładką wyglądać, gdy zestaw zastąpionym podkładką ma silną nazwę:

  ```csharp
  // FileSystem\AssemblyInfo.cs
  [assembly: InternalsVisibleTo("FileSystem.Fakes",
      PublicKey=<Fakes_assembly_public_key>)]
  [assembly: InternalsVisibleTo("FileSystem.Tests",
      PublicKey=<Test_assembly_public_key>)]
  ```

  Jeśli zestaw zastąpionym podkładką ma silną nazwę, struktura sztuczna będzie automatycznie silnie podpisywać wygenerowanego zestawu elementów sztucznych. Masz silny podpis zestawu testowego. Zobacz [Tworzenie i używanie zestawów o silnych nazwach](https://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).

  Struktura elementów sztucznych używa tego samego klucza do podpisywania wszystkich wygenerowanych zestawów, dlatego można użyć tego fragmentu jako punktu wyjścia do dodania atrybutu **InternalsVisibleTo** dla zestawu elementów sztucznych do kodu zestawu zastąpionym podkładką.

```csharp
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]
```

 Możesz określić inny klucz publiczny dla zestawu elementów sztucznych, taki jak klucz utworzony dla zestawu zastąpionym podkładką, określając pełną ścieżkę do pliku **. snk** , który zawiera klucz alternatywny jako wartość atrybutu `KeyFile` w `Fakes`\\`Compilation` elementu **.** Na przykład:

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

### <a name="BKMK_Optimizing_build_times"></a>Optymalizowanie czasów kompilacji
 Kompilacja zestawów pozornych może znacznie zwiększyć czas kompilacji. Generując zestawy pozorne dla zestawów .NET System i zestawów innych firm w osobnym scentralizowanym projekcie, można zminimalizować czas kompilacji. Ponieważ takie zestawy rzadko się zmieniają, można użyć ponownie wygenerowanych zestawów pozornych w innych projektach.

 Z projektów testów jednostkowych możesz po prostu przystąpić do skompilowanych zestawów elementów sztucznych umieszczonych pod FakesAssemblies w folderze projektu.

1. Utwórz nową bibliotekę klas z wersją środowiska uruchomieniowego .NET dopasowania Twoich projektów testów. Wywołajmy go jako fałszywe. prekompilowanie. Usuń plik class1.cs z projektu, niezbędny.

2. Dodaj odwołanie do wszystkich systemowych i zestawów innych firm, których potrzebujesz substytutów.

3. Dodaj plik. sfałszowany dla każdego zestawu i kompilacji.

4. Z projektu testów

    - Upewnij się, że masz odwołanie do środowiska uruchomieniowego podrobionych DLL:

         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll

    - Dla każdego zestawu, który utworzył elementy sztuczne dla, Dodaj odwołanie do odpowiedniego pliku DLL w folderze Prebuild\FakesAssemblies.

### <a name="BKMK_Avoiding_assembly_name_clashing"></a>Unikanie kolizji nazw zestawów
 W środowisku kompilacji zespołowej wszystkie dane wyjściowe kompilacji są scalane w jednym katalogu. W przypadku wielu projektów z wykorzystaniem elementów sztucznych może się zdarzyć, że elementy sztuczne z różnych wersji zastępują nawzajem. Na przykład TestProject1 sztuczne biblioteki mscorlib. dll z .NET Framework 2,0 i TestProject2, które są sztuczne mscorlib. dll dla .NET Framework 4, byłyby do biblioteki mscorlib. Elementy sztuczne. dll.

 Aby uniknąć tego problemu, elementy sztuczne powinny automatycznie tworzyć kwalifikowane nazwy elementów sztucznych w wersji dla odwołań nienależących do projektu podczas dodawania plików sztucznych. Nazwa zestawu Pozorowanego wersją kwalifikowaną dołącza numer wersji, podczas tworzenia nazwy zestawu elementów sztucznych:

 Biorąc pod uwagę zestaw MyAssembly i wersję 1.2.3.4 Nazwa zestawu Pozorowanego to MyAssembly.1.2.3.4.Fakes.

 Możesz zmienić lub usunąć tę wersję, edytując atrybut Version elementu Assembly w. sztuczne:

```xml
attribute of the Assembly element in the .fakes:
<Fakes ...>
  <Assembly Name="MyAssembly" Version="1.2.3.4" />
  ...
</Fakes>

```

## <a name="BKMK_Fakes_naming_conventions"></a>Konwencje nazewnictwa elementów sztucznych

### <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a>Konwencje nazewnictwa typów i typów podkładki
 **Przestrzenie nazw**

- . Substytuty sufiks jest dodawany do przestrzeni nazw.

   Na przykład `System.Fakes` przestrzeń nazw zawiera typy podkładki przestrzeni nazw System.

- Global.Fakes zawiera typ pustej przestrzeni nazw.

  **Nazwy typów**

- Przedrostek shim jest dodawany do nazwy typu, aby zbudować nazwę typu zastępczego.

   Na przykład ShimExample jest typem podkładki typu Example.

- Przedrostek stub jest dodawany do nazwy typu, aby zbudować nazwę typu namiastki.

   Na przykład StubIExample jest typem wycinka typu IExample.

  **Argumenty typu i struktury typów zagnieżdżonych**

- Argumenty typu ogólnego są kopiowane.

- Struktura typów zagnieżdżonych jest kopiowana dla typów zastępczych.

### <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a>Właściwość delegata podkładki lub konwencje nazewnictwa pól delegata
 **Podstawowe reguły** nazewnictwa pól, rozpoczynając od pustej nazwy:

- Nazwa metody jest dołączana.

- Jeśli nazwa metody jest jawną implementacją interfejsu, kropki są usuwane.

- Jeśli metoda jest ogólna, dołączany jest `Of`*n* , gdzie *n* jest liczbą argumentów metody ogólnej.

  **Specjalne nazwy metod** , takie jak metody pobierającej właściwości lub Setters, są traktowane jak opisano w poniższej tabeli.

|Jeśli metoda to...|Przykład|Dołączona nazwa metody|
|-------------------|-------------|--------------------------|
|**Konstruktor**|`.ctor`|`Constructor`|
|Statyczny **Konstruktor**|`.cctor`|`StaticConstructor`|
|Metoda **dostępu** o nazwie metody składająca się z dwóch części oddzielonych znakami "_" (takich jak metody pobierające właściwości)|*kind_name* (przypadek typowy, ale nie wymuszony przez ECMA)|*NameKind*, gdzie obie części są pisane wielkimi literami i wymieniane|
||Metoda pobierająca `Prop` właściwości|`PropGet`|
||Metoda ustawiająca `Prop` właściwości|`PropSet`|
||Akcesor dodający zdarzenie|`Add`|
||Akcesor usuwający zdarzenie|`Remove`|
|**Operator** składający się z dwóch części|`op_name`|`NameOp`|
|Na przykład: + — operator|`op_Add`|`AddOp`|
|Dla **operatora konwersji**dołączany jest typ zwracany.|`T op_Implicit`|`ImplicitOpT`|

 **Uwagi**

- **Metody pobierające i metody ustawiające indeksatory** są traktowane podobnie do właściwości. Domyślna nazwa indeksatora jest `Item`.

- Nazwy **typów parametrów** są przekształcane i łączone.

- **Zwracany typ** jest ignorowany, chyba że istnieje niejednoznaczność przeciążenia. W takim przypadku zwracany typ jest dołączany na końcu nazwy

### <a name="BKMK_Parameter_type_naming_conventions"></a>Konwencje nazewnictwa typów parametrów

|Biorąc pod uwagę|Dołączony ciąg to...|
|-----------|-------------------------|
|**Typ**`T`|T<br /><br /> Przestrzeń nazw, struktura zagnieżdżona i tiki ogólne, są opuszczane.|
|`out T` **parametru out**|`TOut`|
|**Parametr ref** `ref T`|`TRef`|
|**Typ tablicy**`T[]`|`TArray`|
|Typ **tablicy wielowymiarowej** `T[ , , ]`|`T3`|
|Typ **wskaźnika** `T*`|`TPtr`|
|**Typ ogólny**`T<R1, …>`|`TOfR1`|
|**Argument typu ogólnego**`!i` typu `C<TType>`|`Ti`|
|**Argument metody ogólnej**`!!i` metody `M<MMethod>`|`Mi`|
|**Zagnieżdżony typ**`N.T`|`N` jest dołączany, a następnie `T`|

### <a name="BKMK_Recursive_rules"></a>Reguły cykliczne
 Następujące reguły są stosowane cyklicznie:

- Ponieważ substytuty używają C# wygenerować zestawy pozorne, dowolny znak, który skutkowałby nieprawidłowym C# token jest zmieniany na "_" (podkreślenie).

- Jeśli nazwa wynikowa jest niezgodna z dowolnym elementem członkowskim typu deklarującego, schemat numerowania jest używany przez dołączenie dwóch cyfr licznika, począwszy od 01.

## <a name="BKMK_External_resources"></a>Zasoby zewnętrzne

### <a name="BKMK_Guidance"></a>Informator
 [Testowanie w celu ciągłego dostarczania za pomocą programu Visual Studio 2012 — Rozdział 2: testowanie jednostkowe: testowanie wewnątrz](https://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Zobacz też
 [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
