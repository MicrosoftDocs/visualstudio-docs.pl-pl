---
title: Wdrażanie rozwiązania do pakietu Office przy użyciu Instalatora Windows
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: f5aaf0cdff2795ff0726ca2de36e794179f2d924
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648771"
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Wdrażanie rozwiązania do pakietu Office przy użyciu Instalatora Windows
Dowiedz się, jak utworzyć Instalatora Windows dla rozwiązania pakietu Office przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  

Za pomocą programu Visual Studio, aby utworzyć Instalatora Windows, można wdrożyć rozwiązanie Office, który wymaga dostępu administracyjnego na komputerze użytkownika końcowego. Na przykład można użyć takiego pliku do zainstalowania rozwiązania tylko raz dla wszystkich użytkowników komputera. Można także wdrożyć rozwiązania do pakietu Office przy użyciu technologii ClickOnce, jednak, że rozwiązanie musi być zainstalowane oddzielnie dla każdego użytkownika komputera.  


## <a name="in-this-topic"></a>W tym temacie:  

- [Pobierz przykłady dodatku narzędzi VSTO](#Download)  

- [Pobierz InstallShield Limited Edition](#Obtain)  

- [Wybieranie sposobu udzielenia zaufania rozwiązaniu](#ApplySecurity)  

- [Utwórz Instalatora projektu](#Create)  

- [Dodaj dane wyjściowe projektu](#Add)  

- [Dodaj manifesty wdrażania i aplikacji](#AddD)  

- [Konfigurowanie składników zależnych jako warunki wstępne](#Configure)  

- [Określ, której chcesz wdrożyć rozwiązanie na komputerze użytkownika](#Location)  

- [Konfigurowanie dodatku narzędzi VSTO](#ConfigureRegistry)  

- [Konfigurowanie dostosowywania poziomie dokumentu](#ConfigureDocument)  

- [Projektu Instalatora kompilacji](#Build)  

Aby uzyskać więcej informacji na temat sposobu wdrażania rozwiązania do pakietu Office przy użyciu technologii ClickOnce, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  

Aby uzyskać informacje o tym, jak utworzyć plik Instalatora Windows za pomocą [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], zobacz [wdrażanie programu Visual Studio 2010 Tools dla rozwiązań pakietu Office przy użyciu Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=201807).  


## <a name="Download"></a>Pobierz przykłady  
W tym temacie odnosi się do następujących przykładów do pobrania.  



|Przykład<br /><br />|Opis<br /><br />|  
|----------|---------------|  
|[ExcelAddIn](http://go.microsoft.com/fwlink/?LinkID=275492)<br /><br />|Dodatek narzędzi VSTO dla programu Excel, który można zainstalować na komputerze, na który uruchamia 32-bitowy lub 64-bitową wersję pakietu Office.<br /><br />|  
|[ExcelWorkbook](http://go.microsoft.com/fwlink/?LinkID=275493)<br /><br />|Dostosowania poziomu dokumentu programu Excel, który można zainstalować na komputerze, który uruchamia 32-bitowy lub 64-bitową wersję pakietu Office.<br /><br />|  

## <a name="ApplySecurity"></a>Wybieranie sposobu udzielenia zaufania rozwiązaniu  
Zanim rozwiązanie można uruchomić na komputerach użytkowników, należy udzielić zaufania w jeden z następujących sposobów lub użytkownik musi odpowiedzieć na monit o udzielenie zaufania podczas instalacjo rozwiązania.  


- Podpisz manifesty za pomocą certyfikatu identyfikującego znanego i zaufanego wydawcę. Aby uzyskać więcej informacji, zobacz [zaufania rozwiązania przez podpisanie manifestów aplikacji i wdrożenia](../vsto/granting-trust-to-office-solutions.md#Signing).  

- Zainstalować rozwiązanie do katalogu Program Files na komputerze użytkownika.  

> [!NOTE]  
> Dostosowania poziomu dokumentu lokalizację dokumentu również musi być zaufany. Aby uzyskać więcej informacji, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  


## <a name="Obtain"></a>Pobierz InstallShield Limited Edition  
Można utworzyć plik Instalatora Windows używając InstallShield Limited Edition (ISLE), który jest darmowy Jeżeli zainstalowano Visual Studio. ISLE zastępuje funkcje szablonów projektu do instalacji i wdrażania, które oferowane przez poprzednie wersje programu Visual Studio.  


### <a name="to-get-installshield-limited-edition"></a>Aby uzyskać InstallShield Limited Edition  

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.  

   **Nowy projekt** zostanie otwarte okno dialogowe.  

2. W okienku szablonów, rozwiń **inne typy projektów**, a następnie wybierz **instalacja i wdrożenie** szablonu.  

3. Na liście typów projektów dla **instalacja i wdrożenie**, wybierz **Włącz InstallShield Limited Edition**, a następnie wybierz **OK** przycisku.  

   Zostanie wyświetlona strona, która zawiera informacje dotyczące sposobu uzyskania programu InstallShield Limited Edition.  

4. Na tej stronie wybierz **przejdź do witryny sieci web pobierania** łącza.  

5. Na stronie pobierania programu InstallShield Limited Edition wprowadź wymagane informacje w odpowiednich polach, a następnie wybierz **Pobierz teraz** łącza.  

   Po pobraniu, zainstaluj i Aktywuj produkt, **projekt InstallShield Limited Edition** szablon jest wyświetlany w programie Visual Studio.  


## <a name="Create"></a>Utwórz Instalatora projektu  

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], otwórz projekt pakietu Office, który chcesz wdrożyć.  

   Przykłady dodatku narzędzi VSTO dla programów, które są skojarzone z tym tematem zawierają projekt o nazwie **ExcelAddIn**. Próbki dostosowania na poziomie dokumentów zawierają projekt o nazwie **ExcelWorkbook**. Ten temat będzie odnosił się do projektu Office w Twoim rozwiązaniu przy użyciu jednej z tych dwóch nazw.  

2. Na pasku menu wybierz **pliku** > **Dodaj** > **nowy projekt**.  

   **Dodaj nowy projekt** zostanie otwarte okno dialogowe.  

3. W okienku szablonów, rozwiń **inne typy projektów**, a następnie wybierz **instalacja i wdrożenie** szablonu.  

4. Na liście typów projektów dla **instalacja i wdrożenie**, wybierz **projekt InstallShield Limited Edition**, nadaj projektowi nazwę, a następnie wybierz **OK** przycisku.  

   W rozwiązaniu pojawia się projekt konfiguracji instalatora InstallShield, który został utworzony.  

   Przykłady do tego tematu obejmują projekt konfiguracji o nazwie **OfficeAddInSetup**. Ten temat będzie odnosił się do projektu konfiguracji w Twoim rozwiązaniu przy użyciu tej samej nazwie.  


## <a name="Add"></a>Dodaj dane wyjściowe projektu  
Możesz skonfigurować **OfficeAddInSetup** projekt, aby zawierał wyniki Twojego projektu Office. W projektach dodatku narzędzi VSTO projekt wyjściowy jest tylko zestawem rozwiązań. Dla projektów dostosowywanych na poziomie dokumentu projekt wyjściowy zawiera nie tylko zestaw rozwiązań, ale także sam dokument.  


### <a name="to-add-the-project-output"></a>Aby dodać projekt wyjściowy  

1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, a następnie wybierz **Asystent projektu** pliku, który przedstawiono na poniższej ilustracji.  

   ![Asystent pliku w Eksploratorze rozwiązań projektu](../vsto/media/installshield-projectassistant.png "projektu Asystenta plik w Eksploratorze rozwiązań")  

2. Na pasku menu wybierz **widoku** > **Otwórz**.  

3. W dolnej części **Asystenta projektu** wybierz **pliki aplikacji** przycisk, który przedstawiono na poniższej ilustracji.  

   ![Przycisk pliki aplikacji. ](../vsto/media/installshield-applicationfiles.png "Przycisk pliki aplikacji.")  

4. W **pliki aplikacji** wybierz **Dodaj dane wyjściowe projektu** przycisku.  

5. W **Visual Studio Output Selector** okno dialogowe, wybierz opcję **podstawowe wyjście** pole wyboru, a następnie wybierz **OK** przycisku.  


## <a name="AddD"></a>Dodaj manifesty wdrażania i aplikacji  

###  
1. W **pliki aplikacji** wybierz **Dodaj pliki** przycisku.  

2. W **Otwórz** okno dialogowe, przejdź do katalogu wyjściowego **ExcelAddIn** projektu.  

   Zwykle katalog wyjściowy jest **bin\release** podfolderze katalogu głównego projektu, w zależności od konfiguracji kompilacji, który wybierzesz.  

3. W katalogu wyjściowym wybierz **ExcelAddIn.vsto** i **ExcelAddIn.dll.manifest** pliki, a następnie wybierz **Otwórz** przycisku.  

   **Pliki aplikacji** strona zawiera teraz plik wyjściowy projektu, manifest wdrożenia i manifest aplikacji, jak pokazano na następującym rysunku.  

   ![Pliki wyjściowe projektu Instalatora. ](../vsto/media/installshield-outputfiles.png "Plików wyjściowych projektu Instalatora.")  


## <a name="Configure"></a>Konfigurowanie składników zależnych jako warunki wstępne  
W program instalacyjny musi zawierać nie tylko następujące składniki, ale także inne składniki, które są wymagane do rozwiązania w celu uruchomienia.  


- Wersja programu .NET Framework, żądnej dla rozwiązania pakietu Office.  

- Microsoft Visual Studio 2010 Tools for Office Runtime.  


### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Dodawanie programu .NET Framework 4 lub .NET Framework 4.5 jako warunek wstępny  

1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, rozwiń **Określ dane aplikacji** węzła, a następnie wybierz  **Pakiety redystrybucyjne** pliku, który przedstawiono na poniższej ilustracji.  

   ![Pakiety redystrybucyjne plik w Eksploratorze rozwiązań](../vsto/media/installshield-redistributablesfile.png "plików pakietów redystrybucyjnych w Eksploratorze rozwiązań")  

2. Na pasku menu wybierz **widoku** > **Otwórz**.  

   **Pakietów redystrybucyjnych** zostanie otwarta strona.  

3. Na liście składników pakietu redystrybucyjnego, wybierz odpowiednie pole wyboru dla wersji programu .NET Framework, żądnej dla rozwiązania.  

   Na przykład jeśli Twoje rozwiązanie wskazuje [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], wybierz opcję **Microsoft .NET Framework 4.5 Full** pole wyboru. Pojawi się okno dialogowe, pytając, czy zainstalować składnik redystrybucyjny, którego wymaga InstallShield przed dodaniem składników jako warunek wstępny. Jeśli to okno dialogowe nie pojawia się, komponent już istnieje na tym komputerze.  

4. Jeśli pojawi się okno dialogowe, wybierz **nie** przycisku.  


### <a name="AddToolsForOffice"></a>Dodaj program Visual Studio 2010 Tools for Office Runtime  
**Pakietów redystrybucyjnych** strona zawiera element o nazwie **Microsoft VSTO 2010 Runtime**, ale odwołuje się do starszej wersji środowiska uruchomieniowego. W związku z tym można ręcznie utworzyć plik konfiguracji, który odwołuje się do najnowszej wersji. Następnie należy umieścić ten plik, w tym samym katalogu co pliki konfiguracji dla wszystkich innych elementów, które pojawiają się w **pakietów redystrybucyjnych** strony.  


#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Aby dodać Visual Studio 2010 Tools dla pakietu Office runtime jako warunek wstępny  

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

2. Wygeneruj identyfikator GUID w programie Visual Studio. Na **narzędzia** menu, wybierz **Utwórz GUID**.  

3. W **GUID generator** programować, wybierz polecenie **Format rejestru** przycisk opcji, wybierz polecenie **kopiowania** przycisk, a następnie wybierz **zakończenia** przycisk.  

4. W programie Notatnik, Zastąp tekst **miejsce na Twój identyfikator GUID** przez wklejanie identyfikatora GUID w jego miejscu.  

   **&lt;Właściwości&gt;** elementu z pliku jest podobny do następującego.  


   ```xml  
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
   ```  

5. Na pasku menu Notatnika wybierz **pliku** > **Zapisz**.  

6. W **Zapisz jako** okno dialogowe, przejdź do swojej **pulpitu** folderu.  

7. W **Zapisz jako typ** wybierz **wszystkie pliki (&#42;.&#42;)** .  

8. W **nazwy pliku** wprowadź **Visual Studio 2010 Tools dla Office Runtime.prq**, a następnie wybierz **Zapisz** przycisku.  

   > [!NOTE]  
   >    Upewnij się, że dodano **.prq** na końcu nazwy pliku, aby zidentyfikować ten plik jako plik wymagań wstępnych.  

9. Zamknij Notatnik.  

10. Z usługi **pulpitu** folderu, kopiowanie *Visual Studio 2010 Tools dla Office Runtime.prq* pliku do jednej z następujących katalogów na tym komputerze.  

   Dla 32-bitowych systemach operacyjnych: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites\\*  

   Dla 64-bitowych systemach operacyjnych: *% ProgramFiles (x86) %\2013LE\SetupPrerequisites\\*  

11. W **Redistributable** strony projektu InstallShield, wybierz **Odśwież** przycisk, aby odświeżyć listę składników do dystrybucji, jak pokazano na następującym rysunku.  

   ![Przycisk Odśwież. ](../vsto/media/installshield-refreshbutton.png "Przycisku odświeżania.")  

12. Na liście składników pakietu redystrybucyjnego, wybierz **Visual Studio 2010 Tools for Office Runtime** pole wyboru.  

   Okno dialogowe może pojawić się pytaniem, czy chcesz zainstalować składnik redystrybucyjny. Jeśli to okno dialogowe nie pojawia, możesz przejść do [Określ, w której chcesz wdrożyć rozwiązanie na komputer użytkownika](#Location) części tego tematu.  

13. Jeśli pojawi się okno dialogowe, wybierz **nie** przycisku.  


## <a name="Location"></a>Określ, gdzie zainstalować rozwiązanie na komputerze użytkownika  

1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła, rozwiń węzeł **organizowania konfigurację** węzła, a następnie wybierz **ogólne informacje** pliku.  

2. Na pasku menu wybierz **widoku** > **Otwórz**.  

3. Na liście właściwości, wybierz opcję **Przeglądaj** znajdujący się obok **INSTALLDIR** właściwości.  

4. W **Ustaw INSTALLDIR** okno dialogowe, wybierz folder na komputerze użytkownika, w którym chcesz zainstalować rozwiązanie.  

   > [!NOTE]  
   >    Możesz tworzyć również podkatalogi w **Ustaw INSTALLDIR** okno dialogowe, otwierając menu skrótów dla każdego folderu na liście.  


## <a name="ConfigureRegistry"></a>Konfigurowanie dodatku narzędzi VSTO  
Można określić, czy chcesz dodatku narzędzi VSTO dla programów do zainstalowania dla wszystkich użytkowników komputera (na komputer) lub tylko dla użytkownika wykonującego instalację (na użytkownika).  

Jeśli chcesz obsługiwać instalacje dla poszczególnych komputerów, Utwórz dwa osobne pliki instalacyjne. Możesz podzielić instalatory na podstawie wersji pakietu Office (32-bitowych i 64-bitowy) lub Windows w wersji (32-bitowych i 64-bitowy) z systemem użytkownika.  

Instalacje na użytkownika wymagają tylko jednego Instalatora niezależnie od wersji pakietu Office lub Windows.  

> [!NOTE]  
> Ten rozdział ma zastosowanie tylko wtedy, gdy wdrażasz dodatku narzędzi VSTO. Jeżeli wdrażasz dostosowanie poziomu dokumentu, możesz od razu przejść do [Konfigurowanie dostosowywania poziomie dokumentu](#ConfigureDocument) sekcji.  


### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Aby określić, czy chcesz obsługiwać instalacje na użytkownika lub komputera  

1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, rozwiń **Zorganizuj swoją konfigurację** węzła, a następnie wybierz **ogólne informacje**  pliku.  

2. Na pasku menu wybierz **widoku** > **Otwórz**.  

   Właściwości ustawień projektu są wyświetlane.  

3. Na liście **AllUSERS** właściwości, określ, czy to rozwiązanie ma być zainstalowany dla wszystkich użytkowników komputera lub użytkownika, który instaluje rozwiązanie.  

   Aby zainstalować dodatku narzędzi VSTO dla bieżącego użytkownika, wybierz **ALLUSERS = "" (Instalacja na użytkownika)**. Aby zainstalować dodatku narzędzi VSTO dla wszystkich użytkowników komputera, wybierz **ALLUSERS = 1 (Instalacja dla poszczególnych komputerów)**  

   W następnej procedurze utworzysz klucze rejestru, aby umożliwić aplikacji Office wykrycie i załadowanie dodatku narzędzi VSTO. Zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  


### <a name="to-create-registry-keys"></a>Aby utworzyć klucze rejestru  

1. W **Eksploratora rozwiązań**, wybierz **Asystent projektu** węzła.  

   Na pasku menu wybierz **widoku** > **Otwórz**.  

2. W dolnej części **Asystenta projektu** wybierz **rejest aplikacji** przycisk, który przedstawiono na poniższej ilustracji.  

   ![Przycisk rejest aplikacji. ](../vsto/media/installshield-applicationregistry.gif "Przycisk rejest aplikacji.")  

   **Rejest aplikacji** zostanie wyświetlona strona.  

3. W obszarze **chcesz skonfigurować dane rejestru, które zainstaluje Twoja aplikacja?**, wybierz **tak** przycisku opcji.  

4. W **widok rejestru komputera docelowego** liście, Dodaj kluczową hierarchię, która włącza typ tworzonego Instalatora, w której chcesz utworzyć.  

   Ścieżka, skonfigurowanego w tej sekcji, zależy od tego, czy tworzysz Instalator dla poszczególnych użytkowników lub Instalatora na komputerze.  

   **Instalator na użytkownika**  

   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**  

   **Instalatory dla komputera, na podstawie wersji pakietu Office**  



| Wersja pakietu Office<br /><br /> | Ścieżka konfiguracji programu InstallShield<br /><br /> |
|----------------------------| - |
| 32-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64-bitowy<br /><br /> | **HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   **Instalatory dla komputera, na podstawie wersji Windows**  



| Wersja Windows<br /><br /> | Ścieżka konfiguracji programu InstallShield<br /><br /> |
|-----------------------------| - |
| 32-bitowa<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |
| 64-bitowy<br /><br /> | **HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br /> |

   > [!NOTE]  
   >    Instalator Windows 64-bitowego wymaga dwóch ścieżek rejestru, ponieważ jest to możliwe, aby użytkownicy uruchamiali 32-bitowych i 64-bitowej wersji pakietu Office na komputerze z systemem Windows 64-bitowych.  

   > [!NOTE]  
   >    Najlepszym rozwiązaniem jest rozpoczęcie nazwy dodatku narzędzi VSTO dla programów z nazwą Twojej firmy. Ta konwencja zwiększa prawdopodobieństwo, że klucz jest unikatowa i zmniejsza prawdopodobieństwo konfliktu z dodatku narzędzi VSTO od innego dostawcy. Dodatki, które mają taką samą nazwę na przykład, zastąpić wzajemne klucze rejestracyjne. To podejście nie gwarantuje, że klucz jest unikatowa, ale może zmniejszyć potencjalnych konfliktów nazw.  

5. Po utworzeniu hierarchii kluczy Otwórz menu skrótów dla **SampleCompany.ExcelAddIn** klucza, wybierz polecenie **New**, a następnie wybierz **wartość ciągu**.  

   Nowa wartość ciągu pojawia się w **danych rejestru komputera docelowego** listy. Nazwa wartości ciągu jest podświetlona tak, aby można było ją zmienić.  

6. Zmień wartość na **opis**.  

7. Powtórz tę procedurę, aby utworzyć następujące wartości.  



|Typ wartości<br /><br />|Nazwa<br /><br />|  
|--------------|--------|  
|Wartość ciągu<br /><br />|**FriendlyName**<br /><br />|  
|Wartość DWORD<br /><br />|**LoadBehavior**<br /><br />|  
|Wartość ciągu<br /><br />|**Manifest**<br /><br />|  

8. Otwórz menu skrótów dla **opis** wartości, a następnie wybierz **Modyfikuj**.  

   **Edytowanie danych** pojawi się okno dialogowe.  

9. W **dane wartości** tekstu wprowadź **dodatek wersji demonstracyjnej programu Excel**, a następnie wybierz **OK** przycisku.  

   Ten opis jest wyświetlany, gdy użytkownik otwiera aplikację Office, otwiera **opcje** okno dialogowe, a następnie w **Add-Ins** okienku wybiera dodatku narzędzi VSTO.  

10. Otwórz menu skrótów dla **FriendlyName** wartości, a następnie wybierz **Modyfikuj**.  

   **Edytowanie danych** pojawi się okno dialogowe.  

11. W **dane wartości** tekstu wprowadź **dodatek wersji demonstracyjnej programu Excel**, a następnie wybierz **OK** przycisku.  

   Ten ciąg jest wyświetlana w **dodatki COM** okno dialogowe w aplikacji pakietu Office. Domyślnie wartość ciągu jest identyfikatorem dodatku narzędzi VSTO  

12. Otwórz menu skrótów dla **LoadBehavior** wartości, a następnie wybierz **Modyfikuj**.  

   **Edytowanie danych** pojawi się okno dialogowe.  

13. W **dane wartości** tekstu wprowadź **3**, a następnie wybierz **OK** przycisku.  

   Wartość 3 ładuje dodatek narzędzi VSTO dla programów, podczas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat wartości Loadbehaviour, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  

14. Otwórz menu skrótów dla **manifestu** wartości, a następnie wybierz **Modyfikuj**.  

   **Edytowanie danych** pojawi się okno dialogowe.  

15. W **dane wartości** tekstu wprowadź **File:///[INSTALLDIR]ExcelAddIn.VSTO|vstolocal**, a następnie wybierz **OK** przycisku.  

   Visual Studio 2010 Tools for Office Runtime używa tej ścieżki, aby zlokalizować manifest wdrożenia. **[INSTALLDIR]** porcja ścieżki to makro, które mapuje **INSTALLDIR** właściwość **ogólne informacje** strony właściwości projektu instalatora InstallShield. Ta właściwość określa lokalizację na komputerze docelowym, aby zainstalować dodatek narzędzi VSTO dla programów. **| Vstolocal** sufiks gwarantuje, że rozwiązanie jest ładowane z folderu instalacji, a nie pamięci podręcznej funkcji ClickOnce.  

> [!IMPORTANT]  
> Jeśli tworzysz region formularza niestandardowego w dodatku narzędzi VSTO dla programu Outlook, należy utworzyć więcej wpisów rejestru, aby zarejestrować region za pomocą programu Outlook. Aby uzyskać więcej informacji, zobacz [regionów formularza wpisy rejestru dla programu Outlook](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).  


## <a name="ConfigureDocument"></a>Konfigurowanie dostosowywania poziomie dokumentu  
Ten rozdział ma zastosowanie tylko wtedy, gdy wdrażasz dostosowanie poziomu dokumentu. Jeżeli wdrażasz dodatek narzędzi VSTO dla programów, możesz przejść bezpośrednio do [projektu Instalatora kompilacji](#Build) sekcji.  

Dostosowania poziomu dokumentu nie używają kluczy rejestru. Zamiast tego niestandardowe właściwości dokumentu zawierają lokalizację manifestu wdrażania.  

Aby zmodyfikować właściwości niestandardowe, należy utworzyć program, który usuwa dostosowanie poziomu dokumentu z dokumentu, modyfikuje odpowiednie właściwości, a następnie ponowne dołączenie następuje ponowne dostosowanie do dokumentu. Następnie Utwórz akcję niestandardową, która uruchamia program, a potem dodaje tę akcję do swojej instalacji projektu.  

### <a name="to-create-a-program-that-modifies-document-properties"></a>Aby utworzyć program, który modyfikuje właściwości dokumentu.  

1. Na pasku menu wybierz **pliku** > **Dodaj** > **nowy projekt**.  

   **Dodaj nowy projekt** pojawi się okno dialogowe.  

2. W okienku szablonów, w obszarze węzła dla języka, którego chcesz użyć, wybierz **Windows** folderu.  

3. Na liście typów projektów dla **Windows**, wybierz **aplikację Konsolową** szablonu.  

4. Nadaj projektowi nazwę **SetExcelDocumentProperties**, a następnie wybierz **OK** przycisku.  

5. W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** przycisk, otwórz menu skrótów dla **SetExcelDocumentProperties** węzła projektu, a następnie wybierz **Dodaj odwołanie**.  

6. W **Menadżer odwołań** okna dialogowego wybierz **rozszerzenia** kartę, a następnie zaznacz pole wyboru obok następujących zestawów, a następnie wybierz **OK** przycisku.  


   - Obiektów Microsoft.VisualStudio.Tools.Applications.Runtime  

   - Microsoft.VisualStudio.Tools.Applications.ServerDocument  

7. W **Eksploratora rozwiązań**, wybierz **Program.cs** (w przypadku aplikacji C#) lub **Module1.vb** pliku (dla aplikacji Visual Basic).  

8. Na pasku menu wybierz **widoku** > **Otwórz**.  

9. Zastąp zawartości całego pliku następującym kodem.  

[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]  

10. Skompiluj projekt.  


### <a name="to-add-a-custom-action-that-runs-your-program"></a>Aby dodać niestandardową akcję, która uruchamia Twój program  

1. W **Eksploratora rozwiązań**, rozwiń węzeł **OfficeAddInSetup** węzła projektu, a następnie wybierz **Asystent projektu** pliku, który przedstawiono na poniższej ilustracji.  

   ![Asystent pliku w Eksploratorze rozwiązań projektu](../vsto/media/installshield-projectassistant.png "projektu Asystenta plik w Eksploratorze rozwiązań")  

2. Na pasku menu wybierz **widoku** > **Otwórz**.  

3. W dolnej części **Asystenta projektu** wybierz **pliki aplikacji** przycisk, który przedstawiono na poniższej ilustracji.  

   ![Przycisk pliki aplikacji. ](../vsto/media/installshield-applicationfiles.png "Przycisk pliki aplikacji.")  

4. W **pliki aplikacji** wybierz **Dodaj dane wyjściowe projektu** przycisku.  

   **Visual Studio Output Selector** pojawi się okno dialogowe.  

5. W obszarze **SetExcelDocumentProperties** węzeł **podstawowe wyjście** pole wyboru, a następnie wybierz **OK** przycisku.  

6. W **Eksploratora rozwiązań**w obszarze **OfficeAddInSetup** węzła, rozwiń węzeł **zdefiniować wymagania dotyczące konfiguracji i akcji** węzła, a następnie wybierz **niestandardowe Akcje** folderu.  

7. Na pasku menu wybierz **widoku** > **Otwórz**.  

   Lista zdarzeń są wyświetlane w okienku na stronie ekranu.  

   > [!NOTE]  
   >    Tylko kilka zdarzeń, które pojawiają się na tej liście są dostępne w InstallShield Limited Edition. W tej procedurze należy uruchomić program za pomocą **okno dialogowe po instalacji zakończonej sukcesem** zdarzeń.  

8. Na liście zdarzeń w obszarze **akcje niestandardowe podczas instalacji**, otwórz menu skrótów dla **okno dialogowe po instalacji zakończonej sukcesem** zdarzeń, a następnie wybierz **nowego pliku EXE**.  

   Akcja niestandardowa o nazwie **NewCustomAction1** pojawia się w obszarze **okno dialogowe po instalacji zakończonej sukcesem** zdarzeń. Zestaw właściwości niestandardowych akcji pojawia się w okienku obok zdarzenia.  

   > [!IMPORTANT]  
   >    Dwa **okno dialogowe po instalacji zakończonej sukcesem** zdarzenia są wyświetlane na liście zdarzeń. Upewnij się, że wybrano wystąpienie **okno dialogowe po instalacji zakończonej sukcesem** zdarzenia, które pojawia się w obszarze **akcje niestandardowe podczas instalacji** węzła.  

9. Na liście **lokalizacja źródłowa** właściwości, wybierz **instalowane wraz z produktem**.  

10. Wybierz **Przeglądaj** znajdujący się obok **nazwy pliku** właściwości.  

11. W **Przeglądaj w poszukiwaniu pliku docelowego** okno dialogowe, przejdź do **SetExcelDocumentProperties.Primary.output** , a następnie wybierz **Otwórz** przycisku.  

    Lokalizacja tego pliku zależy od folderu, który został określony dla **INSTALLDIR** właściwości projektu Instalatora. Na przykład, jeśli ustawisz tę właściwość do folderu, który nosi nazwę **[Osobistyfolder] DemoWorkbookApp**, można znaleźć **SetExcelDocumentProperties.Primary.output** plików, przechodząc do **[ Folderprogramfiles] \DemoWorkbookApp**.  

    W następnych kilku krokach możesz uzyskać identyfikator rozwiązania dokumentu i następnie przekaż ten identyfikator jako parametr do aplikacji konsoli. Należy także przekazać lokalizację dokumentu, manifest wdrażania oraz zestaw dokumentów.  

12. Otwórz menu skrótów dla **ExcelWorkbook** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze Windows** lub **Otwórz Folder w Eksploratorze plików** w zależności od operacyjne System.  

    Zostanie otwarty folder, który zawiera rozwiązanie.  

13. Otwórz plik projektu rozwiązań w Notatniku. Dla projektów języka Visual Basic nazwa pliku jest *ExcelWorkbook.vbproj*. Dla projektów C#, nazwa pliku jest *ExcelWorkbook.csproj*.  

14. W pliku projektu, wyszukaj **&lt;SolutionID&gt;** elementu, skopiuj jego wartość do Schowka, a następnie zamknij Notatnik.  

    Tę wartość przekazuje się do aplikacji konsoli jako parametr.  

15. Na stronie właściwości **NewCustomAction1**ustaw **wiersza polecenia** właściwość poniższym wierszu tekstu.  


   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"  
   ```  

16. Zastąp **swój identyfikator rozwiązania** identyfikatorem rozwiązania, który został skopiowany do Schowka.  

   > [!IMPORTANT]  
   >    Przetestuj swój Instalatora, aby sprawdzić, czy aplikacja konsoli który uruchamia akcję niestandardową ma dostęp do dokumentów w katalogu [INSTALLDIR]. Niektóre katalogi na komputerze użytkownika mogą wymagać dostępu administracyjnego (na przykład katalogu Program Files). Jeśli wdrażasz swoje rozwiązanie do katalogu, który wymaga dostępu administracyjnego, należy otworzyć **właściwości** okna dialogowego *setup.exe* plików, wybierz **zgodności** , a następnie wybierz pozycję **Uruchom ten program jako administrator** pole wyboru przed udostępnieniem Instalatora. Jeśli nie chcesz, aby użytkownicy, aby uruchomić program instalacyjny z uprawnieniami administracyjnymi, ustaw właściwość [INSTALLDIR] katalogu, do którego użytkownik prawdopodobnie ma dostęp, takie jak **dokumenty** katalogu. Aby uzyskać więcej informacji, zobacz [określić, które chcesz zainstalować rozwiązanie na komputer użytkownika](#Location) części tego tematu.  


## <a name="Build"></a>Projektu Instalatora kompilacji  

1. W **Eksploratora rozwiązań**, rozwiń węzeł **przygotowań do wydania** węzła, a następnie wybierz **wersji** pliku.  

2. Na pasku menu wybierz **widoku** > **Otwórz**.  

   **Kompilacje** zostanie otwarty Eksplorator w okienku bocznym tak, aby można było wybrać typ wersji, której chcesz utworzyć.  

3. W **kompilacje** explorer, wybierz **SingleImage** folderu.  

4. W okienku obok **kompilacje** explorer, wybierz **Setup.exe** kartę.  

5. W **Setup.exe** stronę właściwości z **lokalizacja wstępnie wymaganych składników InstallShield** wybierz **Pobierz z sieci**.  

6. Na pasku menu wybierz **kompilacji** > **programu Configuration Manager**.  

7. W **Konfiguracja rozwiązania aktywnego** wybierz **SingleImage**.  

8. W **projektu kontekstów** tabeli w **konfiguracji** kolumny **OfficeAddInSetup** projektu, wybierz **SingleImage**, a następnie Wybierz **Zamknij** przycisku.  

9. Na pasku menu wybierz **kompilacji** > **skompiluj OfficeAddInSetup**.  

   Po zakończeniu kompilacji, można zlokalizować *setup.exe* pliku **OfficeAddInSetup** projektu w następującej lokalizacji: <em>OfficeAddInSetupProjectRoot</em>**\OfficeAddInSetup\Express\SingleImage\DiskImages\DISK1\\**  


## <a name="see-also"></a>Zobacz także  
[Wymagania wstępne rozwiązania pakietu Office wdrożenia](https://msdn.microsoft.com/library/9f672809-43a3-40a1-9057-397ce3b5126e)  
[Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
[Wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md)  
[Przegląd właściwości niestandardowego dokumentu](../vsto/custom-document-properties-overview.md)  
[Udzielanie zaufania do rozwiązań pakietu Office](../vsto/granting-trust-to-office-solutions.md)  
[Udzielanie zaufania do dokumentów](../vsto/granting-trust-to-documents.md)  
[Wdrażanie programu Visual Studio 2010 Tools dla rozwiązań pakietu Office przy użyciu Instalatora Windows](http://go.microsoft.com/fwlink/?LinkId=201807)  
