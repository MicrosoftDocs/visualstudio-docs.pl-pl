---
title: Rozwiązywanie problemów z rozwiązaniami SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: d6b203fcfbe5de92787ae5d2dcaba1b7d9b9454e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870626"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Rozwiązywanie problemów z rozwiązaniami SharePoint
  Następujące problemy lub alerty, mogą wystąpić podczas debugowania rozwiązań programu SharePoint przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera. Aby uzyskać więcej informacji, zobacz [debugowanie rozwiązania przepływu pracy programu SharePoint 2007](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Ograniczenia tokenu w trybie piaskownicy wizualne części sieci web
 Wizualne części sieci web w trybie piaskownicy rozwiązań nie może przetworzyć standardowa tokenów, takich jak $SPUrl, który obsługuje środowisko wykonawcze programu SharePoint. W rezultacie adres URL nie zostanie rozwiązany i nie można przeglądać zawartość w widoku projektowania projektanta wizualnego składnika web part, jeśli odwołujesz się do niego bezpośrednio w elemencie skryptu, takie jak w poniższym przykładzie:

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 Aby obejść to ograniczenie i rozwiązać, token, znaleźć go za pomocą literałów ciągów:

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Ograniczenia dotyczące znaków w nazwach projektów i elementów projektu
 Nazwy projektów i elementów projektu może zawierać tylko znaki, które są dozwolone w ścieżce wdrożenia w programie SharePoint 2010. Inne znaki są niedozwolone.

### <a name="error-message"></a>Komunikat o błędzie
 Komunikat o błędzie "Nieprawidłowe znaki".

### <a name="resolution"></a>Rozwiązanie
 Nazwy projektów programu SharePoint i elementy projektu można użyć w następujących znaków:

- Alfanumeryczne znaki ASCII

- Miejsce

- Kropka (.)

- Przecinek (,)

- Znak podkreślenia (_)

- Łączniki (-)

- Ukośnik odwrotny (\\)

  Gdy projekt jest spakowany, reguły sprawdzania poprawności sprawdza, czy właściwość ścieżka do wdrożenia dla każdego pliku, który jest wdrażany zawiera tylko te prawidłowe znaki.

## <a name="errors-when-creating-custom-fields"></a>Błędy podczas tworzenia pola niestandardowego
 W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], niestandardowych pól zdefiniowanych w pliku XML. Mogą wystąpić błędy, jeśli pole nie jest zdefiniowany lub odwołuje się przy użyciu określonego formatu.

### <a name="error-message"></a>Komunikat o błędzie
 Komunikat o błędzie "Nieprawidłowe znaki" w czasie tworzenia pakietów.

### <a name="resolution"></a>Rozwiązanie
 Identyfikator definicji pola musi być identyfikatorem GUID, ujęte w nawiasy klamrowe, co ilustruje poniższy przykład:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Jak pokazano na poniższym przykładzie, odwołanie do pola w typie zawartości musi być zdefiniowany przy użyciu formatu pustego elementu (\<FieldRef / >), nie za pomocą elementów rozpoczęcia/zakończenia (\<FieldRef >\</FieldRef >):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Jeśli źródła XML dla pola jest źle sformułowany, nie jest prawidłowym plikiem XML lub wykazuje jakiś inny problem, występuje błąd "nie może przeanalizować pliku".

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nowych definicji witryny innej niż angielska nie są wyświetlane na stronie tworzenia lokacji po wdrożeniu
 Po utworzeniu i wdrożenia definicji witryny przy użyciu innej niż angielska wersji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (czyli wersji z ustawieniami regionalnymi [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] niż 1033), **dostosowania SharePoint** karta nie pojawia się w **Wybór szablonu** pole i nowego szablonu witryny nie są wyświetlane w **nową witrynę programu SharePoint** strony.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Ten problem występuje z powodu nieprawidłowej wartości w **ścieżki** właściwość Konfiguracja definicji witryny webtemp plików, takich jak *webtemp_SiteDefinitionProject1.xml*. W **ścieżki** właściwość pliku webtemp znajdujący się w folderze **lokalizacji wdrożenia**, zmień odpowiednie ustawienia regionalne 1033 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Na przykład aby użyć japońskich ustawieniach regionalnych zmień wartość 1041. Aby uzyskać więcej informacji, zobacz [identyfikatory ustawień regionalnych przypisane przez firmę Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Błąd pojawia się podczas wdrażania projektu przepływu pracy w systemie czyste
 Ten problem występuje, gdy wdrożysz projektu przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] systemie czyste. Oczyść system to komputer, który ma nowej instalacji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i programu SharePoint, ale żadne projekty wdrożonej przepływu pracy.

### <a name="error-message"></a>Komunikat o błędzie
 Nie można znaleźć listy programu SharePoint: Historia przepływu pracy.

### <a name="resolution"></a>Rozwiązanie
 Ten błąd występuje ze względu na Brak listy historii przepływu pracy. Ponieważ środowisko programistyczne jest czysty system, żadne przepływy pracy są wdrażane, a na liście historii przepływu pracy jeszcze nie istnieje. Aby rozwiązać ten problem, ponownie otwórz Kreatora przepływu pracy, co powoduje, że listy historii przepływu pracy, który ma zostać utworzony.

##### <a name="to-reenter-the-workflow-wizard"></a>Aby ponownie wprowadzić kreatora przepływu pracy

1.  W **Eksploratora rozwiązań**, wybierz węzeł przepływ pracy.

2.  W **właściwości** okna, wybierz przycisk wielokropka (...) w dowolnej właściwości, która zawiera przycisk wielokropka.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Użytkownik musi odświeżać strony aplikacji w przeglądarce podczas debugowania, aby wyświetlić zaktualizowany obraz
 Jeśli debugujesz rozwiązania programu SharePoint, która zawiera strony aplikacji za pomocą kontrolki, który wyświetla obraz, taki jak [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] kontrolki obrazu, należy odświeżyć stronę w przeglądarce, aby wyświetlić wszelkie zmiany, które zostały wprowadzone do obrazu.

## <a name="error-the-site-location-is-not-valid"></a>Błąd: Lokalizacja witryny jest nieprawidłowa
 Ten problem może wystąpić, jeśli [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] nie jest zainstalowany. Może również wystąpić, jeśli nie masz uprawnienia dostępu administratora do witryny sieci Web programu SharePoint, który jest określony w **Kreator ustawień niestandardowych SharePoint**.

### <a name="error-message"></a>Komunikat o błędzie

-   Lokalizacja witryny programu SharePoint jest nieprawidłowy.

### <a name="resolution"></a>Rozwiązanie

-   Zainstaluj [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

-   Upewnij się, że masz uprawnienia dostępu administratora do witryny sieci Web programu SharePoint. Aby uzyskać więcej informacji, zobacz [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] artykule Online [Przypisywanie lub usuwanie administratorów aplikacji usług w programie SharePoint Server](https://docs.microsoft.com/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Witryna usuwania sieci web zdarzenie nie występuje w projekcie odbiorcy zdarzeń
 Podczas tworzenia projektu odbiorcy zdarzeń, a następnie wybierz wystąpienia określonych zdarzeń w sieci Web, takich jak "lokacji jest usuwana", nigdy nie wystąpi zdarzenie.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Ten problem występuje, ponieważ zakres funkcji musi być "Witryna", aby obsłużyć zdarzenia na poziomie witryny, ale domyślny zakres funkcji dla projektów odbiornik zdarzeń jest "Web". Dostępne są następujące zdarzenia sieci Web, których to dotyczy:

- Lokacji są usuwane (WebDeleting)

- Usunięto witrynę (WebDeleted)

- Trwa lokacji przenieść (WebMoving)

- Przeniesiono witrynę (WebMoved)

  Aby rozwiązać ten problem, zmień zakres funkcji odbiorcy zdarzeń w następujący sposób.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Aby zmienić zakres funkcji odbiorcy zdarzeń

1.  W **Eksploratora rozwiązań**, otwórz odbiorcy zdarzeń *.feature* w pliku **projektanta funkcji** przez dwukrotne kliknięcie pliku albo otwierając jego menu skrótów i następnie Wybieranie **Otwórz**.

2.  Wybierz strzałkę obok **zakres**, a następnie wybierz **witryny** na liście.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Błąd wdrażania pojawia się po zmianie nazwy identyfikatora w projekcie modelu łączności danych biznesowych
 Ten problem występuje, jeśli zmiana nazwy identyfikatora jednostki w modelu łączności danych biznesowych (BDC), a następnie spróbuj wdrożyć to rozwiązanie.

### <a name="error-messages"></a>Komunikaty o błędach

-   \<*Nazwa modelu*> ma następujące błędy aktywacji zewnętrznego typu zawartości...

-   IMetadataObject o nazwie "\<*nazwę modelu*>" ma wartość pola "name" zduplikowanych...

### <a name="resolution"></a>Rozwiązanie
 Aby rozwiązać ten problem, ręcznie usuń model, a następnie należy ponownie wdrożyć rozwiązanie.  Usuń z modelu, przy użyciu jednej z następujących narzędzi:

-   Administracja centralna programu SharePoint 2010. Aby uzyskać więcej informacji, zobacz [zarządzania modelu usługi łączności danych biznesowych](http://go.microsoft.com/fwlink/?LinkID=181472) witryny sieci Web TechNet firmy Microsoft.

-   Windows PowerShell. Można usunąć modelu, wpisując polecenie w wierszu polecenia: **Remove-SPBusinessDataCatalogModel**. Aby uzyskać więcej informacji, zobacz [ogólne polecenia cmdlet (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) witryny sieci Web TechNet firmy Microsoft.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Błąd jest wyświetlany, gdy użytkownik próbuje wyświetlić wizualny składnik web part w programie SharePoint
 Ten problem występuje, gdy **ścieżki** właściwości kontrolki użytkownika nie zaczyna się od ciągu "CONTROLTEMPLATES\\".

### <a name="error-messages"></a>Komunikaty o błędach

-   Plik "/_CONTROLTEMPLATES/*\<Nazwa projektu >*/*\<nazwa składnika Web Part >*/*\<kontrolki użytkownika nazwa >*.ascx "nie istnieje.

-   Błąd serwera w aplikacji» /».

### <a name="resolution"></a>Rozwiązanie

##### <a name="to-resolve-this-issue"></a>Aby rozwiązać ten problem

1.  W **Eksploratora rozwiązań**, wybierz plik kontrolki użytkownika, którego rozszerzenie nazwy pliku jest *ascx*.

2.  Na pasku menu wybierz **widoku** > **okno właściwości**.

3.  W **właściwości** okna, rozwiń węzeł **lokalizacji wdrożenia** węzła.

4.  Upewnij się, że wartość **ścieżki** właściwość zaczyna się od ciągu "CONTROLTEMPLATES\\".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Błąd pojawia się po uruchomieniu importowanych wielokrotny przepływ danych zawierającego pole formularza zadania
 Ten problem występuje, jeśli Importowanie przepływu pracy, który zawiera formularz zadania, który znajduje się pole, a następnie uruchomić nowy przepływ pracy w tym samym systemie, w którym można zaimportować.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd podczas kroku wdrażania "Aktywacja funkcji": Pole o identyfikatorze [*Guid*] zdefiniowany w funkcji [*Guid*] został znaleziony w bieżącej kolekcji witryn lub podwitryn.

### <a name="resolution"></a>Rozwiązanie
 Ten błąd jest wynikiem kolizji identyfikator pola, które występują, ponieważ importowanie przepływu pracy wielokrotnego użytku, do projektu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie zmienia pole formularza zadania identyfikatorów. W przypadku wdrożenia importowanych przepływu pracy na tym samym serwerze, który zawiera oryginalny przepływ pracy występują kolizje identyfikator pola.

 Aby rozwiązać ten problem, należy użyć funkcji Znajdź i Zamień, aby zmienić wartość atrybutu Identyfikatora pola we wszystkich plikach importowanych przepływu pracy.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Błąd pojawia się po zaimportowaniu zmienionej nazwie wystąpienie listy jest wykonywane.
 Ten problem występuje, jeśli zmiana nazwy wystąpienia listy zaimportowane, a następnie uruchom go [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Komunikat o błędzie
 Błąd kompilacji: Wystąpił błąd podczas kroku wdrażania "Aktywacja funkcji": Plik Template\Features\\[*Importuj projekt*<em>funkcji</em>*nazwa*] \Files\Lists\\[*stare* <em>Nazwa listy</em>] \Schema.xml nie istnieje.

### <a name="resolution"></a>Rozwiązanie
 Po zaimportowaniu wystąpienie listy, atrybut o nazwie CustomSchema jest dodawany do pliku Elements.xml wystąpienia listy. Elements.XML zawiera ścieżkę do niestandardowego pliku schema.xml dla instancji listy. Po zmianie nazwy wystąpienia listy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], zmieni się ścieżka wdrażania niestandardowego pliku schema.xml, ale wartość ścieżki atrybutu CustomSchema nie jest aktualizowana. W rezultacie nie można odnaleźć wystąpienia listy *schema.xml* pliku w starej ścieżki, który jest określony przez atrybut CustomSchema, gdy funkcja jest aktywowana.

 Aby rozwiązać ten problem, należy zaktualizować ścieżki lokalizacji wdrożenia programu *schema.xml* pliku w atrybucie CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>Zakończony przez usługi IIS sesji debugowania programu SharePoint
 Ten problem występuje, jeśli ustawisz punkt przerwania w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązania programu SharePoint, wybierz **F5** klawisz, aby ją uruchomić, a następnie pozostają w punkcie przerwania dłużej niż 90 sekund.

### <a name="error-message"></a>Komunikat o błędzie
 Debugowany proces serwera sieci Web został zakończony przez Internetowe usługi informacyjne (IIS). Można uniknąć tego problemu przez skonfigurowanie ustawień polecenia ping dla puli aplikacji w usługach IIS. Zobacz Pomoc, aby uzyskać więcej informacji.

### <a name="resolution"></a>Rozwiązanie
 Domyślnie pula aplikacji usług IIS czeka 90 sekund dla aplikacji, aby odpowiadać przed jej zamknięciem aplikacji. Ten proces jest nazywany "odpowiada na polecenie ping" aplikacji. Aby rozwiązać ten problem, możesz zwiększyć czas oczekiwania lub aplikacji, które odpowiada na polecenie ping całkowicie wyłączyć.

##### <a name="to-access-the-iis-app-pool-settings"></a>Aby uzyskać dostęp do ustawień puli aplikacji usług IIS

1.  Otwórz Menedżera usług IIS.

2.  W **połączeń** okienku rozwiń węzeł serwera programu SharePoint, a następnie wybierz **pul aplikacji** węzła.

3.  Na **pul aplikacji** wybierz pulę aplikacji programu SharePoint (zazwyczaj "SharePoint - 80"), a następnie w **akcje** okienku wybierz **Zaawansowane ustawienia** łącze.

4.  Aby zwiększyć czas oczekiwania przed upływem limitu czasu usług IIS, należy zmienić wartość **maksymalny czas odpowiedzi polecenia Ping (sekundy)** wartość, która jest większa niż 90 sekund.

5.  Aby wyłączyć odpowiada na polecenie ping usług IIS, należy ustawić **pingowanie włączone** do **False**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Automatycznie Wycofaj pozostawia wystąpienie listy oddzielone w programie SharePoint
 Ten problem występuje, gdy należy wykonać następujące czynności.

1.  Tworzenie definicji listy, który powoduje wystąpienie listy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Wybierz **F5** klawisz, aby uruchomić rozwiązanie.

3.  Zatrzymaj debugowanie lub zamknąć witrynę programu SharePoint.

4.  Otwórz witrynę programu SharePoint, a następnie otwórz wystąpienie listy.

### <a name="error-message"></a>Komunikat o błędzie
 Błąd serwera w aplikacji» /».

### <a name="resolution"></a>Rozwiązanie
 Dzieje się tak, ponieważ po zamknięciu sesji debugowania rozwiązania programu SharePoint, które automatycznie Wycofaj funkcji wycofuje rozwiązanie. Wycofywanie rozwiązania spowoduje usunięcie definicji listy z poziomu programu SharePoint, ale nie usuwa wystąpienie listy. Podstawową definicję listy jest wymagana przez wystąpienie listy.

 Aby rozwiązać ten problem, należy wdrożyć rozwiązania, na pasku menu, wybierając **kompilacji** > **Wdróż**. (Nie Debuguj rozwiązanie, wybierając **F5** klucza.) Następnie można usunąć wystąpienia listy w programie SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Oryginalne rozwiązanie programu SharePoint jest zastępowany przy użyciu wersji wyeksportowanego
 Podczas eksportowania rozwiązania programu SharePoint, należy zaimportować rozwiązanie do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], a następnie wdrożyć rozwiązanie tej samej lokacji, z której został wyeksportowany, zastępuje oryginalne rozwiązanie programu SharePoint. Ten problem występuje, gdy wdrożysz rozwiązania na serwerze, na którym nie ma oryginalne rozwiązanie, które aktywowano na nim.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Aby uniknąć zastąpienia rozwiązanie w witrynie, z którego zostały wyeksportowane, zmienić identyfikatory GUID SolutionID i identyfikatory funkcji ze wszystkich funkcji importowanych w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu.

## <a name="error-appears-when-debugging-starts"></a>Pojawia się błąd, gdy debugowanie się rozpocznie
 Podczas uruchamiania debugowania rozwiązania programu SharePoint w programie Visual Studio, błąd wskazuje, że Visual Studio nie można załadować pliku Web.config, ponieważ podany klucz nie był w słowniku.

### <a name="error-message"></a>Komunikat o błędzie
 Nie można załadować pliku konfiguracji Web.config. Źle sformułowane elementów XML w pliku i spróbuj ponownie. Wystąpił następujący błąd: Podany klucz nie istnieje w słowniku.

### <a name="resolution"></a>Rozwiązanie
 Aby rozwiązać ten problem, upewnij się, że wartość właściwości adres URL witryny projektu programu SharePoint w programie Visual Studio jest zgodny adres URL, który jest przypisany do strefy domyślnej dla mapowania dostępu alternatywnego aplikacji sieci web. Nie można rozpoznać błędu przy użyciu innej strefy, takich jak Intranet, aby uzyskać adres URL. Witryna adres URL projektu i adres URL w strefie domyślne muszą być zgodne. Dostępu mapowań dostępu alternatywnego, Otwórz narzędzie administracji centralnej programu SharePoint 2010, wybrać **Zarządzanie aplikacjami** łącza, a następnie w obszarze **aplikacji sieci Web**, wybierz  **Konfigurowanie alternatywnych mapowań dostępu** łącza. Aby uzyskać więcej informacji, zobacz [tworzenie stref dla aplikacji sieci Web](http://go.microsoft.com/fwlink/?LinkId=192274).

## <a name="see-also"></a>Zobacz także

- [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md)