---
title: Rozwiązywanie problemów z pakietami VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d89c3181757a0ed95b818ba2e73197511bf06e4d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434248"
---
# <a name="troubleshooting-vspackages"></a>Rozwiązywanie problemów z pakietami VSPackage
Poniżej przedstawiono typowe problemy, które może być za pomocą Twojego pakietu VSPackage i porady, aby rozwiązać problemy.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Aby rozwiązać pakietu VSPackage, który przechowuje programu Visual Studio z rozpoczęciem

- Rozpocznij [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.

   Aby rozpocząć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym, w wierszu polecenia wpisz **/safemode devenv.exe**.

   W trakcie tego procesu nie pakietów VSPackage są ładowane z wyjątkiem pakietów VSPackage, które są dołączone do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Aby rozwiązać pakietu VSPackage, który nie zostanie załadowany

1. Upewnij się, że używasz Rejestr główny, w którym pakietu VSPackage jest zarejestrowana w celu uruchomienia zwykle katalog główny rejestru eksperymentalne.

    Aby uzyskać więcej informacji, zobacz [wystąpienie doświadczalne](../extensibility/the-experimental-instance.md).

2. Jeśli pakietu VSPackage jest przeznaczona do uruchamiania w eksperymentalnym Rejestr główny, upewnij się, że używasz wersji doświadczalnej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

    Aby uruchomić doświadczalne wersję, wpisz następujące polecenie w oknie polecenia: **devenv /rootsuffix exp**.

3. Sprawdź wpisy rejestru pakietu VSPackage.

    Aby uzyskać więcej informacji, zobacz [rejestrowanie pakietów VSPackage](registering-and-unregistering-vspackages.md) i [Zarządzanie pakietami VSPackage](../extensibility/managing-vspackages.md).

4. Otwórz **dane wyjściowe** okno wystąpienia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , nie może załadować pakietu VSPackage. Informacji na temat przyczyn nieudanego pakietu VSPackage załadować mogą być wyświetlane w tym oknie.

   > [!NOTE]
   > Jeśli rozpoczynasz wersji doświadczalnej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE), sprawdź **dane wyjściowe** okna obie wersje.

5. Sprawdź dziennik aktywności.

    Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

6. Aby uzyskać więcej informacji na temat wyjątków zgłaszanych przez środowisko IDE kliknij **wyjątki** na **debugowania** menu, aby włączyć wyjątki. W **wyjątki** okno dialogowe Wybierz typy wyjątków, o których chcesz uzyskać więcej informacji.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Aby rozwiązać pakietu VSPackage, która nie jest zarejestrowana

1. Upewnij się, że zestaw pakietu VSPackage znajduje się w zaufanej lokalizacji. RegPkg nie można zarejestrować zestawy w niezaufanych lub częściowo zaufanych lokalizacji, takiej jak udział sieciowy w domyślnej konfiguracji zabezpieczeń platformy .net. Mimo że w każdym przypadku, gdy użytkownik tworzy projekt w niezaufanej lokalizacji zostanie wyświetlone ostrzeżenie, zaznacz pole wyboru "nie pokazuj tego komunikatu ponownie" może uniemożliwić to ostrzeżenie występowaniu.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Aby rozwiązać polecenia, który nie jest widoczny i generuje błąd, po kliknięciu polecenia

1. Scal poleceń menu nowe lub zostały zmienione oraz tych, które już w środowisku IDE, wpisując na następujących [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia: **/rootsuffix devenv/Setup Exp**.

2. Upewnij się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można znaleźć UI.dll Twojego pakietu VSPackage.

   1. Znajdź identyfikator CLSID pakietu VSPackage w sekcji pakiety rejestru:

        HKLM\Software\Microsoft\Visual Studio\\*\<version>* \Packages

   2. Sprawdź, czy ścieżka podana przez podklucz SatelliteDll jest poprawna.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Aby rozwiązać pakietu VSPackage, który zachowuje się nieoczekiwanie

1. Ustaw punkty przerwania w kodzie.

     Dobre punktów początkowych do debugowania są konstruktora, a także metoda inicjowania. Można również ustawić punkty przerwania, w obszarze, który chcesz ocenić, takie jak polecenie menu. Aby włączyć punkty przerwania, należy uruchomić w debugerze.

    1. Na **projektu** menu, kliknij przycisk **właściwości**.

    2. Na **stron właściwości** okno dialogowe, wybierz opcję **debugowania** kartę.

    3. W **argumenty wiersza polecenia** wpisz sufiks głównej środowiska deweloperskiego, elementy docelowe pakietu VSPackage. Na przykład, aby wybrać eksperymentalne kompilacji, wpisz: **RootSuffix Exp**.

    4. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie** lub naciśnij klawisz F5.

        > [!NOTE]
        > Jeśli projekt jest debugowany, utworzyć lub załadować istniejące wystąpienie programu projekt teraz.

2. Korzystanie z dziennika aktywności.

     Śledzenie zachowania pakietu VSPackage, zapisując informacje dziennika aktywności w kluczowych punktach. Ta technika jest szczególnie przydatne podczas uruchamiania pakietu VSPackage w środowisku handlu detalicznego. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

3. Użyj symboli publicznych.

     Aby poprawić czytelność podczas debugowania, można dołączyć symboli do debugera.

    1. Z **narzędzia/Opcje** menu, przejdź do **debugowanie/symbole** okno dialogowe.

    2. Dodaj tę **symboli (.pdb) lokalizacja_pliku**:

         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)

    3. Aby zwiększyć wydajność, należy określić folder pamięci podręcznej symboli, na przykład:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Aby rozwiązać brakuje pakietu VSPackage lub jednej z jego zależności

1. Dla kodu zarządzanego upewnij się, że ścieżki odwołania są poprawne.

   1. Na **projektu** menu, kliknij przycisk **właściwości**.

   2. Wybierz **odwołania** karcie **stron właściwości** okno dialogowe i upewnij się, że wszystkie ścieżki są prawidłowe. Alternatywnie, można użyć **przeglądarki obiektów** Aby przeglądać w poszukiwaniu przywoływanych obiektów.

        Dla kodu zarządzanego, możesz użyć [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) do wyświetlania szczegółów ładowania zestawu nie powiodło się.

2. Dla niezarządzanego kodu można znaleźć identyfikator CLSID pakietu VSPackage w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] węzła rejestru CLSID:

    HKLM\Software\Microsoft\Visual Studio\\*\<version>* \CLSID

   Upewnij się, że wpis InprocServer32 ma poprawną ścieżkę biblioteki dll pakietu VSPackage.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)