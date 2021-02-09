---
title: Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce
description: Jeśli używasz technologii ClickOnce, Dowiedz się, jak wdrożyć rozwiązanie pakietu Office w mniejszej liczbie kroków. Podczas publikowania aktualizacji rozwiązanie automatycznie je wykryje i zainstaluje.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da527da4504d4c2d9375aee0209b0e261fe5fd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877937"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce
  Jeśli używasz technologii ClickOnce, możesz wdrożyć rozwiązanie pakietu Office w mniejszej liczbie kroków. Podczas publikowania aktualizacji rozwiązanie automatycznie je wykryje i zainstaluje. Niedogodność polega na tym, że w technologii ClickOnce rozwiązanie trzeba zainstalować osobno dla każdego użytkownika komputera. W związku z tym należy rozważyć użycie Instalator Windows (*. msi*), jeśli na tym samym komputerze zostanie uruchomione rozwiązanie na jednym z nich.

## <a name="in-this-topic"></a>W tym temacie:

- [Publikowanie rozwiązania](#Publish)

- [Zdecyduj, w jaki sposób chcesz udzielić zaufania do rozwiązania](#Trust)

- [Pomóż użytkownikom zainstalować rozwiązanie](#Helping)

- [Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)](#Put)

- [Umieszczanie dokumentu rozwiązania na serwerze, na którym jest uruchomiony program SharePoint (tylko dostosowania na poziomie dokumentu)](#SharePoint)

- [Tworzenie niestandardowego instalatora](#Custom)

- [Publikowanie aktualizacji](#Update)

- [Zmiana lokalizacji instalacji rozwiązania](#Location)

- [Wycofywanie rozwiązania do wcześniejszej wersji](#Roll)

  Aby uzyskać więcej informacji na temat wdrażania rozwiązania pakietu Office przez utworzenie pliku Instalator Windows, zobacz [wdrażanie rozwiązania biurowego przy użyciu Instalator Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a> Publikowanie rozwiązania
 Rozwiązanie można opublikować za pomocą **Kreatora publikacji** lub **projektanta projektu**. W ramach tej procedury będziesz używać **projektanta projektu** , ponieważ zawiera kompletny zestaw opcji publikacji. Zobacz [Kreator publikacji &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Aby opublikować rozwiązanie

1. W **Eksplorator rozwiązań** wybierz węzeł, który jest nazwany dla projektu.

2. Na pasku menu wybierz **projekt**, **Właściwości** *ProjectName* .

3. W **projektancie projektu** wybierz kartę **Publikowanie** , która przedstawia poniższą ilustrację.

    ![Karta publikowanie projektanta projektu](../vsto/media/vsto-publishtab.png "Karta publikowanie projektanta projektu")

4. W polu **Lokalizacja folderu publikowania (serwer FTP lub ścieżka pliku)** wprowadź ścieżkę do folderu, w którym **Projektant projektu** ma kopiować pliki rozwiązania.

    Możesz użyć dowolnego z następujących typów ścieżek.

   - Ścieżka lokalna (na przykład *C:\FolderName\FolderName*).

   - Ścieżka UNC (Uniform Naming Convention) do folderu w sieci (na przykład *\\ \ServerName\FolderName*).

   - Ścieżka względna (na przykład *PublishFolder \\*, która jest folderem, w którym projekt jest domyślnie publikowany).

5. W polu **adres URL folderu instalacyjnego** wprowadź w pełni kwalifikowaną ścieżkę lokalizacji, w której użytkownicy końcowi znajdą Twoje rozwiązanie.

    Jeśli nie znasz jeszcze lokalizacji, nie wprowadzaj niczego w tym polu. Domyślnie funkcja ClickOnce szuka aktualizacji w folderze, z którego użytkownicy instalują rozwiązanie.

6. Wybierz przycisk **wymagania wstępne** .

7. W oknie dialogowym **wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** .

8. Na liście **Wybierz wstępnie wymagane składniki do zainstalowania** zaznacz pola wyboru dla **Instalator Windows 4,5** i odpowiedni pakiet .NET Framework.

    Na przykład, jeśli rozwiązanie jest przeznaczone dla [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , zaznacz pola wyboru dla **Instalator Windows 4,5** i **Microsoft .NET Framework 4,5 pełne**.

9. Jeśli rozwiązanie jest przeznaczone dla .NET Framework 4,5, zaznacz również pole wyboru **Visual Studio 2010 Tools for Office Runtime** .

    > [!NOTE]
    > Domyślnie to pole wyboru nie jest wyświetlane. Aby było widoczne, należy utworzyć pakiet programu inicjującego. Zobacz [Tworzenie pakietu programu inicjującego dla dodatku VSTO dla pakietu Office 2013 przy użyciu programu Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. W obszarze **Określ lokalizację instalacji dla wymagań wstępnych** wybierz jedną z opcji, która zostanie wyświetlona, a następnie wybierz przycisk **OK** .

     W tabeli poniżej opisano wszystkie opcje.

    |Opcja|Opis|
    |------------|-----------------|
    |**Pobierz wstępnie wymagane składniki z witryny sieci Web dostawcy składników**|Użytkownik jest monitowany o pobranie i zainstalowanie wstępnie wymaganych składników z witryny internetowej dostawcy.|
    |**Pobierz wstępnie wymagane składniki z tej samej lokalizacji co moja aplikacja**|Wstępnie wymagane oprogramowanie jest instalowane razem z oprogramowaniem. W przypadku zaznaczenia tej opcji program Visual Studio automatycznie kopiuje wszystkie wstępnie wymagane pakiety do lokalizacji publikowania. Aby opcja działała, składniki muszą się znajdować na komputerze deweloperskim.|
    |**Pobierz wstępnie wymagane składniki z następującej lokalizacji**|Visual Studio kopiuje wszystkie wstępnie wymagane pakiety do wskazanej lokalizacji i instaluje je razem z rozwiązaniem.|

     Zobacz [okno dialogowe wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).

11. Wybierz przycisk **aktualizacje** , określ, jak często mają być sprawdzane w celu sprawdzenia dostępności aktualizacji przez poszczególnych użytkowników końcowych, a następnie wybierz przycisk **OK** .

    > [!NOTE]
    > Jeśli wdrażasz program przy użyciu dysku CD lub dysku wymiennego, wybierz przycisk opcji **nigdy nie sprawdzaj, czy** są dostępne aktualizacje.

     Informacje o sposobach publikowania aktualizacji znajdują się w temacie [publikowanie aktualizacji](#Update).

12. Wybierz przycisk **Opcje** , zapoznaj się z opcjami w oknie dialogowym **Opcje** , a następnie wybierz przycisk **OK** .

13. Wybierz przycisk **Publikuj teraz** .

     Program Visual Studio dodaje następujące foldery i pliki do folderu publikowania określonego wcześniej w tej procedurze.

    - Folder **plików aplikacji** .

    - Program instalacyjny.

    - Manifest wdrażania odwołujący się do manifestu wdrażania najnowszej wersji.

      Folder **pliki aplikacji** zawiera podfolder dla każdej publikowanej wersji. Każdy podfolder danej wersji zawiera następujące pliki.

    - Manifest aplikacji.

    - Manifest wdrażania.

    - Zestawy dostosowywania.

      Na poniższej ilustracji przedstawiono strukturę folderu publikowania dla dodatku narzędzi VSTO dla programu Outlook.

      ![Struktura folderu publikowania](../vsto/media/publishfolderstructure.png "Struktura folderu publikowania")

    > [!NOTE]
    > Technologia ClickOnce dołącza rozszerzenie *. deploy* do zestawów, aby zabezpieczona instalacja programu Internet Information Services (IIS) nie blokowała plików z powodu niebezpiecznego rozszerzenia. Gdy użytkownik zainstaluje rozwiązanie, ClickOnce usunie rozszerzenie *. deploy* .

14. Skopiuj pliki rozwiązania do lokalizacji instalacji określonej wcześniej w tej procedurze.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> Zdecyduj, w jaki sposób chcesz udzielić zaufania do rozwiązania
 Zanim rozwiązanie będzie można uruchomić na komputerach użytkowników, administrator musi udzielić zaufania albo użytkownicy muszą odpowiedzieć na monit o udzielenie zaufania podczas instalacjo rozwiązania. Aby administrator przyznał zaufanie rozwiązaniu, musi podpisać manifest za pomocą certyfikatu identyfikującego znanego i zaufanego wydawcę. Zobacz temat [zaufanie do rozwiązania, podpisywanie manifestów aplikacji i wdrażania](../vsto/granting-trust-to-office-solutions.md#Signing).

 Jeśli wdrażasz dostosowanie na poziomie dokumentu i chcesz umieścić dokument w folderze na komputerze użytkownika lub udostępnić go w witrynie programu SharePoint, upewnij się, że urząd ufa lokalizacji dokumentu. Zobacz [udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> Pomóż użytkownikom zainstalować rozwiązanie
 Użytkownicy mogą zainstalować rozwiązanie, uruchamiając program instalacyjny, otwierając manifest wdrożenia lub podczas dostosowywania na poziomie dokumentu, otwierając dokument bezpośrednio. Według najlepszych praktyk rozwiązanie należy instalować przy użyciu programu instalacyjnego. Pozostałe dwa podejścia nie zapewniają, że wstępnie wymagane oprogramowanie jest zainstalowane. Jeśli użytkownicy chcą otwierać dokument z lokalizacji instalacji, muszą ją dodać do listy zaufanych lokalizacji w Centrum zaufania w aplikacji pakietu Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Otwieranie dokumentu z dostosowaniem na poziomie dokumentu
 Użytkownicy mogą otwierać dokument zawierający dostosowanie na poziomie dokumentu bezpośrednio z lokalizacji instalacji albo przez skopiowanie go swoich lokalnych komputerów, a następnie otwarcie kopii.

 Według najlepszych praktyk należy otwierać kopię dokumentu na swoim komputerze, tak aby wiele osób nie próbowało otworzyć jednocześnie tego samego wystąpienia. W celu wymuszenia tej praktyki można tak skonfigurować program instalacyjny, aby kopiował dokument na komputery użytkowników. Zobacz [Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Zainstaluj rozwiązanie, otwierając manifest wdrożenia z witryny sieci Web usług IIS
 Użytkownicy mogą zainstalować rozwiązanie dla pakietu Office poprzez otwarcie manifestu wdrażania z Internetu. Jednak zabezpieczona instalacja programu Internet Information Services (IIS) będzie blokować pliki, które mają rozszerzenie *. VSTO* . Zanim będzie można wdrożyć rozwiązanie za pomocą usług IIS, w usługach musi być zdefiniowany typ MIME.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Aby dodać typ MIME .vsto do usług IIS 6.0

1. Na serwerze, na którym działa program IIS 6,0, wybierz kolejno opcje **Start**  >  **Wszystkie programy**  >  **Narzędzia administracyjne**  >   **Internet Information Services (IIS) Menedżer**.

2. Wybierz nazwę komputera, folder **witryny sieci Web** lub witrynę sieci Web, którą konfigurujesz.

3. Na pasku menu wybierz polecenie właściwości **akcji**  >  .

4. Na karcie **nagłówki HTTP** wybierz przycisk **typy MIME** .

5. W oknie **typy MIME** wybierz przycisk **Nowy** .

6. W oknie **Typ MIME** wprowadź **. VSTO** jako rozszerzenie, wprowadź wartość **Application/x-MS-VSTO** jako typ MIME, a następnie Zastosuj nowe ustawienia.

    > [!NOTE]
    > Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Należy następnie opróżnić pamięć podręczną dysku przeglądarki, a następnie spróbować ponownie otworzyć plik *. VSTO* .

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Aby dodać typ MIME. VSTO do usług IIS 7,0

1. Na serwerze, na którym działa program IIS 7,0, wybierz kolejno pozycje **Uruchom**  >  **Wszystkie programy**  >  **akcesoria**.

2. Otwórz menu skrótów dla **wiersza polecenia**, a następnie wybierz  **Uruchom jako administrator.**

3. W polu **Otwórz** Wprowadź następującą ścieżkę, a następnie wybierz przycisk **OK** .

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Wprowadź następujące polecenie, a następnie zastosuj nowe ustawienia.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Aby zmiany zaczęły obowiązywać, należy ponownie uruchomić usługę publikowania w sieci World Wide Web lub poczekać na wykonanie cyklu odświeżania w procesie roboczym. Należy następnie opróżnić pamięć podręczną dysku przeglądarki, a następnie spróbować ponownie otworzyć plik *. VSTO* .

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> Umieszczanie dokumentu rozwiązania na komputerze użytkownika końcowego (tylko dostosowania na poziomie dokumentu)
 Możesz skopiować dokument rozwiązania na komputer użytkownika końcowego, tworząc akcję po wdrożeniu. Dzięki temu użytkownik nie musi ręcznie kopiować dokumentu z lokalizacji instalacji na komputer po zainstalowaniu rozwiązania. Należy utworzyć klasę, która definiuje akcję powdrożeniową, skompilować i opublikować rozwiązanie, zmodyfikować manifest aplikacji i ponownie podpisać aplikację i manifest wdrożenia.

 W poniższych procedurach przyjęto założenie, że nazwa projektu to **ExcelWorkbook** i opublikowanie rozwiązania w utworzonym folderze o nazwie **C:\Publish** na komputerze.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Tworzenie klasy definiującej akcję powdrożeniową

1. Na pasku menu wybierz polecenie **plik**  >  **Dodaj**  >  **Nowy projekt**.

2. W oknie dialogowym **Dodaj nowy projekt** w okienku **zainstalowane szablony** wybierz folder **Windows** .

3. W okienku **Szablony** wybierz szablon **Biblioteka klas** .

4. W polu **Nazwa** wprowadź **FileCopyPDA**, a następnie wybierz przycisk **OK** .

5. W **Eksplorator rozwiązań** wybierz projekt **FileCopyPDA** .

6. Na pasku menu wybierz kolejno pozycje **projekt**  >  **Dodaj odwołanie**.

7. Na karcie **.NET** Dodaj odwołania do `Microsoft.VisualStudio.Tools.Applications.Runtime` i `Microsoft.VisualStudio.Tools.Applications.ServerDocument` .

8. Zmień nazwę klasy na `FileCopyPDA` , a następnie zastąp zawartość pliku kodem. Ten kod wykonuje następujące zadania:

   - Kopiowanie dokumentu do komputera użytkownika.

   - Zmienia właściwość _AssemblyLocation ze ścieżki względnej do w pełni kwalifikowanej ścieżki manifestu wdrożenia.

   - Usunięcie pliku, jeśli użytkownik odinstaluje rozwiązanie.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Kompilowanie i publikowanie rozwiązania

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **FileCopyPDA** , a następnie wybierz polecenie **Kompiluj**.

2. Otwórz menu skrótów dla projektu **ExcelWorkbook** , a następnie wybierz polecenie **Kompiluj**.

3. Otwórz menu skrótów dla projektu **ExcelWorkbook** , a następnie wybierz **Dodaj odwołanie**.

4. W oknie dialogowym **Dodaj odwołanie** wybierz kartę **projekty** , wybierz pozycję **FileCopyPDA**, a następnie wybierz przycisk **OK** .

5. W **Eksplorator rozwiązań** wybierz projekt **ExcelWorkbook** .

6. Na pasku menu wybierz **projekt**  >  **Nowy folder**.

7. Wprowadź **dane**, a następnie wybierz klawisz **Enter** .

8. W **Eksplorator rozwiązań** wybierz folder **dane** .

9. Na pasku menu wybierz **projekt**  >  **Dodaj istniejący element**.

10. W oknie dialogowym **Dodaj istniejący element** przejdź do katalogu wyjściowego dla projektu **ExcelWorkbook** , wybierz plik **ExcelWorkbook.xlsx** , a następnie wybierz przycisk **Dodaj** .

11. W **Eksplorator rozwiązań** wybierz plik **ExcelWorkbook.xlsx** .

12. W oknie **Właściwości** Zmień właściwość **Akcja kompilacji** na **zawartość** i Właściwość **Kopiuj do katalogu wyjściowego** na wartość **Kopiuj, jeśli nowszy**.

     Po wykonaniu tych kroków projekt będzie wyglądać podobnie do poniższej ilustracji.

     ![Struktura projektu akcji po wdrożeniu.](../vsto/media/vsto-postdeployment.png "Struktura projektu akcji po wdrożeniu.")

13. Opublikuj projekt **ExcelWorkbook** .

### <a name="modify-the-application-manifest"></a>Modyfikowanie manifestu aplikacji

1. Otwórz katalog rozwiązania, **c:\Publish**, za pomocą **Eksploratora plików**.

2. Otwórz folder **pliki aplikacji** , a następnie otwórz folder, który odpowiada najnowszej opublikowanej wersji rozwiązania.

3. Otwórz plik **ExcelWorkbook.dll. manifest** w edytorze tekstu, takim jak Notatnik.

4. Po `</vstav3:update>` elemencie Dodaj następujący kod. Dla atrybutu klasy `<vstav3:entryPoint>` elementu należy użyć następującej składni: *NamespaceName. ClassName*. W poniższym przykładzie nazwy przestrzeni nazw i klas są takie same, więc nazwa punktu wejścia jest taka sama `FileCopyPDA.FileCopyPDA` .

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

1. W folderze **%USERPROFILE%\Documents\Visual Studio 2013 \ Projects\ExcelWorkbook\ExcelWorkbook** Skopiuj plik certyfikatu **ExcelWorkbook_TemporaryKey. pfx** , a następnie wklej go do folderu *PublishFolder* **\Dane Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ .

2. Otwórz wiersz polecenia programu Visual Studio, a następnie zmień katalogi na folder **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ (na przykład **c:\publish\Application Files \ ExcelWorkbook_1_0_0_4**).

3. Podpisz zmodyfikowany manifest aplikacji, wykonując następujące polecenie:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.manifest został pomyślnie podpisany”.

4. Przejdź do folderu **c:\Publish** , a następnie zaktualizuj i podpisz manifest wdrożenia, uruchamiając następujące polecenie:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > W poprzednim przykładzie Zastąp MostRecentVersionNumber numerem wersji ostatnio opublikowanej wersji rozwiązania (na przykład **1_0_0_4**).

     Zostanie wyświetlony komunikat „Plik ExcelWorkbook.dll.vsto został pomyślnie podpisany”.

5. Skopiuj plik *ExcelWorkbook. VSTO* do katalogu **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentVersionNumber_ .

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a> Umieszczanie dokumentu rozwiązania na serwerze, na którym jest uruchomiony program SharePoint (tylko dostosowania na poziomie dokumentu)
 Dostosowanie na poziomie dokumentu można opublikować użytkownikom końcowym za pomocą programu SharePoint. Gdy użytkownicy przejdą do witryny programu SharePoint i otworzą dokument, środowisko uruchomieniowe automatycznie zainstaluje rozwiązanie z udostępnionego folderu sieciowego na komputerze lokalnym. Po lokalnym zainstalowaniu rozwiązania dostosowanie nadal będzie działać, nawet, jeśli dokument skopiowano w inne miejsce, na przykład na pulpit.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Aby umieścić dokument na serwerze z programem SharePoint

1. Dodaj dokument z rozwiązania do biblioteki dokumentów w witrynie programu SharePoint.

2. Wykonaj czynności dla jednej z poniższych metod:

    - Za pomocą narzędzia konfiguracji pakietu Office dodaj serwer z programem do Centrum zaufania w programie Word lub Excel na komputerach wszystkich użytkowników.

         Zobacz [zasady i ustawienia zabezpieczeń w pakiecie Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Upewnij się, że każdy użytkownik wykona następujące czynności.

        1. Na komputerze lokalnym Otwórz program Word lub Excel, wybierz kartę **plik** , a następnie wybierz przycisk **Opcje** .

        2. W oknie dialogowym **Centrum zaufania** wybierz przycisk **Zaufane lokalizacje** .

        3. Zaznacz pole wyboru **Zezwalaj na Zaufane lokalizacje w mojej sieci (niezalecane)** , a następnie wybierz przycisk **Dodaj nową lokalizację** .

        4. W polu **ścieżka** wprowadź adres URL biblioteki dokumentów programu SharePoint zawierającej przekazany dokument (na przykład *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName* ).

             Nie dodawaj nazwy domyślnej strony sieci Web, takiej jak *default. aspx* lub *AllItems. aspx*.

        5. Zaznacz pola wyboru **podfoldery tej lokalizacji również są zaufane** , a następnie wybierz przycisk **OK** .

             Gdy użytkownicy otwierają dokument z poziomu witryny programu SharePoint, następuje otwarcie dokumentu i zainstalowanie dostosowania. Użytkownicy mogą wtedy skopiować dokument na swoje komputery. Dostosowanie będzie nadal działać, ponieważ właściwości w dokumencie wskazują jego lokalizację sieciową.

## <a name="create-a-custom-installer"></a><a name="Custom"></a> Tworzenie niestandardowego Instalatora
 Możesz utworzyć niestandardowy Instalator dla rozwiązania pakietu Office, zamiast korzystać z programu instalacyjnego, który został utworzony podczas publikowania rozwiązania. Na przykład możesz użyć skryptu logowania do uruchomienia instalacji lub użyć pliku wsadowego, aby zainstalować rozwiązanie bez interakcji z użytkownikiem. Scenariusze te działają najlepiej, jeśli na komputerach użytkowników końcowych są już zainstalowane wstępnie wymagane składniki.

 W ramach niestandardowego procesu instalacji Wywołaj narzędzie Instalatora dla rozwiązań pakietu Office (*VSTOInstaller.exe*), które jest domyślnie instalowane w następującej lokalizacji:

 *%CommonProgramFiles%\Microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Jeśli narzędzie nie znajduje się w tej lokalizacji, możesz użyć klucza rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** lub **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** , aby znaleźć ścieżkę do tego narzędzia.

 Przy użyciu *VSTOinstaller.exe* można użyć następujących parametrów.

| Parametr | Definicja |
|------------------| - |
| /Install lub /I | Instalowanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Możesz określić ścieżkę na komputerze lokalnym, udział plików UNC (Universal Naming Convention). Można określić ścieżkę lokalną (*C:\FolderName\PublishFolder*), ścieżkę względną (*\\ Publish*) lub w pełni kwalifikowaną lokalizację (*\\ \ServerName\FolderName* lub http://<em>servername/nazwa_folderu</em>). |
| /Uninstall lub /U | Odinstalowywanie rozwiązania. Po tej opcji należy podać ścieżkę manifestu wdrażania. Ścieżkę można określić na komputerze lokalnym, udziale plików UNC. Można określić ścieżkę lokalną (*c:\FolderName\PublishFolder*), ścieżkę względną (*\\ Publish*) lub w pełni kwalifikowaną lokalizację (*\\ \ServerName\FolderName* lub http://<em>servername/nazwa_folderu</em>). |
| /Silent lub /S | Instalowanie lub odinstalowywanie bez monitowania użytkownika o wprowadzenie danych ani wyświetlania jakichkolwiek komunikatów. Jeśli wymagany jest monit dotyczący zaufania, dostosowanie nie jest zainstalowane ani zaktualizowane. |
| /Help lub /? | Wyświetlanie informacji Pomocy. |

 Po uruchomieniu *VSTOinstaller.exe* mogą pojawić się następujące kody błędów.

|Kod błędu|Definicja|
|----------------|----------------|
|0|Rozwiązanie zostało pomyślnie zainstalowane lub odinstalowane albo została wyświetlona Pomoc narzędzia VSTOInstaller.|
|-100|Co najmniej jedna opcja wiersza polecenia jest nieprawidłowa lub została ustawiona więcej niż raz. Aby uzyskać więcej informacji, wpisz "vstoinstaller/?". lub zobacz [Tworzenie niestandardowego Instalatora dla rozwiązania pakietu Office ClickOnce](/previous-versions/bb772078(v=vs.110)).|
|-101|Co najmniej jedna opcja wiersza polecenia jest nieprawidłowa. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|
|-200|Identyfikator URI manifestu wdrożenia jest nieprawidłowy. Aby uzyskać więcej informacji, wpisz „vstoinstaller /?”.|
|-201|Nie można zainstalować rozwiązania, ponieważ manifest wdrożenia jest nieprawidłowy. Zobacz [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|Nie można zainstalować rozwiązania, ponieważ sekcja Visual Studio Tools pakietu Office manifestu aplikacji jest nieprawidłowa. Zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|Nie można zainstalować rozwiązania, ponieważ wystąpił błąd pobierania. Sprawdź identyfikator URI lub lokalizację pliku sieciowego manifestu wdrażania, a następnie ponów próbę.|
|-300|Nie można zainstalować rozwiązania, ponieważ wystąpił wyjątek zabezpieczeń. Zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).|
|-400|Nie można zainstalować rozwiązania.|
|-401|Nie można odinstalować rozwiązania.|
|-500|Operacja została anulowana, ponieważ nie można zainstalować lub odinstalować rozwiązania albo nie można pobrać manifestu wdrażania.|

## <a name="publish-an-update"></a><a name="Update"></a> Publikowanie aktualizacji
 Aby zaktualizować rozwiązanie, Opublikuj je ponownie za pomocą **projektanta projektu** lub **Kreatora publikacji**, a następnie skopiuj zaktualizowane rozwiązanie do lokalizacji instalacji. Podczas kopiowania plików do lokalizacji instalacji trzeba koniecznie zaznaczyć opcję zastąpienia poprzednich plików.

 Przy następnym przeszukiwaniu rozwiązania dla aktualizacji zostanie automatycznie wyszukana i załadowana Nowa wersja.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> Zmiana lokalizacji instalacji rozwiązania
 Po opublikowaniu rozwiązania można dodać lub zmienić ścieżkę instalacji. Często powody takiej zmiany są następujące:

- Program instalacyjny został skompilowany przed ustaleniem ścieżki instalacji.

- Pliki rozwiązania skopiowano do innej lokalizacji.

- Serwer, na którym znajdują się pliki instalacyjne, ma nową nazwę lub lokalizację.

  Aby zmienić ścieżkę instalacji rozwiązania, należy zaktualizować program instalacyjny, po czym użytkownicy muszą go uruchomić. W przypadku dostosowań na poziomie dokumentu użytkownicy muszą również w swoich dokumentach tak zaktualizować odnośną właściwość, aby wskazywała nową lokalizację.

> [!NOTE]
> Jeśli nie chcesz, aby użytkownicy mogli aktualizować właściwości dokumentu, możesz polecić użytkownikom uzyskanie zaktualizowanego dokumentu z lokalizacji instalacji.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Aby zmienić ścieżkę instalacji w programie instalacyjnym

1. Otwórz okno **wiersza polecenia** , a następnie zmień katalogi na folder instalacji.

2. Uruchom program instalacyjny i Uwzględnij `/url` parametr, który przyjmuje nową ścieżkę instalacji jako ciąg.

    Poniższy przykład pokazuje, jak zmienić ścieżkę instalacji na lokalizację w witrynie internetowej firmy Fabrikam; widoczny adres URL można zastąpić dowolną inną ścieżką:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Jeśli pojawi się komunikat z informacją, że podpis pliku wykonywalnego zostanie unieważniony, certyfikat użyty do podpisania rozwiązania jest nieważny, a wydawca nieznany. W rezultacie przed zainstalowaniem rozwiązania użytkownicy będą musieli potwierdzić, że ufają jego źródłu.

   > [!NOTE]
   > Aby wyświetlić bieżącą wartość adresu URL, uruchom polecenie `setup.exe /url` .

   W przypadku dostosowań na poziomie dokumentu użytkownicy muszą otworzyć dokument, a następnie zaktualizować jego właściwość _AssemblyLocation. Poniżej zamieszczono odpowiednią procedurę.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Aby zaktualizować właściwość _AssemblyLocation w dokumencie

1. Na karcie **plik** wybierz pozycję **informacje**, którą przedstawiono na poniższej ilustracji.

     ![Karta informacje w programie Excel](../vsto/media/vsto-infotab.png "Karta informacje w programie Excel")

2. Na liście **Właściwości** wybierz pozycję **Zaawansowane właściwości**, które przedstawiono na poniższej ilustracji.

     ![Zaawansowane właściwości w programie Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Zaawansowane właściwości w programie Excel.")

3. Na karcie **niestandardowe** na liście **Właściwości** wybierz _AssemblyLocation, jak pokazano na poniższej ilustracji.

     ![Właściwość AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "Właściwość AssemblyLocation.")

     Pole **Value** zawiera identyfikator manifestu wdrożenia.

4. Przed identyfikatorem wprowadź w pełni kwalifikowaną ścieżkę do dokumentu, a po nim pasek w  | *identyfikatorze* ścieżki formatu (na przykład *File://servername/FolderName/filename|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Aby uzyskać więcej informacji o sposobie formatowania tego identyfikatora, zobacz [niestandardowe właściwości dokumentu — Omówienie](../vsto/custom-document-properties-overview.md).

5. Wybierz przycisk **OK** , a następnie Zapisz i Zamknij dokument.

6. Uruchom program instalacyjny bez parametru /url. Rozwiązanie zostanie zainstalowane w podanej lokalizacji.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> Wycofywanie rozwiązania do wcześniejszej wersji
 Wycofanie rozwiązania powoduje, że użytkownicy wrócą do korzystania z jego starszej wersji.

#### <a name="to-roll-back-a-solution"></a>Aby wycofać rozwiązanie

1. Otwórz lokalizację instalacji rozwiązania.

2. W folderze publikowania najwyższego poziomu usuń manifest wdrożenia (plik *. VSTO* ).

3. Znajdź podfolder wersji, do której chcesz wycofać rozwiązanie.

4. Skopiuj manifest wdrażania z tego podfolderu do folderu publikowania najwyższego poziomu.

     Na przykład aby wycofać rozwiązanie o nazwie **OutlookAddIn1** z wersji 1.0.0.1 do wersji 1.0.0.0, skopiuj plik **OutlookAddIn1. vsto** z folderu **OutlookAddIn1_1_0_0_0** . Wklej plik do folderu publikowania najwyższego poziomu, zastępując manifest wdrożenia specyficzny dla wersji dla **OutlookAddIn1_1_0_0_1** , który już istnieje.

     Na ilustracji poniżej widać strukturę folderu publikowania w opisywanym przykładzie.

     ![Struktura folderu publikowania](../vsto/media/publishfolderstructure.png "Struktura folderu publikowania")

     Gdy użytkownik następnym razem otworzy aplikację lub dostosowany dokument, zostanie wykryta zmiana manifestu wdrażania. Starsza wersja rozwiązania dla pakietu Office jest uruchamiana z pamięci podręcznej funkcji ClickOnce.

> [!NOTE]
> Dane lokalne są zapisywane tylko dla jednej poprzedniej wersji rozwiązania. Jeśli wycofasz dwie wersje, dane lokalne nie są zachowywane. Aby uzyskać więcej informacji na temat danych lokalnych, zobacz [dostęp do danych lokalnych i zdalnych w aplikacjach ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Zobacz też

- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Publikowanie rozwiązań pakietu Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Instrukcje: publikowanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Instrukcje: Instalowanie rozwiązania Office ClickOnce](/previous-versions/bb608592(v=vs.110))
- [Instrukcje: publikowanie rozwiązania pakietu Office na poziomie dokumentu na serwerze programu SharePoint przy użyciu technologii ClickOnce](/previous-versions/bb608595(v=vs.110))
- [Tworzenie niestandardowego Instalatora dla rozwiązania Office ClickOnce](/previous-versions/bb772078(v=vs.110))