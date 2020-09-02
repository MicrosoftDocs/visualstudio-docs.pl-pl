---
title: Uaktualnianie projektów niestandardowych | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037210"
---
# <a name="upgrading-custom-projects"></a>Uaktualnianie projektów niestandardowych
Jeśli zmienisz informacje utrwalane w pliku projektu między różnymi wersjami programu Visual Studio, musisz obsługiwać uaktualnianie pliku projektu ze starego do nowej wersji. W celu obsługi uaktualniania, które umożliwia uczestnictwo w **Kreatorze konwersji programu Visual Studio**, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs. Ten interfejs zawiera jedyny mechanizm dostępny do uaktualnienia kopii. Uaktualnianie projektu odbywa się w ramach otwierania rozwiązania. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Interfejs jest implementowany przez fabrykę projektu lub powinien być co najmniej uzyskany z fabryki projektu.  
  
 Stary mechanizm, który korzysta z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu, jest nadal obsługiwany, ale koncepcyjnie uaktualnia system projektu w ramach otwartego projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Interfejs jest w związku z tym wywoływany przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisko, nawet jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs jest wywoływany lub zaimplementowany. Takie podejście umożliwia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> zaimplementowanie tylko części uaktualnienia i projektu oraz delegowanie reszty pracy do wykonania w miejscu (prawdopodobnie w nowej lokalizacji) przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejs.  
  
 Aby zapoznać się z przykładową implementacją programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , zobacz [VSSDK Samples](../misc/vssdk-samples.md).  
  
 Podczas uaktualniania projektu powstają następujące scenariusze:  
  
- Jeśli plik ma nowszy format niż może obsłużyć projekt, musi zwrócić błąd informujący o tym. Przyjęto założenie, że Starsza wersja produktu — na przykład Visual Studio .NET 2003 — zawiera kod służący do sprawdzania wersji.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodzie, uaktualnienie zostanie zaimplementowane jako uaktualnienie w miejscu przed otwarciem projektu.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodzie, uaktualnienie zostanie zaimplementowane jako uaktualnienie kopiowania.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołaniu, wówczas użytkownikowi zostanie wyświetlony monit o uaktualnienie środowiska, aby uaktualnić plik projektu jako uaktualnienie w miejscu, po otwarciu projektu. Na przykład w środowisku zostanie wyświetlony komunikat z prośbą o uaktualnienie użytkownika, gdy użytkownik otworzy starszą wersję rozwiązania.  
  
- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołaniu, należy monitować użytkownika o uaktualnienie pliku projektu.  
  
     Poniżej znajduje się przykładowy komunikat monitu o uaktualnienie:  
  
     "Projekt ' %1 ' został utworzony przy użyciu starszej wersji programu Visual Studio. Jeśli otworzysz go przy użyciu tej wersji programu Visual Studio, możesz nie być w stanie otworzyć go ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt? "  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory  
  
1. Zaimplementuj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> w tym metodę w implementacji w fabryce projektu lub Przekształć implementacje z implementacji w fabryce projektu.  
  
2. Jeśli chcesz przeprowadzić uaktualnienie w miejscu w ramach otwierania rozwiązania, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametr w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.  
  
3. Jeśli chcesz przeprowadzić uaktualnienie w miejscu w ramach otwierania rozwiązania, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametr w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.  
  
4. W przypadku obu kroków 2 i 3 rzeczywiste kroki uaktualniania plików, korzystając z programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> , można zaimplementować zgodnie z opisem w sekcji "implementacja `IVsProjectUpgade` " poniżej lub można delegować rzeczywiste uaktualnienie plików do programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
5. Użyj metod programu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Aby opublikować komunikaty powiązane z uaktualnieniem dla użytkownika przy użyciu Kreatora migracji programu Visual Studio.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Interfejs służy do implementowania dowolnego rodzaju uaktualnienia plików, które muszą wystąpić w ramach uaktualnienia projektu. Ten interfejs nie jest wywoływany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , ale jest dostarczany jako mechanizm do uaktualnienia plików, które są częścią systemu projektu, ale główny system projektu może nie być bezpośrednio świadomy. Na przykład taka sytuacja może wystąpić, jeśli pliki i właściwości powiązane z kompilatorem nie są obsługiwane przez ten sam zespół programistyczny obsługujący resztę systemu projektu.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementacja IVsProjectUpgrade  
 Jeśli system projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> tylko program, nie może uczestniczyć w **Kreatorze konwersji programu Visual Studio**. Jednak nawet w przypadku zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu można nadal delegować uaktualnienie pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacji.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade  
  
1. Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda jest wywoływana przez środowisko po otwarciu projektu i przed wykonaniem jakiejkolwiek innej akcji użytkownika w projekcie. Jeśli użytkownik otrzymał już monit o uaktualnienie rozwiązania, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> Flaga zostanie przeniesiona do `grfUpgradeFlags` parametru. Jeśli użytkownik otwiera projekt bezpośrednio, na przykład za pomocą polecenia **Dodaj istniejący projekt** , <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie zostanie przeniesiona, a projekt musi monitować użytkownika o uaktualnienie.  
  
2. W odpowiedzi na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołanie, projekt musi oszacować, czy plik projektu jest uaktualniany. Jeśli projekt nie musi uaktualnić typu projektu do nowej wersji, może po prostu zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> flagę.  
  
3. Jeśli projekt musi uaktualnić typ projektu do nowej wersji, należy określić, czy plik projektu może być modyfikowany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody i przekazanie wartości <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru. Projekt musi wykonać następujące czynności:  
  
   - Jeśli `VSQueryEditResult` wartość zwrócona w `pfEditCanceled` parametrze to <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> , uaktualnienie można wykonać, ponieważ plik projektu może być zapisany.  
  
   - Jeśli `VSQueryEditResult` wartość zwrócona w `pfEditCanceled` parametrze to, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> a `VSQueryEditResult` wartość ma <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> ustawiony bit, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> należy zwrócić błąd, ponieważ użytkownicy powinni rozwiązać problem z uprawnieniami. Projekt powinien następnie wykonać następujące czynności:  
  
        Zgłoś błąd użytkownikowi przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> . i zwróć <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> Kod błędu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
   - Jeśli `VSQueryEditResult` wartość jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i `VSQueryEditResultFlags` ma <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> ustawiony bit, plik projektu powinien zostać wyewidencjonowany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ,...).  
  
4. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołanie w pliku projektu powoduje wyewidencjonowanie pliku i Najnowsza wersja do pobrania, to projekt zostanie zwolniony i ponownie załadowany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda jest wywoływana ponownie po utworzeniu innego wystąpienia projektu. Na tym drugim wywołaniu plik projektu może być zapisany na dysku; zaleca się, aby projekt zapisywał kopię pliku projektu w poprzednim formacie za pomocą. Stare rozszerzenie, wprowadź niezbędne zmiany uaktualnienia i Zapisz plik projektu w nowym formacie. Jeśli jakakolwiek część procesu uaktualniania nie powiedzie się, metoda musi wskazywać na błąd, zwracając wartość <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> . Powoduje to, że projekt zostanie zwolniony w Eksplorator rozwiązań.  
  
    Ważne jest, aby zrozumieć cały proces występujący w środowisku, w przypadku którego wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody (określenie wartości ReportOnly) zwróci <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> flagi i.  
  
5. Użytkownik próbuje otworzyć plik projektu.  
  
6. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementację.  
  
7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>W przypadku powracania `true` środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementację.  
  
8. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementację, aby otworzyć plik i zainicjować obiekt projektu, na przykład Project1.  
  
9. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` implementację, aby określić, czy plik projektu musi zostać uaktualniony.  
  
10. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru.  
  
11. Środowisko zwraca wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit jest ustawiony w `VSQueryEditResultFlags` .  
  
12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> wywołania implementacji `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ).  
  
    To wywołanie może spowodować wyewidencjonowanie nowej kopii pliku projektu oraz pobranie najnowszej wersji, a także konieczność ponownego załadowania pliku projektu. W tym momencie występuje jedna z dwóch rzeczy:  
  
- W przypadku obsługi własnego załadowania projektu, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementację (VSITEMID_ROOT). Po otrzymaniu tego wywołania ponownie załaduj pierwsze wystąpienie projektu (Project1) i Kontynuuj uaktualnianie pliku projektu. Środowisko wie, że w przypadku powrotu do programu () zostanie obsłużone własne ponowne załadowanie projektu `true` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
- Jeśli nie obsłużysz własnego ponownego ładowania projektu, Wróć `false` do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ). W tym przypadku przed <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) zwraca, środowisko tworzy kolejne nowe wystąpienie projektu, na przykład Project2, w następujący sposób:  
  
  1. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> pierwszy obiekt projektu, Project1, w ten sposób umieszcza ten obiekt w stanie nieaktywnym.  
  
  2. Środowisko wywołuje `IVsProjectFactory::CreateProject` implementację, aby utworzyć drugie wystąpienie projektu, Project2.  
  
  3. Środowisko wywołuje `IPersistFileFormat::Load` implementację, aby otworzyć plik i zainicjować drugi obiekt projektu, Project2.  
  
  4. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` przez drugi czas, aby określić, czy obiekt projektu powinien zostać uaktualniony. To wywołanie jest jednak wykonywane na nowym, drugim wystąpieniu projektu, Project2. Jest to projekt otwarty w rozwiązaniu.  
  
      > [!NOTE]
      > W przypadku, gdy pierwszy projekt, Project1, jest umieszczany w stanie nieaktywnym, wówczas należy zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> z pierwszego wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wdrożenia. Aby zapoznać się z implementacją programu, zobacz temat [Basic Project](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) `IVsProjectUpgrade::UpgradeProject` .  
  
  5. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru.  
  
  6. Środowisko jest zwracane <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> , a uaktualnienie może być realizowane, ponieważ plik projektu może być zapisany.  
  
  Jeśli uaktualnienie nie powiedzie się, Wróć <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> z `IVsProjectUpgrade::UpgradeProject` . Jeśli uaktualnienie nie jest wymagane lub nie chcesz go uaktualnić, Traktuj `IVsProjectUpgrade::UpgradeProject` wywołanie jako No-op. Jeśli powrócisz <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> , węzeł zastępczy zostanie dodany do rozwiązania dla projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator konwersji programu Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Uaktualnianie elementów projektu](../misc/upgrading-project-items.md)   
 [Projekty](../extensibility/internals/projects.md)