---
title: Wdrażanie narzędzi programu Visual Studio dla rozwiązania pakietu Office przy użyciu Instalatora Windows
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46bfa808cbf99e942d7aadd2802f51eecfcefae8
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444909"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Wdrażanie narzędzi programu Visual Studio dla rozwiązania pakietu Office przy użyciu Instalatora Windows

## <a name="summary"></a>Podsumowanie

Dowiedz się, jak wdrożyć dodatek Microsoft Visual Studio Tools for Office (VSTO) lub rozwiązanie na poziomie dokumentu przy użyciu projektu instalatora programu Visual Studio.

Wouter van Vugt, Radca Prawny

Ted Pattison, Ted Pattison Group

Ten artykuł został zaktualizowany przez firmę Microsoft za zgodą oryginalnych autorów.

**Dotyczy:** Narzędzia programu Visual Studio dla pakietu Office, pakietu Microsoft Office, programu Microsoft Visual Studio.

## <a name="overview"></a>Omówienie

Rozwiązanie VSTO można opracować i wdrożyć rozwiązanie przy użyciu pakietu Instalatora Windows. Ta dyskusja obejmuje kroki wdrażania prostego dodatku pakietu Office.

## <a name="deployment-methods"></a>Metody wdrażania

ClickOnce może być łatwo używany do tworzenia ustawień dla dodatków i rozwiązań. Nie można jednak zainstalować dodatków, które wymagają uprawnień administracyjnych, takich jak dodatki na poziomie komputera.

Dodatki, które wymagają uprawnień administracyjnych, można zainstalować za pomocą Instalatora Windows, ale tworzenie instalacji wymaga więcej wysiłku.

Aby zapoznać się z omówieniem sposobu wdrażania rozwiązania VSTO przy użyciu funkcji ClickOnce, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu funkcji ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Wdrażanie rozwiązań pakietu Office, które są przeznaczone dla środowiska wykonawczego VSTO

ClickOnce i Pakiety Instalatora Windows należy wykonać te same podstawowe zadania podczas instalowania rozwiązania pakietu Office.

1. Zainstaluj składniki wymaganego na komputerze użytkownika.
2. Wdrażanie określonych składników dla rozwiązania.
3. W przypadku dodatków utwórz wpisy rejestru.
4. Zaufaj rozwiązaniu, aby umożliwić jego wykonanie.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Wymagane składniki wymagań wstępnych na komputerze docelowym

Oto lista oprogramowania, które musi być zainstalowane na komputerze, aby uruchomić rozwiązania VSTO:

- Pakiet Microsoft Office 2010 lub nowszy.
- Microsoft .NET Framework 4 lub nowsze.
- Narzędzia programu Microsoft Visual Studio 2010 dla środowiska wykonawczego pakietu Office.
  Środowisko wykonawcze udostępnia środowisko, które zarządza dodatkami i rozwiązaniami na poziomie dokumentu. Wersja środowiska wykonawczego jest dostarczany z pakietem Microsoft Office, ale można rozpowszechniać określoną wersję z dodatkiem.
- Zestawy interop podstawowy dla pakietu Microsoft Office, jeśli nie używasz osadzonych typów interop.
- Wszystkie zestawy narzędzi, do których odwołują się projekty.

### <a name="specific-components-for-the-solution"></a>Konkretne składniki rozwiązania

Pakiet instalatora musi zainstalować te składniki na komputerze użytkownika:

- Dokument pakietu Microsoft Office, jeśli tworzysz rozwiązanie na poziomie dokumentu.
- Zestaw dostosowywania i wszelkie zestawy, które wymaga.
- Dodatkowe składniki, takie jak pliki konfiguracyjne.
- Manifest aplikacji (manifest).
- Manifest wdrażania (.vsto).

### <a name="registry-entries-for-add-ins"></a>Wpisy rejestru dla dodatków

Pakiet Microsoft Office używa wpisów rejestru do lokalizowania i ładowania dodatków. Te wpisy rejestru powinny być tworzone w ramach procesu wdrażania. Aby uzyskać więcej informacji na temat tych wpisów rejestru, zobacz [Wpisy rejestru dla dodatków VSTO](registry-entries-for-vsto-add-ins.md).

Dodatki programu Outlook, które wyświetlają niestandardowe regiony formularzy, wymagają dodatkowych wpisów rejestru, które umożliwiają identyfikowanie regionów formularza. Aby uzyskać więcej informacji o wpisach rejestru, zobacz [Wpisy rejestru dla regionów formularza programu Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Rozwiązania na poziomie dokumentu nie wymagają żadnych wpisów rejestru. Zamiast tego właściwości wewnątrz dokumentu są używane do lokalizowania dostosowywania. Aby uzyskać więcej informacji na temat tych właściwości, zobacz [Omówienie właściwości dokumentu niestandardowego](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Ufanie rozwiązaniu VSTO

Aby można było uruchomić dostosowanie, rozwiązanie musi być zaufane przez komputer. Dodatek można ufać, podpisując manifest za pomocą certyfikatu, tworząc relację zaufania z listą dołączania lub instalując go w zaufanej lokalizacji na komputerze.

Aby uzyskać więcej informacji na temat uzyskiwania certyfikatu do podpisywania, zobacz [ClickOnce Deployment and Authenticode](../deployment/clickonce-and-authenticode.md). Aby uzyskać więcej informacji na temat ufania rozwiązaniom, zobacz [Ufanie rozwiązaniom pakietu Office przy użyciu list dołączania](trusting-office-solutions-by-using-inclusion-lists.md). W pliku Instalatora Windows można dodać wpis listy dołączania z akcją niestandardową. Aby uzyskać więcej informacji na temat włączania listy dołączania, zobacz [Jak: Konfigurowanie zabezpieczeń listy dołączania](how-to-configure-inclusion-list-security.md).

Jeśli żadna z tych opcji nie jest używana, użytkownik jest wyświetlany monit zaufania, aby umożliwić mu podjęcie decyzji, czy ufać rozwiązaniu.

Aby uzyskać więcej informacji na temat zabezpieczeń związanych z rozwiązaniami na poziomie dokumentu, zobacz [Przyznawanie zaufania do dokumentów](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Tworzenie instalatora podstawowego

Szablony projektów instalacji i wdrażania są dołączone do rozszerzenia [Microsoft Visual Studio Installer Projects,](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) które jest dostępne do pobrania.

Aby utworzyć instalator dla rozwiązania pakietu Office, należy wykonać następujące zadania:

- Dodaj składniki rozwiązania pakietu Office, które zostaną wdrożone.
- W przypadku dodatków na poziomie aplikacji należy skonfigurować klucze rejestru.
- Skonfiguruj składniki wstępne, aby można je było zainstalować na komputerach użytkowników końcowych.
- Skonfiguruj warunki uruchamiania, aby sprawdzić, czy wymagane składniki wymagań wstępnych są dostępne. Warunki uruchamiania mogą być używane do blokowania instalacji, jeśli wszystkie wymagane wymagania wstępne nie są zainstalowane.

Pierwszym krokiem jest utworzenie projektu instalacji.

### <a name="to-create-the-addin-setup-project"></a>Aby utworzyć projekt Instalatora dodatku

1. Otwórz program Office AddIn Project, który chcesz wdrożyć. W tym przykładzie używamy dodatku programu Excel o nazwie ExcelAddIn.
2. Po otwarciu programu Office Project w menu **Plik** rozwiń węzeł **Dodaj** i kliknij pozycję **Nowy projekt,** aby dodać nowy projekt.
::: moniker range="=vs-2017"
3. W oknie dialogowym **Dodawanie nowego projektu** rozwiń węzeł Inne **typy projektów** w **okienku Typy projektów,** a następnie rozwiń węzeł **Ustawienia i wdrożenie,** a następnie wybierz pozycję **Instalator programu Visual Studio**.
4. W okienku **Szablony** wybierz pozycję **Projekt instalacji** z grupy zainstalowane szablony **programu Visual Studio.**
::: moniker-end
::: moniker range="=vs-2019"
3. W oknie **dialogowym Dodawanie nowego projektu** wybierz szablon **Projektu instalacji.**
4. Kliknij przycisk **Dalej**.
::: moniker-end

5. W polu **Nazwa** wpisz **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Kliknij **przycisk Otwórz,** aby utworzyć nowy projekt instalacji.
::: moniker-end
::: moniker range="=vs-2019"
6. Kliknij **przycisk Utwórz,** aby utworzyć nowy projekt instalacji.
::: moniker-end

Program Visual Studio otwiera Eksploratora systemu plików dla nowego projektu instalacji. Eksplorator systemu plików umożliwia dodawanie plików do projektu instalacji.

   ![Zrzut ekranu przedstawiający Eksploratora systemu plików dla projektu instalacji](media/setup-project-figure-1.png)

   **Rysunek 1: Eksplorator systemu plików dla projektu instalacji**

Projekt instalacji musi wdrożyć program ExcelAddIn. Projekt instalacji dla tego zadania można skonfigurować, dodając dane wyjściowe projektu Programu ExcelAddIn do projektu instalacji.

### <a name="to-add-the-exceladdin-project-output"></a>Aby dodać dane wyjściowe projektu Programu ExcelAddIn

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję OfficeAddInSetup**, kliknij polecenie **Dodaj,** a następnie **pozycję Wyjście projektu**.
2. W oknie dialogowym **Dodawanie grupy wyjściowej projektu** wybierz **exceladdin** z listy projektu i **wyjście podstawowe**.
3. Kliknij **przycisk OK,** aby dodać dane wyjściowe projektu do projektu instalacyjnego.

    ![Zrzut ekranu przedstawiający okno dialogowe Grupa wyjściowa dodawania projektu instalatora](media/setup-project-figure-2.png)

    **Rysunek 2: Okno dialogowe Konfigurowanie grupy wyjściowej dodaj projekt**

Projekt instalacji musi wdrożyć manifest wdrożenia i manifest aplikacji. Dodaj te dwa pliki do projektu instalacji jako pliki autonomiczne z folderu wyjściowego projektu ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Aby dodać manifesty wdrażania i aplikacji

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję OfficeAddInSetup**, kliknij polecenie **Dodaj**i kliknij polecenie **Plik**.
2. W oknie dialogowym **Dodawanie plików** przejdź do katalogu wyjściowego **programu ExcelAddIn.** Zazwyczaj katalog wyjściowy jest podfolderem **wydania pojemnika\\** katalogu głównego projektu, w zależności od wybranej konfiguracji kompilacji.
3. Wybierz pliki **ExcelAddIn.vsto** i **ExcelAddIn.dll.manifest** i kliknij przycisk **Otwórz,** aby dodać te dwa pliki do projektu instalacji.

    ![Zrzut ekranu przedstawiający manifesty aplikacji i wdrażania w Eksploratorze rozwiązań](media/setup-project-figure-3.jpg)

    **Rysunek 3: Manifesty aplikacji i wdrażania dla Eksploratora rozwiązań dodatku**

Odwoływanie się do programu ExcelAddIn obejmuje wszystkie składniki, których wymaga program ExcelAddIn. Te składniki muszą być wykluczone i wdrożone przy użyciu pakietów wstępnych, aby umożliwić ich poprawne zarejestrowanie. Ponadto postanowienia licencyjne dotyczące oprogramowania muszą być wyświetlane i akceptowane przed rozpoczęciem instalacji.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Aby wykluczyć zależności projektu Programu ExcelAddIn

1. W **Eksploratorze rozwiązań**w węźle **OfficeAddInSetup** zaznacz wszystkie elementy zależności poniżej elementu **Wykryte zależności,** z wyjątkiem programu **Microsoft .NET Framework** lub dowolnego zestawu, który kończy się na ** \*pliku . Utilities.dll**. Zestawy narzędzia są przeznaczone do wdrożenia wraz z aplikacją.
2. Kliknij prawym przyciskiem myszy grupę i wybierz polecenie **Właściwości**.
3. W oknie **Właściwości** zmień właściwość **Wyklucz** na **True,** aby wykluczyć zestawy zależne z projektu instalacji. Upewnij się, że nie wyklucza żadnych zestawów narzędziowych.

    ![Zrzut ekranu przedstawiający Eksploratora rozwiązań przedstawiający zależności do wykluczenia](media/setup-project-figure-4.jpg)

    **Wykres 4: Z wyłączeniem zależności**

Pakiet Instalatora Windows można skonfigurować do instalowania składników wymaganych przez dodanie programu instalacyjnego, znanego również jako program uruchamiający. Ten program instalacyjny może zainstalować składniki wymaganego, proces zwany boottrapping.

W przypadku **programu ExcelAddIn**te wymagania wstępne muszą być zainstalowane, zanim dodatek będzie mógł działać poprawnie:

- Wersja programu Microsoft .NET Framework przeznaczona dla rozwiązania pakietu Office.
- Narzędzia programu Microsoft Visual Studio 2010 dla środowiska wykonawczego pakietu Office.

Aby skonfigurować składniki zależne jako wymagania wstępne

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **OfficeAddInSetup** i wybierz polecenie **Właściwości**.
2. Zostanie wyświetlone okno dialogowe **Strony właściwości OfficeAddInSetup.**
3. Kliknij przycisk **Wymagania wstępne.**
4. W oknie dialogowym Wymagania wstępne wybierz poprawną wersję programu .NET Framework i narzędzia programu Microsoft Visual Studio Tools for Office Runtime.

    ![Zrzut ekranu przedstawiający okno dialogowe Wymagania wstępne](media/setup-project-figure-5.png)

    **Rysunek 5: Okno dialogowe Wymagania wstępne**

    > [!NOTE]
    >Niektóre skonfigurowane pakiety wstępnych w programie Visual Studio Setup Project są zależne od wybranej konfiguracji kompilacji. Należy wybrać odpowiednie składniki wymagane dla każdej używanej konfiguracji kompilacji.

Pakiet Microsoft Office lokalizuje dodatki przy użyciu kluczy rejestru. Klucze w gałęzi\_\_HKEY CURRENT USER są używane do rejestrowania dodatku dla każdego użytkownika. Klucze w obszarze\_\_HKEY LOCAL MACHINE są używane do rejestrowania dodatku dla wszystkich użytkowników komputera. Aby uzyskać więcej informacji na temat kluczy rejestru, zobacz [Wpisy rejestru dla dodatków VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Aby skonfigurować rejestr

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję OfficeAddInSetup**.
2. Rozwiń **widok**.
3. Kliknij **pozycję Rejestr,** aby otworzyć okno edytora rejestru.
4. W edytorze **Registry(OfficeAddInSetup)** rozwiń węzeł **HKEY\_LOCAL\_MACHINE,** a następnie **program Software**.
5. Usuń ** \[przycisk\]Producenta**?znaleziony w obszarze **HKEY\_LOCAL\_MACHINE\\Software**.
6. Rozwiń **HKEY\_CURRENT\_USER,** a następnie **Oprogramowanie**.
7. Usuń klucz ** \[Producent\] ** znaleziony w obszarze **HKEY\_\_CURRENT USER\\Software**.
8. Aby dodać klucze rejestru do instalacji dodatku, kliknij prawym przyciskiem myszy klucz **Ulucha/komputera,** wybierz pozycję **Nowy klucz**. Użyj tekstu **Oprogramowanie** dla nazwy nowego klucza. Kliknij prawym przyciskiem myszy nowo utworzony klawisz **Software** i utwórz nowy klucz z tekstem **Microsoft**.
9. Użyj podobnego procesu, aby utworzyć całą hierarchię kluczy wymaganą dla rejestracji dodatku:

    **\\Oprogramowanie gałęzi komputera\\Microsoft\\\\Office\\Excel\\Addins SampleCompany.ExcelAddIn**

    Nazwa firmy jest często używana jako prefiks nazwy dodatku w celu zapewnienia unikatowości.

10. Kliknij prawym przyciskiem myszy klucz **SampleCompany.ExcelAddIn,** wybierz polecenie **Nowy**i kliknij polecenie **Wartość ciągu**. Użyj tekstu **Opis** nazwy.
11. Ten krok służy do dodawania trzech kolejnych wartości:
    - **FriendlyName** typu **String**
    - **Zachowanie ładunku** typu **DWORD**
    - **Manifest** typu **String**

12. Kliknij prawym przyciskiem myszy wartość **Opis** w edytorze rejestru i kliknij polecenie **Okno Właściwości**. W **oknie Właściwości**wprowadź polecenie **Dodaj demo programu Excel** dla właściwości Wartość.
13. Wybierz klucz **FriendlyName** w edytorze rejestru. W **oknie Właściwości**zmień właściwość **Value** na Excel **Demo AddIn**.
14. Wybierz klucz **LoadBehavior** w edytorze rejestru. W **oknie Właściwości**zmień **właściwość Value** na **3.** Wartość 3 dla LoadBehavior wskazuje, że dodatek powinien zostać załadowany podczas uruchamiania aplikacji hosta. Aby uzyskać więcej informacji na temat zachowania ładowania, zobacz [Wpisy rejestru dla dodatków VSTO](registry-entries-for-vsto-add-ins.md).

15. Wybierz klucz **manifestu** w edytorze rejestru. W **oknie Właściwości**zmień właściwość **Value** na **file:///[TARGETDIR]ExcelAddIn.vsto|vstolocal**

    ![Zrzut ekranu przedstawiający Edytor rejestru](media/setup-project-figure-6.png)

    **Rysunek 6: Konfigurowanie kluczy rejestru**

      Środowisko wykonawcze VSTO używa tego klucza rejestru do zlokalizowania manifestu wdrożenia. Makro [TARGETDIR] zostanie zastąpione folderem, w którym dodatek jest zainstalowany. Makro będzie zawierać końcowe \ znak, więc nazwa pliku manifestu wdrożenia powinny być ExcelAddIn.vsto bez znaku \.
      **Vstolocal** postfix, informuje środowiska wykonawczego VSTO, że dodatek należy załadować z tej lokalizacji zamiast ClickOnce pamięci podręcznej. Usunięcie tego postfix spowoduje, że środowisko uruchomieniowe, aby skopiować dostosowanie do clickonce pamięci podręcznej.

   >[!WARNING]
   >Należy zachować szczególną ostrożność z Edytora rejestru w programie Visual Studio. Na przykład jeśli przypadkowo ustawisz DeleteAtUninstall dla niewłaściwego klucza, możesz usunąć aktywną część rejestru, pozostawiając komputer użytkownika w niespójnym lub jeszcze gorszym stanie.

64-bitowe wersje pakietu Office będą używać gałęzi rejestru 64-bitowego do wyszukiwania dodatków. Aby zarejestrować dodatki w obszarze gałęzi rejestru 64-bitowego, platforma docelowa projektu konfiguracji musi być ustawiona tylko na 64-bitową.

1. Wybierz projekt **OfficeAddInSetup** w Eksploratorze rozwiązań.
2. Przejdź do okna **Właściwości** i ustaw właściwość **TargetPlatform** na **x64**.

Zainstalowanie dodatku dla wersji 32-bitowej i 64-bitowej pakietu Office wymaga utworzenia dwóch oddzielnych pakietów MSI. Jeden dla 32-bitowych i jeden dla 64-bitowych.

  ![Zrzut ekranu przedstawiający okno Właściwości przedstawiające platformę docelową do rejestrowania dodatków w 64-bitowym pakiecie Office](media/setup-project-figure-7.jpg)

  **Rysunek 7: Platforma docelowa do rejestrowania dodatków w 64-bitowym pakiecie Office**

Jeśli pakiet MSI jest używany do zainstalowania dodatku lub rozwiązania, może zostać zainstalowany bez konieczności instalowania wymaganych wymagań wstępnych. Za pomocą warunków uruchamiania w msi można zablokować instalację dodatku, jeśli wymagania wstępne nie są zainstalowane.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Konfigurowanie warunku uruchamiania w celu wykrycia środowiska wykonawczego VSTO

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję OfficeAddInSetup**.
2. Rozwiń **widok**.
3. Kliknij pozycję **Warunki uruchamiania**.
4. W edytorze **Warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy **pozycję Wymagania na komputerze docelowym,** a następnie kliknij polecenie Dodaj warunek uruchomienia **rejestru**. Ten warunek wyszukiwania może przeszukiwać rejestr w poszukiwaniu klucza instalowanego przez środowisko wykonawcze VSTO. Wartość klucza jest następnie dostępna dla różnych elementów instalatora za pośrednictwem właściwości o nazwie. Warunek uruchamiania używa właściwości zdefiniowanej przez warunek wyszukiwania, aby sprawdzić, czy pewna wartość.
5. W edytorze **Warunki uruchamiania (OfficeAddInSetup)** wybierz warunek wyszukiwania **Wyszukaj w rejestrzeWbior1,** kliknij go prawym przyciskiem myszy i wybierz **polecenie Okno Właściwości**.

6. W oknie **Właściwości** ustaw następujące właściwości:
   1. Ustaw wartość **(Nazwa)** na **Wyszukaj środowisko uruchomieniowe VSTO 2010**.
   2. Zmień wartość **właściwości** na **VSTORUNTIMEREDIST**.
   3. Ustawianie wartości **programu RegKey** na **SOFTWARE\\Microsoft\\VSTO Runtime Setup\\v4R**
   4. Pozostaw **właściwość root** ustawioną na **vsdrrHKLM**.
   5. Zmień właściwość **Value** na **Version**.

7. W edytorze **Warunki uruchamiania (OfficeAddInSetup)** wybierz warunek uruchomienia **Condition1,** kliknij go prawym przyciskiem myszy i wybierz **polecenie Okno Właściwości**.
8. W oknie Właściwości ustaw następujące właściwości:
   1. Ustaw **(Nazwa)** na **Sprawdź dostępność środowiska wykonawczego VSTO 2010**.
   2. Zmień wartość **Warunku** na **\>VSTORUNTIMEREDIST ="10.0.30319"**
   3. Pozostaw **właściwość InstallURL** pustą.
   4. Ustaw **komunikat** na **narzędzia programu Visual Studio 2010 dla środowiska wykonawczego pakietu Office nie jest zainstalowany. Uruchom plik Setup.exe, aby zainstalować dodatek**.

        ![Zrzut ekranu przedstawiający okno Właściwości stanu Uruchom weryfikuj dostępność środowiska wykonawczego](media/setup-project-figure-8.jpg)

        **Rysunek 8: Okno właściwości stanu Weryfikuj dostępność środowiska wykonawczego**

 Powyższy warunek uruchomienia jawnie sprawdza obecność środowiska wykonawczego VSTO, gdy jest zainstalowany przez pakiet programu inicjującego.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Konfigurowanie warunku uruchamiania w celu wykrycia środowiska wykonawczego VSTO zainstalowanego przez pakiet Office

1. W edytorze **Warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy pozycję **Search Target Machine**, a następnie kliknij polecenie Dodaj wyszukiwanie w **rejestrze**.
2. Wybierz warunek **wyszukaj w rejestrzeWej1,** kliknij go prawym przyciskiem myszy i wybierz polecenie **Okno Właściwości**.
3. W oknie **Właściwości** ustaw następujące właściwości:
    1. Ustaw wartość **(Nazwa)** na **Wyszukaj środowisko uruchomieniowe vsto pakietu Office**.
    2. Zmień wartość **właściwości** na **OfficeRuntime**.
    3. Ustaw wartość **regkey** **na\\\\SOFTWARE Microsoft VSTO Runtime Setup\\v4**.
    4. Pozostaw **właściwość root** ustawioną na **vsdrrHKLM**.
    5. Zmień właściwość **Value** na **Version**.

4. W edytorze **Warunki uruchamiania (OfficeAddInSetup)** wybierz warunek wcześniejszego uruchomienia **programu Weryfikuj dostępność środowiska wykonawczego VSTO 2010,** kliknij prawym przyciskiem myszy warunek i wybierz polecenie **Okno Właściwości**.

5. Zmień wartość **właściwości Condition** na ** \>VSTORUNTIMEREDIST ="10.0.30319"\>OR OFFICERUNTIME ="10.0.21022"**. Numery wersji mogą być różne dla Ciebie w zależności od wersji środowiska wykonawczego, który wymaga dodatku.

    ![Zrzut ekranu przedstawiający stan uruchamiania dla systemu Windows właściwości](media/setup-project-figure-9.jpg)
  
    **Rysunek 9: Właściwości systemu Windows dla warunku Weryfikuj dostępność środowiska wykonawczego za pomocą funkcji Redist lub Office**

Jeśli element docelowy dodatku .NET Framework 4 lub nowsze, typy wewnątrz podstawowych zestawów interop (PIA), do których się odwołuje, mogą być osadzone w zestawie VSTO.

Aby sprawdzić, czy typy interop zostaną osadzone w dodatku, wykonując następujące kroki:

1. Rozwiń węzeł odwołań w Eksploratorze rozwiązań
2. Wybierz jedno z odwołań PIA, na przykład **Office**.
3. Wyświetl okna właściwości, naciskając klawisz F4 lub wybierając właściwości z menu kontekstowego Złożenia.
4. Sprawdź wartość właściwości **Osadź Typy interop**.

Jeśli wartość jest ustawiona na **True**, następnie typy są osadzone i można przejść w dół do [**do tworzenia projektu konfiguracji**](#to-build-the-setup-project) sekcji.

Aby uzyskać więcej informacji, zobacz [Równoważność typów i osadzone typy międzypionowe](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Aby skonfigurować warunki uruchamiania w celu wykrycia tych w przypadku pia office

1. W edytorze **Warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy **pozycję Wymagania na komputerze docelowym,** a następnie kliknij polecenie Dodaj warunek uruchomienia **Instalatora Windows**. Ten warunek uruchomienia wyszukuje pia pakietu Office, wyszukując identyfikator określonego składnika.
2. Kliknij prawym przyciskiem myszy **pozycję Wyszukaj składnik1** i kliknij polecenie **Okno Właściwości,** aby wyświetlić właściwości warunku uruchomienia.
3. W **oknie Właściwości**ustaw następujące właściwości:

    1. Zmienianie wartości właściwości **(Nazwa)** na **Wyszukaj udostępnione pia pakietu Office**
    2. Zmień wartość **identyfikatora składnika** na Identyfikator składnika używanego składnika pakietu Office. Listę identyfikatorów komponentów można znaleźć w poniższej tabeli, na przykład **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Zmień wartość **właściwości Właściwość** na **HASSHAREDPIA**.

4. W edytorze **Warunki uruchamiania(OfficeAddInSetup)** kliknij prawym przyciskiem myszy **pozycję Condition1** i kliknij polecenie **Okno Właściwości,** aby wyświetlić właściwości warunku uruchamiania.

5. Zmień te właściwości **Condition1:**

    1. Zmień **(Nazwa)** na **Weryfikuj dostępność udostępnionego pia pakietu Office**.
    2. Zmień **warunek** na **HASSHAREDPIA**.
    3. Pozostaw **InstallUrl** puste.
    4. Zmień składnik **Wiadomość** na **Wymagany do interakcji z programem Excel nie jest dostępny. Uruchom plik setup.exe**.

    ![Zrzut ekranu przedstawiający okno Właściwości stanu uruchom udostępnioną pia pakietu Office](media/setup-project-figure-10.jpg)
  
    **Rysunek 10: Okno Właściwości stanu uruchom udostępnianie pia pakietu Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Identyfikatory składników podstawowych zestawów interop dla pakietu Microsoft Office

|Podstawowy zespół międzyoperacyjny|Office 2010|Office 2013|Office 2013 (64-bitowy)|Office 2016|Office 2016 (64-bitowy)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E}|{7C6D92EF-7B45-46E5-8670-819663220E}|
|PowerPoint|{EWGBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC}|{B2279272-3FD2-434D-B94E-E4E0F8561AC}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Tag inteligentny|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5b-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Udostępnione w pakiecie Office|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Projekt|{957A4EC0-E67b-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Zrzut ekranu przedstawiający ostateczne warunki startu](media/setup-project-figure-11.jpg)

  **Rysunek 11: Ostateczne warunki startu**

Można dodatkowo uściślić warunki uruchamiania instalacji programu ExcelAddIn. Na przykład może być przydatne sprawdzenie, czy zainstalowana jest rzeczywista docelowa aplikacja pakietu Office.

### <a name="to-build-the-setup-project"></a>Aby utworzyć projekt instalacji

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **OfficeAddInSetup** i kliknij polecenie **Kompilacja**.
2. Za pomocą **Eksploratora Windows**przejdź do katalogu wyjściowego projektu **OfficeAddInSetup** i przejdź do folderu Wydanie lub Debugowanie, w zależności od wybranej konfiguracji kompilacji. Skopiuj wszystkie pliki z folderu do lokalizacji, do którą użytkownicy mogą uzyskać dostęp.

Aby przetestować konfigurację programu ExcelAddIn

1. Przejdź do lokalizacji, do której skopiowano program **OfficeAddInSetup.**
2. Kliknij dwukrotnie plik setup.exe, aby zainstalować dodatek **OfficeAddInSetup.** Zaakceptuj wszystkie wyświetlane postanowienia licencyjne dotyczące oprogramowania i ukończ kreatora konfiguracji, aby zainstalować dodatek na komputerze użytkownika.

Rozwiązanie pakietu Office programu Excel należy zainstalować i uruchomić z lokalizacji określonej podczas instalacji.

## <a name="additional-requirements-for-document-level-solutions"></a>Dodatkowe wymagania dotyczące rozwiązań na poziomie dokumentu

Wdrażanie rozwiązań na poziomie dokumentu wymaga kilku różnych kroków konfiguracji w projekcie instalacji Instalatora Windows.

Oto lista podstawowych kroków wymaganych do wdrożenia rozwiązania na poziomie dokumentu:

- Utwórz projekt instalacji programu Visual Studio.
- Dodaj podstawowe dane wyjściowe rozwiązania na poziomie dokumentu. Dane wyjściowe podstawowe obejmują również dokument pakietu Microsoft Office.
- Dodaj manifesty wdrażania i aplikacji jako luźne pliki.
- Wyklucz składniki zależne z pakietu instalatora (z wyjątkiem wszystkich zestawów narzędzi).
- Konfigurowanie pakietów wstępnych.
- Skonfiguruj warunki uruchamiania.
- Skompiluj projekt instalacji i skopiuj wyniki do lokalizacji wdrożenia.
- Wdrażanie rozwiązania na poziomie dokumentu na komputerze użytkownika przez wykonanie instalatora.
- W razie potrzeby zaktualizuj właściwości dokumentu niestandardowego.

### <a name="changing-the-location-of-the-deployed-document"></a>Zmiana lokalizacji wdrożonego dokumentu

Właściwości wewnątrz dokumentu pakietu Office są używane do lokalizowania rozwiązań na poziomie dokumentu. Jeśli dokument jest zainstalowany w tym samym folderze co zestaw VSTO, nie są wymagane żadne zmiany. Jeśli jednak jest zainstalowany w innym folderze, te właściwości będą musiały zostać zaktualizowane podczas instalacji.

Aby uzyskać więcej informacji na temat tych właściwości dokumentu, zobacz [Omówienie właściwości dokumentu niestandardowego](custom-document-properties-overview.md).

Aby zmienić te właściwości, należy użyć akcji niestandardowej podczas instalacji.

W poniższym przykładzie użyto rozwiązania na poziomie dokumentu o nazwie ExcelWorkbookProject i projektu instalacji o nazwie ExcelWorkbookSetup. Projekt Programu ExcelWorkbookSetup jest konfigurowany przy użyciu tych samych kroków opisanych powyżej, z wyjątkiem ustawiania kluczy rejestru.

Aby dodać niestandardowy projekt akcji do rozwiązania programu Visual Studio

1. Dodaj nowy projekt konsoli platformy .NET do rozwiązania, klikając prawym przyciskiem myszy **projekt wdrażania dokumentów pakietu Office** w **Eksploratorze rozwiązań**
2. Rozwiń **pozycję Dodaj** i kliknij pozycję **Nowy projekt**.
3. Wybierz szablon aplikacji konsoli i nadaj nazwę projektu **AddCustomizationCustomAction**.

    ![Zrzut ekranu przedstawiający Eksploratora rozwiązań — AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Rysunek 12: Eksplorator rozwiązań — dodajcustomizationCustomaction**

4. Dodaj odwołanie do tych zestawów:
    1. System.componentmodel
    2. System.Configuration.Install
    3. Microsoft.VisualStudio.Tools.Applications
    4. Microsoft.visualstudio.tools.applications.serverdocument

5. Skopiuj ten kod do Program.cs lub Program.vb

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

Aby dodać dostosowanie do dokumentu, należy mieć identyfikator rozwiązania rozwiązania na poziomie dokumentu VSTO. Ta wartość jest pobierana z pliku projektu programu Visual Studio.

Aby pobrać identyfikator rozwiązania

1. W menu **Kompilacja** kliknij polecenie **Build Solution,** aby utworzyć rozwiązanie na poziomie dokumentu i dodać właściwość identyfikatora rozwiązania do pliku projektu.
2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt programu **ExcelWorkbookProject** na poziomie dokumentu
3. Kliknij **przycisk UnloadProject,** aby uzyskać dostęp do pliku projektu z wewnątrz programu Visual Studio.

    ![Zrzut ekranu przedstawiający rozwiązanie zwalniające dokument programu Excel z eksploratora rozwiązań](media/setup-project-figure-16.jpg)

    **Rysunek 13: Rozładunek rozwiązania dokumentu programu Excel**

4. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookProject** i kliknij polecenie **EditExcelWorkbookProject.vbproj** lub **Edytuj program ExcelWorkbookProject.csproj**.
5. W edytorze **ExcelWorkbookProject** znajdź element **SolutionID** wewnątrz elementu **PropertyGroup.**
6. Skopiuj wartość GUID tego elementu.

    ![Pobieranie solutionid](media/setup-project-figure-17.jpg)

    **Rysunek 14: Pobieranie solutionID**

7. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookProject** i kliknij polecenie **Ponownie załaduj projekt**.
8. Kliknij **przycisk Tak** w oknie dialogowym, które wydaje się zamykać edytor **ExcelWorkbookProject.**
9. Identyfikator **rozwiązania** będzie używany w akcji Zainstaluj niestandardowe.

Ostatnim krokiem jest skonfigurowanie akcji niestandardowej dla kroków **Zainstaluj** i **Odinstaluj.**

### <a name="to-configure-the-setup-project"></a>Aby skonfigurować projekt instalacji

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję ExcelWorkbookSetup**, rozwiń pozycję **Dodaj** i kliknij polecenie **Wyjście projektu**.
2. W oknie dialogowym **Dodawanie grupy wyjściowej projektu** na liście **Projekt** kliknij pozycję **DodajcustomizationCustomAction**.
3. Wybierz **opcję Wyjście podstawowe** i kliknij przycisk **OK,** aby zamknąć okno dialogowe i dodać zestaw zawierający akcję niestandardową do projektu instalacji.

    ![Zrzut ekranu przedstawiający akcję niestandardową manifestu dokumentu — dodawanie grupy wyjściowej projektu](media/setup-project-figure-18.jpg)

    **Rysunek 15: Akcja niestandardowa manifestu dokumentu — dodawanie grupy wyjściowej projektu**

4. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookSetup**.
5. Rozwiń **widok** i kliknij pozycję **Akcje niestandardowe**.
6. W edytorze **Akcje niestandardowe (ExcelWorkbookSetup)** kliknij prawym przyciskiem myszy **pozycję Akcje niestandardowe** i kliknij polecenie **Dodaj akcję niestandardową**.
7. W oknie dialogowym **Wybieranie elementu w projekcie** na liście **Szukaj w** kliknij pozycję Folder **aplikacji**. Wybierz **pozycję Dane wyjściowe podstawowe z addcustomizationCustomAction(active)** i kliknij przycisk **OK,** aby dodać akcję niestandardową do kroku Instalacja.
8. W **obszarze węzła Instalacja**kliknij prawym przyciskiem myszy **pozycję Dane wyjściowe podstawowe z addcustomizationCustomAction(Active)** i kliknij polecenie **Zmień nazwę**. Nazwij akcję niestandardową **Kopiuj dokument do folderu Moje dokumenty i dołącz dostosowanie**.
9. W **obszarze węzła Odinstalowywanie**kliknij prawym przyciskiem myszy **pozycję Podstawowe dane wyjściowe z addcustomizationCustomAction(Active)** i kliknij polecenie **Zmień nazwę**. Nazwij akcję niestandardową **Usuń dokument z folderu Dokumenty**.

    ![Zrzut ekranu przedstawiający okno Akcje niestandardowe manifestu dokumentu](media/setup-project-figure-19.jpg)

    **Rysunek 16: Akcje niestandardowe manifestu dokumentu**

10. W edytorze **Akcje niestandardowe (ExcelWorkbookSetup)** kliknij prawym przyciskiem myszy **pozycję Kopiuj dokument do moich dokumentów i dołącz dostosowywanie** i kliknij polecenie **Okno Właściwości**.
11. W oknie **Właściwości CustomActionData** wprowadź lokalizację **biblioteki** DLL dostosowywania, manifest wdrożenia i lokalizację dokumentu pakietu Microsoft Office. Program SolutionID jest również potrzebny.
12. Jeśli chcesz zarejestrować błędy konfiguracji do pliku, dołącz logfile parametr.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Zrzut ekranu przedstawiający okno Akcja niestandardowa do skopiowania dokumentu do właściwości moich dokumentów](media/setup-project-figure-20.jpg)

    **Rysunek 17: Akcja niestandardowa kopiowania dokumentu do moich dokumentów**

13. Akcja niestandardowa dla odinstalowywania wymaga nazwy dokumentu, można podać, że przy użyciu tego samego parametru documentLocation w **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Skompiluj i wdrażaj projekt **Programu ExcelWorkbookSetup.**
15. **Poszukaj** w folderze Moje dokumenty i otwórz plik ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Dodatkowe zasoby

[Jak: Instalowanie narzędzi programu Visual Studio dla środowiska wykonawczego pakietu Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Podstawowe zestawy międzyoperacyjne pakietu Office](office-primary-interop-assemblies.md)

[Wpisy rejestru dla dodatków VSTO](registry-entries-for-vsto-add-ins.md)

[Niestandardowe właściwości dokumentu ― Omówienie](custom-document-properties-overview.md)

[Określanie regionów formularzy w rejestrze systemu Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Udzielanie zaufania do dokumentów](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>O autorach

Wouter van Vugt jest microsoft MVP z technologii Office Open XML i niezależny konsultant koncentruje się na tworzeniu aplikacji biznesowych pakietu Office (OBA) z SharePoint, Microsoft Office i powiązanych technologii .NET.
Wouter jest częstym współpracownikiem witryn społeczności deweloperów, takich jak [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Opublikował kilka oficjalnych artykułów i artykułów, a także książkę dostępną w internecie pod tytułem Open XML: Explained e-book.
Wouter jest założycielem Code-Counsel, holenderskiej firmy zajmującej się dostarczaniem najnowocześniejszych treści technicznych za pośrednictwem różnych kanałów. Możesz dowiedzieć się więcej o Wouter czytając jego blog.

Ted Pattison jest MVP programu SharePoint, autorem, trenerem i założycielem Ted Pattison Group. Jesienią 2005 r. Ted został zatrudniony przez grupę Microsoft Developer Platform Evangelism do autora programu szkoleniowego dla deweloperów Ascend dla programu Windows SharePoint Services 3.0 i Microsoft Office SharePoint Server 2007. Od tego czasu Ted był całkowicie skoncentrowany na kształceniu profesjonalnych programistów w zakresie technologii SharePoint 2007. Ted zakończył pisanie książki dla microsoft press zatytułowanej Inside Windows SharePoint Services 3.0, która koncentruje się na tym, jak używać programu SharePoint jako platformy programistycznej do tworzenia rozwiązań biznesowych. Ted pisze również kolumnę poświęconą deweloperom dla magazynu MSDN zatytułowaną Office Space.
