---
title: Rozwiązywanie problemów z usługą pakietów VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94cb575969f232c9b4d60e7ddc93f9f727132951
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718717"
---
# <a name="troubleshooting-vspackages"></a>Rozwiązywanie problemów z pakietami VSPackage
Poniżej przedstawiono typowe problemy, które mogą mieć pakietu VSPackage i porady dotyczące rozwiązywania problemów.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Aby rozwiązać problem z pakietu VSPackage, który uniemożliwia uruchomienie programu Visual Studio

- Uruchom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.

   Aby uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, w wierszu polecenia wpisz **devenv. exe/safemode**.

   W trakcie tego procesu nie są załadowane żadne pakietów VSPackage z wyjątkiem pakietów VSPackage, które są dołączone do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Aby rozwiązać problem z pakietu VSPackage, który nie jest ładowany

1. Upewnij się, że korzystasz z katalogu głównego rejestru, w którym pakietu VSPackage jest zarejestrowana do uruchomienia, zazwyczaj eksperymentalny katalog główny rejestru.

    Aby uzyskać więcej informacji, zobacz [wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

2. Jeśli pakietu VSPackage jest przeznaczony do uruchomienia w katalogu doświadczalnym, upewnij się, że jest uruchomiona wersja eksperymentalna [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

    Aby uruchomić eksperymentalną wersję, wpisz następujące polecenie w oknie polecenia: **devenv/rootsuffix Exp**.

3. Sprawdź wpisy rejestru pakietu VSPackage.

    Aby uzyskać więcej informacji, zobacz [Rejestrowanie pakietów VSPackage](registering-and-unregistering-vspackages.md) i [Zarządzanie pakietów VSPackage](../extensibility/managing-vspackages.md).

4. Otwórz okno **dane wyjściowe** wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], które nie może załadować pakietu VSPackage. Informacje na temat przyczyny niepowodzenia ładowania pakietu VSPackage mogą być wyświetlane w tym oknie.

   > [!NOTE]
   > Jeśli uruchamiasz eksperymentalną wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska projektowego (IDE), Sprawdź okno **dane wyjściowe** obu wersji.

5. Przejrzyj dziennik aktywności.

    Aby uzyskać więcej informacji, zobacz [How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

6. Aby uzyskać więcej informacji o wyjątkach zgłaszanych przez IDE, kliknij pozycję **wyjątki** w menu **debugowanie** , aby włączyć wyjątki. W oknie dialogowym **wyjątki** wybierz typy wyjątków, dla których chcesz uzyskać więcej informacji.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Aby rozwiązać problem z pakietu VSPackage, który nie rejestruje

1. Upewnij się, że zestaw pakietu VSPackage znajduje się w zaufanej lokalizacji. RegPkg nie może zarejestrować zestawów w niezaufanej lub częściowo zaufanej lokalizacji, takiej jak udział sieciowy w domyślnej konfiguracji zabezpieczeń platformy .NET. Mimo że ostrzeżenie jest wyświetlane za każdym razem, gdy użytkownik tworzy projekt w niezaufanej lokalizacji, pole wyboru "nie pokazuj tego komunikatu ponownie" może zapobiec wystąpieniu tego ostrzeżenia.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Rozwiązywanie problemów z niewidocznym poleceniem lub generującym błąd po kliknięciu polecenia

1. Scal nowe lub zmienione polecenia menu i te, które są już w środowisku IDE, wpisując następujące polecenie w wierszu polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]: **devenv/rootsuffix Exp/Setup**.

2. Upewnij się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mogą znaleźć interfejs użytkownika. dll dla pakietu VSPackage.

   1. Znajdź identyfikator CLSID pakietu VSPackage w sekcji Packages rejestru:

        HKLM\Software\Microsoft\Visual Studio\\ *\<wersja >* \Packages

   2. Sprawdź, czy ścieżka określona przez podklucz SatelliteDll jest poprawna.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Aby rozwiązać problem z pakietu VSPackage, który działa nieoczekiwanie

1. Ustaw punkty przerwania w kodzie.

     Dobrym punktem początkowym do debugowania są Konstruktor i metoda inicjacji. Możesz również ustawić punkty przerwania w obszarze, który chcesz oszacować, na przykład polecenie menu. Aby włączyć punkty przerwania, należy uruchomić polecenie w debugerze.

    1. W menu **projekt** kliknij polecenie **Właściwości**.

    2. W oknie dialogowym **strony właściwości** wybierz kartę **debugowanie** .

    3. W polu **argumenty wiersza polecenia** wpisz sufiks korzenia środowiska programistycznego, które są używane przez pakietu VSPackage. Na przykład, aby wybrać kompilację eksperymentalną, wpisz: **/rootsuffix Exp**.

    4. W menu **debugowanie** kliknij **Rozpocznij debugowanie** lub naciśnij klawisz F5.

        > [!NOTE]
        > Jeśli debugujesz projekt, Utwórz lub Załaduj już istniejące wystąpienie projektu.

2. Użyj dziennika aktywności.

     Śledź zachowanie pakietu VSPackage, pisząc informacje w dzienniku aktywności w kluczowych punktach. Ta technika jest szczególnie przydatna w przypadku uruchamiania pakietu VSPackage w środowisku handlu detalicznego. Aby uzyskać więcej informacji, zobacz [How to: Use the Activity Log](../extensibility/how-to-use-the-activity-log.md).

3. Użyj symboli publicznych.

     Aby zwiększyć czytelność podczas debugowania, można dołączyć symbole do debugera.

    1. W menu **Narzędzia/Opcje** przejdź do okna dialogowego **debugowanie/symbole** .

    2. Dodaj następującą **lokalizację pliku symboli (. pdb)** :

         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)

    3. Aby zwiększyć wydajność, określ folder pamięci podręcznej symboli, na przykład:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Aby rozwiązać problem braku pakietu VSPackage lub jednej z jego zależności

1. W przypadku kodu zarządzanego upewnij się, że ścieżki odwołań są poprawne.

   1. W menu **projekt** kliknij polecenie **Właściwości**.

   2. Wybierz kartę **odwołania** w oknie dialogowym **strony właściwości** i upewnij się, że wszystkie ścieżki są poprawne. Alternatywnie możesz użyć **Przeglądarka obiektów** , aby przeglądać w poszukiwaniu obiektów, do których istnieją odwołania.

        W przypadku kodu zarządzanego można użyć programu [Fuslogvw. exe (Podgląd dziennika powiązań zestawu)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) , aby wyświetlić szczegóły nieudanych obciążeń zestawu.

2. W przypadku kodu niezarządzanego Znajdź identyfikator CLSID pakietu VSPackage w węźle rejestru CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:

    HKLM\Software\Microsoft\Visual Studio\\ *\<wersja >* \CLSID

   Upewnij się, że wpis InprocServer32 ma poprawną ścieżkę do biblioteki dll pakietu VSPackage.

## <a name="see-also"></a>Zobacz także
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)