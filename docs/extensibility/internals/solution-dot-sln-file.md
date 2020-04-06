---
title: Rozwiązanie (. Sln)
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705331"
---
# <a name="solution-sln-file"></a>Plik rozwiązania (.sln)

Rozwiązanie to struktura organizowania projektów w programie Visual Studio. Rozwiązanie przechowuje informacje o stanie dla projektów w dwóch plikach:

- .sln (tekstowy, udostępniony)

- .suo (binarne, specyficzne dla użytkownika opcje rozwiązania)

Aby uzyskać więcej informacji na temat plików .suo, zobacz [Opcje użytkownika rozwiązania (. Suo) Plik](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Jeśli pakiet VSPackage jest ładowany w wyniku odwołania się do pliku <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln, środowisko wywołuje odczyt w pliku .sln.

Plik .sln zawiera informacje tekstowe używane przez środowisko do znajdowania i ładowania parametrów wartości nazwy dla utrwalonych danych i projektu VSPackages odwołuje się. Gdy użytkownik otworzy rozwiązanie, środowisko przechodzi `preSolution`przez `Project`, `postSolution` i informacje w pliku .sln, aby załadować rozwiązanie, projekty w ramach rozwiązania i wszelkie utrwalone informacje dołączone do rozwiązania.

Plik każdego projektu zawiera dodatkowe informacje odczytywane przez środowisko w celu wypełnienia hierarchii elementami tego projektu. Trwałość danych hierarchii jest kontrolowana przez projekt. Dane zwykle nie są przechowywane w pliku .sln, chociaż w przypadku wybrania tej opcji można celowo zapisać informacje o projekcie w pliku .sln. Aby uzyskać więcej informacji na temat trwałości, zobacz [Trwałość projektu](../../extensibility/internals/project-persistence.md) oraz [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Nagłówek pliku

Nagłówek pliku .sln wygląda następująco:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definicje

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardowy nagłówek definiujący wersję formatu pliku.

`# Visual Studio 15`\
Główna wersja programu Visual Studio, która (ostatnio) zapisała ten plik rozwiązania. Te informacje steruje numer wersji w ikonie rozwiązania.

`VisualStudioVersion = 15.0.26730.15`\
Pełna wersja programu Visual Studio, która (ostatnio) zapisała plik rozwiązania. Jeśli plik rozwiązania jest zapisywany przez nowszą wersję programu Visual Studio, która ma tę samą wersję główną, ta wartość nie jest aktualizowana, aby zmniejszyć zmiany w plikach rozwiązania.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Minimalna (najstarsza) wersja programu Visual Studio, która może otworzyć ten plik rozwiązania.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definicje

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardowy nagłówek definiujący wersję formatu pliku.

`# Visual Studio Version 16`\
Główna wersja programu Visual Studio, która (ostatnio) zapisała ten plik rozwiązania. Te informacje steruje numer wersji w ikonie rozwiązania.

`VisualStudioVersion = 16.0.28701.123`\
Pełna wersja programu Visual Studio, która (ostatnio) zapisała plik rozwiązania. Jeśli plik rozwiązania jest zapisywany przez nowszą wersję programu Visual Studio, która ma tę samą wersję główną, ta wartość nie jest aktualizowana, aby zmniejszyć zmiany w pliku.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Minimalna (najstarsza) wersja programu Visual Studio, która może otworzyć ten plik rozwiązania.

::: moniker-end

## <a name="file-body"></a>Treść pliku

Treść pliku .sln składa się z kilku `GlobalSection`sekcji oznaczonych etykietą , w ten sposób:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Aby załadować rozwiązanie, środowisko wykonuje następującą sekwencję zadań:

1. Środowisko odczytuje sekcję Global pliku .sln i `preSolution`przetwarza wszystkie sekcje oznaczone . W tym przykładowym pliku istnieje jedna taka instrukcja:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Gdy środowisko odczytuje `GlobalSection('name')` tag, mapuje nazwę do VSPackage przy użyciu rejestru. Nazwa klucza powinna istnieć w rejestrze w obszarze [HKLM\\<Application ID Registry Root\>\SolutionPersistence\AggregateGUIDs]. Wartością domyślną kluczy jest identyfikator GUID pakietu (REG_SZ) programu VSPackage, który napisał wpisy.

2. Środowisko ładuje VSPackage, `QueryInterface` wywołuje vspackage dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfejsu i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> wywołuje metodę z danymi w sekcji, dzięki czemu VSPackage można przechowywać dane. Środowisko powtarza ten proces `preSolution` dla każdej sekcji.

3. Środowisko iteruje za pośrednictwem bloków trwałości projektu. W tym przypadku istnieje jeden projekt.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Ta instrukcja zawiera unikatowy identyfikator GUID projektu i identyfikator GUID typu projektu. Te informacje są używane przez środowisko, aby znaleźć plik projektu lub pliki należące do rozwiązania i VSPackage wymagane dla każdego projektu. Identyfikator GUID projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> jest przekazywany do załadowania określonego VSPackage związane z projektem, a następnie projekt jest ładowany przez VSPackage. W takim przypadku VSPackage, który jest ładowany dla tego projektu jest Visual Basic.

   Każdy projekt może utrwalić unikatowy identyfikator wystąpienia projektu, dzięki czemu można uzyskać do niego dostęp zgodnie z potrzebami innych projektów w rozwiązaniu. W idealnym przypadku, jeśli rozwiązanie i projekty są pod kontrolą kodu źródłowego, ścieżka do projektu powinna być względem ścieżki do rozwiązania. Po pierwszym załadowaniu rozwiązania pliki projektu nie mogą znajdować się na komputerze użytkownika. Dzięki przechowywaniu pliku projektu na serwerze względem pliku rozwiązania jest stosunkowo proste, aby plik projektu został znaleziony i skopiowany na komputer użytkownika. Następnie kopiuje i ładuje pozostałe pliki potrzebne do projektu.

4. Na podstawie informacji zawartych w sekcji projektu pliku .sln środowisko ładuje każdy plik projektu. Sam projekt jest następnie odpowiedzialny za wypełnianie hierarchii projektu i ładowanie wszystkich projektów zagnieżdżonych.

5. Po przetworzeniu wszystkich sekcji pliku .sln rozwiązanie jest wyświetlane w Eksploratorze rozwiązań i jest gotowe do modyfikacji przez użytkownika.

Jeśli wszelkie VSPackage, który implementuje projekt w <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> rozwiązaniu nie można załadować, metoda jest wywoływana i każdy inny projekt w rozwiązaniu ma szansę zignorować zmiany, które mogły zostać wprowadzone podczas ładowania. Jeśli wystąpią błędy analizy, jak najwięcej informacji, jak to możliwe jest zachowywane z plikami rozwiązania i środowisko wyświetla okno dialogowe z ostrzeżeniem użytkownika, że rozwiązanie jest uszkodzony.

Po zapisaniu lub zamknięciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> rozwiązania metoda jest wywoływana i przekazywana do hierarchii, aby sprawdzić, czy wprowadzono zmiany w rozwiązaniu, które należy wprowadzić do pliku .sln. Wartość null, przekazana `QuerySaveSolutionProps` do <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>in , wskazuje, że informacje są zachowywane dla rozwiązania. Jeśli wartość nie jest null, utrwalone informacje są dla określonego <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projektu, określone przez wskaźnik do interfejsu.

Jeśli istnieją informacje do zapisania, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejs jest wywoływany ze wskaźnikiem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metody. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> jest następnie wywoływana przez środowisko, aby pobrać `IPropertyBag` pary nazwa-wartość z interfejsu i zapisać informacje w pliku .sln.

`SaveSolutionProps`i `WriteSolutionProps` obiekty są nazywane rekursywnie przez środowisko, `IPropertyBag` aby pobrać informacje, które mają być zapisane z interfejsu, dopóki wszystkie zmiany nie zostaną wprowadzone do pliku .sln. W ten sposób można zapewnić, że informacje będą zachowywane z rozwiązaniem i dostępne przy następnym otwarciu rozwiązania.

Każdy załadowany VSPackage jest wyliczona, aby sprawdzić, czy ma coś do zapisania w pliku .sln. Jest tylko w czasie ładowania, że klucze rejestru są poszukiwane. Środowisko wie o wszystkich załadowanych pakietów, ponieważ są one w pamięci w momencie zapisywania rozwiązania.

Tylko plik .sln zawiera wpisy w sekcjach `preSolution` i. `postSolution` Nie ma podobnych sekcji w pliku .suo, ponieważ rozwiązanie wymaga tych informacji, aby załadować poprawnie. Plik .suo zawiera opcje specyficzne dla użytkownika, takie jak notatki prywatne, które nie są przeznaczone do udostępniania lub umieszczania pod kontrolą kodu źródłowego.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Plik opcji użytkownika rozwiązania (Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Rozwiązania](../../extensibility/internals/solutions-overview.md)
