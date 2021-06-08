---
title: Dostosowywanie kompilacji | Microsoft Docs
description: Dowiedz się więcej na temat kilku wpięć rozszerzalności, których można użyć do dostosowywania projektów MSBuild, które korzystają ze standardowego procesu kompilacji.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 19dafcbb956634eeea5fa0ed967e93a8a8d5e546
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588452"
---
# <a name="customize-your-build"></a>Dostosowywanie kompilacji

Projekty MSBuild, które używają standardowego procesu kompilacji (importowanie *Microsoft.Common.props* i *Microsoft.Common.targets)* mają kilka wpięć rozszerzalności, których można użyć do dostosowania procesu kompilacji.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Dodawanie argumentów do wywołania programu MSBuild w wierszu polecenia dla projektu

Plik *Directory.Build.rsp* w katalogu źródłowym lub powyżej zostanie zastosowany do kompilacji wiersza polecenia projektu. Aby uzyskać szczegółowe informacje, zobacz [pliki odpowiedzi programu MSBuild.](../msbuild/msbuild-response-files.md#directorybuildrsp)

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props i Directory.Build.targets

Przed wersją 15 programu MSBuild, aby udostępnić nową, niestandardową właściwość dla projektów w rozwiązaniu, trzeba było ręcznie dodać odwołanie do tej właściwości do każdego pliku projektu w rozwiązaniu. Lub trzeba było zdefiniować właściwość w pliku *props,* a następnie jawnie zaimportować plik *props* między innymi w każdym projekcie w rozwiązaniu.

Jednak teraz można dodać nową właściwość do każdego projektu w jednym kroku, definiując ją w jednym pliku o nazwie *Directory.Build.props* w folderze głównym, który zawiera źródło. Gdy program MSBuild jest uruchamiany, *plik Microsoft.Common.props* wyszukuje w strukturze katalogów plik *Directory.Build.props* (a *plik Microsoft.Common.targets* wyszukuje plik *Directory.Build.targets).* Jeśli znajdzie ją, zaim importuje właściwość . *Directory.Build.props* to plik zdefiniowany przez użytkownika, który zapewnia dostosowania do projektów w katalogu.

> [!NOTE]
> W systemach plików opartych na systemie Linux jest wielkość liter. Upewnij się, że nazwa pliku Directory.Build.props ma dokładnie taką samą nazwę, lub że nie zostanie wykryta podczas procesu kompilacji.
>
> Zobacz [ten problem z serwisem GitHub,](https://github.com/dotnet/core/issues/1991#issue-368441031) aby uzyskać więcej informacji.

### <a name="directorybuildprops-example"></a>Przykład Directory.Build.props

Jeśli na przykład chcesz umożliwić wszystkim projektom dostęp do nowej funkcji **Roslyn /deterministic** (widocznej w obiekcie docelowym Roslyn przez właściwość ), możesz wykonać `CoreCompile` następujące `$(Deterministic)` czynności.

1. Utwórz nowy plik w katalogu głównym swojego repo o nazwie *Directory.Build.props.*
2. Dodaj następujący kod XML do pliku .

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Uruchom msbuild. Istniejące importy *Microsoft.Common.props* i *Microsoft.Common.targets* twojego projektu znajdują plik i importuje go.

### <a name="search-scope"></a>Zakres wyszukiwania

Podczas wyszukiwania pliku *Directory.Build.props* program MSBuild przekieruje strukturę katalogów w górę od lokalizacji projektu ( ), zatrzymując się po zlokalizowaniu pliku `$(MSBuildProjectFullPath)` *Directory.Build.props.* Jeśli na przykład masz plik `$(MSBuildProjectFullPath)` *c:\users\username\code\test\case1,* program MSBuild rozpocznie wyszukiwanie w tym miejscu, a następnie przeszuka strukturę katalogów w górę do momentu zlokalizowania pliku *Directory.Build.props,* tak jak w poniższej strukturze katalogów.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Lokalizacja pliku rozwiązania nie ma znaczenia dla *directory.build.props.*

### <a name="import-order"></a>Zamówienie importu

*Directory.Build.props* jest importowany bardzo wcześnie w *Microsoft.Common.props*, a właściwości zdefiniowane później są dla niego niedostępne. Dlatego należy unikać odwoływania się do właściwości, które nie zostały jeszcze zdefiniowane (i zostaną ocenione jako puste).

Właściwości, które są ustawione w *Directory.Build.props* można zastąpić w innym miejscu w pliku projektu lub w zaimportowanych plikach, więc należy pamiętać o ustawieniach w *Directory.Build.props* jako określania wartości domyślnych dla projektów.

*Plik Directory.Build.targets jest* importowany z pliku *Microsoft.Common.targets* po zaimportowaniu *plików targets* z pakietów NuGet. Może więc przesłonić właściwości i elementy docelowe zdefiniowane w większości logiki kompilacji lub ustawić właściwości dla wszystkich projektów niezależnie od ustawień poszczególnych projektów.

Jeśli musisz ustawić właściwość lub zdefiniować element docelowy dla pojedynczego projektu, który zastępuje poprzednie ustawienia, umieść tę logikę w pliku projektu po ostatecznym zaimportowaniu. Aby to zrobić w projekcie w stylu zestawu SDK, należy najpierw zastąpić atrybut w stylu zestawu SDK równoważnymi importami. Zobacz [How to use MSBuild project SDKs (Jak używać zestawów SDK projektów MSBuild).](how-to-use-project-sdk.md)

> [!NOTE]
> Aparat MSBuild odczytuje we wszystkich zaimportowanych plikach podczas oceny przed rozpoczęciem wykonywania kompilacji dla dowolnego projektu (w tym dowolnego ), więc nie oczekuje się, że te pliki zostaną zmodyfikowane przez lub inną część `PreBuildEvent` `PreBuildEvent` procesu kompilacji. Wszelkie modyfikacje będą obowiązywać dopiero po następnymMSBuild.exe *lub* Visual Studio kompilacji.

### <a name="use-case-multi-level-merging"></a>Przypadek użycia: scalanie na wielu poziomie

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

Warto mieć wspólne właściwości dla wszystkich projektów *(1),* typowe właściwości dla projektów *src* *(2-src)* i typowe właściwości dla projektów *testowych* *(2-test).*

Aby program MSBuild poprawnie scalił pliki "wewnętrzne"*(2-src* i *2-test*) z plikiem "zewnętrznym"*(1),* należy wziąć pod uwagę, że po tym, jak program MSBuild znajdzie plik *Directory.Build.props,* zatrzyma dalsze skanowanie. Aby kontynuować skanowanie i scalanie z plikiem zewnętrznym, umieść ten kod w obu plikach wewnętrznych:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Podsumowanie ogólnego podejścia do programu MSBuild jest następujące:

- W przypadku dowolnego projektu program MSBuild znajduje pierwszy katalog *Directory.Build.props* w górę struktury rozwiązania, scala go z wartościami domyślnymi i przestaje skanować w celu więcej
- Jeśli chcesz znaleźć i scalić wiele poziomów, wówczas [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (pokazany powyżej) "zewnętrzny" plik z "wewnętrznego" pliku
- Jeśli plik "zewnętrzny" sam nie zaimportuje również czegoś powyżej, skanowanie zostanie zatrzymane
- Aby kontrolować proces skanowania/scalania, `$(DirectoryBuildPropsPath)` użyj i `$(ImportDirectoryBuildProps)`

Lub mówiąc prościej: *pierwszy directory.build.props,* który nie importuje niczego, to miejsce, w którym zatrzymuje się program MSBuild.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Wybieranie między dodawaniem właściwości do pliku .props lub .targets

Program MSBuild jest zależny od kolejności importowania, a ostatnia definicja właściwości (lub obiektu docelowego lub `UsingTask` ) jest używaną definicją.

W przypadku używania jawnych importów można importować z pliku *props* lub *targets* w dowolnym momencie. Oto powszechnie używana konwencja:

- *Pliki props* są importowane na wczesnym etapie kolejności importowania.

- *Pliki targets*  są importowane z opóźnieniem w kolejności kompilacji.

Ta konwencja jest wymuszana przez importy (oznacza to, że importowanie pliku Sdk.props jest najpierw wykonywane, zanim cała zawartość pliku, a następnie zestaw `<Project Sdk="SdkName">` *Sdk.targets* jest  ostatni, po całej zawartości pliku).

Podczas podejmowania decyzji o tym, gdzie umieścić właściwości, należy stosować się do następujących ogólnych wytycznych:

- W przypadku wielu właściwości nie ma znaczenia, gdzie są zdefiniowane, ponieważ nie są zastępowane i będą odczytywane tylko w czasie wykonywania.

- W przypadku zachowania, które można dostosować w poszczególnych projektach, ustaw wartości domyślne w *plikach props.*

- Unikaj ustawiania właściwości zależnych w plikach *props,* odczytując wartość potencjalnie dostosowanej właściwości, ponieważ dostosowanie nie nastąpi, dopóki program MSBuild nie odczyta projektu użytkownika.

- Ustaw właściwości zależne w *plikach targets,* ponieważ będą one odbierać dostosowania z poszczególnych projektów.

- Jeśli musisz przesłonić właściwości, zrób to w pliku *targets,* gdy wszystkie dostosowania projektu użytkownika będą miały szansę na efekt. Należy zachować ostrożność podczas korzystania z właściwości pochodnych; Może być również konieczne zastąpienie właściwości pochodnych.

- Uwzględnij elementy *w plikach props* (z warunkiem właściwości). Wszystkie właściwości są rozważane przed dowolnym elementem, więc dostosowania właściwości projektu użytkownika są odbierane, co daje projektowi użytkownika możliwość doprowadzenia do lub dowolnego elementu w ramach `Remove` `Update` importu.

- Zdefiniuj obiekty docelowe *w plikach targets.* Jeśli jednak plik *targets* jest importowany przez zestaw SDK, pamiętaj, że w tym scenariuszu zastępowanie obiektu docelowego jest trudniejsze, ponieważ projekt użytkownika nie ma miejsca, aby zastąpić go domyślnie.

- Jeśli to możliwe, preferuj dostosowywanie właściwości w czasie oceny zamiast zmieniania właściwości wewnątrz obiektu docelowego. Te wytyczne ułatwiają ładowanie projektu i zrozumienie jego działania.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Domyślnie *importuje wartość Microsoft.Common.props,* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` a *microsoft.common.targets importuje* `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets` wartość . Wartość domyślna `MSBuildProjectExtensionsPath` to `$(BaseIntermediateOutputPath)` , `obj/` . NuGet używa tego mechanizmu, aby odwoływać się do logiki kompilacji dostarczanej z pakietami; oznacza to, że podczas przywracania tworzy `{project}.nuget.g.props` pliki odwołujące się do zawartości pakietu.

Ten mechanizm rozszerzalności można wyłączyć, ustawiając właściwość na w pliku `ImportProjectExtensionProps` `false` *Directory.Build.props* lub przed zaimportowanie pliku *Microsoft.Common.props.*

> [!NOTE]
> Wyłączenie importów MSBuildProjectExtensionsPath uniemożliwi zastosowanie logiki kompilacji dostarczanej w pakietach NuGet do projektu. Niektóre pakiety NuGet wymagają logiki kompilacji, aby wykonać swoją funkcję, i będą renderowane jako bezużyteczne po wyłączeniu.

## <a name="user-file"></a>Plik użytkownika

*Plik Microsoft.Common.CurrentVersion.targets* importuje wartość , jeśli istnieje, więc możesz utworzyć plik obok projektu `$(MSBuildProjectFullPath).user` z tym dodatkowym rozszerzeniem. W przypadku długoterminowych zmian, które planujesz zaewidencjarzyć w kontroli źródła, preferuj zmianę samego projektu, aby przyszli konserwatorzy nie wiedzieli o tym mechanizmie rozszerzeń.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath i MSBuildUserExtensionsPath

> [!WARNING]
> Korzystanie z tych mechanizmów rozszerzeń utrudnia uzyskiwanie powtarzalnych kompilacji między maszynami. Spróbuj użyć konfiguracji, która może zostać zaewidencjonowana w systemie kontroli źródła i udostępniona wszystkim deweloperom bazy kodu.

Według konwencji importowanie wielu podstawowych plików logiki kompilacji

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

przed ich zawartością, i

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

Później. Ta konwencja pozwala zainstalowanym zestawom SDK rozszerzyć logikę kompilacji typowych typów projektów.

Ta sama struktura katalogów jest przeszukiwana w folderze , który jest `$(MSBuildUserExtensionsPath)` folderem na użytkownika *%LOCALAPPDATA%\Microsoft\MSBuild.* Pliki umieszczone w tym folderze zostaną zaimportowane dla wszystkich kompilacji odpowiedniego typu projektu uruchamianych przy użyciu poświadczeń tego użytkownika. Rozszerzenia użytkownika można wyłączyć, ustawiając właściwości nazwane na c imieniu importowanego pliku we wzorcu `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` . Na przykład ustawienie `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` na to `false` uniemożliwi importowanie `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*` .

## <a name="customize-the-solution-build"></a>Dostosowywanie kompilacji rozwiązania

> [!IMPORTANT]
> Dostosowywanie kompilacji rozwiązania w ten sposób ma zastosowanie tylko do kompilacji wiersza polecenia zMSBuild.exe *.* Nie **dotyczy to** kompilacji wewnątrz Visual Studio. Z tego powodu nie zaleca się dostosowywania na poziomie rozwiązania. Lepszą alternatywą dla dostosowywania wszystkich projektów w rozwiązaniu jest użycie plików *Directory.Build.props* i *Directory.build.targets* w folderze rozwiązania, jak omówiono w innym miejscu tego artykułu.

Gdy program MSBuild tworzy plik rozwiązania, najpierw tłumaczy go wewnętrznie na plik projektu, a następnie tworzy go. Wygenerowany plik projektu importuje przed zdefiniowaniem wszystkich obiektów docelowych i po zaimportowaniu obiektów docelowych, w tym obiektów docelowych zainstalowanych `before.{solutionname}.sln.targets` `after.{solutionname}.sln.targets` w `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` katalogach i .

Można na przykład zdefiniować nowy element docelowy do napisania niestandardowego komunikatu dziennika po utworzeniu pliku *MyCustomizedSolution.sln,* tworząc plik w tym samym katalogu o nazwie *. MyCustomizedSolution.sln.targets,* który zawiera

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

Kompilacja rozwiązania jest oddzielona od kompilacji projektu, więc ustawienia w tym miejscu nie wpływają na kompilacje projektu.

## <a name="customize-all-net-builds"></a>Dostosowywanie wszystkich kompilacji .NET

Podczas konserwacji serwera kompilacji może być konieczne globalne skonfigurowanie ustawień programu MSBuild dla wszystkich kompilacji na serwerze.  W zasadzie można modyfikować globalne pliki *Microsoft.Common.Targets* lub *Microsoft.Common.Props,* ale istnieje lepszy sposób. Możesz wpływać na wszystkie kompilacje określonego typu projektu (na przykład wszystkie projekty języka C#) przy użyciu niektórych właściwości programu MSBuild i dodając określone niestandardowe `.targets` pliki `.props` i .

Aby wpłynąć na wszystkie kompilacje w języku C# lub Visual Basic zarządzane przez instalację programu MSBuild lub programu Visual Studio, utwórz plik *Custom.Before.Microsoft.Common.Targets* lub *Custom.After.Microsoft.Common.Targets* z elementami docelowymi, które będą uruchamiane przed lub po pliku *Microsoft.Common.targets,* albo plik *Custom.Before.Microsoft.Common.Props* lub *Custom.After.Microsoft.Common.Props* z właściwościami, które będą przetwarzane przed lub po *microsoft.Common.props*.

Lokalizacje tych plików można określić przy użyciu następujących właściwości programu MSBuild:

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

Typowe *wersje* tych właściwości mają wpływ zarówno na język C#, jak i Visual Basic projektów. Te właściwości można ustawić w wierszu polecenia programu MSBuild.

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

Najlepsze podejście zależy od scenariusza. Korzystając Visual Studio rozszerzalności, można dostosować system kompilacji i zapewnić mechanizm instalowania dostosowań i zarządzania nimi.

Jeśli masz dedykowany serwer kompilacji i chcesz mieć pewność, że niektóre obiekty docelowe są zawsze wykonywane na wszystkich kompilacjach odpowiedniego typu projektu, które są wykonywane na tym serwerze, użycie globalnego niestandardowego pliku ma `.targets` `.props` sens.  Jeśli chcesz, aby niestandardowe obiekty docelowe wykonywały się tylko wtedy, gdy mają zastosowanie określone warunki, użyj innej lokalizacji pliku i ustaw ścieżkę do tego pliku, ustawiając odpowiednią właściwość MSBuild w wierszu polecenia programu MSBuild tylko wtedy, gdy jest to konieczne.

> [!WARNING]
> Visual Studio używa niestandardowego pliku lub plików, jeśli znajdzie je w folderze MSBuild za każdym razem, gdy tworzy dowolny projekt `.targets` `.props` o zgodnym typie. Może to mieć niezamierzone konsekwencje, a jeśli zostanie wykonane niepoprawnie, może Visual Studio kompilacji na komputerze.

## <a name="customize-c-builds"></a>Dostosowywanie kompilacji języka C++

W przypadku projektów w języku C++ wspomniane wcześniej niestandardowe pliki *targets* i *.props* nie mogą być używane w taki sam sposób, aby przesłaniać ustawienia domyślne. *Plik Directory.Build.props* jest importowany przez plik *Microsoft.Common.props,* który jest importowany w pliku , podczas gdy większość ustawień domyślnych jest zdefiniowanych w pliku Microsoft.Cpp.props i dla wielu właściwości nie można użyć warunku "jeśli jeszcze nie zdefiniowano", ponieważ właściwość jest już zdefiniowana, ale wartość domyślna musi być inna dla określonych właściwości projektu zdefiniowanych w pliku `Microsoft.Cpp.Default.props`  `PropertyGroup` `Label="Configuration"` (zobacz [.vcxproj i .props file structure](/cpp/build/reference/vcxproj-file-structure)).

Można jednak użyć następujących właściwości, aby określić pliki *.props,* które mają być automatycznie importowane przed/po *plikach Microsoft.Cpp.: \**

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

Aby dostosować domyślne wartości właściwości dla wszystkich kompilacji języka C++, utwórz kolejny plik *props* (np. *MyProps.props)* i zdefiniuj właściwość w celu jej `ForceImportAfterCppProps` `Directory.Build.props` określenia:

<PropertyGroup><ForceImportAfterCppProps>$(MsbuildThisFileDirectory)\MyProps.props<ForceImportAfterCppProps>
</PropertyGroup>

*MyProps.props* zostanie automatycznie zaimportowany na samym końcu *pliku Microsoft.Cpp.props.*

## <a name="customize-all-c-builds"></a>Dostosowywanie wszystkich kompilacji języka C++

Dostosowywanie instalacji programu Visual Studio nie jest zalecane, ponieważ śledzenie takich dostosowań nie jest łatwe, ale jeśli rozszerzasz program Visual Studio w celu dostosowania kompilacji języka C++ dla określonej platformy, możesz tworzyć pliki dla każdej platformy i umieszczać je w odpowiednich folderach importu dla tych platform w ramach `.targets` rozszerzenia Visual Studio.

Plik `.targets` dla platformy Win32, *Microsoft.Cpp.Win32.targets,* zawiera następujący `Import` element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

Na końcu tego samego pliku znajduje się podobny element:

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

Podobne elementy importu istnieją dla innych platform docelowych w folderze *%ProgramFiles32%\MSBuild\Microsoft.Cpp\v{wersja}\Platforms. \*

Po umieścić plik w odpowiednim folderze zgodnie z platformą program MSBuild importuje plik do każdej kompilacji `.targets` `ImportAfter` języka C++ dla tej platformy. W razie potrzeby `.targets` można umieścić w tym miejscu wiele plików. 

Korzystając Visual Studio rozszerzalności, możliwe są dalsze dostosowania, takie jak definiowanie nowej platformy. Aby uzyskać więcej informacji, zobacz [C++ project extensibility (Rozszerzalność projektu języka C++).](../extensibility/visual-cpp-project-extensibility.md)

### <a name="specify-a-custom-import-on-the-command-line"></a>Określanie importu niestandardowego w wierszu polecenia

Dla niestandardowych, które chcesz uwzględnić dla określonej kompilacji projektu języka C++ ustaw jedną lub obie właściwości i `.targets` `ForceImportBeforeCppTargets` w `ForceImportAfterCppTargets` wierszu polecenia.

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

W przypadku ustawienia globalnego (na przykład wpływania na wszystkie kompilacje języka C++ dla platformy na serwerze kompilacji) istnieją dwie metody. Najpierw można ustawić te właściwości przy użyciu systemowej zmiennej środowiskowej, która jest zawsze ustawiona. Działa to, ponieważ program MSBuild zawsze odczytuje środowisko i tworzy (lub zastępuje) właściwości dla wszystkich zmiennych środowiskowych.

## <a name="see-also"></a>Zobacz też

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
