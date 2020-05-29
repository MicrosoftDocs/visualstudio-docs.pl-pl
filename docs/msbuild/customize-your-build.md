---
title: Dostosuj kompilację | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b0cb05948f8010964eefe101cbc77d48a149566
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180405"
---
# <a name="customize-your-build"></a>Dostosowywanie kompilacji

Projekty programu MSBuild korzystające ze standardowego procesu kompilacji (importowane elementy *Microsoft. Common. props* i *Microsoft. Common. targets*) mają kilka punktów zaczepienia rozszerzalności, których można użyć do dostosowania procesu kompilacji.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Dodawanie argumentów do wywołań MSBuild wiersza polecenia dla projektu

Plik *Directory. Build. rsp* w katalogu źródłowym lub nowszym zostanie zastosowany do kompilacji wiersza polecenia projektu. Aby uzyskać szczegółowe informacje, zobacz [pliki odpowiedzi MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory. Build. props i Directory. Build. targets

W wersjach wcześniejszych niż 15, jeśli chcesz udostępnić nową, niestandardową właściwość do projektów w rozwiązaniu, trzeba ręcznie dodać odwołanie do tej właściwości do każdego pliku projektu w rozwiązaniu. Lub trzeba zdefiniować właściwość w pliku *. props* , a następnie jawnie zaimportować plik *. props* w każdym projekcie w rozwiązaniu, między innymi.

Można jednak teraz dodać nową właściwość do każdego projektu w jednym kroku, definiując ją w pojedynczym pliku o nazwie *Directory. Build. props* w folderze głównym, który zawiera źródło. Gdy program MSBuild działa, *Microsoft. Common. props* przeszukuje strukturę katalogów dla *katalogu. Build. props* plik (i *Microsoft. Common. targets* szuka *katalogu. Build. targets*). Jeśli zostanie znaleziony, zaimportuje właściwość. *Directory. Build. props* to plik zdefiniowany przez użytkownika, który udostępnia dostosowania do projektów w katalogu.

> [!NOTE]
> W systemach plików opartych na systemie Linux jest rozróżniana wielkość liter. Upewnij się, że wielkość liter w pliku Directory. Build. props pasuje do dokładnie lub nie zostanie wykryta podczas procesu kompilacji.
>
> Aby uzyskać więcej informacji, zobacz [ten problem](https://github.com/dotnet/core/issues/1991#issue-368441031) w usłudze GitHub.

### <a name="directorybuildprops-example"></a>Przykład katalogu. Build. props

Na przykład jeśli chcesz włączyć wszystkie projekty w celu uzyskania dostępu do nowej funkcji Roslyn **/Deterministic** (która jest dostępna w `CoreCompile` miejscu docelowym Roslyn przez właściwość `$(Deterministic)` ), możesz wykonać następujące czynności.

1. Utwórz nowy plik w katalogu głównym repozytorium o nazwie *Directory. Build. props*.
2. Dodaj następujący kod XML do pliku.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Uruchom program MSBuild. Istniejące Importy elementu *Microsoft. Common. props* i *Microsoft. Common. targets* są wyszukiwane i importowane.

### <a name="search-scope"></a>Zakres wyszukiwania

Podczas wyszukiwania pliku *Directory. Build. props* plik programu MSBuild przeprowadzi strukturę katalogów w górę z lokalizacji projektu ( `$(MSBuildProjectFullPath)` ), zatrzymując po znalezieniu pliku *Directory. Build. props* . Na przykład jeśli `$(MSBuildProjectFullPath)` została *c:\users\username\code\test\case1*, program MSBuild zacznie tam przeszukiwać, a następnie przeszukać strukturę katalogów w górę do momentu zlokalizowania pliku *Directory. Build. props* , tak jak w przypadku poniższej struktury katalogów.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Lokalizacja pliku rozwiązania nie jest istotna dla *katalogu. Build. props*.

### <a name="import-order"></a>Importuj zamówienie

Plik *Directory. Build. props* jest zaimportowany bardzo wcześnie w elemencie *Microsoft. Common. props*, a właściwości zdefiniowane później są niedostępne dla tego programu. Dlatego należy unikać odwoływania się do właściwości, które nie zostały jeszcze zdefiniowane (i które zostaną oszacowane jako puste).

Właściwości ustawiane w *katalogu Directory. Build. props* mogą zostać zastąpione w innym miejscu w pliku projektu lub w zaimportowanych plikach, dlatego należy zastanowić się, że ustawienia w *katalogu Directory. Build. props* określają wartości domyślne dla projektów.

*Katalog. Build. targets* został zaimportowany z *Microsoft. Common. targets* po imporcie *. targets* Files z pakietów NuGet. W związku z tym można przesłonić właściwości i obiekty docelowe zdefiniowane w większości logiki kompilacji lub ustawić właściwości dla wszystkich projektów, niezależnie od tego, co jest ustawione dla poszczególnych projektów.

Gdy trzeba ustawić właściwość lub zdefiniować obiekt docelowy dla pojedynczego projektu, który zastępuje wszystkie wcześniejsze ustawienia, należy umieścić tę logikę w pliku projektu po ostatecznym zaimportowaniu. Aby to zrobić w projekcie w stylu zestawu SDK, najpierw trzeba zastąpić atrybut stylu zestawu SDK analogicznym importem. Zobacz [, jak używać zestawów SDK projektu MSBuild](how-to-use-project-sdk.md).

> [!NOTE]
> Aparat MSBuild odczytuje wszystkie zaimportowane pliki podczas oceny przed rozpoczęciem wykonywania kompilacji dla dowolnego projektu (łącznie z dowolnym `PreBuildEvent` ), więc te pliki nie powinny być modyfikowane przez ani w `PreBuildEvent` żadnej innej części procesu kompilacji. Wszelkie modyfikacje nie zaczną obowiązywać do następnego wywołania programu *MSBuild. exe* lub następnej kompilacji programu Visual Studio.

### <a name="use-case-multi-level-merging"></a>Przypadek użycia: scalanie wielopoziomowe

Załóżmy, że masz standardową strukturę rozwiązań:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Może być pożądane posiadanie wspólnych właściwości dla wszystkich projektów *(1)*, wspólnych właściwości projektów *src* *(2-SRC)* i wspólnych właściwości projektów *testowych* *(2-testowe)*.

Aby program MSBuild prawidłowo scalał pliki wewnętrzne (*2-src* i *2-Test*) z plikiem zewnętrznym (*1*), należy wziąć pod uwagę, że gdy program MSBuild odnajdzie plik *Directory. Build. props* , zatrzyma dalsze skanowanie. Aby kontynuować skanowanie i scalanie w zewnętrznym pliku, Umieść ten kod w obu plikach wewnętrznych:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Podsumowanie ogólnego podejścia programu MSBuild jest następujące:

- W przypadku dowolnego projektu MSBuild znajduje pierwszy *katalog. Build. props* w górę struktury rozwiązania, Scala go z wartościami domyślnymi i kończy skanowanie w celu uzyskania większej liczby
- Jeśli chcesz, aby można było znaleźć i scalić wiele poziomów, wówczas [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (pokazany powyżej) plik "zewnętrzny" z pliku "wewnętrzny"
- Jeśli plik "zewnętrzny" nie jest również zaimportowany powyżej, a następnie trwa skanowanie
- Aby kontrolować proces skanowania/scalania, użyj `$(DirectoryBuildPropsPath)` i`$(ImportDirectoryBuildProps)`

Lub po prostu: pierwszy *katalog. Build. props* , który nie importuje wszystkiego, jest zatrzymywany przez MSBuild.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Wybierz między dodawaniem właściwości do pliku. props lub. targets

MSBuild jest zależna od kolejności importu, a ostatnią definicją właściwości (lub `UsingTask` docelową) jest definicja użyta.

W przypadku korzystania z jawnego importu można importować z pliku *. props* lub *. targets* w dowolnym momencie. Oto ogólnie stosowana Konwencja:

- pliki *. props* są importowane wczesnie w kolejności importu.

- pliki *. targets* są importowane najpóźniej w kolejności kompilacji.

Ta konwencja jest wymuszana przez `<Project Sdk="SdkName">` Importy (to oznacza, że import *zestawu SDK. props* jest pierwszy, przed całą zawartością pliku, *zestaw SDK. targets* jest ostatni po całej zawartości pliku).

Podczas decydowania o miejscu, w którym należy umieścić właściwości, użyj następujących ogólnych wytycznych:

- W przypadku wielu właściwości nie ma znaczenia, gdzie są zdefiniowane, ponieważ nie są zastępowane i będą odczytywane tylko w czasie wykonywania.

- W przypadku zachowania, które może być dostosowane w pojedynczym projekcie, ustaw wartości domyślne w plikach *. props* .

- Należy unikać ustawiania właściwości zależnych w plikach *. props* , odczytując wartość prawdopodobnie dostosowanej właściwości, ponieważ nie będzie ona miała zastosowania do momentu, gdy MSBuild odczyta projekt użytkownika.

- Ustaw właściwości zależne w plikach *. targets* , ponieważ będą one pobierać dostosowania z poszczególnych projektów.

- Jeśli zachodzi potrzeba zastąpienia właściwości, zrób to w pliku *. targets* , gdy wszystkie dostosowania użytkownika i projektu zaczną obowiązywać. Należy zachować ostrożność w przypadku używania właściwości pochodnych; należy również zastąpić właściwości pochodne.

- Uwzględnij elementy w plikach *. props* (warunek na właściwości). Wszystkie właściwości są brane pod uwagę przed dowolnym elementem, więc dostosowania właściwości użytkownika i projektu są pobierane, a to daje projekt użytkownikowi możliwość `Remove` lub dowolny element, który został `Update` przez niego zaimportowany.

- Zdefiniuj elementy docelowe w plikach *. targets* . Jeśli jednak plik *targets* zostanie zaimportowany przez zestaw SDK, należy pamiętać, że w tym scenariuszu bardziej trudne jest zastępowanie obiektu docelowego, ponieważ projekt użytkownika nie ma miejsca, aby przesłonić go domyślnie.

- Jeśli to możliwe, Preferuj Dostosowywanie właściwości w czasie oceniania nad zmianami właściwości w elemencie docelowym. Te wskazówki ułatwiają załadowanie projektu i zrozumienie jego działania.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Domyślnie importowane są Importy *Microsoft. Common. props* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` i *Microsoft. Common. targets* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets` . Wartość domyślna `MSBuildProjectExtensionsPath` to `$(BaseIntermediateOutputPath)` , `obj/` . NuGet używa tego mechanizmu do odwoływania się do logiki kompilacji dostarczanej z pakietami. oznacza to, że w czasie przywracania tworzy `{project}.nuget.g.props` pliki odwołujące się do zawartości pakietu.

Można wyłączyć ten mechanizm rozszerzalności, ustawiając właściwość `ImportProjectExtensionProps` na `false` w *katalogu. Build. props* lub przed zaimportowaniem *Microsoft. Common. props*.

> [!NOTE]
> Wyłączenie MSBuildProjectExtensionsPath Importy uniemożliwi logikę kompilacji dostarczaną w pakietach NuGet od zastosowania do projektu. Niektóre pakiety NuGet wymagają logiki kompilacji do wykonywania ich funkcji i będą renderowane jako bezużyteczny, gdy jest to wyłączone.

## <a name="user-file"></a>plik. User

Plik *Microsoft. Common. CurrentVersion. targets* Imports `$(MSBuildProjectFullPath).user` (jeśli istnieje), więc można utworzyć obok projektu, który ma dodatkowe rozszerzenie. Aby uzyskać długoterminowe zmiany, które planujesz zaewidencjonować kontrolę źródła, wolisz zmienić projekt, tak aby w przyszłości nie trzeba było wiedzieć o tym mechanizmie rozszerzenia.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath i MSBuildUserExtensionsPath

> [!WARNING]
> Korzystanie z tych mechanizmów rozszerzeń utrudnia Kompilowanie kompilacji między maszynami. Spróbuj użyć konfiguracji, którą można sprawdzić w systemie kontroli źródła i udostępnić wszystkim deweloperom bazy kodu.

Zgodnie z Konwencją, importuje się wiele podstawowych plików logiki kompilacji

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

przed ich zawartością i

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

ustawiając. Ta konwencja pozwala zainstalowanym zestawom SDK na rozszerzanie logiki kompilacji wspólnych typów projektów.

Ta sama struktura katalogów jest przeszukiwana `$(MSBuildUserExtensionsPath)` , która jest folderem na użytkownika *%LocalAppData%\Microsoft\MSBuild*. Pliki umieszczone w tym folderze zostaną zaimportowane dla wszystkich kompilacji odpowiedniego typu projektu uruchamianego w ramach poświadczeń tego użytkownika. Rozszerzenia użytkownika można wyłączyć przez ustawienie właściwości nazwanych po importowaniu pliku we wzorcu `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` . Na przykład ustawienie `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` `false` uniemożliwia zaimportowanie `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` .

## <a name="customize-the-solution-build"></a>Dostosuj kompilację rozwiązania

> [!IMPORTANT]
> Dostosowanie kompilacji rozwiązania w ten sposób dotyczy tylko kompilacji z wiersza polecenia przy użyciu programu *MSBuild. exe*. Nie **dotyczy to** kompilacji w programie Visual Studio.

Gdy program MSBuild kompiluje plik rozwiązania, najpierw przekształci go wewnętrznie w plik projektu, a następnie kompiluje. Wygenerowany plik projektu importuje `before.{solutionname}.sln.targets` przed zdefiniowaniem elementów docelowych i `after.{solutionname}.sln.targets` po importowaniu elementów docelowych, w tym elementów docelowych zainstalowanych do `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` katalogów i.

Na przykład można zdefiniować nowy obiekt docelowy, aby zapisać niestandardowy komunikat dziennika po skompilowaniu *MyCustomizedSolution. sln* , tworząc plik w tym samym katalogu o nazwie *After. MyCustomizedSolution. sln. targets* , które zawierają

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

Kompilacja rozwiązania jest oddzielona od kompilacji projektu, dlatego tutaj ustawienia nie wpływają na kompilacje projektu.

## <a name="customize-all-net-builds"></a>Dostosuj wszystkie kompilacje platformy .NET

W przypadku obsługi serwera kompilacji może być konieczne skonfigurowanie globalnie ustawień programu MSBuild dla wszystkich kompilacji na serwerze.  W zasadzie można modyfikować pliki globalne *Microsoft. Common. targets* lub *Microsoft. Common. props* , ale istnieje lepszy sposób. Możesz mieć wpływ na wszystkie kompilacje określonego typu projektu (na przykład wszystkie projekty C#), używając niektórych właściwości programu MSBuild i dodając niektóre niestandardowe `.targets` i `.props` pliki.

Aby mieć wpływ na wszystkie kompilacje w języku C# lub Visual Basic, które podlegają instalacji programu MSBuild lub programu Visual Studio, Utwórz plik *niestandardowy. before. Microsoft. Common. targets* lub *Custom. After. Microsoft. Common. targets* z obiektami docelowymi, które zostaną uruchomione przed lub po pliku *Microsoft. Common. datatargets*lub Custom. *before. Microsoft. Common. props* lub *Custom. After. Microsoft. Common. props* z właściwościami, które będą przetwarzane przed lub po elemencie *Microsoft. Common.*

Lokalizacje tych plików można określić przy użyciu następujących właściwości programu MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

*Wspólne* wersje tych właściwości wpływają na projekty C# i Visual Basic. Te właściwości można ustawić w wierszu polecenia programu MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Najlepsze podejście zależy od Twojego scenariusza. Korzystając z rozszerzalności programu Visual Studio, można dostosować system kompilacji i udostępnić mechanizm do instalowania dostosowań i zarządzania nimi.

Jeśli masz dedykowany serwer kompilacji i chcesz się upewnić, że niektóre elementy docelowe są zawsze wykonywane na wszystkich kompilacjach odpowiedniego typu projektu, który jest wykonywany na tym serwerze, użyj globalnie niestandardowego `.targets` lub `.props` pliku.  Jeśli chcesz, aby niestandardowe elementy docelowe były wykonywane tylko wtedy, gdy są spełnione określone warunki, użyj innej lokalizacji pliku i Ustaw ścieżkę do tego pliku, ustawiając odpowiednią właściwość programu MSBuild w wierszu polecenia programu MSBuild tylko wtedy, gdy jest to konieczne.

> [!WARNING]
> Program Visual Studio używa niestandardowych `.targets` lub `.props` plików, jeśli znajdzie je w folderze programu MSBuild za każdym razem, gdy kompiluje wszystkie projekty pasującego typu. Może to mieć niezamierzone konsekwencje, a jeśli to zrobisz, program Visual Studio może wymusić kompilację na komputerze.

## <a name="customize-c-builds"></a>Dostosuj kompilacje języka C++

W przypadku projektów języka C++ wspomniane wcześniej pliki custom *. targets* i *. props* nie mogą być używane w taki sam sposób, aby przesłonić ustawienia domyślne. *Katalog. Build. props* jest zaimportowany przez *firmę Microsoft. Common. props*, który jest importowany w `Microsoft.Cpp.Default.props` czasie, gdy większość wartości domyślnych jest zdefiniowana w pliku *Microsoft. cpp. props* i dla wielu właściwości warunek "Jeśli nie jest jeszcze zdefiniowany", nie można użyć warunku, ponieważ właściwość jest już zdefiniowana, ale wartość domyślna musi być inna dla określonych właściwości projektu zdefiniowanych w elemencie `PropertyGroup` with `Label="Configuration"` (zobacz [. vcxproj i. props — struktura plików](/cpp/build/reference/vcxproj-file-structure)).

Można jednak użyć następujących właściwości, aby określić pliki *. props* , które mają być automatycznie importowane przed/po pliku * \* Microsoft. cpp.* Files:

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Aby dostosować wartości domyślne właściwości dla wszystkich kompilacji C++, należy utworzyć kolejną *. plik PROPS* (Powiedz, *. props*) i zdefiniować `ForceImportAfterCppProps` Właściwość w `Directory.Build.props` wskazaniu:

<PropertyGroup><ForceImportAfterCppProps>$ (MsbuildThisFileDirectory) \MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

Właściwości *. props* są automatycznie importowane na końcu elementu *Microsoft. cpp. props*.

## <a name="customize-all-c-builds"></a>Dostosuj wszystkie kompilacje C++

Nie zaleca się dostosowywania instalacji programu Visual Studio, ponieważ nie jest to łatwe śledzenie takich dostosowań, ale jeśli rozszerzasz program Visual Studio, aby dostosować kompilacje C++ dla określonej platformy, możesz utworzyć `.targets` pliki dla każdej platformy i umieścić je w odpowiednich folderach importu dla tych platform w ramach rozszerzenia programu Visual Studio.

`.targets`Plik dla platformy Win32, *Microsoft. cpp. Win32. targets*, zawiera następujący `Import` element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Znajduje się podobny element blisko końca tego samego pliku:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Podobne elementy importowania istnieją dla innych platform docelowych w programie *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {Version} \ platforms \* .

Po umieszczeniu `.targets` pliku w odpowiednim `ImportAfter` folderze zgodnie z platformą, MSBuild importuje plik do każdej kompilacji C++ dla tej platformy. `.targets`W razie konieczności można umieścić wiele plików. 

Korzystając z rozszerzalności programu Visual Studio, możliwe jest dalsze dostosowanie, takie jak Definiowanie nowej platformy. Aby uzyskać więcej informacji, zobacz [rozszerzalność projektu C++](../extensibility/visual-cpp-project-extensibility.md).

### <a name="specify-a-custom-import-on-the-command-line"></a>Określanie niestandardowego importu w wierszu polecenia

Dla niestandardowego, `.targets` który ma zostać uwzględniony dla określonej kompilacji projektu języka C++, Ustaw jedną lub obie właściwości `ForceImportBeforeCppTargets` i `ForceImportAfterCppTargets` w wierszu polecenia.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

W przypadku ustawienia globalnego (aby mieć wpływ na wszystkie kompilacje C++ dla platformy na serwerze kompilacji) Istnieją dwie metody. Najpierw można ustawić te właściwości przy użyciu zmiennej środowiskowej systemu, która jest zawsze ustawiona. Dzieje się tak, ponieważ program MSBuild zawsze odczytuje środowisko i tworzy (lub przesłania) właściwości dla wszystkich zmiennych środowiskowych.

## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
