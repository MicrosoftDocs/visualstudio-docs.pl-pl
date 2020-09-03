---
title: Rozwiązanie (. Sln) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154961"
---
# <a name="solution-sln-file"></a>Plik rozwiązania (Sln)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozwiązanie to struktura służąca do organizowania projektów w programie Visual Studio. Rozwiązanie utrzymuje informacje o stanie projektów w. sln (opartych na tekście, udostępnionych) i. suo (w przypadku plików binarnych specyficznych dla użytkownika). Aby uzyskać więcej informacji na temat plików. suo, zobacz [Opcje użytkownika rozwiązania (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Jeśli pakietu VSPackage zostanie załadowana w wyniku odwoływania się w pliku. sln, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> do odczytu w pliku. sln.  
  
 Plik. sln zawiera informacje tekstowe, które są wykorzystywane przez środowisko do znajdowania i ładowania parametrów nazwa-wartość dla utrwalonych danych i projektu, do którego się odwołuje. Gdy użytkownik otwiera rozwiązanie, środowisko przeprowadzi przez `preSolution` , `Project` i `postSolution` informacje w pliku. sln, aby załadować rozwiązanie, projekty w ramach rozwiązania oraz wszelkie utrwalone informacje dołączone do rozwiązania.  
  
 Plik każdego projektu zawiera dodatkowe informacje odczytywane przez środowisko w celu zapełnienia hierarchii elementami tego projektu. Trwałość danych hierarchii jest kontrolowana przez projekt; dane nie są zwykle przechowywane w pliku. sln, chociaż można celowo napisać informacje o projekcie do pliku. sln, jeśli zdecydujesz się to zrobić. Aby uzyskać więcej informacji dotyczących trwałości, zobacz temat [trwałość projektu](../../extensibility/internals/project-persistence.md) i [otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Zawartość pliku rozwiązania  
 Plik. sln składa się z kilku sekcji, jak pokazano w poniższym kodzie.  
  
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
  
 Aby załadować rozwiązanie, środowisko wykonuje poniższą sekwencję zadań.  
  
1. Środowisko odczytuje globalną sekcję pliku. sln i przetwarza wszystkie sekcje oznaczone `preSolution` . W takim przypadku istnieje jedna taka instrukcja:  
  
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
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opcje użytkownika rozwiązania (. Suo) — plik](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Rozwiązania](../../extensibility/internals/solutions-overview.md)
