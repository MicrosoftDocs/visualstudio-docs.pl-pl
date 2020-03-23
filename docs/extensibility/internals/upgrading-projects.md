---
title: Modernizacja projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303233"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów

Zmiany w modelu projektu z jednej wersji programu Visual Studio do następnej może wymagać, aby projekty i rozwiązania zostały uaktualnione, tak aby można było uruchomić w nowszej wersji. Zapewnia [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfejsy, które mogą służyć do implementowania obsługi uaktualnień w własnych projektach.

## <a name="upgrade-strategies"></a>Strategie aktualizacji

Aby obsługiwać uaktualnienie, implementacja systemu projektu musi zdefiniować i wdrożyć strategię uaktualniania. Przy określaniu strategii można wybrać obsługę kopii zapasowej obok siebie (SxS), kopiowania kopii zapasowej lub obu tych obrażeń.

- Kopia zapasowa SxS oznacza, że projekt kopiuje tylko te pliki, które wymagają uaktualnienia w miejscu, dodając odpowiedni sufiks nazwy pliku, na przykład ".old".

- Kopiuj kopię zapasową oznacza, że projekt kopiuje wszystkie elementy projektu do lokalizacji kopii zapasowej dostarczonej przez użytkownika. Odpowiednie pliki w oryginalnej lokalizacji projektu są następnie uaktualniane.

## <a name="how-upgrade-works"></a>Jak działa uaktualnienie

Gdy rozwiązanie utworzone we wcześniejszej wersji programu Visual Studio jest otwierane w nowszej wersji, IDE sprawdza plik rozwiązania, aby ustalić, czy musi zostać uaktualniony. Jeśli wymagana jest aktualizacja, **Kreator uaktualniania** jest uruchamiany automatycznie, aby przejść użytkownika przez proces uaktualniania.

Gdy rozwiązanie wymaga uaktualnienia, wysyła zapytanie do każdej fabryki projektu o strategię uaktualniania. Strategia określa, czy fabryka projektu obsługuje kopię zapasową lub kopię zapasową SxS. Informacje są wysyłane do **Kreatora uaktualnień,** który zbiera informacje wymagane do wykonania kopii zapasowej i przedstawia użytkownikowi odpowiednie opcje.

### <a name="multi-project-solutions"></a>Rozwiązania wieloprojektowe

Jeśli rozwiązanie zawiera wiele projektów i strategie uaktualniania różnią się, na przykład gdy projekt C++, który obsługuje tylko kopię zapasową SxS i projekt sieci Web, który obsługuje tylko kopiowanie kopii zapasowej, fabryki projektu muszą negocjować strategię uaktualniania.

Rozwiązanie wysyła zapytanie do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>każdej fabryki projektu dla . Następnie wywołuje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> aby sprawdzić, czy globalne pliki projektu wymagają uaktualnienia i określić obsługiwane strategie uaktualniania. Następnie wywoływany jest **Kreator uaktualniania.**

Po zakończeniu pracy kreatora, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływana na każdej fabryce projektu do wykonania rzeczywistego uaktualnienia. Aby ułatwić tworzenie kopii zapasowej, metody IVsProjectUpgradeViaFactory zapewniają <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługę rejestrowania szczegółów procesu uaktualniania. Nie można buforować tej usługi.

Po zaktualizowaniu wszystkich odpowiednich plików globalnych każda fabryka projektu może zdecydować się na wystąpienie projektu. Realizacja projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>musi wspierać . Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> jest następnie wywoływana, aby uaktualnić wszystkie odpowiednie elementy projektu.

> [!NOTE]
> Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> nie zapewnia usługi SVsUpgradeLogger. Usługę tę można uzyskać <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>dzwoniąc.

## <a name="best-practices"></a>Najlepsze rozwiązania

Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi, aby sprawdzić, czy można edytować plik przed jego edycją, i możesz zapisać go przed zapisaniem. Pomoże to implementacji kopii zapasowej i uaktualnienia obsługi plików projektu pod kontrolą źródła, pliki z niewystarczającymi uprawnieniami i tak dalej.

Skorzystaj <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> z usługi podczas wszystkich faz tworzenia kopii zapasowych i uaktualniania, aby dostarczyć informacji o powodach lub niepowodzeniu procesu uaktualniania.

Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualniania projektów, zobacz komentarze do IVsProjectUpgrade w vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Uaktualnianie projektów niestandardowych

Jeśli zmienisz informacje utrwalone w pliku projektu między różnymi wersjami programu Visual Studio produktu, należy obsługiwać uaktualnianie pliku projektu ze starej do nowej wersji. Aby obsługiwać uaktualnianie, które umożliwia uczestnictwo w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> **Kreatorze konwersji programu Visual Studio,** zaimplementuj interfejs. Ten interfejs zawiera jedyny mechanizm dostępny do uaktualniania kopii. Modernizacja projektu odbywa się jako część rozwiązania otwiera. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> jest realizowany przez fabrykę projektu lub powinien być przynajmniej zyskiwany z fabryki projektu.

Stary mechanizm, który <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> używa interfejsu jest nadal obsługiwany, ale koncepcyjnie uaktualnia system projektu jako część projektu otwarte. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> jest zatem wywoływany przez środowisko Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Studio, nawet jeśli interfejs jest wywoływany lub implementowany. Takie podejście umożliwia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> zaimplementowanie kopiowania i projektu tylko części uaktualnienia i delegowania pozostałą część pracy, które <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> mają być wykonane w miejscu (ewentualnie w nowej lokalizacji) przez interfejs.

Aby uzyskać przykładową implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, zobacz [przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Następujące scenariusze powstają z uaktualnień projektu:

- Jeśli plik jest nowszym formatem niż projekt może obsługiwać, następnie musi zwrócić błąd stwierdzający to. Zakłada się, że starsza wersja produktu zawiera kod, aby sprawdzić wersję.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> flaga jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> określona w metodzie, uaktualnienie zostanie zaimplementowane jako uaktualnienie w miejscu przed otwarciem projektu.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> flaga jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> określona w metodzie, uaktualnienie jest implementowane jako uaktualnienie kopii.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> określona w wywołaniu, użytkownik został poproszony przez środowisko o uaktualnienie pliku projektu jako uaktualnienia w miejscu, po otwarciu projektu. Na przykład środowisko monituje użytkownika o uaktualnienie, gdy użytkownik otworzy starszą wersję rozwiązania.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga nie jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> określona w wywołaniu, należy monitować użytkownika o uaktualnienie pliku projektu.

     Poniżej znajduje się przykładowy komunikat monitu o uaktualnienie:

     "Projekt '%1' został utworzony przy starszej wersji programu Visual Studio. Jeśli otworzysz go za pomocą tej wersji programu Visual Studio, może nie być można otworzyć go ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory

1. Zaimplementuj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, w szczególności <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodę w implementacji fabryki projektu lub spraw, aby implementacje były wywoływane z implementacji fabryki projektu.

2. Jeśli chcesz wykonać uaktualnienie w miejscu jako część otwierania rozwiązania, `VSPUVF_FLAGS` podaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako parametr w implementacji.

3. Jeśli chcesz wykonać uaktualnienie w miejscu jako część otwierania rozwiązania, `VSPUVF_FLAGS` podaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako parametr w implementacji.

4. Dla obu kroków 2 i 3, rzeczywiste <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>kroki uaktualniania pliku, za pomocą `IVsProjectUpgade`, można zaimplementować zgodnie z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>opisem w sekcji "Implementowanie" poniżej, lub można delegować rzeczywiste uaktualnienie pliku do .

5. Użyj metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> publikowania wiadomości powiązanych z uaktualnieniem dla użytkownika za pomocą Kreatora migracji programu Visual Studio.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>interfejs jest używany do implementacji wszelkiego rodzaju aktualizacji plików, które muszą się zdarzyć w ramach aktualizacji projektu. Ten interfejs nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>jest wywoływany z programu , ale jest dostarczany jako mechanizm uaktualniania plików, które są częścią systemu projektu, ale główny system projektu może nie być bezpośrednio świadomy. Na przykład taka sytuacja może wystąpić, jeśli pliki i właściwości związane z kompilatorem nie są obsługiwane przez ten sam zespół deweloperski, który obsługuje resztę systemu projektu.

### <a name="ivsprojectupgrade-implementation"></a>Implementacja IVsProjectUpgrade

Jeśli system projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementuje tylko, nie może uczestniczyć w **Kreatorze konwersji programu Visual Studio**. Jednak nawet jeśli zaimplementujesz <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs, nadal <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> można delegować uaktualnienie pliku do implementacji.

#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade

1. Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda jest wywoływana przez środowisko po otwarciu projektu i przed podjęciem jakiejkolwiek innej akcji użytkownika w projekcie. Jeśli użytkownik został już poproszony o uaktualnienie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> rozwiązania, flaga `grfUpgradeFlags` jest przekazywana w parametrze. Jeśli użytkownik otworzy projekt bezpośrednio, na przykład za pomocą polecenia <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> **Dodaj istniejący projekt,** flaga nie jest przekazywana, a projekt musi monitować użytkownika o uaktualnienie.

2. W odpowiedzi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> na wywołanie projekt musi ocenić, czy plik projektu jest uaktualniany. Jeśli projekt nie trzeba uaktualnić typ projektu do nowej wersji, <xref:Microsoft.VisualStudio.VSConstants.S_OK> a następnie można po prostu zwrócić flagę.

3. Jeśli projekt musi uaktualnić typ projektu do nowej wersji, należy określić, czy plik <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> projektu może być <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> modyfikowany `rgfQueryEdit` przez wywołanie metody i przekazywanie w wartości dla parametru. Następnie projekt musi wykonać następujące czynności:

    - Jeśli `VSQueryEditResult` wartość zwrócona `pfEditCanceled` w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>parametrze jest , a następnie uaktualnienie można kontynuować, ponieważ plik projektu mogą być zapisywane.

    - Jeśli `VSQueryEditResult` wartość zwrócona `pfEditCanceled` w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> parametrze jest i `VSQueryEditResult` wartość ma <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bit ustawiony, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musi zwrócić błąd, ponieważ użytkownicy powinni rozwiązać problem uprawnień siebie. Projekt powinien następnie wykonać następujące czynności:

         Zgłoś błąd użytkownikowi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> wywołując <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>zwracając kod błędu do .

    - Jeśli `VSQueryEditResult` wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> jest, `VSQueryEditResultFlags` a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> wartość ma ustawioną wartość bitową, plik <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>projektu <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>powinien zostać wyewidencjonowany przez wywołanie ( , ,...).

4. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołanie pliku projektu powoduje, że plik ma zostać wyewidencjonowany, a najnowsza wersja ma zostać pobrana, projekt zostanie zwolniony i ponownie załadowany. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> jest wywoływana ponownie po utworzeniu innego wystąpienia projektu. W tym drugim wywołaniu plik projektu można zapisać na dysku; zaleca się zapisanie kopii pliku projektu w poprzednim formacie za pomocą pliku . STARE rozszerzenie, dokonać niezbędnych zmian uaktualnienia i zapisać plik projektu w nowym formacie. Ponownie, jeśli jakakolwiek część procesu uaktualniania nie powiedzie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>się, metoda musi wskazywać błąd przez zwrócenie . Powoduje to, że projekt ma zostać zwolniony w Eksploratorze rozwiązań.

     Ważne jest, aby zrozumieć kompletny proces, który występuje w środowisku <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> dla przypadku, w którym wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> metody <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> (określając wartość ReportOnly) zwraca i flagi.

5. Użytkownik próbuje otworzyć plik projektu.

6. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.

7. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`zwraca , a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> następnie środowisko wywołuje implementacji.

8. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementacji, aby otworzyć plik i zainicjować obiekt projektu, na przykład Project1.

9. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` implementacji, aby ustalić, czy plik projektu musi zostać uaktualniony.

10. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> wartości `rgfQueryEdit` dla parametru.

11. Środowisko zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit jest `VSQueryEditResultFlags`ustawiony w .

12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> `IVsQueryEditQuerySave::QueryEditFiles` wywołania<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>implementacji ( , ).

To wywołanie może spowodować nową kopię pliku projektu do wyewidencjonowania i najnowszej wersji pobrane, a także konieczność ponownego załadowania pliku projektu. W tym momencie dzieje się jedna z dwóch rzeczy:

- Jeśli obsłużysz własny projekt przeładować, a następnie środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) implementacji. Po otrzymaniu tego wywołania, ponownie załadować pierwsze wystąpienie projektu (Project1) i kontynuować uaktualnianie pliku projektu. Środowisko wie, że obsługujesz przeładowanie `true` własnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>projektu, jeśli wrócisz do ( ).

- Jeśli nie obsłużysz własnego projektu, `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> zwrócisz (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). W takim przypadku <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>przed (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zwraca, środowisko tworzy kolejne nowe wystąpienie projektu, na przykład Project2, w następujący sposób:

    1. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> pierwszy obiekt projektu, Project1, umieszczając ten obiekt w stanie nieaktywnym.

    2. Środowisko wywołuje `IVsProjectFactory::CreateProject` implementacji, aby utworzyć drugie wystąpienie projektu, Project2.

    3. Środowisko wywołuje `IPersistFileFormat::Load` implementacji, aby otworzyć plik i zainicjować drugi obiekt projektu, Project2.

    4. Środowisko wymaga `IVsProjectUpgrade::UpgradeProject` po raz drugi, aby ustalić, czy obiekt projektu należy uaktualnić. Jednak to wywołanie jest dokonywane na nowe, drugie wystąpienie projektu, Project2. Jest to projekt, który jest otwarty w rozwiązaniu.

        > [!NOTE]
        > W przypadku, gdy pierwszy projekt, Project1, jest umieszczony w stanie <xref:Microsoft.VisualStudio.VSConstants.S_OK> nieaktywnym, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> a następnie należy powrócić z pierwszego wywołania do implementacji.

    5. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać w <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> wartości `rgfQueryEdit` dla parametru.

    6. Środowisko zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> i uaktualnienie można kontynuować, ponieważ plik projektu mogą być zapisywane.

Jeśli nie uda ci <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> `IVsProjectUpgrade::UpgradeProject`się uaktualnić, wróć z . Jeśli uaktualnienie nie jest konieczne lub zdecydujesz `IVsProjectUpgrade::UpgradeProject` się nie uaktualniać, potraktuj wywołanie jako nie-op. Jeśli zwrócisz, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>węzeł zastępczy zostanie dodany do rozwiązania dla projektu.

## <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu

Jeśli dodasz lub zarządzasz elementami wewnątrz systemów projektu, które nie zostały zaimplementujne, może być konieczne uczestnictwo w procesie uaktualniania projektu. Crystal Reports jest przykładem elementu, który można dodać do systemu projektu.

Zazwyczaj realizatorzy elementów projektu chcą wykorzystać już w pełni skonkrzegnowany i uaktualniony projekt, ponieważ muszą wiedzieć, jakie są odwołania do projektu i jakie inne właściwości projektu są tam, aby podjąć decyzję o uaktualnieniu.

### <a name="to-get-the-project-upgrade-notification"></a>Aby uzyskać powiadomienie o uaktualnieniu projektu

1. Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flagę (zdefiniowaną w vsshell80.idl) w implementacji elementu projektu. Powoduje to, że element projektu VSPackage do automatycznego ładowania, gdy powłoka programu Visual Studio określa, że system projektu jest w trakcie uaktualniania.

2. Doradzić <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> za pomocą metody.

3. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> jest uruchamiany po zakończeniu wdrażania systemu projektu i utworzeniu nowego uaktualnionego projektu. W zależności od <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> scenariusza interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>uruchamiany <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> po , , lub metody.

### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić pliki elementów projektu

1. Należy starannie zarządzać procesem tworzenia kopii zapasowych plików w implementacji elementu projektu. Dotyczy to w szczególności kopii zapasowej side-by-side, gdzie `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody jest ustawiony na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, gdzie pliki, które zostały utworzone kopie zapasowe są umieszczane wraz z plikami, które są oznaczone jako ".old". Kopie zapasowe plików starszych niż czas systemowy, kiedy projekt został uaktualniony można określić jako przestarzałe. Ponadto mogą one zostać zastąpione, chyba że podejmiesz konkretne kroki, aby temu zapobiec.

2. W momencie, gdy element projektu otrzymuje powiadomienie o uaktualnieniu projektu, **Kreator konwersji programu Visual Studio** jest nadal wyświetlany. W związku z tym należy <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> użyć metod interfejsu, aby zapewnić komunikaty uaktualnienia do interfejsu użytkownika kreatora.

## <a name="see-also"></a>Zobacz też

- [Projekty](../../extensibility/internals/projects.md)
