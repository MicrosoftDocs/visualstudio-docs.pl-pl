---
title: Dostosowywanie kompilacji | Dokumenty firmy Microsoft
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
ms.openlocfilehash: e7ddf87f5fa9f937c0272e37f3a6b4aba29f2d6c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652797"
---
# <a name="customize-your-build"></a>Dostosowywanie kompilacji

Projekty MSBuild, które używają standardowego procesu kompilacji (importowanie *Microsoft.Common.props* i *Microsoft.Common.targets)* mają kilka haków rozszerzalności, których można użyć do dostosowania procesu kompilacji.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Dodawanie argumentów do wywołań MSBuild wiersza polecenia dla projektu

Plik *Directory.Build.rsp* w katalogu źródłowym lub powyżej katalogu źródłowego zostanie zastosowany do kompilacji wiersza polecenia projektu. Aby uzyskać szczegółowe informacje, zobacz [PLIKI odpowiedzi MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Katalog.Build.props i Directory.Build.targets

Przed MSBuild w wersji 15, jeśli chcesz zapewnić nową, niestandardową właściwość do projektów w rozwiązaniu, trzeba było ręcznie dodać odwołanie do tej właściwości do każdego pliku projektu w rozwiązaniu. Lub trzeba było zdefiniować właściwość w pliku *.props,* a następnie jawnie zaimportować plik *.props* w każdym projekcie w rozwiązaniu, między innymi.

Jednak teraz można dodać nową właściwość do każdego projektu w jednym kroku, definiując ją w jednym pliku o nazwie *Directory.Build.props* w folderze głównym, który zawiera źródło. Po uruchomieniu programu MSBuild *firma Microsoft.Common.props* przeszukuje strukturę katalogów w poszukiwaniu pliku *Directory.Build.props* (a *microsoft.common.targets* szuka *directory.build.targets).* Jeśli znajdzie jeden, importuje właściwość. *Directory.Build.props* to plik zdefiniowany przez użytkownika, który zapewnia dostosowania projektów w katalogu.

> [!NOTE]
> Systemy plików oparte na systemie Linux są rozróżniane. Upewnij się, że wielkość liter nazwa pliku Directory.Build.props jest dokładnie zgodna lub nie zostanie wykryta podczas procesu kompilacji.
>
> Zobacz [ten problem z githubem,](https://github.com/dotnet/core/issues/1991#issue-368441031) aby uzyskać więcej informacji.

### <a name="directorybuildprops-example"></a>Przykład directory.build.props

Na przykład jeśli chcesz włączyć wszystkie projekty, aby uzyskać dostęp do nowej roslyn **/deterministic** funkcji (która jest widoczna w roslyn `CoreCompile` docelowej przez właściwość), `$(Deterministic)`można wykonać następujące czynności.

1. Utwórz nowy plik w katalogu repozytorium o nazwie *Directory.Build.props*.
2. Dodaj do pliku następujący kod XML.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Uruchom msbuild. Istniejące importy programu *Microsoft.Common.props* i *Microsoft.Common.targets* znajdują plik i importują go.

### <a name="search-scope"></a>Zakres wyszukiwania

Podczas wyszukiwania pliku *Directory.Build.props,* MSBuild przechadza strukturę katalogów w górę od lokalizacji projektu (`$(MSBuildProjectFullPath)`), zatrzymując się po zlokalizowaniu pliku *Directory.Build.props.* Na przykład, `$(MSBuildProjectFullPath)` jeśli był *c:\users\username\code\test\case1*, MSBuild rozpocznie wyszukiwanie tam, a następnie przeszuka strukturę katalogów w górę, aż znajdzie plik *Directory.Build.props,* jak w poniższej strukturze katalogów.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Lokalizacja pliku rozwiązania nie ma znaczenia dla *pliku Directory.Build.props*.

### <a name="import-order"></a>Zamówienie importu

*Directory.Build.props* jest importowany bardzo wcześnie w *microsoft.common.props*, a właściwości zdefiniowane później są niedostępne dla niego. Należy więc unikać odwoływania się do właściwości, które nie są jeszcze zdefiniowane (i oceni do opróżnienia).

*Directory.Build.targets* jest importowany z *witryny Microsoft.Common.targets* po zaimportowaniu plików *.targets* z pakietów NuGet. Tak więc może zastąpić właściwości i obiekty docelowe zdefiniowane w większości logiki kompilacji, ale czasami może być konieczne dostosowanie pliku projektu po ostatecznym imporcie.

### <a name="use-case-multi-level-merging"></a>Przypadek użycia: scalanie wielopoziomowe

Załóżmy, że masz tę standardową strukturę rozwiązania:

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

Pożądane może być mieć wspólne właściwości dla wszystkich projektów *(1),* wspólne właściwości dla projektów *src* *(2-src)* i wspólne właściwości dla projektów *testowych* *(2-test)*.

Aby MSBuild poprawnie scalić "wewnętrzne" pliki *(2-src* i *2-test)* z "zewnętrznym" plikiem (*1*), należy wziąć pod uwagę, że gdy MSBuild znajdzie plik *Directory.Build.props,* zatrzymuje dalsze skanowanie. Aby kontynuować skanowanie i scalanie do pliku zewnętrznego, umieść ten kod w obu plikach wewnętrznych:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Podsumowanie ogólnego podejścia MSBuild jest następujące:

- Dla danego projektu MSBuild znajduje pierwszy *Katalog.Build.props* w górę w strukturze rozwiązania, scala go z wartościami domyślnymi i zatrzymuje skanowanie w celu uzyskania więcej
- Jeśli chcesz znaleźć i scalić wiele [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) poziomów, a następnie (pokazany powyżej) plik "zewnętrzny" z pliku "wewnętrznego"
- Jeśli "zewnętrzny" plik nie importuje również czegoś nad nim, skanowanie zatrzymuje się tam
- Aby kontrolować proces skanowania/scalania, `$(DirectoryBuildPropsPath)``$(ImportDirectoryBuildProps)`

Albo po prostu: pierwszy *Directory.Build.props,* który nie importuje niczego jest, gdzie MSBuild zatrzymuje.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Wybierz między dodawaniem właściwości do pliku .props lub .targets

MSBuild jest zależny od zamówienia importu, a `UsingTask` ostatnia definicja właściwości (lub lub lub docelowej) jest używana definicja.

Podczas używania jawnego importu można importować pliki *.props* lub *.targets* w dowolnym momencie. Oto powszechnie stosowana konwencja:

- Pliki *.props* są importowane na początku zamówienia importu.

- *Pliki .targets* są importowane z opóźnieniem w kolejności kompilacji.

Ta konwencja jest `<Project Sdk="SdkName">` wymuszana przez import (to znaczy, import *Sdk.props* jest pierwszy, przed całą zawartością pliku, a następnie *Sdk.targets* jest ostatni, po całej zawartości pliku).

Przy podejmowaniu decyzji, gdzie umieścić właściwości, należy użyć następujących ogólnych wytycznych:

- Dla wielu właściwości nie ma znaczenia, gdzie są one zdefiniowane, ponieważ nie są zastępowane i będą odczytywane tylko w czasie wykonywania.

- W przypadku zachowania, które może być dostosowane w poszczególnych projektach, ustaw wartości domyślne w *plikach .props.*

- Należy unikać ustawiania właściwości zależnych w *plikach .props,* odczytając wartość ewentualnie dostosowanej właściwości, ponieważ dostosowanie nie nastąpi, dopóki MSBuild nie przeczyta projektu użytkownika.

- Ustaw właściwości zależne w plikach *.targets,* ponieważ będą one odbierać dostosowania z poszczególnych projektów.

- Jeśli chcesz zastąpić właściwości, zrób to w pliku *.targets,* po wszystkich dostosowań projektu użytkownika miały szansę na zaniechanych. Należy zachować ostrożność podczas korzystania z właściwości pochodnych; właściwości pochodne mogą również wymagać zastąpienia.

- Uwzględnij elementy w *plikach .props* (uwarunkowane właściwością). Wszystkie właściwości są brane pod uwagę przed każdym elementem, więc dostosowania właściwości projektu użytkownika `Remove` są `Update` pobierane, a to daje projektowi użytkownika możliwość lub dowolny element wniesiony przez import.

- Definiowanie obiektów docelowych w *plikach .targets.* Jeśli jednak plik *.targets* jest importowany przez sdk, należy pamiętać, że ten scenariusz sprawia, że zastępowanie obiektu docelowego jest trudniejsze, ponieważ projekt użytkownika nie ma miejsca na zastąpienie go domyślnie.

- Jeśli to możliwe, preferuj dostosowywanie właściwości w czasie oceny nad zmianą właściwości wewnątrz obiektu docelowego. Ta wytyczna ułatwia załadowanie projektu i zrozumienie, co robi.

## <a name="msbuildprojectextensionspath"></a>ŚCIEŻKA MSBuildProjectExtensionsPath

Domyślnie *microsoft.common.props* importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` i *Microsoft.Common.targets* importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Wartością `MSBuildProjectExtensionsPath` domyślną `$(BaseIntermediateOutputPath)` `obj/`jest , . NuGet używa tego mechanizmu, aby odwołać się do logiki kompilacji dostarczane z pakietami; oznacza to, że w `{project}.nuget.g.props` czasie przywracania tworzy pliki, które odwołują się do zawartości pakietu.

Ten mechanizm rozszerzalności można wyłączyć, `ImportProjectExtensionProps` ustawiając właściwość `false` w *katalogu.Build.props* lub przed zaimportowaniem *pliku Microsoft.Common.props*.

> [!NOTE]
> Wyłączenie importu MSBuildProjectExtensionsPath uniemożliwi logikę kompilacji dostarczoną w pakietach NuGet do projektu. Niektóre pakiety NuGet wymagają logiki kompilacji do wykonywania ich funkcji i będą renderowane bezużyteczne, gdy jest to wyłączone.

## <a name="user-file"></a>plik użytkownika

*Microsoft.Common.CurrentVersion.targets* importuje, `$(MSBuildProjectFullPath).user` jeśli istnieje, dzięki czemu można utworzyć plik obok projektu z tym dodatkowym rozszerzeniem. W przypadku długoterminowych zmian, które zamierzasz zaewidencjonować w kontroli źródła, wolisz zmienić sam projekt, aby przyszli opiekunowie nie musieli wiedzieć o tym mechanizmie rozszerzenia.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>Ścieżka MSBuildExtensionsPath i MSBuildUserExtensionsPath

> [!WARNING]
> Korzystanie z tych mechanizmów rozszerzenia utrudnia uzyskanie powtarzalnych kompilacji na różnych komputerach. Spróbuj użyć konfiguracji, która może być zaewidencjonowana w systemie kontroli źródła i współużytkowana przez wszystkich deweloperów bazy kodu.

Zgodnie z konwencją wiele podstawowych plików logiki kompilacji importuje

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

przed ich zawartością, oraz

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Później. Ta konwencja umożliwia zainstalowane pakiety SDK, aby rozszerzyć logikę kompilacji typowych typów projektów.

Ta sama struktura katalogów `$(MSBuildUserExtensionsPath)`jest przeszukiwana w programie , który jest folderem na użytkownika *%LOCALAPPDATA%\Microsoft\MSBuild*. Pliki umieszczone w tym folderze zostaną zaimportowane dla wszystkich kompilacji odpowiedniego typu projektu uruchamianych pod poświadczeniami tego użytkownika. Rozszerzenia użytkowników można wyłączyć, ustawiając właściwości nazwane po pliku `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`importowania we wzorcu . Na przykład `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` ustawienie, aby `false` `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`zapobiec importowaniu .

## <a name="customize-the-solution-build"></a>Dostosowywanie kompilacji rozwiązania

> [!IMPORTANT]
> Dostosowywanie kompilacji rozwiązania w ten sposób dotyczy tylko kompilacji wiersza polecenia za pomocą *pliku MSBuild.exe*. Nie **ma** zastosowania do kompilacji wewnątrz programu Visual Studio.

Gdy MSBuild tworzy plik rozwiązania, najpierw tłumaczy go wewnętrznie do pliku projektu, a następnie tworzy go. Wygenerowany plik projektu `before.{solutionname}.sln.targets` importuje przed `after.{solutionname}.sln.targets` zdefiniowaniem dowolnych obiektów docelowych `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` i po zaimportowaniu obiektów docelowych, w tym obiektów docelowych zainstalowanych w katalogach i katalogach.

Na przykład można zdefiniować nowy obiekt docelowy, aby napisać niestandardowy komunikat dziennika po utworzeniu *MyCustomizedSolution.sln,* tworząc plik w tym samym katalogu *nazwanym po. MyCustomizedSolution.sln.targets,* który zawiera

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>Dostosowywanie wszystkich kompilacji platformy .NET

Podczas obsługi serwera kompilacji może być konieczne skonfigurowanie ustawień MSBuild globalnie dla wszystkich kompilacji na serwerze.  Zasadniczo można zmodyfikować globalne *pliki Microsoft.Common.Targets* lub *Microsoft.Common.Props,* ale istnieje lepszy sposób. Można mieć wpływ na wszystkie kompilacje określonego typu projektu (takich jak wszystkie projekty Języka C#) przy użyciu niektórych właściwości MSBuild i dodanie niektórych niestandardowych `.targets` i `.props` plików.

Aby mieć wpływ na wszystkie kompilacje języka C# lub Visual Basic podlegające instalacji msBuild lub Visual Studio, należy utworzyć plik *Custom.Before.Microsoft.Common.Targets* lub *Custom.After.Microsoft.Common.Targets* z obiektami docelowymi, które będą uruchamiane przed lub po *programie Microsoft.Common.targets,* lub *plikiem Custom.Before.Microsoft.Common.Props* lub *Custom.After.Microsoft.Common.Props* z właściwościami, które będą przetwarzane przed lub po *microsoft.common.props.*

Lokalizacje tych plików można określić przy użyciu następujących właściwości MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets (CustomAfterMicrosoftCommonTargets)
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- Niestandardowe pomicrosoftcsharpProps
- NiestandardowezamicrosoftvisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets (CustomAfMicrosoftCSharpTargets)
- CustomAfterMicrosoftVisualBasicTargets (Zestawy niestandardowe)

*Typowe* wersje tych właściwości wpływają zarówno na projekty języka C# i Visual Basic. Właściwości te można ustawić w wierszu polecenia MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Najlepsze podejście zależy od scenariusza. Jeśli masz serwer kompilacji dedykowanej i chcesz upewnić się, że niektóre obiekty docelowe zawsze są wykonywane `.targets` `.props` na wszystkich kompilacjach odpowiedniego typu projektu, które są wykonywane na tym serwerze, użycie globalnego niestandardowego lub pliku ma sens.  Jeśli chcesz, aby niestandardowe obiekty docelowe były wykonywane tylko wtedy, gdy mają zastosowanie określone warunki, użyj innej lokalizacji pliku i ustaw ścieżkę do tego pliku, ustawiając odpowiednią właściwość MSBuild w wierszu polecenia MSBuild tylko wtedy, gdy jest to potrzebne.

> [!WARNING]
> Visual Studio używa `.targets` plików `.props` niestandardowych lub plików, jeśli znajdzie je w folderze MSBuild, gdy tworzy dowolny projekt odpowiedniego typu. Może to mieć niezamierzone konsekwencje, a jeśli zostanie wykonane niepoprawnie, można wyłączyć możliwość visual studio do tworzenia na komputerze.

## <a name="customize-all-c-builds"></a>Dostosowywanie wszystkich kompilacji języka C++

W przypadku projektów języka C++ `.targets` wcześniej `.props` wymienione niestandardowe i pliki są ignorowane. W przypadku projektów języka C++ można tworzyć `.targets` pliki dla każdej platformy i umieszczać je w odpowiednich folderach importu dla tych platform.

Plik `.targets` platformy Win32, *Microsoft.Cpp.Win32.targets,* zawiera `Import` następujący element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Istnieje podobny element na końcu tego samego pliku:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Podobne elementy importu istnieją dla innych platform docelowych w *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{version}\Platforms\*.

Po umieszczeniu `.targets` pliku w odpowiednim folderze zgodnie z platformą, MSBuild importuje plik do każdej kompilacji Języka C++ dla tej platformy. W razie `.targets` potrzeby można umieścić tam wiele plików.

### <a name="specify-a-custom-import-on-the-command-line"></a>Określanie niestandardowego importu w wierszu polecenia

Dla `.targets` niestandardowych, które mają być uwzględnione dla określonej kompilacji projektu C++, należy ustawić jedną lub obie właściwości `ForceImportBeforeCppTargets` i `ForceImportAfterCppTargets` w wierszu polecenia.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

Dla ustawienia globalnego (aby mieć wpływ, powiedzmy, wszystkie kompilacje języka C++ dla platformy na serwerze kompilacji), istnieją dwie metody. Po pierwsze można ustawić te właściwości przy użyciu zmiennej środowiskowej systemu, która jest zawsze ustawiona. Działa to, ponieważ MSBuild zawsze odczytuje środowisko i tworzy (lub zastępuje) właściwości dla wszystkich zmiennych środowiskowych.

## <a name="see-also"></a>Zobacz też

- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
