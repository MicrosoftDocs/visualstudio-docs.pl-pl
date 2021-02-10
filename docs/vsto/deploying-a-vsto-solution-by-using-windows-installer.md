---
title: Wdrażanie rozwiązania VSTO przy użyciu Instalator Windows
description: Dowiedz się, jak wdrożyć dodatek narzędzi Microsoft Visual Studio Tools dla pakietu Office (VSTO) lub rozwiązanie na poziomie dokumentu przy użyciu projektu Instalator programu Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75c2d97e8cd30bb3cf5605d50e65a68513590647
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939373"
---
# <a name="deploying-a-vsto-solution-using-windows-installer"></a>Wdrażanie rozwiązania VSTO przy użyciu Instalator Windows

## <a name="summary"></a>Podsumowanie

Dowiedz się, jak wdrożyć dodatek narzędzi Microsoft Visual Studio Tools dla pakietu Office (VSTO) lub rozwiązanie na poziomie dokumentu przy użyciu projektu Instalator programu Visual Studio.

Wouter van vugt, Code prawnik

Ted Pattison, Ted Pattison

Ten artykuł został zaktualizowany przez firmę Microsoft z uprawnieniami od oryginalnych autorów.

**Dotyczy:** Visual Studio Tools pakietu Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>Omówienie

Możesz opracować rozwiązanie VSTO i wdrożyć rozwiązanie przy użyciu pakietu Instalator Windows. Ta dyskusja obejmuje procedurę wdrażania prostego dodatku dla pakietu Office.

## <a name="deployment-methods"></a>Metody wdrażania

Technologii ClickOnce można łatwo używać do tworzenia ustawień dla dodatków i rozwiązań. Nie może jednak instalować dodatków, które wymagają uprawnień administracyjnych, takich jak dodatki na poziomie komputera.

Dodatki wymagające uprawnień administracyjnych można instalować przy użyciu Instalator Windows, ale w celu utworzenia konfiguracji wymagane jest zwiększenie nakładu pracy.

Aby zapoznać się z omówieniem sposobu wdrażania rozwiązania VSTO przy użyciu technologii ClickOnce, zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>Wdrażanie rozwiązań pakietu Office przeznaczonych dla środowiska uruchomieniowego programu VSTO

Pakiety ClickOnce i Instalator Windows muszą wykonywać te same zadania podstawowe podczas instalowania rozwiązania pakietu Office.

1. Zainstaluj wstępnie wymagane składniki na komputerze użytkownika.
2. Wdróż określone składniki dla rozwiązania.
3. W przypadku dodatków Utwórz wpisy rejestru.
4. Ufaj temu rozwiązaniu, aby umożliwić jego wykonanie.

### <a name="required-prerequisite-components-on-the-target-computer"></a>Składniki wymagane wstępnie na komputerze docelowym

Poniżej znajduje się lista programów, które muszą być zainstalowane na komputerze, aby uruchomić rozwiązania VSTO:

- Microsoft Office 2010 lub nowszy.
- Microsoft .NET Framework w wersji 4 lub nowszej.
- Narzędzia Microsoft Visual Studio 2010 Tools for Office Runtime.
  Środowisko uruchomieniowe zapewnia środowisko, które zarządza dodatkami i rozwiązaniami na poziomie dokumentu. Wersja środowiska uruchomieniowego jest dostarczana z Microsoft Office ale może być konieczne ponowne rozproszenie określonej wersji z dodatkiem.
- Podstawowe zestawy międzyoperacyjności dla Microsoft Office, jeśli nie używasz osadzonych typów międzyoperacyjnych.
- Wszystkie zestawy narzędzi, do których odwołują się projekty.

### <a name="specific-components-for-the-solution"></a>Określone składniki rozwiązania

Pakiet Instalatora musi instalować te składniki na komputerze użytkownika:

- Dokument Microsoft Office, jeśli tworzysz rozwiązanie na poziomie dokumentu.
- Zestaw do dostosowywania i wszystkie wymagane przez niego zestawy.
- Dodatkowe składniki, takie jak pliki konfiguracji.
- Manifest aplikacji (manifest).
- Manifest wdrożenia (. VSTO).

### <a name="registry-entries-for-add-ins"></a>Wpisy rejestru dla dodatków

Microsoft Office używa wpisów rejestru do lokalizowania i ładowania dodatków. Te wpisy rejestru należy utworzyć w ramach procesu wdrażania. Aby uzyskać więcej informacji na temat tych wpisów rejestru, zobacz [wpisy rejestru dla dodatków narzędzi VSTO](registry-entries-for-vsto-add-ins.md).

Dodatki programu Outlook, które wyświetlają niestandardowe regiony formularzy, wymagają dodatkowych wpisów rejestru, które umożliwiają zidentyfikowanie regionów formularza. Aby uzyskać więcej informacji na temat wpisów rejestru, zobacz [wpisy rejestru dla regionów formularzy programu Outlook](registry-entries-for-vsto-add-ins.md#OutlookEntries).

Rozwiązania na poziomie dokumentu nie wymagają żadnych wpisów rejestru. Zamiast tego, właściwości wewnątrz dokumentu są używane do lokalizowania dostosowania. Aby uzyskać więcej informacji o tych właściwościach, zobacz [niestandardowe właściwości dokumentu — Omówienie](custom-document-properties-overview.md).

### <a name="trusting-the-vsto-solution"></a>Zaufanie do rozwiązania VSTO

Aby można było wykonać dostosowanie, rozwiązanie musi być zaufane przez komputer. Dodatek może być zaufany przez podpisywanie manifestu z certyfikatem, tworzenie relacji zaufania z listą dołączania lub instalowanie jej w zaufanej lokalizacji na maszynie.

Aby uzyskać więcej informacji na temat uzyskiwania certyfikatu do podpisywania, zobacz [wdrażanie ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md). Aby uzyskać więcej informacji o zaufanych rozwiązaniach, zobacz [ufanie rozwiązań pakietu Office przy użyciu list dołączania](trusting-office-solutions-by-using-inclusion-lists.md). Do pliku Instalator Windows można dodać wpis listy dołączania z akcją niestandardową. Aby uzyskać więcej informacji na temat włączania listy dołączania, zobacz [How to: Configure list dołączania — zabezpieczenia](how-to-configure-inclusion-list-security.md).

Jeśli żadna z opcji nie zostanie użyta, do użytkownika zostanie wyświetlony monit o zaufanie, aby umożliwić im zaufać temu rozwiązaniu.

Aby uzyskać więcej informacji o zabezpieczeniach związanych z rozwiązaniami na poziomie dokumentu, zobacz [udzielanie zaufania do dokumentów](granting-trust-to-documents.md).

## <a name="creating-a-basic-installer"></a>Tworzenie podstawowego Instalatora

Szablony projektu instalacji i wdrażania są dołączone do rozszerzenia [projekty instalatora Microsoft Visual Studio](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) , które jest dostępne do pobrania.

Aby utworzyć Instalatora dla rozwiązania pakietu Office, należy wykonać następujące zadania:

- Dodaj składniki rozwiązania pakietu Office, które zostaną wdrożone.
- Dla dodatków na poziomie aplikacji Skonfiguruj klucze rejestru.
- Skonfiguruj wstępnie wymagane składniki, aby można je było zainstalować na komputerach użytkowników końcowych.
- Skonfiguruj warunki uruchamiania, aby sprawdzić, czy dostępne są wymagane składniki wymagające wymagań wstępnych. Warunki uruchamiania mogą służyć do blokowania instalacji, jeśli wszystkie wymagane wymagania wstępne nie są zainstalowane.

Pierwszym krokiem jest utworzenie projektu Instalatora.

### <a name="to-create-the-addin-setup-project"></a>Aby utworzyć projekt Instalatora dodatku

1. Otwórz projekt dodatku pakietu Office, który chcesz wdrożyć. W tym przykładzie używamy dodatku dla programu Excel o nazwie ExcelAddIn.
2. Po otwarciu projektu pakietu Office w menu **plik** rozwiń węzeł **Dodaj** i kliknij pozycję **Nowy projekt** , aby dodać nowy projekt.
::: moniker range="=vs-2017"
3. W oknie dialogowym **Dodaj nowy projekt** rozwiń pozycję **Inne typy projektów** w okienku **typy projektów** , a następnie rozwiń węzeł **Instalacja i wdrożenie** , a następnie wybierz pozycję **Instalator programu Visual Studio**.
4. W okienku **Szablony** wybierz pozycję **Konfiguruj projekt** z grupy **zainstalowanych szablonów programu Visual Studio** .
::: moniker-end
::: moniker range="=vs-2019"
3. W oknie dialogowym **Dodawanie nowego projektu** wybierz szablon **projektu Instalatora** .
4. Kliknij przycisk **Dalej**.
::: moniker-end

5. W polu **Nazwa** wpisz **OfficeAddInSetup**.
::: moniker range="=vs-2017"
6. Kliknij przycisk **Otwórz** , aby utworzyć nowy projekt Instalatora.
::: moniker-end
::: moniker range="=vs-2019"
6. Kliknij przycisk **Utwórz** , aby utworzyć nowy projekt Instalatora.
::: moniker-end

Program Visual Studio otwiera Eksplorator systemu plików dla nowego projektu Instalatora. Eksplorator systemu plików umożliwia dodanie plików do projektu Instalatora.

   ![Zrzut ekranu Eksploratora systemu plików dla projektu Instalatora](media/setup-project-figure-1.png)

   **Rysunek 1: Eksplorator systemu plików dla projektu Instalatora**

Projekt instalacyjny musi wdrożyć ExcelAddIn. Możesz skonfigurować projekt konfiguracji dla tego zadania, dodając dane wyjściowe projektu ExcelAddIn do projektu Instalatora.

### <a name="to-add-the-exceladdin-project-output"></a>Aby dodać dane wyjściowe projektu ExcelAddIn

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **OfficeAddInSetup**, kliknij polecenie **Dodaj** , a następnie **dane wyjściowe projektu**.
2. W oknie dialogowym **Dodaj grupę wyjściową projektu** wybierz pozycję **ExcelAddIn** z listy projekt i pozycję **podstawowe dane wyjściowe**.
3. Kliknij przycisk **OK** , aby dodać dane wyjściowe projektu do projektu Instalatora.

    ![Zrzut ekranu przedstawiający okno dialogowe konfiguracji Dodaj grupę wyjściową projektu](media/setup-project-figure-2.png)

    **Rysunek 2. okno dialogowe Konfigurowanie projektu Dodaj grupę wyjściową projektu**

Projekt instalacyjny musi wdrożyć manifest wdrożenia i manifest aplikacji. Dodaj te dwa pliki do projektu Instalatora jako pliki autonomiczne z folderu wyjściowego projektu ExcelAddIn.

### <a name="to-add-the-deployment-and-application-manifests"></a>Aby dodać manifesty wdrożenia i aplikacji

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **OfficeAddInSetup**, kliknij pozycję **Dodaj**, a następnie kliknij pozycję **plik**.
2. W oknie dialogowym **Dodaj pliki** przejdź do katalogu wyjściowego **ExcelAddIn** . Zazwyczaj katalog wyjściowy jest podfolderem **\\ zwolnienia** z katalogu głównego projektu, w zależności od wybranej konfiguracji kompilacji.
3. Wybierz pliki **ExcelAddIn. VSTO** i **ExcelAddIn.dll. manifest** , a następnie kliknij przycisk **Otwórz** , aby dodać te dwa pliki do projektu Instalatora.

    ![Zrzut ekranu aplikacji i manifestów wdrożenia w Eksplorator rozwiązań](media/setup-project-figure-3.jpg)

    **Rysunek 3. manifesty aplikacji i wdrażania dla dodatku w Eksplorator rozwiązań**

Odwołanie do ExcelAddIn obejmuje wszystkie składniki, których wymaga ExcelAddIn. Te składniki muszą być wykluczone i wdrożone przy użyciu wstępnie wymaganych pakietów, aby umożliwić ich poprawne zarejestrowanie. Ponadto przed rozpoczęciem instalacji należy wyświetlić i zaakceptować postanowienia licencyjne dotyczące oprogramowania.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>Aby wykluczyć zależności projektu ExcelAddIn

1. W **Eksplorator rozwiązań** w węźle **OfficeAddInSetup** zaznacz pozycję Wszystkie elementy zależności pod **wykrytymi elementami zależnymi** , z wyjątkiem **platformy Microsoft .NET Framework** lub dowolnego zestawu kończącego się na **\*.Utilities.dll**. Zestawy narzędzi są przeznaczone do wdrożenia wraz z Twoją aplikacją.
2. Kliknij prawym przyciskiem myszy grupę i wybierz pozycję **Właściwości**.
3. W oknie **Właściwości** Zmień właściwość **exclude** na **true** , aby wykluczyć zestawy zależne z projektu Instalatora. Upewnij się, że żadne zestawy narzędzi nie zostały wykluczone.

    ![Zrzut ekranu przedstawiający Eksplorator rozwiązań pokazujący zależności do wykluczenia](media/setup-project-figure-4.jpg)

    **Rysunek 4. wykluczanie zależności**

Można skonfigurować pakiet Instalator Windows, aby zainstalować wstępnie wymagane składniki przez dodanie programu instalacyjnego, znanego również jako program inicjujący. Ten program instalacyjny może zainstalować wstępnie wymagane składniki, proces nazywany uruchomieniem.

W przypadku **ExcelAddIn** należy zainstalować te wymagania wstępne, aby dodatek mógł działać poprawnie:

- Wersja platformy Microsoft .NET, której celem jest rozwiązanie pakietu Office.
- Microsoft Visual Studio 2010 Tools for Office Runtime.

Aby skonfigurować składniki zależne jako wymagania wstępne

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **OfficeAddInSetup** i wybierz polecenie **Właściwości**.
2. Zostanie wyświetlone okno dialogowe **strony właściwości OfficeAddInSetup** .
3. Kliknij przycisk **wymagania wstępne** .
4. W oknie dialogowym wymagania wstępne Wybierz poprawną wersję .NET Framework i narzędzia Microsoft Visual Studio dla środowiska uruchomieniowego pakietu Office.

    ![Zrzut ekranu przedstawiający okno dialogowe wymagania wstępne](media/setup-project-figure-5.png)

    **Rysunek 5. okno dialogowe wymagania wstępne**

    > [!NOTE]
    >Niektóre ze skonfigurowanych wstępnie wymaganych pakietów w projekcie instalacyjnym programu Visual Studio są zależne od wybranej konfiguracji kompilacji. Należy wybrać odpowiednie wstępnie wymagane składniki dla każdej konfiguracji kompilacji, która jest używana.

Microsoft Office lokalizuje Dodatki przy użyciu kluczy rejestru. Klucze w \_ gałęzi Current User HKEY \_ są używane do rejestrowania dodatku dla każdego pojedynczego użytkownika. Klucze w ramach \_ \_ gałęzi maszyny lokalnej HKEY są używane do rejestrowania dodatku dla wszystkich użytkowników komputera. Aby uzyskać więcej informacji na temat kluczy rejestru, zobacz [wpisy rejestru dla dodatków narzędzi VSTO](registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-the-registry"></a>Aby skonfigurować rejestr

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **OfficeAddInSetup**.
2. Rozwiń **Widok**.
3. Kliknij pozycję **Rejestr** , aby otworzyć okno Edytor rejestru.
4. W edytorze **rejestru (OfficeAddInSetup)** rozwiń węzeł **HKEY \_ Local \_ Machine** , a następnie **Software**.
5. Usuń klucz **\[ producenta \]**? znaleziony w obszarze **HKEY \_ Local \_ Machine \\**.
6. Rozwiń węzeł **HKEY \_ bieżący \_ użytkownik** , a następnie pozycję **oprogramowanie**.
7. Usuń klucz **\[ producenta \]** znaleziony w obszarze **HKEY \_ bieżące \_ \\ oprogramowanie użytkownika**.
8. Aby dodać klucze rejestru dla instalacji dodatku, kliknij prawym przyciskiem myszy klucz **Hive User/Machine** , wybierz pozycję **nowy klucz**. Użyj **oprogramowania** tekstowego jako nazwy nowego klucza. Kliknij prawym przyciskiem myszy nowo utworzony klucz **oprogramowania** i Utwórz nowy klucz z tekstem **firmy Microsoft**.
9. Użyj podobnego procesu, aby utworzyć całą hierarchię kluczy wymaganą dla rejestracji dodatku:

    **Użytkownik/maszyna Hive \\ oprogramowania \\ Microsoft \\ Office \\ Excel \\ Addins \\ klucza SampleCompany. ExcelAddIn**

    Nazwa firmy jest często używana jako prefiks nazwy dodatku w celu zapewnienia unikatowości.

10. Kliknij prawym przyciskiem myszy klucz **klucza SampleCompany. ExcelAddIn** , wybierz pozycję **Nowy**, a następnie kliknij pozycję **wartość ciągu**. Użyj **opisu** tekstu dla nazwy.
11. Ten krok umożliwia dodanie trzech więcej wartości:
    - **FriendlyName** typu **String**
    - **LoadBehavior** typu **DWORD**
    - **Manifest** typu **String**

12. Kliknij prawym przyciskiem myszy wartość **Opis** w Edytorze rejestru, a następnie kliknij pozycję **okno właściwości**. W **oknie właściwości** wprowadź dla właściwości Value **dodatek demonstracji programu Excel** .
13. Wybierz klucz **FriendlyName** w Edytorze rejestru. W **oknie właściwości** Zmień właściwość **wartość** na **dodatek demonstracyjny programu Excel**.
14. Wybierz klucz **LoadBehavior** w Edytorze rejestru. W **oknie właściwości** Zmień właściwość **wartość** na **3.** Wartość 3 dla LoadBehavior wskazuje, że dodatek należy załadować przy uruchamianiu aplikacji hosta. Aby uzyskać więcej informacji na temat zachowania ładowania, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](registry-entries-for-vsto-add-ins.md).

15. Wybierz klucz **manifestu** w Edytorze rejestru. W **oknie właściwości** Zmień właściwość **wartość** na **plik:///[TARGETDIR] ExcelAddIn. VSTO | vstolocal**

    ![Zrzut ekranu edytora rejestru](media/setup-project-figure-6.png)

    **Ilustracja 6. Konfigurowanie kluczy rejestru**

      Środowisko uruchomieniowe VSTO używa tego klucza rejestru do lokalizowania manifestu wdrożenia. Makro [TARGETDIR] zostanie zastąpione folderem, w którym jest zainstalowany dodatek. Makro będzie zawierać końcowy znak \, dlatego nazwa pliku manifestu wdrażania powinna być ExcelAddIn. VSTO bez znaku \.
      Przyrostkowy **vstolocal** , informuje środowisko uruchomieniowe programu VSTO, że dodatek powinien zostać załadowany z tej lokalizacji zamiast z pamięci podręcznej ClickOnce. Usunięcie tego przyrostka spowoduje, że środowisko uruchomieniowe skopiuje dostosowanie do pamięci podręcznej ClickOnce.

   >[!WARNING]
   >Należy zachować ostrożność w Edytorze rejestru w programie Visual Studio. Na przykład, jeśli przypadkowo ustawisz DeleteAtUninstall dla niewłaściwego klucza, możesz usunąć aktywną część rejestru, pozostawiając komputer użytkownika niespójny lub nawet gorszy stan.

64-bitowe wersje pakietu Office będą używać gałęzi rejestru 64-bitowego w celu wyszukania dodatków. Aby zarejestrować dodatki w gałęzi rejestru 64-bitowego, platforma docelowa projektu konfiguracji musi być ustawiona na 64-bitowe.

1. Wybierz projekt **OfficeAddInSetup** w Eksploratorze rozwiązań.
2. Przejdź do okna **Właściwości** i ustaw właściwość **targetplatform** na **x64**.

Zainstalowanie dodatku dla zarówno 32-bitowej, jak i 64-bitowej wersji pakietu Office, spowoduje konieczność utworzenia dwóch oddzielnych pakietów MSI. Jeden dla 32-bitowych i jeden dla 64-bitowy.

  ![Zrzut ekranu przedstawiający okno właściwości z platformą docelową do rejestrowania dodatków z pakietem 64-bitowym](media/setup-project-figure-7.jpg)

  **Rysunek 7: platforma docelowa do rejestrowania dodatków z pakietem 64-bitowym**

Jeśli pakiet MSI jest używany do instalowania dodatku lub rozwiązania, może on zostać zainstalowany bez zainstalowanego wymaganego wymagania wstępnego. Możesz użyć warunków uruchamiania w pliku MSI, aby zablokować dodatek z instalacji, jeśli wymagania wstępne nie są zainstalowane.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>Skonfiguruj warunek uruchomienia w celu wykrycia środowiska uruchomieniowego programu VSTO

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **OfficeAddInSetup**.
2. Rozwiń **Widok**.
3. Kliknij pozycję **warunki uruchamiania**.
4. W edytorze **warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy pozycję **wymagania na komputerze docelowym**, a następnie kliknij polecenie **Dodaj warunek uruchomienia rejestru**. Ten warunek wyszukiwania może przeszukać w rejestrze klucz, który jest instalowany przez środowisko uruchomieniowe programu VSTO. Wartość klucza jest następnie dostępna dla różnych elementów Instalatora za pomocą nazwanej właściwości. Warunek uruchamiania używa właściwości zdefiniowanej przez warunek wyszukiwania do sprawdzenia określonej wartości.
5. W edytorze **warunki uruchamiania (OfficeAddInSetup)** wybierz warunek wyszukiwania **RegistryEntry1** , kliknij prawym przyciskiem myszy warunek, a następnie wybierz polecenie **okno właściwości**.

6. W oknie **Właściwości** ustaw następujące właściwości:
   1. Ustaw wartość **(nazwa)** , aby **wyszukać środowisko uruchomieniowe programu VSTO 2010**.
   2. Zmień wartość **Właściwości** na **VSTORUNTIMEREDIST**.
   3. Ustaw wartość **klucz rejestru** na **oprogramowanie \\ Microsoft \\ VSTO uruchomieniowe Setup \\ v4R**
   4. Pozostaw Właściwość **root** ustawioną na wartość **vsdrrHKLM**.
   5. Zmień właściwość **Value** na **Version**.

7. W edytorze **warunki uruchamiania (OfficeAddInSetup)** wybierz warunek uruchamiania **Condition1** , kliknij prawym przyciskiem myszy warunek, a następnie wybierz polecenie **okno właściwości**.
8. W okno Właściwości ustaw następujące właściwości:
   1. Ustaw wartość **(nazwa)** , aby **zweryfikować dostępność środowiska uruchomieniowego VSTO 2010**.
   2. Zmień wartość **warunku** na **VSTORUNTIMEREDIST \> = "10.0.30319"**
   3. Pozostaw pustą właściwość **InstallUrl** .
   4. Ustaw **komunikat** dla **środowiska uruchomieniowego Visual Studio 2010 Tools for Office nie jest zainstalowany. Uruchom Setup.exe, aby zainstalować dodatek**.

        ![Zrzut ekranu okna właściwości dla stanu uruchamiania Sprawdź dostępność środowiska uruchomieniowego](media/setup-project-figure-8.jpg)

        **Ilustracja 8. okno właściwości dla stanu uruchomienia sprawdzania dostępności środowiska uruchomieniowego**

 Warunek uruchomienia powyżej jawnie sprawdza obecność środowiska uruchomieniowego programu VSTO, gdy jest on instalowany przez pakiet programu inicjującego.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Skonfiguruj warunek uruchamiania w celu wykrycia środowiska uruchomieniowego programu VSTO zainstalowanego przez pakiet Office

1. W edytorze **warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy **maszynę docelową wyszukiwania**, a następnie kliknij polecenie **Dodaj przeszukiwanie rejestru**.
2. Wybierz warunek wyszukiwania **RegistryEntry1** , kliknij prawym przyciskiem myszy warunek, a następnie wybierz **okno właściwości**.
3. W oknie **Właściwości** ustaw następujące właściwości:
    1. Ustaw wartość **(nazwa)** , aby **wyszukać środowisko uruchomieniowe programu Office VSTO**.
    2. Zmień wartość **Właściwości** na **OfficeRuntime**.
    3. Ustaw wartość **klucz rejestru** na **oprogramowanie \\ Microsoft \\ VSTO uruchomieniowe Setup \\ v4**.
    4. Pozostaw Właściwość **root** ustawioną na wartość **vsdrrHKLM**.
    5. Zmień właściwość **Value** na **Version**.

4. W edytorze **warunki uruchamiania (OfficeAddInSetup)** zaznacz wcześniej warunek uruchamiania **Sprawdź dostępność programu VSTO 2010 w środowisku uruchomieniowym** , kliknij prawym przyciskiem myszy warunek, a następnie wybierz polecenie **Właściwości okno**.

5. Zmień wartość właściwości **Condition** na **VSTORUNTIMEREDIST \> = "10.0.30319" lub OFFICERUNTIME \> = "10.0.21022"**. Numery wersji może się różnić w zależności od wersji środowiska uruchomieniowego, które są wymagane przez dodatek.

    ![Zrzut ekranu przedstawiający właściwości systemu Windows dla warunku uruchamiania](media/setup-project-figure-9.jpg)
  
    **Rysunek 9. okna właściwości sprawdzania dostępności środowiska uruchomieniowego za pomocą programu Redist lub warunku uruchomienia pakietu Office**

Jeśli elementy docelowe dodatku .NET Framework 4 lub nowsze, typy wewnątrz podstawowych zestawów międzyoperacyjnych (PIA), do których istnieją odwołania, mogą zostać osadzone w zestawie narzędzi VSTO.

Aby sprawdzić, czy typy międzyoperacyjności będą osadzone w dodatku, wykonaj następujące czynności:

1. Rozwiń węzeł odwołania w Eksplorator rozwiązań
2. Wybierz jedno z odwołań PIA, na przykład **Office**.
3. Wyświetl okna właściwości, naciskając klawisz F4 lub wybierając pozycję Właściwości z menu kontekstowego zestawy.
4. Sprawdź wartość właściwości **Osadź typy międzyoperacyjności**.

Jeśli wartość jest równa **true**, typy są osadzane i można przejść do sekcji, [**Aby utworzyć projekt Instalatora**](#to-build-the-setup-project) .

Aby uzyskać więcej informacji, zobacz [równoważność typów i osadzone typy międzyoperacyjnych](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types)

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Aby skonfigurować warunki uruchamiania w celu wykrycia, że dla pakietu Office zestawów PIA

1. W edytorze **warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy pozycję **wymagania na komputerze docelowym**, a następnie **kliknij polecenie Dodaj Instalator Windows warunek uruchomienia**. Ten warunek uruchomienia wyszukuje zestaw PIA pakietu Office przez wyszukiwanie określonego identyfikatora składnika.
2. Kliknij prawym przyciskiem myszy pozycję **Wyszukaj Component1** , a następnie kliknij pozycję **okno właściwości** , aby wyświetlić właściwości warunku uruchamiania.
3. W **oknie właściwości** ustaw następujące właściwości:

    1. Zmień wartość właściwości **(Name)** w celu **wyszukania udostępnionego PIA pakietu Office**
    2. Zmień wartość **ComponentID** na identyfikator składnika dla używanego składnika pakietu Office. Listę identyfikatorów składników można znaleźć w poniższej tabeli, na przykład **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**.
    3. Zmień wartość właściwości **Właściwości** na **HASSHAREDPIA**.

4. W edytorze **warunki uruchamiania (OfficeAddInSetup)** kliknij prawym przyciskiem myszy pozycję **Condition1** , a następnie kliknij pozycję **okno właściwości** , aby wyświetlić właściwości warunku uruchomienia.

5. Zmień te właściwości **Condition1**:

    1. Zmień wartość **(nazwa)** , aby **zweryfikować dostępność wspólnego PIA pakietu Office**.
    2. Zmień **warunek** na **HASSHAREDPIA**.
    3. Pozostaw puste pole **InstallUrl** .
    4. Zmiana **komunikatu** na **składnik wymagany do współdziałania z programem Excel jest niedostępna. Uruchom setup.exe**.

    ![Zrzut ekranu przedstawiający okno właściwości w celu sprawdzenia warunku uruchomienia PIA dla pakietu Office](media/setup-project-figure-10.jpg)
  
    **Rysunek 10. okno właściwości dla sprawdzenia warunku uruchomienia PIA dla pakietu Office**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Identyfikatory składników podstawowych zestawów międzyoperacyjnych dla Microsoft Office

|Podstawowy zestaw międzyoperacyjny|Office 2010|Office 2013|Pakiet Office 2013 (64-bitowy)|Office 2016|Pakiet Office 2016 (64-bitowy)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2,0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Tag inteligentny|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Udostępnianie pakietu Office|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|Project|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![Zrzut ekranu przedstawiający końcowe warunki uruchamiania](media/setup-project-figure-11.jpg)

  **Ilustracja 11. ostateczne warunki uruchamiania**

Można dokładniej zawęzić warunki uruchamiania instalacji usługi ExcelAddIn. Może być na przykład przydatne do sprawdzenia, czy rzeczywista docelowa aplikacja pakietu Office jest zainstalowana.

### <a name="to-build-the-setup-project"></a>Aby skompilować projekt instalacyjny

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **OfficeAddInSetup** , a następnie kliknij pozycję **Kompiluj**.
2. Korzystając z **Eksploratora Windows**, przejdź do katalogu wyjściowego projektu **OfficeAddInSetup** i przejdź do folderu wersja lub Debuguj, w zależności od wybranej konfiguracji kompilacji. Skopiuj wszystkie pliki z folderu do lokalizacji, do której użytkownicy mogą uzyskać dostęp.

Aby przetestować konfigurację ExcelAddIn

1. Przejdź do lokalizacji, do której skopiowano **OfficeAddInSetup** .
2. Kliknij dwukrotnie plik setup.exe, aby zainstalować dodatek **OfficeAddInSetup** . Zaakceptuj wszelkie wyświetlane postanowienia licencyjne dotyczące oprogramowania, a następnie Ukończ pracę Kreatora instalacji dodatku na komputerze użytkownika.

Rozwiązanie Office Excel należy zainstalować i uruchomić z lokalizacji określonej podczas instalacji.

## <a name="additional-requirements-for-document-level-solutions"></a>Dodatkowe wymagania dotyczące rozwiązań na poziomie dokumentu

Wdrażanie rozwiązań na poziomie dokumentu wymaga wykonania kilku różnych czynności konfiguracyjnych w projekcie konfiguracji Instalator Windows.

Poniżej przedstawiono listę podstawowych kroków wymaganych do wdrożenia rozwiązania na poziomie dokumentu:

- Utwórz projekt Instalatora programu Visual Studio.
- Dodaj podstawowe dane wyjściowe rozwiązania na poziomie dokumentu. Główne wyjście zawiera również dokument Microsoft Office.
- Dodaj manifesty wdrożenia i aplikacji jako luźne pliki.
- Wyklucz składniki zależne z pakietu Instalatora (z wyjątkiem zestawów narzędzi).
- Skonfiguruj wstępnie wymagane pakiety.
- Skonfiguruj warunki uruchamiania.
- Utwórz projekt konfiguracji i skopiuj wyniki do lokalizacji wdrożenia.
- Wdróż rozwiązanie na poziomie dokumentu na komputerze użytkownika, wykonując konfigurację.
- W razie konieczności zaktualizuj niestandardowe właściwości dokumentu.

### <a name="changing-the-location-of-the-deployed-document"></a>Zmiana lokalizacji wdrożonego dokumentu

Właściwości wewnątrz dokumentu pakietu Office służą do lokalizowania rozwiązań na poziomie dokumentu. Jeśli dokument jest zainstalowany w tym samym folderze co zestaw narzędzi VSTO, nie są wymagane żadne zmiany. Jeśli jednak jest zainstalowana w innym folderze, te właściwości będą musiały zostać zaktualizowane podczas instalacji.

Aby uzyskać więcej informacji o tych właściwościach dokumentu, zobacz [niestandardowe właściwości dokumentu — Omówienie](custom-document-properties-overview.md).

Aby zmienić te właściwości, należy użyć akcji niestandardowej podczas instalacji.

W poniższym przykładzie jest stosowane rozwiązanie poziomu dokumentu o nazwie ExcelWorkbookProject i projekt konfiguracji o nazwie ExcelWorkbookSetup. Projekt ExcelWorkbookSetup jest konfigurowany przy użyciu tych samych kroków opisanych powyżej, z wyjątkiem ustawiania kluczy rejestru.

Aby dodać projekt akcji niestandardowej do rozwiązania programu Visual Studio

1. Dodaj nowy projekt konsoli .NET do rozwiązania, klikając prawym przyciskiem myszy **projekt wdrożenia dokumentu pakietu Office** w **Eksplorator rozwiązań**
2. Rozwiń węzeł **Dodaj** i kliknij pozycję **Nowy projekt**.
3. Wybierz szablon aplikacja konsoli i nadaj nazwę projektowi **AddCustomizationCustomAction**.

    ![Zrzut ekranu przedstawiający Eksplorator rozwiązań AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **Rysunek 12. Eksplorator rozwiązań — AddCustomizationCustomAction**

4. Dodaj odwołanie do tych zestawów:
    1. System. ComponentModel
    2. System.Configwersja. Zainstaluj
    3. Microsoft. VisualStudio. Tools. Applications
    4. Microsoft. VisualStudio. Tools. Applications. ServerDocument

5. Skopiuj ten kod do Program.cs lub program. vb

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

Aby dodać dostosowanie do dokumentu, musisz mieć identyfikator rozwiązania dla rozwiązania na poziomie dokumentu programu VSTO. Ta wartość jest pobierana z pliku projektu programu Visual Studio.

Aby pobrać identyfikator rozwiązania

1. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie** , aby skompilować rozwiązanie na poziomie dokumentu, a następnie Dodaj właściwość identyfikator rozwiązania do pliku projektu.
2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt na poziomie dokumentu **ExcelWorkbookProject**
3. Kliknij pozycję **UnloadProject** , aby uzyskać dostęp do pliku projektu z programu Visual Studio.

    ![Zrzut ekranu przedstawiający Eksplorator rozwiązań rozładowywanie rozwiązania dokumentu programu Excel](media/setup-project-figure-16.jpg)

    **Ilustracja 13. rozładowywanie rozwiązania dokumentu programu Excel**

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookProject** , a następnie kliknij pozycję **EditExcelWorkbookProject. vbproj** lub **Edytuj ExcelWorkbookProject. csproj**.
5. W edytorze **ExcelWorkbookProject** Znajdź element **solutionId** wewnątrz elementu **Właściwości** .
6. Skopiuj wartość identyfikatora GUID tego elementu.

    ![Pobieranie SolutionID](media/setup-project-figure-17.jpg)

    **Ilustracja 14. Pobieranie SolutionID**

7. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookProject** , a następnie kliknij pozycję **Załaduj ponownie projekt**.
8. Kliknij przycisk **tak** w wyświetlonym oknie dialogowym, aby zamknąć Edytor **ExcelWorkbookProject** .
9. **Identyfikator rozwiązania** zostanie użyty w akcji Zainstaluj niestandardową.

Ostatnim krokiem jest skonfigurowanie akcji niestandardowej dla kroków **instalacji** i **dezinstalacji** .

### <a name="to-configure-the-setup-project"></a>Aby skonfigurować projekt instalacyjny

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookSetup**, rozwiń węzeł **Dodaj** i kliknij pozycję **dane wyjściowe projektu**.
2. W oknie dialogowym **Dodaj grupę wyjściową projektu** , na liście **projekt** kliknij pozycję **AddCustomizationCustomAction**.
3. Wybierz pozycję **podstawowe dane wyjściowe** , a następnie kliknij przycisk **OK** , aby zamknąć okno dialogowe i dodać zestaw zawierający akcję niestandardową do projektu Instalatora.

    ![Zrzut ekranu akcji niestandardowej manifestu dokumentu — okno Dodaj grupę wyjściową projektu](media/setup-project-figure-18.jpg)

    **Ilustracja 15. akcja niestandardowa manifestu dokumentu — Dodaj grupę wyjściową projektu**

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ExcelWorkbookSetup**.
5. Rozwiń węzeł **Widok** i kliknij pozycję **Akcje niestandardowe**.
6. W edytorze **Akcje niestandardowe (ExcelWorkbookSetup)** kliknij prawym przyciskiem myszy **Akcje niestandardowe** i kliknij polecenie **Dodaj akcję niestandardową**.
7. W oknie dialogowym **Wybierz element w projekcie** , na liście **Szukaj w** kliknij pozycję **folder aplikacji**. Wybierz pozycję **podstawowe wyjście z AddCustomizationCustomAction (aktywny)** , a następnie kliknij przycisk **OK** , aby dodać akcję niestandardową do kroku instalacji.
8. W **węźle instalacja** kliknij prawym przyciskiem myszy pozycję **podstawowe dane wyjściowe z AddCustomizationCustomAction (aktywny)**, a następnie kliknij polecenie **Zmień nazwę**. Nadaj nazwę akcji niestandardowej **Kopiuj dokument do folderu Moje dokumenty i Dołącz dostosowanie**.
9. W **węźle Odinstaluj** kliknij prawym przyciskiem myszy pozycję **podstawowe dane wyjściowe z AddCustomizationCustomAction (aktywny)** i kliknij polecenie **Zmień nazwę**. Nadaj nazwę akcji niestandardowej **Usuń dokument z folderu dokumenty**.

    ![Zrzut ekranu okna akcji niestandardowych manifestu dokumentu](media/setup-project-figure-19.jpg)

    **Ilustracja 16. akcje niestandardowe manifestu dokumentu**

10. W edytorze **Akcje niestandardowe (ExcelWorkbookSetup)** kliknij prawym przyciskiem myszy pozycję **Kopiuj dokument do folderu Moje dokumenty i Dołącz dostosowanie** i kliknij polecenie **okno właściwości**.
11. W oknie  **Właściwości** CustomActionData wprowadź lokalizację biblioteki DLL dostosowania, manifest wdrożenia i lokalizację dokumentu Microsoft Office. Wymagany jest również SolutionID.
12. Jeśli chcesz rejestrować błędy instalacji do pliku, Dołącz parametr LogFile.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![Zrzut ekranu akcji niestandardowej w celu skopiowania dokumentu do folderu Moje dokumenty okno Właściwości](media/setup-project-figure-20.jpg)

    **Ilustracja 17. akcja niestandardowa w celu skopiowania dokumentu do folderu Moje dokumenty**

13. Akcja niestandardowa dla odinstalowania wymaga nazwy dokumentu, można podać, że przy użyciu tego samego parametru documentLocation w **CustomActionData**

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. Kompiluj i Wdróż projekt **ExcelWorkbookSetup** .
15. Wyszukaj w folderze **Moje dokumenty** i otwórz plik ExcelWorkbookProject.xlsx.

## <a name="additional-resources"></a>Dodatkowe zasoby

[Instrukcje: Instalowanie Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Podstawowe zestawy międzyoperacyjne pakietu Office](office-primary-interop-assemblies.md)

[Wpisy rejestru dotyczące dodatków narzędzi VSTO](registry-entries-for-vsto-add-ins.md)

[Niestandardowe właściwości dokumentu ― Omówienie](custom-document-properties-overview.md)

[Określanie regionów formularzy w rejestrze systemu Windows](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[Udzielanie zaufania do dokumentów](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>Informacje o autorze

Wouter van vugt to firma Microsoft MVP z technologiami Office Open XML i niezależnym konsultantem skupiającym się na tworzeniu pakietu Office Business Applications (OBAs) z programem SharePoint, Microsoft Office i pokrewnymi technologiami platformy .NET.
Wouter to częste współautor dla witryn społeczności deweloperów, takich jak [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12)). Opublikowanie kilku oficjalnych dokumentów i artykułów jest również książkami dostępnymi w wierszu zatytułowanym Open XML: wyjaśnienie książki elektronicznej.
Wouter to założyciela kodu — firma holenderska, która koncentruje się na dostarczaniu zawartości technicznej do wycinania z różnych kanałów. Więcej informacji na temat Wouter można znaleźć w blogu.

Ted Pattison to program SharePoint MVP, autor, trainer i założyciel grupy Ted Pattison. W odniesieniu do 2005 Ted został zatrudniony przez firmę Microsoft Developer platform propagator Group, aby utworzyć program Windows SharePoint Services 3,0 i Microsoft Office SharePoint Server 2007. Od tego czasu Ted został całkowicie skoncentrowany na analizie profesjonalnych deweloperów korzystających z technologii SharePoint 2007. Ted zakończył pisanie książki dla Microsoft Press zatytułowanej w programie Windows SharePoint Services 3,0, który koncentruje się na sposobie używania programu SharePoint jako platformy deweloperskiej do tworzenia rozwiązań dla firm. Ted również zapisuje kolumnę priorytetową dla deweloperów w witrynie MSDN Magazine z tytułem.
