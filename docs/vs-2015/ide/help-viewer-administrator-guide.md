---
title: Podręcznik administratora programu Podgląd pomocy | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e0f63555cbda069c3db0a3a1d5819292fc3cda14
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799708"
---
# <a name="help-viewer-administrator-guide"></a>Podręcznik administratora programu Podgląd Pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podgląd Pomocy umożliwia zarządzanie lokalnymi instalacjami pomocy dla środowisk sieciowych, z lub bez dostępu do Internetu. Zawartość pomocy lokalnej jest skonfigurowana na kompurtera. Domyślnie użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować ich lokalną instalację pomocy.  
  
 Jeśli środowisko sieciowe pozwala klientom na dostęp do Internetu, w Podglądzie pomocy pozwala wdrażać lokalnie zawartości pomocy z Internetu za pomocą skryptów wiersza polecenia.  
  
 Jeśli środowisko sieciowe nie zezwala klientom na dostęp do Internetu, w Podglądzie pomocy można wdrożyć lokalnie zawartości pomocy z intranetu lub udziału sieciowego. Można także wyłączyć opcje pomocy programu Visual Studio IDE, takich jak Pomoc online/offline, instalację zawartości podczas pierwszego uruchomienia środowiska IDE, określanie usługi zawartości intranetu i zarządzania zawartością, zastępowanie klucza rejestru.  
  
 Podstawowa składnia jest następująca:  
  
 \<*Ścieżka do*> \HlpCtntmgr.exe /operation \< *argument*>/catalogname \< *nazwa*>/Locale \< *ustawieńregionalnych*>/sourceuri \< *ścieżka .msha lub adres URL*>  
  
 Aby uzyskać więcej informacji na temat składni wiersza polecenia HlpCtntMgr.exe, zobacz [argumenty wiersza polecenia dla menedżera zawartości Pomocy](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Aby uzyskać więcej informacji na temat tworzenia zawartości, tworzenia punktu końcowego usługi sieci intranet i podobnych rodzajów działań zobacz zestaw SDK podglądu pomocy.  
  
## <a name="deploying-local-help-content-from-the-internet"></a>Wdrażanie lokalnej zawartości pomocy z Internetu  
 Usługi pakiet zawartości MSDN można użyć do wdrożenia lokalnej zawartości pomocy z Internetu do komputerów klienckich. Należy użyć następującej składni:  
  
 \\<*Ścieżka do*> \v2.2\HlpCtntmgr.exe /operation \< *nazwa*>/catalogname \< *Nazwa wykazu*>/Locale \<  *Ustawienia regionalne*>  
  
 Aby uzyskać więcej informacji na temat składni wiersza polecenia HlpCtntMgr.exe, zobacz [argumenty wiersza polecenia dla menedżera zawartości Pomocy](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Wymagania:  
  
- Komputery klienckie muszą mieć dostęp do Internetu.  
  
- Użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować, Dodaj lub usuń lokalną zawartość pomocy po zakończeniu instalacji.  
  
  Ostrzeżenia:  
  
- Domyślnym źródłem pomocy będzie nadal Online.  
  
  > [!TIP]
  >  Domyślne źródło pomocy można zmienić, modyfikując klucz rejestru HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Aby uzyskać więcej informacji, zobacz [przesłonięcia menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md).  
  
- Klienci będą nadal się monit o zainstalowanie podstawowa zawartość pomocy przy pierwszym uruchomieniu programu Visual Studio. Możesz wyłączyć ten monit, modyfikując klucz rejestru HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład instaluje zawartość w języku angielskim dla programu Visual Studio na komputerze klienckim.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Aby zainstalować zawartość w języku angielskim z Internetu  
  
1.  Wybierz **Start** , a następnie wybierz **Uruchom**.  
  
2.  Wpisz następujące polecenie:  
  
     C:\Program pliki (x86) \Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation instalacji/catalogname VisualStudio14/Locale en-us  
  
3.  Naciśnij klawisz ENTER.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Wdrażanie wstępnie zainstalowanych lokalnej zawartości pomocy na komputerach klienckich  
 Można zainstalować zestaw treści z online do jednego komputera, a następnie skopiować ten zainstalowany zestaw treści na inne komputery.  
  
 Wymagania:  
  
- Komputer, na którym jest instalowany zestaw zawartości musi mieć dostęp do Internetu.  
  
- Użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować, Dodaj lub usuń lokalną zawartość pomocy po zakończeniu instalacji.  
  
  > [!TIP]
  >  Jeśli użytkownicy nie mają praw administratora, zalecane jest, aby wyłączyć kartę Zarządzaj zawartością w Podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [przesłonięcia menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md).  
  
  Ostrzeżenia:  
  
- Jeśli użytkownicy nie mają praw administratora, zalecane jest, aby wyłączyć kartę Zarządzaj zawartością w Podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [przesłonięcia menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md).  
  
- Domyślnym źródłem pomocy będzie nadal Online.  
  
- Klienci będą nadal się monit o zainstalowanie podstawowa zawartość pomocy przy pierwszym uruchomieniu programu Visual Studio. Aby uzyskać więcej informacji, zobacz [przesłonięcia menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md).  
  
### <a name="create-the-content-set"></a>Utwórz zestaw zawartości  
 Przed utworzeniem zestawu podstawowego zawartości, należy najpierw odinstalować wszystkie lokalne zawartości programu Visual Studio na komputerze docelowym.  
  
##### <a name="to-uninstall-local-help"></a>Aby odinstalować Pomoc lokalną  
  
1. W Podglądzie pomocy wybierz **zarządzanie zawartością** kartę.  
  
2. W obszarze **dostępnej dokumentacji**, przejdź do zestawu dokumentów programu Visual Studio.  
  
3. Wybierz **Usuń** obok każdej podpozycji.  
  
4. Wybierz **Start** do odinstalowania  
  
5. Przejdź do *n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 i sprawdź, czy folder zawiera tylko plik catalogType.xml.  
  
   Po usunięciu wszystkich uprzednio zainstalowanych pomocy programu Visual Studio zawartości lokalnej, jesteś gotowy do pobrania podstawowego zestawu zawartości.  
  
##### <a name="to-download-the-content"></a>Aby pobrać zawartość  
  
1. W Podglądzie pomocy wybierz **zarządzanie zawartością** kartę.  
  
2. W obszarze **dostępnej dokumentacji**, przejdź do zestawów dokumentacji, aby pobrać, a następnie wybierz **Dodaj**.  
  
3. Wybierz **Start**.  
  
   Następnie należy spakować zawartości, aby można było wdrożyć na komputerach klienckich.  
  
##### <a name="to-package-the-content"></a>Aby spakować zawartość  
  
1.  Utwórz folder do skopiowania do niego zawartość na potrzeby późniejszego wdrożenia.  
  
     Na przykład: c:\VS12Help.  
  
2.  Otwórz cmd.exe z uprawnieniami administratora.  
  
3.  Przejdź do folderu, który został utworzony w kroku 1.  
  
4.  Wpisz następujące polecenie:  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \< *nazwa_folderu*> \ /y /e /k /o  
  
     Na przykład: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>Wdrażanie zawartości  
  
##### <a name="to-deploy-the-content"></a>Aby wdrożyć zawartość  
  
1.  Utwórz udział sieciowy i skopiuj zawartość pomocy theee do tej lokalizacji.  
  
     Na przykład skopiuj zawartość c:\VS12Help do \\\myserver\VS12Help.  
  
2.  Utwórz plik .bat, aby zawierał skrypt wdrażania dla zawartości pomocy. Ponieważ klient prawdopodobnie nałożył blokadę odczytu na dowolnym pliki usuwane w ramach wypychania, należy zamknąć klienta przed wypchnięciem aktualizacji.  
  
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
  
3.  Uruchom plik bat na komputerach lokalnych, które zawartości pomocy jest zainstalowane na urządzeniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Argumenty wiersza polecenia Menedżera zawartości pomocy](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Przesłonięcia Menedżera zawartości Pomocy](../ide/help-content-manager-overrides.md)
