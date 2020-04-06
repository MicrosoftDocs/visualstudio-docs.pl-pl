---
title: Rozwiązywanie problemów z pakietami VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4827a36bd8e76462a137ae7e903c1ab624121c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698913"
---
# <a name="troubleshooting-vspackages"></a>Rozwiązywanie problemów z pakietami VSPackage
Poniżej przedstawiono typowe problemy, które mogą mieć z VSPackage i porady, aby rozwiązać problemy.

### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Aby rozwiązać problem vspackage, który utrzymuje visual studio od uruchamiania

- Uruchom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w trybie awaryjnym.

   Aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchomić w trybie awaryjnym, w wierszu polecenia wpisz **devenv.exe /safemode**.

   Podczas tego procesu nie vspackages są ładowane z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]wyjątkiem VSPackages, które są dołączone do .

### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Aby rozwiązać problem vspackage, który nie ładuje

1. Upewnij się, że używasz katalogu głównego rejestru, w którym vspackage jest zarejestrowany do uruchomienia, zwykle eksperymentalny katalog główny rejestru.

    Aby uzyskać więcej informacji, zobacz [Wystąpienie eksperymentalne](../extensibility/the-experimental-instance.md).

2. Jeśli vspackage jest przeznaczony do uruchomienia w katalogu głównym rejestru eksperymentalnego, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]upewnij się, że jest uruchomiona eksperymentalna wersja programu .

    Aby uruchomić wersję eksperymentalną, wpisz następujące polecenie w oknie polecenia: **devenv /rootsuffix exp**.

3. Sprawdź wpisy rejestru VSPackage.

    Aby uzyskać więcej informacji, zobacz [Rejestrowanie pakietów VSPackages](registering-and-unregistering-vspackages.md) i [zarządzanie pakietami VSPackages](../extensibility/managing-vspackages.md).

4. Otwórz okno **Dane wyjściowe** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wystąpienia, które nie może załadować VSPackage. Informacje o tym, dlaczego vspackage nie można załadować mogą być wyświetlane w tym oknie.

   > [!NOTE]
   > Jeśli uruchamiasz eksperymentalną [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ze zintegrowanego środowiska programistycznego (IDE), sprawdź okno **Dane wyjściowe** obu wersji.

5. Sprawdź dziennik aktywności.

    Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

6. Aby uzyskać więcej informacji na temat wyjątków zgłaszanych przez IDE, kliknij **wyjątki** w menu **debugowania,** aby włączyć wyjątki. W oknie dialogowym **Wyjątki** wybierz typy wyjątków, o których chcesz uzyskać więcej informacji.

### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Aby rozwiązać problem vspackage, który nie rejestruje

1. Upewnij się, że zestaw VSPackage znajduje się w zaufanej lokalizacji. Program RegPkg nie może rejestrować zestawów w niezaufanej lub częściowo zaufanej lokalizacji, takiej jak udział sieciowy w domyślnej konfiguracji zabezpieczeń .net. Mimo że ostrzeżenie pojawia się za każdym razem, gdy użytkownik tworzy projekt w niezaufanej lokalizacji, pole wyboru "nie pokazuj ponownie tego komunikatu" może zapobiec ponownemu wystąpieniu tego ostrzeżenia.

### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Aby rozwiązać problem z poleceniem, które nie jest widoczne lub generuje błąd po kliknięciu polecenia

1. Scal nowe lub zmienione polecenia menu i te już w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, wpisując następujące w wierszu polecenia: **devenv /rootsuffix Exp /setup**.

2. Upewnij się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można znaleźć UI.dll dla VSPackage.

   1. Znajdź CLSID VSPackage w sekcji Pakiety rejestru:

        Wersja HKLM\Software\Microsoft\Visual Studio\\*\<>* \Packages

   2. Sprawdź, czy ścieżka podkluczowa SatelliteDll jest poprawna.

### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Aby rozwiązać problem vspackage, który zachowuje się nieoczekiwanie

1. Ustaw punkty przerwania w kodzie.

     Dobrymi punktami wyjścia do debugowania są konstruktor i metoda inicjowania. Można również ustawić punkty przerwania w obszarze, który chcesz ocenić, na przykład polecenie menu. Aby włączyć punkty przerwania, należy uruchomić w debugerze.

    1. W menu **Projekt** kliknij polecenie **Właściwości**.

    2. W oknie dialogowym **Strony właściwości** wybierz kartę **Debugowanie.**

    3. W polu **Argumenty wiersza polecenia** wpisz sufiks główny środowiska programistycznego, który jest przeznaczony dla programu VSPackage. Na przykład, aby wybrać kompilację eksperymentalną, wpisz: **/RootSuffix Exp**.

    4. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie** lub naciśnij klawisz F5.

        > [!NOTE]
        > Jeśli debugujesz projekt, utwórz lub załaduj istniejące wystąpienie projektu teraz.

2. Użyj dziennika aktywności.

     Śledzenie zachowania VSPackage, zapisując informacje w dzienniku aktywności w kluczowych punktach. Ta technika jest szczególnie przydatna po uruchomieniu VSPackage w środowisku sieci sprzedaży detalicznej. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).

3. Używaj symboli publicznych.

     Aby poprawić czytelność podczas debugowania, można dołączyć symbole do debugera.

    1. Z menu **Narzędzia/Opcje** przejdź do okna dialogowego **Debugowanie/Symbole.**

    2. Dodaj lokalizację **tego pliku symbolu (pdb):**

         `https://msdl.microsoft.com/download/symbols`

    3. Aby zwiększyć wydajność, należy określić folder pamięci podręcznej symboli, na przykład:

        ```
        C:\symbols
        ```

### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Aby rozwiązać problem z brakującym pakietem VSPackage lub jedną z jego zależności

1. W przypadku kodu zarządzanego upewnij się, że ścieżki odwołań są poprawne.

   1. W menu **Projekt** kliknij polecenie **Właściwości**.

   2. Zaznacz kartę **Odwołania** w oknie dialogowym **Strony właściwości** i upewnij się, że wszystkie ścieżki są poprawne. Alternatywnie można użyć **przeglądarki obiektów** do przeglądania obiektów, do których istnieją odwołania.

        Dla kodu zarządzanego, można użyć [Fuslogvw.exe (Assembly Binding Log Viewer)](/dotnet/framework/tools/fuslogvw-exe-assembly-binding-log-viewer) do wyświetlania szczegółów nie powiodło się obciążenia zestawu.

2. W przypadku kodu niezarządzanego znajdź identyfikator CLSID [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programu VSPackage w węźle rejestru CLSID:

    Wersja HKLM\Software\Microsoft\Visual Studio\\*\<>* \CLSID

   Upewnij się, że wpis InprocServer32 ma poprawną ścieżkę biblioteki DLL VSPackage.

## <a name="see-also"></a>Zobacz też
- [Pakiety VSPackage](../extensibility/internals/vspackages.md)
