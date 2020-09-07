---
title: Używanie Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d8a0db05788682bf08f9899cebb517370a1627b6
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508967"
---
# <a name="use-visual-studio-tools-for-unity"></a>Korzystanie z narzędzi Visual Studio Tools for Unity

W tej sekcji dowiesz się, jak korzystać z funkcji integracji i zwiększania produktywności Visual Studio Tools for Unity oraz jak korzystać z debugera programu Visual Studio na potrzeby projektowania środowiska Unity.

## <a name="open-unity-scripts-in-visual-studio"></a>Otwieranie skryptów aparatu Unity w programie Visual Studio

Gdy program Visual Studio jest [ustawiony jako zewnętrzny edytor skryptów dla aparatu Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), otwarcie dowolnego skryptu z edytora Unity zostanie automatycznie uruchomione lub przejdzie do programu Visual Studio z otwartym wybranym skryptem. Po prostu kliknij dwukrotnie skrypt w projekcie aparatu Unity.

Alternatywnie możesz otworzyć program Visual Studio bez otwartego skryptu w edytorze źródła, wybierając pozycję **Otwórz projekt C#** z menu **zasoby** w aparacie Unity.

![Otwórz projekt C#](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity

Możesz szybko uzyskać dostęp do dokumentacji dotyczącej skryptów aparatu Unity z programu Visual Studio. Jeśli Visual Studio Tools for Unity nie odnajdzie lokalnie dokumentacji interfejsu API, spróbuje ją znaleźć w trybie online.

- W programie Visual Studio zaznacz lub umieść kursor nad interfejsem API Unity, dla którego chcesz się dowiedzieć, a następnie naciśnij **klawisze CTRL** + **Alt** + **M**, **Ctrl** + **H**

## <a name="intellisense-for-unity-api-messages"></a>Funkcja IntelliSense dla komunikatów interfejsu API usługi Unity

Uzupełnianie kodu IntelliSense ułatwia implementowanie komunikatów interfejsu API środowiska Unity w skryptach o stałej obsłudze oraz ułatwia naukę interfejsu API aparatu Unity. Aby używać funkcji IntelliSense dla komunikatów Unity:

1. Umieść kursor w nowym wierszu wewnątrz treści klasy, która pochodzi od `MonoBehaviour` .

2. Rozpocznij wpisywanie nazwy komunikatu aparatu Unity, na przykład `OnTriggerEnter` .

3. Po wpisaniu liter "**ontri**" zostanie wyświetlona lista sugestii IntelliSense.

   ![Korzystanie z IntelliSense](media/vstu_intellisense1.png)

4. Wybór na liście można zmienić na trzy sposoby:

    - Za pomocą klawiszy strzałek w **górę** i **w dół** .

    - Klikając przyciskiem myszy na żądanym elemencie.

    - Kontynuując wpisywanie nazwy żądanego elementu.

5. Technologia IntelliSense może wstawić wybrany komunikat Unity, w tym wszelkie niezbędne parametry:

    - Naciskając klawisz **Tab**.

    - Naciskając klawisz **Enter**.

    - Przez dwukrotne kliknięcie wybranego elementu.

   ![Wstawianie komunikatu aparatu Unity z funkcji IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Kreator skryptów bezobsługowych aparatu Unity

Aby wyświetlić listę wszystkich metod interfejsu API aparatu Unity i szybko zaimplementować pustą definicję, można użyć kreatora z zachowaniem prostym. Ta funkcja, szczególnie z włączoną opcją **Generuj Komentarze metody** , jest przydatna, jeśli nadal wiesz, co jest dostępne w interfejsie API aparatu Unity.

Aby utworzyć puste definicje metod antyzachowań przy użyciu kreatora bezproblemowego:

1. W programie Visual Studio Umieść kursor w miejscu, w którym mają zostać wstawione metody, a następnie naciśnij **klawisze CTRL** + **+** + **M** , aby uruchomić Kreatora działania.

2. W oknie **Tworzenie metod skryptu** zaznacz pole wyboru obok nazwy każdej metody, którą chcesz dodać.

3. Użyj listy rozwijanej **wersja struktury** , aby wybrać żądaną wersję.

4. Domyślnie metody są wstawiane na pozycji kursora. Alternatywnie można wybrać opcję wstawienia ich po dowolnej metodzie, która jest już zaimplementowana w klasie, zmieniając wartość menu rozwijanego **punktu wstawiania** do wybranej lokalizacji.

5. Jeśli chcesz, aby Kreator generował komentarze dotyczące wybranych metod, zaznacz pole wyboru **Generuj Komentarze do metody** . Te komentarze mają na celu ułatwienie zrozumienia, kiedy Metoda jest wywoływana i jakie są jej ogólne zobowiązania.

6. Wybierz przycisk **OK** , aby zamknąć kreatora i wstawić metody do kodu.

   ![Okno dialogowe kreatora działania.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Eksplorator projektów aparatu Unity

![Okno Eksplorator projektów środowiska Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

Eksplorator projektów aparatu Unity pokazuje wszystkie pliki i katalogi projektu środowiska Unity w taki sam sposób, jak edytor Unity. Różni się to od nawigowania po skryptach aparatu Unity przy użyciu normalnego Eksplorator rozwiązań programu Visual Studio, który organizuje je w projekty i rozwiązanie wygenerowane przez program Visual Studio.

- W głównym menu programu Visual Studio wybierz pozycję **wyświetl > Eksplorator projektów środowiska Unity**. Skrót klawiaturowy: **Alt** + **SHIFT** + **E**

   ![Wyświetl okno Eksplorator projektów środowiska Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-debugging"></a>Debugowanie aparatu Unity

Visual Studio Tools for Unity umożliwia debugowanie skryptów edytora i gier dla projektu Unity przy użyciu zaawansowanego debugera programu Visual Studio.

### <a name="debug-in-the-unity-editor"></a>Debugowanie w edytorze Unity

#### <a name="start-debugging"></a>Rozpocznij debugowanie

1. Połącz program Visual Studio z aparatem Unity **Play** , klikając przycisk Odtwórz **z etykietą Dołącz do aparatu Unity**lub użyj skrótu klawiaturowego **F5**.

   ![Kliknij pozycję Odtwórz w programie Visual Studio](media/vstu_play-button.png)

2. Przejdź do aparatu Unity i kliknij przycisk **Odtwórz** , aby uruchomić grę w edytorze.

   ![Kliknij pozycję Odtwórz w środowisku Unity](media/vstu_unity-play-button.png)

3. Gdy gra jest uruchomiona w edytorze aparatu Unity podczas połączenia z programem Visual Studio, wszystkie napotkane punkty przerwania spowodują wstrzymanie wykonywania gry i wyświetlenie wiersza kodu, w którym gra osiągnęła punkt przerwania w programie Visual Studio.

#### <a name="stop-debugging"></a>Zatrzymaj debugowanie

- Kliknij przycisk **Zatrzymaj** w programie Visual Studio lub użyj skrótu klawiaturowego **Shift + F5**.

  ![Kliknij przycisk Zatrzymaj w programie Visual Studio](media/vstu_stop-debugger.png)

Aby dowiedzieć się więcej o debugowaniu w programie Visual Studio, zobacz [pierwsze spojrzenie na debuger programu Visual Studio](../debugger/debugger-feature-tour.md).

#### <a name="attach-to-unity-and-play"></a>Dołącz do aparatu Unity i Odtwórz

Aby dodać wygodę, można zmienić przycisk **Dołącz do aparatu Unity** w celu **dołączenia do trybu Unity i tryb odtwarzania** .

1. Kliknij małą **strzałkę w dół** obok przycisku **Dołącz do aparatu Unity** .

1. Wybierz opcję **Dołącz do aparatu Unity i Odtwórz** z menu rozwijanego.

    ![Dołącz i Odtwórz](media/vstu_attach-and-play.png)

Przycisk odtwarzania otrzymuje oznaczenie " **Dołącz do aparatu Unity" i Odtwórz**. Kliknięcie tego przycisku lub użycie skrótu klawiaturowego **F5** powoduje automatyczne przełączenie do edytora aparatu Unity i uruchomienie gry w edytorze, oprócz dołączania debugera programu Visual Studio.

Kliknięcie przycisku **Zatrzymaj** w programie Visual Studio lub użycie skrótu klawiaturowego **SHIFT** + **F5** spowoduje automatyczne zatrzymanie gry w edytorze aparatu Unity.

### <a name="debug-unity-player-builds"></a>Debuguj kompilacje odtwarzacza Unity

Można debugować kompilacje deweloperskie różnych graczy programu Unity przy użyciu programu Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Włączanie debugowania skryptów w odtwarzaczu Unity

1. W aparacie Unity Otwórz ustawienia kompilacji, wybierając kolejno pozycje **plik > ustawienia kompilacji**.

2. W oknie Ustawienia kompilacji zaznacz pola wyboru **kompilacja** i **debugowanie skryptu** .

   ![Skonfiguruj ustawienia kompilacji aparatu Unity na potrzeby debugowania.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Wybierz wystąpienie aparatu Unity, do którego ma zostać dołączony debuger

- W programie Visual Studio w menu głównym wybierz polecenie **debuguj > Dołącz debuger Unity**.

   ![Dołącz debuger aparatu Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

   W oknie dialogowym **Wybieranie wystąpienia aparatu Unity** są wyświetlane pewne informacje o każdym wystąpieniu aparatu Unity, z którym można nawiązać połączenie.

   ![Wybierz wystąpienie aparatu Unity, z którym chcesz nawiązać połączenie.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

   **Project**

   Nazwa projektu Unity, który jest uruchomiony w tym wystąpieniu aparatu Unity.

   **Maszyna** Nazwa komputera lub urządzenia, na którym działa to wystąpienie aparatu Unity.

   **Type** **Edytor** typów, jeśli to wystąpienie aparatu Unity działa jako część edytora Unity; **Player** Jeśli to wystąpienie aparatu Unity jest odtwarzaczem autonomicznym.

   **Port** Numer portu gniazda UDP, dla którego jest nawiązywane połączenie z tym wystąpieniem aparatu Unity.

> [!IMPORTANT]
> Ponieważ Visual Studio Tools for Unity i wystąpienie aparatu Unity komunikuje się za pośrednictwem gniazda sieciowego UDP, Zapora może zażądać tego programu. W takim przypadku konieczne będzie autoryzowanie połączenia, aby rozszerzenia VSTU i Unity mogły komunikować się.

### <a name="debug-a-dll-in-your-unity-project"></a>Debugowanie biblioteki DLL w projekcie aparatu Unity

Wielu deweloperów aparatu Unity zapisuje składniki kodu jako zewnętrzne biblioteki DLL, dzięki czemu funkcje, które opracowują, mogą być łatwo współużytkowane z innymi projektami. Visual Studio Tools for Unity ułatwia debugowanie kodu w tych bibliotekach DLL bezproblemowo z innym kodem w projekcie środowiska Unity.

> [!NOTE]
> W tej chwili Visual Studio Tools for Unity obsługuje tylko zarządzane biblioteki DLL. Nie obsługuje debugowania bibliotek DLL kodu natywnego, takich jak te, które są zapisywane w języku C++.

Należy zauważyć, że w opisany tutaj scenariuszu założono, że masz kod źródłowy — to znaczy, że tworzysz lub ponownie korzystasz z własnego kodu pierwszej firmy lub masz kod źródłowy dla biblioteki innej firmy, i planujesz wdrożyć ją w projekcie Unity jako plik DLL. W tym scenariuszu nie opisano debugowania biblioteki DLL, dla której nie masz kodu źródłowego.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Aby debugować zarządzany projekt DLL używany w projekcie aparatu Unity

1. Dodaj istniejący projekt DLL do rozwiązania programu Visual Studio wygenerowanego przez Visual Studio Tools for Unity. Rzadziej, możesz rozpocząć pracę z nowym zarządzanym projektem DLL, aby zawierał składniki kodu w projekcie Unity; w takim przypadku można zamiast tego dodać nowy zarządzany projekt do rozwiązania Visual Studio.

   ![Dodaj istniejący projekt DLL do rozwiązania.](../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

   W obu przypadkach Visual Studio Tools for Unity utrzymuje odwołanie do projektu, nawet jeśli trzeba ponownie wygenerować pliki projektu i rozwiązania, więc wystarczy wykonać te kroki tylko raz.

2. Odwołuje się do poprawnego profilu środowiska Unity Framework w projekcie DLL. W programie Visual Studio we właściwościach projektu DLL ustaw właściwość **platformy docelowej** na używaną wersję środowiska Unity. Jest to Biblioteka klas bazowych Unity zgodna ze zgodnością interfejsów API, które są obiektami docelowymi projektu, takimi jak interfejsy Unity pełnej, mikrolub sieci Web klas podstawowych. Zapobiega to wywoływaniu przez bibliotekę DLL metod platformy, które istnieją w innych strukturach lub poziomach zgodności, ale które mogą nie istnieć w używanej wersji środowiska Unity.

> [!NOTE]
> Poniższe elementy są wymagane tylko w przypadku korzystania ze starszego środowiska uruchomieniowego aparatu Unity. Jeśli używasz nowego środowiska uruchomieniowego aparatu Unity, nie musisz już korzystać z tych dedykowanych profilów 3,5. Użyj profilu platformy .NET 4. x zgodnego z wersją aparatu Unity.

   ![Ustaw platformę docelową bibliotek DLL na strukturę aparatu Unity.](../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

3. Skopiuj bibliotekę DLL do folderu zasobów projektu aparatu Unity. W środowisku Unity zasoby to pliki spakowane i wdrożone razem z aplikacją aparatu Unity, aby mogły być ładowane w czasie wykonywania. Ponieważ biblioteki DLL są połączone w czasie wykonywania, biblioteki dll należy wdrożyć jako zasoby. Aby można było wdrożyć jako element zawartości, Edytor Unity wymaga umieszczenia bibliotek DLL wewnątrz folderu Assets w projekcie środowiska Unity. Można to zrobić na dwa sposoby:

   - Zmodyfikuj ustawienia kompilacji projektu DLL, aby uwzględnić zadanie po utworzeniu skompilowane, które kopiuje wyjściowe pliki DLL i PDB z folderu wyjściowego do folderu **Assets** projektu środowiska Unity.

   - Zmodyfikuj ustawienia kompilacji projektu DLL, aby ustawić folder wyjściowy jako folder **zasobów** projektu środowiska Unity. Pliki DLL i PDB zostaną umieszczone w folderze **Assets** .

   Pliki PDB są konieczne do debugowania, ponieważ zawierają symbole debugowania biblioteki DLL i mapują kod DLL na jego formularz kodu źródłowego. Jeśli celem jest starsze środowisko uruchomieniowe, Visual Studio Tools for Unity będzie używać informacji z bibliotek DLL i PDB do tworzenia biblioteki DLL. Plik MDB, który jest formatem symboli debugowania używanym przez starszy aparat skryptów aparatu Unity. Jeśli obiektem docelowym jest nowy środowisko uruchomieniowe i użyto przenośnego pliku PDB, Visual Studio Tools for Unity nie spróbuje wykonać konwersji symboli, ponieważ nowe środowisko uruchomieniowe aparatu Unity będzie w stanie natywnie wykorzystać przenośne plików PDB.

   Więcej informacji na temat generowania plików PDB można znaleźć [tutaj](../debugger/how-to-set-debug-and-release-configurations.md). Jeśli chcesz utworzyć nowe środowisko uruchomieniowe, upewnij się, że "informacje o debugowaniu" są ustawione na "Przenośne", aby poprawnie wygenerować przenośnego pliku PDB. Jeśli obiektem docelowym jest starsze środowisko uruchomieniowe, musisz użyć pełnego.

4. Debuguj swój kod. Można teraz debugować kod źródłowy biblioteki DLL wraz z kodem źródłowym projektu środowiska Unity i korzystać ze wszystkich funkcji debugowania, które są używane do, takich jak punkty przerwania i przechodzenie przez kod.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Można szybko uzyskać dostęp do funkcji Unity Tools for Visual Studio przy użyciu skrótów klawiaturowych. Poniżej znajduje się podsumowanie dostępnych skrótów.

|Polecenie|Skrót|Nazwa polecenia skrótu|
|-------------|--------------|---------------------------|
|Otwórz kreatora z zachowaniem zachowań|**Ctrl** + **SHIFT** + **M**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|
|Otwórz Eksplorator projektów środowiska Unity|**Alt** + **SHIFT** + **E**|**Widok. UnityProjectExplorer**|
|Dokumentacja programu Access Unity|**Ctrl** + **Alt** + **M, Ctrl** + **H**|**Help. UnityAPIReference**|
|Dołącz do debugera aparatu Unity (odtwarzacz lub Edytor)|**_Brak domyślnego_**|**Debuguj. AttachUnityDebugger**|

Kombinacje klawiszy skrótów można zmienić, jeśli nie jest to ustawienie domyślne. Aby uzyskać informacje o tym, jak to zmienić, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych w programie Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
