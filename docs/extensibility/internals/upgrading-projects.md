---
title: Uaktualnianie projektów | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a6a9e5b73315d8332c71e0fb7ddc3c6c1df041c3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344683"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów

Zmiany do modelu projektu z jednej wersji programu Visual Studio do następnego mogą wymagać, że projekty i rozwiązania uaktualnienia, aby umożliwić im uruchamianie w nowszej wersji. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Udostępnia interfejsy, które mogą służyć do implementowania obsługi uaktualnienia do własnych projektów.

## <a name="upgrade-strategies"></a>Strategie uaktualniania

Do obsługi uaktualnienia, implementacji systemu projektu muszą definiować ani implementować strategię uaktualnienia. Przy określaniu strategii, istnieje możliwość obsługi kopii zapasowych side-by-side (SxS) i/lub kopii zapasowej.

- Kopia zapasowa SxS oznacza to, czy projekt kopiuje tylko pliki wymagające uaktualnienia w miejscu, dodając sufiks nazwy odpowiedni plik, na przykład ".old".

- Kopii zapasowej oznacza to, czy projekt kopiuje wszystkie elementy projektu do podanego przez użytkownika lokalizacji kopii zapasowej. Następnie uaktualniane są odpowiednie pliki w oryginalnej lokalizacji projektu.

## <a name="how-upgrade-works"></a>Jak uaktualnić działa

Po otwarciu rozwiązania utworzone we wcześniejszej wersji programu Visual Studio w nowszej wersji, IDE sprawdza, czy plik rozwiązania, aby określić, jeśli musi zostać uaktualniony. Jeśli uaktualnianie jest wymagane, **Kreatora uaktualniania** jest uruchamiane automatycznie przeprowadzi użytkownika przez proces uaktualniania.

To rozwiązanie wymaga uaktualnienia, wysyła zapytanie każda fabryka projektu dla jego strategii uaktualniania. Strategii, która określa, czy fabryka projektu obsługuje kopii zapasowej lub kopii zapasowej SxS. Informacje są wysyłane do **Kreatora uaktualniania**, która zbiera informacje wymagane do tworzenia kopii zapasowej i wyświetlane odpowiednie opcje dla użytkownika.

### <a name="multi-project-solutions"></a>Rozwiązania dotyczące wielu projektów

Jeśli rozwiązanie zawiera wiele projektów i uaktualniania strategie są różne, np. gdy projekt C++, który obsługuje tylko SxS kopii zapasowej, a projekt sieci Web, które obsługują tylko kopii zapasowej, fabryk projektów muszą uzgodnić strategii uaktualniania.

Rozwiązanie zapytania każda fabryka projektu dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> Zobacz, czy pliki projektu globalnego wymagają, uaktualnianie i określenia obsługiwanych strategie uaktualnienia. **Kreatora uaktualniania** zostanie następnie wywołana.

Po użytkownik Dokańcza pracę z kreatorem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływana w każdej fabryki projektu do wykonania rzeczywistego uaktualnienia. W celu ułatwienia kopii zapasowej, zapewniają metody IVsProjectUpgradeViaFactory <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługę, aby rejestrować szczegóły procesu uaktualniania. Nie można buforować tej usługi.

Po zaktualizowaniu wszystkie odpowiednie pliki globalnego, każda fabryka projektu można utworzyć projektu. Implementacja projektu musi obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Wywoływana jest metoda następnie uaktualnić wszystkie elementy projektu.

> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> Metody nie dostarcza usługi SVsUpgradeLogger. Tę usługę można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Najlepsze praktyki

Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi Sprawdź, czy można edytować plik przed jego edycji i można go zapisać przed zapisaniem zmian. Ułatwi to kopia zapasowa i uaktualniania implementacje obsługują pliki projektu objętego kontrolą źródła, pliki o niewystarczających uprawnieniach i tak dalej.

Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługi podczas wszystkich etapów tworzenia kopii zapasowej i uaktualniania zawiera informacje na temat powodzenie lub niepowodzenie procesu uaktualniania.

Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualnianie projektów znajdują się komentarze IVsProjectUpgrade w vsshell2.idl.

## <a name="upgrading-custom-projects"></a> Uaktualnianie projektów niestandardowych

W przypadku zmiany dane utrwalone w pliku projektu, między różnymi wersjami programu Visual Studio produktu, a następnie potrzeba do obsługi, uaktualnianie pliku projektu ze starej do nowej wersji. Do obsługi, uaktualniania z można uczestniczyć w **Kreator konwersji Visual Studio**, implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu. Ten interfejs zawiera tylko mechanizm dostępne dla uaktualnienie kopii. W przypadku uaktualniania projektu odbywa się jako część rozwiązania zostanie otwarty. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Interfejs jest implementowany przez fabrykę projektu lub powinien wynosić co najmniej możliwe do uzyskania z fabryki projektu.

Stary mechanizm, który używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu nadal jest obsługiwany, ale pod względem koncepcyjnym uaktualnia system projektu jako część otwarty projekt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Interfejsu w związku z tym jest wywoływana przez program Visual Studio środowiska, nawet jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs o nazwie lub zaimplementowana. Takie podejście umożliwia <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> zaimplementować kopię tylko części uaktualnienia projektu i delegować pozostałej pracy do wykonania w miejscu (prawdopodobnie w nowej lokalizacji), <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu.

Na przykład implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, zobacz [przykłady VSSDK](https://aka.ms/vs2015sdksamples).

Następujące scenariusze wynikają z uaktualnienia projektu:

- Jeśli plik jest nowszy format, niż jest możliwe projektu, aplikacja musi zwracać komunikat o błędzie informujący, to. Przy założeniu, że starszą wersję produktu zawiera kod, aby sprawdzić wersję.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody uaktualnienia będzie można zaimplementować jako uaktualnienie w miejscu, przed otwarciem projektu.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody uaktualniania jest implementowany jako uaktualnienie kopii.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołać, a następnie monicie użytkownika przez środowisko do uaktualnienia pliku projektu jako uaktualnienie w miejscu, po otwarciu projektu. Na przykład środowisko monituje użytkownika o uaktualnienie, gdy użytkownik otworzy starszej wersji rozwiązania.

- Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga nie jest określony w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołać, a następnie musi monitować użytkownika o zaktualizować pliku projektu.

     Oto przykładowy komunikat monitu uaktualnienia:

     "Projekt"%1"został utworzony w starszej wersji programu Visual Studio. Jeśli otworzysz go za pomocą tej wersji programu Visual Studio, nie można go otworzyć ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory

1. Implementuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, w szczególności <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody w danej implementacji fabryka projektu lub implementacji można wywołać za pomocą implementacji fabryka projektu.

2. Jeśli chcesz wykonać uaktualnienie w miejscu w ramach rozwiązania, otwierając podać flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> jako `VSPUVF_FLAGS` parametru w swojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.

3. Jeśli chcesz wykonać uaktualnienie w miejscu w ramach rozwiązania, otwierając podać flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> jako `VSPUVF_FLAGS` parametru w swojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.

4. Oba kroki 2 i 3, rzeczywisty plik uaktualnienia kroków, za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, można zaimplementować zgodnie z opisem w temacie "Implementowanie `IVsProjectUpgade`" sekcji poniżej, lub możesz delegować uaktualnienia rzeczywistego pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Należy użyć metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> do uaktualnienia powiązane komunikaty dla użytkownika przy użyciu Kreatora migracji programu Visual Studio.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Interfejs jest używany do implementowania dowolny rodzaj uaktualnienia pliku, który musi zostać przeprowadzona w ramach uaktualnienia projektu. Ten interfejs nie jest wywoływana z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale jest dostarczany jako mechanizm do zaktualizowania plików, które są częścią system projektu, ale system projektu może nie być świadome bezpośrednio. Na przykład ta sytuacja może wystąpić, jeśli kompilator związane z plików i właściwości nie są obsługiwane przez ten sam zespół projektowy, obsługujący reszty systemu projektu.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade Implementation

Jeśli zaimplementowano systemu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> tylko nie mogą uczestniczyć w **Kreator konwersji Visual Studio**. Jednak nawet w przypadku zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, można nadal delegować uaktualnienia pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacji.

#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade

1. Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda jest wywoływana przez środowisko, po otwarciu i przed żadnego innego użytkownika w projekcie mogły zostać podjęte działania. Jeśli użytkownik ma już został monit o Uaktualnij rozwiązanie, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga jest przekazywany w `grfUpgradeFlags` parametru. Jeśli użytkownik otworzy projekt bezpośrednio, takie jako przy użyciu **Dodaj istniejący projekt** polecenia, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> flaga nie zostanie przekazany i projekt musi monitować użytkownika o uaktualnienie.

2. W odpowiedzi na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołanie, musi ocenić projekt, czy plik projektu jest uaktualniany. Jeśli projekt nie trzeba uaktualniać typu projektu do nowej wersji, a następnie można po prostu zwrócenia <xref:Microsoft.VisualStudio.VSConstants.S_OK> flagi.

3. Jeśli projekt należy uaktualnić tego typu projektu do nowej wersji, a następnie należy określić, czy plik projektu może być modyfikowana przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metody i przekazywać wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru. Projekt musi wykonać następujące czynności:

    - Jeśli `VSQueryEditResult` wartości zwracanej w `pfEditCanceled` parametr jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, a następnie można kontynuować uaktualniania, ponieważ mogą być zapisywane w pliku projektu.

    - Jeśli `VSQueryEditResult` wartości zwracanej w `pfEditCanceled` parametr jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> i `VSQueryEditResult` ma wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> bitu, następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musi zwrócić błąd, ponieważ użytkownicy powinna być rozpoznawana uprawnienia wystawić samodzielnie. Projekt następnie należy wykonać następujące czynności:

         Zgłoś błąd dla użytkownika, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> i zwracają <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> kod błędu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    - Jeśli `VSQueryEditResult` wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> i `VSQueryEditResultFlags` ma wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> bitu, a następnie w pliku projektu można wyewidencjonować przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołanie pliku projektu powoduje, że plik jest wyewidencjonowany i najnowszej wersji, które mają zostać pobrane, a następnie projekt nie zostanie zwolniony i ponownie załadowany. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Jest ponownie wywoływana metoda po utworzeniu inne wystąpienie projektu. W tym drugim wywołaniu, mogą być zapisywane w pliku projektu na dysku; zalecane jest, że projekt zapisać kopię pliku projektu w poprzednim formacie za pomocą. STARE rozszerzenia, zmiany jego niezbędne uaktualnienia i Zapisz plik projektu w nowym formacie. Ponownie, jeśli w dowolnej części proces uaktualniania zakończy się niepowodzeniem, metoda musi wskazywać, błąd, zwracając <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Powoduje to projekt, aby zostać zwolniony w Eksploratorze rozwiązań.

     Jest ważne zrozumieć pełny proces, który występuje w środowisku, w przypadku, w którym wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (Określanie wartości ReportOnly) metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> flag.

5. Użytkownik próbuje otworzyć plik projektu.

6. Wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.

7. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> zwraca `true`, a następnie wywołania środowiska usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.

8. Wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementacji Otwórz plik i inicjują obiekt projektu, na przykład projektu Project1.

9. Wywołania środowiska użytkownika `IVsProjectUpgrade::UpgradeProject` implementacji, aby ustalić, czy w pliku projektu musi zostać uaktualniony.

10. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> dla `rgfQueryEdit` parametru.

11. Zwraca środowiska <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> dla `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> jest ustawiony bit `VSQueryEditResultFlags`.

12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacja wywołuje `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

To wywołanie może spowodować, że nowa kopia pliku projektu do kasy i pobrać najnowszej wersji, a także konieczności ponownego ładowania pliku projektu. W tym momencie stanie jedna z następujących czynności:

- Jeśli możesz obsługiwać własne ponownie załadować projektu, następnie środowisko wywołuje swoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementacji (VSITEMID_ROOT). Po otrzymaniu tego wywołania Załaduj ponownie pierwsze wystąpienie projektu (projektu Project1), a następnie kontynuować uaktualnianie pliku projektu. Środowisko wie, obsługiwać własne ponownie załadować projektu, jeśli wrócisz `true` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

- Jeśli nie obsługiwać własne ponownie załadować projektu, a następnie wrócisz `false` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). W tym przypadku przed <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zwróci wartość, środowisko tworzy nowe wystąpienie innego projektu, na przykład Project2 w następujący sposób:

    1. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> na pierwszy obiekt projektu, projektu Project1, dlatego umieszczanie tego obiektu w stan nieaktywny.

    2. Wywołania środowiska użytkownika `IVsProjectFactory::CreateProject` implementacji, aby utworzyć drugie wystąpienie projektu o nazwie Project2.

    3. Wywołania środowiska użytkownika `IPersistFileFormat::Load` implementacji Otwórz plik i zainicjowania drugiego obiektu projektu o nazwie Project2.

    4. Wywołania środowiska `IVsProjectUpgrade::UpgradeProject` raz drugi w celu określenia, czy obiekt projektu powinny zostać uaktualnione. Jednak to wywołanie nowy, drugie wystąpienie projektu o nazwie Project2. Jest to projekt, który jest otwierany w rozwiązaniu.

        > [!NOTE]
        > W przypadku pierwszego projektu projektu Project1, jest umieszczany w stan nieaktywny, a następnie musi zwracać <xref:Microsoft.VisualStudio.VSConstants.S_OK> z pierwszego wywołania usługi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementacji.

    5. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> dla `rgfQueryEdit` parametru.

    6. Zwraca środowiska <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> i można kontynuować uaktualniania, ponieważ mogą być zapisywane w pliku projektu.

W przypadku awarii do uaktualnienia, zwracają <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> z `IVsProjectUpgrade::UpgradeProject`. Jeśli uaktualnienie nie jest konieczne, lub nie zdecydujesz się na uaktualnienie, należy traktować `IVsProjectUpgrade::UpgradeProject` wywołać jako pusta. Po powrocie <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, węzeł zastępczy jest dodawany do rozwiązania dla Twojego projektu.

## <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu

W przypadku dodania lub zarządzania elementami wewnątrz systemy projektu, który nie należy implementować, konieczne może uczestniczyć w procesie uaktualniania projektu. Crystal Reports znajduje się przykład elementu, który można dodać do systemu projektu.

Zazwyczaj chcesz wykorzystać już w pełni utworzona i uaktualnionego projektu, ponieważ muszą wiedzieć, jakie są odwołania do projektu i jakie inne właściwości projektu są podejmowanie decyzji uaktualnienia implementacji elementu projektu.

### <a name="to-get-the-project-upgrade-notification"></a>Aby uzyskać powiadomienia o uaktualnieniu projektu

1. Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> flagi (zdefiniowanymi w vsshell80.idl) w danej implementacji elementu projektu. Powoduje to element projektu pakietu VSPackage ładowane automatycznie, gdy powłoki programu Visual Studio Określa, czy system projektu trwa uaktualnianie.

2. Aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsu za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Interfejsu jest uruchamiany po implementacji systemu projektu został wykonany jego operacji uaktualnienia, a następnie jest tworzony nowy projekt uaktualniony. W zależności od scenariusza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsu jest wyzwalane po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metody.

### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić plików elementów projektów

1. Należy rozważnie zarządzać procesu tworzenia kopii zapasowej plików w danej implementacji elementu projektu. W szczególności dotyczy to usługi kopii zapasowej side-by-side, gdzie `fUpgradeFlag` parametru <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> ustawiono metodę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, gdzie pliki, które miały utworzone kopie zapasowe są umieszczane na stronie pliki, które są oznaczone jako ".old". Kopie zapasowe plików starszych niż czas systemowy, gdy został uaktualniony projekt może być wyznaczony jako nieaktualne. Ponadto one mogą zostać zastąpione, jeśli należy podjąć specjalne kroki, aby zapobiec takiej sytuacji.

2. W tym czasie element projektu pobiera powiadomienie z informacją o uaktualnieniu projektu **Kreator konwersji Visual Studio** jest nadal wyświetlany. Dlatego należy używać metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfejsu, aby zapewnić uaktualnienia wiadomości do Kreatora interfejsu użytkownika.

## <a name="see-also"></a>Zobacz także

- [Projekty](../../extensibility/internals/projects.md)