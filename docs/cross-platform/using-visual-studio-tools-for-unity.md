---
title: Korzystanie z narzędzi programu Visual Studio dla unity | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5a0595fdf7331c8b2825c6092b5b29a19974887b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302260"
---
# <a name="use-visual-studio-tools-for-unity"></a>Korzystanie z narzędzi Visual Studio Tools for Unity

W tej sekcji dowiesz się, jak używać narzędzi visual studio dla funkcji integracji i produktywności Unity i jak używać debugera programu Visual Studio do tworzenia unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otwieranie skryptów Unity w programie Visual Studio

Gdy visual studio jest [ustawiony jako edytor skryptów zewnętrznych dla Unity,](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)otwarcie dowolnego skryptu z edytora Unity zostanie automatycznie uruchomiony lub przełączyć się do programu Visual Studio z otwartym wybranym skryptem. Wystarczy dwukrotnie kliknąć skrypt w projekcie Unity.

Alternatywnie można otworzyć program Visual Studio bez otwierania skryptu w edytorze źródłowym, wybierając **open C# Project** z menu **Zasoby** w Unity.

![Otwórz projekt W#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji unity

Można uzyskać dostęp do dokumentacji skryptów Unity szybko z programu Visual Studio. Jeśli visual studio tools for Unity nie znajdzie dokumentacji interfejsu API lokalnie, spróbuje znaleźć go w trybie online.

- W programie Visual Studio wyróżnij lub umieść kursor za pomocą interfejsu API unity, o który chcesz się dowiedzieć, a następnie naciśnij **klawisze Ctrl**+**Alt**+**M**, **Ctrl**+**H**

## <a name="intellisense-for-unity-api-messages"></a>Komunikaty interfejsu API Intellisense for Unity

Intellisense code-completion ułatwia implementowanie komunikatów interfejsu API Unity w skryptach MonoBehaviour i pomaga w nauce interfejsu API Unity. Aby użyć komunikatów IntelliSense for Unity:

1. Umieść kursor na nowej linii wewnątrz treści klasy, która `MonoBehaviour`pochodzi od .

2. Zacznij wpisywać nazwę wiadomości Unity, `OnTriggerEnter`na przykład .

3. Po wpisaniu liter "**ontri**" pojawi się lista sugestii IntelliSense.

   ![Korzystanie z IntelliSense](media/vstu_intellisense1.png)

4. Zaznaczenie na liście można zmienić na trzy sposoby:

    - Za pomocą klawiszy strzałek **w górę** i **w dół.**

    - Klikając myszką na żądany element.

    - Kontynuując wpisywanie nazwy żądanego elementu.

5. IntelliSense może wstawić wybrany komunikat Unity, łącznie z niezbędnymi parametrami:

    - Naciskając **klawisz Tab**.

    - Naciskając **klawisz Enter**.

    - Klikając dwukrotnie wybrany element.

   ![Wstaw komunikat Unity z usługi IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Kreator skryptów Unity MonoBehavior

Można użyć Kreatora MonoBehavior, aby wyświetlić listę wszystkich metod interfejsu API Unity i szybko zaimplementować pustą definicję. Ta funkcja, szczególnie z opcji **Generuj komentarze metody** włączone, jest przydatna, jeśli nadal uczysz się, co jest dostępne w interfejsie API Unity.

Aby utworzyć puste definicje metod MonoBehavior za pomocą Kreatora MonoBehavior:

1. W programie Visual Studio umieść kursor w miejscu, w którym mają być wstawiane metody, a następnie naciśnij klawisz **Ctrl**+**Shift**+**M,** aby uruchomić Kreatora MonoBehavior.

2. W oknie **Tworzenie metod skryptu** zaznacz pole wyboru obok nazwy każdej metody, którą chcesz dodać.

3. Użyj **listy** rozwijanej Wersji frameworka, aby wybrać żądaną wersję.

4. Domyślnie metody są wstawiane w miejscu kursora. Alternatywnie można wybrać, aby wstawić je po dowolnej metody, która jest już zaimplementowana w klasie, zmieniając wartość **wstawiania punktu** listy rozwijanej do lokalizacji, które chcesz.

5. Jeśli chcesz, aby kreator wygenerował komentarze dla wybranych metod, zaznacz pole wyboru **Generuj komentarze metody.** Te komentarze mają na celu pomóc zrozumieć, kiedy metoda jest wywoływana i jakie są jej ogólne obowiązki.

6. Wybierz przycisk **OK,** aby zamknąć kreatora i wstawić metody do kodu.

   ![Okno dialogowe kreatora monobehavior.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Eksplorator projektu Unity

![Okno Eksplorator projektu Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Unity Project Explorer pokazuje wszystkie pliki projektu Unity i katalogi w taki sam sposób, jak Edytor Unity nie. To różni się od nawigacji skryptów Unity z normalnym Visual Studio Solution Explorer, który organizuje je w projektach i rozwiązanie generowane przez program Visual Studio.

- W głównym menu programu Visual Studio wybierz pozycję **Wyświetl > Eksploratora projektu Unity**. Skrót klawiaturowy: **Alt**+**Shift**+**E**

   ![Służy do wyświetlania okna Eksploratora projektów Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Debugowanie jedności

Narzędzia programu Visual Studio dla unity umożliwia debugowanie skryptów edytora i gry dla projektu Unity przy użyciu zaawansowanego debugera programu Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Debugowanie w edytorze Unity

#### <a name="start-debugging"></a>Rozpocznij debugowanie

1. Połącz program Visual Studio z unity, klikając przycisk **Odtwórz** z etykietą **Dołącz do unity**lub użyj skrótu klawiaturowego **F5**.

   ![Kliknij przycisk Odtwórz w programie Visual Studio](media/vstu_play-button.png)

2. Przełącz się na Jedność i kliknij przycisk **Odtwórz,** aby uruchomić grę w edytorze.

   ![Kliknij przycisk Odtwórz w jedności](media/vstu_unity-play-button.png)

3. Gdy gra jest uruchomiona w edytorze Unity podczas połączenia z programem Visual Studio, wszystkie punkty przerwania napotka wstrzymanie wykonania gry i przywołać wiersz kodu, w którym gra trafić punkt przerwania w programie Visual Studio.

#### <a name="stop-debugging"></a>Zatrzymywać debugowanie

- Kliknij przycisk **Zatrzymaj** w programie Visual Studio lub użyj skrótu klawiaturowego **Shift + F5**.

  ![Kliknij pozycję Zatrzymaj w programie Visual Studio](media/vstu_stop-debugger.png)

Aby dowiedzieć się więcej na temat debugowania w programie Visual Studio, zobacz [Pierwsze spojrzenie na debuger programu Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Dołącz do Jedności i Grać

Dla dodatkowej wygody można zmienić przycisk **Dołącz do jedności** na Tryb **dołączenia do unity i trybu odtwarzania.**

1. Kliknij małą **strzałkę w dół** obok przycisku Dołącz do **jedności.**

1. Z menu rozwijanego **wybierz pozycję Dołącz do unity i odtwórz.**

    ![Dołączanie i odtwarzanie](media/vstu_attach-and-play.png)

Przycisk odtwarzania zostanie oznaczony jako **Dołącz do Unity i Play**. Kliknięcie tego przycisku lub za pomocą skrótu klawiaturowego **F5** teraz automatycznie przełącza się do edytora Unity i uruchamia grę w edytorze, oprócz dołączania debugera programu Visual Studio.

Kliknięcie przycisku **Zatrzymaj** w programie Visual Studio lub za pomocą skrótu klawiaturowego **Shift**+**F5** spowoduje automatyczne zatrzymanie gry w edytorze Unity.

### <a name="debug-unity-player-builds"></a>Debug Unity gracz buduje

Można debugować kompilacje rozwoju różnych odtwarzaczy Unity z Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Włączanie debugowania skryptów w odtwarzaczu Unity

1. W obszarze Unity otwórz ustawienia kompilacji, wybierając **pozycję Ustawienia > kompilacji plików**.

2. W oknie Ustawienia kompilacji zaznacz pola wyboru **Kompilacja dewelopera** i **Debugowanie skryptów.**

   ![Konfigurowanie ustawień kompilacji Unity do debugowania.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Wybierz wystąpienie Unity, aby dołączyć debuger do

- W programie Visual Studio w menu głównym wybierz polecenie **Debugowanie > Dołącz debuger unity**.

   ![Dołącz debuger Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   W oknie dialogowym **Wybierz wystąpienie unity** wyświetlane są pewne informacje o każdym wystąpieniu unity, z które można się połączyć.

   ![Wybierz wystąpienie Unity, z którą chcesz się połączyć.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Nazwa projektu Unity, który jest uruchomiony w tym wystąpieniu Unity.

   **Maszyna** Nazwa komputera lub urządzenia, na których jest uruchomione to wystąpienie Unity.

   **Wpisz** **Edytor,** jeśli to wystąpienie Unity jest uruchomiony jako część Edytora Unity; **Gracz,** jeśli to wystąpienie Unity jest samodzielnym graczem.

   **Port** Numer portu gniazda UDP, które to wystąpienie Unity komunikuje się nad.

> [!IMPORTANT]
> Ponieważ narzędzia programu Visual Studio dla unity i wystąpienie Unity komunikują się za pośrednictwem gniazda sieciowego UDP, zapora może o to poprosić. W takim przypadku musisz autoryzować połączenie, aby vstu i unity mogły się komunikować.

### <a name="debug-a-dll-in-your-unity-project"></a>Debugowanie biblioteki DLL w projekcie Unity

Wielu deweloperów Unity pisze składniki kodu jako zewnętrzne biblioteki DLL, dzięki czemu funkcje, które opracowują, mogą być łatwo współużytkowane z innymi projektami. Narzędzia programu Visual Studio dla unity ułatwia debugowanie kodu w tych bibliotekach DLL bezproblemowo z innym kodem w projekcie Unity.

> [!NOTE]
> W tej chwili Visual Studio Tools for Unity obsługuje tylko zarządzane biblioteki DLL. Nie obsługuje debugowania bibliotek DLL kodu macierzystego, takich jak te napisane w języku C++.

Należy zauważyć, że scenariusz opisany w tym miejscu zakłada, że masz kod źródłowy — oznacza to, że tworzysz lub ponownie używasz własnego kodu własnej firmy lub masz kod źródłowy do biblioteki innej firmy i planuje wdrożyć go w projekcie Unity jako biblioteki DLL. W tym scenariuszu nie opisano debugowania biblioteki DLL, dla których nie masz kodu źródłowego.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Aby debugować zarządzany projekt DLL używany w projekcie Unity

1. Dodaj istniejący projekt biblioteki DLL do rozwiązania programu Visual Studio generowanego przez narzędzia programu Visual Studio dla unity. Rzadziej można uruchamiać nowy projekt biblioteki DLL zarządzane, aby zawierać składniki kodu w projekcie Unity; jeśli tak jest, można dodać nowy projekt biblioteki DLL zarządzane zamiast tego rozwiązania programu Visual Studio. Aby uzyskać więcej informacji na temat dodawania nowego lub istniejącego projektu do rozwiązania, zobacz [Jak: Dodawanie projektów do rozwiązania](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Dodaj istniejący projekt biblioteki DLL do rozwiązania.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   W obu przypadkach Visual Studio Tools for Unity przechowuje odwołanie do projektu, nawet jeśli ma ponownie wygenerować pliki projektu i rozwiązania, więc wystarczy wykonać te kroki tylko raz.

2. Odwołaj się do poprawnego profilu struktury Unity w projekcie DLL. W programie Visual Studio we właściwościach projektu biblioteki DLL ustaw właściwość **struktury docelowej** na używana wersja struktury Unity. Jest to biblioteka klas podstawowych Unity, która odpowiada zgodności interfejsu API, która jest przeznaczona dla projektu, na przykład biblioteki klas pełnych, mikroprzedsiębiorsk lub sieci web. Zapobiega to biblioteki DLL z wywoływania metod struktury, które istnieją w innych ramach lub poziomów zgodności, ale które mogą nie istnieć w wersji struktury Unity używasz.

> [!NOTE]
> Następujące są wymagane tylko wtedy, gdy używasz środowiska wykonawczego starszej wersji Unity. Jeśli używasz nowego środowiska wykonawczego Unity, nie trzeba już używać tych dedykowanych profilów 3.5. Użyj profilu .NET 4.x zgodnego z twoją wersją Unity.

   ![Ustaw platformę docelową biblioteki DLL na platformę Unity.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Skopiuj bibliotekę DLL do folderu Zasobów projektu Unity. W unity zasoby są pliki, które są pakowane i wdrażane razem z aplikacją Unity, dzięki czemu mogą być ładowane w czasie wykonywania. Ponieważ biblioteki DLL są połączone w czasie wykonywania, biblioteki DLL muszą być wdrożone jako zasoby. Aby wdrożyć jako zasób, Edytor Unity wymaga bibliotek DLL, które mają być umieszczone wewnątrz folderu Zasoby w projekcie Unity. Można to zrobić na dwa sposoby:

   - Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, aby uwzględnić zadanie utworzone po utworzeniu, które kopiuje wyjściowe pliki DLL i PDB z folderu wyjściowego do folderu **Zasoby** projektu Unity.

   - Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, aby ustawić jego folder **wyjściowy** jako folder Zasoby projektu Unity. Pliki DLL i PDB zostaną umieszczone w folderze **Zasoby.**

   Pliki PDB są potrzebne do debugowania, ponieważ zawierają symbole debugowania biblioteki DLL i mapują kod biblioteki DLL na formularz kodu źródłowego. Jeśli są przeznaczone dla starszego środowiska uruchomieniowego, Visual Studio Tools for Unity użyje informacji z biblioteki DLL i PDB do utworzenia biblioteki DLL. MDB, który jest formatem symbolu debugowania używanym przez starszy aparat skryptów Unity. Jeśli są przeznaczone dla nowego środowiska uruchomieniowego i przy użyciu Portable-PDB, Visual Studio Tools for Unity nie będzie próbował wykonać żadną konwersję symboli, jak nowy środowisko uruchomieniowe Unity jest w stanie natywnie korzystać z portable-PDB.

   Więcej informacji na temat generowania PDB można znaleźć [tutaj](/visualstudio/debugger/how-to-set-debug-and-release-configurations). Jeśli są przeznaczone dla nowego środowiska uruchomieniowego, upewnij się, że "Debugowanie informacje" jest ustawiona na "Przenośny", w celu prawidłowego generowania Portable-PDB. Jeśli kierujesz starsze środowisko uruchomieniowe, musisz użyć "Pełne".

4. Debuguj kod. Teraz można debugować kod źródłowy biblioteki DLL wraz z kodem źródłowym projektu Unity i używać wszystkich funkcji debugowania, które są używane, takich jak punkty przerwania i przechodzenie przez kod.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Dostęp do funkcji Unity Tools for Visual Studio można szybko uzyskać, używając ich skrótów klawiaturowych. Oto podsumowanie dostępnych skrótów.

|Polecenie|Skrót|Nazwa polecenia skrótu|
|-------------|--------------|---------------------------|
|Otwieranie Kreatora monobehavior|**Ctrl**+**Shift**Przesunięcie+**ctrl M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Otwórz Eksploratora projektów Unity|**Alt**+**Shift**+**E**|**View.UnityProjectExplorer**|
|Dokumentacja programu Access Unity|**Ctrl**+**Alt**+**M, Ctrl**+**H**|**Wniosek o pomoc.UnityAPIReferencja**|
|Dołącz do debugera Unity (odtwarzacza lub edytora)|**_brak wartości domyślnej_**|**Debug.AttachUnityDebugger**|

Możesz zmienić kombinacje klawiszy skrótów, jeśli nie podoba ci się ustawienie domyślne. Aby uzyskać informacje na temat jego zmiany, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
