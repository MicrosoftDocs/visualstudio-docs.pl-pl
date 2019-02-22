---
title: Rozwiązanie (. Plik sln) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 117faeeeeb2dd72d7a59f63c46b27f268bcd8766
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644669"
---
# <a name="solution-sln-file"></a>Plik rozwiązania (Sln)
To rozwiązanie jest strukturą służący do organizowania projektów w programie Visual Studio. Rozwiązanie przechowuje informacje o stanie dla projektów w plikach .suo (opcje rozwiązania binarne, specyficzne dla użytkownika) i SLN (oparte na tekście, udostępniony). Aby uzyskać więcej informacji na temat .suo — pliki Zobacz [opcje użytkownika rozwiązania (. Plik suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).

 Jeśli Twoje pakietu VSPackage jest załadowana w wyniku odwołuje się w pliku .sln, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> do odczytu w pliku .sln.

 Plik sln zawiera informacje oparte na tekście, używanymi środowiska, aby znaleźć i załadować parametrów nazwa wartość utrwalonych danych i projekt odwołuje się do pakietów VSPackage. Po otwarciu rozwiązania środowiska przewijać `preSolution`, `Project`, i `postSolution` informacje zawarte w pliku .sln, ładowanie rozwiązania, projekty w rozwiązaniu i wszelkie informacje utrwalonych dołączonych do rozwiązania.

 Plik każdy projekt zawiera dodatkowe informacje, przeczytaj przez środowisko, aby wypełnić hierarchii z elementami tego projektu. Trwałość danych w hierarchii jest kontrolowany przez projekt; dane nie są zwykle przechowywane w pliku .sln, mimo że można celowo zapisać informacji o projekcie do pliku .sln, jeśli zdecydujesz się to zrobić. Aby uzyskać więcej informacji dotyczących trwałości, zobacz [trwałość projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="solution-file-contents"></a>Zawartość pliku rozwiązania
 Plik SLN składa się z kilku sekcji, jak pokazano w poniższym kodzie.

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

 Aby załadować rozwiązania, środowiska wykonuje następującą sekwencję zadań.

1. Środowisko odczytuje sekcji globalnej pliku .sln i przetwarza wszystkie sekcje oznaczone `preSolution`. W tym przypadku jest jeden taki raport:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

    Gdy środowisko odczytuje `GlobalSection('name')` tagu, jest on mapowany nazwę pakietu VSPackage za pomocą rejestru. Nazwa klucza powinna istnieć w kluczu rejestru [HKLM\\< katalog główny rejestru identyfikator aplikacji\>\SolutionPersistence\AggregateGUIDs]. Wartość domyślna kluczy to identyfikator GUID pakietu (REG_SZ) o pakietu VSPackage, który napisał wpisów.

2. Środowisko ładuje pakietu VSPackage, wywołania `QueryInterface` na VSPackage dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfejsu i wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> metody z danymi w sekcji, dzięki czemu dane można przechowywać pakietu VSPackage. Środowisko powtarza ten proces dla każdej `preSolution` sekcji.

3. Środowisko wykonuje iterację przez bloki trwałość projektu. W tym przypadku jest jeden projekt.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

    Ta instrukcja zawiera unikatowy identyfikator GUID projektu i identyfikator GUID typu projektu. Te informacje są używane przez środowisko, aby znaleźć pliki należące do rozwiązania lub pliku projektu i pakietu VSPackage wymagane dla każdego projektu. Projekt, identyfikator GUID jest przekazywany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> można załadować określonego pakietu VSPackage związanych z projektem, następnie projekt jest ładowany przez pakietu VSPackage. W tym przypadku pakietu VSPackage, który jest ładowany dla tego projektu jest języka Visual Basic.

    Każdy projekt można utrwalić identyfikator wystąpienia unikatowego projektu, tak aby był on dostępny w razie potrzeby przez inne projekty w rozwiązaniu. Najlepiej Jeśli rozwiązanie i projekty są pod kontrolą kodu źródłowego, ścieżka do projektu powinna być określona względem ścieżki do rozwiązania. Po pierwszym załadowaniu rozwiązania, pliki projektu nie może znajdować się na komputerze użytkownika. Problemy pliku projektu, przechowywane na serwerze względem pliku rozwiązania, jest stosunkowo prosta dla pliku projektu, aby znaleźć i kopiowane do komputera użytkownika. Następnie kopiuje i ładuje pozostałe pliki potrzebne do projektu.

4. Na podstawie informacji zawartych w sekcji Projekt pliku .sln, środowiska ładuje każdego pliku projektu. Projekt, sama jest następnie odpowiedzialna za wypełnianie hierarchii projektu i ładowania jakiegokolwiek projektu zagnieżdżonego.

5. Po przetworzeniu wszystkich sekcji pliku SLN, rozwiązanie jest wyświetlany w Eksploratorze rozwiązań i jest gotowy do modyfikacji przez użytkownika.

   W przypadku dowolnego pakietu VSPackage, który implementuje projektu w rozwiązaniu nie można załadować, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> wywoływana jest metoda, a każdy inny projekt w rozwiązaniu otrzymuje szansę, aby zignorować zmiany mogą mieć wprowadzone podczas ładowania. Jeśli wystąpią błędy podczas analizowania, jak najwięcej informacji jest zachowywany z plików rozwiązania i środowiska Wyświetla okno dialogowe z ostrzeżeniem, że rozwiązanie jest uszkodzony.

   Gdy rozwiązanie jest zapisywany lub zamknięte, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> metoda jest nazywana i przekazywana do hierarchii, aby zobaczyć, czy wprowadzono zmiany do rozwiązania, które muszą być wprowadzane do pliku .sln. Wartość null, przekazany do `QuerySaveSolutionProps` w <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, wskazuje on trwałość informacje dotyczące rozwiązania. Jeśli wartość nie jest null, utrwalonych informacje są przeznaczone dla określonego projektu, określane przez wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu.

   Jeśli ma informacji, które mają być zapisywane, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfejsu jest wywoływana za pomocą wskaźnika do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metody. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> Następnie wywoływana jest metoda przez środowisko, które można pobrać par nazwa wartość z `IPropertyBag` interfejs i zapisywanie informacji o pliku .sln.

   `SaveSolutionProps` i `WriteSolutionProps` obiekty są nazywane cyklicznie przez środowisko, aby pobrać informacje do zapisania z `IPropertyBag` interfejsu do momentu wszystkie zmiany zostały wprowadzone w pliku .sln. W ten sposób możesz upewnić się, że informacje zostaną utrwalone za pomocą rozwiązania i dostępne następnym otwarciu rozwiązania.

   Każdy załadowanego pakietu VSPackage są wyliczane Aby sprawdzić, czy ma ona żadnych czynności, aby zapisać do pliku .sln. Jest tylko w czasie ładowania, który badane są tabele kluczy rejestru. Środowiska wie o wszystkie pakiety załadowany, ponieważ są one w pamięci w czasie, rozwiązanie jest zapisywany.

   Tylko plik sln zawiera wpisy w `preSolution` i `postSolution` sekcje. Istnieją nie podobne sekcje w pliku .suo, ponieważ rozwiązanie wymaga tych informacji, aby załadować się poprawnie. Plik .suo zawiera opcje specyficzne dla użytkownika, takie jak informacje o prywatne, które nie powinny być udostępnione lub umieszczone pod kontrolą kodu źródłowego.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Plik opcji użytkownika rozwiązania (Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Rozwiązania](../../extensibility/internals/solutions.md)