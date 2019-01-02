---
title: Wpisy rejestru dotyczące dodatków narzędzi VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3436ddcdcb8c521985487738d4045e1e1bbd830a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909115"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Wpisy rejestru dotyczące dodatków narzędzi VSTO
  W przypadku wdrażania dodatków narzędzi VSTO, które są tworzone za pomocą programu Visual Studio, należy utworzyć określony zbiór wpisów rejestru. Te wpisy rejestru Podaj informacje, które umożliwiają aplikacji Microsoft Office wykrycie i załadowanie dodatku narzędzi VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Podczas tworzenia projektu Visual Studio tworzy te wpisy rejestru na komputerze deweloperskim, tak że można łatwo uruchomić i debugować dodatku narzędzi VSTO. Jeśli używasz technologii ClickOnce do wdrażania dodatku narzędzi VSTO dla programów wpisy rejestru są tworzone automatycznie na komputerze użytkownika końcowego. Jeśli używasz Instalatora Windows do wdrożenia dodatku narzędzi VSTO dla programów, należy skonfigurować projekt InstallShield Limited Edition, aby utworzyć wpisy rejestru na komputerze użytkownika końcowego.  
  
 Aby uzyskać więcej informacji na temat sposobu wpisy rejestru są używane podczas procesu ładowania dla dodatków narzędzi VSTO zobacz [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  W tym temacie, tekst *identyfikator dodatku* reprezentuje unikatowy identyfikator dla dodatku VSTO. Domyślnie identyfikator jest nazwy zestawu dodatku narzędzi VSTO.  
  
## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Rejestrowanie dodatków narzędzi VSTO dla bieżącego użytkownika, a wszyscy użytkownicy  
 Dodatek narzędzi VSTO dla programów jest zainstalowany, możesz go zarejestrować na dwa sposoby:  
  
- Dla bieżącego użytkownika (oznacza to, że jest dostępna tylko dla użytkownika, który jest zalogowany na komputerze jest zainstalowany dodatku narzędzi VSTO). W tym przypadku wpisy rejestru zostały utworzone na podstawie **HKEY_CURRENT_USER**.  
  
- Dla wszystkich użytkowników (każdy użytkownik, który loguje się do komputera można używać dodatku narzędzi VSTO). W tym przypadku wpisy rejestru zostały utworzone na podstawie **HKEY_LOCAL_MACHINE**.  
  
  Wszystkie dodatków narzędzi VSTO tworzone przy użyciu programu Visual Studio można zarejestrować dla bieżącego użytkownika. Jednak można zarejestrować dodatków narzędzi VSTO dla wszystkich użytkowników tylko w niektórych scenariuszach. Te scenariusze są zależne od wersji pakietu Microsoft Office na komputerze i sposób wdrożenia dodatku narzędzi VSTO.  
  
### <a name="microsoft-office-version"></a>Wersja Microsoft Office  
 Aplikacje pakietu Office można załadować dodatków narzędzi VSTO, które są zarejestrowane w ramach **HKEY_LOCAL_MACHINE** lub **HKEY_CURRENT_USER**.  
  
 Aby załadować dodatków narzędzi VSTO, które są zarejestrowane w ramach **HKEY_LOCAL_MACHINE**, komputery muszą mieć pakiet aktualizacji 976477 zainstalowane. Aby uzyskać więcej informacji, zobacz [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Typ wdrożenia  
 Jeśli używasz technologii ClickOnce do wdrażania dodatku narzędzi VSTO dodatku narzędzi VSTO można zarejestrować tylko dla bieżącego użytkownika. Jest to spowodowane ClickOnce obsługuje tylko tworzenie klucze w ramach **HKEY_CURRENT_USER**. Jeśli chcesz zarejestrować dodatku narzędzi VSTO dla wszystkich użytkowników na komputerze, musi być wdrażania dodatku narzędzi VSTO Instalatora Windows. Aby uzyskać więcej informacji na temat tych typów wdrożeń, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) i [wdrażania rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Wpisy rejestru  
 Wymagane dodatku narzędzi VSTO wpisy rejestru znajdują się w następującym kluczu rejestru dla wszystkich aplikacji, z wyjątkiem programu Visio, gdzie *głównego* jest **HKEY_CURRENT_USER** lub **HKEY_LOCAL_MACHINE** .  
  
 **Wszystkie aplikacje z wyjątkiem programu Visio**  
  
|Wersja pakietu Office|Ścieżka konfiguracji|  
|--------------------|------------------------|  
|32-bitowa|*Główny*\Software\Microsoft\Office\\*Nazwa aplikacji*\Addins\\*identyfikator dodatku*|  
|64-bitowy|*Główny*\Software\Wow6432Node\Microsoft\Office\\*Nazwa aplikacji*\Addins\\*identyfikator dodatku*|  
  
 **Programu Visio**  
  
|Wersja pakietu Office|Ścieżka konfiguracji|  
|--------------------|------------------------|  
|32-bitowa|*Główny*\Software\Microsoft\Visio\Addins\\*identyfikator dodatku*|  
|64-bitowy|*Główny*\Software\Wow6432Node\Visio\Addins\\*identyfikator dodatku*|  
  
 W poniższej tabeli wymieniono wpisy w tym kluczu rejestru.  
  
|Wpis|Typ|Wartość|  
|-----------|----------|-----------|  
|**Opis**|REG_SZ|Wymagana. Krótki opis dodatku narzędzi VSTO.<br /><br /> Ten opis jest wyświetlany, gdy użytkownik wybierze dodatku narzędzi VSTO dla programów w **Add-Ins** okienku **opcje** okno dialogowe w aplikacji Microsoft Office.|  
|**FriendlyName**|REG_SZ|Wymagana. Opisowa nazwa dodatku narzędzi VSTO, która jest wyświetlana w **dodatki COM** okno dialogowe w aplikacji Microsoft Office. Wartość domyślna to identyfikator dodatku narzędzi VSTO|  
|**LoadBehavior**|REG_DWORD|Wymagana. Wartość, która określa, kiedy aplikacja próbuje załadować dodatku narzędzi VSTO dla programów i bieżący stan dodatku narzędzi VSTO (załadowane lub zwolnione).<br /><br /> Domyślnie ten wpis jest ustawiony na 3, która określa, że dodatek narzędzi VSTO dla programów jest ładowany podczas uruchamiania. Aby uzyskać więcej informacji, zobacz [wartości Loadbehaviour](#LoadBehavior). **Uwaga:**  Jeśli dodatku narzędzi VSTO wyłączenia przez użytkownika, ta akcja modyfikuje **LoadBehavior** wartość w **HKEY_CURRENT_USER** gałąź rejestru. Dla każdego użytkownika, wartość **LoadBehavior** wartość w gałęzi HKEY_CURRENT_USER zastępuje to domyślne **LoadBehavior** zdefiniowane w **HKEY_LOCAL_MACHINE** hive.|  
|**Manifest**|REG_SZ|Wymagana. Pełna ścieżka pliku manifestu wdrożenia dla dodatku narzędzi VSTO dla programów. Ścieżka może być lokalizacji na komputerze lokalnym udziału sieciowego (UNC) lub serwera sieci Web (HTTP).<br /><br /> Jeśli używasz Instalatora Windows, aby wdrożyć to rozwiązanie, należy dodać prefiks **file:///** do **manifestu** ścieżki. Należy również Dołącz ciąg  **&#124;vstolocal** (czyli znaku kreski pionowej **&#124;** następuje **vstolocal**) na końcu tej ścieżki. Daje to gwarancję, że rozwiązanie jest ładowane z folderu instalacji, a nie pamięci podręcznej funkcji ClickOnce. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Uwaga:**  Podczas tworzenia dodatku narzędzi VSTO dla programów na komputerze deweloperskim w programie Visual Studio automatycznie dołącza  **&#124;vstolocal** ciągu do tego wpisu rejestru.|  
  
###  <a name="OutlookEntries"></a> Wpisy rejestru dla regionów formularza programu Outlook  
 Jeśli tworzysz region formularza niestandardowego w dodatku narzędzi VSTO dla programu Outlook, wpisy rejestru dodatkowe są używane do rejestrowania regionu formularza programu Outlook. Te wpisy są tworzone w kluczu rejestru różnych dla każdej klasy wiadomości, który obsługuje regionu formularza. Te klucze rejestru znajdują się w następującej lokalizacji, gdzie *głównego* jest **HKEY_CURRENT_USER** lub **HKEY_LOCAL_MACHINE**.  
  
 *Główny*\Software\Microsoft\Office\Outlook\FormRegions\\*message — klasa*  
  
 Podobnie jak inne wpisy rejestru współużytkowane przez wszystkie dodatki narzędzi VSTO dla programów, Visual Studio tworzy formularz region wpisy rejestru na komputerze deweloperskim podczas kompilowania projektu. Jeśli używasz technologii ClickOnce do wdrażania dodatku narzędzi VSTO dla programów wpisy rejestru są tworzone automatycznie na komputerze użytkownika końcowego. Jeśli używasz Instalatora Windows do wdrożenia dodatku narzędzi VSTO dla programów, należy skonfigurować projekt InstallShield Limited Edition, aby utworzyć wpisy rejestru na komputerze użytkownika końcowego.  
  
 Aby uzyskać więcej informacji na temat wpisów rejestru regionu formularza, zobacz [Określ lokalizację regionów formularzy w niestandardowym formularzu](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Aby uzyskać więcej informacji na temat regionów formularzy programu Outlook, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> Wartości Loadbehaviour  
 **LoadBehavior** wpis w *głównego*\Software\Microsoft\Office\\*Nazwa aplikacji*\Addins\\*dodatku Identyfikator* klucz zawiera bitowa kombinacja wartości, które określają zachowanie wykonywania dodatku narzędzi VSTO. Znaczącego bitu (wartości 0 i 1) wskazuje, czy dodatku narzędzi VSTO jest obecnie załadowane lub załadowane. Inne usługi bits wskazywać, kiedy aplikacja próbuje załadować dodatku narzędzi VSTO.  
  
 Zazwyczaj **LoadBehavior** wpis ma być równa 0, 3 lub 16 (w zapisie dziesiętnym) po dodatku narzędzi VSTO jest zainstalowany na komputerach użytkowników końcowych. Domyślnie program Visual Studio ustawia **LoadBehavior** wpisu dodatku narzędzi VSTO dla programów do 3 podczas kompilowania lub opublikować go.  
  
 W poniższej tabeli wymieniono wszystkie możliwe wartości **LoadBehavior** wpisu. Niektóre opisy w tej tabeli można znaleźć na potrzeby ładowania dodatku narzędzi VSTO dla programów, ręcznie lub programowo. Aby załadować dodatku narzędzi VSTO ręcznie, zaznacz pole wyboru obok dodatku narzędzi VSTO dla programów w **dodatki COM** okno dialogowe w aplikacji. Aby załadować dodatku narzędzi VSTO programowo, należy ustawić <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> właściwość <xref:Microsoft.Office.Core.COMAddIn> obiekt, który reprezentuje dodatku narzędzi VSTO dla programów do **true**.  
  
|Wartość (w zapisie dziesiętnym)|Stan dodatku narzędzi VSTO|Zachowanie VSTO dodatku obciążenia|Opis|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Zwolniono|Nie są ładowane automatycznie|Aplikacja nigdy nie próbuje załadować dodatku narzędzi VSTO automatycznie. Użytkownik może próbować ręcznie załadować dodatku narzędzi VSTO lub dodatku narzędzi VSTO dla programów może być załadowany programowo.<br /><br /> Jeśli dodatku narzędzi VSTO zostanie pomyślnie załadowana, **LoadBehavior** wartość pozostaje 0, ale stan dodatku narzędzi VSTO dla programów w **dodatki COM** okno dialogowe jest aktualizowana w celu wskazania, że dodatku narzędzi VSTO zostanie załadowana.|  
|1|załadowano|Nie są ładowane automatycznie|Aplikacja nigdy nie próbuje załadować dodatku narzędzi VSTO automatycznie. Użytkownik może próbować ręcznie załadować dodatku narzędzi VSTO lub dodatku narzędzi VSTO dla programów może być załadowany programowo.<br /><br /> Mimo że **dodatki COM** okno dialogowe wskazuje, że dodatek narzędzi VSTO dla programów jest załadowany po uruchomieniu aplikacji, dodatku narzędzi VSTO dla programów nie został załadowany, dopóki nie jest ładowany ręcznie lub programowo.<br /><br /> Gdy aplikacja ładuje się pomyślnie dodatku narzędzi VSTO **LoadBehavior** wartość zmienia się od 0 i pozostaje na 0, po zamknięciu aplikacji.|  
|2|Zwolniono|Ładowania przy uruchamianiu|Aplikacja nie podejmuje próby ładowania dodatku narzędzi VSTO automatycznie. Użytkownik może próbować ręcznie załadować dodatku narzędzi VSTO lub dodatku narzędzi VSTO dla programów może być załadowany programowo.<br /><br /> Gdy aplikacja ładuje się pomyślnie dodatku narzędzi VSTO **LoadBehavior** wartość zmienia się na 3 i pozostaje na poziomie 3 po zamknięciu aplikacji.|  
|3|załadowano|Ładowania przy uruchamianiu|Aplikacja próbuje załadować dodatku narzędzi VSTO dla programów, podczas uruchamiania aplikacji. Jest wartością domyślną, podczas tworzenia lub opublikować dodatku narzędzi VSTO dla programu Visual Studio.<br /><br /> Gdy aplikacja ładuje się pomyślnie dodatku narzędzi VSTO **LoadBehavior** wartość pozostaje 3. Jeśli wystąpi błąd podczas ładowania dodatku narzędzi VSTO **LoadBehavior** wartość zmienia się na 2 i pozostaje na poziomie 2 po zamknięciu aplikacji.|  
|8|Zwolniono|Ładowanie na żądanie|Aplikacja nie podejmuje próby ładowania dodatku narzędzi VSTO automatycznie. Użytkownik może próbować ręcznie załadować dodatku narzędzi VSTO lub dodatku narzędzi VSTO dla programów może być załadowany programowo.<br /><br /> Gdy aplikacja ładuje się pomyślnie dodatku narzędzi VSTO **LoadBehavior** zmiany wartości na 9.|  
|9|załadowano|Ładowanie na żądanie|Dodatek narzędzi VSTO dla programów będą ładowane tylko wtedy, gdy aplikacja wymaga, np. gdy użytkownik kliknie element interfejsu użytkownika, korzysta z funkcji w dodatku narzędzi VSTO dla programów (na przykład niestandardowy przycisk na Wstążce).<br /><br /> Gdy aplikacja ładuje się pomyślnie dodatku narzędzi VSTO **LoadBehavior** wartość pozostaje 9, ale stan dodatku narzędzi VSTO dla programów w **dodatki COM** okno dialogowe zostanie zaktualizowany, aby wskazać, że dodatku narzędzi VSTO obecnie załadowane. Jeśli wystąpi błąd podczas ładowania dodatku narzędzi VSTO **LoadBehavior** zmiany wartości na 8.|  
|16|załadowano|Załaduj po raz pierwszy, a następnie załaduj na żądanie|Ta wartość ma dodatku narzędzi VSTO dla programów mają zostać załadowane na żądanie. Dodatek narzędzi VSTO dla programów ładowania aplikacji, gdy użytkownik uruchamia aplikację po raz pierwszy. Przy następnym razem użytkownik uruchomi aplikację, wszelkie elementy interfejsu użytkownika, które są definiowane przez dodatku narzędzi VSTO ładowania aplikacji, ale dodatku narzędzi VSTO dla programów nie został załadowany, dopóki użytkownik kliknie element interfejsu użytkownika, który jest skojarzony z dodatku narzędzi VSTO.<br /><br /> Gdy pomyślnie ładowania aplikacji dodatku narzędzi VSTO po raz pierwszy **LoadBehavior** wartość pozostaje 16, gdy jest ładowany dodatku narzędzi VSTO. Po zamknięciu aplikacji **LoadBehavior** zmiany wartości na 9.|  
  
## <a name="see-also"></a>Zobacz także  
 [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
