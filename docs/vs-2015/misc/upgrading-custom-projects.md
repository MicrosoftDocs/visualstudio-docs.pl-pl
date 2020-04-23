---
title: Uaktualnianie projektów niestandardowych | Dokumenty firmy Microsoft
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
ms.openlocfilehash: c91013e7d5650e82fd9e5f6e39e28c4609e4fbfe
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037210"
---
# <a name="upgrading-custom-projects"></a>Uaktualnianie projektów niestandardowych
Jeśli zmienisz informacje utrwalone w pliku projektu między różnymi wersjami programu Visual Studio produktu, należy obsługiwać uaktualnianie pliku projektu ze starej do nowej wersji. Aby obsługiwać uaktualnianie, które umożliwia uczestnictwo w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> **Kreatorze konwersji programu Visual Studio,** zaimplementuj interfejs. Ten interfejs zawiera jedyny mechanizm dostępny do uaktualniania kopii. Modernizacja projektu odbywa się jako część rozwiązania otwiera. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> jest realizowany przez fabrykę projektu lub powinien być przynajmniej zyskiwany z fabryki projektu.  
  
 Stary mechanizm, który <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> używa interfejsu jest nadal obsługiwany, ale koncepcyjnie uaktualnia system projektu jako część projektu otwarte. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> jest zatem wywoływany [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przez środowisko, nawet jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs jest wywoływany lub implementowany. Takie podejście umożliwia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> zaimplementowanie kopiowania i projektu tylko części uaktualnienia i delegowania pozostałą część pracy, które <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> mają być wykonane w miejscu (ewentualnie w nowej lokalizacji) przez interfejs.  
  
 Aby uzyskać przykładową implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, zobacz [przykłady VSSDK](../misc/vssdk-samples.md).  
  
 Następujące scenariusze powstają z uaktualnień projektu:  
  
- Jeśli plik jest nowszym formatem niż projekt może obsługiwać, następnie musi zwrócić błąd stwierdzający to. Zakłada się, że starsza wersja produktu — na przykład Visual Studio .NET 2003 — zawiera kod, aby sprawdzić, czy wersja.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flaga jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> określona w metodzie, uaktualnienie zostanie zaimplementowane jako uaktualnienie w miejscu przed otwarciem projektu.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flaga jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> określona w metodzie, uaktualnienie jest implementowane jako uaktualnienie kopii.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> określona w wywołaniu, użytkownik został poproszony przez środowisko o uaktualnienie pliku projektu jako uaktualnienia w miejscu, po otwarciu projektu. Na przykład środowisko monituje użytkownika o uaktualnienie, gdy użytkownik otworzy starszą wersję rozwiązania.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> określona w wywołaniu, należy monitować użytkownika o uaktualnienie pliku projektu.  
  
     Poniżej znajduje się przykładowy komunikat monitu o uaktualnienie:  
  
     "Projekt '%1' został utworzony przy starszej wersji programu Visual Studio. Jeśli otworzysz go za pomocą tej wersji programu Visual Studio, może nie być można otworzyć go ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory  
  
1. Zaimplementuj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, w szczególności <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodę w implementacji fabryki projektu lub spraw, aby implementacje były wywoływane z implementacji fabryki projektu.  
  
2. Jeśli chcesz wykonać uaktualnienie w miejscu jako część otwierania rozwiązania, `VSPUVF_FLAGS` podaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako parametr w implementacji.  
  
3. Jeśli chcesz wykonać uaktualnienie w miejscu jako część otwierania rozwiązania, `VSPUVF_FLAGS` podaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako parametr w implementacji.  
  
4. Dla obu kroków 2 i 3, rzeczywiste <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>kroki uaktualniania pliku, za pomocą `IVsProjectUpgade`, można zaimplementować zgodnie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>opisem w sekcji "Implementowanie" poniżej, lub można delegować rzeczywiste uaktualnienie pliku do .  
  
5. Użyj metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> publikowania wiadomości powiązanych z uaktualnieniem dla użytkownika za pomocą Kreatora migracji programu Visual Studio.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>interfejs jest używany do implementacji wszelkiego rodzaju aktualizacji plików, które muszą się zdarzyć w ramach aktualizacji projektu. Ten interfejs nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>jest wywoływany z programu , ale jest dostarczany jako mechanizm uaktualniania plików, które są częścią systemu projektu, ale główny system projektu może nie być bezpośrednio świadomy. Na przykład taka sytuacja może wystąpić, jeśli pliki i właściwości związane z kompilatorem nie są obsługiwane przez ten sam zespół deweloperski, który obsługuje resztę systemu projektu.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementacja IVsProjectUpgrade  
 Jeśli system projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementuje tylko, nie może uczestniczyć w **Kreatorze konwersji programu Visual Studio**. Jednak nawet jeśli zaimplementujesz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs, nadal <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> można delegować uaktualnienie pliku do implementacji.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade  
  
1. Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda jest wywoływana przez środowisko po otwarciu projektu i przed podjęciem jakiejkolwiek innej akcji użytkownika w projekcie. Jeśli użytkownik został już poproszony o uaktualnienie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> rozwiązania, flaga `grfUpgradeFlags` jest przekazywana w parametrze. Jeśli użytkownik otworzy projekt bezpośrednio, na przykład za pomocą polecenia <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> **Dodaj istniejący projekt,** flaga nie jest przekazywana, a projekt musi monitować użytkownika o uaktualnienie.  
  
2. W odpowiedzi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> na wywołanie projekt musi ocenić, czy plik projektu jest uaktualniany. Jeśli projekt nie trzeba uaktualnić typ projektu do nowej wersji, <xref:Microsoft.VisualStudio.VSConstants.S_OK> a następnie można po prostu zwrócić flagę.  
  
3. Jeśli projekt musi uaktualnić typ projektu do nowej wersji, należy określić, czy plik <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> projektu może być <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> modyfikowany `rgfQueryEdit` przez wywołanie metody i przekazywanie w wartości dla parametru. Następnie projekt musi wykonać następujące czynności:  
  
   - Jeśli `VSQueryEditResult` wartość zwrócona `pfEditCanceled` w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>parametrze jest , a następnie uaktualnienie można kontynuować, ponieważ plik projektu mogą być zapisywane.  
  
   - Jeśli `VSQueryEditResult` wartość zwrócona `pfEditCanceled` w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> parametrze jest i `VSQueryEditResult` wartość ma <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit ustawiony, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musi zwrócić błąd, ponieważ użytkownicy powinni rozwiązać problem uprawnień siebie. Projekt powinien następnie wykonać następujące czynności:  
  
        Zgłoś błąd użytkownikowi, wywołując program <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>. i zwraca <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> kod <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>błędu do .  
  
   - Jeśli `VSQueryEditResult` wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> jest, `VSQueryEditResultFlags` a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> wartość ma ustawioną wartość bitową, plik <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>projektu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>powinien zostać wyewidencjonowany przez wywołanie ( , ,...).  
  
4. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołanie pliku projektu powoduje, że plik ma zostać wyewidencjonowany, a najnowsza wersja ma zostać pobrana, projekt zostanie zwolniony i ponownie załadowany. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> jest wywoływana ponownie po utworzeniu innego wystąpienia projektu. W tym drugim wywołaniu plik projektu można zapisać na dysku; zaleca się zapisanie kopii pliku projektu w poprzednim formacie za pomocą pliku . STARE rozszerzenie, dokonać niezbędnych zmian uaktualnienia i zapisać plik projektu w nowym formacie. Ponownie, jeśli jakakolwiek część procesu uaktualniania nie powiedzie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>się, metoda musi wskazywać błąd przez zwrócenie . Powoduje to, że projekt ma zostać zwolniony w Eksploratorze rozwiązań.  
  
    Ważne jest, aby zrozumieć kompletny proces, który występuje w środowisku <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dla przypadku, w którym wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> metody <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> (określając wartość ReportOnly) zwraca i flagi.  
  
5. Użytkownik próbuje otworzyć plik projektu.  
  
6. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.  
  
7. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`zwraca , a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> następnie środowisko wywołuje implementacji.  
  
8. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementacji, aby otworzyć plik i zainicjować obiekt projektu, na przykład Project1.  
  
9. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` implementacji, aby ustalić, czy plik projektu musi zostać uaktualniony.  
  
10. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> wartości `rgfQueryEdit` dla parametru.  
  
11. Środowisko zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit jest `VSQueryEditResultFlags`ustawiony w .  
  
12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> `IVsQueryEditQuerySave::QueryEditFiles` wywołania<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>implementacji ( , ).  
  
    To wywołanie może spowodować nową kopię pliku projektu do wyewidencjonowania i najnowszej wersji pobrane, a także konieczność ponownego załadowania pliku projektu. W tym momencie dzieje się jedna z dwóch rzeczy:  
  
- Jeśli obsłużysz własny projekt przeładować, a następnie środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) implementacji. Po otrzymaniu tego wywołania, ponownie załadować pierwsze wystąpienie projektu (Project1) i kontynuować uaktualnianie pliku projektu. Środowisko wie, że obsługujesz przeładowanie `true` własnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>projektu, jeśli wrócisz do ( ).  
  
- Jeśli nie obsłużysz własnego projektu, `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> zwrócisz (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). W takim przypadku <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>przed ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) zwraca, środowisko tworzy kolejne nowe, wystąpienie projektu, na przykład Project2, w następujący sposób:  
  
  1. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> pierwszy obiekt projektu, Project1, umieszczając ten obiekt w stanie nieaktywnym.  
  
  2. Środowisko wywołuje `IVsProjectFactory::CreateProject` implementacji, aby utworzyć drugie wystąpienie projektu, Project2.  
  
  3. Środowisko wywołuje `IPersistFileFormat::Load` implementacji, aby otworzyć plik i zainicjować drugi obiekt projektu, Project2.  
  
  4. Środowisko wymaga `IVsProjectUpgrade::UpgradeProject` po raz drugi, aby ustalić, czy obiekt projektu należy uaktualnić. Jednak to wywołanie jest dokonywane na nowe, drugie wystąpienie projektu, Project2. Jest to projekt, który jest otwarty w rozwiązaniu.  
  
      > [!NOTE]
      > W przypadku, gdy pierwszy projekt, Project1, jest umieszczony w stanie <xref:Microsoft.VisualStudio.VSConstants.S_OK> nieaktywnym, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> a następnie należy powrócić z pierwszego wywołania do implementacji. Zobacz [Projekt podstawowy,](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) `IVsProjectUpgrade::UpgradeProject`aby zapoznać się z implementacją pliku .  
  
  5. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> wartości `rgfQueryEdit` dla parametru.  
  
  6. Środowisko zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i uaktualnienie można kontynuować, ponieważ plik projektu mogą być zapisywane.  
  
  Jeśli nie uda ci <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> `IVsProjectUpgrade::UpgradeProject`się uaktualnić, wróć z . Jeśli uaktualnienie nie jest konieczne lub zdecydujesz `IVsProjectUpgrade::UpgradeProject` się nie uaktualniać, potraktuj wywołanie jako nie-op. Jeśli zwrócisz, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>węzeł zastępczy zostanie dodany do rozwiązania dla projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator konwersji programu Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Uaktualnianie elementów projektu](../misc/upgrading-project-items.md)   
 [Projekty](../extensibility/internals/projects.md)