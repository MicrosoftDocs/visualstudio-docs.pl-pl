---
title: Przykład ImageOptimizer do aktualizowania Visual Studio rozszerzeń
description: Skorzystaj z przykładu, aby dowiedzieć się, jak zaktualizować rozszerzenie Visual Studio do pracy z Visual Studio 2022 (wersja zapoznawcza).
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 12bbc159884c16ea89849e5c97a4b87292f7089d
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602227"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer — aktualizowanie rozszerzenia Visual Studio krok po kroku

[!INCLUDE [preview-note](../includes/preview-note.md)]

Ten przewodnik zawiera wszystkie kroki wymagane do dodania obsługi programu Visual Studio 2022 przy zachowaniu obsługi programu Visual Studio 2019 przy użyciu rozszerzenia Optymalizator obrazów jako analizy przypadku.  
Jest to dokładny przewodnik po linkach zatwierdzania usługi Git do poszczególnych kroków, ale ukończone ściągnięcie można zobaczyć tutaj: [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) .

Na końcu [tego przewodnika dostępne](#other-samples) są również dodatkowe przykłady.

## <a name="step-1---modernize-the-project"></a>Krok 1. Modernizacja projektu

Zobacz [Modernize projektu](update-visual-studio-extension.md#modernize-your-vsix-project).

[git commit e052465](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

Najpierw przesuniemy projekt VSIX i test jednostkowy do programu .NET 4.7.2 na stronie właściwości projektów:

   ![Wersja struktury wybojowa](media/samples/framework-bump.png)

Optymalizator obrazów odwołuje się do niektórych starych niestandardowych pakietów 14.* i 15.*, zamiast tego zainstalujemy pakiet [ `Microsoft.VisualStudio.Sdk` NuGet,](https://www.nuget.org/packages/microsoft.visualstudio.sdk) który konsoliduje wszystkie wymagane odwołania.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

Tworzenie projektu zakończy się pomyślnie i otrzymamy kilka ostrzeżeń wątkowych. Naprawimy te ostrzeżenia, klikając i `ctrl` `.` używając funkcji IntelliSense, aby dodać brakujące wiersze przełączania wątków.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>Krok 2. Refaktoryzacja kodu źródłowego w udostępnionym projekcie

Zobacz [Shared projects (Projekty udostępnione).](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting)

Obsługa programu Visual Studio 2022 wymaga dodania nowego projektu udostępnionego, który będzie zawierać kod źródłowy rozszerzenia, który będzie współużytkowanie między projektami VSIX z programu Visual Studio 2019 i Visual Studio 2022.

1. Dodawanie nowego projektu udostępnionego do rozwiązania

   [git commit abf249d](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Dodawanie udostępnionego projektu](media/samples/add-shared-project.png)

1. Dodaj odwołanie do udostępnionego projektu do projektu VSIX.

   [git commit e8e941e](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Dodawanie udostępnionego odwołania do projektu" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Przenieś pliki kodu źródłowego (cs, xaml, resx) do nowego udostępnionego projektu **z wyjątkiem** następujących:
    - `source.extension.vsixmanifest`
    - Pliki metadanych rozszerzenia (ikony, licencje, informacje o wersji itp.)
    - Pliki VSCT
    - Połączone pliki
    - Zewnętrzne narzędzia lub biblioteki, które muszą zostać uwzględnione w vsix

   [git commit f31f051](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Przenoszenie plików do projektu udostępnionego](media/samples/move-to-shared-project.png)

1. Teraz przenieś wszystkie metadane, pliki VSCT, połączone pliki oraz zewnętrzne narzędzia/biblioteki do lokalizacji udostępnionej i dodaj je z powrotem jako połączone elementy do projektu VSIX. **Nie usuwaj** `source.extension.vsixmanifest` .

   [git commit 73ba920 — przenoszenie plików](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git commit d5e36b2 — dodawanie zewnętrznych narzędzi/bibliotek](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. W tym projekcie musimy przenieść ikonę rozszerzenia, plik VSCT i narzędzia zewnętrzne do nowego folderu `ImageOptimizer\Resources` . Skopiuj je do folderu udostępnionego i usuń z projektu VSIX.
   1. Dodano je z powrotem jako połączone elementy i jeśli elementy są już połączonymi elementami, mogą pozostać bez nich (na przykład licencja).
   1. Sprawdź, czy akcja kompilacji i inne właściwości są poprawnie ustawione w dodanych połączonych plikach, zaznaczając każdy z nich i sprawdzając okno narzędzia właściwości. W naszym projekcie musieliśmy ustawić następujące elementy:
       - Ustaw `icon.png` akcję kompilacji na wartość `Content` i oznacz jako Uwzględnij w VSIX wartość `true`
       - Ustaw `ImageOptimizer.vsct` akcję kompilacji na `VSCTComplile` i uwzględnij w VSIX na `false`
       - Ustaw całą akcję kompilacji plików w obszarze na i oznacz `Resources\Tools` `Content` jako Uwzględnij w VSIX wartość `true`

           ![Dodawanie połączonych plików do projektu VSIX](media/samples/add-linked-files.png)

       - Ponadto jest to zależność typu , w tym celu musimy ręcznie dodać tę zależność `ImageOptimizer.cs` `ImageOptimizer.vsct` do pliku csproj:

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Jeśli okno narzędzia właściwości uniemożliwia ustawienie konkretnej akcji kompilacji, możesz ręcznie zmodyfikować pliki csproj zgodnie z powyższymi ustawieniami i ustawić akcję kompilacji zgodnie z potrzebami.

1. Skompilowanie projektu w celu zweryfikowania zmian i rozwiązania wszelkich błędów/problemów. Zapoznaj się z [sekcją często zadawanych pytań,](update-visual-studio-extension.md#q--a) aby uzyskać informacje o typowych problemach.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>Krok 3. Dodawanie Visual Studio VSIX 2022

Zobacz [Dodawanie Visual Studio docelowego 2022.](update-visual-studio-extension.md#add-a-visual-studio-2022-target)

1. Dodaj nowy projekt VSIX do rozwiązania.
1. Usuń dodatkowy kod źródłowy w nowym projekcie z wyjątkiem `source.extension.vsixmanifest.`

   ![Tworzenie nowego projektu VSIX](media/samples/visual-studio-2022-vsix-initial.png)

1. Dodaj odwołanie do udostępnionego projektu.

   [git commit dd49cb2](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Dodawanie odwołania do projektu udostępnionego" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Dodaj połączone pliki z projektu VSIX Visual Studio 2019 i sprawdź, czy ich właściwości "Akcja kompilacji" i "Uwzględnij w VSIX" są zgodne. Skopiuj również plik , modyfikujemy go później, aby obsługi Visual Studio `source.extension.vsixmanifest` 2022 r.

   [git commit 98c43ee](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![Dodawanie połączonych plików do projektu VSIX](media/samples/visual-studio-2022-add-linked-files.png)

1. Próba kompilacji pokazuje, że brakuje odwołania do `System.Windows.Forms` . Wystarczy dodać go do naszego projektu Visual Studio 2022 i ponownie skompilować.

   [git commit de71ccd](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. Uaktualnianie `Microsoft.VisualStudio.SDK` i odwołania do pakietów Visual Studio wersji `Microsoft.VSSDK.BuildTools` 2022.

   [git commit d581fc3](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Są to najnowsze wersje dostępne podczas tworzenia tego przewodnika. Zalecane jest, aby uzyskać najnowsze dostępne wersje.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Edytuj `source.extension.vsixmanifest` plik, aby odzwierciedlić docelowy Visual Studio 2022 r.

   [git commit 9d393c7](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Ustaw `<InstallationTarget>` tag w celu odzwierciedlenia Visual Studio 2022 r. i wskaż ładunek amd64:

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Zmodyfikuj wymaganie wstępne, aby uwzględnić tylko Visual Studio 2022 i więcej:

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

I gotowe!

Dzięki temu tworzenie powoduje teraz tworzenie obu Visual Studio 2019 i Visual Studio VSIXes 2022.

## <a name="other-samples"></a>Inne przykłady

- [Narzędzia ProPower](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Umożliwia wgląd w przeglądarkę internetową z informacjami pomocy o wybranej klasie/obiekcie.
  - FixMixedTabs
    - Skanuje dokumenty i zastępuje karty spacjami lub odwrotnie

## <a name="next-steps"></a>Następne kroki

Przygotuj się do zaktualizowania rozszerzenia, czytając ten przewodnik od początku [do końca.](update-visual-studio-extension.md)
