---
title: Uaktualnianie projektów niestandardowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: b222da27d07cc08774a525819edf2d462bd28844
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795496"
---
# <a name="upgrading-custom-projects"></a>Uaktualnianie projektów niestandardowych
W przypadku zmiany dane utrwalone w pliku projektu, między różnymi wersjami programu Visual Studio produktu, a następnie potrzeba do obsługi, uaktualnianie pliku projektu ze starej do nowej wersji. Do obsługi, uaktualniania z można uczestniczyć w **Kreator konwersji Visual Studio**, implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu. Ten interfejs zawiera tylko mechanizm dostępne dla uaktualnienie kopii. W przypadku uaktualniania projektu odbywa się jako część rozwiązania zostanie otwarty. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Interfejs jest implementowany przez fabrykę projektu lub powinien wynosić co najmniej możliwe do uzyskania z fabryki projektu.  
  
 Stary mechanizm, który używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu nadal jest obsługiwany, ale pod względem koncepcyjnym uaktualnia system projektu jako część otwarty projekt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Interfejsu w związku z tym jest wywoływana przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiska, nawet jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs o nazwie lub zaimplementowana. Takie podejście umożliwia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> zaimplementować kopię tylko części uaktualnienia projektu i delegować pozostałej pracy do wykonania w miejscu (prawdopodobnie w nowej lokalizacji), <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu.  
  
 Na przykład implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, zobacz [przykłady VSSDK](../misc/vssdk-samples.md).  
  
 Następujące scenariusze wynikają z uaktualnienia projektu:  
  
-   Jeśli plik jest nowszy format, niż jest możliwe projektu, aplikacja musi zwracać komunikat o błędzie informujący, to. Założono, że starszą wersję produktu — na przykład Visual Studio .NET 2003 — zawiera kod, aby sprawdzić wersję.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody uaktualnienia będzie można zaimplementować jako uaktualnienie w miejscu, przed otwarciem projektu.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody uaktualniania jest implementowany jako uaktualnienie kopii.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołać, a następnie monicie użytkownika przez środowisko do uaktualnienia pliku projektu jako uaktualnienie w miejscu, po otwarciu projektu. Na przykład środowisko monituje użytkownika o uaktualnienie, gdy użytkownik otworzy starszej wersji rozwiązania.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie jest określony w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołać, a następnie musi monitować użytkownika o zaktualizować pliku projektu.  
  
     Oto przykładowy komunikat monitu uaktualnienia:  
  
     "Projekt"%1"został utworzony w starszej wersji programu Visual Studio. Jeśli otworzysz go za pomocą tej wersji programu Visual Studio, nie można go otworzyć ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory  
  
1.  Implementuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, w szczególności <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody w danej implementacji fabryka projektu lub implementacji można wywołać za pomocą implementacji fabryka projektu.  
  
2.  Jeśli chcesz wykonać uaktualnienie w miejscu w ramach rozwiązania, otwierając podać flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametru w swojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.  
  
3.  Jeśli chcesz wykonać uaktualnienie w miejscu w ramach rozwiązania, otwierając podać flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametru w swojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.  
  
4.  Oba kroki 2 i 3, rzeczywisty plik uaktualnienia kroków, za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, można zaimplementować zgodnie z opisem w temacie "Implementowanie `IVsProjectUpgade`" sekcji poniżej, lub możesz delegować uaktualnienia rzeczywistego pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Należy użyć metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> do uaktualnienia powiązane komunikaty dla użytkownika przy użyciu Kreatora migracji programu Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Interfejs jest używany do implementowania dowolny rodzaj uaktualnienia pliku, który musi zostać przeprowadzona w ramach uaktualnienia projektu. Ten interfejs nie jest wywoływana z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale jest dostarczany jako mechanizm do zaktualizowania plików, które są częścią system projektu, ale system projektu może nie być świadome bezpośrednio. Na przykład ta sytuacja może wystąpić, jeśli kompilator związane z plików i właściwości nie są obsługiwane przez ten sam zespół projektowy, obsługujący reszty systemu projektu.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade Implementation  
 Jeśli zaimplementowano systemu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> tylko nie mogą uczestniczyć w **Kreator konwersji Visual Studio**. Jednak nawet w przypadku zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, można nadal delegować uaktualnienia pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacji.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade  
  
1. Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda jest wywoływana przez środowisko, po otwarciu i przed żadnego innego użytkownika w projekcie mogły zostać podjęte działania. Jeśli użytkownik ma już został monit o Uaktualnij rozwiązanie, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga jest przekazywany w `grfUpgradeFlags` parametru. Jeśli użytkownik otworzy projekt bezpośrednio, takie jako przy użyciu **Dodaj istniejący projekt** polecenia, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie zostanie przekazany i projekt musi monitować użytkownika o uaktualnienie.  
  
2. W odpowiedzi na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołanie, musi ocenić projekt, czy plik projektu jest uaktualniany. Jeśli projekt nie trzeba uaktualniać typu projektu do nowej wersji, a następnie można po prostu zwrócenia <xref:Microsoft.VisualStudio.VSConstants.S_OK> flagi.  
  
3. Jeśli projekt należy uaktualnić tego typu projektu do nowej wersji, a następnie należy określić, czy plik projektu może być modyfikowana przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody i przekazywać wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru. Projekt musi wykonać następujące czynności:  
  
   -   Jeśli `VSQueryEditResult` wartości zwracanej w `pfEditCanceled` parametr jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, a następnie można kontynuować uaktualniania, ponieważ mogą być zapisywane w pliku projektu.  
  
   -   Jeśli `VSQueryEditResult` wartości zwracanej w `pfEditCanceled` parametr jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i `VSQueryEditResult` ma wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitu, następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musi zwrócić błąd, ponieważ użytkownicy powinna być rozpoznawana uprawnienia wystawić samodzielnie. Projekt następnie należy wykonać następujące czynności:  
  
        Zgłoś błąd dla użytkownika, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. i zwróć <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> kod błędu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
   -   Jeśli `VSQueryEditResult` wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i `VSQueryEditResultFlags` ma wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitu, a następnie w pliku projektu można wyewidencjonować przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołanie pliku projektu powoduje, że plik jest wyewidencjonowany i najnowszej wersji, które mają zostać pobrane, a następnie projekt nie zostanie zwolniony i ponownie załadowany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Jest ponownie wywoływana metoda po utworzeniu inne wystąpienie projektu. W tym drugim wywołaniu, mogą być zapisywane w pliku projektu na dysku; zalecane jest, że projekt zapisać kopię pliku projektu w poprzednim formacie za pomocą. STARE rozszerzenia, zmiany jego niezbędne uaktualnienia i Zapisz plik projektu w nowym formacie. Ponownie, jeśli w dowolnej części proces uaktualniania zakończy się niepowodzeniem, metoda musi wskazywać, błąd, zwracając <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Powoduje to projekt, aby zostać zwolniony w Eksploratorze rozwiązań.  
  
    Jest ważne zrozumieć pełny proces, który występuje w środowisku, w przypadku, w którym wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (Określanie wartości ReportOnly) metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> flag.  
  
5. Użytkownik próbuje otworzyć plik projektu.  
  
6. Wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.  
  
7. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> zwraca `true`, a następnie wywołania środowiska usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.  
  
8. Wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementacji Otwórz plik i inicjują obiekt projektu, na przykład projektu Project1.  
  
9. Wywołania środowiska użytkownika `IVsProjectUpgrade::UpgradeProject` implementacji, aby ustalić, czy w pliku projektu musi zostać uaktualniony.  
  
10. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru.  
  
11. Zwraca środowiska <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> dla `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> jest ustawiony bit `VSQueryEditResultFlags`.  
  
12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacja wywołuje `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
    To wywołanie może spowodować, że nowa kopia pliku projektu do kasy i pobrać najnowszej wersji, a także konieczności ponownego ładowania pliku projektu. W tym momencie stanie jedna z następujących czynności:  
  
- Jeśli możesz obsługiwać własne ponownie załadować projektu, następnie środowisko wywołuje swoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementacji (VSITEMID_ROOT). Po otrzymaniu tego wywołania Załaduj ponownie pierwsze wystąpienie projektu (projektu Project1), a następnie kontynuować uaktualnianie pliku projektu. Środowisko wie, obsługiwać własne ponownie załadować projektu, jeśli wrócisz `true` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
- Jeśli nie obsługiwać własne ponownie załadować projektu, a następnie wrócisz `false` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). W tym przypadku przed <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>([QEF_ForceEdit_NoPrompting](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True), [QEF_DisallowInMemoryEdits](assetId:///T:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags?qualifyHint=False&autoUpgrade=True),) zwróci wartość, środowisko tworzy kolejny nowy, wystąpienie projektu, na przykład Project2 jako następujące:  
  
  1.  Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> na pierwszy obiekt projektu, projektu Project1, dlatego umieszczanie tego obiektu w stan nieaktywny.  
  
  2.  Wywołania środowiska użytkownika `IVsProjectFactory::CreateProject` implementacji, aby utworzyć drugie wystąpienie projektu o nazwie Project2.  
  
  3.  Wywołania środowiska użytkownika `IPersistFileFormat::Load` implementacji Otwórz plik i zainicjowania drugiego obiektu projektu o nazwie Project2.  
  
  4.  Wywołania środowiska `IVsProjectUpgrade::UpgradeProject` raz drugi w celu określenia, czy obiekt projektu powinny zostać uaktualnione. Jednak to wywołanie nowy, drugie wystąpienie projektu o nazwie Project2. Jest to projekt, który jest otwierany w rozwiązaniu.  
  
      > [!NOTE]
      >  W przypadku pierwszego projektu projektu Project1, jest umieszczany w stan nieaktywny, a następnie musi zwracać <xref:Microsoft.VisualStudio.VSConstants.S_OK> z pierwszego wywołania usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementacji. Zobacz [podstawowego projektu](http://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) dla implementacji `IVsProjectUpgrade::UpgradeProject`.  
  
  5.  Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru.  
  
  6.  Zwraca środowiska <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i można kontynuować uaktualniania, ponieważ mogą być zapisywane w pliku projektu.  
  
  W przypadku awarii do uaktualnienia, zwracają <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> z `IVsProjectUpgrade::UpgradeProject`. Jeśli uaktualnienie nie jest konieczne, lub nie zdecydujesz się na uaktualnienie, należy traktować `IVsProjectUpgrade::UpgradeProject` wywołać jako pusta. Po powrocie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, węzeł zastępczy jest dodawany do rozwiązania dla Twojego projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator konwersji Visual Studio](http://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Uaktualnianie elementów projektu](../misc/upgrading-project-items.md)   
 [Projekty](../extensibility/internals/projects.md)