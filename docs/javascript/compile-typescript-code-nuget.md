---
title: Kompilowanie i kompilowanie kodu TypeScript przy użyciu narzędzia NuGet
description: Dowiedz się, jak kompilować i kompilować TypeScript w programie Visual Studio.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ac917248915129b8d93dc776ac7d35a2ed227069
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2020
ms.locfileid: "87454604"
---
# <a name="compile-typescript-code-aspnet-core"></a>Kompiluj kod języka TypeScript (ASP.NET Core)

Obsługę języka TypeScript można dodać do swoich projektów przy użyciu TypeScript SDK, która jest domyślnie dostępna w Instalatorze programu Visual Studio lub za pomocą pakietu NuGet. W przypadku projektów utworzonych w programie Visual Studio 2019 zachęcamy do używania języka TypeScript NuGet do większej przenośności na różnych platformach i środowiskach.

W przypadku projektów ASP.NET Core jednym typowym użyciem pakietu NuGet jest kompilowanie kodu TypeScript przy użyciu interfejs wiersza polecenia platformy .NET Core. Chyba że ręcznie edytujesz plik projektu, aby zaimportować cele kompilacji z instalacji TypeScript SDK, pakiet NuGet jest jedynym sposobem włączania kompilacji TypeScript przy użyciu poleceń interfejs wiersza polecenia platformy .NET Core, takich jak `dotnet build` i `dotnet publish` . Ponadto w przypadku [integracji](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) z programem MSBuild przy użyciu ASP.NET Core i języka TypeScript wybierz pakiet NuGet za pośrednictwem pakietu npm.

## <a name="add-typescript-support-with-nuget"></a>Dodawanie obsługi języka TypeScript przy użyciu narzędzia NuGet

[Pakiet NuGet języka TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) dodaje obsługę języka TypeScript. Gdy pakiet NuGet dla języka TypeScript 3,2 lub nowszego jest zainstalowany w projekcie, odpowiednia wersja usługi języka TypeScript zostanie załadowana w edytorze.

Jeśli program Visual Studio jest zainstalowany, node.exe powiązane z nim zostaną automatycznie pobrane przez program Visual Studio. Jeśli nie masz zainstalowanego Node.js, zalecamy zainstalowanie wersji LTS z witryny sieci Web [Node.js](https://nodejs.org/en/download/) .

1. Otwórz projekt ASP.NET Core w programie Visual Studio.

1. W Eksplorator rozwiązań (okienko po prawej). Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zarządzaj pakietami NuGet**. Na karcie **Przeglądaj** Wyszukaj pozycję **Microsoft. TypeScript. MSBuild**, a następnie kliknij pozycję **Zainstaluj** po prawej stronie, aby zainstalować pakiet.

   ![Dodaj pakiet NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Program Visual Studio dodaje pakiet NuGet w węźle **zależności** w Eksplorator rozwiązań. Następujące odwołanie do pakietu zostanie dodane do pliku *. csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **dodaj > nowy element**. Wybierz **plik konfiguracji języka TYPESCRIPT JSON**, a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje *tsconfig.js* do pliku w katalogu głównym projektu. Tego pliku można użyć do [skonfigurowania opcji](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora języka TypeScript.

1. Otwórz *tsconfig.js* i zaktualizuj, aby ustawić odpowiednie opcje kompilatora.

   Poniżej znajduje się przykład prostego *tsconfig.jsw* pliku.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   W tym przykładzie:
   - *include zawiera* informacje o kompilatorze, gdzie można znaleźć pliki TypeScript (*. TS).
   - Opcja *outDir* określa folder wyjściowy dla zwykłych plików JavaScript, które są transstertne przez kompilator języka TypeScript.
   - Opcja *mapy źródła* wskazuje, czy kompilator generuje pliki *mapy źródła* .

   Poprzednia konfiguracja zawiera tylko podstawowe wprowadzenie do konfigurowania języka TypeScript. Aby uzyskać informacje o innych opcjach, zobacz [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Kompilowanie aplikacji

1. Dodaj do projektu pliki TypeScript (*. TS*) lub TypeScript JSX (*. TSX*), a następnie Dodaj kod języka TypeScript. Aby zapoznać się z prostym przykładem języka TypeScript, użyj następujących elementów:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Jeśli używasz starszego projektu typu innego niż zestaw SDK, postępuj zgodnie z instrukcjami w temacie [usuwanie domyślnych importów](#remove-default-imports) przed kompilacją.

1. Wybierz **kompiluj > Kompiluj rozwiązanie**.

   Mimo że aplikacja automatycznie kompiluje się po uruchomieniu, chcemy obejrzeć coś, co się dzieje w trakcie procesu kompilacji:

   Jeśli zostały wygenerowane mapy źródeł, Otwórz folder określony w opcji *outDir* , a następnie Znajdź wygenerowany plik *. js wraz z wygenerowanymi plikami * js. map.

   Pliki mapy źródłowej są wymagane do debugowania.

1. Jeśli chcesz skompilować za każdym razem, gdy zapisujesz projekt, użyj opcji *compileOnSave* w *. tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Aby zapoznać się z przykładem użycia Gulp z modułem uruchamiającego zadań do kompilowania aplikacji, zobacz [ASP.NET Core i TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Jeśli występują problemy, w których program Visual Studio używa wersji Node.js lub narzędzia innej firmy, które różni się od oczekiwanej wersji, może być konieczne ustawienie ścieżki programu Visual Studio do użycia. Wybierz pozycję **Narzędzia**  >  **Opcje**. W obszarze **projekty i rozwiązania**wybierz pozycję **Sieć Web zarządzanie pakietami**  >  **zewnętrzne narzędzia sieci Web**.

### <a name="nuget-package-structure-details"></a>Szczegóły struktury pakietu NuGet

`Microsoft.TypeScript.MSBuild.nupkg`zawiera dwa foldery główne:

- folder *kompilacji*

    W tym folderze znajdują się dwa pliki.
    Oba są punktami wejścia — odpowiednio do pliku głównego języka TypeScript i pliku props.

    1. *Microsoft. TypeScript. MSBuild. targets*

        Ten plik ustawia zmienne, które określają platformę uruchomieniową, taką jak ścieżka do *TypeScript.Tasks.dll*, przed zaimportowaniem pliku *Microsoft. TypeScript. targets* z folderu *Tools* .

    2. *Microsoft. TypeScript. MSBuild. props*

        Ten plik importuje *Microsoft. TypeScript. default. props* z folderu Tools i ustawia właściwości wskazujące, że kompilacja została zainicjowana za pośrednictwem *Narzędzia* NuGet.

- folder *narzędzi*

    Wersje pakietów sprzed 2,3 zawierają tylko folder TSC. *Elementy Microsoft. TypeScript. targets* i *TypeScript.Tasks.dll* znajdują się na poziomie głównym.

    W pakietach w wersji 2,3 i nowszych poziom główny zawiera `Microsoft.TypeScript.targets` i `Microsoft.TypeScript.Default.props` . Aby uzyskać więcej informacji o tych plikach, zobacz [Konfiguracja programu MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Ponadto folder zawiera trzy podfoldery:

    1. *net45*

        Ten folder zawiera `TypeScript.Tasks.dll` i inne biblioteki DLL, od których zależy.
        Podczas kompilowania projektu na platformie Windows program MSBuild używa bibliotek DLL z tego folderu.

    2. *Standard 1.3*

        Ten folder zawiera inną wersję programu `TypeScript.Tasks.dll` , która jest używana podczas kompilowania projektów na komputerze z systemem innym niż Windows.

    3. *TSC*

        Ten folder zawiera `tsc.js` `tsserver.js` i wszystkie pliki zależności wymagane do uruchamiania ich jako skrypty węzłów.

        > [!NOTE]
        > Jeśli jest zainstalowany program Visual Studio, zostanie on automatycznie pobrany z dołączonego *node.exe* . W przeciwnym razie Node.js muszą być zainstalowane na komputerze.

        Wersje wcześniejsze niż 3,1 zawierały `tsc.exe` plik wykonywalny do uruchomienia kompilacji. W wersji 3,1, zostało to usunięte na korzyść użycia `node.exe` .

### <a name="remove-default-imports"></a>Usuń Importy domyślne

W starszych projektach ASP.NET Core, które używają [formatu w stylu innym niż zestaw SDK](https://docs.microsoft.com/nuget/resources/check-project-format), może być konieczne usunięcie niektórych elementów plików projektu.

Jeśli używasz pakietu NuGet do obsługi programu MSBuild dla projektu, plik projektu nie może importować `Microsoft.TypeScript.Default.props` ani `Microsoft.TypeScript.targets` . Pliki zostaną zaimportowane przez pakiet NuGet, dzięki czemu mogą one spowodować niezamierzone zachowanie.

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zwolnij projekt**.

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Edytuj \<*project file name*\> **.

   Plik projektu zostanie otwarty.

1. Usuń odwołania do `Microsoft.TypeScript.Default.props` i `Microsoft.TypeScript.targets` .

   Importy do usunięcia wyglądają podobnie do następujących:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
