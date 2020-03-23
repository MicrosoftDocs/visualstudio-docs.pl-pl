---
title: Wdrażanie rozwiązania pakietu Office przy użyciu funkcji ClickOnce
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
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416565"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Wdrażanie rozwiązania pakietu Office przy użyciu funkcji ClickOnce
  Rozwiązanie pakietu Office można wdrożyć w mniejszej liczbie kroków, jeśli używasz ClickOnce. Podczas publikowania aktualizacji rozwiązanie automatycznie je wykryje i zainstaluje. Niedogodność polega na tym, że w technologii ClickOnce rozwiązanie trzeba zainstalować osobno dla każdego użytkownika komputera. W związku z tym należy rozważyć użycie Instalatora Windows (*msi*), jeśli więcej niż jeden użytkownik uruchomi rozwiązanie na tym samym komputerze.

## <a name="in-this-topic"></a>W tym temacie:

- [Publikowanie rozwiązania](#Publish)

- [Zdecyduj, w jaki sposób chcesz udzielić zaufania do rozwiązania](#Trust)

- [Pomóż użytkownikom zainstalować rozwiązanie](#Helping)

- [Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)](#Put)

- [Umieszczanie dokumentu rozwiązania na serwerze z uruchomionym programem SharePoint (tylko dostosowania na poziomie dokumentu)](#SharePoint)

- [Tworzenie niestandardowego instalatora](#Custom)

- [Publikowanie aktualizacji](#Update)

- [Zmienianie lokalizacji instalacji rozwiązania](#Location)

- [Wycofywanie rozwiązania do wcześniejszej wersji](#Roll)

  Aby uzyskać więcej informacji na temat wdrażania rozwiązania pakietu Office przez utworzenie pliku Instalatora Windows, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a>Publikowanie rozwiązania
 Rozwiązanie można opublikować za pomocą **Kreatora publikowania** lub **projektanta projektów**. W tej procedurze użyjesz **Projektanta projektu,** ponieważ zawiera pełny zestaw opcji publikowania. Zobacz [Kreator publikowania &#40;program rozwoju pakietu Office w programie Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Aby opublikować rozwiązanie

1. W **Eksploratorze rozwiązań**wybierz węzeł, który ma nazwę dla projektu.

2. Na pasku menu wybierz polecenie **Project**, *ProjectName* **Properties**.

3. W **projektancie projektu**wybierz kartę **Publikowania,** na której pokazano poniższą ilustrację.

    ![Karta publikowania projektanta projektów](../vsto/media/vsto-publishtab.png "Karta publikowania projektanta projektów")

4. W polu **Lokalizacja folderu publikowania (serwer ftp lub ścieżka pliku)** wprowadź ścieżkę folderu, w którym **projektant projektu** ma kopiować pliki rozwiązania.

    Możesz użyć dowolnego z następujących typów ścieżek.

   - Ścieżka lokalna (na przykład *C:\FolderName\FolderName*).

   - Ścieżka unc (Uniform Naming Convention) do folderu w sieci (na przykład * \\\ServerName\FolderName*).

   - Ścieżka względna (na przykład *PublishFolder\\*, która jest folderem, do którego projekt jest publikowany domyślnie).

5. W polu **Adres URL folderu instalacyjnego** wprowadź w pełni kwalifikowaną ścieżkę lokalizacji, w której użytkownicy końcowi znajdą rozwiązanie.

    Jeśli nie znasz jeszcze lokalizacji, nie wprowadzaj niczego w tym polu. Domyślnie funkcja ClickOnce szuka aktualizacji w folderze, z którego użytkownicy instalują rozwiązanie.

6. Wybierz przycisk **Wymagania wstępne.**

7. W oknie dialogowym **Wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny do zainstalowania składników wymagań wstępnych.**

8. Na liście **Wybierz wymagania wstępne do zainstalowania** zaznacz pola wyboru dla **Instalatora Windows 4.5** i odpowiedniego pakietu .NET Framework.

    Jeśli na przykład rozwiązanie [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]jest przeznaczone dla , zaznacz pola wyboru dla **Instalatora Windows 4.5** i **Microsoft .NET Framework 4.5 Full**.

9. Jeśli rozwiązanie jest przeznaczone dla platformy .NET Framework 4.5, należy również zaznaczyć pole wyboru **Narzędzia programu Visual Studio 2010 dla środowiska wykonawczego pakietu Office.**

    > [!NOTE]
    > Domyślnie to pole wyboru nie jest wyświetlane. Aby było widoczne, należy utworzyć pakiet programu inicjującego. Zobacz [Tworzenie pakietu programu Bootstrapper dla dodatku VSTO pakietu Office 2013 w programie Visual Studio 2012.](create-vsto-add-ins-for-office-by-using-visual-studio.md)

10. W obszarze **Określanie lokalizacji instalacji dla wymagań wstępnych**wybierz jedną z wyświetlonych opcji, a następnie wybierz przycisk **OK.**

     W tabeli poniżej opisano wszystkie opcje.

    |Opcja|Opis|
    |------------|-----------------|
    |**Pobieranie wymagań wstępnych ze strony internetowej dostawcy komponentu**|Użytkownik jest monitowany o pobranie i zainstalowanie wstępnie wymaganych składników z witryny internetowej dostawcy.|
    |**Pobieranie wymagań wstępnych z tej samej lokalizacji co moja aplikacja**|Wstępnie wymagane oprogramowanie jest instalowane razem z oprogramowaniem. W przypadku zaznaczenia tej opcji program Visual Studio automatycznie kopiuje wszystkie wstępnie wymagane pakiety do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
    |**Pobieranie wymagań wstępnych z następującej lokalizacji**|Visual Studio kopiuje wszystkie wstępnie wymagane pakiety do wskazanej lokalizacji i instaluje je razem z rozwiązaniem.|

     Zobacz [Okno dialogowe Wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).

11. Wybierz przycisk **Aktualizacje,** określ, jak często chcesz, aby dodatek VSTO lub dostosowywanie każdego użytkownika końcowego sprawdzał dostępność aktualizacji, a następnie wybierz przycisk **OK.**

    > [!NOTE]
    > Jeśli wdrażasz przy użyciu dysku CD lub dysku wymiennego, wybierz przycisk **opcji Nigdy nie sprawdzaj dostępności aktualizacji.**

     Aby uzyskać informacje dotyczące publikowania aktualizacji, zobacz [Publikowanie aktualizacji](#Update).

12. Wybierz przycisk **Opcje,** przejrzyj opcje w oknie dialogowym **Opcje,** a następnie wybierz przycisk **OK.**

13. Wybierz przycisk **Publikuj teraz.**

     Program Visual Studio dodaje następujące foldery i pliki do folderu publikowania określonego wcześniej w tej procedurze.

    - Folder **Pliki aplikacji.**

    - Program instalacyjny.

    - Manifest wdrażania odwołujący się do manifestu wdrażania najnowszej wersji.

      Folder **Pliki aplikacji** zawiera podfolder dla każdej opublikowanej wersji. Każdy podfolder danej wersji zawiera następujące pliki.

    - Manifest aplikacji.

    - Manifest wdrażania.

    - Zestawy dostosowywania.

      Na poniższej ilustracji przedstawiono strukturę folderu publikowania dodatku VSTO programu Outlook.

      ![Publikowanie struktury folderów](../vsto/media/publishfolderstructure.png "Publikowanie struktury folderów")

    > [!NOTE]
    > ClickOnce dołącza *rozszerzenie .deploy* do zestawów, tak aby zabezpieczona instalacja internetowych usług informacyjnych (IIS) nie blokował plików z powodu niebezpiecznego rozszerzenia. Gdy użytkownik zainstaluje rozwiązanie, ClickOnce usuwa rozszerzenie *.deploy.*

14. Skopiuj pliki rozwiązania do lokalizacji instalacji określonej wcześniej w tej procedurze.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Zdecyduj, w jaki sposób chcesz udzielić zaufania do rozwiązania
 Zanim rozwiązanie będzie można uruchomić na komputerach użytkowników, administrator musi udzielić zaufania albo użytkownicy muszą odpowiedzieć na monit o udzielenie zaufania podczas instalacjo rozwiązania. Aby administrator przyznał zaufanie rozwiązaniu, musi podpisać manifest za pomocą certyfikatu identyfikującego znanego i zaufanego wydawcę. Zobacz [Ufanie rozwiązaniu, podpisując manifesty aplikacji i wdrażania](../vsto/granting-trust-to-office-solutions.md#Signing).

 Jeśli wdrażasz dostosowanie na poziomie dokumentu i chcesz umieścić dokument w folderze na komputerze użytkownika lub udostępnić go w witrynie programu SharePoint, upewnij się, że pakiet Office ufa lokalizacji dokumentu. Zobacz [Przyznawanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Pomóż użytkownikom zainstalować rozwiązanie
 Użytkownicy mogą zainstalować rozwiązanie, uruchamiając program instalacyjny, otwierając manifest wdrożenia lub podczas dostosowywania na poziomie dokumentu, otwierając dokument bezpośrednio. Według najlepszych praktyk rozwiązanie należy instalować przy użyciu programu instalacyjnego. Pozostałe dwa podejścia nie zapewniają, że oprogramowanie wymagania wstępne jest zainstalowany. Jeśli użytkownicy chcą otwierać dokument z lokalizacji instalacji, muszą ją dodać do listy zaufanych lokalizacji w Centrum zaufania w aplikacji pakietu Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Otwieranie dokumentu z dostosowaniem na poziomie dokumentu
 Użytkownicy mogą otwierać dokument zawierający dostosowanie na poziomie dokumentu bezpośrednio z lokalizacji instalacji albo przez skopiowanie go swoich lokalnych komputerów, a następnie otwarcie kopii.

 Według najlepszych praktyk należy otwierać kopię dokumentu na swoim komputerze, tak aby wiele osób nie próbowało otworzyć jednocześnie tego samego wystąpienia. W celu wymuszenia tej praktyki można tak skonfigurować program instalacyjny, aby kopiował dokument na komputery użytkowników. Zobacz [Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu).](#Put)

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Zainstaluj rozwiązanie, otwierając manifest wdrażania z witryny sieci Web usług IIS
 Użytkownicy mogą zainstalować rozwiązanie dla pakietu Office poprzez otwarcie manifestu wdrażania z Internetu. Jednak zabezpieczona instalacja internetowych usług informacyjnych (IIS) zablokuje pliki z rozszerzeniem *.vsto.* Zanim będzie można wdrożyć rozwiązanie za pomocą usług IIS, w usługach musi być zdefiniowany typ MIME.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Aby dodać typ MIME .vsto do usług IIS 6.0

1. Na serwerze z uruchomionymi usługami IIS 6.0 wybierz pozycję **Uruchom** > menedżera wszystkich narzędzi**administracyjnych narzędzi** >  **administracyjnych** > **(IIS).**

2. Wybierz nazwę komputera, **folderu Witryn sieci Web** lub skonfigurowany serwis sieci Web.

3. Na pasku menu wybierz pozycję**Właściwości** **akcji** > .

4. Na karcie **Nagłówki HTTP** wybierz przycisk **Typy MIME.**

5. W oknie **Typy MIME** wybierz przycisk **Nowy.**

6. W oknie **Typ MIME** wprowadź **.vsto** jako rozszerzenie, wprowadź **application/x-ms-vsto** jako typ MIME, a następnie zastosuj nowe ustawienia.

    > [!NOTE]
    > Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Następnie należy opróżnić pamięć podręczną dysku przeglądarki, a następnie ponownie otworzyć plik *vsto.*

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Aby dodać typ MIME vsto do usługi IIS 7.0

1. Na serwerze z uruchomionymi**usługami** > IIS 7.0 wybierz pozycję **Uruchom** > wszystkie**programy Akcesoria**.

2. Otwórz menu skrótów **wiersza polecenia,** a następnie wybierz pozycję **Uruchom jako administrator.**

3. W polu **Otwórz** wprowadź następującą ścieżkę, a następnie wybierz przycisk **OK.**

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Wprowadź następujące polecenie, a następnie zastosuj nowe ustawienia.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Następnie należy opróżnić pamięć podręczną dysku przeglądarki, a następnie ponownie otworzyć plik *vsto.*

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)
 Dokument rozwiązania można skopiować na komputer użytkownika końcowego, tworząc dla nich akcję po wdrożeniu. W ten sposób użytkownik nie musi ręcznie kopiować dokumentu z lokalizacji instalacji na komputer po zainstalowaniu rozwiązania. Należy utworzyć klasę, która definiuje akcję po wdrożeniu, skompilować i opublikować rozwiązanie, zmodyfikować manifest aplikacji i ponownie podpisać manifest aplikacji i wdrożenia.

 W poniższych procedurach przyjęto założenie, że nazwa projektu to **ExcelWorkbook** i że rozwiązanie zostanie opublikowane w utworzonym folderze o nazwie **C:\publish** na komputerze.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Tworzenie klasy definiującej akcję powdrożeniową

1. Na pasku menu wybierz pozycję **Dodaj plik** > **Add** > **nowego projektu**.

2. W oknie dialogowym **Dodawanie nowego projektu** w okienku Zainstalowane **szablony** wybierz folder **Windows.**

3. W okienku **Szablony** wybierz szablon **Biblioteka klas.**

4. W polu **Nazwa** wprowadź polecenie **FileCopyPDA**, a następnie wybierz przycisk **OK.**

5. W **Eksploratorze rozwiązań**wybierz projekt **FileCopyPDA.**

6. Na pasku menu wybierz pozycję **Project** > **Add Reference**.

7. Na karcie **.NET** dodaj odwołania `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument`do i .

8. Zmień nazwę klasy `FileCopyPDA`na , a następnie zastąp zawartość pliku kodem. Ten kod wykonuje następujące zadania:

   - Kopiowanie dokumentu do komputera użytkownika.

   - Zmienia właściwość _AssemblyLocation ze ścieżki względnej na w pełni kwalifikowaną ścieżkę dla manifestu wdrożenia.

   - Usunięcie pliku, jeśli użytkownik odinstaluje rozwiązanie.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Kompilowanie i publikowanie rozwiązania

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **FileCopyPDA,** a następnie wybierz polecenie **Buduj**.

2. Otwórz menu skrótów dla projektu **programu ExcelWorkbook,** a następnie wybierz polecenie **Buduj**.

3. Otwórz menu skrótów dla projektu **programu ExcelWorkbook,** a następnie wybierz pozycję **Dodaj odwołanie**.

4. W oknie dialogowym **Dodawanie odwołania** wybierz kartę **Projekty,** wybierz polecenie **FileCopyPDA**, a następnie wybierz przycisk **OK.**

5. W **Eksploratorze rozwiązań**wybierz projekt **programu ExcelWorkbook.**

6. Na pasku menu wybierz pozycję **Project** > **New Folder**.

7. Wprowadź **dane**, a następnie wybierz klawisz **Enter.**

8. W **Eksploratorze rozwiązań**wybierz folder **Dane.**

9. Na pasku menu wybierz pozycję **Project** > **Add Existing Item**.

10. W oknie dialogowym **Dodawanie istniejącego elementu** przejdź do katalogu wyjściowego projektu **programu ExcelWorkbook,** wybierz plik **ExcelWorkbook.xlsx,** a następnie wybierz przycisk **Dodaj.**

11. W **Eksploratorze rozwiązań** wybierz plik **ExcelWorkbook.xlsx.**

12. W oknie Właściwości zmień właściwość **Akcja kompilacji** na **Zawartość** i właściwość **Kopiuj na Katalog wyjściowy** na **Kopiuj, jeśli nowsza**. **Properties**

     Po wykonaniu tych kroków projekt będzie podobny do poniższej ilustracji.

     ![Struktura projektu akcji po wdrożeniu.](../vsto/media/vsto-postdeployment.png "Struktura projektu akcji po wdrożeniu.")

13. Opublikuj projekt **programu ExcelWorkbook.**

### <a name="modify-the-application-manifest"></a>Modyfikowanie manifestu aplikacji

1. Otwórz katalog rozwiązań **c:\publish**, używając **Eksploratora plików**.

2. Otwórz folder **Pliki aplikacji,** a następnie otwórz folder odpowiadający najnowszej opublikowanej wersji rozwiązania.

3. Otwórz plik **ExcelWorkbook.dll.manifest** w edytorze tekstu, takim jak Notatnik.

4. Po `</vstav3:update>` elemencie dodaj następujący kod. Dla atrybutu klasy `<vstav3:entryPoint>` elementu należy użyć następującej składni: *NamespaceName.ClassName*. W poniższym przykładzie nazwy obszaru nazw i klas są takie same, więc wynikowa nazwa punktu wejścia to `FileCopyPDA.FileCopyPDA`.

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

1. W folderze **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** skopiuj plik certyfikatu **ExcelWorkbook_TemporaryKey.pfx,** a następnie wklej go do *folderu PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ folder.

2. Otwórz wiersz polecenia programu Visual Studio, a następnie zmień katalogi na folder **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ (na przykład **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3. Podpisz zmodyfikowany manifest aplikacji, wykonując następujące polecenie:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.manifest został pomyślnie podpisany”.

4. Zmień folder **c:\publish,** a następnie zaktualizuj i podpisz manifest wdrożenia, uruchamiając następujące polecenie:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > W poprzednim przykładzie zastąp MostRecentVersionNumber numerem wersji ostatnio opublikowanej wersji rozwiązania (na przykład **1_0_0_4**).

     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.vsto został pomyślnie podpisany”.

5. Skopiuj plik *ExcelWorkbook.vsto* do katalogu **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber._

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Umieszczanie dokumentu rozwiązania na serwerze z uruchomionym programem SharePoint (tylko dostosowania na poziomie dokumentu)
 Dostosowanie na poziomie dokumentu można opublikować użytkownikom końcowym za pomocą programu SharePoint. Gdy użytkownicy przejdą do witryny programu SharePoint i otworzą dokument, środowisko uruchomieniowe automatycznie zainstaluje rozwiązanie z udostępnionego folderu sieciowego na komputerze lokalnym. Po lokalnym zainstalowaniu rozwiązania dostosowanie nadal będzie działać, nawet, jeśli dokument skopiowano w inne miejsce, na przykład na pulpit.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Aby umieścić dokument na serwerze z programem SharePoint

1. Dodaj dokument z rozwiązania do biblioteki dokumentów w witrynie programu SharePoint.

2. Wykonaj czynności dla jednej z poniższych metod:

    - Za pomocą narzędzia konfiguracji pakietu Office dodaj serwer z programem do Centrum zaufania w programie Word lub Excel na komputerach wszystkich użytkowników.

         Zobacz [Zasady i ustawienia zabezpieczeń w pakiecie Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Upewnij się, że każdy użytkownik wykona następujące czynności.

        1. Na komputerze lokalnym otwórz program Word lub Excel, wybierz kartę **Plik,** a następnie wybierz przycisk **Opcje.**

        2. W oknie dialogowym **Centrum zaufania** wybierz przycisk **Zaufane lokalizacje.**

        3. Zaznacz pole wyboru **Zezwalaj na zaufane lokalizacje w mojej sieci (nie zalecane),** a następnie wybierz przycisk **Dodaj nową lokalizację.**

        4. W polu **Ścieżka** wprowadź adres URL biblioteki dokumentów programu SharePoint zawierającej przekazany *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*dokument (na przykład ).

             Nie dodawaj nazwy domyślnej strony sieci Web, takiej jak *default.aspx* lub *AllItems.aspx*.

        5. Zaznacz pole wyboru **Podfoldery tej lokalizacji są również zaufane,** a następnie wybierz przycisk **OK.**

             Gdy użytkownicy otwierają dokument z poziomu witryny programu SharePoint, następuje otwarcie dokumentu i zainstalowanie dostosowania. Użytkownicy mogą wtedy skopiować dokument na swoje komputery. Dostosowanie będzie nadal działać, ponieważ właściwości w dokumencie wskazują jego lokalizację sieciową.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Tworzenie instalatora niestandardowego
 Można utworzyć niestandardowy instalator dla rozwiązania pakietu Office, zamiast używać programu instalacyjnego, który jest tworzony dla Ciebie podczas publikowania rozwiązania. Na przykład można użyć skryptu logowania, aby rozpocząć instalację, lub można użyć pliku wsadowego, aby zainstalować rozwiązanie bez interakcji z użytkownikiem. Scenariusze te działają najlepiej, jeśli na komputerach użytkowników końcowych są już zainstalowane wstępnie wymagane składniki.

 W ramach niestandardowego procesu instalacji należy wywołać narzędzie instalatora rozwiązań pakietu Office *(VSTOInstaller.exe),* które jest domyślnie instalowane w następującej lokalizacji:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Jeśli narzędzia nie ma w tej lokalizacji, można użyć klucza rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** lub **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath,** aby znaleźć ścieżkę do tego narzędzia.

 W pliku *VSTOinstaller.exe*można użyć następujących parametrów.

| Parametr | Definicja |
|------------------| - |
| /Install lub /I | Instalowanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Można określić ścieżkę na komputerze lokalnym, udział plików konwencji nazewnictwa uniwersalnego (UNC). Można określić ścieżkę lokalną (*C:\FolderName\PublishFolder*), ścieżkę względną (*Publikuj\\*) lub w pełni kwalifikowaną lokalizację (*\\\ServerName\FolderName* lub http://<em>ServerName/FolderName</em>). |
| /Uninstall lub /U | Odinstalowywanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Można określić, że ścieżka może znajdować się na komputerze lokalnym, udział plików UNC. Można określić ścieżkę lokalną (*c:\FolderName\PublishFolder*), ścieżkę względną (*Publikuj\\*) lub w pełni kwalifikowaną lokalizację (*\\\ServerName\FolderName* lub http://<em>ServerName/FolderName</em>). |
| /Silent lub /S | Instalowanie lub odinstalowywanie bez monitowania użytkownika o wprowadzenie danych ani wyświetlania jakichkolwiek komunikatów. Jeśli wymagany jest monit o zaufanie, dostosowanie nie jest zainstalowane ani zaktualizowane. |
| /Help lub /? | Wyświetlanie informacji Pomocy. |

 Po uruchomieniu *pliku VSTOinstaller.exe*mogą pojawić się następujące kody błędów.

|Kod błędu|Definicja|
|----------------|----------------|
|0|Rozwiązanie zostało pomyślnie zainstalowane lub odinstalowane albo została wyświetlona Pomoc narzędzia VSTOInstaller.|
|-100|Co najmniej jedna opcja wiersza polecenia jest nieprawidłowa lub została ustawiona więcej niż raz. Aby uzyskać więcej informacji, wpisz "vstoinstaller /?" lub zobacz [Tworzenie niestandardowego instalatora dla rozwiązania ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Co najmniej jedna opcja wiersza polecenia jest nieprawidłowa. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|
|-200|Identyfikator URI manifestu wdrożenia jest nieprawidłowy. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|
|-201|Nie można zainstalować rozwiązania, ponieważ manifest wdrażania jest nieprawidłowy. Zobacz [Manifesty wdrażania rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Nie można zainstalować rozwiązania, ponieważ sekcja Narzędzia programu Visual Studio dla pakietu Office manifestu aplikacji jest nieprawidłowa. Zobacz [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Nie można zainstalować rozwiązania, ponieważ wystąpił błąd pobierania. Sprawdź identyfikator URI lub lokalizację pliku sieciowego manifestu wdrażania, a następnie ponów próbę.|
|-300|Nie można zainstalować rozwiązania, ponieważ wystąpił wyjątek zabezpieczeń. Zobacz [rozwiązania Secure Office](../vsto/securing-office-solutions.md).|
|-400|Nie można zainstalować rozwiązania.|
|-401|Nie można odinstalować rozwiązania.|
|-500|Operacja została anulowana, ponieważ nie można zainstalować lub odinstalować rozwiązania albo nie można pobrać manifestu wdrażania.|

## <a name="publish-an-update"></a><a name="Update"></a>Publikowanie aktualizacji
 Aby zaktualizować rozwiązanie, należy opublikować go ponownie za pomocą **Projektanta projektu** lub **Kreatora publikowania**, a następnie skopiować zaktualizowane rozwiązanie do lokalizacji instalacji. Podczas kopiowania plików do lokalizacji instalacji trzeba koniecznie zaznaczyć opcję zastąpienia poprzednich plików.

 Następnym razem, gdy rozwiązanie sprawdza dostępność aktualizacji, zostanie automatycznie odnajdywane i ładowane przez nową wersję.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Zmienianie lokalizacji instalacji rozwiązania
 Po opublikowaniu rozwiązania można dodać lub zmienić ścieżkę instalacji. Często powody takiej zmiany są następujące:

- Program instalacyjny został skompilowany przed ustaleniem ścieżki instalacji.

- Pliki rozwiązania skopiowano do innej lokalizacji.

- Serwer, na którym znajdują się pliki instalacyjne, ma nową nazwę lub lokalizację.

  Aby zmienić ścieżkę instalacji rozwiązania, należy zaktualizować program instalacyjny, po czym użytkownicy muszą go uruchomić. W przypadku dostosowań na poziomie dokumentu użytkownicy muszą również w swoich dokumentach tak zaktualizować odnośną właściwość, aby wskazywała nową lokalizację.

> [!NOTE]
> Jeśli nie chcesz prosić użytkowników o zaktualizowanie ich właściwości dokumentu, możesz poprosić użytkowników o uzyskanie zaktualizowanego dokumentu z lokalizacji instalacji.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Aby zmienić ścieżkę instalacji w programie instalacyjnym

1. Otwórz okno **wiersza polecenia,** a następnie zmień katalogi na folder instalacyjny.

2. Uruchom program instalacyjny `/url` i dołącz parametr, który przyjmuje nową ścieżkę instalacji jako ciąg.

    Poniższy przykład pokazuje, jak zmienić ścieżkę instalacji na lokalizację w witrynie internetowej firmy Fabrikam; widoczny adres URL można zastąpić dowolną inną ścieżką:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Jeśli pojawi się komunikat z informacją, że podpis pliku wykonywalnego zostanie unieważniony, certyfikat użyty do podpisania rozwiązania jest nieważny, a wydawca nieznany. W rezultacie przed zainstalowaniem rozwiązania użytkownicy będą musieli potwierdzić, że ufają jego źródłu.

   > [!NOTE]
   > Aby wyświetlić bieżącą wartość `setup.exe /url`adresu URL, uruchom program .

   W przypadku dostosowań na poziomie dokumentu użytkownicy muszą otworzyć dokument, a następnie zaktualizować jego _AssemblyLocation właściwości. Poniżej zamieszczono odpowiednią procedurę.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Aby zaktualizować właściwość _AssemblyLocation w dokumencie

1. Na karcie **Plik** wybierz pozycję **Informacje**, na którym pokazano poniższą ilustrację.

     ![Karta Informacje w programie Excel](../vsto/media/vsto-infotab.png "Karta Informacje w programie Excel")

2. Na liście **Właściwości** wybierz pozycję **Właściwości zaawansowane**, na którym pokazano poniższą ilustrację.

     ![Właściwości zaawansowane w programie Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Właściwości zaawansowane w programie Excel.")

3. Na karcie **Niestandardowe** na liście **Właściwości** wybierz pozycję _AssemblyLocation, jak pokazano na poniższej ilustracji.

     ![Właściwość AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Właściwość AssemblyLocation.")

     Pole **Wartość** zawiera identyfikator manifestu wdrożenia.

4. Przed identyfikatorem wprowadź w pełni kwalifikowaną ścieżkę dokumentu, a następnie pasek w formacie*Identyfikator* *ścieżki*|(na przykład *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Aby uzyskać więcej informacji na temat formatowania tego [identyfikatora, zobacz Omówienie właściwości dokumentu niestandardowego](../vsto/custom-document-properties-overview.md).

5. Wybierz przycisk **OK,** a następnie zapisz i zamknij dokument.

6. Uruchom program instalacyjny bez parametru /url. Rozwiązanie zostanie zainstalowane w podanej lokalizacji.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Wycofywanie rozwiązania do wcześniejszej wersji
 Wycofanie rozwiązania powoduje, że użytkownicy wrócą do korzystania z jego starszej wersji.

#### <a name="to-roll-back-a-solution"></a>Aby wycofać rozwiązanie

1. Otwórz lokalizację instalacji rozwiązania.

2. W folderze publikowania najwyższego poziomu usuń manifest wdrożenia (plik *vsto).*

3. Znajdź podfolder wersji, do której chcesz wycofać rozwiązanie.

4. Skopiuj manifest wdrażania z tego podfolderu do folderu publikowania najwyższego poziomu.

     Na przykład, aby wycofać rozwiązanie o nazwie **OutlookAddIn1** z wersji 1.0.0.1 do wersji 1.0.0.0, skopiuj plik **OutlookAddIn1.vsto** z folderu **OutlookAddIn1_1_0_0_0.** Wklej plik do folderu publikowania najwyższego poziomu, zastępując manifest wdrożenia specyficzne dla wersji dla **OutlookAddIn1_1_0_0_1,** który już tam był.

     Na ilustracji poniżej widać strukturę folderu publikowania w opisywanym przykładzie.

     ![Publikowanie struktury folderów](../vsto/media/publishfolderstructure.png "Publikowanie struktury folderów")

     Gdy użytkownik następnym razem otworzy aplikację lub dostosowany dokument, zostanie wykryta zmiana manifestu wdrażania. Starsza wersja rozwiązania dla pakietu Office jest uruchamiana z pamięci podręcznej funkcji ClickOnce.

> [!NOTE]
> Dane lokalne są zapisywane tylko dla jednej poprzedniej wersji rozwiązania. Jeśli wycofasz dwie wersje, dane lokalne nie są zachowywane. Aby uzyskać więcej informacji na temat danych lokalnych, zobacz [Dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Zobacz też

- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Publikowanie rozwiązań pakietu Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Jak: Publikowanie rozwiązania pakietu Office przy użyciu clickonce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Jak: Zainstaluj rozwiązanie ClickOnce Office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Jak: Publikowanie rozwiązania pakietu Office na poziomie dokumentu na serwerze programu SharePoint przy użyciu funkcji ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Tworzenie niestandardowego instalatora dla rozwiązania biurowego ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)