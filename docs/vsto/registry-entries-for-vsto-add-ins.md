---
title: Wpisy rejestru dla dodatków VSTO
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
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416526"
---
# <a name="registry-entries-for-vsto-add-ins"></a>Wpisy rejestru dla dodatków VSTO
  Podczas wdrażania dodatków VSTO utworzonych przy użyciu programu Visual Studio należy utworzyć określony zestaw wpisów rejestru. Te wpisy rejestru zawierają informacje, które umożliwiają aplikacji pakietu Microsoft Office odnajdywanie i ładowanie dodatku VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Podczas tworzenia projektu visual studio tworzy te wpisy rejestru na komputerze deweloperskim, dzięki czemu można łatwo uruchomić i debugować dodatek VSTO. Jeśli używasz ClickOnce do wdrożenia dodatku VSTO, wpisy rejestru są tworzone automatycznie na komputerze użytkownika końcowego. Jeśli do wdrożenia dodatku VSTO jest używany Instalator Windows, należy skonfigurować projekt InstallShield Limited Edition w celu utworzenia wpisów rejestru na komputerze użytkownika końcowego.

 Aby uzyskać więcej informacji o sposobie używanego wpisów rejestru podczas procesu ładowania dodatków VSTO, zobacz [Architektura dodatków VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> W tym temacie *identyfikator dodatku* tekstowego reprezentuje unikatowy identyfikator dodatku VSTO. Domyślnie identyfikator jest nazwą zestawu dodatku VSTO.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>Zarejestruj dodatki VSTO dla bieżącego użytkownika a wszystkich użytkowników
 Po zainstalowaniu dodatku VSTO można go zarejestrować na dwa sposoby:

- Tylko dla bieżącego użytkownika (oznacza to, że jest on dostępny tylko dla użytkownika, który jest zalogowany do komputera po zainstalowaniu dodatku VSTO). W takim przypadku wpisy rejestru są tworzone w obszarze **HKEY_CURRENT_USER**.

- Dla wszystkich użytkowników (oznacza to, że każdy użytkownik loguje się do komputera można użyć dodatku VSTO). W takim przypadku wpisy rejestru są tworzone w obszarze **HKEY_LOCAL_MACHINE**.

  Wszystkie dodatki VSTO, które można utworzyć za pomocą programu Visual Studio mogą być rejestrowane dla bieżącego użytkownika. Jednak dodatki VSTO mogą być rejestrowane dla wszystkich użytkowników tylko w niektórych scenariuszach. Te scenariusze zależą od wersji pakietu Microsoft Office na komputerze i sposobu wdrażania dodatku VSTO.

### <a name="deployment-type"></a>Typ wdrożenia
 Jeśli używasz ClickOnce do wdrożenia dodatku VSTO, dodatek VSTO może być zarejestrowany tylko dla bieżącego użytkownika. Dzieje się tak, ponieważ ClickOnce obsługuje tylko tworzenie kluczy w **obszarze HKEY_CURRENT_USER**. Jeśli chcesz zarejestrować dodatek VSTO dla wszystkich użytkowników na komputerze, musisz użyć Instalatora Windows, aby wdrożyć dodatek VSTO. Aby uzyskać więcej informacji na temat tych typów wdrażania, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu funkcji ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md) i [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="registry-entries"></a>Wpisy rejestru
 Wymagane wpisy rejestru dodatków VSTO znajdują się pod następującymi kluczami rejestru, gdzie *root* jest **HKEY_CURRENT_USER** lub **HKEY_LOCAL_MACHINE** w zależności od tego, czy instalacja jest dla bieżącego użytkownika lub wszystkich użytkowników.

|Aplikacja pakietu Office|Ścieżka konfiguracji|
|------------------|------------------|
|Visio|*Główny*\Software\Microsoft\\*Visio*\\\Addins*add in add-in ID*|
|Wszystkie inne|*Główny*\\\Software\Microsoft\Office Office Nazwa\\*dodatku*\Addins Identyfikator*dodatku*|

> [!NOTE]
> Jeśli instalator jest skierowany do wszystkich użytkowników 64-bitowego systemu Windows, zaleca się, aby zawiera dwa wpisy rejestru, jeden w obszarze\\HKEY_LOCAL_MACHINE\Software\Microsoft i jeden w obszarze HKEY_LOCAL_MACHINE\Software**WOW6432Node**\Microsoft hive. Jest to spowodowane tym, że użytkownicy mogą korzystać z 32-bitowych lub 64-bitowych wersji pakietu Office na komputerze.
>
>Jeśli Instalator jest skierowany do bieżącego użytkownika, nie musi instalować w WOW6432Node, ponieważ ścieżka HKEY_CURRENT_USER\Oprogramowanie jest współużytkowana.
>
>Aby uzyskać więcej informacji, zobacz [32-bitowe i 64-bitowe dane aplikacji w rejestrze](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry)

 W poniższej tabeli wymieniono wpisy pod tym kluczem rejestru.

|Wpis|Typ|Wartość|
|-----------|----------|-----------|
|**Opis**|REG_SZ|Wymagany. Krótki opis dodatku VSTO.<br /><br /> Ten opis jest wyświetlany, gdy użytkownik wybierze dodatek VSTO w okienku **Dodatków** okna dialogowego **Opcje** w aplikacji pakietu Microsoft Office.|
|**FriendlyName**|REG_SZ|Wymagany. Opisowa nazwa dodatku VSTO wyświetlana w oknie dialogowym **Dodatki COM w** aplikacji pakietu Microsoft Office. Wartością domyślną jest identyfikator dodatku VSTO.|
|**Loadbehavior**|REG_DWORD|Wymagany. Wartość, która określa, kiedy aplikacja próbuje załadować dodatek VSTO i bieżący stan dodatku VSTO (załadowany lub zwolniony).<br /><br /> Domyślnie ten wpis jest ustawiony na 3, który określa, że dodatek VSTO jest ładowany podczas uruchamiania. Aby uzyskać więcej informacji, zobacz [LoadBehavior values](#LoadBehavior). **Uwaga:**  Jeśli użytkownik wyłączy dodatek VSTO, ta akcja modyfikuje wartość **LoadBehavior** w gałęzi rejestru **HKEY_CURRENT_USER.** Dla każdego użytkownika wartość **LoadBehavior** wartość w gałęzi HKEY_CURRENT_USER zastępuje domyślne **LoadBehavior** zdefiniowane w **gałęzi HKEY_LOCAL_MACHINE.**|
|**Manifest**|REG_SZ|Wymagany. Pełna ścieżka manifestu wdrażania dla dodatku VSTO. Ścieżka może być lokalizacją na komputerze lokalnym, udziałem sieciowym (UNC) lub serwerem sieci Web (HTTP).<br /><br /> Jeśli używasz Instalatora Windows do wdrożenia rozwiązania, należy dodać prefiks **file:///** do ścieżki **manifestu.** Należy również dołączyć ciąg **&#124;vstolocal** (czyli znak potoku **&#124;** następuje **vstolocal**) na końcu tej ścieżki. Gwarantuje to, że rozwiązanie jest ładowane z folderu instalacyjnego, a nie z pamięci podręcznej ClickOnce. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md). **Uwaga:**  Podczas tworzenia dodatku VSTO na komputerze deweloperskim program Visual Studio automatycznie dołącza **ciąg vstolocal&#124;** do tego wpisu rejestru.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a>Wpisy rejestru dla regionów formularzy programu Outlook
 Jeśli utworzysz niestandardowy region formularza w dodatku VSTO dla programu Outlook, dodatkowe wpisy rejestru są używane do rejestrowania regionu formularza w programie Outlook. Te wpisy są tworzone przy innym kluczu rejestru dla każdej klasy wiadomości, która obsługuje region formularza. Te klucze rejestru znajdują się w następującej lokalizacji, gdzie *root* jest **HKEY_CURRENT_USER** lub **HKEY_LOCAL_MACHINE**.

 *Główna*\\*klasa wiadomości* \Software\Microsoft\Office\Outlook\FormRegions

 Podobnie jak inne wpisy rejestru udostępnione przez wszystkie dodatki VSTO, program Visual Studio tworzy wpisy rejestru regionu formularza na komputerze deweloperskim podczas tworzenia projektu. Jeśli używasz ClickOnce do wdrożenia dodatku VSTO, wpisy rejestru są tworzone automatycznie na komputerze użytkownika końcowego. Jeśli do wdrożenia dodatku VSTO jest używany Instalator Windows, należy skonfigurować projekt InstallShield Limited Edition w celu utworzenia wpisów rejestru na komputerze użytkownika końcowego.

 Aby uzyskać więcej informacji o wpisach rejestru regionu formularza, zobacz [Określanie lokalizacji regionu formularza w formularzu niestandardowym](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Aby uzyskać więcej informacji o regionach formularzy programu Outlook, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a>Wartości LoadBehavior
 Wpis **LoadBehavior** w *katalogu głównym*\Software\Microsoft\Office\\nazwa*aplikacji*\Addins\\*addins add-in name id* zawiera bitową kombinację wartości, które określają zachowanie czasu wykonywania dodatku VSTO. Najniższy bit zamówienia (wartości 0 i 1) wskazuje, czy dodatek VSTO jest obecnie zwalniany lub ładowany. Inne bity wskazują, kiedy aplikacja próbuje załadować dodatek VSTO.

 Zazwyczaj wpis **LoadBehavior** jest przeznaczony do ustawienia 0, 3 lub 16 (w przecinku), gdy dodatek VSTO jest zainstalowany na komputerach użytkowników końcowych. Domyślnie Visual Studio ustawia **loadBehavior** wpis dodatku VSTO do 3 podczas tworzenia lub publikowania go.

 W poniższej tabeli wymieniono wszystkie możliwe wartości wpisu **LoadBehavior.** Niektóre opisy w tej tabeli odnoszą się do ładowania dodatku VSTO ręcznie lub programowo. Aby ręcznie załadować dodatek VSTO, zaznacz pole wyboru obok dodatku VSTO w oknie dialogowym **Dodatki COM w** aplikacji. Aby programowo załadować dodatek VSTO, <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> ustaw właściwość <xref:Microsoft.Office.Core.COMAddIn> obiektu reprezentującego dodatek VSTO na **wartość true**.

|Wartość (dziesiętna)|Stan dodatku VSTO|Zachowanie ładowania dodatku VSTO|Opis|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|Zwolniono|Nie ładuj się automatycznie|Aplikacja nigdy nie próbuje załadować dodatek VSTO automatycznie. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub dodatek VSTO można załadować programowo.<br /><br /> Jeśli dodatek VSTO został pomyślnie załadowany, wartość **LoadBehavior** pozostaje 0, ale stan dodatku VSTO w oknie dialogowym Dodatki COM jest **aktualizowany,** aby wskazać, że dodatek VSTO jest ładowany.|
|1|załadowano|Nie ładuj się automatycznie|Aplikacja nigdy nie próbuje załadować dodatek VSTO automatycznie. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub dodatek VSTO można załadować programowo.<br /><br /> Chociaż okno dialogowe **Dodatki COM** wskazuje, że dodatek VSTO jest ładowany po uruchomieniu aplikacji, dodatek VSTO nie jest ładowany, dopóki nie zostanie załadowany ręcznie lub programowo.<br /><br /> Jeśli aplikacja pomyślnie ładuje dodatek VSTO, **Wartość LoadBehavior** zmienia się na 0 i pozostaje na 0 po zamknięciu aplikacji.|
|2|Zwolniono|Ładowanie przy starcie|Aplikacja nie próbuje automatycznie załadować dodatku VSTO. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub dodatek VSTO można załadować programowo.<br /><br /> Jeśli aplikacja pomyślnie ładuje dodatek VSTO, **Wartość LoadBehavior** zmienia się na 3 i pozostaje na 3 po zamknięciu aplikacji.|
|3|załadowano|Ładowanie przy starcie|Aplikacja próbuje załadować dodatek VSTO po uruchomieniu aplikacji. Jest to wartość domyślna podczas tworzenia lub publikowania dodatku VSTO w programie Visual Studio.<br /><br /> Jeśli aplikacja pomyślnie ładuje dodatek VSTO, **LoadBehavior** wartość pozostaje 3. Jeśli wystąpi błąd podczas ładowania dodatku VSTO, **LoadBehavior** wartość zmienia się na 2 i pozostaje na 2 po zamknięciu aplikacji.|
|8|Zwolniono|Obciążenie na żądanie|Aplikacja nie próbuje automatycznie załadować dodatku VSTO. Użytkownik może spróbować ręcznie załadować dodatek VSTO lub dodatek VSTO można załadować programowo.<br /><br /> Jeśli aplikacja pomyślnie ładuje dodatek VSTO, **wartość LoadBehavior** zmienia się na 9.|
|9|załadowano|Obciążenie na żądanie|Dodatek VSTO zostanie załadowany tylko wtedy, gdy aplikacja tego wymaga, na przykład gdy użytkownik kliknie element interfejsu użytkownika, który używa funkcji w dodatku VSTO (na przykład przycisk niestandardowy na Wstążce).<br /><br /> Jeśli aplikacja pomyślnie ładuje dodatek VSTO, wartość **LoadBehavior** pozostaje 9, ale stan dodatku VSTO w oknie dialogowym dodatki COM jest **aktualizowany,** aby wskazać, że dodatek VSTO jest aktualnie załadowany. Jeśli wystąpi błąd podczas ładowania dodatku VSTO, **Wartość LoadBehavior** zmienia się na 8.|
|16|załadowano|Załaduj najpierw, a następnie załaduj na żądanie|Ustaw tę wartość, jeśli chcesz, aby dodatek VSTO był ładowany na żądanie. Aplikacja ładuje dodatek VSTO, gdy użytkownik uruchamia aplikację po raz pierwszy. Następnym razem, gdy użytkownik uruchamia aplikację, aplikacja ładuje wszystkie elementy interfejsu użytkownika, które są zdefiniowane przez dodatek VSTO, ale dodatek VSTO nie jest ładowany, dopóki użytkownik nie kliknie elementu interfejsu użytkownika skojarzonego z dodatkiem VSTO.<br /><br /> Gdy aplikacja pomyślnie ładuje dodatek VSTO po raz pierwszy, **LoadBehavior** wartość pozostaje 16 podczas ładowania dodatku VSTO. Po zamknięciu aplikacji **LoadBehavior** wartość zmienia się na 9.|

## <a name="see-also"></a>Zobacz też
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
 