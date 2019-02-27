---
title: Podręcznik administratora programu Podgląd pomocy
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21497404d6cdad3f55bffd97fd0329d76418b313
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841579"
---
# <a name="help-viewer-administrator-guide"></a>Podręcznik administratora programu Podgląd pomocy

Podgląd Pomocy umożliwia zarządzanie lokalnymi instalacjami pomocy dla środowisk sieciowych, z lub bez dostępu do Internetu. Zawartość pomocy lokalnej jest skonfigurowana na kompurtera. Domyślnie użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować ich lokalną instalację pomocy.

Jeśli środowisko sieciowe pozwala klientom na dostęp do Internetu, można użyć **menedżera zawartości Pomocy** pliku wykonywalnego do wdrażania lokalnie zawartości pomocy z Internetu. Aby uzyskać więcej informacji na temat *HlpCtntMgr.exe* składnia wiersza polecenia, zobacz [argumenty wiersza polecenia dla menedżera zawartości Pomocy](../help-viewer/command-line-arguments.md).

Aby uzyskać informacje dotyczące tworzenia zawartości, tworzenia punktu końcowego usługi sieci intranet i podobnych rodzajów działań, zobacz [zestaw SDK podglądu pomocy](../extensibility/internals/microsoft-help-viewer-sdk.md).

Jeśli nie masz dostępu do Internetu w danym środowisku sieciowym, w Podglądzie pomocy można wdrażać lokalnie zawartości pomocy z intranetu lub udziału sieciowego. Można także wyłączyć opcje pomocy programu Visual Studio IDE, za pomocą [przesłania klucza rejestru](../help-viewer/behavior-overrides.md) dla funkcji, takich jak:

- online i pomoc w trybie offline

- instalację zawartości podczas pierwszego uruchomienia środowiska IDE

- Określanie usługi zawartości intranetu

- Zarządzanie zawartością

## <a name="deploy-local-help-content-from-the-internet"></a>Wdrażanie lokalnej zawartości pomocy z Internetu

Możesz użyć **menedżera zawartości Pomocy** (*HlpCtntMgr.exe*) do wdrożenia lokalnej zawartości pomocy z Internetu do komputerów klienckich. Należy użyć następującej składni:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Aby uzyskać więcej informacji na temat *HlpCtntMgr.exe* składnia wiersza polecenia, zobacz [argumenty wiersza polecenia dla menedżera zawartości Pomocy](../help-viewer/command-line-arguments.md).

Wymagania:

-   Komputery klienckie muszą mieć dostęp do Internetu.

-   Użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować, Dodaj lub usuń lokalną zawartość pomocy po zakończeniu instalacji.

Ostrzeżenia:

-   Domyślnym źródłem pomocy będzie nadal online.

### <a name="example"></a>Przykład

Poniższy przykład instaluje zawartość w języku angielskim dla programu Visual Studio na komputerze klienckim.

#### <a name="to-install-english-content-from-the-internet"></a>Aby zainstalować zawartość w języku angielskim z Internetu

1.  Wybierz **Start** , a następnie wybierz **Uruchom**.

2.  Wpisz następujące polecenie:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Naciśnij klawisz **wprowadź**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Wdrażanie wstępnie zainstalowanych lokalnie zawartości pomocy, na komputerach klienckich

Można zainstalować zestaw treści z online do jednego komputera, a następnie skopiować ten zainstalowany zestaw treści na inne komputery.

Wymagania:

-   Komputer, na którym jest instalowany zestaw zawartości musi mieć dostęp do Internetu.

-   Użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować, Dodaj lub usuń lokalną zawartość pomocy po zakończeniu instalacji.

    > [!TIP]
    > Jeśli użytkownicy nie mają praw administratora, zalecane jest wyłączenie **zarządzanie zawartością** karty w Podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [przesłonięcia menedżera zawartości Pomocy](../help-viewer/behavior-overrides.md).

Ostrzeżenia:

-   Domyślnym źródłem pomocy będzie nadal online.

### <a name="create-the-content-set"></a>Utwórz zestaw zawartości

Przed utworzeniem zestawu podstawowego zawartości, należy najpierw odinstalować wszystkie lokalne zawartości programu Visual Studio na komputerze docelowym.

#### <a name="to-uninstall-local-help"></a>Aby odinstalować Pomoc lokalną

1. W Podglądzie pomocy wybierz **zarządzanie zawartością** kartę.

2. Przejdź do zestawu dokumentów programu Visual Studio.

3. Wybierz **Usuń** obok każdej podpozycji.

4. Wybierz **aktualizacji** do odinstalowania.

5. Przejdź do *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* i sprawdź, czy folder zawiera tylko plik *catalogType.xml*.

   Po usunięciu wszystkich uprzednio zainstalowanych pomocy programu Visual Studio zawartości lokalnej, jesteś gotowy do pobrania podstawowego zestawu zawartości.

#### <a name="to-download-the-content"></a>Aby pobrać zawartość

1.  W Podglądzie pomocy wybierz **zarządzanie zawartością** kartę.

2.  W obszarze **zalecana dokumentacja** lub **dostępnej dokumentacji**, przejdź do zestawów dokumentacji, aby pobrać, a następnie wybierz **Dodaj**.

3.  Wybierz **aktualizacji**.

Następnie należy spakować zawartości, aby można było wdrożyć na komputerach klienckich.

#### <a name="to-package-the-content"></a>Aby spakować zawartość

1.  Utwórz folder do skopiowania do niego zawartość na potrzeby późniejszego wdrożenia. Na przykład: *C:\VSHelp*.

2.  Otwórz *cmd.exe* z uprawnieniami administratora.

3.  Przejdź do folderu, który został utworzony w kroku 1.

4.  Wpisz następujące polecenie:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Na przykład: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Wdrażanie zawartości

1.  Utwórz udział sieciowy i skopiuj zawartość pomocy do tej lokalizacji.

     Na przykład skopiuj zawartość *C:\VSHelp* do  *\\\myserver\VSHelp*.

2.  Tworzenie *.bat* plik będzie zawierał skrypt wdrażania dla zawartości pomocy. Ponieważ klient prawdopodobnie nałożył blokadę odczytu na dowolnym pliki usuwane w ramach wypychania, należy zamknąć klienta przed wypchnięciem aktualizacji. Na przykład:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3.  Uruchom *.bat* plików na komputerach lokalnych, które chcesz zainstalować zawartości pomocy na.

## <a name="see-also"></a>Zobacz także

- [Argumenty wiersza polecenia dla menedżera zawartości pomocy](../help-viewer/command-line-arguments.md)
- [Przesłonięcia menedżera zawartości pomocy](../help-viewer/behavior-overrides.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)
- [Zestaw SDK podglądu pomocy](../extensibility/internals/microsoft-help-viewer-sdk.md)