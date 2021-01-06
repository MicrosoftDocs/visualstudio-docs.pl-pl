---
title: Rozwiązanie (. Sln) — plik
description: Zapoznaj się z plikiem. sln, który jest jednym z plików, które utrzymują informacje o stanie projektu w programie Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 903b33d72d3a97eb4ed3f7ad0bc865999bee54cf
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877510"
---
# <a name="solution-sln-file"></a>Plik rozwiązania (. sln)

Rozwiązanie to struktura służąca do organizowania projektów w programie Visual Studio. Rozwiązanie utrzymuje informacje o stanie projektów w dwóch plikach:

- plik SLN (oparty na tekście, udostępniony)

- plik. suo (dane binarne — opcje rozwiązania specyficzne dla użytkownika)

Aby uzyskać więcej informacji na temat plików. suo, zobacz [Opcje użytkownika rozwiązania (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Jeśli pakietu VSPackage zostanie załadowana w wyniku odwoływania się w pliku. sln, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> do odczytu w pliku. sln.

Plik. sln zawiera informacje tekstowe, które są wykorzystywane przez środowisko do znajdowania i ładowania parametrów nazwa-wartość dla utrwalonych danych i projektu, do którego się odwołuje. Gdy użytkownik otwiera rozwiązanie, środowisko przeprowadzi przez `preSolution` , `Project` i `postSolution` informacje w pliku. sln, aby załadować rozwiązanie, projekty w ramach rozwiązania oraz wszelkie utrwalone informacje dołączone do rozwiązania.

Plik każdego projektu zawiera dodatkowe informacje odczytywane przez środowisko w celu zapełnienia hierarchii elementami tego projektu. Trwałość danych hierarchii jest kontrolowana przez projekt. Dane nie są zwykle przechowywane w pliku. sln, chociaż można celowo napisać informacje o projekcie do pliku. sln, jeśli zdecydujesz się to zrobić. Aby uzyskać więcej informacji na temat trwałości, zobacz temat [trwałość projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Nagłówek pliku

Nagłówek pliku. sln wygląda następująco:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definicje

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Standardowy nagłówek, który definiuje wersję formatu pliku.

`# Visual Studio 15`\
Wersja główna programu Visual Studio, która ostatnio zapisała ten plik rozwiązania. Te informacje kontrolują numer wersji w ikonie rozwiązania.

`VisualStudioVersion = 15.0.26730.15`\
Pełna wersja programu Visual Studio, która ostatnio zapisała plik rozwiązania. Jeśli plik rozwiązania zostanie zapisany przez nowszą wersję programu Visual Studio, która ma tę samą wersję główną, ta wartość nie zostanie zaktualizowana w celu zmniejszenia liczby zmian w plikach rozwiązania.

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
Standardowy nagłówek, który definiuje wersję formatu pliku.

`# Visual Studio Version 16`\
Wersja główna programu Visual Studio, która ostatnio zapisała ten plik rozwiązania. Te informacje kontrolują numer wersji w ikonie rozwiązania.

`VisualStudioVersion = 16.0.28701.123`\
Pełna wersja programu Visual Studio, która ostatnio zapisała plik rozwiązania. Jeśli plik rozwiązania zostanie zapisany przez nowszą wersję programu Visual Studio, która ma tę samą wersję główną, ta wartość nie zostanie zaktualizowana, aby zmniejszyć liczbę zmian w pliku.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Minimalna (najstarsza) wersja programu Visual Studio, która może otworzyć ten plik rozwiązania.

::: moniker-end

## <a name="file-body"></a>Treść pliku

Treść pliku. sln składa się z kilku sekcji oznaczonych jako `GlobalSection` :

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

1. Środowisko odczytuje globalną sekcję pliku. sln i przetwarza wszystkie sekcje oznaczone `preSolution` . W tym przykładowym pliku istnieje jedna taka instrukcja:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Gdy środowisko odczytuje `GlobalSection('name')` tag, mapuje nazwę na pakietu VSPackage przy użyciu rejestru. Nazwa klucza powinna istnieć w rejestrze w obszarze [HKLM \\<identyfikator aplikacji Registry root \> \SolutionPersistence\AggregateGUIDs]. Wartość domyślna kluczy jest identyfikatorem GUID pakietu (REG_SZ) pakietu VSPackage, który napisał wpisy.

2. Środowisko ładuje pakietu VSPackage, wywołuje `QueryInterface` pakietu VSPackage dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfejsu i wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> metodę z danymi w sekcji, dzięki czemu pakietu VSPackage może przechowywać dane. Środowisko powtarza ten proces dla każdej `preSolution` sekcji.

3. Środowisko wykonuje iterację bloków trwałości projektu. W takim przypadku istnieje jeden projekt.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Ta instrukcja zawiera unikatowy identyfikator GUID projektu i identyfikator GUID typu projektu. Te informacje są używane przez środowisko do znajdowania pliku projektu lub plików należących do rozwiązania oraz pakietu VSPackage wymaganych dla każdego projektu. Identyfikator GUID projektu jest przesyłany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> w celu załadowania konkretnych pakietu VSPackage związanych z projektem, a następnie projekt jest ładowany przez pakietu VSPackage. W takim przypadku pakietu VSPackage, który jest ładowany dla tego projektu jest Visual Basic.

   Każdy projekt może utrwalać unikatowy identyfikator wystąpienia projektu, aby można było uzyskać do niego dostęp zgodnie z wymaganiami innych projektów w rozwiązaniu. Najlepiej, jeśli rozwiązanie i projekty znajdują się pod kontrolą kodu źródłowego, ścieżka do projektu powinna być względna względem ścieżki do rozwiązania. Po pierwszym załadowaniu rozwiązania pliki projektu nie mogą znajdować się na komputerze użytkownika. Posiadanie pliku projektu przechowywanego na serwerze względem pliku rozwiązania jest stosunkowo proste dla pliku projektu, który ma zostać odnaleziony i skopiowany do komputera użytkownika. Następnie kopiuje i ładuje pozostałe pliki niezbędne do projektu.

4. Na podstawie informacji zawartych w sekcji projektu pliku. sln środowisko ładuje każdy plik projektu. Sam projekt jest odpowiedzialny za wypełnienie hierarchii projektu i załadowanie dowolnych zagnieżdżonych projektów.

5. Po przetworzeniu wszystkich sekcji pliku. sln rozwiązanie jest wyświetlane w Eksplorator rozwiązań i jest gotowe do modyfikacji przez użytkownika.

Jeśli jakiekolwiek pakietu VSPackage implementujące projekt w rozwiązaniu nie zostaną załadowane, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> Metoda jest wywoływana, a każdy inny projekt w rozwiązaniu otrzymuje szansę ignorowania zmian, które mogły zostać wprowadzone podczas ładowania. W przypadku wystąpienia błędów analizy ilość informacji, jak to możliwe, jest zachowywana wraz z plikami rozwiązania, a środowisko wyświetla okno dialogowe z ostrzeżeniem, że rozwiązanie jest uszkodzone.

Gdy rozwiązanie zostanie zapisane lub zamknięte, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Metoda jest wywoływana i przenoszona do hierarchii, aby sprawdzić, czy wprowadzono zmiany w rozwiązaniu, które należy wprowadzić do pliku. sln. Wartość null, przeniesiona do wartości `QuerySaveSolutionProps` w <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , wskazuje, że informacje są utrwalane dla rozwiązania. Jeśli wartość nie jest równa null, utrwalone informacje są dla określonego projektu, określane przez wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu.

Jeśli informacje mają być zapisane, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejs jest wywoływany ze wskaźnikiem do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metody. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>Metoda jest następnie wywoływana przez środowisko w celu pobrania par nazwa-wartość z `IPropertyBag` interfejsu i zapisania informacji w pliku. sln.

`SaveSolutionProps``WriteSolutionProps`obiekty i są wywoływane cyklicznie przez środowisko w celu pobierania informacji do zapisania z interfejsu, `IPropertyBag` dopóki wszystkie zmiany nie zostaną wprowadzone do pliku. sln. W ten sposób można upewnić się, że informacje zostaną utrwalone wraz z rozwiązaniem i dostępne po następnym otwarciu rozwiązania.

Każdy załadowany pakietu VSPackage jest wyliczany, aby zobaczyć, czy ma coś, co ma być zapisane w pliku sln. Jest to możliwe tylko w czasie ładowania, w którym są wykonywane zapytania o klucze rejestru. Środowisko wie o wszystkich załadowanych pakietach, ponieważ znajdują się w pamięci w momencie zapisania rozwiązania.

Tylko plik. sln zawiera wpisy w `preSolution` `postSolution` sekcjach i. Nie ma podobnych sekcji w pliku. suo, ponieważ rozwiązanie wymaga poprawnego załadowania tych informacji. Plik. suo zawiera opcje specyficzne dla użytkownika, takie jak notatki prywatne, które nie są przeznaczone do udostępniania lub umieszczane pod kontrolą kodu źródłowego.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Plik opcji użytkownika rozwiązania (Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Rozwiązania](../../extensibility/internals/solutions-overview.md)
