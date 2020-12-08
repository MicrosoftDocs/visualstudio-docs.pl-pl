---
title: Wdróż rozwiązanie pakietu Office przy użyciu Instalator Windows
description: Informacje na temat tworzenia Instalator Windows można wdrożyć za pomocą programu Visual Studio, które wymaga dostępu administracyjnego na komputerze użytkownika końcowego.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
ms.openlocfilehash: c001b3ce308c9e991cee747bdcab3ad646b226ab
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847120"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Wdróż rozwiązanie pakietu Office przy użyciu Instalator Windows

Dowiedz się, jak utworzyć Instalator Windows dla rozwiązania pakietu Office przy użyciu programu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

Za pomocą programu Visual Studio do tworzenia Instalator Windows można wdrożyć rozwiązanie pakietu Office, które wymaga dostępu administracyjnego na komputerze użytkownika końcowego. Na przykład można użyć takiego pliku, aby zainstalować rozwiązanie tylko raz dla wszystkich użytkowników komputera. Możesz również wdrożyć rozwiązanie pakietu Office przy użyciu technologii ClickOnce, ale to rozwiązanie musi być zainstalowane osobno dla każdego użytkownika komputera.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-topic"></a>W tym temacie:

- [Pobierz przykłady dodatków VSTO](#Download)

- [Pobierz InstallShield Limited Edition](#Obtain)

- [Zdecyduj, jak udzielić zaufania do rozwiązania](#ApplySecurity)

- [Tworzenie projektu konfiguracji](#Create)

- [Dodawanie danych wyjściowych projektu](#Add)

- [Dodawanie manifestów wdrożenia i aplikacji](#AddD)

- [Skonfiguruj składniki zależne jako wymagania wstępne](#Configure)

- [Określ, gdzie chcesz wdrożyć rozwiązanie na komputerze użytkownika](#Location)

- [Konfigurowanie dodatku narzędzi VSTO](#ConfigureRegistry)

- [Skonfiguruj dostosowanie na poziomie dokumentu](#ConfigureDocument)

- [Tworzenie projektu Instalatora](#Build)

Aby uzyskać więcej informacji na temat wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce, zobacz [wdrażanie rozwiązania z pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

Informacje o sposobach tworzenia pliku Instalator Windows przy użyciu programu [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] znajdują się w temacie [Deploy a Visual Studio 2010 Tools for Office rozwiązanie przy użyciu Instalator Windows](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10)).

## <a name="download-samples"></a><a name="Download"></a>Pobierz przykłady
Ten temat odnosi się do następujących próbek do pobrania.

|Sample<br /><br />|Opis<br /><br />|
|----------|---------------|
|[ExcelAddIn](https://code.msdn.microsoft.com/VSTO-Deploy-an-Office-fbcc09ad)<br /><br />|Dodatek narzędzi VSTO dla programu Excel, który można zainstalować na komputerze z uruchomioną 32-bitową lub 64-bitową wersją pakietu Office.<br /><br />|
|[ExcelWorkbook](https://code.msdn.microsoft.com/VSTO-Deploy-a-Customization-f70fae33)<br /><br />|Dostosowanie na poziomie dokumentu programu Excel, które można zainstalować na komputerze z uruchomioną 32-bitową lub 64-bitową wersją pakietu Office.<br /><br />|

## <a name="decide-how-to-grant-trust-to-the-solution"></a><a name="ApplySecurity"></a>Zdecyduj, jak udzielić zaufania do rozwiązania
Aby można było uruchomić rozwiązanie na komputerach użytkowników, należy udzielić zaufania w jeden z następujących sposobów lub użytkownicy muszą odpowiedzieć na monit zaufania podczas instalacji rozwiązania.

- Podpisz manifesty przy użyciu certyfikatu, który identyfikuje znanego i zaufanego wydawcę. Aby uzyskać więcej informacji, zobacz temat [ufanie rozwiązaniu przez podpisywanie manifestów aplikacji i wdrażania](../vsto/granting-trust-to-office-solutions.md#Signing).

- Zainstaluj rozwiązanie w katalogu Program Files na komputerze użytkownika.

> [!NOTE]
> W przypadku dostosowań na poziomie dokumentu, lokalizacja dokumentu musi być również zaufana. Aby uzyskać więcej informacji, zobacz [przyznawanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="get-installshield-limited-edition"></a><a name="Obtain"></a>Pobierz InstallShield Limited Edition

Plik Instalator Windows można utworzyć przy użyciu narzędzia InstallShield Limited Edition (wyspa), które jest bezpłatne, jeśli zainstalowano program Visual Studio. ISLE zastępuje funkcje szablonów projektu na potrzeby instalacji i wdrożenia, które są oferowane przez poprzednie wersje programu Visual Studio.

### <a name="to-get-installshield-limited-edition"></a>Aby uzyskać InstallShield Limited Edition

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

   Zostanie otwarte okno dialogowe **Nowy projekt** .

2. W okienku szablony rozwiń pozycję **Inne typy projektów**, a następnie wybierz szablon **Konfiguracja i wdrożenie** .

3. Na liście typów projektów na potrzeby **instalacji i wdrażania** wybierz opcję **Włącz InstallShield Limited Edition**, a następnie wybierz przycisk **OK** .

   Zostanie wyświetlona strona zawierająca informacje o sposobie pobrania programu InstallShield Limited Edition.

4. Na tej stronie wybierz łącze **Przejdź do witryny pobierania** .

5. Na stronie pobierania dla programu InstallShield Limited Edition wprowadź wymagane informacje w odpowiednich polach, a następnie wybierz link **Pobierz teraz** .

   Po pobraniu, zainstalowaniu i aktywowaniu produktu szablon **programu InstallShield Limited Edition** jest wyświetlany w programie Visual Studio.

## <a name="create-a-setup-project"></a><a name="Create"></a>Tworzenie projektu konfiguracji

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwórz projekt pakietu Office, który chcesz wdrożyć.

   Przykłady dodatków narzędzi VSTO, które są skojarzone z tym tematem, zawierają projekt o nazwie **ExcelAddIn**. Przykłady dostosowania na poziomie dokumentu zawierają projekt o nazwie **ExcelWorkbook**. Ten temat będzie odnosił się do projektu pakietu Office w rozwiązaniu przy użyciu jednej z tych dwóch nazw.

2. Na pasku menu wybierz polecenie **plik**  >  **Dodaj**  >  **Nowy projekt**.

   Zostanie otwarte okno dialogowe **Dodaj nowy projekt** .

3. W okienku szablony rozwiń pozycję **Inne typy projektów**, a następnie wybierz szablon **Konfiguracja i wdrożenie** .

4. Na liście typów projektów na potrzeby **instalacji i wdrażania** wybierz opcję **projekt InstallShield Limited Edition**, nazwij projekt, a następnie wybierz przycisk **OK** .

   Utworzony projekt instalacji InstallShield zostanie wyświetlony w rozwiązaniu.

   Przykłady dla tego tematu zawierają projekt konfiguracji o nazwie **OfficeAddInSetup**. Ten temat będzie odnosił się do projektu konfiguracji w rozwiązaniu przy użyciu tej samej nazwy.

## <a name="add-the-project-output"></a><a name="Add"></a>Dodawanie danych wyjściowych projektu

Projekt **OfficeAddInSetup** można skonfigurować tak, aby zawierał dane wyjściowe projektu pakietu Office. W przypadku projektów dodatku VSTO dane wyjściowe projektu są tylko zestawem rozwiązania. W przypadku projektów dostosowania na poziomie dokumentu dane wyjściowe projektu zawierają nie tylko zestaw rozwiązań, ale również sam dokument.

### <a name="to-add-the-project-output"></a>Aby dodać dane wyjściowe projektu

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup** , a następnie wybierz plik **Asystenta projektu** , który przedstawiono na poniższej ilustracji.

   ![Plik Asystenta projektu w Eksplorator rozwiązań](../vsto/media/installshield-projectassistant.png "Plik Asystenta projektu w Eksplorator rozwiązań")

2. Na pasku menu wybierz **Widok**  >  **Otwórz**.

3. W dolnej części strony **Asystenta projektu** wybierz przycisk **pliki aplikacji** , który pokazuje poniższą ilustrację.

   ![Przycisk pliki aplikacji.](../vsto/media/installshield-applicationfiles.png "Przycisk pliki aplikacji.")

4. Na stronie **pliki aplikacji** wybierz przycisk Dodaj dane **wyjściowe projektu** .

5. W oknie dialogowym **Selektor danych wyjściowych programu Visual Studio** zaznacz pole wyboru **podstawowe dane wyjściowe** , a następnie wybierz przycisk **OK** .

## <a name="add-the-deployment-and-application-manifests"></a><a name="AddD"></a>Dodawanie manifestów wdrożenia i aplikacji

1. Na stronie **pliki aplikacji** wybierz przycisk **Dodaj pliki** .

2. W oknie dialogowym **Otwórz** przejdź do katalogu wyjściowego projektu **ExcelAddIn** .

   Zazwyczaj katalog wyjściowy jest podfolderem **bin\Release** katalogu głównego projektu, w zależności od wybranej konfiguracji kompilacji.

3. W katalogu danych wyjściowych wybierz pliki **ExcelAddIn. VSTO** i **ExcelAddIn.dll. manifest** , a następnie wybierz przycisk **Otwórz** .

   Strona **pliki aplikacji** zawiera teraz plik wyjściowy projektu, manifest wdrożenia i manifest aplikacji, jak pokazano na poniższej ilustracji.

   ![Pliki wyjściowe projektu Instalatora.](../vsto/media/installshield-outputfiles.png "Pliki wyjściowe projektu Instalatora.")

## <a name="configure-the-dependent-components-as-prerequisites"></a><a name="Configure"></a>Skonfiguruj składniki zależne jako wymagania wstępne

W aplikacji Instalatora należy uwzględnić nie tylko poniższe składniki, ale również inne składniki, które są wymagane do działania Twojego rozwiązania.

- Wersja .NET Framework, do której odwołuje się rozwiązanie pakietu Office.

- Narzędzia Microsoft Visual Studio 2010 Tools for Office Runtime.

### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Dodaj .NET Framework 4 lub .NET Framework 4,5 jako warunek wstępny

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup** , rozwiń węzeł **Określ dane aplikacji** , a następnie wybierz plik **redystrybucyjny** , który przedstawiono na poniższej ilustracji.

   ![Plik redystrybucyjny w Eksplorator rozwiązań](../vsto/media/installshield-redistributablesfile.png "Plik redystrybucyjny w Eksplorator rozwiązań")

2. Na pasku menu wybierz **Widok**  >  **Otwórz**.

   Zostanie otwarta strona **redystrybucyjne** .

3. Na liście składników redystrybucyjnych zaznacz odpowiednie pole wyboru dla wersji .NET Framework, do której odwołuje się rozwiązanie.

   Na przykład, jeśli rozwiązanie jest przeznaczone dla programu [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , zaznacz pole wyboru **Microsoft .NET Framework 4,5** . Może pojawić się okno dialogowe z pytaniem, czy chcesz zainstalować składnik redystrybucyjny, którego wymaga program InstallShield, zanim będzie można dodać składnik jako warunek wstępny. Jeśli to okno dialogowe nie zostanie wyświetlone, składnik już istnieje na komputerze.

4. Jeśli to okno dialogowe zostanie wyświetlone, wybierz przycisk **nie** .

### <a name="add-the-visual-studio-2010-tools-for-office-runtime"></a><a name="AddToolsForOffice"></a>Dodaj Visual Studio 2010 Tools dla pakietu Office Runtime

Strona **redystrybucyjna** zawiera element o nazwie **Microsoft VSTO 2010 Runtime**, ale odwołuje się do starszej wersji środowiska uruchomieniowego. W związku z tym można ręcznie utworzyć plik konfiguracji, który odwołuje się do najnowszej wersji. Następnie należy umieścić ten plik w tym samym katalogu, w którym znajdują się pliki konfiguracji dla wszystkich innych elementów, które pojawiają się na stronie **redystrybucyjne** .

#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Aby dodać program Visual Studio 2010 Tools for Office Runtime jako warunek wstępny

1. Otwórz Notatnik, a następnie wklej następujący kod XML do pliku tekstowego.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <SetupPrereq>
   <conditions>
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>
   </conditions>
   <files>
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>
   </files>
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">
   </execute>
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>

   </SetupPrereq>
   ```

2. Wygeneruj identyfikator GUID w programie Visual Studio. W menu **Narzędzia** wybierz polecenie **Utwórz identyfikator GUID**.

3. W programie **Generator GUID** wybierz przycisk opcji **Format rejestru** , wybierz przycisk **Kopiuj** , a następnie wybierz przycisk **Zakończ** .

4. W Notatniku Zastąp tekst, w którym znajduje się **Identyfikator GUID** , WKLEJAJĄC identyfikator GUID w jego miejscu.

   Element **&lt; właściwości &gt;** pliku jest podobny do poniższego.

   ```xml
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>
   ```

5. Na pasku menu w Notatniku wybierz **plik**  >  **Zapisz**.

6. W oknie dialogowym **Zapisywanie jako** przejdź do folderu **pulpit** .

7. Na liście **Zapisz jako typ** wybierz pozycję **wszystkie pliki (&#42;. &#42;)**.

8. W polu **Nazwa pliku** wprowadź **program Visual Studio 2010 Tools for Office Runtime. prq**, a następnie wybierz przycisk **Zapisz** .

   > [!NOTE]
   > Upewnij się, że na końcu nazwy pliku została dodana wartość **. prq** , aby zidentyfikować ten plik jako plik wymagań wstępnych.

9. Zamknij Notatnik.

10. Z folderu **pulpitu** Skopiuj plik *Runtime. prq narzędzi programu Visual Studio 2010* do jednego z następujących katalogów na komputerze.

   W przypadku 32-bitowych systemów operacyjnych *: \\ %ProgramFiles%\InstallShield\2013LE\SetupPrerequisites*

   W przypadku 64-bitowych systemów operacyjnych: *% ProgramFiles (x86)% \ 2013LE \ \\ SetupPrerequisites*

11. Na stronie **redystrybucyjna** projektu InstallShield wybierz przycisk **Odśwież** , aby odświeżyć listę składników redystrybucyjnych, jak pokazano na poniższej ilustracji.

   ![Przycisk Odśwież.](../vsto/media/installshield-refreshbutton.png "Przycisk Odśwież.")

12. Na liście składników redystrybucyjnych zaznacz pole wyboru **Visual Studio 2010 Tools for Office Runtime** .

   Może pojawić się okno dialogowe z pytaniem, czy chcesz zainstalować składnik redystrybucyjny. Jeśli to okno dialogowe nie zostanie wyświetlone, możesz przejść do sekcji [Określanie, gdzie chcesz wdrożyć rozwiązanie na komputerze użytkownika](#Location) w tym temacie.

13. Jeśli to okno dialogowe zostanie wyświetlone, wybierz przycisk **nie** .

## <a name="specify-where-to-install-the-solution-on-the-users-computer"></a><a name="Location"></a>Określ, gdzie zainstalować rozwiązanie na komputerze użytkownika

1. W **Eksplorator rozwiązań** rozwiń węzeł **OfficeAddInSetup** , rozwiń węzeł **Organizuj ustawienia** , a następnie wybierz plik **Informacje ogólne** .

2. Na pasku menu wybierz **Widok**  >  **Otwórz**.

3. Na liście właściwości wybierz przycisk **Przeglądaj** obok właściwości **INSTALLDIR** .

4. W oknie dialogowym **Ustaw INSTALLDIR** wybierz folder na komputerze użytkownika, na którym chcesz zainstalować rozwiązanie.

   > [!NOTE]
   > Możesz również utworzyć podkatalogi w oknie dialogowym **Ustaw INSTALLDIR** , otwierając menu skrótów dla każdego folderu na liście.

## <a name="configure-a-vsto-add-in"></a><a name="ConfigureRegistry"></a>Konfigurowanie dodatku narzędzi VSTO

Możesz określić, czy dodatek VSTO ma być zainstalowany dla wszystkich użytkowników komputera (na komputer), czy tylko dla użytkownika wykonującego instalację (na użytkownika).

Jeśli chcesz obsługiwać instalacje dla poszczególnych komputerów, Utwórz dwa osobne Instalatory. Instalatory można podzielić na podstawie wersji pakietu Office (32-bitowej i 64-bitowej) lub w wersji systemu Windows (32-bit i 64-bit), która jest uruchomiona przez użytkownika.

Instalacje dla poszczególnych użytkowników wymagają tylko jednego Instalatora, niezależnie od wersji pakietu Office lub systemu Windows.

> [!NOTE]
> Ta sekcja ma zastosowanie tylko w przypadku wdrażania dodatku VSTO. Jeśli wdrażasz dostosowanie na poziomie dokumentu, możesz od razu przejść do sekcji [Konfigurowanie dostosowania na poziomie dokumentu](#ConfigureDocument) .

### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Aby określić, czy mają być obsługiwane instalacje dla poszczególnych użytkowników i komputerów

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup** , rozwiń węzeł **Organizuj ustawienia** , a następnie wybierz plik **Informacje ogólne** .

2. Na pasku menu wybierz **Widok**  >  **Otwórz**.

   Pojawią się właściwości projektu instalacyjnego.

3. Na liście właściwości **AllUSERS** Określ, czy to rozwiązanie ma być zainstalowane dla wszystkich użytkowników komputera, czy tylko dla użytkownika, który instaluje rozwiązanie.

   Aby zainstalować dodatek VSTO dla bieżącego użytkownika, wybierz **AllUsers = "" (instalacja na użytkownika)**. Aby zainstalować dodatek VSTO dla wszystkich użytkowników komputera, wybierz **ALLUSERS = 1 (instalacja na komputer)**

   W następnej procedurze utworzysz klucze rejestru, aby umożliwić aplikacji pakietu Office odnajdywanie i ładowanie dodatku VSTO. Zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-create-registry-keys"></a>Aby utworzyć klucze rejestru

1. W **Eksplorator rozwiązań** wybierz węzeł **Asystent projektu** .

   Na pasku menu wybierz **Widok**  >  **Otwórz**.

2. W dolnej części strony **Asystenta projektu** wybierz przycisk **Rejestr aplikacji** , który pokazuje poniższą ilustrację.

   ![Przycisk rejestr aplikacji.](../vsto/media/installshield-applicationregistry.gif "Przycisk rejestr aplikacji.")

   Zostanie wyświetlona strona **Rejestr aplikacji** .

3. W obszarze **czy chcesz skonfigurować dane rejestru, które będą instalowane przez aplikację?**, wybierz przycisk opcji **tak** .

4. Na liście **widok rejestru komputera docelowego** Dodaj hierarchię kluczy, która włącza typ Instalatora, który ma zostać utworzony.

   Ścieżka skonfigurowana w tej sekcji zależy od tego, czy tworzysz Instalatora dla poszczególnych użytkowników, czy Instalatora dla poszczególnych komputerów.

   **Instalator dla poszczególnych użytkowników**

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**

   **Instalatory dla komputera na podstawie wersji pakietu Office**

| Wersja pakietu Office<br /><br /> | Ścieżka konfiguracji InstallShield<br /><br /> |
|----------------------------| - |
| 32-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Instalatory dla komputera na podstawie wersji systemu Windows**

| Wersja systemu Windows<br /><br /> | Ścieżka konfiguracji InstallShield<br /><br /> |
|-----------------------------| - |
| 32-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]
   > Instalator programu dla 64-bitowego systemu Windows wymaga dwóch ścieżek rejestru, ponieważ jest możliwe, aby użytkownicy uruchamiali 32-bitowe i 64-bitowe wersje pakietu Office na komputerze z systemem 64-bitowym.

   > [!NOTE]
   > Najlepszym rozwiązaniem jest rozpoczęcie pracy nazwy dodatku VSTO z nazwą firmy. Ta konwencja zwiększa prawdopodobieństwo, że klucz będzie unikatowy i zmniejsza prawdopodobieństwo konfliktu z dodatkiem narzędzia VSTO od innego dostawcy. Dodatki, które mają taką samą nazwę, mogą na przykład zastąpić wszystkie inne klucze rejestracji. Takie podejście nie może zagwarantować, że klucz będzie unikatowy, ale może zmniejszyć liczbę potencjalnych kolizji nazw.

5. Po utworzeniu hierarchii kluczy Otwórz menu skrótów dla klucza **klucza SampleCompany. ExcelAddIn** , wybierz pozycję **Nowy**, a następnie wybierz pozycję **wartość ciągu**.

   Nowa wartość ciągu zostanie wyświetlona na liście **danych rejestru na komputerze docelowym** . Nazwa wartości ciągu zostanie wyróżniona, aby można było zmienić jej nazwę.

6. Zmień nazwę wartości na **Description**.

7. Powtórz ten proces, aby utworzyć następujące wartości.

|Typ wartości<br /><br />|Nazwa<br /><br />|
|--------------|--------|
|Wartość ciągu<br /><br />|**FriendlyName**<br /><br />|
|Wartość DWORD<br /><br />|**LoadBehavior**<br /><br />|
|Wartość ciągu<br /><br />|**Manifestu**<br /><br />|

8. Otwórz menu skrótów dla wartości **Opis** , a następnie wybierz **Modyfikuj**.

   Zostanie wyświetlone okno dialogowe **Edytowanie danych** .

9. W polu tekstowym **dane wartości** wprowadź **dodatek demonstracji programu Excel**, a następnie wybierz przycisk **OK** .

   Ten opis jest wyświetlany, gdy użytkownik otwiera aplikację pakietu Office, otwiera okno dialogowe **Opcje** , a następnie w okienku **dodatków** wybiera dodatek narzędzi VSTO.

10. Otwórz menu skrótów dla wartości **FriendlyName** , a następnie wybierz **Modyfikuj**.

   Zostanie wyświetlone okno dialogowe **Edytowanie danych** .

11. W polu tekstowym **dane wartości** wprowadź **dodatek demonstracji programu Excel**, a następnie wybierz przycisk **OK** .

   Ten ciąg jest wyświetlany w oknie dialogowym **Dodatki COM** w aplikacji pakietu Office. Domyślnie wartość ciągu jest IDENTYFIKATORem dodatku VSTO.

12. Otwórz menu skrótów dla wartości **LoadBehavior** , a następnie wybierz **Modyfikuj**.

   Zostanie wyświetlone okno dialogowe **Edytowanie danych** .

13. W polu tekstowym **dane wartości** wprowadź **3**, a następnie wybierz przycisk **OK** .

   Wartość 3 ładuje dodatek VSTO podczas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat wartości LoadBehavior, zobacz [wpisy rejestru dla dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

14. Otwórz menu skrótów dla wartości **manifestu** , a następnie wybierz **Modyfikuj**.

   Zostanie wyświetlone okno dialogowe **Edytowanie danych** .

15. W polu tekstowym **dane wartości** wprowadź **plik:///[INSTALLDIR] ExcelAddIn. VSTO | vstolocal**, a następnie wybierz przycisk **OK** .

   Narzędzia Visual Studio 2010 Tools for Office Runtime używają tej ścieżki do lokalizowania manifestu wdrożenia. Część **[INSTALLDIR]** tej ścieżki jest makrem, które mapuje do właściwości **INSTALLDIR** na stronie właściwości **Informacje ogólne** w projekcie Instalatora InstallShield. Ta właściwość określa lokalizację na komputerze docelowym, w której ma zostać zainstalowany dodatek narzędzi VSTO. Sufiks **| vstolocal** gwarantuje, że Twoje rozwiązanie zostanie załadowane z folderu instalacji, a nie z pamięci podręcznej ClickOnce.

> [!IMPORTANT]
> W przypadku tworzenia niestandardowego regionu formularza w dodatku narzędzi VSTO dla programu Outlook należy utworzyć więcej wpisów rejestru w celu zarejestrowania regionu w programie Outlook. Aby uzyskać więcej informacji, zobacz [wpisy rejestru dla regionów formularzy programu Outlook](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).

## <a name="configure-a-document-level-customization"></a><a name="ConfigureDocument"></a>Skonfiguruj dostosowanie na poziomie dokumentu

Ta sekcja ma zastosowanie tylko wtedy, gdy wdrażasz dostosowanie na poziomie dokumentu. Jeśli wdrażasz dodatek VSTO, możesz przejść od razu do sekcji [kompilacja projektu instalacji](#Build) .

Dostosowania na poziomie dokumentu nie używają kluczy rejestru. Zamiast tego właściwości dokumentu niestandardowego zawierają lokalizację manifestu wdrożenia.

Aby zmodyfikować właściwości niestandardowe, należy utworzyć program, który usuwa dostosowanie na poziomie dokumentu z dokumentu, modyfikuje odpowiednie właściwości, a następnie dołącza dostosowania do dokumentu. Następnie utworzysz akcję niestandardową, która uruchamia program, i dodasz tę akcję do projektu Instalatora.

### <a name="to-create-a-program-that-modifies-document-properties"></a>Aby utworzyć program modyfikujący właściwości dokumentu

1. Na pasku menu wybierz polecenie **plik**  >  **Dodaj**  >  **Nowy projekt**.

   Pojawi się okno dialogowe **Dodaj nowy projekt** .

2. W okienku szablony w obszarze węzła dla języka, którego chcesz użyć, wybierz folder **Windows** .

3. Na liście typów projektów dla **systemu Windows** wybierz szablon **aplikacja konsoli** .

4. Nazwij projekt **SetExcelDocumentProperties**, a następnie wybierz przycisk **OK** .

5. W **Eksplorator rozwiązań** wybierz przycisk **Pokaż wszystkie pliki** , otwórz menu skrótów dla węzła projektu **SetExcelDocumentProperties** , a następnie wybierz **Dodaj odwołanie**.

6. W oknie dialogowym **Menedżer odwołań** wybierz kartę **rozszerzenia** , a następnie zaznacz pole wyboru obok następujących zestawów, a następnie wybierz przycisk **OK** .

   - Microsoft. VisualStudio. Tools. Applications. Runtime

   - Microsoft. VisualStudio. Tools. Applications. ServerDocument

7. W **Eksplorator rozwiązań** wybierz plik **program.cs** (dla aplikacji C#) lub plik **Module1. vb** (dla aplikacji Visual Basic).

8. Na pasku menu wybierz **Widok**  >  **Otwórz**.

9. Zastąp zawartość całego pliku następującym kodem.

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]

10. Kompiluj projekt.

### <a name="to-add-a-custom-action-that-runs-your-program"></a>Aby dodać akcję niestandardową, która uruchamia program

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup** , a następnie wybierz plik **Asystenta projektu** , który przedstawiono na poniższej ilustracji.

   ![Plik Asystenta projektu w Eksplorator rozwiązań](../vsto/media/installshield-projectassistant.png "Plik Asystenta projektu w Eksplorator rozwiązań")

2. Na pasku menu wybierz **Widok**  >  **Otwórz**.

3. W dolnej części strony **Asystenta projektu** wybierz przycisk **pliki aplikacji** , który pokazuje poniższą ilustrację.

   ![Przycisk pliki aplikacji.](../vsto/media/installshield-applicationfiles.png "Przycisk pliki aplikacji.")

4. Na stronie **pliki aplikacji** wybierz przycisk Dodaj dane **wyjściowe projektu** .

   Zostanie wyświetlone okno dialogowe **Selektor danych wyjściowych programu Visual Studio** .

5. W węźle **SetExcelDocumentProperties** zaznacz pole wyboru **podstawowe dane wyjściowe** , a następnie wybierz przycisk **OK** .

6. W **Eksplorator rozwiązań** w węźle **OfficeAddInSetup** rozwiń węzeł **Zdefiniuj wymagania instalacji i akcje** , a następnie wybierz folder **Akcje niestandardowe** .

7. Na pasku menu wybierz **Widok**  >  **Otwórz**.

   Lista zdarzeń pojawia się w okienku po stronie ekranu.

   > [!NOTE]
   > Tylko kilka zdarzeń, które pojawiają się na tej liście, są dostępne w programie InstallShield Limited Edition. W tej procedurze zostanie uruchomiony program przy użyciu zdarzenia **okna dialogowego po zakończeniu instalacji** .

8. Na liście zdarzeń w obszarze **Akcje niestandardowe podczas instalacji** Otwórz menu skrótów dla zdarzenia **okna dialogowego po zakończeniu instalacji** , a następnie wybierz polecenie **nowy plik exe**.

   Akcja niestandardowa o nazwie **NewCustomAction1** pojawia się w obszarze zdarzenia **okna dialogowego po pomyślnym zakończeniu instalacji** . Zestaw właściwości dla akcji niestandardowej pojawia się w okienku obok zdarzeń.

   > [!IMPORTANT]
   > Dwa **po zakończeniu instalacji zdarzenia okna dialogowego sukces** są wyświetlane na liście zdarzeń. Upewnij się, że wybrano wystąpienie zdarzenia **okna dialogowego po zakończeniu instalacji** , które jest wyświetlane w obszarze **Akcje niestandardowe** w węźle instalacja.

9. Na liście właściwości **lokalizacja źródłowa** wybierz opcję **zainstalowane z produktem**.

10. Wybierz przycisk **Przeglądaj** obok właściwości **Nazwa pliku** .

11. W oknie dialogowym **Przeglądaj w poszukiwaniu pliku docelowego** przejdź do pliku **SetExcelDocumentProperties. Primary. Output** , a następnie wybierz przycisk **Otwórz** .

    Lokalizacja tego pliku zależy od folderu określonego dla właściwości **INSTALLDIR** projektu Instalatora. Na przykład w przypadku ustawienia tej właściwości do folderu o nazwie **[osobistyfolder] DemoWorkbookApp** można znaleźć plik **SetExcelDocumentProperties. Primary. Output** , przechodząc do elementu **[folderprogramfiles] \DemoWorkbookApp**.

    W następnych kilku krokach otrzymasz Identyfikator rozwiązania dokumentu, a następnie przekażesz ten identyfikator jako parametr do aplikacji konsoli. Przejdziesz również do lokalizacji dokumentu, manifestu wdrażania i zestawu dokumentów.

12. Otwórz menu skrótów dla projektu **ExcelWorkbook** , a następnie wybierz polecenie **Otwórz folder w Eksploratorze Windows** lub **Otwórz folder w Eksploratorze plików, w** zależności od używanego systemu operacyjnego.

    Zostanie otwarty folder zawierający Twoje rozwiązanie.

13. Otwórz plik projektu rozwiązania w Notatniku. W przypadku projektów Visual Basic nazwa pliku to *ExcelWorkbook. vbproj*. W przypadku projektów C# Nazwa pliku to *ExcelWorkbook. csproj*.

14. W pliku projektu Wyszukaj element **&lt; solutionId &gt;** , skopiuj jego wartość do schowka, a następnie zamknij Notatnik.

    Ta wartość jest przekazywany do aplikacji konsoli jako parametr.

15. Na stronie właściwości **NewCustomAction1** ustaw właściwość **wiersza polecenia** na następujący wiersz tekstu.

   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"
   ```

16. Zastąp **Identyfikator rozwiązania** identyfikatorem, który został skopiowany do Schowka.

   > [!IMPORTANT]
   > Przetestuj Instalatora, aby sprawdzić, czy Aplikacja konsolowa, w której działa ta akcja niestandardowa, ma dostęp do dokumentów w katalogu [INSTALLDIR]. Niektóre katalogi na komputerze użytkownika mogą wymagać dostępu administracyjnego (na przykład katalogu Program Files). Jeśli wdrażasz swoje rozwiązanie w katalogu, który wymaga dostępu administracyjnego, należy otworzyć okno dialogowe **Właściwości** pliku *setup.exe* , wybrać kartę **zgodność** , a następnie zaznaczyć pole wyboru **Uruchom ten program jako administrator** przed rozpoczęciem dystrybucji Instalatora. Jeśli nie chcesz, aby użytkownicy mogli uruchamiać program instalacyjny z uprawnieniami administracyjnymi, ustaw właściwość [INSTALLDIR] na katalog, do którego użytkownik prawdopodobnie ma już dostęp, na przykład katalog **dokumentów** . Aby uzyskać więcej informacji, zobacz sekcję [Określanie, gdzie chcesz zainstalować rozwiązanie na komputerze użytkownika w](#Location) tym temacie.

## <a name="build-the-setup-project"></a><a name="Build"></a>Tworzenie projektu Instalatora

1. W **Eksplorator rozwiązań** rozwiń węzeł **przygotowanie do wydania** , a następnie wybierz plik **wydań** .

2. Na pasku menu wybierz **Widok**  >  **Otwórz**.

   Eksplorator **kompilacje** zostanie otwarty w okienku bocznym, dzięki czemu można wybrać typ wersji, którą chcesz utworzyć.

3. W Eksploratorze **kompilacji** wybierz folder **SingleImage** .

4. W okienku obok Eksploratora **kompilacje** wybierz kartę **Setup.exe** .

5. Na stronie właściwości **Setup.exe** z listy **Lokalizacja wymagań wstępnych InstallShield** wybierz pozycję **Pobierz z sieci Web**.

6. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **Configuration Manager**.

7. Na liście **Konfiguracja aktywnego rozwiązania** wybierz pozycję **SingleImage**.

8. W tabeli **kontekstowe projektu** w kolumnie **Konfiguracja** projektu **OfficeAddInSetup** wybierz pozycję **SingleImage**, a następnie wybierz przycisk **Zamknij** .

9. Na pasku menu wybierz kolejno opcje **Kompiluj**  >  **kompilacje OfficeAddInSetup**.

   Po zakończeniu kompilacji można zlokalizować plik *setup.exe* projektu **OfficeAddInSetup** w następującej lokalizacji: <em>OfficeAddInSetupProjectRoot</em>**\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1 \\**

## <a name="see-also"></a>Zobacz także

- [Wymagania wstępne dotyczące wdrażania pakietu Office](/previous-versions/bb608617(v=vs.110))
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md)
- [Przegląd właściwości dokumentu niestandardowego](../vsto/custom-document-properties-overview.md)
- [Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)
- [Wdróż rozwiązanie Visual Studio 2010 Tools for Office przy użyciu Instalator Windows](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))