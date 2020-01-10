---
title: Uaktualnianie projektów | Microsoft Docs
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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848778"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów

Zmiany w modelu projektu z jednej wersji programu Visual Studio na następną mogą wymagać uaktualnienia projektów i rozwiązań, aby mogły być uruchamiane w nowszej wersji. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] udostępnia interfejsy, których można używać do implementowania obsługi uaktualniania we własnych projektach.

## <a name="upgrade-strategies"></a>Strategie uaktualniania

W celu obsługi uaktualnienia wdrożenie systemu projektu musi definiować i implementować strategię uaktualniania. W celu określenia strategii możesz wybrać obsługę kopii zapasowych (SxS) obok siebie, kopii zapasowej lub obu tych funkcji.

- Kopia zapasowa SxS oznacza, że projekt kopiuje tylko te pliki, które wymagają uaktualnienia w miejscu, dodając odpowiedni sufiks nazwy pliku, na przykład ". old".

- Kopia zapasowa oznacza, że projekt kopiuje wszystkie elementy projektu do lokalizacji kopii zapasowej dostarczonej przez użytkownika. Odpowiednie pliki w oryginalnej lokalizacji projektu są następnie uaktualniane.

## <a name="how-upgrade-works"></a>Jak działa uaktualnienie

Jeśli rozwiązanie utworzone we wcześniejszej wersji programu Visual Studio zostanie otwarte w nowszej wersji, środowisko IDE sprawdzi plik rozwiązania, aby ustalić, czy należy go uaktualnić. Jeśli jest wymagane uaktualnienie, **Kreator uaktualniania** zostanie automatycznie uruchomiony, aby przeprowadzić użytkownika przez proces uaktualniania.

Gdy rozwiązanie wymaga uaktualnienia, wysyła zapytanie do każdej fabryki projektu w celu jej strategii uaktualniania. Strategia określa, czy fabryka projektów obsługuje kopie zapasowe i kopie zapasowe SxS. Informacje są wysyłane do **Kreatora uaktualniania**, który zbiera informacje wymagane do utworzenia kopii zapasowej i przedstawia odpowiednie opcje dla użytkownika.

### <a name="multi-project-solutions"></a>Rozwiązania obejmujące wiele projektów

Jeśli rozwiązanie zawiera wiele projektów, a strategie uaktualniania różnią się, na przykład gdy C++ projekt obsługujący tylko kopie zapasowe SxS i projekt sieci Web obsługujący tylko kopie zapasowe, fabryki projektu muszą negocjować strategię uaktualniania.

Rozwiązanie wysyła zapytanie do każdej fabryki projektu dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A>, aby sprawdzić, czy globalne pliki projektu wymagają uaktualnienia i określić obsługiwane strategie uaktualniania. Następnie zostanie wywołany **Kreator uaktualniania** .

Po ukończeniu pracy kreatora przez użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływana w każdej fabryce projektu, aby przeprowadzić rzeczywiste uaktualnienie. Aby ułatwić tworzenie kopii zapasowych, metody IVsProjectUpgradeViaFactory zapewniają usługę <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger>, aby rejestrować szczegóły procesu uaktualniania. Nie można buforować tej usługi.

Po zaktualizowaniu wszystkich odpowiednich plików globalnych każda fabryka projektu może wybrać utworzenie wystąpienia projektu. Implementacja projektu musi obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> jest następnie wywoływana w celu uaktualnienia wszystkich odpowiednich elementów projektu.

> [!NOTE]
> Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> nie zapewnia usługi SVsUpgradeLogger. Tę usługę można uzyskać, wywołując <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Najlepsze praktyki

Użyj usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>, aby sprawdzić, czy można edytować plik przed jego edycją i zapisać go przed zapisaniem. Dzięki temu implementacje kopii zapasowych i uaktualnień będą obsługiwać pliki projektu pod kontrolą źródła, pliki z niewystarczającymi uprawnieniami i tak dalej.

Użyj usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> podczas wszystkich faz tworzenia kopii zapasowych i uaktualniania, aby podać informacje o powodzeniu lub niepowodzeniu procesu uaktualniania.

Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualniania projektów, zobacz komentarze dotyczące IVsProjectUpgrade w vsshell2. idl.

## <a name="upgrading-custom-projects"></a>Uaktualnianie projektów niestandardowych

Jeśli zmienisz informacje utrwalane w pliku projektu między różnymi wersjami programu Visual Studio, musisz obsługiwać uaktualnianie pliku projektu ze starego do nowej wersji. Aby umożliwić obsługę uaktualniania, który umożliwia uczestnictwo w **Kreatorze konwersji programu Visual Studio**, zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Ten interfejs zawiera jedyny mechanizm dostępny do uaktualnienia kopii. Uaktualnianie projektu odbywa się w ramach otwierania rozwiązania. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> jest implementowany przez fabrykę projektu lub powinien być co najmniej uzyskany z fabryki projektu.

Stary mechanizm, który używa interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> jest nadal obsługiwany, ale koncepcyjnie uaktualnia system projektu w ramach otwartego projektu. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> jest więc wywoływany przez środowisko programu Visual Studio, nawet jeśli interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> jest wywoływany lub zaimplementowany. Takie podejście umożliwia użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> do zaimplementowania tylko części uaktualnienia i projektu i delegowanie reszty pracy do wykonania w miejscu (prawdopodobnie w nowej lokalizacji) przez interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Aby zapoznać się z przykładową implementacją <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, zobacz [przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Podczas uaktualniania projektu powstają następujące scenariusze:

- Jeśli plik ma nowszy format niż może obsłużyć projekt, musi zwrócić błąd informujący o tym. Przyjęto założenie, że Starsza wersja produktu zawiera kod, aby sprawdzić wersję.

- Jeśli flaga <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jest określona w metodzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, uaktualnienie zostanie zaimplementowane jako uaktualnienie w miejscu przed otwarciem projektu.

- Jeśli flaga <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jest określona w metodzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, uaktualnienie zostanie zaimplementowane jako uaktualnienie kopiowania.

- Jeśli flaga <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> jest określona w wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, użytkownik zostanie poproszony przez środowisko, aby uaktualnić plik projektu jako uaktualnienie w miejscu, po otwarciu projektu. Na przykład w środowisku zostanie wyświetlony komunikat z prośbą o uaktualnienie użytkownika, gdy użytkownik otworzy starszą wersję rozwiązania.

- Jeśli flaga <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> nie została określona w wywołaniu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, należy monitować użytkownika o uaktualnienie pliku projektu.

     Poniżej znajduje się przykładowy komunikat monitu o uaktualnienie:

     "Projekt ' %1 ' został utworzony przy użyciu starszej wersji programu Visual Studio. Jeśli otworzysz go przy użyciu tej wersji programu Visual Studio, możesz nie być w stanie otworzyć go ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory

1. Zaimplementuj metodę interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, w tym metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> w implementacji fabryki projektu, lub wprowadź implementacje z implementacji w fabryce projektu.

2. Jeśli chcesz przeprowadzić uaktualnienie w miejscu w ramach otwierania rozwiązania, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako parametr `VSPUVF_FLAGS` w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Jeśli chcesz przeprowadzić uaktualnienie w miejscu w ramach otwierania rozwiązania, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako parametr `VSPUVF_FLAGS` w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. W przypadku obu etapów 2 i 3 rzeczywiste kroki uaktualniania plików, za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, można zaimplementować zgodnie z opisem w sekcji "Implementowanie `IVsProjectUpgade`" poniżej lub można delegować rzeczywiste uaktualnienie plików do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Korzystając z metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>, można publikować komunikaty powiązane z uaktualnieniem dla użytkownika przy użyciu Kreatora migracji programu Visual Studio.

6. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> służy do implementowania dowolnego rodzaju uaktualnienia plików, które muszą wystąpić w ramach uaktualnienia projektu. Ten interfejs nie jest wywoływany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale jest dostarczany jako mechanizm do uaktualnienia plików, które są częścią systemu projektu, ale główny system projektu może nie być bezpośrednio świadomy. Na przykład taka sytuacja może wystąpić, jeśli pliki i właściwości powiązane z kompilatorem nie są obsługiwane przez ten sam zespół programistyczny obsługujący resztę systemu projektu.

### <a name="ivsprojectupgrade-implementation"></a>Implementacja IVsProjectUpgrade

Jeśli system projektu implementuje tylko <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, nie może uczestniczyć w **Kreatorze konwersji programu Visual Studio**. Jednak nawet w przypadku zaimplementowania interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> nadal można delegować uaktualnienie pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacji.

#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade

1. Gdy użytkownik próbuje otworzyć projekt, Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> jest wywoływana przez środowisko po otwarciu projektu i przed wykonaniem jakiejkolwiek innej akcji użytkownika w projekcie. Jeśli użytkownik otrzymał już monit o uaktualnienie rozwiązania, flaga <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> jest przenoszona w parametrze `grfUpgradeFlags`. Jeśli użytkownik otwiera projekt bezpośrednio, na przykład za pomocą polecenia **Dodaj istniejący projekt** , flaga <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> nie zostanie przeniesiona, a projekt musi monitować użytkownika o uaktualnienie.

2. W odpowiedzi na wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, projekt musi oszacować, czy plik projektu został uaktualniony. Jeśli projekt nie musi uaktualnić typu projektu do nowej wersji, może po prostu zwrócić flagę <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Jeśli projekt musi uaktualnić typ projektu do nowej wersji, należy określić, czy plik projektu może być modyfikowany przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazanie wartości <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> parametru `rgfQueryEdit`. Projekt musi wykonać następujące czynności:

    - Jeśli wartość `VSQueryEditResult` zwrócona w parametrze `pfEditCanceled` jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, uaktualnienie można wykonać, ponieważ plik projektu może być zapisany.

    - Jeśli wartość `VSQueryEditResult` zwrócona w parametrze `pfEditCanceled` jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>, a `VSQueryEditResult` wartość ma ustawiony bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>, wówczas <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musi zwrócić błąd, ponieważ użytkownicy powinni rozwiązać sam problem z uprawnieniami. Projekt powinien następnie wykonać następujące czynności:

         Zgłoś błąd użytkownikowi przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> i zwrócenie kodu błędu <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    - Jeśli wartość `VSQueryEditResult` jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> i `VSQueryEditResultFlags` wartość ma ustawiony bit <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>, plik projektu powinien zostać wyewidencjonowany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4. Jeśli wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> w pliku projektu powoduje wyewidencjonowanie pliku, a Najnowsza wersja do pobrania, projekt zostanie zwolniony i ponownie załadowany. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> jest wywoływana ponownie po utworzeniu innego wystąpienia projektu. Na tym drugim wywołaniu plik projektu może być zapisany na dysku; zaleca się, aby projekt zapisywał kopię pliku projektu w poprzednim formacie za pomocą. Stare rozszerzenie, wprowadź niezbędne zmiany uaktualnienia i Zapisz plik projektu w nowym formacie. Jeśli jakakolwiek część procesu uaktualniania nie powiedzie się, metoda musi wskazywać na błąd, zwracając <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Powoduje to, że projekt zostanie zwolniony w Eksplorator rozwiązań.

     Ważne jest, aby zrozumieć cały proces występujący w środowisku, w przypadku którego wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (określenie wartości ReportOnly) zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> i flagi <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. Użytkownik próbuje otworzyć plik projektu.

6. Środowisko wywołuje implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> zwraca `true`, środowisko wywoła implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. Środowisko wywołuje implementację <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A>, aby otworzyć plik i zainicjować obiekt projektu, na przykład Project1.

9. Środowisko wywołuje implementację `IVsProjectUpgrade::UpgradeProject`, aby określić, czy plik projektu musi zostać uaktualniony.

10. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> parametru `rgfQueryEdit`.

11. Środowisko zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> dla `VSQueryEditResult`, a <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit jest ustawiony w `VSQueryEditResultFlags`.

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> wywołań implementacji `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

To wywołanie może spowodować wyewidencjonowanie nowej kopii pliku projektu oraz pobranie najnowszej wersji, a także konieczność ponownego załadowania pliku projektu. W tym momencie występuje jedna z dwóch rzeczy:

- W przypadku obsługi własnego załadowania projektu, środowisko wywołuje implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Po otrzymaniu tego wywołania ponownie załaduj pierwsze wystąpienie projektu (Project1) i Kontynuuj uaktualnianie pliku projektu. Środowisko wie, że w przypadku powrotu do `true` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>) jest obsługiwane ponowne załadowanie projektu.

- Jeśli nie obsłużysz własnego ponownego ładowania projektu, zwróć `false` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). W tym przypadku przed <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zwraca, środowisko tworzy kolejne nowe wystąpienie projektu, na przykład Project2, w następujący sposób:

    1. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> w pierwszym obiekcie projektu, Project1, w ten sposób umieszcza ten obiekt w stanie nieaktywnym.

    2. Środowisko wywołuje implementację `IVsProjectFactory::CreateProject`, aby utworzyć drugie wystąpienie projektu, Project2.

    3. Środowisko wywołuje implementację `IPersistFileFormat::Load`, aby otworzyć plik i zainicjować drugi obiekt projektu, Project2.

    4. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` przez drugi raz, aby określić, czy obiekt projektu powinien zostać uaktualniony. To wywołanie jest jednak wykonywane na nowym, drugim wystąpieniu projektu, Project2. Jest to projekt otwarty w rozwiązaniu.

        > [!NOTE]
        > W przypadku, gdy pierwszy projekt, Project1, jest umieszczany w stanie nieaktywnym, należy zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> od pierwszego wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementacji.

    5. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> parametru `rgfQueryEdit`.

    6. Środowisko zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> i można przeprowadzić uaktualnienie, ponieważ plik projektu może być zapisany.

Jeśli uaktualnienie nie powiedzie się, zwróć <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z `IVsProjectUpgrade::UpgradeProject`. Jeśli uaktualnienie nie jest wymagane lub nie chcesz go uaktualnić, Traktuj `IVsProjectUpgrade::UpgradeProject` wywołanie jako No-op. W przypadku powrotu <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>węzeł zastępczy zostanie dodany do rozwiązania dla projektu.

## <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu

W przypadku dodawania elementów i zarządzania nimi w systemach projektów, które nie zostały wdrożone, może być konieczne uczestnictwo w procesie uaktualniania projektu. Crystal Reports to przykład elementu, który można dodać do systemu projektu.

Zazwyczaj implementujący elementy projektu chcą korzystać z już w pełni skonkretyzowanych i uaktualnionych projektów, ponieważ chcą wiedzieć, jakie są odwołania do projektu i jakie inne właściwości projektu mają być podejmowane w celu podjęcia decyzji o uaktualnieniu.

### <a name="to-get-the-project-upgrade-notification"></a>Aby uzyskać powiadomienie o uaktualnieniu projektu

1. Ustaw flagę <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> (zdefiniowaną w vsshell80. idl) w implementacji elementu projektu. Powoduje to automatyczne ładowanie elementu projektu, gdy powłoka programu Visual Studio ustali, że system projektu jest w trakcie uaktualniania.

2. Należy polecić interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> za pomocą metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>.

3. Interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> jest uruchamiany po zakończeniu przez implementację systemu projektu operacji uaktualniania i utworzeniu nowego uaktualnionego projektu. W zależności od scenariusza interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> jest uruchamiany po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodach.

### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić pliki elementów projektu

1. Należy dokładnie zarządzać procesem tworzenia kopii zapasowej plików w implementacji elementu projektu. Ma to zastosowanie w szczególności w przypadku kopii zapasowej równoległej, gdzie parametr `fUpgradeFlag` metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest ustawiony na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, gdzie pliki, których kopia zapasowa została utworzona, są umieszczane na plikach, które zostały wystawione jako ". old". Kopie zapasowe plików starszej niż czas systemowy, po uaktualnieniu projektu, można wyznaczyć jako nieodświeżone. Ponadto mogą zostać nadpisywane, chyba że podejmujesz konkretne czynności, aby tego uniknąć.

2. Po otrzymaniu przez element projektu powiadomienia o uaktualnieniu projektu zostanie wyświetlony **Kreator konwersji programu Visual Studio** . W związku z tym należy używać metod interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> do udostępniania komunikatów uaktualniania do interfejsu użytkownika kreatora.

## <a name="see-also"></a>Zobacz także

- [Projekty](../../extensibility/internals/projects.md)
