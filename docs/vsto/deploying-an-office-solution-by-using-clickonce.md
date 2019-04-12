---
title: Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90f7fe4d3e4b316f48aed46c40b3d24e0969a536
ms.sourcegitcommit: 7eb85d296146186e7a39a17f628866817858ffb0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59504435"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce
  Można wdrożyć rozwiązania pakietu Office w mniejszej liczby czynności, jeśli użycie technologii ClickOnce. Podczas publikowania aktualizacji rozwiązanie automatycznie je wykryje i zainstaluje. Niedogodność polega na tym, że w technologii ClickOnce rozwiązanie trzeba zainstalować osobno dla każdego użytkownika komputera. W związku z tym, należy rozważyć użycie Instalatora Windows (*.msi*) Jeśli więcej niż jeden użytkownik uruchomi swoje rozwiązanie na tym samym komputerze.

## <a name="in-this-topic"></a>W tym temacie:

- [Publikowanie rozwiązania](#Publish)

- [Decyzja w sprawie sposobu udzielenia zaufania rozwiązaniu](#Trust)

- [Pomaganie użytkownikom w instalowaniu rozwiązania](#Helping)

- [Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)](#Put)

- [Umieszczanie dokumentu rozwiązania na serwerze z programem SharePoint (tylko dostosowania na poziomie dokumentu)](#SharePoint)

- [Tworzenie niestandardowego instalatora](#Custom)

- [Publikowanie aktualizacji](#Update)

- [Zmiana lokalizacji instalacji rozwiązania](#Location)

- [Wycofywanie rozwiązania do wcześniejszej wersji](#Roll)

  Aby uzyskać więcej informacji na temat wdrażania rozwiązania do pakietu Office przez utworzenie pliku Instalatora Windows, zobacz [wdrażania rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

##  <a name="Publish"></a> Publikowanie rozwiązania
 Rozwiązanie można opublikować za pomocą **Kreatora publikacji** lub **projektanta projektu**. W tej procedurze użyjesz **projektanta projektu** ponieważ zapewnia kompletny zestaw opcji publikowania. Zobacz [Kreator publikowania &#40;programowanie Office w Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Aby opublikować rozwiązanie

1. W **Eksploratora rozwiązań**, wybierz węzeł, który nosi nazwę dla projektu.

2. Na pasku menu wybierz **projektu**, *ProjectName* **właściwości**.

3. W **projektanta projektu**, wybierz **Publikuj** kartę, która na następującej ilustracji pokazano.

    ![Na karcie publikowanie w Projektancie projektu](../vsto/media/vsto-publishtab.png "na karcie publikowanie w Projektancie projektu")

4. W **lokalizacja folderu publikowania (serwer ftp lub ścieżka do pliku)** wprowadź ścieżkę do folderu, w której chcesz **projektanta projektu** kopiować pliki rozwiązania.

    Możesz użyć dowolnego z następujących typów ścieżek.

   -   Ścieżka lokalna (na przykład *C:\FolderName\FolderName*).

   -   Ścieżkę Uniform Naming Convention (UNC) do folderu w sieci (na przykład  *\\\ServerName\FolderName*).

   -   Ścieżka względna (na przykład *PublishFolder\\*, czyli do folderu, w którym projekt zostanie opublikowany domyślnie).

5. W **adres URL folderu instalacyjnego** wprowadź pełną ścieżkę lokalizacji, w którym użytkownicy końcowi znajdą rozwiązanie.

    Jeśli jeszcze nie znasz lokalizacji, nie wypełniaj tego pola. Domyślnie funkcja ClickOnce szuka aktualizacji w folderze, z którego użytkownicy instalują rozwiązanie.

6. Wybierz **wymagania wstępne** przycisku.

7. W **wymagania wstępne** okna dialogowego pole, upewnij się, że **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.

8. W **wybierz wstępnie wymagane składniki do zainstalowania** listy, zaznacz pole wyboru dla **Windows Installer 4.5** i odpowiedniego pakietu .NET Framework.

    Na przykład jeśli Twoje rozwiązanie wskazuje [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], zaznacz pole wyboru dla **Windows Installer 4.5** i **Microsoft .NET Framework 4.5 Full**.

9. Jeśli rozwiązanie jest przeznaczony dla .NET Framework 4.5, również wybrać opcję **Visual Studio 2010 Tools for Office Runtime** pole wyboru.

    > [!NOTE]
    >  Domyślnie nie jest wyświetlane to pole wyboru. Aby było widoczne, należy utworzyć pakiet programu inicjującego. Zobacz [Tworzenie pakietu programu inicjującego dla dodatku pakietu Office 2013 VSTO za pomocą programu Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. W obszarze **Określ lokalizację instalacji wstępnie wymaganych składników**, wybierz jedną z opcji, które są wyświetlane, a następnie wybierz **OK** przycisku.

     W tabeli poniżej opisano wszystkie opcje.

    |Opcja|Opis|
    |------------|-----------------|
    |**Pobierz wstępnie wymagane składniki z witryny dostawcy składników**|Użytkownik jest monitowany o pobranie i zainstalowanie wstępnie wymaganych składników z witryny internetowej dostawcy.|
    |**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co aplikację**|Wstępnie wymagane oprogramowanie jest instalowane razem z oprogramowaniem. W przypadku zaznaczenia tej opcji program Visual Studio automatycznie kopiuje wszystkie wstępnie wymagane pakiety do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
    |**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Visual Studio kopiuje wszystkie wstępnie wymagane pakiety do wskazanej lokalizacji i instaluje je razem z rozwiązaniem.|

     Zobacz [wstępnie wymagane składniki, okno dialogowe](../ide/reference/prerequisites-dialog-box.md).

11. Wybierz **aktualizacje** przycisk, określ, jak często chcesz każdego użytkownika końcowego dodatku narzędzi VSTO lub dostosowywania sprawdzać dostępność aktualizacji, a następnie wybierz **OK** przycisku.

    > [!NOTE]
    >  Jeśli instalujesz z dysku CD lub dysku wymiennego, wybierz **nigdy nie sprawdzaj aktualizacji** przycisku opcji.

     Aby uzyskać informacje o sposobie publikowania aktualizacji, zobacz [publikowanie aktualizacji](#Update).

12. Wybierz **opcje** przycisk, przejrzyj opcje w **opcje** okna dialogowego pole, a następnie wybierz **OK** przycisku.

13. Wybierz **Publikuj teraz** przycisku.

     Program Visual Studio dodaje następujące foldery i pliki do folderu publikowania określonego wcześniej w tej procedurze.

    - **Pliki aplikacji** folderu.

    - Program instalacyjny.

    - Manifest wdrażania odwołujący się do manifestu wdrażania najnowszej wersji.

      **Pliki aplikacji** folder zawiera osobny podfolder dla każdej publikowanej wersji. Każdy podfolder danej wersji zawiera następujące pliki.

    - Manifest aplikacji.

    - Manifest wdrażania.

    - Zestawy dostosowywania.

      Na poniższej ilustracji przedstawiono strukturę folderu publikowania dla dodatku narzędzi VSTO dla programu Outlook.

      ![Struktura folderu publikowania](../vsto/media/publishfolderstructure.png "strukturę folderu publikowania")

    > [!NOTE]
    >  Funkcja ClickOnce dołącza *.deploy* rozszerzenia do zestawów, tak aby bezpieczna instalacja programu Internetowe usługi informacyjne (IIS) nie blokowała plików z powodu niebezpiecznego rozszerzenia. Po zainstalowaniu rozwiązania ClickOnce usuwa *.deploy* rozszerzenia.

14. Skopiuj pliki rozwiązania do lokalizacji instalacji określonej wcześniej w tej procedurze.

##  <a name="Trust"></a> Decyzja w sprawie sposobu udzielenia zaufania rozwiązaniu
 Zanim rozwiązanie będzie można uruchomić na komputerach użytkowników, administrator musi udzielić zaufania albo użytkownicy muszą odpowiedzieć na monit o udzielenie zaufania podczas instalacjo rozwiązania. Aby administrator przyznał zaufanie rozwiązaniu, musi podpisać manifest za pomocą certyfikatu identyfikującego znanego i zaufanego wydawcę. Zobacz [zaufania rozwiązania przez podpisanie manifestów aplikacji i wdrożenia](../vsto/granting-trust-to-office-solutions.md#Signing).

 Jeśli wdrażasz dostosowywania poziomie dokumentu i chcesz umieścić dokument do folderu na komputerze użytkownika lub udostępnić dokument w witrynie programu SharePoint, upewnij się, że pakiet Office ufa lokalizacji dokumentu. Zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

##  <a name="Helping"></a> Pomaganie użytkownikom w instalowaniu rozwiązania
 Użytkownicy mogą zainstalować rozwiązanie przez uruchomienie programu instalacyjnego, otwarcie manifestu wdrażania lub podczas dostosowywania poziomie dokumentu, bezpośrednie otwarcie dokumentu. Według najlepszych praktyk rozwiązanie należy instalować przy użyciu programu instalacyjnego. Pozostałe dwie metody nie gwarantują, że wstępnie wymagane oprogramowanie jest zainstalowane. Jeśli użytkownicy chcą otwierać dokument z lokalizacji instalacji, muszą ją dodać do listy zaufanych lokalizacji w Centrum zaufania w aplikacji pakietu Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Otwieranie dokumentu z dostosowaniem na poziomie dokumentu
 Użytkownicy mogą otwierać dokument zawierający dostosowanie na poziomie dokumentu bezpośrednio z lokalizacji instalacji albo przez skopiowanie go swoich lokalnych komputerów, a następnie otwarcie kopii.

 Według najlepszych praktyk należy otwierać kopię dokumentu na swoim komputerze, tak aby wiele osób nie próbowało otworzyć jednocześnie tego samego wystąpienia. W celu wymuszenia tej praktyki można tak skonfigurować program instalacyjny, aby kopiował dokument na komputery użytkowników. Zobacz [umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instalowanie rozwiązania przez otwarcie manifestu wdrażania z witryny sieci Web usług IIS
 Użytkownicy mogą zainstalować rozwiązanie dla pakietu Office poprzez otwarcie manifestu wdrażania z Internetu. Jednak bezpieczna instalacja programu Internetowe usługi informacyjne (IIS) blokuje pliki, które mają *.vsto* rozszerzenia. Zanim będzie można wdrożyć rozwiązanie za pomocą usług IIS, w usługach musi być zdefiniowany typ MIME.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Aby dodać typ MIME .vsto do usług IIS 6.0

1.  Na serwerze, na którym działa program IIS 6.0 wybierz **Start** > **wszystkie programy** > **narzędzia administracyjne**  >   **Internetowych usług informacyjnych (IIS) Manager**.

2.  Wybierz nazwę komputera **witryn sieci Web** folderu lub witryny sieci web, którą konfigurujesz.

3.  Na pasku menu wybierz **akcji** > **właściwości**.

4.  Na **nagłówków HTTP** kartę, wybrać **typy MIME** przycisku.

5.  W **typy MIME** oknie Wybierz **New** przycisku.

6.  W **typ MIME** oknie wprowadź **.vsto** jako rozszerzenie wprowadź **application/x-ms-vsto** jako MIME typu, a następnie Zastosuj nowe ustawienia.

    > [!NOTE]
    >  Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Należy następnie opróżnić pamięć podręczną dysku w przeglądarce i spróbuj otworzyć *.vsto* plik ponownie.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Aby dodać typ MIME .vsto do usług IIS 7.0

1.  Na serwerze, na którym jest uruchomiony usług IIS 7.0, wybierz **Start** > **wszystkie programy** > **Akcesoria**.

2.  Otwórz menu skrótów dla **polecenia**, a następnie wybierz **Uruchom jako administrator.**

3.  W **Otwórz** wprowadź następującą ścieżkę, a następnie wybierz **OK** przycisku.

    ```cmd
    %windir%\system32\inetsrv
    ```

4.  Wprowadź następujące polecenie, a następnie zastosuj nowe ustawienia.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    >  Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Należy następnie opróżnić pamięć podręczną dysku w przeglądarce i spróbuj otworzyć *.vsto* plik ponownie.

##  <a name="Put"></a> Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)
 Tworząc akcję powdrożeniową, możesz skopiować dokumentu rozwiązania na komputerze użytkownika końcowego dla nich. Dzięki temu użytkownik nie musi ręcznie kopiować dokumentu z lokalizacji instalacji do swojego komputera po zainstalowaniu rozwiązania. Należy utworzyć klasę definiującą akcję powdrożeniową, kompilacji i opublikować rozwiązanie, zmodyfikować manifest aplikacji i ponownie podpisać manifesty aplikacji i wdrażania.

 W poniższych procedurach założono, że nazwa projektu jest **ExcelWorkbook** i opublikować rozwiązanie do utworzonego folderu o nazwie **C:\publish** na tym komputerze.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Tworzenie klasy definiującej akcję powdrożeniową

1. Na pasku menu wybierz **pliku** > **Dodaj** > **nowy projekt**.

2. W **Dodaj nowy projekt** dialogowym **zainstalowane szablony** okienku wybierz **Windows** folderu.

3. W **szablony** okienku wybierz **biblioteki klas** szablonu.

4. W **nazwa** wprowadź **FileCopyPDA**, a następnie wybierz **OK** przycisku.

5. W **Eksploratora rozwiązań**, wybierz **FileCopyPDA** projektu.

6. Na pasku menu wybierz **projektu** > **Dodaj odwołanie**.

7. Na **.NET** kartę, należy dodać odwołania do `Microsoft.VisualStudio.Tools.Applications.Runtime` i `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.

8. Zmień nazwę klasy, która ma `FileCopyPDA`, a następnie zastąp zawartość pliku z kodem. Kod będzie wykonywał następujące zadania:

   - Kopiowanie dokumentu do komputera użytkownika.

   - Zmienia właściwość _AssemblyLocation ścieżki względnej do pełni kwalifikowaną ścieżką do manifestu wdrażania.

   - Usunięcie pliku, jeśli użytkownik odinstaluje rozwiązanie.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Kompilowanie i publikowanie rozwiązania

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **FileCopyPDA** projektu, a następnie wybierz **kompilacji**.

2.  Otwórz menu skrótów dla **ExcelWorkbook** projektu, a następnie wybierz **kompilacji**.

3.  Otwórz menu skrótów dla **ExcelWorkbook** projektu, a następnie wybierz **Dodaj odwołanie**.

4.  W **Dodaj odwołanie** okna dialogowego wybierz **projektów** karty, wybierz polecenie **FileCopyPDA**, a następnie wybierz **OK** przycisk.

5.  W **Eksploratora rozwiązań**, wybierz **ExcelWorkbook** projektu.

6.  Na pasku menu wybierz **projektu** > **nowy Folder**.

7.  Wprowadź **danych**, a następnie wybierz **Enter** klucza.

8.  W **Eksploratora rozwiązań**, wybierz **danych** folderu.

9. Na pasku menu wybierz **projektu** > **Dodaj istniejący element**.

10. W **Dodaj istniejący element** okno dialogowe, przejdź do katalogu wyjściowego dla **ExcelWorkbook** projektu, wybierz **ExcelWorkbook.xlsx** , a następnie wybierz  **Dodaj** przycisku.

11. W **Eksploratora rozwiązań** wybierz **ExcelWorkbook.xlsx** pliku.

12. W **właściwości** oknie zmiany **Build Action** właściwości **zawartości** i **Kopiuj do katalogu wyjściowego** właściwości  **Kopiuj Jeśli nowszy**.

     Po zakończeniu tych czynności projekt będzie przypominał poniższą ilustrację.

     ![Struktury projektu akcji powdrożeniowej. ](../vsto/media/vsto-postdeployment.png "Struktura wpisu Akcja wdrażania projektu.")

13. Publikowanie **ExcelWorkbook** projektu.

### <a name="modify-the-application-manifest"></a>Modyfikowanie manifestu aplikacji

1.  Otwórz katalog rozwiązania **c:\publish**, za pomocą **Eksploratora plików**.

2.  Otwórz **pliki aplikacji** folder, a następnie otwórz folder odpowiadający najnowszej opublikowanej wersji rozwiązania.

3.  Otwórz **ExcelWorkbook.dll.manifest** plik w edytorze tekstów, takiego jak Notatnik.

4.  Po `</vstav3:update>` elementu, Dodaj następujący kod. Dla atrybutu klasy elementu `<vstav3:entryPoint>` elementu, należy użyć następującej składni: *NamespaceName.ClassName*. W poniższym przykładzie nazwy przestrzeni nazw i klasy są takie same, dzięki czemu wynikowy nazwy punktu wejścia jest `FileCopyPDA.FileCopyPDA`.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Ponowne podpisywanie manifestów aplikacji i wdrażania

1.  W **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** folderu, kopiowanie **ExcelWorkbook_TemporaryKey.pfx** plik certyfikatu, a następnie wklej ją do  *PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ folderu.

2.  Otwórz wiersz polecenia programu Visual Studio, a następnie zmień katalogi na **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ folderu (na przykład **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3.  Podpisz zmodyfikowany manifest aplikacji, wykonując następujące polecenie:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.manifest został pomyślnie podpisany”.

4.  Zmień **c:\publish** folder, a następnie aktualizacji i zaloguj wdrożenia manifestu, uruchamiając następujące polecenie:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    >  W poprzednim przykładzie, Zamień wartość elementu MostRecentVersionNumber numer wersji najnowszej opublikowanej wersji rozwiązania (na przykład **1_0_0_4**).

     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.vsto został pomyślnie podpisany”.

5.  Kopiuj *plik excelworkbook.dll.VSTO został* plik **c:\publish\Application Files\ExcelWorkbook**\__wartość elementu MostRecentVersionNumber_ katalogu.

##  <a name="SharePoint"></a> Umieszczanie dokumentu rozwiązania na serwerze, na którym uruchomiony jest SharePoint (tylko dostosowania na poziomie dokumentu)
 Dostosowanie na poziomie dokumentu można opublikować użytkownikom końcowym za pomocą programu SharePoint. Gdy użytkownicy przejdą do witryny programu SharePoint i otworzą dokument, środowisko uruchomieniowe automatycznie zainstaluje rozwiązanie z udostępnionego folderu sieciowego na komputerze lokalnym. Po lokalnym zainstalowaniu rozwiązania dostosowanie nadal będzie działać, nawet, jeśli dokument skopiowano w inne miejsce, na przykład na pulpit.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Aby umieścić dokument na serwerze z programem SharePoint

1.  Dodaj dokument z rozwiązania do biblioteki dokumentów w witrynie programu SharePoint.

2.  Wykonaj czynności dla jednej z poniższych metod:

    -   Za pomocą narzędzia konfiguracji pakietu Office dodaj serwer z programem do Centrum zaufania w programie Word lub Excel na komputerach wszystkich użytkowników.

         Zobacz [zasady zabezpieczeń i ustawienia w pakiecie Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).

    -   Upewnij się, że każdy użytkownik wykona następujące czynności.

        1.  Na komputerze lokalnym, Otwórz program Word lub Excel, wybierz **pliku** kartę, a następnie wybierz **opcje** przycisku.

        2.  W **Centrum zaufania** okna dialogowego wybierz **zaufane lokalizacje** przycisku.

        3.  Wybierz **Zezwalaj na zaufane lokalizacje w mojej sieci (niezalecane)** pole wyboru, a następnie wybierz **Dodaj nową lokalizację** przycisku.

        4.  W **ścieżki** wprowadź adres URL biblioteki dokumentów programu SharePoint, która zawiera dokument, który został przekazany (na przykład *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).

             Nie dodawaj nazwy domyślnej strony sieci Web, takich jak *default.aspx* lub *AllItems.aspx*.

        5.  Wybierz **podfoldery tej lokalizacji są także zaufane** pole wyboru, a następnie wybierz **OK** przycisku.

             Gdy użytkownicy otwierają dokument z poziomu witryny programu SharePoint, następuje otwarcie dokumentu i zainstalowanie dostosowania. Użytkownicy mogą wtedy skopiować dokument na swoje komputery. Dostosowanie będzie nadal działać, ponieważ właściwości w dokumencie wskazują jego lokalizację sieciową.

##  <a name="Custom"></a> Tworzenie niestandardowego Instalatora
 Można utworzyć niestandardowego Instalatora dla rozwiązania pakietu Office, a nie za pomocą programu instalacyjnego, który jest tworzony automatycznie podczas publikowania rozwiązania. Na przykład można użyć znaku w skrypcie aby rozpocząć instalację lub wystarczą plik wsadowy może instalować rozwiązanie bez udziału użytkownika. Scenariusze te działają najlepiej, jeśli na komputerach użytkowników końcowych są już zainstalowane wstępnie wymagane składniki.

 W ramach procesu niestandardowej instalacji, należy wywołać narzędzie Instalatora dla rozwiązań pakietu Office (*VSTOInstaller.exe*), która jest domyślnie instalowana w następującej lokalizacji:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Jeśli narzędzie nie znajduje się w tej lokalizacji, możesz użyć **folderze Runtime Setup\v4\InstallerPath** lub **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4 \InstallerPath** klucz rejestru, aby znaleźć ścieżkę do tego narzędzia.

 Można użyć poniższych parametrów za pomocą *VSTOinstaller.exe*.


| Parametr | Definicja |
|------------------| - |
| /Install lub /I | Instalowanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Można określić ścieżkę na komputerze lokalnym universal naming convention (UNC) udziału plików. Można określić ścieżkę lokalną (*C:\FolderName\PublishFolder*), ścieżką względną (*Publikuj\\*), lub w pełni kwalifikowanej lokalizacji (*\\\ServerName\ Nazwa folderu* lub http://<em>ServerName/FolderName</em>). |
| /Uninstall lub /U | Odinstalowywanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Można określić ścieżki, może być na komputerze lokalnym, UNC udziału plików. Można określić ścieżkę lokalną (*c:\FolderName\PublishFolder*), ścieżką względną (*Publikuj\\*), lub w pełni kwalifikowanej lokalizacji (*\\\ServerName\ Nazwa folderu* lub http://<em>ServerName/FolderName</em>). |
| /Silent lub /S | Instalowanie lub odinstalowywanie bez monitowania użytkownika o wprowadzenie danych ani wyświetlania jakichkolwiek komunikatów. Jeśli wymagana jest monit o udzielenie zaufania, dostosowanie nie jest zainstalowany lub aktualizowane. |
| /Help lub /? | Wyświetlanie informacji Pomocy. |

 Po uruchomieniu *VSTOinstaller.exe*, następujące kody błędów mogą być wyświetlane.

|Kod błędu|Definicja|
|----------------|----------------|
|0|Rozwiązanie zostało pomyślnie zainstalowane lub odinstalowane albo została wyświetlona Pomoc narzędzia VSTOInstaller.|
|-100|Co najmniej jedna opcja wiersza polecenia są nieprawidłowe lub nie ustawiono więcej niż jeden raz. Aby uzyskać więcej informacji, wpisz "vstoinstaller /?" lub zobacz [utworzyć niestandardowego Instalatora dla rozwiązania ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Co najmniej jedna opcja wiersza polecenia są nieprawidłowe. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|
|-200|Identyfikator URI manifestu wdrażania jest nieprawidłowy. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|
|-201|Nie można zainstalować rozwiązania, ponieważ manifest wdrażania jest nieprawidłowy. Zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Nie można zainstalować rozwiązania, ponieważ Visual Studio Tools for Office części manifestu aplikacji nie jest prawidłowa. Zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Nie można zainstalować rozwiązania, ponieważ wystąpił błąd pobierania. Sprawdź identyfikator URI lub lokalizację pliku sieciowego manifestu wdrażania, a następnie ponów próbę.|
|-300|Nie można zainstalować rozwiązania, ponieważ wystąpił wyjątek zabezpieczeń. Zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).|
|-400|Nie można zainstalować rozwiązania.|
|-401|Nie można odinstalować rozwiązania.|
|-500|Operacja została anulowana, ponieważ nie można zainstalować lub odinstalować rozwiązania albo nie można pobrać manifestu wdrażania.|

##  <a name="Update"></a> Publikowanie aktualizacji
 Aby zaktualizować to rozwiązanie, należy je opublikować ponownie przy użyciu **projektanta projektu** lub **Kreatora publikacji**, a następnie skopiować zaktualizowane rozwiązanie do lokalizacji instalacji. Podczas kopiowania plików do lokalizacji instalacji trzeba koniecznie zaznaczyć opcję zastąpienia poprzednich plików.

 Gdy następnym razem rozwiązanie będzie sprawdzać dostępność aktualizacji, znajdzie i automatycznie zainstaluje nową wersję.

##  <a name="Location"></a> Zmiana lokalizacji instalacji rozwiązania
 Po opublikowaniu rozwiązania można dodać lub zmienić ścieżkę instalacji. Często powody takiej zmiany są następujące:

- Program instalacyjny został skompilowany przed ustaleniem ścieżki instalacji.

- Pliki rozwiązania skopiowano do innej lokalizacji.

- Serwer, na którym znajdują się pliki instalacyjne, ma nową nazwę lub lokalizację.

  Aby zmienić ścieżkę instalacji rozwiązania, należy zaktualizować program instalacyjny, po czym użytkownicy muszą go uruchomić. W przypadku dostosowań na poziomie dokumentu użytkownicy muszą również w swoich dokumentach tak zaktualizować odnośną właściwość, aby wskazywała nową lokalizację.

> [!NOTE]
>  Jeśli nie chcesz poprosić użytkowników o właściwości dokumentów, możesz poprosić użytkownikom pobranie zaktualizowanego dokumentu z lokalizacji instalacji.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Aby zmienić ścieżkę instalacji w programie instalacyjnym

1. Otwórz **polecenia** okna, a następnie zmień katalogi do folderu instalacji.

2. Uruchom program instalacyjny i obejmują `/url` parametr, który przyjmuje nową ścieżkę instalacji jako ciągu.

    Poniższy przykład pokazuje, jak zmienić ścieżkę instalacji na lokalizację w witrynie internetowej firmy Fabrikam; widoczny adres URL można zastąpić dowolną inną ścieżką:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   >  Jeśli pojawi się komunikat z informacją, że podpis pliku wykonywalnego zostanie unieważniony, certyfikat użyty do podpisania rozwiązania jest nieważny, a wydawca nieznany. W rezultacie przed zainstalowaniem rozwiązania użytkownicy będą musieli potwierdzić, że ufają jego źródłu.

   > [!NOTE]
   >  Aby wyświetlić bieżącą wartość adresu URL, należy uruchomić `setup.exe /url`.

   Przypadku dostosowań na poziomie dokumentu użytkownicy muszą otworzyć dokument, a następnie zaktualizować jego właściwość _AssemblyLocation. Poniżej zamieszczono odpowiednią procedurę.

#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Aby zaktualizować właściwość _AssemblyLocation w dokumencie

1.  Na **pliku** karty, wybierz polecenie **informacje**, który przedstawiono na poniższej ilustracji.

     ![Karta informacje w programie Excel](../vsto/media/vsto-infotab.png "karta informacje w programie Excel")

2.  W **właściwości** wybierz **zaawansowane właściwości**, który przedstawiono na poniższej ilustracji.

     ![Zaawansowane właściwości w programie Excel. ](../vsto/media/vsto-advanceddocumentproperties.png "Zaawansowane właściwości w programie Excel.")

3.  Na **niestandardowe** karcie **właściwości** wybierz _AssemblyLocation, jak pokazano na następującym rysunku.

     ![Właściwość AssemblyLocation. ](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation właściwości.")

     **Wartość** pole zawiera identyfikator manifestu wdrażania.

4.  Przed identyfikatorem wprowadź w pełni kwalifikowaną ścieżkę dokumentu, następuje pasku w formacie *ścieżki*|*identyfikator* (na przykład *File://ServerName/ Nazwa folderu/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Aby uzyskać więcej informacji na temat formatowania tego identyfikatora, zobacz [właściwości niestandardowego dokumentu ― omówienie](../vsto/custom-document-properties-overview.md).

5.  Wybierz **OK** przycisk, a następnie zapisz i zamknij dokument.

6.  Uruchom program instalacyjny bez parametru /url. Rozwiązanie zostanie zainstalowane w podanej lokalizacji.

##  <a name="Roll"></a> Wycofywanie rozwiązania do wcześniejszej wersji
 Wycofanie rozwiązania powoduje, że użytkownicy wrócą do korzystania z jego starszej wersji.

#### <a name="to-roll-back-a-solution"></a>Aby wycofać rozwiązanie

1.  Otwórz lokalizację instalacji rozwiązania.

2.  W najwyższego poziomu folderu publikowania, Usuń manifest wdrażania ( *.vsto* pliku).

3.  Znajdź podfolder wersji, do której chcesz wycofać rozwiązanie.

4.  Skopiuj manifest wdrażania z tego podfolderu do folderu publikowania najwyższego poziomu.

     Na przykład, aby wycofać rozwiązanie, która jest wywoływana **OutlookAddIn1** z wersji 1.0.0.1 do wersji 1.0.0.0, skopiuj plik **OutlookAddIn1.vsto** z **OutlookAddIn1_1_0_0_0** folderu. Wklej plik do najwyższego poziomu publikowanie folderu, zastępując manifest wdrażania wersji **OutlookAddIn1_1_0_0_1** było już istnieje.

     Na ilustracji poniżej widać strukturę folderu publikowania w opisywanym przykładzie.

     ![Struktura folderu publikowania](../vsto/media/publishfolderstructure.png "strukturę folderu publikowania")

     Gdy użytkownik następnym razem otworzy aplikację lub dostosowany dokument, zostanie wykryta zmiana manifestu wdrażania. Starsza wersja rozwiązania dla pakietu Office jest uruchamiana z pamięci podręcznej funkcji ClickOnce.

> [!NOTE]
>  Dane lokalne są zapisywane tylko dla jednej poprzedniej wersji rozwiązania. W przypadku wycofania dwie wersje lokalne dane nie zostaną zachowane. Aby uzyskać więcej informacji na temat danych lokalnych, zobacz [dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Publikowanie rozwiązań Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Instrukcje: Publikowanie rozwiązań pakietu Office przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Instrukcje: Zainstalować rozwiązanie ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Instrukcje: Publikowanie rozwiązań Office poziomu dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Tworzenie niestandardowego Instalatora dla rozwiązań office ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)