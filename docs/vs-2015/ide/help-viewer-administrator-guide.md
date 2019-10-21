---
title: Przewodnik administratora podglądu pomocy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03cacd8de574de92002b44b237cd84c22e761eaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645574"
---
# <a name="help-viewer-administrator-guide"></a>Podręcznik administratora programu Podgląd Pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podgląd pomocy umożliwia zarządzanie lokalnymi instalacjami pomocy dla środowisk sieciowych z dostępem do Internetu lub bez niego. Lokalna zawartość pomocy jest konfigurowana na poszczególnych komputerach. Domyślnie użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować lokalną instalację pomocy.

 Jeśli środowisko sieciowe pozwala klientom na dostęp do Internetu, podgląd pomocy programu umożliwia użycie skryptów wiersza polecenia do wdrożenia lokalnej zawartości pomocy z Internetu.

 Jeśli środowisko sieciowe nie zezwala klientom na dostęp do Internetu, podgląd pomocy może wdrożyć lokalną zawartość pomocy z intranetu lub udziału sieciowego. Możesz również wyłączyć opcje pomocy środowiska IDE programu Visual Studio, takie jak pomoc online/offline, Instalowanie zawartości podczas pierwszego uruchomienia środowiska IDE, określanie intranetowej usługi zawartości i zarządzanie zawartością przy użyciu przesłonięć kluczy rejestru.

 Podstawowa składnia jest następująca:

 \<*ścieżkę do*> \HlpCtntmgr.exe/operation \<*argument*>/CatalogName \<*name*> wymaganego/locale. \<*locale*>/SourceUri \< *. msha Path lub URL* 0

 Aby uzyskać więcej informacji na temat składni wiersza polecenia HlpCtntMgr. exe, zobacz [argumenty wiersza polecenia dla Menedżera zawartości pomocy](../ide/command-line-arguments-for-the-help-content-manager.md).

 Aby uzyskać więcej informacji na temat tworzenia zawartości, tworzenia punktu końcowego usługi sieci intranet i podobnych rodzajów działań, zobacz zestaw SDK podglądu pomocy.

## <a name="deploying-local-help-content-from-the-internet"></a>Wdrażanie lokalnej zawartości pomocy z Internetu
 Za pomocą usługi pakietu zawartości MSDN można wdrożyć lokalną zawartość pomocy z Internetu na komputerach klienckich. Użyj następującej składni:

 \\ <*ścieżkę do*> \v2.2\HlpCtntmgr.exe/operation \<*name*>/catalogname \<*Catalog Name*> wymaganego/locale. \<*locale* >

 Aby uzyskać więcej informacji na temat składni wiersza polecenia HlpCtntMgr. exe, zobacz [argumenty wiersza polecenia dla Menedżera zawartości pomocy](../ide/command-line-arguments-for-the-help-content-manager.md).

 Wymagania

- Komputery klienckie muszą mieć dostęp do Internetu.

- Użytkownicy muszą mieć uprawnienia administratora, aby aktualizować, dodawać lub usuwać lokalną zawartość pomocy po jej zainstalowaniu.

  Zastrzeżenia

- Domyślne źródło pomocy nadal będzie w trybie online.

  > [!TIP]
  > Można zmienić domyślne źródło pomocy, modyfikując klucz rejestru HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Aby uzyskać więcej informacji, zobacz [przesłonięcia Menedżera zawartości pomocy](../ide/help-content-manager-overrides.md).

- Klienci będą nadal monitowani o zainstalowanie podstawowej zawartości pomocy przy pierwszym uruchomieniu programu Visual Studio. Możesz wyłączyć ten monit, modyfikując klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.

### <a name="example"></a>Przykład
 Poniższy przykład instaluje zawartość w języku angielskim dla programu Visual Studio na komputerze klienckim.

##### <a name="to-install-english-content-from-the-internet"></a>Aby zainstalować zawartość w języku angielskim z Internetu

1. Wybierz przycisk **Start** , a następnie wybierz polecenie **Uruchom**.

2. Wpisz następujące polecenie:

     C:\Program Files (x86) \Microsoft help Viewer\v2.2\HlpCtntmgr.exe/operation Install/CatalogName VisualStudio14 wymaganego/locale. en-us

3. Naciśnij klawisz ENTER.

## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Wdrażanie wstępnie zainstalowanej lokalnej zawartości pomocy na komputerach klienckich
 Możesz zainstalować zestaw zawartości z trybu online na jednym komputerze, a następnie skopiować ten zainstalowany zestaw zawartości na inne komputery.

 Wymagania

- Komputer, na którym jest instalowany zestaw zawartości, musi mieć dostęp do Internetu.

- Użytkownicy muszą mieć uprawnienia administratora, aby aktualizować, dodawać lub usuwać lokalną zawartość pomocy po jej zainstalowaniu.

  > [!TIP]
  > Jeśli użytkownicy nie mają uprawnień administratora, zaleca się wyłączenie karty Zarządzanie zawartością w podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [przesłonięcia Menedżera zawartości pomocy](../ide/help-content-manager-overrides.md).

  Zastrzeżenia

- Jeśli użytkownicy nie mają uprawnień administratora, zaleca się wyłączenie karty Zarządzanie zawartością w podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [przesłonięcia Menedżera zawartości pomocy](../ide/help-content-manager-overrides.md).

- Domyślne źródło pomocy nadal będzie w trybie online.

- Klienci będą nadal monitowani o zainstalowanie podstawowej zawartości pomocy przy pierwszym uruchomieniu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przesłonięcia Menedżera zawartości pomocy](../ide/help-content-manager-overrides.md).

### <a name="create-the-content-set"></a>Tworzenie zestawu zawartości
 Aby można było utworzyć podstawowy zestaw zawartości, należy najpierw odinstalować całą lokalną zawartość programu Visual Studio na komputerze docelowym.

##### <a name="to-uninstall-local-help"></a>Aby odinstalować pomoc lokalną

1. W podglądzie pomocy wybierz kartę **Zarządzanie zawartością** .

2. W obszarze **dostępna dokumentacja**przejdź do zestawu dokumentów programu Visual Studio.

3. Wybierz pozycję **Usuń** obok każdego elementu podrzędnego.

4. Wybierz pozycję **Rozpocznij** , aby odinstalować

5. Przejdź do *n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 i sprawdź, czy folder zawiera tylko plik catalogType. XML.

   Po usunięciu wszystkich wcześniej zainstalowanych lokalnych zawartości pomocy programu Visual Studio możesz pobrać podstawowy zestaw zawartości.

##### <a name="to-download-the-content"></a>Aby pobrać zawartość

1. W podglądzie pomocy wybierz kartę **Zarządzanie zawartością** .

2. W obszarze **dostępna dokumentacja**przejdź do zestawów dokumentacji, które chcesz pobrać, a następnie wybierz pozycję **Dodaj**.

3. Wybierz pozycję **Rozpocznij**.

   Następnie należy spakować zawartość, aby można ją było wdrożyć na komputerach klienckich.

##### <a name="to-package-the-content"></a>Aby spakować zawartość

1. Utwórz folder, do którego chcesz skopiować zawartość do późniejszego wdrożenia.

     Na przykład: c:\VS12Help.

2. Otwórz cmd. exe z uprawnieniami administratora.

3. Przejdź do folderu utworzonego w kroku 1.

4. Wpisz następujące polecenie:

     XCOPY%SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \<*nazwafolderu*> \/y/e/k/o

     Na przykład: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`

### <a name="deploying-the-content"></a>Wdrażanie zawartości

##### <a name="to-deploy-the-content"></a>Aby wdrożyć zawartość

1. Utwórz udział sieciowy i skopiuj zawartość pomocy rozszerzeniem do tej lokalizacji.

     Na przykład skopiuj zawartość z c:\VS12Help do \\ \myserver\VS12Help.

2. Utwórz plik. bat, aby zawierał skrypt wdrażania dla zawartości pomocy. Ponieważ klient może mieć blokadę odczytu na dowolnym z plików, które są usuwane w ramach wypychania, należy zamknąć klienta przed wypchnięciem aktualizacji.

     Na przykład:

    ```
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)

    REM - get processor type and create/run registry update file
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64

    @echo Architecture type is x86

    ECHO Windows Registry Editor Version 5.00 > x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg
    ECHO "FirstTimeRun"="False"  >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg

    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg

    regedit.exe /s x86.reg
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)

    GOTO CONTINUE

    :AMD64
    @echo Architecture type is AMD64

    ECHO Windows Registry Editor Version 5.00 > x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg
    ECHO "FirstTimeRun"="False"  >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg

    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg

    regedit.exe /s x64.reg
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)

    :CONTINUE
    ```

3. Uruchom plik bat na maszynach lokalnych, na których ma zostać zainstalowana zawartość pomocy.

## <a name="see-also"></a>Zobacz też
 [Argumenty wiersza polecenia dla programu Help Content Manager dla](../ide/command-line-arguments-for-the-help-content-manager.md) Menedżera [zawartości pomocy](../ide/help-content-manager-overrides.md)
