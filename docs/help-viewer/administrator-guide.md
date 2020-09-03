---
title: Podręcznik administratora podglądu pomocy
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 037ee411c156d21145160dc95b40078fd841493c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825125"
---
# <a name="help-viewer-administrator-guide"></a>Podręcznik administratora podglądu pomocy

Podgląd pomocy umożliwia zarządzanie lokalnymi instalacjami pomocy dla środowisk sieciowych z dostępem do Internetu lub bez niego. Lokalna zawartość pomocy jest konfigurowana na poszczególnych komputerach. Domyślnie użytkownicy muszą mieć uprawnienia administratora, aby zaktualizować lokalną instalację pomocy.

Jeśli środowisko sieciowe pozwala klientom na dostęp do Internetu, można użyć pliku wykonywalnego **Menedżera zawartości pomocy** do wdrożenia lokalnej zawartości pomocy z Internetu. Aby uzyskać więcej informacji na temat składni wiersza polecenia *HlpCtntMgr.exe* , zobacz [argumenty wiersza polecenia dla Menedżera zawartości pomocy](../help-viewer/command-line-arguments.md).

Aby uzyskać informacje na temat tworzenia zawartości, tworzenia punktu końcowego usługi sieci intranet i podobnych rodzajów działań, zobacz [zestaw SDK podglądu pomocy](../extensibility/internals/microsoft-help-viewer-sdk.md).

Jeśli nie masz dostępu do Internetu w środowisku sieciowym, podgląd pomocy programu może wdrożyć lokalną zawartość pomocy z intranetu lub udziału sieciowego. Opcje pomocy środowiska IDE programu Visual Studio można także wyłączyć, używając [zastąpień klucza rejestru](../help-viewer/behavior-overrides.md) do obsługi takich funkcji, jak:

- Pomoc online i offline

- Instalowanie zawartości podczas pierwszego uruchomienia środowiska IDE

- Określanie usługi zawartości intranetowej

- Zarządzanie zawartością

## <a name="deploy-local-help-content-from-the-internet"></a>Wdrażanie lokalnej zawartości pomocy z Internetu

Za pomocą **Menedżera zawartości pomocy** (*HlpCtntMgr.exe*) można wdrożyć lokalną zawartość pomocy z Internetu na komputerach klienckich. Użyj następującej składni:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Aby uzyskać więcej informacji na temat składni wiersza polecenia *HlpCtntMgr.exe* , zobacz [argumenty wiersza polecenia dla Menedżera zawartości pomocy](../help-viewer/command-line-arguments.md).

Wymagania:

- Komputery klienckie muszą mieć dostęp do Internetu.

- Użytkownicy muszą mieć uprawnienia administratora, aby aktualizować, dodawać lub usuwać lokalną zawartość pomocy po jej zainstalowaniu.

Zastrzeżenia

- Domyślne źródło pomocy nadal będzie w trybie online.

### <a name="example"></a>Przykład

Poniższy przykład instaluje zawartość w języku angielskim dla programu Visual Studio na komputerze klienckim.

#### <a name="to-install-english-content-from-the-internet"></a>Aby zainstalować zawartość w języku angielskim z Internetu

1. Wybierz przycisk **Start** , a następnie wybierz polecenie **Uruchom**.

2. Wpisz następujące polecenie:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Naciśnij klawisz **Enter**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Wdróż wstępnie zainstalowaną lokalną zawartość pomocy na komputerach klienckich

Możesz zainstalować zestaw zawartości z trybu online na jednym komputerze, a następnie skopiować ten zainstalowany zestaw zawartości na inne komputery.

Wymagania:

- Komputer, na którym jest instalowany zestaw zawartości, musi mieć dostęp do Internetu.

- Użytkownicy muszą mieć uprawnienia administratora, aby aktualizować, dodawać lub usuwać lokalną zawartość pomocy po jej zainstalowaniu.

    > [!TIP]
    > Jeśli użytkownicy nie mają uprawnień administratora, zaleca się wyłączenie karty **Zarządzanie zawartością** w podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [przesłonięcia Menedżera zawartości pomocy](../help-viewer/behavior-overrides.md).

Zastrzeżenia

- Domyślne źródło pomocy nadal będzie w trybie online.

### <a name="create-the-content-set"></a>Tworzenie zestawu zawartości

Aby można było utworzyć podstawowy zestaw zawartości, należy najpierw odinstalować całą lokalną zawartość programu Visual Studio na komputerze docelowym.

#### <a name="to-uninstall-local-help"></a>Aby odinstalować pomoc lokalną

1. W podglądzie pomocy wybierz kartę **Zarządzanie zawartością** .

2. Przejdź do zestawu dokumentów programu Visual Studio.

3. Wybierz pozycję **Usuń** obok każdego elementu podrzędnego.

4. Wybierz **aktualizację** do odinstalowania.

5. Przejdź do *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* i sprawdź, czy folder zawiera tylko plik *catalogType.xml*.

   Po usunięciu wszystkich wcześniej zainstalowanych lokalnych zawartości pomocy programu Visual Studio możesz pobrać podstawowy zestaw zawartości.

#### <a name="to-download-the-content"></a>Aby pobrać zawartość

1. W podglądzie pomocy wybierz kartę **Zarządzanie zawartością** .

2. W obszarze **zalecana dokumentacja** lub **dostępna dokumentacja**przejdź do zestawów dokumentacji, które chcesz pobrać, a następnie wybierz pozycję **Dodaj**.

3. Wybierz pozycję **Aktualizuj**.

Następnie należy spakować zawartość, aby można ją było wdrożyć na komputerach klienckich.

#### <a name="to-package-the-content"></a>Aby spakować zawartość

1. Utwórz folder, do którego chcesz skopiować zawartość do późniejszego wdrożenia. Na przykład: *C:\VSHelp*.

2. Otwórz *cmd.exe* z uprawnieniami administratora.

3. Przejdź do folderu utworzonego w kroku 1.

4. Wpisz następujące polecenie:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Na przykład: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Wdróż zawartość

1. Utwórz udział sieciowy i skopiuj zawartość pomocy do tej lokalizacji.

     Na przykład skopiuj zawartość z *C:\VSHelp* do * \\ \myserver\VSHelp*.

2. Utwórz plik *. bat* , aby zawierał skrypt wdrażania dla zawartości pomocy. Ponieważ klient może mieć blokadę odczytu na dowolnym z plików, które są usuwane w ramach wypychania, należy zamknąć klienta przed wypchnięciem aktualizacji. Na przykład:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. Uruchom plik *bat* na lokalnych komputerach, na których chcesz zainstalować zawartość pomocy.

## <a name="see-also"></a>Zobacz też

- [Argumenty wiersza polecenia dla Menedżera zawartości pomocy](../help-viewer/command-line-arguments.md)
- [Przesłonięcia Menedżera zawartości pomocy](../help-viewer/behavior-overrides.md)
- [Podgląd Pomocy firmy Microsoft](../help-viewer/overview.md)
- [Zestaw SDK podglądu pomocy](../extensibility/internals/microsoft-help-viewer-sdk.md)