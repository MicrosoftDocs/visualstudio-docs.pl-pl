---
title: Rozwiązywanie problemów z rozwiązaniami programu SharePoint | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fcb30056021a865d0b0e605de462ff72ced5a383
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "73661886"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Rozwiązywanie problemów z rozwiązaniami programu SharePoint
  Podczas debugowania rozwiązań programu SharePoint za pomocą debugera mogą wystąpić następujące problemy lub alerty [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Debugowanie rozwiązań przepływu pracy programu SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Ograniczenia tokenu w wizualnych częściach sieci Web w trybie piaskownicy
 Wizualne składniki Web Part w rozwiązaniach w trybie piaskownicy nie mogą przetwarzać tokenów standardowych, takich jak $SPUrl, obsługiwane przez środowisko uruchomieniowe programu SharePoint. W związku z tym adres URL nie jest rozpoznawany i nie można wyświetlić podglądu zawartości widok Projekt w programie Visual Web Part Designer, jeśli odwołujesz się do niego bezpośrednio w elemencie skryptu, na przykład w poniższym przykładzie:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Aby obejść to ograniczenie i rozwiązać token, należy odwołać się do niego przy użyciu literałów:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Ograniczenia znaków w nazwach projektów i elementów projektu
 Nazwy projektów i elementów projektu mogą zawierać tylko znaki, które są prawidłowe w ścieżce wdrożenia w programie SharePoint 2010. Żadne inne znaki nie są dozwolone.

### <a name="error-message"></a>Komunikat o błędzie
 Komunikat o błędzie "nieprawidłowe znaki".

### <a name="resolution"></a>Rozwiązanie
 W przypadku nazw projektów programu SharePoint i elementów projektu należy używać tylko następujących znaków:

- Alfanumeryczne znaki ASCII

- Miejsce

- Kropka (.)

- Przecinek (,)

- Podkreślenie (_)

- Kreska (-)

- Ukośnik odwrotny ( \\ )

  Gdy projekt jest spakowany, reguła walidacji sprawdza, czy właściwość ścieżka wdrożenia dla każdego wdrażanego pliku zawiera tylko te prawidłowe znaki.

## <a name="errors-when-creating-custom-fields"></a>Błędy podczas tworzenia pól niestandardowych
 W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pola niestandardowe są zdefiniowane w kodzie XML. Błędy mogą wystąpić, jeśli pole nie jest zdefiniowane lub nie można się do niego odwoływać przy użyciu określonego formatu.

### <a name="error-message"></a>Komunikat o błędzie
 Komunikat o błędzie "nieprawidłowe znaki" w czasie pakowania.

### <a name="resolution"></a>Rozwiązanie
 Identyfikator dla definicji pola musi być identyfikatorem GUID ujętym w nawiasy klamrowe, jak pokazano w poniższym przykładzie:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Jak pokazano na poniższym przykładzie, odwołanie do pola w typie zawartości musi być zdefiniowane przy użyciu formatu pustego elementu ( \<FieldRef /> ), a nie za pomocą elementów początkowych/końcowych ( \<FieldRef> \</FieldRef> ):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Jeśli źródłowy kod XML dla pola jest źle sformułowany, nie jest prawidłowym plikiem XML lub wykazuje inny problem, wystąpił błąd "nie można przeanalizować pliku".

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nowe definicje lokacji inne niż angielskie nie są wyświetlane na stronie tworzenia witryny po wdrożeniu
 Po utworzeniu i wdrożeniu definicji lokacji przy użyciu wersji językowej innej niż angielska [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (czyli wersji z ustawieniami regionalnymi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] inną niż 1033) karta **dostosowania programu SharePoint** nie jest wyświetlana w polu **Wybór szablonu** , a nowy szablon witryny nie jest wyświetlany na **nowej stronie witryny programu SharePoint** .

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Ten problem występuje z powodu nieprawidłowej wartości we właściwości **Path** pliku konfiguracji definicji witryny webtemp, takiej jak *webtemp_SiteDefinitionProject1.xml*. We właściwości **Path** pliku WEBTEMP, który znajduje się w **lokalizacji wdrożenia**, Zmień 1033 na odpowiednie ustawienia regionalne [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Na przykład, aby użyć japońskiego ustawienia regionalnego, Zmień wartość na 1041. Aby uzyskać więcej informacji, zobacz [identyfikatory ustawień regionalnych przypisanych przez firmę Microsoft](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Błąd pojawia się, gdy projekt przepływu pracy jest wdrażany w czystym systemie
 Ten problem występuje w przypadku wdrożenia projektu przepływu pracy w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] w systemie. Czysty system to komputer, który ma nową instalację programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu SharePoint, ale nie wdrożone projekty przepływu pracy.

### <a name="error-message"></a>Komunikat o błędzie
 Nie można znaleźć listy programu SharePoint: Historia przepływu pracy.

### <a name="resolution"></a>Rozwiązanie
 Ten błąd występuje z powodu braku listy historii przepływu pracy. Ponieważ środowisko programistyczne jest czystym systemem, nie są wdrażane żadne przepływy pracy, a lista historii przepływu pracy jeszcze nie istnieje. Aby rozwiązać ten problem, Otwórz ponownie Kreatora przepływu pracy, co spowoduje utworzenie listy historii przepływu pracy.

##### <a name="to-reenter-the-workflow-wizard"></a>Aby ponownie wprowadzić kreatora przepływu pracy

1. W **Eksplorator rozwiązań**wybierz węzeł przepływ pracy.

2. W oknie **Właściwości** wybierz przycisk wielokropka (...) we właściwości, która ma przycisk wielokropka.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Użytkownik musi odświeżyć stronę aplikacji w przeglądarce podczas debugowania w celu wyświetlenia zaktualizowanego obrazu
 Jeśli debugujesz rozwiązanie SharePoint zawierające stronę aplikacji z kontrolką wyświetlającą obraz, taki jak [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] kontrolka obrazu, należy odświeżyć stronę w przeglądarce, aby wyświetlić wszystkie zmiany wprowadzone do obrazu.

## <a name="error-the-site-location-is-not-valid"></a>Błąd: lokalizacja witryny jest nieprawidłowa
 Ten problem może wystąpić, jeśli [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] nie jest zainstalowany. Może się to zdarzyć również wtedy, gdy użytkownik nie ma dostępu administratora do witryny sieci Web programu SharePoint, która jest określona w **Kreatorze dostosowywania programu SharePoint**.

### <a name="error-message"></a>Komunikat o błędzie

- Lokalizacja witryny programu SharePoint jest nieprawidłowa.

### <a name="resolution"></a>Rozwiązanie

- Zainstaluj system [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Upewnij się, że masz uprawnienia administratora do witryny sieci Web programu SharePoint. Aby uzyskać więcej informacji, zobacz [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] artykuł online [przypisywanie lub usuwanie administratorów aplikacji usług w programie SharePoint Server](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Zdarzenie sieci Web usuwania witryny nie występuje w projekcie odbiorcy zdarzeń
 Podczas tworzenia projektu odbiorcy zdarzeń i wybierania pewnych zdarzeń sieci Web, takich jak "witryna jest usuwana", zdarzenie nigdy nie występuje.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Ten problem występuje, ponieważ zakres funkcji musi mieć wartość "site" do obsługi zdarzeń na poziomie lokacji, ale domyślny zakres funkcji dla projektów odbiorcy zdarzeń to "Web". Zdarzenia sieci Web, których to dotyczy:

- Trwa usuwanie witryny (usuwanie elementu Web)

- Lokacja została usunięta (usunięto ją z sieci)

- Trwa przenoszenie witryny (przenoszenie)

- Witryna została przeniesiona (przeniesiono)

  Aby rozwiązać ten problem, Zmień zakres funkcji odbiorcy zdarzeń w następujący sposób.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Aby zmienić zakres funkcji odbiorcy zdarzeń

1. W **Eksplorator rozwiązań**Otwórz plik *. feature* odbiorcy zdarzeń w **Projektancie funkcji** przez dwukrotne kliknięcie pliku lub otwarcie jego menu skrótów, a następnie wybranie polecenia **Otwórz**.

2. Wybierz strzałkę obok pozycji **zakres**, a następnie wybierz pozycję **lokacja** na wyświetlonej liście.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Błąd wdrażania występuje po zmianie nazwy identyfikatora w projekcie modelu usługi łączności danych firmy
 Ten problem występuje, jeśli zmienisz nazwę identyfikatora jednostki w modelu łączności danych biznesowych (BDC), a następnie spróbujesz wdrożyć rozwiązanie.

### <a name="error-messages"></a>Komunikaty o błędach

- \<*model name*> ma następujące błędy aktywacji zewnętrznego typu zawartości...

- IMetadataObject o nazwie " \<*model name*> " zawiera zduplikowaną wartość w polu "name"...

### <a name="resolution"></a>Rozwiązanie
 Aby rozwiązać ten problem, Usuń model ręcznie, a następnie ponownie Wdróż rozwiązanie.  Model można usunąć przy użyciu jednego z następujących narzędzi:

- Administracja centralna programu SharePoint 2010. Aby uzyskać więcej informacji, zobacz [Zarządzanie modelami BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) w witrynie sieci Web Microsoft TechNet.

- Windows PowerShell. Możesz usunąć model, wpisując to polecenie w wierszu polecenia: **Remove-SPBusinessDataCatalogModel**. Aby uzyskać więcej informacji, zobacz [Ogólne polecenia cmdlet (SharePoint Server 2010)](/powershell/module/sharepoint-server) w witrynie sieci Web Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Wystąpił błąd podczas próby wyświetlenia wizualnego składnika Web Part w programie SharePoint
 Ten problem występuje, gdy właściwość **Path** kontrolki użytkownika nie zaczyna się od ciągu "elementy ControlTemplates \\ ".

### <a name="error-messages"></a>Komunikaty o błędach

- Plik "/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* . ascx" nie istnieje.

- Błąd serwera w aplikacji "/".

### <a name="resolution"></a>Rozwiązanie

##### <a name="to-resolve-this-issue"></a>Aby rozwiązać ten problem

1. W **Eksplorator rozwiązań**wybierz plik kontrolki użytkownika, którego rozszerzenie nazwy pliku to *. ascx*.

2. Na pasku menu wybierz **View**  >  **okno właściwości**widoku.

3. W oknie **Właściwości** rozwiń węzeł **Lokalizacja wdrożenia** .

4. Upewnij się, że wartość właściwości **Path** zaczyna się od ciągu "elementy ControlTemplates \\ ".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Błąd pojawia się, gdy zostanie uruchomiony importowany przepływ pracy wielokrotnego użytku zawierający pole formularza zadania
 Ten problem występuje w przypadku zaimportowania przepływu pracy zawierającego formularz zadania, który ma pole, a następnie uruchomienie nowego przepływu pracy w tym samym systemie, z którego został on zaimportowany.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd w kroku wdrożenia "Activate Features": w bieżącym zbiorze witryn lub w podlokacji znaleziono pole o identyfikatorze [*GUID*] zdefiniowane w funkcji [*GUID*].

### <a name="resolution"></a>Rozwiązanie
 Ten błąd jest wynikiem kolizji identyfikatora pola, które występuje, ponieważ projekt przepływu pracy wielokrotnego użytku w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie zmienia identyfikatorów pól formularza zadania. W przypadku wdrożenia zaimportowanego przepływu pracy na tym samym serwerze, który zawiera oryginalny przepływ pracy, występują kolizje identyfikatora pola.

 Aby rozwiązać ten problem, użyj funkcji Znajdź i Zamień, aby zmienić wartość atrybutu ID pola we wszystkich zaimportowanych plikach przepływu pracy.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Błąd pojawia się, gdy zostanie uruchomione wystąpienie zaimportowanej nazwy listy
 Ten problem występuje, jeśli zmienisz nazwę zaimportowanego wystąpienia listy, a następnie uruchomisz go w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

### <a name="error-message"></a>Komunikat o błędzie
 Błąd kompilacji: Wystąpił błąd w kroku wdrożenia "Activate Features": plik Template\Features \\ [*Nazwa*<em>funkcji</em>*importowania projektu*] \Files\Lists \\ [*stara*<em>Nazwa listy</em>] \Schema.xml nie istnieje.

### <a name="resolution"></a>Rozwiązanie
 Podczas importowania wystąpienia listy atrybut o nazwie CustomSchema jest dodawany do pliku Elements.xml wystąpienia listy. Elements.xml zawiera ścieżkę schema.xml niestandardowego dla wystąpienia listy. Zmiana nazwy wystąpienia listy w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] powoduje zmianę ścieżki wdrożenia dla schema.xml niestandardowej, ale wartość ścieżki atrybutu CustomSchema nie jest aktualizowana. W związku z tym wystąpienie listy nie może odnaleźć pliku *schema.xml* w starej ścieżce, która jest określona przez atrybut CustomSchema, gdy ta funkcja jest aktywowana.

 Aby rozwiązać ten problem, zaktualizuj ścieżkę lokalizacji wdrożenia pliku *schema.xml* w atrybucie CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Sesja debugowania programu SharePoint zakończona przez usługi IIS
 Ten problem występuje, jeśli ustawisz punkt przerwania w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązaniu programu SharePoint, wybierz klawisz **F5** , aby go uruchomić, a następnie pozostanie w punkcie przerwania dłuższym niż 90 sekund.

### <a name="error-message"></a>Komunikat o błędzie
 Debugowany proces serwera sieci Web został przerwany przez Internet Information Services (IIS). Można uniknąć tego problemu przez skonfigurowanie ustawień ping puli aplikacji w usługach IIS. Aby uzyskać więcej informacji, zobacz Pomoc.

### <a name="resolution"></a>Rozwiązanie
 Domyślnie Pula aplikacji usług IIS czeka 90 sekund na odpowiedź aplikacji przed zamknięciem aplikacji. Ten proces jest nazywany "Pingowanie" aplikacji. Aby rozwiązać ten problem, można albo całkowicie zwiększyć czas oczekiwania lub wyłączyć polecenie ping aplikacji.

##### <a name="to-access-the-iis-app-pool-settings"></a>Aby uzyskać dostęp do ustawień puli aplikacji usług IIS

1. Otwórz Menedżera usług IIS.

2. W okienku **połączenia** rozwiń węzeł serwer programu SharePoint, a następnie wybierz węzeł **Pule aplikacji** .

3. Na stronie **Pule aplikacji** wybierz pulę aplikacji programu SharePoint (zazwyczaj "SharePoint-80"), a następnie w okienku **Akcje** wybierz łącze **Ustawienia zaawansowane** .

4. Aby zwiększyć czas oczekiwania przed upływem limitu czasu usług IIS, Zmień wartość w polu **Maksymalny czas odpowiedzi polecenia ping (w sekundach)** na wartość, która jest większa niż 90 sekund.

5. Aby wyłączyć funkcję ping dla usług IIS, ustaw dla opcji **ping** **wartość false**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Funkcja autowycofywania opuszcza wystąpienie listy oddzielonej w programie SharePoint
 Ten problem występuje w przypadku wykonania poniższych kroków.

1. Utwórz definicję listy, która ma wystąpienie listy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Wybierz klawisz **F5** , aby uruchomić rozwiązanie.

3. Zatrzymaj debugowanie lub Zamknij witrynę programu SharePoint.

4. Otwórz ponownie witrynę programu SharePoint i Otwórz wystąpienie listy.

### <a name="error-message"></a>Komunikat o błędzie
 Błąd serwera w aplikacji "/".

### <a name="resolution"></a>Rozwiązanie
 Dzieje się tak, ponieważ po zamknięciu sesji debugowania rozwiązania SharePoint Funkcja autowycofywania wycofa rozwiązanie. Wycofywanie usuwa definicję listy z programu SharePoint, ale nie usuwa wystąpienia listy. Źródłowa definicja listy jest wymagana przez wystąpienie listy.

 Aby rozwiązać ten problem, wdróż rozwiązanie przez program, na pasku menu wybierz polecenie **Kompiluj**  >  **wdrażanie**. (Nie Debuguj rozwiązania, wybierając klawisz **F5** ). Następnie Usuń wystąpienie listy w programie SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Oryginalne rozwiązanie programu SharePoint zostało zastąpione wyeksportowaną wersją
 Jeśli eksportujesz rozwiązanie programu SharePoint, zaimportuj je do programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , a następnie wdróż rozwiązanie z powrotem do tej samej lokacji, z której zostały wyeksportowane, oryginalne rozwiązanie programu SharePoint zostanie zastąpione. Ten problem nie występuje w przypadku wdrożenia rozwiązania na serwerze, na którym nie zostało aktywowane oryginalne rozwiązanie.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Aby uniknąć nadpisywania rozwiązania w lokacji, z której została wyeksportowana, należy zmienić identyfikatory GUID SolutionID i identyfikator funkcji wszystkich zaimportowanych funkcji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekcie.

## <a name="error-appears-when-debugging-starts"></a>Błąd pojawia się, gdy debugowanie rozpocznie się
 Po rozpoczęciu debugowania rozwiązania programu SharePoint w programie Visual Studio błąd wskazuje, że program Visual Studio nie może załadować pliku Web.config, ponieważ dany klucz nie był w słowniku.

### <a name="error-message"></a>Komunikat o błędzie
 Nie można załadować pliku konfiguracji Web.config. Sprawdź plik pod kątem nieprawidłowych elementów XML i spróbuj ponownie. Wystąpił następujący błąd: podany klucz nie był obecny w słowniku.

### <a name="resolution"></a>Rozwiązanie
 Aby rozwiązać ten problem, upewnij się, że wartość właściwości adres URL witryny projektu programu SharePoint w programie Visual Studio jest zgodna z adresem URL przypisanym do strefy domyślnej dla mapowań dostępu alternatywnego aplikacji sieci Web. Nie można rozwiązać tego błędu za pomocą innej strefy, takiej jak intranet, dla adresu URL. Adres URL witryny dla projektu i adres URL w strefie domyślnej muszą być zgodne. Aby uzyskać dostęp do mapowań alternatywnego dostępu, Otwórz narzędzie SharePoint 2010 Central Administration, wybierz link **Zarządzanie aplikacjami** , a następnie w obszarze **aplikacje sieci Web**wybierz łącze **Konfiguruj alternatywne mapowania dostępu** . Aby uzyskać więcej informacji, zobacz [Tworzenie stref dla aplikacji sieci Web](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Debugowanie w Visual Studio](../debugger/debugger-feature-tour.md)