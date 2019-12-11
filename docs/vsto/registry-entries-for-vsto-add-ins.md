---
title: Wpisy rejestru dotyczące dodatków narzędzi VSTO
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 464820258e5c20474d74f92eb108344deccc49f1
ms.sourcegitcommit: 0a8855572c6c88f4b2ece232c04aa124fbd9cec3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955052"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Wpisy rejestru dotyczące dodatków narzędzi VSTO
  Podczas wdrażania dodatków VSTO utworzonych przy użyciu programu Visual Studio należy utworzyć określony zbiór wpisów rejestru. Te wpisy rejestru zawierają informacje umożliwiające aplikacji Microsoft Office odnajdywania i ładowania dodatku VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Podczas kompilowania projektu program Visual Studio tworzy te wpisy rejestru na komputerze deweloperskim, dzięki czemu można łatwo uruchamiać i debugować dodatek narzędzi VSTO. Jeśli używasz technologii ClickOnce do wdrożenia dodatku VSTO, wpisy rejestru są tworzone automatycznie na komputerze użytkownika końcowego. Jeśli używasz Instalator Windows do wdrożenia dodatku VSTO, musisz skonfigurować projekt InstallShield Limited Edition, aby utworzyć wpisy rejestru na komputerze użytkownika końcowego.

 Aby uzyskać więcej informacji na temat sposobu użycia wpisów rejestru w procesie ładowania dla dodatków narzędzi VSTO, zobacz [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> W tym temacie *Identyfikator dodatku* tekstu reprezentuje unikatowy identyfikator dodatku VSTO. Domyślnie identyfikator jest nazwą zestawu dodatku VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Zarejestruj Dodatki narzędzia VSTO dla bieżącego użytkownika a wszyscy użytkownicy
 Po zainstalowaniu dodatku VSTO można go zarejestrować na dwa sposoby:

- Tylko dla bieżącego użytkownika (oznacza to, że jest dostępny tylko dla użytkownika, który jest zalogowany na komputerze po zainstalowaniu dodatku VSTO). W takim przypadku wpisy rejestru są tworzone w obszarze **HKEY_CURRENT_USER**.

- Dla wszystkich użytkowników (oznacza to, że każdy Użytkownik logujący się na komputerze może korzystać z dodatku VSTO). W takim przypadku wpisy rejestru są tworzone w obszarze **HKEY_LOCAL_MACHINE**.

  Wszystkie dodatki narzędzi VSTO tworzone za pomocą programu Visual Studio mogą być zarejestrowane dla bieżącego użytkownika. Jednak dodatki narzędzi VSTO mogą być rejestrowane dla wszystkich użytkowników tylko w określonych scenariuszach. Te scenariusze zależą od wersji Microsoft Office na komputerze oraz sposobu wdrożenia dodatku VSTO.

### <a name="deployment-type"></a>Typ wdrożenia
 Jeśli używasz technologii ClickOnce do wdrożenia dodatku VSTO, dodatek VSTO może być zarejestrowany tylko dla bieżącego użytkownika. Dzieje się tak, ponieważ ClickOnce obsługuje tylko tworzenie kluczy w obszarze **HKEY_CURRENT_USER**. Jeśli chcesz zarejestrować dodatek Narzędzia VSTO dla wszystkich użytkowników na komputerze, musisz użyć Instalator Windows do wdrożenia dodatku VSTO. Aby uzyskać więcej informacji na temat tych typów wdrożeń, zobacz [wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) i [wdrażanie rozwiązania pakietu office przy użyciu Instalator Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Wpisy rejestru
 Wymagane wpisy rejestru dodatku VSTO znajdują się w następujących kluczach rejestru, w których *katalog główny* jest **HKEY_CURRENT_USER** lub **HKEY_LOCAL_MACHINE** w zależności od tego, czy instalacja jest dla bieżącego użytkownika, czy dla wszystkich użytkowników.

|Aplikacja pakietu Office|Ścieżka konfiguracyjna|
|------------------|------------------|
|Visio|*Główny*\Software\Microsoft\\\\*programu Visio*\Addins *Identyfikator dodatku*|
|Wszystkie inne|*Główna*\Software\Microsoft\Office\\*Nazwa aplikacji pakietu Office*\Addins\\*Identyfikator dodatku*|

> [!NOTE]
> Jeśli Instalator jest przeznaczony dla wszystkich użytkowników w systemie 64-bitowym, zaleca się, aby zawierał dwa wpisy rejestru, jeden pod HKEY_LOCAL_MACHINE \Software\Microsoft i jeden w HKEY_LOCAL_MACHINE \Software\\**Wow6432Node**\Microsoft. Wynika to z faktu, że użytkownicy mogą korzystać z wersji pakietu Office 32-bitowej lub 64-bitowej na komputerze.
>
>Jeśli Instalator jest przeznaczony dla bieżącego użytkownika, nie trzeba go instalować do WOW6432Node, ponieważ ścieżka \Software HKEY_CURRENT_USER jest udostępniona.
>
>Aby uzyskać więcej informacji [, zobacz 32-bitowe i 64-bitowe dane aplikacji w rejestrze](https://docs.microsoft.com/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 Poniższa tabela zawiera listę wpisów w tym kluczu rejestru.

|Entry|Typ|Wartość|
|-----------|----------|-----------|
|**Opis**|REG_SZ|Wymagany. Krótki opis dodatku narzędzi VSTO.<br /><br /> Ten opis jest wyświetlany, gdy użytkownik wybierze dodatek VSTO w okienku **dodatków** okna dialogowego **opcje** w aplikacji Microsoft Office.|
|**FriendlyName**|REG_SZ|Wymagany. Opisowa nazwa dodatku VSTO, który jest wyświetlany w oknie dialogowym **dodatków COM** w aplikacji Microsoft Office. Wartość domyślna to identyfikator dodatku VSTO.|
|**LoadBehavior**|REG_DWORD|Wymagany. Wartość określająca, kiedy aplikacja próbuje załadować dodatek narzędzi VSTO i bieżący stan dodatku VSTO (załadowany lub zwolniony).<br /><br /> Domyślnie ten wpis jest ustawiony na 3, co oznacza, że dodatek VSTO jest ładowany podczas uruchamiania. Aby uzyskać więcej informacji, zobacz [LoadBehavior wartości](#LoadBehavior). **Uwaga:**  Jeśli użytkownik wyłączy dodatek VSTO, ta akcja modyfikuje wartość **LoadBehavior** w gałęzi rejestru **HKEY_CURRENT_USER** . Dla każdego użytkownika wartość **LoadBehavior** w gałęzi HKEY_CURRENT_USER zastępuje domyślny **LoadBehavior** zdefiniowany w gałęzi **HKEY_LOCAL_MACHINE** .|
|**Manifest**|REG_SZ|Wymagany. Pełna ścieżka manifestu wdrożenia dla dodatku VSTO. Ścieżka może być lokalizacją na komputerze lokalnym, udziałem sieciowym (UNC) lub serwerem sieci Web (HTTP).<br /><br /> Jeśli używasz Instalator Windows do wdrożenia rozwiązania, musisz dodać prefiks **File:///** do ścieżki **manifestu** . Należy również dołączyć ciąg  **&#124;vstolocal** (czyli znak **&#124;** potoku, a następnie **vstolocal**) na końcu tej ścieżki. Dzięki temu Twoje rozwiązanie zostanie załadowane z folderu instalacji, a nie z pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego przy użyciu Instalator Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Uwaga:**  Po utworzeniu dodatku narzędzi VSTO na komputerze deweloperskim program Visual Studio automatycznie dołącza ciąg  **&#124;vstolocal** do tego wpisu rejestru.|

### <a name="OutlookEntries"></a>Wpisy rejestru dla regionów formularzy programu Outlook
 Jeśli utworzysz niestandardowy region formularza w dodatku VSTO dla programu Outlook, do zarejestrowania regionu formularza w programie Outlook są używane dodatkowe wpisy rejestru. Te wpisy są tworzone w innym kluczu rejestru dla każdej klasy komunikatów obsługiwanej przez region formularza. Te klucze rejestru znajdują się w następującej lokalizacji, gdzie *root* jest **HKEY_CURRENT_USER** lub **HKEY_LOCAL_MACHINE**.

 *Root*\Software\Microsoft\Office\Outlook\FormRegions\\*message class*

 Podobnie jak w przypadku innych wpisów rejestru udostępnionych przez wszystkie dodatki narzędzi VSTO, program Visual Studio tworzy wpisy rejestru regionów formularzy na komputerze deweloperskim podczas kompilowania projektu. Jeśli używasz technologii ClickOnce do wdrożenia dodatku VSTO, wpisy rejestru są tworzone automatycznie na komputerze użytkownika końcowego. Jeśli używasz Instalator Windows do wdrożenia dodatku VSTO, musisz skonfigurować projekt InstallShield Limited Edition, aby utworzyć wpisy rejestru na komputerze użytkownika końcowego.

 Aby uzyskać więcej informacji na temat wpisów rejestru regionów formularzy, zobacz [Określanie lokalizacji regionu formularza w formularzu niestandardowym](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Aby uzyskać więcej informacji na temat regionów formularzy programu Outlook, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="LoadBehavior"></a>LoadBehavior wartości
 Wpis **LoadBehavior** w *katalogu głównym*\Software\Microsoft\Office\\*Nazwa aplikacji*\Addins\\klucz *identyfikatora dodatku* zawiera bitową kombinację wartości, które określają zachowanie w czasie wykonywania dodatku VSTO. Najniższy bit Order (wartości 0 i 1) wskazuje, czy dodatek VSTO jest obecnie zwolniony, czy załadowany. Inne bity wskazują, kiedy aplikacja próbuje załadować dodatek narzędzi VSTO.

 Zazwyczaj wpis **LoadBehavior** ma być ustawiony na wartość 0, 3 lub 16 (w postaci dziesiętnej), gdy dodatek VSTO zostanie zainstalowany na komputerach użytkowników końcowych. Domyślnie program Visual Studio ustawia wpis **LoadBehavior** dodatku VSTO na 3 podczas kompilacji lub publikacji.

 W poniższej tabeli wymieniono wszystkie możliwe wartości wpisu **LoadBehavior** . Niektóre opisy w tej tabeli odnoszą się do ręcznego ładowania dodatku narzędzi VSTO lub programowo. Aby ręcznie załadować dodatek Narzędzia VSTO, zaznacz pole wyboru obok dodatku VSTO w oknie dialogowym **Dodatki COM** w aplikacji. Aby programowo załadować dodatek narzędzi VSTO, należy ustawić właściwość <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> obiektu <xref:Microsoft.Office.Core.COMAddIn>, który reprezentuje dodatek VSTO do **wartości true**.

|Wartość (w formacie dziesiętnym)|Stan dodatku narzędzi VSTO|Zachowanie ładowania dodatku narzędzi VSTO|Opis|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Zwolniono|Nie Ładuj automatycznie|Aplikacja nigdy nie próbuje automatycznie załadować dodatku VSTO. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub programowo załadować dodatek narzędzi VSTO.<br /><br /> Jeśli dodatek VSTO zostanie pomyślnie załadowany, wartość **LoadBehavior** pozostaje równa 0, ale stan dodatku VSTO w oknie dialogowym **Dodatki COM** zostanie zaktualizowany, aby wskazać, że dodatek VSTO jest ładowany.|
|1|załadowano|Nie Ładuj automatycznie|Aplikacja nigdy nie próbuje automatycznie załadować dodatku VSTO. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub programowo załadować dodatek narzędzi VSTO.<br /><br /> Mimo że okno dialogowe **Dodatki COM** wskazuje, że dodatek VSTO jest ładowany po uruchomieniu aplikacji, dodatek VSTO nie zostanie załadowany, dopóki nie zostanie załadowany ręcznie lub programowo.<br /><br /> Jeśli aplikacja pomyślnie załaduje dodatek VSTO, wartość **LoadBehavior** zmieni się na 0 i pozostanie 0 po zamknięciu aplikacji.|
|2|Zwolniono|Załaduj przy uruchomieniu|Aplikacja nie próbuje automatycznie załadować dodatku VSTO. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub programowo załadować dodatek narzędzi VSTO.<br /><br /> Jeśli aplikacja pomyślnie załaduje dodatek VSTO, wartość **LoadBehavior** zmieni się na 3 i pozostanie w 3 po zamknięciu aplikacji.|
|3|załadowano|Załaduj przy uruchomieniu|Aplikacja próbuje załadować dodatek VSTO podczas uruchamiania aplikacji. Jest to wartość domyślna podczas kompilowania lub publikowania dodatku narzędzi VSTO w programie Visual Studio.<br /><br /> Jeśli aplikacja pomyślnie załaduje dodatek VSTO, wartość **LoadBehavior** będzie równa 3. Jeśli wystąpi błąd podczas ładowania dodatku VSTO, wartość **LoadBehavior** zmieni się na 2 i pozostanie w 2 po zamknięciu aplikacji.|
|8|Zwolniono|Ładuj na żądanie|Aplikacja nie próbuje automatycznie załadować dodatku VSTO. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub programowo załadować dodatek narzędzi VSTO.<br /><br /> Jeśli aplikacja pomyślnie załaduje dodatek VSTO, wartość **LoadBehavior** zmieni się na 9.|
|9|załadowano|Ładuj na żądanie|Dodatek VSTO zostanie załadowany tylko wtedy, gdy aplikacja go wymaga, na przykład wtedy, gdy użytkownik kliknie element interfejsu użytkownika, który używa funkcji w dodatku VSTO (np. przycisk niestandardowy na Wstążce).<br /><br /> Jeśli aplikacja pomyślnie załaduje dodatek VSTO, wartość **LoadBehavior** pozostaje 9, ale stan dodatku VSTO w oknie dialogowym **Dodatki COM** zostanie zaktualizowany, aby wskazać, że dodatek VSTO jest aktualnie załadowany. Jeśli wystąpi błąd podczas ładowania dodatku VSTO, wartość **LoadBehavior** zmieni się na 8.|
|16|załadowano|Ładuj pierwszy raz, a następnie Ładuj na żądanie|Ustaw tę wartość, jeśli chcesz, aby dodatek VSTO został załadowany na żądanie. Aplikacja ładuje dodatek VSTO, gdy użytkownik uruchamia aplikację po raz pierwszy. Gdy następnym razem użytkownik uruchomi aplikację, aplikacja ładuje wszystkie elementy interfejsu użytkownika, które są zdefiniowane przez dodatek VSTO, ale dodatek VSTO nie zostanie załadowany, dopóki użytkownik nie kliknie elementu interfejsu użytkownika, który jest skojarzony z dodatkiem VSTO.<br /><br /> Gdy aplikacja pomyślnie ładuje dodatek VSTO po raz pierwszy, wartość **LoadBehavior** pozostaje 16 podczas ładowania dodatku VSTO. Po zamknięciu aplikacji wartość **LoadBehavior** zmieni się na 9.|

## <a name="see-also"></a>Zobacz także
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
