---
title: Generowanie kodu, kompilacji i konwencje nazewnictwa w Microsoft Fakes | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 20221de4-2a9e-4787-b99a-b5855bb90872
caps.latest.revision: 18
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70392f50ecd13539012672bf71900c30845af734
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783374"
---
# <a name="code-generation-compilation-and-naming-conventions-in-microsoft-fakes"></a>Konwencje dotyczące generowania, kompilowania i nazywania w Microsoft Fakes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono opcje i kwestie w substytuty Generowanie i kompilacja kodu i opisano konwencje nazewnictwa dla typów, elementów członkowskich i parametrów pozornie wygenerowanych.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Generowanie i kompilacja kodu](#BKMK_Code_generation_and_compilation)  
  
- [Konfigurowanie generowania kodu odcinków](#BKMK_Configuring_code_generation_of_stubs) • [Filtrowanie typów](#BKMK_Type_filtering) • [tworzenie namiastek dla klas konkretnych i metod wirtualnych](#BKMK_Stubbing_concrete_classes_and_virtual_methods) • [typy wewnętrzne](#BKMK_Internal_types) • [ Optymalizacja tworzenia razy](#BKMK_Optimizing_build_times) • [unikanie konfliktu nazw zestawów](#BKMK_Avoiding_assembly_name_clashing)  
  
  [Konwencje nazewnictwa substytutów](#BKMK_Fakes_naming_conventions)  
  
- [Typ podkładek i klas zastępczych wpisz konwencji nazewnictwa](#BKMK_Shim_type_and_stub_type_naming_conventions) • [podkładki delegata właściwości ani klas zastępczych delegata pola konwencji nazewnictwa](#BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions) • [konwencje nazewnictwa typu parametru](#BKMK_Parameter_type_naming_conventions) • [cykliczne reguły](#BKMK_Recursive_rules)  
  
  [Zasoby zewnętrzne](#BKMK_External_resources)  
  
- [Wskazówki](#BKMK_Guidance)  
  
##  <a name="BKMK_Code_generation_and_compilation"></a> Generowanie i kompilacja kodu  
  
###  <a name="BKMK_Configuring_code_generation_of_stubs"></a> Konfigurowanie generowania kodu odcinków  
 Generowanie typów namiastek jest skonfigurowany w pliku XML, który ma rozszerzenie pliku .fakes. Fakes framework integruje się w procesie kompilacji przez własne zadania MSBuild i wykrywa te pliki w czasie kompilacji. Generator kodu pozornego kompiluje typy namiastek w zestaw i dodaje odwołanie do projektu.  
  
 Poniższy przykład ilustruje typy namiastki zdefiniowane w FileSystem.dll:  
  
```xml  
<Fakes xmlns="http://schemas.microsoft.com/fakes/2011/">  
    <Assembly Name="FileSystem"/>  
</Fakes>  
  
```  
  
###  <a name="BKMK_Type_filtering"></a> Filtrowanie typów  
 W pliku .fakes można ustawić filtry w celu ograniczenia typów, które mają być generowane namiastki. Możesz dodać nieograniczoną liczbę elementów Clear, Add, Remove elementów elementu StubGeneration, aby zbudować listę wybranych typów.  
  
 Na przykład ten plik .fakes generuje namiastki dla typów w przestrzeni nazw System i System.IO, ale nie obejmuje wszystkich typów zawierających "Handle" w systemie:  
  
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
  
-   Filtry domyślnie wielkość liter; filtry dopasowują podciąg:  
  
     `el` pasuje do "hello"  
  
-   Dodawanie `!` do końca filtru uczyni go dokładne dopasowanie uwzględniające:  
  
     `el!` nie pasuje do "hello"  
  
     `hello!` pasuje do "hello"  
  
-   Dodawanie `*` do końca filtru uczyni go pasującym do przedrostka ciągu:  
  
     `el*` nie pasuje do "hello"  
  
     `he*` pasuje do "hello"  
  
-   Wiele filtrów na rozdzielonej średnikami liście zostanie połączonych jako alternatywa:  
  
     `el;wo` pasuje do "hello" i "world"  
  
###  <a name="BKMK_Stubbing_concrete_classes_and_virtual_methods"></a> Tworzenie namiastek dla klas konkretnych i metod wirtualnych  
 Domyślnie typy namiastki są generowane dla wszystkich niezamkniętych klas. Istnieje możliwość ograniczenie typów namiastki do konkretnych klas abstrakcyjnych za pomocą pliku konfiguracji .fakes:  
  
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
  
###  <a name="BKMK_Internal_types"></a> Typy wewnętrzne  
 Generator kodu pozornego wygeneruje typy zastępcze i typy namiastki dla typów, które są widoczne dla wygenerowanego zestawu pozornego. Aby typy wewnętrzne zestawu typu shim były widoczne dla elementów sztucznych i zestaw testowy, należy dodać <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybuty do kodu zestawu typu shim, który zwiększa widoczność w wygenerowanych zestawach fakes i zestawu testowego. Oto przykład:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes")]  
[assembly: InternalsVisibleTo("FileSystem.Tests")]  
```  
  
 **Typy wewnętrzne w zestawach o silnej nazwie**  
  
 Jeśli zestawu typu shim ma silnej nazwy i mają dostęp do wewnętrznych typów zestawu:  
  
- Zarówno zestaw testowy i zestaw Pozorowany muszą posiadać silne nazwy.  
  
- Należy dodać klucze publiczne testu i podrobionego zestawu do **InternalsVisibleToAttribute** atrybutów w zestawach typu shim. Poniżej przedstawiono, jak nasze przykładowe atrybuty w kodzie zestawu shimmed będzie wyglądać po zestawu typu shim ma silnej nazwy:  
  
  ```csharp  
  // FileSystem\AssemblyInfo.cs  
  [assembly: InternalsVisibleTo("FileSystem.Fakes",  
      PublicKey=<Fakes_assembly_public_key>)]  
  [assembly: InternalsVisibleTo("FileSystem.Tests",  
      PublicKey=<Test_assembly_public_key>)]  
  ```  
  
  Jeśli zestawu typu shim ma silnej nazwy, Fakes framework automatycznie podpisze wygenerowanego zestawu pozornego. Masz silny podpis zestawu testowego. Zobacz [tworzenie i używanie zestawów o silnych nazwach](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
  Struktura Fakes używa tego samego klucza do podpisywania wszystkich generowanych zestawów, więc ten fragment kodu jako punktu wyjścia służy do dodawania **InternalsVisibleTo** atrybutu zestawu pozorowanego w kodzie zestawu typu shim.  
  
```csharp  
[assembly: InternalsVisibleTo("FileSystem.Fakes, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e92decb949446f688ab9f6973436c535bf50acd1fd580495aae3f875aa4e4f663ca77908c63b7f0996977cb98fcfdb35e05aa2c842002703cad835473caac5ef14107e3a7fae01120a96558785f48319f66daabc862872b2c53f5ac11fa335c0165e202b4c011334c7bc8f4c4e570cf255190f4e3e2cbc9137ca57cb687947bc")]  
```  
  
 Można określić inny klucz publiczny zestawu Pozorowanego, taki jak klucz utworzony dla zestawu typu shim, podając pełną ścieżkę do **.snk** pliku, który zawiera klucz alternatywny jako `KeyFile` wartość atrybutu `Fakes` \\ `Compilation` elementu **.fakes** pliku. Na przykład:  
  
```xml  
<-- FileSystem.Fakes.fakes -->  
<Fakes ...>  
  <Compilation KeyFile="full_path_to_the_alternate_snk_file" />  
</Fakes>  
  
```  
  
 Następnie trzeba użyć klucza publicznego alternatywna **.snk** pliku jako drugiego parametru atrybutu InternalVisibleTo do zestawu Pozorowanego w kodzie zestawu shimmed:  
  
```csharp  
// FileSystem\AssemblyInfo.cs  
[assembly: InternalsVisibleTo("FileSystem.Fakes",  
    PublicKey=<Alternate_public_key>)]  
[assembly: InternalsVisibleTo("FileSystem.Tests",  
    PublicKey=<Test_assembly_public_key>)]  
```  
  
 W przykładzie powyżej wartości `Alternate_public_key` i `Test_assembly_public_key` może być taki sam.  
  
###  <a name="BKMK_Optimizing_build_times"></a> Optymalizacja czasów kompilacji  
 Kompilacja zestawów pozornych może znacznie zwiększyć czas kompilacji. Generując zestawy pozorne dla zestawów .NET System i zestawów innych firm w osobnym scentralizowanym projekcie, można zminimalizować czas kompilacji. Ponieważ takie zestawy rzadko się zmieniają, można użyć ponownie wygenerowanych zestawów pozornych w innych projektach.  
  
 Z projektów testów jednostkowych można po prostu wziąć referencję do skompilowanych zestawów pozornych, które są umieszczone w FakesAssemblies w folderze projektu.  
  
1.  Utwórz nową bibliotekę klas z wersją środowiska uruchomieniowego .NET dopasowania Twoich projektów testów. Nazwijmy ją Fakes.Prebuild. Usuń plik class1.cs z projektu, nie jest wymagane.  
  
2.  Dodaj odwołanie do wszystkich systemowych i zestawów innych firm, których potrzebujesz substytutów.  
  
3.  Dodaj plik .fakes do każdego zestawu i kompilacji.  
  
4.  Z projektu testów  
  
    -   Upewnij się, że masz odwołanie do środowiska uruchomieniowego podrobionych DLL:  
  
         C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.QualityTools.Testing.Fakes.dll  
  
    -   Dla każdego zestawu, utworzono substytuty, Dodaj odwołanie do odpowiedniego pliku DLL w folderze Fakes.Prebuild\FakesAssemblies projektu.  
  
###  <a name="BKMK_Avoiding_assembly_name_clashing"></a> Unikanie konfliktu nazw zestawów  
 W środowisku kompilacji zespołowej wszystkie dane wyjściowe kompilacji są scalane w jednym katalogu. W przypadku wielu projektów używa substytutów może się zdarzyć, że zestawy pozorne z różnych wersji nadpiszą. Na przykład TestProject1 elementów sztucznych mscorlib.dll z testproject1 z .NET Framework 2.0 i TestProject2 elementów sztucznych mscorlib.dll dla programu .NET Framework 4 zarówno dałaby do mscorlib. Zestaw Substytuowany Fakes.dll.  
  
 Aby uniknąć tego problemu, substytuty powinny automatycznie tworzyć nazwy zestawów pozorowanych z wersją kwalifikowaną dla odwołań do projektu bez podczas dodawania plików .fakes. Nazwa zestawu Pozorowanego wersją kwalifikowaną dołącza numer wersji, podczas tworzenia nazwy zestawu elementów sztucznych:  
  
 Biorąc pod uwagę zestaw MyAssembly i wersję 1.2.3.4 Nazwa zestawu Pozorowanego to MyAssembly.1.2.3.4.Fakes.  
  
 Można zmienić lub usunąć tę wersję przez edycję atrybutu wersja elementu zestaw w .fakes:  
  
```xml  
attribute of the Assembly element in the .fakes:  
<Fakes ...>  
  <Assembly Name="MyAssembly" Version="1.2.3.4" />  
  ...  
</Fakes>  
  
```  
  
##  <a name="BKMK_Fakes_naming_conventions"></a> Konwencje nazewnictwa substytutów  
  
###  <a name="BKMK_Shim_type_and_stub_type_naming_conventions"></a> Typ podkładek i klas zastępczych wpisz konwencje nazewnictwa  
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
  
###  <a name="BKMK_Shim_delegate_property_or_stub_delegate_field_naming_conventions"></a> Właściwości delegata zastępczego lub konwencji nazewnictwa pól delegata namiastki  
 **Podstawowe zasady** dla nazewnictwa pól, zaczynając od pustej nazwy:  
  
- Nazwa metody jest dołączana.  
  
- Jeśli nazwa metody jest jawną implementacją interfejsu, kropki są usuwane.  
  
- Jeśli metoda jest ogólna, `Of` *n* jest dołączana w przypadku gdy *n* jest to liczba argumentów metody ogólnej.  
  
  **Specjalne nazwy metod** takie jak właściwości getter lub setter są traktowane zgodnie z opisem w poniższej tabeli.  
  
|Jeśli metoda to...|Przykład|Dołączona nazwa metody|  
|-------------------|-------------|--------------------------|  
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
  
 **Uwagi**  
  
-   **Gettery i settery indeksatorów** traktuje się podobnie do właściwości. Domyślna nazwa indeksatora to `Item`.  
  
-   **Typ parametru** nazwy są przekształcane i łączone.  
  
-   **Zwracany typ** jest ignorowana, chyba że istnieje dwuznaczność przeciążenia. Jeśli jest to możliwe, typ zwracany jest dołączany na końcu nazwy  
  
###  <a name="BKMK_Parameter_type_naming_conventions"></a> Konwencje nazewnictwa typu parametru  
  
|Biorąc pod uwagę|Dołączany ciąg to...|  
|-----------|-------------------------|  
|A **typu**`T`|T<br /><br /> Przestrzeń nazw, struktura zagnieżdżona i tiki ogólne, są opuszczane.|  
|**Parametr wyjściowy**`out T`|`TOut`|  
|A **parametr ref** `ref T`|`TRef`|  
|**Typu tablicy**`T[]`|`TArray`|  
|A **tablicy wielowymiarowej** typu `T[ , , ]`|`T3`|  
|A **wskaźnik** typu `T*`|`TPtr`|  
|A **typu ogólnego**`T<R1, …>`|`TOfR1`|  
|A **argument typu ogólnego** `!i` typu `C<TType>`|`Ti`|  
|A **argument metody ogólnej** `!!i` metody `M<MMethod>`|`Mi`|  
|A **zagnieżdżony typ**`N.T`|`N` jest dołączany, następnie `T`|  
  
###  <a name="BKMK_Recursive_rules"></a> Zasady cykliczne  
 Następujące reguły są stosowane cyklicznie:  
  
-   Ponieważ substytuty używają C# wygenerować zestawy pozorne, dowolny znak, który skutkowałby nieprawidłowym C# token jest zmieniany na "_" (podkreślenie).  
  
-   Jeśli nazwa wynikowa jest niezgodna z dowolnym elementem członkowskim typu deklarującego, schemat numerowania jest używany przez dołączenie dwóch cyfr licznika, począwszy od 01.  
  
##  <a name="BKMK_External_resources"></a> Zasoby zewnętrzne  
  
###  <a name="BKMK_Guidance"></a> Wskazówki dotyczące  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 2: Testy jednostkowe: Testowanie wnętrza](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Zobacz też  
 [Izolowanie testowanego kodu za pomocą struktury Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)
