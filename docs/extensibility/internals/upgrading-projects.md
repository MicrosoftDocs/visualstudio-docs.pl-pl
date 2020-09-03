---
title: Uaktualnianie projektów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a99207fc14cf9f462bc1abc88d6fed166ea6523f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704265"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów

Zmiany w modelu projektu z jednej wersji programu Visual Studio na następną mogą wymagać uaktualnienia projektów i rozwiązań, aby mogły być uruchamiane w nowszej wersji. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Udostępnia interfejsy, które mogą służyć do implementowania obsługi uaktualniania we własnych projektach.

## <a name="upgrade-strategies"></a>Strategie uaktualniania

W celu obsługi uaktualnienia wdrożenie systemu projektu musi definiować i implementować strategię uaktualniania. W celu określenia strategii możesz wybrać obsługę kopii zapasowych (SxS) obok siebie, kopii zapasowej lub obu tych funkcji.

- Kopia zapasowa SxS oznacza, że projekt kopiuje tylko te pliki, które wymagają uaktualnienia w miejscu, dodając odpowiedni sufiks nazwy pliku, na przykład ". old".

- Kopia zapasowa oznacza, że projekt kopiuje wszystkie elementy projektu do lokalizacji kopii zapasowej dostarczonej przez użytkownika. Odpowiednie pliki w oryginalnej lokalizacji projektu są następnie uaktualniane.

## <a name="how-upgrade-works"></a>Jak działa uaktualnienie

Jeśli rozwiązanie utworzone we wcześniejszej wersji programu Visual Studio zostanie otwarte w nowszej wersji, środowisko IDE sprawdzi plik rozwiązania, aby ustalić, czy należy go uaktualnić. Jeśli jest wymagane uaktualnienie, **Kreator uaktualniania** zostanie automatycznie uruchomiony, aby przeprowadzić użytkownika przez proces uaktualniania.

Gdy rozwiązanie wymaga uaktualnienia, wysyła zapytanie do każdej fabryki projektu w celu jej strategii uaktualniania. Strategia określa, czy fabryka projektów obsługuje kopie zapasowe i kopie zapasowe SxS. Informacje są wysyłane do **Kreatora uaktualniania**, który zbiera informacje wymagane do utworzenia kopii zapasowej i przedstawia odpowiednie opcje dla użytkownika.

### <a name="multi-project-solutions"></a>Rozwiązania obejmujące wiele projektów

Jeśli rozwiązanie zawiera wiele projektów, a strategie uaktualniania różnią się, na przykład gdy projekt C++ obsługuje tylko kopie zapasowe SxS i projekt sieci Web, który obsługuje tylko kopiowanie kopii zapasowych, fabryki projektu muszą negocjować strategię uaktualniania.

Rozwiązanie wysyła zapytanie do każdego fabryki projektu dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Następnie wywołuje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> Aby zobaczyć, czy globalne pliki projektu wymagają uaktualnienia i określić obsługiwane strategie uaktualniania. Następnie zostanie wywołany **Kreator uaktualniania** .

Gdy użytkownik ukończy kreatora, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływana w każdej fabryce projektu, aby przeprowadzić rzeczywiste uaktualnienie. Aby ułatwić tworzenie kopii zapasowych, metody IVsProjectUpgradeViaFactory umożliwiają <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usłudze rejestrowanie szczegółów procesu uaktualniania. Nie można buforować tej usługi.

Po zaktualizowaniu wszystkich odpowiednich plików globalnych każda fabryka projektu może wybrać utworzenie wystąpienia projektu. Implementacja projektu musi obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda jest następnie wywoływana w celu uaktualnienia wszystkich odpowiednich elementów projektu.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Metoda nie zapewnia usługi SVsUpgradeLogger. Tę usługę można uzyskać, wywołując metodę <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .

## <a name="best-practices"></a>Najlepsze rozwiązania

Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi, aby sprawdzić, czy możesz edytować plik przed jego edycją i zapisać go przed zapisaniem. Dzięki temu implementacje kopii zapasowych i uaktualnień będą obsługiwać pliki projektu pod kontrolą źródła, pliki z niewystarczającymi uprawnieniami i tak dalej.

Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługi podczas wszystkich faz tworzenia kopii zapasowych i uaktualniania, aby podać informacje o powodzeniu lub niepowodzeniu procesu uaktualniania.

Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualniania projektów, zobacz komentarze dotyczące IVsProjectUpgrade w vsshell2. idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a> Uaktualnianie projektów niestandardowych

Jeśli zmienisz informacje utrwalane w pliku projektu między różnymi wersjami programu Visual Studio, musisz obsługiwać uaktualnianie pliku projektu ze starego do nowej wersji. W celu obsługi uaktualniania, które umożliwia uczestnictwo w **Kreatorze konwersji programu Visual Studio**, zaimplementuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs. Ten interfejs zawiera jedyny mechanizm dostępny do uaktualnienia kopii. Uaktualnianie projektu odbywa się w ramach otwierania rozwiązania. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>Interfejs jest implementowany przez fabrykę projektu lub powinien być co najmniej uzyskany z fabryki projektu.

Stary mechanizm, który korzysta z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu, jest nadal obsługiwany, ale koncepcyjnie uaktualnia system projektu w ramach otwartego projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>Interfejs jest więc wywoływany przez środowisko programu Visual Studio, nawet jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs jest wywoływany lub zaimplementowany. Takie podejście umożliwia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> zaimplementowanie tylko części uaktualnienia i projektu oraz delegowanie reszty pracy do wykonania w miejscu (prawdopodobnie w nowej lokalizacji) przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejs.

Aby zapoznać się z przykładową implementacją programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , zobacz [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Podczas uaktualniania projektu powstają następujące scenariusze:

- Jeśli plik ma nowszy format niż może obsłużyć projekt, musi zwrócić błąd informujący o tym. Przyjęto założenie, że Starsza wersja produktu zawiera kod, aby sprawdzić wersję.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodzie, uaktualnienie zostanie zaimplementowane jako uaktualnienie w miejscu przed otwarciem projektu.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metodzie, uaktualnienie zostanie zaimplementowane jako uaktualnienie kopiowania.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołaniu, wówczas użytkownikowi zostanie wyświetlony monit o uaktualnienie środowiska, aby uaktualnić plik projektu jako uaktualnienie w miejscu, po otwarciu projektu. Na przykład w środowisku zostanie wyświetlony komunikat z prośbą o uaktualnienie użytkownika, gdy użytkownik otworzy starszą wersję rozwiązania.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga nie jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołaniu, należy monitować użytkownika o uaktualnienie pliku projektu.

     Poniżej znajduje się przykładowy komunikat monitu o uaktualnienie:

     "Projekt ' %1 ' został utworzony przy użyciu starszej wersji programu Visual Studio. Jeśli otworzysz go przy użyciu tej wersji programu Visual Studio, możesz nie być w stanie otworzyć go ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory

1. Zaimplementuj metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> w tym metodę w implementacji w fabryce projektu lub Przekształć implementacje z implementacji w fabryce projektu.

2. Jeśli chcesz przeprowadzić uaktualnienie w miejscu w ramach otwierania rozwiązania, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako `VSPUVF_FLAGS` parametr w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.

3. Jeśli chcesz przeprowadzić uaktualnienie w miejscu w ramach otwierania rozwiązania, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako `VSPUVF_FLAGS` parametr w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.

4. W przypadku obu kroków 2 i 3 rzeczywiste kroki uaktualniania plików, korzystając z programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> , można zaimplementować zgodnie z opisem w sekcji "implementacja `IVsProjectUpgade` " poniżej lub można delegować rzeczywiste uaktualnienie plików do programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

5. Użyj metod programu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> Aby opublikować komunikaty powiązane z uaktualnieniem dla użytkownika przy użyciu Kreatora migracji programu Visual Studio.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Interfejs służy do implementowania dowolnego rodzaju uaktualnienia plików, które muszą wystąpić w ramach uaktualnienia projektu. Ten interfejs nie jest wywoływany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , ale jest dostarczany jako mechanizm do uaktualnienia plików, które są częścią systemu projektu, ale główny system projektu może nie być bezpośrednio świadomy. Na przykład taka sytuacja może wystąpić, jeśli pliki i właściwości powiązane z kompilatorem nie są obsługiwane przez ten sam zespół programistyczny obsługujący resztę systemu projektu.

### <a name="ivsprojectupgrade-implementation"></a>Implementacja IVsProjectUpgrade

Jeśli system projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> tylko program, nie może uczestniczyć w **Kreatorze konwersji programu Visual Studio**. Jednak nawet w przypadku zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu można nadal delegować uaktualnienie pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacji.

#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade

1. Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda jest wywoływana przez środowisko po otwarciu projektu i przed wykonaniem jakiejkolwiek innej akcji użytkownika w projekcie. Jeśli użytkownik otrzymał już monit o uaktualnienie rozwiązania, <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> Flaga zostanie przeniesiona do `grfUpgradeFlags` parametru. Jeśli użytkownik otwiera projekt bezpośrednio, na przykład za pomocą polecenia **Dodaj istniejący projekt** , <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga nie zostanie przeniesiona, a projekt musi monitować użytkownika o uaktualnienie.

2. W odpowiedzi na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołanie, projekt musi oszacować, czy plik projektu jest uaktualniany. Jeśli projekt nie musi uaktualnić typu projektu do nowej wersji, może po prostu zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> flagę.

3. Jeśli projekt musi uaktualnić typ projektu do nowej wersji, należy określić, czy plik projektu może być modyfikowany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody i przekazanie wartości <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> `rgfQueryEdit` parametru. Projekt musi wykonać następujące czynności:

    - Jeśli `VSQueryEditResult` wartość zwrócona w `pfEditCanceled` parametrze to <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> , uaktualnienie można wykonać, ponieważ plik projektu może być zapisany.

    - Jeśli `VSQueryEditResult` wartość zwrócona w `pfEditCanceled` parametrze to, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> a `VSQueryEditResult` wartość ma <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> ustawiony bit, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> należy zwrócić błąd, ponieważ użytkownicy powinni rozwiązać problem z uprawnieniami. Projekt powinien następnie wykonać następujące czynności:

         Zgłoś błąd użytkownikowi przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> i zwrócenie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> kodu błędu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .

    - Jeśli `VSQueryEditResult` wartość jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> i `VSQueryEditResultFlags` ma <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> ustawiony bit, plik projektu powinien zostać wyewidencjonowany przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> ,...).

4. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołanie w pliku projektu powoduje wyewidencjonowanie pliku i Najnowsza wersja do pobrania, to projekt zostanie zwolniony i ponownie załadowany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Metoda jest wywoływana ponownie po utworzeniu innego wystąpienia projektu. Na tym drugim wywołaniu plik projektu może być zapisany na dysku; zaleca się, aby projekt zapisywał kopię pliku projektu w poprzednim formacie za pomocą. Stare rozszerzenie, wprowadź niezbędne zmiany uaktualnienia i Zapisz plik projektu w nowym formacie. Jeśli jakakolwiek część procesu uaktualniania nie powiedzie się, metoda musi wskazywać na błąd, zwracając wartość <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> . Powoduje to, że projekt zostanie zwolniony w Eksplorator rozwiązań.

     Ważne jest, aby zrozumieć cały proces występujący w środowisku, w przypadku którego wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody (określenie wartości ReportOnly) zwróci <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> flagi i.

5. Użytkownik próbuje otworzyć plik projektu.

6. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementację.

7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>W przypadku powracania `true` środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementację.

8. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementację, aby otworzyć plik i zainicjować obiekt projektu, na przykład Project1.

9. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` implementację, aby określić, czy plik projektu musi zostać uaktualniony.

10. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` parametru.

11. Środowisko zwraca wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bit jest ustawiony w `VSQueryEditResultFlags` .

12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> wywołania implementacji `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits> ).

To wywołanie może spowodować wyewidencjonowanie nowej kopii pliku projektu oraz pobranie najnowszej wersji, a także konieczność ponownego załadowania pliku projektu. W tym momencie występuje jedna z dwóch rzeczy:

- W przypadku obsługi własnego załadowania projektu, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementację (VSITEMID_ROOT). Po otrzymaniu tego wywołania ponownie załaduj pierwsze wystąpienie projektu (Project1) i Kontynuuj uaktualnianie pliku projektu. Środowisko wie, że w przypadku powrotu do programu () zostanie obsłużone własne ponowne załadowanie projektu `true` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> .

- Jeśli nie obsłużysz własnego ponownego ładowania projektu, Wróć `false` do <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload> ). W tym przypadku przed <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zwraca, środowisko tworzy inne nowe wystąpienie projektu, na przykład Project2, w następujący sposób:

    1. Środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> pierwszy obiekt projektu, Project1, w ten sposób umieszcza ten obiekt w stanie nieaktywnym.

    2. Środowisko wywołuje `IVsProjectFactory::CreateProject` implementację, aby utworzyć drugie wystąpienie projektu, Project2.

    3. Środowisko wywołuje `IPersistFileFormat::Load` implementację, aby otworzyć plik i zainicjować drugi obiekt projektu, Project2.

    4. Środowisko wywołuje `IVsProjectUpgrade::UpgradeProject` przez drugi czas, aby określić, czy obiekt projektu powinien zostać uaktualniony. To wywołanie jest jednak wykonywane na nowym, drugim wystąpieniu projektu, Project2. Jest to projekt otwarty w rozwiązaniu.

        > [!NOTE]
        > W przypadku, gdy pierwszy projekt, Project1, jest umieszczany w stanie nieaktywnym, wówczas należy zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> z pierwszego wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wdrożenia.

    5. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekazać wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> `rgfQueryEdit` parametru.

    6. Środowisko jest zwracane <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> , a uaktualnienie może być realizowane, ponieważ plik projektu może być zapisany.

Jeśli uaktualnienie nie powiedzie się, Wróć <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z `IVsProjectUpgrade::UpgradeProject` . Jeśli uaktualnienie nie jest wymagane lub nie chcesz go uaktualnić, Traktuj `IVsProjectUpgrade::UpgradeProject` wywołanie jako No-op. Jeśli powrócisz <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> , węzeł zastępczy zostanie dodany do rozwiązania dla projektu.

## <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu

W przypadku dodawania elementów i zarządzania nimi w systemach projektów, które nie zostały wdrożone, może być konieczne uczestnictwo w procesie uaktualniania projektu. Crystal Reports to przykład elementu, który można dodać do systemu projektu.

Zazwyczaj implementujący elementy projektu chcą korzystać z już w pełni skonkretyzowanych i uaktualnionych projektów, ponieważ chcą wiedzieć, jakie są odwołania do projektu i jakie inne właściwości projektu mają być podejmowane w celu podjęcia decyzji o uaktualnieniu.

### <a name="to-get-the-project-upgrade-notification"></a>Aby uzyskać powiadomienie o uaktualnieniu projektu

1. Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flagę (zdefiniowaną w vsshell80. idl) w implementacji elementu projektu. Powoduje to automatyczne ładowanie elementu projektu, gdy powłoka programu Visual Studio ustali, że system projektu jest w trakcie uaktualniania.

2. Doradzanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsem za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade>Interfejs jest uruchamiany po zakończeniu wykonywania operacji uaktualniania przez implementację systemu projektu i zostanie utworzony nowy uaktualniony projekt. W zależności od scenariusza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejs jest uruchamiany po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metodzie, lub.

### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić pliki elementów projektu

1. Należy dokładnie zarządzać procesem tworzenia kopii zapasowej plików w implementacji elementu projektu. Ma to zastosowanie w szczególności w przypadku kopii zapasowej równoległej, gdzie `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody jest ustawiony na <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> , gdzie pliki, których kopia zapasowa została utworzona, są umieszczane na plikach, które są oznaczone jako ". old". Kopie zapasowe plików starszej niż czas systemowy, po uaktualnieniu projektu, można wyznaczyć jako nieodświeżone. Ponadto mogą zostać nadpisywane, chyba że podejmujesz konkretne czynności, aby tego uniknąć.

2. Po otrzymaniu przez element projektu powiadomienia o uaktualnieniu projektu zostanie wyświetlony **Kreator konwersji programu Visual Studio** . W związku z tym należy używać metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfejsu do udostępniania komunikatów uaktualniania do interfejsu użytkownika kreatora.

## <a name="see-also"></a>Zobacz też

- [Projekty](../../extensibility/internals/projects.md)
