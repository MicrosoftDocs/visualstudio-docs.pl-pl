---
title: Używanie narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: abae34aad980d42018c217e150ea72b5896e436e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60073805"
---
# <a name="use-visual-studio-tools-for-unity"></a>Korzystanie z narzędzi Visual Studio Tools for Unity

W tej sekcji dowiesz się, jak używać programu Visual Studio Tools dla integracji firmy Unity i funkcji zwiększających wydajność i jak za pomocą debugera programu Visual Studio do tworzenia gier Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otwierać skrypty Unity w programie Visual Studio

Gdy program Visual Studio jest [edytorem skryptu zewnętrznego dla aparatu Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio)Otwieranie dowolnego skryptu za pomocą programu Unity editor spowoduje automatyczne uruchomienie i otwórz przełącznika w programie Visual Studio z wybranym skryptu. Kliknij dwukrotnie tylko skrypt w swoim projekcie aparatu Unity.

Alternatywnie, można otworzyć programu Visual Studio bez skryptu, które są otwarte w edytorze źródła, wybierając **Otwórz projekt C#** z **zasoby** menu na platformie Unity.

![Otwórz projekt C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity

Możesz uzyskać dostęp Unity dokumentacji szybko z programu Visual Studio do skryptów. Visual Studio Tools for Unity nie znajduje się w dokumentacji interfejsu API lokalnie, spróbuje znaleźć go w trybie online.

- W programie Visual Studio, zaznacz lub umieść kursor nad interfejsu API aparatu Unity, aby dowiedzieć się o, a następnie naciśnij klawisz **Ctrl**+**Alt**+**M**, **Ctrl**+**H**

## <a name="intellisense-for-unity-api-messages"></a>Funkcja IntelliSense dla komunikatów Unity interfejsu API

Uzupełniania kodu IntelliSense ułatwia Implementuj komunikaty aparatu Unity interfejsu API w skryptach obiekt MonoBehaviour i pomaga nauki interfejsu API aparatu Unity. Aby użyć funkcji IntelliSense dla komunikatów Unity:

1. Umieść kursor w nowym wierszu w treści klasy, która pochodzi od klasy `MonoBehaviour`.

2. Rozpocznij wpisywanie nazwy Unity komunikatów, takie jak `OnTriggerEnter`.

3. Gdy litery "**ontri**" został wpisany, zostanie wyświetlona lista sugestie funkcji IntelliSense.

   ![Korzystanie z IntelliSense](media/vstu_intellisense1.png)

4. Wybór na liście, można zmienić na trzy sposoby:

    - Za pomocą **się** i **dół** klawiszy strzałek.

    - Przez kliknięcie myszą do żądanego elementu.

    - Kontynuując wpisz nazwę żądanego elementu.

5. Technologia IntelliSense można wstawić wybrane wiadomości Unity, w tym wszelkie niezbędne parametry:

    - Naciskając **kartę**.

    - Naciskając **Enter**.

    - Klikając wybrany element.

   ![Wstaw komunikatów aparatu Unity z technologii IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Kreator skryptów MonoBehavior aparatu Unity

Kreator MonoBehavior służy do wyświetlania listy wszystkich metod interfejsu API aparatu Unity i szybko zaimplementuj pustą definicję. Tej funkcji, szczególnie przy użyciu **Generuj komentarze metod** opcję włączone, jest przydatne, jeśli są nadal uczenia, co jest dostępne w interfejsie API aparatu Unity.

Aby utworzyć pusty definicje metod MonoBehavior za pomocą Kreatora MonoBehavior:

1. W programie Visual Studio, umieść kursor w miejscu metody służące do wstawienia, a następnie naciśnij klawisz **Ctrl**+**Shift**+**M** do uruchomienia Kreator MonoBehavior.

2. W **tworzyć metody skryptu** okna, zaznacz pole wyboru obok nazwy każdej metody, które chcesz dodać.

3. Użyj **Framework w wersji** listy rozwijanej wybierz odpowiednią wersję.

4. Domyślnie metody są wstawiane na położenie kursora. Alternatywnie, możesz wstawić je po dowolnej metody, która jest już zaimplementowana w klasie, zmieniając wartość **punkt wstawiania** listę rozwijaną, aby lokalizacji.

5. Jeśli chcesz, aby Kreator Generuj komentarze metod wybrano, Oznacz **Generuj komentarze metod** pola wyboru. Te komentarze są przeznaczone do pomagają zrozumieć, kiedy metoda jest wywoływana, i jakie są jej obowiązki ogólne.

6. Wybierz **OK** przycisk, aby zakończyć działanie kreatora i wstawianie metody w kodzie.

   ![Okno dialogowe Kreator monobehavior. ](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Eksplorator projektu środowiska Unity

![Okno Eksploratora projektów aparatu Unity. ](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Eksplorator projektu środowiska Unity pokazuje wszystkie pliki projektu środowiska Unity i katalogów w taki sam sposób, który wykonuje Unity Editor. Stanowi to odmianę przechodząc skrypty Unity za pomocą normalnego Eksploratorze rozwiązań Visual Studio, który organizuje ich w projekty i rozwiązania, generowane przez program Visual Studio.

- W menu głównym programu Visual Studio wybierz **Widok > Eksploratora projektów aparatu Unity**. Klawisz skrótu: **ALT**+**Shift**+**E**

   ![Wyświetl okno Eksploratora projektów aparatu Unity. ](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Profilowanie aparatu Unity

Visual Studio Tools for Unity umożliwia debugowanie edytora i gier skrypty dla projektu środowiska Unity za pomocą zaawansowany debuger programu Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Debugowanie w programie Unity editor

#### <a name="start-debugging"></a>Rozpocznij debugowanie

1. Łączenie programu Visual Studio do aparatu Unity, klikając **Odtwórz** przycisk o nazwie **Dołącz do aparatu Unity**, lub użyj skrótu klawiaturowego **F5**.

   ![Kliknij przycisk odtwarzania w programie Visual Studio](media/vstu_play-button.png)

2. Przełącz do aparatu Unity i kliknij przycisk **Odtwórz** przycisk, aby uruchomić grę w edytorze.

   ![Kliknij przycisk Play na platformie Unity](media/vstu_unity-play-button.png)

3. Uruchamiając gry w Edytor platformy Unity podczas połączenia z programu Visual Studio, wszelkie punkty przerwania, napotkała wstrzymać wykonanie w gry, a przywołać wiersza kodu, w którym gry trafiony punkt przerwania w programie Visual Studio.

#### <a name="stop-debugging"></a>Zatrzymaj debugowanie

- Kliknij przycisk **zatrzymać** znajdujący się w programie Visual Studio lub użyj skrótu klawiaturowego **Shift + F5**.

  ![Kliknij przycisk Zatrzymaj w programie Visual Studio](media/vstu_stop-debugger.png)

Aby dowiedzieć się więcej o debugowaniu w programie Visual Studio, zobacz [Pierwsze spojrzenie na debugera programu Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Dołącz do aparatu Unity i Odtwórz

Dla wygody, można zmienić **Dołącz do aparatu Unity** przycisk, aby **Dołącz do aparatu Unity i Odtwórz** trybu.

1. Kliknij małą **Strzałka w dół** obok **Dołącz do aparatu Unity** przycisku.

1. Wybierz **Dołącz do aparatu Unity i Odtwórz** z menu rozwijanego.

    ![Dołączanie i odtwarzanie](media/vstu_attach-and-play.png)

Przycisk odtwarzania staje się etykietą **Dołącz do aparatu Unity i Odtwórz**. Kliknięcie tego przycisku, lub za pomocą skrótu klawiaturowego **F5** teraz automatycznie przełącza się do programu Unity editor i uruchamia gry w edytorze, oprócz dołączanie debugera programu Visual Studio.

Klikając **zatrzymać** znajdujący się w programie Visual Studio lub za pomocą skrótu klawiaturowego **Shift**+**F5** zostanie automatycznie zatrzymany gier w programie Unity editor.

### <a name="debug-unity-player-builds"></a>Debugowanie Unity player kompilacji

Można debugować rozwoju kompilacje wiele odtwarzaczy, Unity w programie Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Włączanie debugowania skryptu w odtwarzaczu aparatu Unity

1. Na platformie Unity, Otwórz ustawienia kompilacji, wybierając **Plik > Ustawienia kompilacji**.

2. W oknie Ustawienia kompilacji, należy oznaczyć **kompilacji rozwoju** i **debugowanie skryptu** pola wyboru.

   ![Konfigurowanie ustawień kompilacji platformy Unity na potrzeby debugowania. ](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Wybór wystąpienia aparatu Unity, aby dołączyć debuger

- W programie Visual Studio, w menu głównym wybierz **Debuguj > Dołącz debuger aparatu Unity**.

   ![Dołącz debuger aparatu Unity. ](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   **Wybór wystąpienia aparatu Unity** Wyświetla okno dialogowe niektóre informacje na temat każdego wystąpienia aparatu Unity, w którym można nawiązać połączenie.

   ![Wybierz wystąpienie aparatu Unity, aby nawiązać połączenie. ](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Nazwa projektu środowiska Unity, który działa w tym wystąpieniu aparatu Unity.

   **Maszyna** nazwę komputera lub urządzenia z systemem tego wystąpienia aparatu Unity.

   **Typ** **edytora** Jeśli to wystąpienie aparatu Unity jest uruchomiony jako część programu Unity Editor; **Player** przypadku autonomicznym odtwarzaczu tego wystąpienia aparatu Unity.

   **Port** numer portu gniazda UDP, który tego wystąpienia aparatu Unity komunikuje się za pośrednictwem.

> [!IMPORTANT]
> Ponieważ Visual Studio Tools for Unity i wystąpienia środowiska Unity komunikują się za pośrednictwem gniazd sieciowych UDP, Zapora może poprosić o nim. W takim przypadku musisz autoryzować połączenie, tak aby VSTU i Unity mogą komunikować się.

### <a name="debug-a-dll-in-your-unity-project"></a>Debuguj DLL w swoim projekcie aparatu Unity

Wielu deweloperów Unity piszesz kod składników jako zewnętrzne biblioteki DLL tak, aby funkcje, które opracowują można łatwo udostępniać z innymi projektami. Visual Studio Tools for Unity ułatwia debugowanie kodu w tych bibliotek DLL, które bezproblemowo z innym kodem w swoim projekcie aparatu Unity.

> [!NOTE]
> W tej chwili Visual Studio Tools for Unity obsługuje tylko zarządzane biblioteki dll. Nie obsługuje debugowania kodu natywnej biblioteki dll, takich jak napisanego w języku C++.

Należy pamiętać, że opisanym tutaj scenariuszu założono, że kod źródłowy — oznacza to, tworzysz lub ponowne wykorzystanie kodu firmy Microsoft lub masz źródło kodu do biblioteki innych firm i zamierzasz wdrożyć ją w swoim projekcie aparatu Unity jako biblioteki DLL. W tym scenariuszu nie opisano profilowanie DLL, dla której nie masz kodu źródłowego.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Debugowanie zarządzanego projektu biblioteki DLL używane w swoim projekcie aparatu Unity

1. Dodaj istniejący projekt DLL do rozwiązania Visual Studio, generowane przez program Visual Studio Tools for Unity. Rzadziej może być rozpoczynaniu nowego zarządzanego projektu biblioteki DLL zawiera składniki kodu w swoim projekcie aparatu Unity; Jeśli tak jest rzeczywiście, możesz zamiast tego dodać nowego zarządzanego projektu biblioteki DLL do rozwiązania Visual Studio. Aby uzyskać więcej informacji na temat dodawania nowego lub istniejącego projektu do rozwiązania, zobacz [jak: Dodaj do rozwiązania, projekty](https://msdn.microsoft.com/library/ff460187.aspx).

   ![Dodaj istniejący projekt DLL do rozwiązania. ](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   W obu przypadkach program Visual Studio Tools for Unity przechowuje odwołanie do projektu, nawet wtedy, gdy jest ponownie wygenerować plików projektu i rozwiązania ponownie, wystarczy tylko jeden raz wykonać te kroki.

2. Odwołanie do poprawnego profilu framework Unity w projekcie biblioteki DLL. W programie Visual Studio, we właściwościach projektu biblioteki DLL, ustaw **platformę docelową** właściwości do korzystania z wersji framework aparatu Unity. Jest to Unity podstawowej biblioteki klas zgodną zgodności interfejsu API, że docelowy system operacyjny projektu, takie jak pełne Unity, micro lub sieci web podstawowej biblioteki klas. Zapobiega to wywołanie metody framework znajdujące się w innych platform lub poziomy zgodności, ale który nie istnieje w wersji framework Unity, którą używasz biblioteki DLL.

> [!NOTE]
> Poniżej przedstawiono tylko wymagane, jeśli używasz starszej wersji środowiska uruchomieniowego mechanizmu Unity. Jeśli używasz nowego środowiska uruchomieniowego Unity nie trzeba już używać tych dedykowanych profilów 3.5. Użyj platformy .NET 4.x profilu zgodne z wersją środowiska Unity.

   ![Ustawić platformę docelową biblioteki DLL platformy Unity. ](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Skopiuj bibliotekę DLL do folderu zasobów w swoim projekcie aparatu Unity. Na platformie Unity zasoby są pliki, które są pakowane i wdrażany wraz z Twojej aplikacji platformy Unity, tak aby mogły być załadowane w czasie wykonywania. Ponieważ biblioteki DLL są połączone w czasie wykonywania, biblioteki DLL musi zostać wdrożony jako zasoby. Edytor platformy Unity można wdrożyć jako element zawartości, wymaga bibliotek DLL, które należy umieścić w folderze Zasoby w swoim projekcie aparatu Unity. Istnieją dwa sposoby, możesz to zrobić:

   - Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, aby obejmować końcowe utworzone zadanie, które kopiuje pliki wyjściowe DLL i pliku PDB z jego folderu danych wyjściowych, aby **zasoby** folderu projektu środowiska Unity.

   - Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, aby ustawić jej folderu danych wyjściowych **zasoby** folderu projektu środowiska Unity. Biblioteki DLL i pliku PDB, pliki zostaną umieszczone w **zasoby** folderu.

   PDB, pliki są wymagane podczas debugowania, ponieważ zawiera symbole debugowania biblioteki DLL i utwórz mapę kodu, biblioteki DLL do postaci kodu źródłowego. Jeśli jest przeznaczony dla starszej wersji środowiska uruchomieniowego, Visual Studio Tools for Unity użyje informacji z biblioteki DLL i pliku PDB do tworzenia biblioteki DLL. Plik MDB debugowania symbol format jest używany przez aparat skryptów starszego aparatu Unity. Jeśli są przeznaczone dla nowego środowiska uruchomieniowego i przy użyciu pliku PDB przenośny, Visual Studio Tools for Unity nie spróbuje wykonać żadnych konwersji symbolu jako nowe środowisko uruchomieniowe Unity jest w stanie natywnie korzystanie z plików PDB przenośny.
   
   Można znaleźć więcej informacji na temat generowania plików PDB [tutaj](https://docs.microsoft.com/en-us/visualstudio/debugger/how-to-set-debug-and-release-configurations?view=vs-2019). Jeśli nowe środowisko uruchomieniowe, upewnij się, że "Informacje o debugowaniu" jest ustawiona na "Portable", aby można było prawidłowo wygenerować pliku PDB przenośny. Jeśli jest przeznaczony dla starszej wersji środowiska uruchomieniowego, należy użyć "Pełnej".

4. Debugowanie kodu. Można teraz debugować kod źródłowy biblioteki DLL wraz z kodu źródłowego w swoim projekcie aparatu Unity i wszystkie funkcje, które już znasz, takich jak punkty przerwania debugowania i krokowe wykonywanie kodu.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Narzędzia Unity Tools do obsługi funkcji programu Visual Studio można szybko wyświetlić za pomocą ich skróty klawiaturowe. Poniżej przedstawiono podsumowanie skróty, które są dostępne.

|Polecenie|Skrót|Nazwa polecenia skrótu|
|-------------|--------------|---------------------------|
|Otwórz kreatora MonoBehavior|**CTRL**+**Shift**+**M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Otwórz Eksploratora projektów aparatu Unity|**ALT**+**Shift**+**E**|**View.UnityProjectExplorer**|
|Uzyskać dostęp do dokumentacji aparatu Unity|**CTRL**+**Alt**+**M, Ctrl**+**H**|**Help.UnityAPIReference**|
|Dołącz do debuger aparatu Unity (player lub Edytor)|**_Brak wartości domyślnej_**|**Debug.AttachUnityDebugger**|

Kombinacje klawiszy skrótów można zmienić, jeśli nie chcesz, aby domyślnie. Aby uzyskać informacji na temat sposobu zmiany, zobacz [identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
