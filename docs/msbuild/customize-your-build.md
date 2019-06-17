---
title: Dostosowywanie kompilacji | Dokumentacja firmy Microsoft
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e644fd6fc521318512bbc5dd25838a379af78a9
ms.sourcegitcommit: dd3c8cbf56c7d7f82f6d8818211d45847ab3fcfc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141169"
---
# <a name="customize-your-build"></a>Dostosowywanie kompilacji

Proces kompilacji projektów MSBuild, które używają standardowych (importowanie *Microsoft.Common.props* i *Microsoft.Common.targets*) ma kilka punkty zaczepienia rozszerzalności, których można użyć w celu dostosowania kompilacji proces.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Dodaj argumenty wiersza polecenia wywołań programu MSBuild w projekcie

A *Directory.Build.rsp* pliku w lub powyżej katalogu źródłowego zostaną zastosowane do kompilacji z wiersza polecenia projektu. Aby uzyskać więcej informacji, zobacz [pliki odpowiedzi MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props i Directory.Build.targets

Przed MSBuild wersji 15 Jeśli chcesz podać nowe, niestandardowe właściwości do projektów w rozwiązaniu, trzeba było ręcznie Dodaj odwołanie do tej właściwości do każdego pliku projektu w rozwiązaniu. Czy zdefiniować właściwość w *.props* pliku, a następnie zaimportuj jawnie *.props* pliku każdego projektu w rozwiązaniu, między innymi.

Jednak teraz możesz dodać nową właściwość do każdego projektu w jednym kroku, definiując je w pojedynczy plik o nazwie *Directory.Build.props* w folderze głównym, który zawiera Twoje źródło. Po uruchomieniu programu MSBuild *Microsoft.Common.props* wyszukuje struktury katalogów dla *Directory.Build.props* pliku (i *Microsoft.Common.targets* szuka *Directory.Build.targets*). Jeśli zostanie znaleziony, importuje właściwości. *Directory.Build.props* jest plikiem zdefiniowanych przez użytkownika zawiera dostosowania do projektów w katalogu.

> [!NOTE]
> Systemy plików z systemem Linux jest rozróżniana wielkość liter. Upewnij się, że wielkość liter w wyrazie Directory.Build.props filename dokładnie odpowiada lub nie zostanie wykryty w procesie kompilacji.
>
> Zobacz [problem w usłudze GitHub](https://github.com/dotnet/core/issues/1991#issue-368441031) Aby uzyskać więcej informacji.

### <a name="directorybuildprops-example"></a>Przykład Directory.Build.props

Na przykład, jeśli chcesz włączyć wszystkie Twoje projekty dostęp do nowych Roslyn **/ deterministic** funkcji (która jest widoczna w Roslyn `CoreCompile` docelowego przez właściwość `$(Deterministic)`), można wykonać następujące czynności.

1. Utwórz nowy plik w folderze głównym repozytorium o nazwie *Directory.Build.props*.
2. Dodaj następujący kod XML do pliku.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. Uruchom program MSBuild. Importy istniejącego projektu *Microsoft.Common.props* i *Microsoft.Common.targets* znaleźć pliku i zaimportuj go.

### <a name="search-scope"></a>Zakres wyszukiwania

Podczas wyszukiwania *Directory.Build.props* pliku, MSBuild przedstawia strukturę katalogów do góry z lokalizacji projektu (`$(MSBuildProjectFullPath)`), trwa zatrzymywanie po zlokalizuje *Directory.Build.props* plik. Na przykład jeśli Twoja `$(MSBuildProjectFullPath)` został *c:\users\username\code\test\case1*, MSBuild rozpocząć wyszukiwanie istnieje, i następnie wyszukiwania struktury katalogów w górę, dopóki znajduje się *Directory.Build.props* pliku, jak następującą strukturę katalogów.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Lokalizacja pliku rozwiązania nie ma znaczenia *Directory.Build.props*.

### <a name="import-order"></a>Kolejność importu

*Directory.Build.props* jest zaimportowana bardzo wczesnym *Microsoft.Common.props*, a właściwości zdefiniowane w dalszej części są niedostępne do niego. Tak należy unikać odnoszące się do właściwości, które nie zostały jeszcze zdefiniowane (i oceni pusty).

*Directory.Build.targets* została zaimportowana z *Microsoft.Common.targets* po zaimportowaniu *.targets* pliki z pakietów NuGet. Tak można zastąpić, właściwości i obiektów docelowych określonych w większości logikę kompilacji, ale czasami konieczne może być Dostosowywanie pliku projektu po zaimportowaniu końcowej.

### <a name="use-case-multi-level-merging"></a>Przypadek użycia: scalanie wielopoziomowe

Załóżmy, że ta struktura standardowe rozwiązanie:

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

Może być wskazane zastosowanie właściwości wspólne dla wszystkich projektów *(1)* , typowe właściwości *src* projektów *(2-src)* oraz typowe właściwości  *Testowanie* projektów *(2-test)* .

Aby poprawnie scalić "wewnętrzny" pliki programu MSBuild (*2 src* i *2 test*) z plikiem "zewnętrzny" (*1*), należy wziąć pod uwagę, o których raz MSBuild znajduje *Directory.Build.props* plik przestanie dalsze skanowanie. Aby kontynuować skanowanie i scalić do zewnętrznego pliku, umieść ten kod w obu plikach wewnętrzny:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Podsumowanie w MSBuild, ogólne podejście jest następująca:

- Dla każdego projektu w serwisie MSBuild wyszukuje pierwszy *Directory.Build.props* w górę w strukturze rozwiązania scala je przy użyciu ustawień domyślnych i zatrzymuje skanowanie, aby uzyskać więcej informacji
- Jeśli chcesz, aby wiele poziomów, aby znaleźć i scalone, następnie [ `<Import...>` ](../msbuild/property-functions.md#msbuild-getpathoffileabove) (jak pokazano powyżej) "zewnętrzny" plik z pliku "wewnętrzny"
- Jeśli plik "zewnętrzny" jest sam nie również zaimportować coś, co powyżej, następnie skanowanie zatrzymuje
- Aby kontrolować proces skanowania scalania, należy użyć `$(DirectoryBuildPropsPath)` i `$(ImportDirectoryBuildProps)`

Lub po prostu: pierwszy *Directory.Build.props* , nie importuje wszystko to, gdzie zatrzymuje programu MSBuild.

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>Wybieranie między Dodawanie właściwości do pliku .props i .targets

Program MSBuild jest kolejność importu zależnej od i ostatnia definicja właściwości (lub `UsingTask` lub docelowa) jest definicja używane.

Korzystając z jawnych importów, można importować z *.props* lub *.targets* pliku w dowolnym momencie. W tym miejscu jest powszechnie używanych Konwencji:

- *.props* pliki są importowane wcześnie w poleceniu importu.

- *.TARGETS* pliki są importowane w kolejności kompilacji.

Ta konwencja jest wymuszana przez `<Project Sdk="SdkName">` importuje (oznacza to, że importowanie *Sdk.props* wykorzystasz, zanim wszystkie zawartość pliku, następnie *Sdk.targets* pochodzi ostatniego, po dokonaniu wszystkich zawartości Plik).

Podejmując decyzję umieścić właściwości, należy użyć następujących ogólnych wytycznych:

- Wiele właściwości nie ma znaczenia, gdzie one są zdefiniowane, ponieważ nie są zastępowane i będzie można ich odczytać tylko w czasie wykonywania.

- W przypadku zachowanie, które mogą być dostosowane na platformie pojedynczego projektu, należy ustawić wartości domyślne w *.props* plików.

- Należy unikać ustawiania właściwości zależnych *.props* pliki, odczytując wartości właściwości prawdopodobnie dostosowane, ponieważ dostosowania nie nastąpi aż MSBuild odczytuje projektu użytkownika.

- Ustaw właściwości zależne *.targets* plików, ponieważ będzie wznowiona dostosowania z indywidualnymi projektami.

- Jeśli musisz zastąpić właściwości odbywa się w *.targets* pliku po wszystkie dostosowania projektu użytkownika miał(a) Pan(i) zaczęły obowiązywać. Należy zachować ostrożność podczas przy użyciu pochodne właściwości; pochodne właściwości może być konieczne można także zastąpić.

- Uwzględnij elementy w *.props* plików (można korzystać we właściwości). Wszystkie właściwości są wziąć pod uwagę przed dowolny element, tak aby dostosowania właściwości projektu użytkownika uzyskać pobierane i daje możliwość projektu użytkownika `Remove` lub `Update` dowolny element dołączonych za pomocą importowania.

- Definiowanie elementów docelowych w *.targets* plików. Jednak jeśli *.targets* plików zaimportowanych przez zestaw SDK, należy pamiętać, że w tym scenariuszu sprawia, że zastępowanie docelowej trudniejsze, ponieważ projekt użytkownika nie ma miejsce do jej zastąpienie domyślnie.

- Jeśli to możliwe najpierw Dostosowywanie właściwości w czasie oceny za pośrednictwem zmiana właściwości wewnątrz elementu docelowego. Ta wytyczna ułatwia ładowania projektu i zrozumieć, jakie jest zastosowanie.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

Domyślnie *Microsoft.Common.props* importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props` i *Microsoft.Common.targets* importuje `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. Wartość domyślna `MSBuildProjectExtensionsPath` jest `$(BaseIntermediateOutputPath)`, `obj/`. NuGet korzysta z tego mechanizmu do odwoływania się do tworzenia logiki oferowane przez pakiety; oznacza to, w czasie przywracania tworzy `{project}.nuget.g.props` pliki, które odwołują się do zawartości pakietu.

Możesz wyłączyć ten mechanizm rozszerzalności, ustawiając właściwość `ImportProjectExtensionProps` do `false` w *Directory.Build.props* lub przed zaimportowaniem *Microsoft.Common.props*.

> [!NOTE]
> Wyłączenie Importy MSBuildProjectExtensionsPath uniemożliwia logikę kompilacji dostarczanych w pakietach NuGet z zastosowania do projektu. Niektóre pakiety NuGet wymagają logikę kompilacji do wykonywania ich funkcji i będzie renderowana bezcelowe gdy ta opcja jest wyłączona.

## <a name="user-file"></a>plik .user, odnoszący

*Microsoft.Common.CurrentVersion.targets* importuje `$(MSBuildProjectFullPath).user` Jeśli istnieje, aby można było utworzyć plik obok projektu za pomocą tego dodatkowe rozszerzenia. Długoterminowe zmian, które planujesz zaewidencjonować w kontroli źródła najpierw zmiany w samym projekcie, tak, aby w przyszłości maintainers nie trzeba wiedzieć o tego mechanizmu rozszerzenia.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath i MSBuildUserExtensionsPath

> [!WARNING]
> Za pomocą tych mechanizmów rozszerzenia utrudnia można pobrać powtarzalnych kompilacji na komputerach. Spróbuj użyć konfiguracji, które mogą być sprawdzone w systemie kontroli źródła współdzielona przez wszystkich deweloperów bazy kodu.

Zgodnie z Konwencją wiele głównych importowania plików logikę kompilacji

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

przed ich zawartość i

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

później. Ta Konwencja umożliwia zainstalowanych zestawów SDK rozszerzyć logikę kompilacji popularnych typów projektów.

Tej samej struktury katalogów jest przeszukiwany w `$(MSBuildUserExtensionsPath)`, czyli do folderu na użytkownika *%LOCALAPPDATA%\Microsoft\MSBuild*. Pliki umieszczone w tym folderze zostaną zaimportowane dla wszystkich kompilacji odpowiedniego typu projektu, uruchom w ramach poświadczeń użytkownika. Możesz wyłączyć rozszerzenia użytkownika przez ustawienie właściwości o nazwie po importowania pliku we wzorcu `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Na przykład ustawienie `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` do `false` uniemożliwiłyby importowania `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Dostosowywanie kompilacji rozwiązania

> [!IMPORTANT]
> Dostosowywanie kompilacji rozwiązania, w ten sposób stosuje się tylko do narzędzia wiersza polecenia kompilacji z *MSBuild.exe*. Jego **nie** dotyczą kompilacje w programie Visual Studio.

Gdy MSBuild tworzy pliku rozwiązania, najpierw tłumaczy to wewnętrznie do pliku projektu, a następnie kompilacji. Importuje plik wygenerowanego projektu `before.{solutionname}.sln.targets` przed zdefiniowaniem wszystkich obiektów docelowych i `after.{solutionname}.sln.targets` po zaimportowaniu elementów docelowych, tym cele, które zainstalowano na `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` i `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` katalogów.

Na przykład można zdefiniować nowy obiekt docelowy, aby zapisać dziennik niestandardowy komunikat po kompilacji *MyCustomizedSolution.sln* przez utworzenie pliku w tym samym katalogu o nazwie *po. MyCustomizedSolution.sln.targets* zawierający

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)

- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
