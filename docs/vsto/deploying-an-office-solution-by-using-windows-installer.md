---
title: Wdrażanie rozwiązania pakietu Office przy użyciu Instalator Windows
description: Dowiedz się, Visual Studio utworzyć aplikację za Instalator Windows, możesz wdrożyć rozwiązanie pakietu Office, które wymaga dostępu administracyjnego na komputerze użytkownika końcowego.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f6dfa2bb4d3309420cf0a9a71e79b5d07b5477ce
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828530"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Wdrażanie rozwiązania pakietu Office przy użyciu Instalator Windows

Dowiedz się, jak utworzyć Instalator Windows rozwiązania pakietu Office przy użyciu programu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] .

Używając Visual Studio do tworzenia Instalator Windows, można wdrożyć rozwiązanie pakietu Office, które wymaga dostępu administracyjnego na komputerze użytkownika końcowego. Na przykład można użyć takiego pliku, aby zainstalować rozwiązanie tylko raz dla wszystkich użytkowników komputera. Rozwiązanie pakietu Office można również wdrożyć przy użyciu technologii ClickOnce, ale to rozwiązanie należy zainstalować osobno dla każdego użytkownika komputera.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-topic"></a>W tym temacie:

- [Pobieranie przykładów dodatków VSTO](#Download)

- [Pobierz program InstallShield Limited Edition](#Obtain)

- [Decydowanie o tym, jak udzielić zaufania rozwiązaniu](#ApplySecurity)

- [Tworzenie projektu konfiguracji](#Create)

- [Dodawanie danych wyjściowych projektu](#Add)

- [Dodawanie manifestów wdrożenia i aplikacji](#AddD)

- [Konfigurowanie składników zależnych jako wymagań wstępnych](#Configure)

- [Określ miejsce wdrożenia rozwiązania na komputerze użytkownika](#Location)

- [Konfigurowanie dodatku VSTO](#ConfigureRegistry)

- [Konfigurowanie dostosowania na poziomie dokumentu](#ConfigureDocument)

- [Kompilowanie projektu konfiguracji](#Build)

Aby uzyskać więcej informacji na temat wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce, zobacz Wdrażanie rozwiązania [pakietu Office przy użyciu technologii ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)

Aby uzyskać informacje na temat tworzenia pliku Instalator Windows przy użyciu programu , zobacz [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] [Deploy a Visual Studio 2010 Tools for Office solution using Instalator Windows](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))(Wdrażanie rozwiązania narzędzi programu Visual Studio 2010 dla pakietu Office przy użyciu programu Instalator Windows).

## <a name="download-samples"></a><a name="Download"></a>Pobierz przykłady
Ten temat dotyczy następujących przykładów do pobrania.

|Sample<br /><br />|Opis<br /><br />|
|----------|---------------|
|[ExcelAddIn](https://code.msdn.microsoft.com/VSTO-Deploy-an-Office-fbcc09ad)<br /><br />|Dodatek VSTO programu Excel, który można zainstalować na komputerze z 32-bitową lub 64-bitową wersją pakietu Office.<br /><br />|
|[Excelworkbook](https://code.msdn.microsoft.com/VSTO-Deploy-a-Customization-f70fae33)<br /><br />|Dostosowanie na poziomie dokumentu programu Excel, które można zainstalować na komputerze z 32-bitową lub 64-bitową wersją pakietu Office.<br /><br />|

## <a name="decide-how-to-grant-trust-to-the-solution"></a><a name="ApplySecurity"></a>Decydowanie o tym, jak udzielić zaufania rozwiązaniu
Przed uruchomieniem rozwiązania na komputerach użytkowników należy udzielić zaufania w jeden z następujących sposobów lub użytkownicy muszą odpowiedzieć na monit o zaufanie podczas instalowania rozwiązania.

- Podpisz manifesty przy użyciu certyfikatu, który identyfikuje znanego i zaufanego wydawcę. Aby uzyskać więcej informacji, zobacz Trust the solution by signing the application and deployment manifests (Ufaj [rozwiązaniu przez podpisywanie manifestów aplikacji i wdrożenia).](../vsto/granting-trust-to-office-solutions.md#Signing)

- Zainstaluj rozwiązanie w katalogu Program Files na komputerze użytkownika.

> [!NOTE]
> W przypadku dostosowań na poziomie dokumentu lokalizacja dokumentu również musi być zaufana. Aby uzyskać więcej informacji, zobacz [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md).

## <a name="get-installshield-limited-edition"></a><a name="Obtain"></a>Pobierz program InstallShield Limited Edition

Plik Instalator Windows można utworzyć przy użyciu programu InstallShield Limited Edition (ISLE), który jest bezpłatny, jeśli zainstalowano Visual Studio. ISLE zastępuje funkcje szablonów projektów na czas instalacji i wdrażania, które były oferowane Visual Studio poprzednich wersjach.

### <a name="to-get-installshield-limited-edition"></a>Aby uzyskać program InstallShield Limited Edition

1. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).**

   Zostanie **otwarte okno dialogowe** Nowy projekt.

2. W okienku szablonów rozwiń **pozycję Inne typy projektów,** a następnie wybierz szablon **Konfiguracja i wdrażanie.**

3. Na liście typów projektów dla **instalatora** i wdrożenia wybierz pozycję **Włącz installShield Limited Edition,** a następnie wybierz **przycisk OK.**

   Zostanie wyświetlona strona z informacjami na temat sposobu uzyskania aplikacji InstallShield Limited Edition.

4. Na tej stronie wybierz link **Przejdź do witryny internetowej pobierania.**

5. Na stronie pobierania aplikacji InstallShield Limited Edition wprowadź wymagane informacje w odpowiednich polach, a następnie wybierz **link** Pobierz teraz.

   Po pobraniu, zainstalowaniu i aktywowaniu produktu szablon **InstallShield Limited Edition Project** pojawi się w Visual Studio.

## <a name="create-a-setup-project"></a><a name="Create"></a>Tworzenie projektu konfiguracji

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programie otwórz projekt pakietu Office, który chcesz wdrożyć.

   Przykłady dodatku VSTO skojarzone z tym tematem zawierają projekt o nazwie **ExcelAddIn**. Przykłady dostosowywania na poziomie dokumentu zawierają projekt o nazwie **ExcelWorkbook**. W tym temacie będziemy odwoływać się do projektu pakietu Office w rozwiązaniu przy użyciu jednej z tych dwóch nazw.

2. Na pasku menu wybierz pozycję **Plik**  >  **Dodaj nowy**  >  **projekt.**

   Zostanie **otwarte okno dialogowe Dodawanie** nowego projektu.

3. W okienku szablonów rozwiń **pozycję Inne typy projektów,** a następnie wybierz **szablon Konfiguracja i wdrażanie.**

4. Na liście typów projektów instalatora i wdrażania wybierz pozycję **InstallShield Limited Edition Project**, nazwij projekt, a następnie wybierz **przycisk OK.**

   Utworzony projekt instalacyjny installShield zostanie wyświetlony w rozwiązaniu.

   Przykłady dla tego tematu zawierają projekt instalacyjny o nazwie **OfficeAddInSetup**. Ten temat będzie odwoływać się do projektu konfiguracji w rozwiązaniu przy użyciu tej samej nazwy.

## <a name="add-the-project-output"></a><a name="Add"></a>Dodawanie danych wyjściowych projektu

Projekt **OfficeAddInSetup należy** skonfigurować tak, aby zawierał dane wyjściowe projektu pakietu Office. W przypadku projektów dodatków VSTO dane wyjściowe projektu są tylko zestawem rozwiązania. W przypadku projektów dostosowywania na poziomie dokumentu dane wyjściowe projektu obejmują nie tylko zestaw rozwiązania, ale także sam dokument.

### <a name="to-add-the-project-output"></a>Aby dodać dane wyjściowe projektu

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup,** a następnie wybierz plik **Asystent** projektu, który przedstawiono na poniższej ilustracji.

   ![Plik Asystenta projektu w Eksplorator rozwiązań](../vsto/media/installshield-projectassistant.png "Plik Asystenta projektu w Eksplorator rozwiązań")

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

3. W dolnej części **strony Asystent projektu** wybierz przycisk **Pliki** aplikacji, który przedstawiono na poniższej ilustracji.

   ![Przycisk Pliki aplikacji.](../vsto/media/installshield-applicationfiles.png "Przycisk Pliki aplikacji.")

4. Na stronie **Pliki aplikacji** wybierz przycisk Dodaj **dane wyjściowe** projektu.

5. W **oknie dialogowym Visual Studio Output Selector (Selektor** danych wyjściowych) zaznacz pole wyboru Primary Output (Podstawowe dane **wyjściowe),** a następnie wybierz przycisk **OK.**

## <a name="add-the-deployment-and-application-manifests"></a><a name="AddD"></a>Dodawanie manifestów wdrożenia i aplikacji

1. Na stronie **Pliki aplikacji** wybierz przycisk **Dodaj** pliki.

2. W **oknie** dialogowym Otwieranie przejdź do katalogu wyjściowego projektu **ExcelAddIn.**

   Zazwyczaj katalog wyjściowy jest podfolderem **bin\release** katalogu głównego projektu, w zależności od wybranej konfiguracji kompilacji.

3. W katalogu wyjściowym wybierz pliki **ExcelAddIn.vsto** **iExcelAddIn.dll.manifest,** a następnie wybierz przycisk **Otwórz.**

   Strona **Pliki aplikacji** zawiera teraz plik wyjściowy projektu, manifest wdrożenia i manifest aplikacji, jak pokazano na poniższej ilustracji.

   ![Pliki wyjściowe projektu konfiguracji.](../vsto/media/installshield-outputfiles.png "Pliki wyjściowe projektu konfiguracji.")

## <a name="configure-the-dependent-components-as-prerequisites"></a><a name="Configure"></a>Konfigurowanie składników zależnych jako wymagań wstępnych

W aplikacji instalacyjnej należy uwzględnić nie tylko następujące składniki, ale także inne składniki wymagane do działania rozwiązania.

- Wersja pliku docelowego .NET Framework pakietu Office.

- Pakiet Microsoft Visual Studio 2010 Tools for Office Runtime.

### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Dodaj .NET Framework 4 lub .NET Framework 4.5 jako wymaganie wstępne

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup,** rozwiń węzeł **Określ** dane aplikacji, a następnie wybierz plik **Redistributables,** który przedstawiono na poniższej ilustracji.

   ![Plik Redistributables w Eksplorator rozwiązań](../vsto/media/installshield-redistributablesfile.png "Plik Redistributables w Eksplorator rozwiązań")

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

   Zostanie **otwarta strona Redystrybucyjne.**

3. Na liście składników redystrybucyjnego zaznacz odpowiednie pole wyboru dla wersji pakietu .NET Framework docelowego rozwiązania.

   Jeśli na przykład rozwiązanie jest docelowe dla programu , zaznacz pole [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] **wyboru Microsoft .NET Framework 4.5 Full.** Może zostać wyświetlone okno dialogowe z pytaniem, czy chcesz zainstalować składnik redystrybucyjnego, którego wymaga program InstallShield, zanim będzie można dodać składnik jako wymaganie wstępne. Jeśli to okno dialogowe nie zostanie wyświetlone, składnik już istnieje na komputerze.

4. Jeśli zostanie wyświetlone okno dialogowe, wybierz **przycisk** Nie.

### <a name="add-the-visual-studio-2010-tools-for-office-runtime"></a><a name="AddToolsForOffice"></a>Dodawanie narzędzia Visual Studio 2010 Tools for Office Runtime

Strona **Redystrybucyjne** zawiera element o nazwie **Microsoft VSTO 2010 Runtime,** ale odwołuje się do starszej wersji środowiska uruchomieniowego. W związku z tym można ręcznie utworzyć plik konfiguracji, który odwołuje się do najnowszej wersji. Następnie należy umieścić ten plik w tym samym katalogu co pliki konfiguracji dla wszystkich innych elementów, które pojawiają się na stronie **Redystrybucyjne.**

#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Aby dodać środowisko uruchomieniowe Visual Studio 2010 Tools for Office jako wymaganie wstępne

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

2. Wygeneruj identyfikator GUID w Visual Studio. W menu **Narzędzia** wybierz pozycję **Utwórz identyfikator GUID.**

3. W **programie generatora identyfikatorów GUID** wybierz przycisk **Format** rejestru, wybierz przycisk **Kopiuj,** a następnie wybierz **przycisk** Zakończ.

4. W Notatniku zastąp tekst Identyfikator GUID znajduje się **tutaj,** wklejając w jego miejscu identyfikator GUID.

   Element **&lt; właściwości &gt;** pliku jest podobny do poniższego.

   ```xml
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >
   </properties>
   ```

5. Na pasku menu w Notatniku wybierz pozycję **Plik**  >  **Zapisz.**

6. W **oknie dialogowym** Zapisywanie jako przejdź do folderu **pulpitu.**

7. Na liście **Zapisz jako typ wybierz** pozycję Wszystkie pliki **(&#42;.&#42;).**

8. W polu **Nazwa pliku** wprowadź Visual Studio **2010 Tools for Office Runtime.prq,** a następnie wybierz **przycisk** Zapisz.

   > [!NOTE]
   > Upewnij się, że na końcu nazwy pliku dodasz plik **prq,** aby zidentyfikować ten plik jako plik wymagań wstępnych.

9. Zamknij Notatnik.

10. Z folderu **Desktop** skopiuj plik *Visual Studio 2010 Tools for Office Runtime.prq* do jednego z następujących katalogów na komputerze.

   W przypadku 32-bitowych systemów operacyjnych: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites \\*

   W przypadku 64-bitowych systemów operacyjnych: *%ProgramFiles(x86)%\2013LE\SetupPrerequisites \\*

11. Na stronie **Redystrybucyjne** projektu  InstallShield wybierz przycisk Odśwież, aby odświeżyć listę składników redystrybucyjnego, jak pokazano na poniższej ilustracji.

   ![Przycisk odświeżania.](../vsto/media/installshield-refreshbutton.png "Przycisk odświeżenia.")

12. Na liście składników redystrybucyjnego zaznacz pole **wyboru Visual Studio 2010 Tools for Office Runtime.**

   Może zostać wyświetlone okno dialogowe z pytaniem, czy chcesz zainstalować składnik redystrybucyjnego. Jeśli to okno dialogowe nie zostanie wyświetlone, możesz przejść do sekcji Określanie miejsca wdrożenia rozwiązania na komputerze [użytkownika](#Location) w tym temacie.

13. Jeśli zostanie wyświetlone to okno dialogowe, wybierz **przycisk** Nie.

## <a name="specify-where-to-install-the-solution-on-the-users-computer"></a><a name="Location"></a>Określanie miejsca instalacji rozwiązania na komputerze użytkownika

1. W **Eksplorator rozwiązań** rozwiń węzeł **OfficeAddInSetup,** rozwiń węzeł **Organizuj** konfigurację, a następnie wybierz **plik Informacje** ogólne.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

3. Na liście właściwości wybierz przycisk **Przeglądaj** obok właściwości **INSTALLDIR.**

4. W **oknie dialogowym Ustawianie** katalogu INSTALLDIR wybierz folder na komputerze użytkownika, na którym chcesz zainstalować rozwiązanie.

   > [!NOTE]
   > Możesz również utworzyć podkatalogi w oknie dialogowym **Ustaw KATALOG_INSTALACJI,** otwierając menu skrótów dla dowolnego folderu na liście.

## <a name="configure-a-vsto-add-in"></a><a name="ConfigureRegistry"></a>Konfigurowanie dodatku VSTO

Możesz określić, czy dodatek VSTO ma być instalowany dla wszystkich użytkowników komputera (na komputerze), czy tylko dla użytkownika wykonującego instalację (na użytkownika).

Jeśli chcesz obsługiwać instalacje na komputerze, utwórz dwa oddzielne instalatory. Instalatory można podzielić na podstawie wersji pakietu Office (32-bitowej i 64-bitowej) lub w wersji systemu Windows (32-bitowej i 64-bitowej), z których korzysta użytkownik.

Instalacje na użytkownika wymagają tylko jednego instalatora niezależnie od wersji pakietu Office lub systemu Windows.

> [!NOTE]
> Ta sekcja ma zastosowanie tylko w przypadku wdrażania dodatku VSTO. Jeśli wdrażasz dostosowanie na poziomie dokumentu, możesz natychmiast przejść do sekcji Konfigurowanie dostosowywania [na poziomie](#ConfigureDocument) dokumentu.

### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Aby określić, czy chcesz obsługiwać instalacje na użytkownika, czy na komputerze

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup,**  rozwiń węzeł Organizuj konfigurację, a następnie wybierz **plik Informacje** ogólne.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

   Zostaną wyświetlone właściwości projektu konfiguracji.

3. Na liście właściwości **AllUSERS** określ, czy to rozwiązanie ma być instalowane dla wszystkich użytkowników komputera, czy tylko dla użytkownika, który instaluje rozwiązanie.

   Aby zainstalować dodatek VSTO dla bieżącego użytkownika, wybierz pozycję **ALLUSERS="" (Instalacja na użytkownika).** Aby zainstalować dodatek VSTO dla wszystkich użytkowników komputera, wybierz pozycję **ALLUSERS=1 (instalacja na maszynę)**

   W następnej procedurze utworzysz klucze rejestru, aby umożliwić aplikacji pakietu Office odnajdywanie i ładowanie dodatku VSTO. Zobacz [Wpisy rejestru dla dodatków VSTO.](../vsto/registry-entries-for-vsto-add-ins.md)

### <a name="to-create-registry-keys"></a>Aby utworzyć klucze rejestru

1. W **Eksplorator rozwiązań** wybierz węzeł **Asystent projektu.**

   Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

2. W dolnej części **strony Asystent projektu** wybierz przycisk **Rejestr** aplikacji, który przedstawiono na poniższej ilustracji.

   ![Przycisk Rejestr aplikacji.](../vsto/media/installshield-applicationregistry.gif "Przycisk Rejestr aplikacji.")

   Zostanie **wyświetlona strona Rejestr** aplikacji.

3. W **obszarze Czy chcesz skonfigurować dane rejestru,** które zostaną zainstalowane przez aplikację? wybierz **przycisk** Tak.

4. Z listy **widoków Rejestr** komputera docelowego dodaj hierarchię kluczy, która umożliwia typ instalatora, który chcesz utworzyć.

   Ścieżka skonfigurowana w tej sekcji zależy od tego, czy tworzysz instalatora na użytkownika, czy instalatora dla komputera.

   **Instalator na użytkownika**

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**

   **Instalatory na komputer na podstawie wersji pakietu Office**

| Wersja pakietu Office<br /><br /> | Ścieżka konfiguracji installShield<br /><br /> |
|----------------------------| - |
| 32-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Instalatory na komputer oparte na wersji systemu Windows**

| Wersja systemu Windows<br /><br /> | Ścieżka konfiguracji installShield<br /><br /> |
|-----------------------------| - |
| 32-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\SOFTWARE(32-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\SOFTWARE(64-Bit)\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]
   > Instalator 64-bitowego systemu Windows wymaga dwóch ścieżek rejestru, ponieważ użytkownicy mogą uruchamiać 32-bitowe i 64-bitowe wersje pakietu Office na komputerze z 64-bitowym systemem Windows.

   > [!NOTE]
   > Najlepszym rozwiązaniem jest rozpoczęcie nazwy dodatku VSTO od nazwy firmy. Ta konwencja zwiększa prawdopodobieństwo, że klucz będzie unikatowy, i zmniejsza ryzyko konfliktu z dodatku VSTO innego dostawcy. Dodatki, które mają taką samą nazwę, mogą na przykład zastępować klucze rejestracji innych osób. Takie podejście nie gwarantuje, że klucz będzie unikatowy, ale może ograniczyć potencjalne konflikty nazw.

5. Po utworzeniu hierarchii kluczy otwórz menu skrótów dla klucza **SampleCompany.ExcelAddIn,** wybierz pozycję **Nowa**, a następnie wybierz **pozycję Wartość ciągu**.

   Nowa wartość ciągu pojawi się **na liście danych Rejestr** komputera docelowego. Nazwa wartości ciągu jest wyróżniona, aby można było zmienić jej nazwę.

6. Zmień nazwę wartości na **Opis**.

7. Powtórz ten proces, aby utworzyć następujące wartości.

|Typ wartości<br /><br />|Nazwa<br /><br />|
|--------------|--------|
|Wartość ciągu<br /><br />|**FriendlyName**<br /><br />|
|Wartość DWORD<br /><br />|**Loadbehavior**<br /><br />|
|Wartość ciągu<br /><br />|**Manifestu**<br /><br />|

8. Otwórz menu skrótów dla wartości **Opis,** a następnie wybierz pozycję **Modyfikuj**.

   Zostanie **wyświetlone okno dialogowe** Edytowanie danych.

9. W polu **tekstowym Value data (Dane** wartości) wprowadź **tekst Demo Add-In (Pokazowy** dodatek programu Excel), a następnie wybierz przycisk **OK.**

   Ten opis jest wyświetlany, gdy użytkownik  otworzy aplikację pakietu Office,  otworzy okno dialogowe Opcje, a następnie w okienku Dodatki wybierze dodatek narzędzi VSTO.

10. Otwórz menu skrótów dla **wartości FriendlyName,** a następnie wybierz pozycję **Modyfikuj**.

   Zostanie **wyświetlone okno dialogowe** Edytowanie danych.

11. W polu **tekstowym Value data (Dane** wartości) wprowadź **tekst Demo Add-In (Pokazowy** dodatek programu Excel), a następnie wybierz przycisk **OK.**

   Ten ciąg pojawia się w **oknie dialogowym** Dodatki COM w aplikacji pakietu Office. Domyślnie wartością ciągu jest identyfikator dodatku VSTO.

12. Otwórz menu skrótów dla **wartości LoadBehavior,** a następnie wybierz pozycję **Modyfikuj.**

   Zostanie **wyświetlone okno dialogowe** Edytowanie danych.

13. W polu **tekstowym Dane** wartości wprowadź **3**, a następnie wybierz **przycisk OK.**

   Wartość 3 ładuje dodatek VSTO podczas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat wartości LoadBehavior, zobacz wpisy rejestru dla dodatków [VSTO.](../vsto/registry-entries-for-vsto-add-ins.md)

14. Otwórz menu skrótów dla **wartości Manifest,** a następnie wybierz pozycję **Modyfikuj**.

   Zostanie **wyświetlone okno dialogowe** Edytowanie danych.

15. W polu **tekstowym** Dane wartości wprowadź **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal,** a następnie wybierz **przycisk OK.**

   W Visual Studio 2010 Tools for Office Runtime ta ścieżka jest używana do lokalizowania manifestu wdrożenia. Część **[INSTALLDIR]** tej ścieżki to makro mapowane na właściwość  **INSTALLDIR** na stronie właściwości Informacje ogólne projektu instalacyjnego installShield. Ta właściwość określa lokalizację na komputerze docelowym, w którym ma być instalowany dodatek VSTO. **Sufiks |vstolocal** gwarantuje załadowanie rozwiązania z folderu instalacyjnego, a nie pamięci podręcznej ClickOnce.

> [!IMPORTANT]
> Jeśli tworzysz niestandardowy region formularza w dodatku VSTO dla programu Outlook, musisz utworzyć więcej wpisów rejestru, aby zarejestrować region w programie Outlook. Aby uzyskać więcej informacji, zobacz [Wpisy rejestru dla regionów formularzy programu Outlook.](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries)

## <a name="configure-a-document-level-customization"></a><a name="ConfigureDocument"></a>Konfigurowanie dostosowywania na poziomie dokumentu

Ta sekcja ma zastosowanie tylko w przypadku wdrażania dostosowania na poziomie dokumentu. Jeśli wdrażasz dodatek VSTO, możesz natychmiast przejść do sekcji [Tworzenie projektu konfiguracji.](#Build)

Dostosowania na poziomie dokumentu nie używają kluczy rejestru. Zamiast tego niestandardowe właściwości dokumentu zawierają lokalizację manifestu wdrożenia.

Aby zmodyfikować właściwości niestandardowe, należy utworzyć program, który usunie dostosowanie na poziomie dokumentu z dokumentu, zmodyfikuje odpowiednie właściwości, a następnie ponownie dołączy dostosowanie do dokumentu. Następnie utworzysz akcję niestandardową uruchamianą przez program i dodasz ją do projektu konfiguracji.

### <a name="to-create-a-program-that-modifies-document-properties"></a>Aby utworzyć program modyfikujący właściwości dokumentu

1. Na pasku menu wybierz pozycję **Plik**  >  **Dodaj nowy**  >  **projekt.**

   Zostanie **wyświetlone okno dialogowe Dodawanie** nowego projektu.

2. W okienku szablonów w węźle języka, którego chcesz użyć, wybierz folder **Windows.**

3. Na liście typów projektów dla systemu **Windows** wybierz szablon **Aplikacja konsolowa.**

4. Nadaj **projektowi nazwę SetExcelDocumentProperties,** a następnie wybierz **przycisk OK.**

5. W **Eksplorator rozwiązań** wybierz przycisk  Pokaż wszystkie pliki, otwórz menu skrótów dla węzła projektu **SetExcelDocumentProperties,** a następnie wybierz pozycję **Dodaj odwołanie.**

6. W **oknie dialogowym Menedżer** odwoływać wybierz **kartę** Rozszerzenia, a następnie zaznacz pole wyboru obok następujących zestawów, a następnie wybierz **przycisk OK.**

   - Microsoft.VisualStudio.Tools.Applications.Runtime

   - Microsoft.visualstudio.tools.applications.serverdocument

7. W **Eksplorator rozwiązań** wybierz plik **Program.cs** (dla aplikacji języka C#) lub plik **Module1.vb** (dla Visual Basic aplikacji).

8. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

9. Zastąp zawartość całego pliku następującym kodem.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb" id="Snippet1":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs" id="Snippet1":::

10. Skompiluj projekt.

### <a name="to-add-a-custom-action-that-runs-your-program"></a>Aby dodać akcję niestandardową, która uruchamia program

1. W **Eksplorator rozwiązań** rozwiń węzeł projektu **OfficeAddInSetup,** a następnie wybierz plik **Asystent** projektu, który przedstawiono na poniższej ilustracji.

   ![Plik Asystenta projektu w Eksplorator rozwiązań](../vsto/media/installshield-projectassistant.png "Plik Asystenta projektu w Eksplorator rozwiązań")

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

3. W dolnej części **strony Asystent projektu** wybierz przycisk **Pliki** aplikacji, który przedstawiono na poniższej ilustracji.

   ![Przycisk Pliki aplikacji.](../vsto/media/installshield-applicationfiles.png "Przycisk Pliki aplikacji.")

4. Na stronie **Pliki aplikacji** wybierz przycisk Dodaj **dane wyjściowe** projektu.

   Zostanie **Visual Studio okno dialogowe Selektor** danych wyjściowych.

5. W **węźle SetExcelDocumentProperties** zaznacz pole wyboru Podstawowe dane **wyjściowe,** a następnie wybierz **przycisk OK.**

6. W **Eksplorator rozwiązań** w węźle **OfficeAddInSetup** rozwiń węzeł Definiuj wymagania i akcje instalacji, a następnie wybierz folder **Akcje niestandardowe.** 

7. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

   Lista zdarzeń jest wyświetlana w okienku z boku ekranu.

   > [!NOTE]
   > W programie InstallShield Limited Edition dostępnych jest tylko kilka zdarzeń wyświetlanych na tej liście. W tej procedurze program zostanie uruchomiony przy użyciu zdarzenia dialogowego Po ukończeniu instalacji **zakończonego powodzeniem.**

8. Na liście zdarzeń w obszarze **Akcje** niestandardowe podczas instalacji otwórz menu skrótów zdarzenia dialogowego Po ukończeniu instalacji **zakończonego powodzeniem,** a następnie wybierz **pozycję Nowy plik EXE.**

   Akcja niestandardowa o nazwie **NewCustomAction1** jest wyświetlana w ramach zdarzenia okna dialogowego **Po ukończeniu instalacji zakończonego powodzeniem.** Zestaw właściwości akcji niestandardowej jest wyświetlany w okienku obok zdarzeń.

   > [!IMPORTANT]
   > Na **liście zdarzeń są wyświetlane** dwa zdarzenia okna dialogowego Po ukończeniu instalacji zakończone powodzeniem. Upewnij się, że wybierasz wystąpienie zdarzenia dialogowego Po ukończeniu instalacji **zakończonego powodzeniem** wyświetlanego w węźle **Akcje niestandardowe podczas instalacji.**

9. Na liście właściwości **Lokalizacja źródłową** wybierz pozycję **Zainstalowane z produktem**.

10. Wybierz przycisk **Przeglądaj** obok właściwości **Nazwa** pliku.

11. W **oknie dialogowym** Przeglądaj w celu wybrania pliku docelowego przejdź do pliku **SetExcelDocumentProperties.Primary.output,** a następnie wybierz **przycisk** Otwórz.

    Lokalizacja tego pliku zależy od folderu określonego dla właściwości **INSTALLDIR** projektu instalacyjnego. Jeśli na przykład ustawisz właściwość na folder o nazwie **[PersonalFolder]DemoWorkbookApp,** możesz znaleźć plik **SetExcelDocumentProperties.Primary.output,** przeglądając **foldery [ProgramFilesFolder]\DemoWorkbookApp.**

    W następnych kilku krokach pobierzesz identyfikator rozwiązania dokumentu, a następnie przekażesz ten identyfikator jako parametr do aplikacji konsolowej. Przekażesz również lokalizację dokumentu, manifest wdrożenia i zestaw dokumentu.

12. Otwórz menu skrótów dla projektu **ExcelWorkbook,** a następnie wybierz pozycję Otwórz folder w programie **Eksplorator Windows** lub Otwórz folder w programie **Eksplorator plików** w zależności od systemu operacyjnego.

    Zostanie otwarty folder zawierający rozwiązanie.

13. Otwórz plik projektu rozwiązania w Notatniku. W Visual Basic nazwa pliku to *ExcelWorkbook.vbproj.* W przypadku projektów w języku C# nazwa pliku to *ExcelWorkbook.csproj.*

14. W pliku projektu wyszukaj element **&lt; SolutionID, &gt;** skopiuj jego wartość do schowka, a następnie zamknij Notatnik.

    Ta wartość jest przekazywać do aplikacji konsolowej jako parametr.

15. Na stronie właściwości obiektu **NewCustomAction1** ustaw właściwość **Wiersz** polecenia na następujący wiersz tekstu.

   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"
   ```

16. Zastąp **identyfikator rozwiązania** identyfikatorem rozwiązania skopiowanym do schowka.

   > [!IMPORTANT]
   > Przetestuj instalatora, aby sprawdzić, czy aplikacja konsolowa uruchamiana przez tę akcję niestandardową może uzyskać dostęp do dokumentów w katalogu [INSTALLDIR]. Niektóre katalogi na komputerze użytkownika mogą wymagać dostępu administracyjnego (na przykład katalogu Program Files). Jeśli wdrażasz rozwiązanie w katalogu, który wymaga dostępu administracyjnego, otwórz okno dialogowe Właściwości pliku  *setup.exe, wybierz* kartę Zgodność, a następnie zaznacz pole wyboru Uruchom ten program jako **administrator** przed dystrybucją instalatora.  Jeśli nie chcesz, aby użytkownicy uruchamiali program instalacyjny z uprawnieniami administracyjnymi, ustaw właściwość [INSTALLDIR] na katalog, do którego użytkownik prawdopodobnie ma już dostęp, taki jak katalog **Dokumenty.** Aby uzyskać więcej informacji, zobacz [sekcję Określanie](#Location) miejsca instalacji rozwiązania na komputerze użytkownika w tym temacie.

## <a name="build-the-setup-project"></a><a name="Build"></a>Kompilowanie projektu konfiguracji

1. W **Eksplorator rozwiązań** rozwiń węzeł Przygotowanie do **wydania,** a następnie wybierz **plik Wydania.**

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **Otwórz.**

   Eksplorator **kompilacji** zostanie otwarty w okienku bocznym, aby można było wybrać typ wydania, który chcesz utworzyć.

3. W **eksploratorze kompilacji** wybierz folder **SingleImage.**

4. W okienku obok Eksploratora **kompilacji** wybierz **kartęSetup.exe** kompilacji.

5. Na stronie **właściwościSetup.exe** z listy InstallShield Prerequisites Location (Lokalizacja wymagań **wstępnych aplikacji InstallShield)** **wybierz pozycję Download From The Web (Pobierz z Sieci Web).**

6. Na pasku menu wybierz pozycję **Kompilacja**  >  **Menedżer konfiguracji.**

7. Na liście **Konfiguracja aktywnego rozwiązania** wybierz pozycję **SingleImage.**

8. W **tabeli Konteksty projektu** w kolumnie **Konfiguracja** projektu **OfficeAddInSetup** wybierz pozycję **SingleImage,** a następnie wybierz **przycisk** Zamknij.

9. Na pasku menu wybierz pozycję **Build**  >  **Build OfficeAddInSetup (Kompilacja kompilacji OfficeDdInSetup).**

   Po zakończeniu kompilacji można zlokalizować plik *setup.exe* projektu **OfficeAddInSetup** w następującej lokalizacji: <em>OfficeAddInSetupProjectRoot</em>**\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1 \\**

## <a name="see-also"></a>Zobacz też

- [Wymagania wstępne rozwiązania pakietu Office dotyczące wdrażania](/previous-versions/bb608617(v=vs.110))
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Wpisy rejestru dla dodatków VSTO](../vsto/registry-entries-for-vsto-add-ins.md)
- [Omówienie właściwości dokumentów niestandardowych](../vsto/custom-document-properties-overview.md)
- [Udzielanie zaufania rozwiązaniom pakietu Office](../vsto/granting-trust-to-office-solutions.md)
- [Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)
- [Wdrażanie rozwiązania Visual Studio 2010 Tools for Office przy użyciu Instalator Windows](/previous-versions/visualstudio/visual-studio-2010/ff937654(v=msdn.10))