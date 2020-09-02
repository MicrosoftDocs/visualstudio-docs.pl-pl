---
title: Używanie Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: cd05f5ebad1a07e818e377b90aeb5e137f296cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810286"
---
# <a name="using-visual-studio-tools-for-unity"></a>Używanie rozszerzenia Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji dowiesz się, jak korzystać z funkcji integracji i zwiększania produktywności Visual Studio Tools for Unity oraz jak korzystać z debugera programu Visual Studio na potrzeby projektowania środowiska Unity.  
  
## <a name="unity-integration-and-productivity"></a>Integracja i produktywność aparatu Unity  
 Visual Studio Tools for Unity integruje się z edytorem aparatu Unity, aby zwiększyć produktywność. Te funkcje zwiększające produktywność automatyzują typowe zadania tworzenia skryptów i zapewniają informacje z aparatu Unity do programu Visual Studio, dzięki czemu nie trzeba przełączać się do edytora Unity, aby go znaleźć.  
  
### <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity  
 Możesz szybko uzyskać dostęp do dokumentacji dotyczącej skryptów aparatu Unity z programu Visual Studio. Jeśli Visual Studio Tools for Unity nie odnajdzie lokalnie dokumentacji interfejsu API, spróbuje ją znaleźć w trybie online.  
  
##### <a name="to-access-unity-documentation"></a>Aby uzyskać dostęp do dokumentacji aparatu Unity  
  
- W programie Visual Studio zaznacz lub umieść kursor nad interfejsem API Unity, dla którego chcesz się dowiedzieć, a następnie naciśnij **klawisze Ctrl + Alt + M, CTRL + H**  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Kreator skryptów bezobsługowych aparatu Unity  
 W środowisku Unity większość skryptów jest implementowana przez wyprowadzanie z klasy zachowań i zastępowanie niektórych metod. Za pomocą Kreatora bezproblemowego można szybko utworzyć puste definicje metod, które mają być przeciążone. Za pomocą tego kreatora można określić jedną lub więcej metod, które mają zostać przeciążać z listy dostępnych metod, wybrać miejsce wstawienia do kodu i zdecydować, czy dołączać komentarze dotyczące sposobu ich używania.  
  
 ![Okno dialogowe kreatora działania.](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>Aby utworzyć puste definicje metod antyzachowań przy użyciu kreatora z zachowaniem antyzachowań  
  
1. W programie Visual Studio Umieść kursor w miejscu, gdzie można chcieć wstawić metody, a następnie naciśnij **klawisze Ctrl + Shift + M** , aby uruchomić kreatora z zastosowaniem funkcji bezproblemowych. Lub, jeśli chcesz wstawić nowe metody po wykonaniu już implementacji, możesz określić tę opcję później; po prostu naciśnij **klawisze Ctrl + Shift + M**.  
  
2. Wybierz metody do przeciążenia. W oknie **Tworzenie metod skryptu** w obszarze **Wybierz metody do utworzenia**zaznacz pole wyboru obok nazwy każdej metody, która ma zostać przeciążać.  
  
3. Upewnij się, że wersja architektury wyświetlana na liście rozwijanej **wersji platformy** jest zgodna z używaną wersją. Jeśli nie pasuje, Zmień wartość listy rozwijanej na wersję, której chcesz użyć.  
  
4. Wybierz, gdzie mają zostać wstawione metody. Domyślnie metody są wstawiane na pozycji kursora; Jeśli chcesz wstawić je w innym miejscu, możesz je wstawić po dowolnej metodzie, która jest już zaimplementowana w klasie. Aby wybrać jedną z tych lokalizacji, Zmień wartość rozwijaną **punktu wstawiania** na żądaną lokalizację.  
  
5. Jeśli chcesz, aby Kreator generował komentarze dotyczące wybranych metod, zaznacz pole wyboru **Generuj Komentarze do metody** . Te komentarze mają na celu ułatwienie zrozumienia, kiedy Metoda jest wywoływana i jakie są jej ogólne zobowiązania.  
  
6. Wybierz przycisk **OK** , aby zamknąć kreatora i wstawić metody do kodu.  
  
   Kreator z zachowaniem aktywności jest szczególnie przydatny, gdy nadal uczysz się interfejsem API Unity lub gdy zachodzi potrzeba przeciążenia metody, której nie znasz. Dzięki interfejsowi API aparatu Unity możesz preferować Kreatora szybkiego działania, aby szybko tworzyć już znane metody.  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Kreator tworzenia skryptów szybkiego działania  
 Jeśli znasz już interfejs API aparatu Unity, możesz zaimplementować przeciążone metody jeszcze szybciej przy użyciu Kreatora szybkiego działania. Za pomocą tego kreatora można określić tylko jedną metodę, która jest wstawiana bez komentarzy do metody w lokalizacji kursora.  
  
 ![Okno dialogowe szybkie działanie kreatora.](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Aby utworzyć pustą definicję metody bezzachowanie przy użyciu Kreatora szybkiego działania  
  
1. W programie Visual Studio Umieść kursor w miejscu, w którym chcesz wstawić metodę, a następnie naciśnij **klawisze Ctrl + Shift + Q** , aby uruchomić Kreatora szybkiego działania. W przeciwieństwie do innych kreatorów z zastosowaniem funkcji bezproblemowych, należy w sposób niezbędny umieścić kursor przy użyciu tego kreatora, ponieważ nowa metoda jest zawsze wstawiana w tym miejscu.  
  
2. Upewnij się, że wersja architektury wyświetlana w prawym górnym rogu okna **Tworzenie metody skryptu** jest zgodna z używaną wersją. Jeśli nie pasuje, Zmień wartość listy rozwijanej na wersję, której chcesz użyć.  
  
3. Znajdź metodę, która ma zostać przeciążać. W oknie Tworzenie metody skryptu Rozpocznij wpisywanie nazwy metody w polu tekstowym. Zostanie wyświetlona lista metod, których nazwy są zgodne z wprowadzonymi informacjami.  
  
4. Wybierz metodę, która ma zostać przeciążać. Gdy dana metoda zostanie wyświetlona na liście, wybierz ją przy użyciu klawiszy myszy lub strzałek, a następnie naciśnij klawisz **Enter**. Jeśli jest to jedyna metoda na liście, można po prostu nacisnąć klawisz **Enter**. Metoda jest wstawiana do kodu.  
  
### <a name="unity-project-explorer"></a>Eksplorator projektów aparatu Unity  
 Eksplorator projektów środowiska Unity umożliwia nawigowanie po projekcie aparatu Unity w programie Visual Studio.  
  
 ![Okno Eksplorator projektów środowiska Unity.](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>Aby wyświetlić Eksplorator projektów środowiska Unity  
  
- W programie Visual Studio, w menu głównym, wybierz **Widok**, **Eksplorator projektów środowiska Unity**. Klawiatura: **Alt + Shift + E**  
  
   ![Wyświetl okno Eksplorator projektów środowiska Unity.](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Eksplorator projektów aparatu Unity pokazuje wszystkie pliki i katalogi projektu środowiska Unity w taki sam sposób, jak edytor Unity — jest to inne niż nawigowanie po skryptach Unity przy użyciu Eksplorator rozwiązań, który zawiera tylko pliki skryptów i wyświetla je jako projekty i rozwiązanie generowane przez Visual Studio Tools for Unity organizuje je. Szczególnie w dużych projektach często łatwiej jest zlokalizować skrypt, który ma zostać zmodyfikowany za pomocą Eksploratora projektów środowiska Unity. ułatwia to również modyfikowanie innych rodzajów plików — na przykład plików konfiguracyjnych tekstowych — w programie Visual Studio bez dodawania ich do jednego z projektów w rozwiązaniu Visual Studio.  
  
### <a name="unity-error-list"></a>Lista błędów Unity  
 W programie Visual Studio można wyświetlać komunikaty z konsoli aparatu Unity, gdy jest ona podłączona do wystąpienia aparatu Unity. Dotyczy to również błędów i ostrzeżeń z aparatu Unity. Komunikaty są wyświetlane w oknie **Lista błędów** programu Visual Studio; komunikaty o błędach z aparatu Unity są wyświetlane na karcie **Błędy** , komunikaty ostrzegawcze na karcie **ostrzeżenia** , a inne komunikaty — na przykład komunikaty wysyłane przy użyciu interfejsu API programu Debug. log Unity — są wyświetlane na karcie **komunikaty** .  
  
 Aby wyświetlić komunikaty, projekt środowiska Unity musi [debugować projekt w odtwarzaczu Unity](#debugging-your-project-in-a-unity-player) , aby obsługiwał debugowanie skryptów i zaimportować pakiet Visual Studio Tools for Unity odpowiedni dla używanej wersji programu Visual Studio, a program Visual Studio musi [połączyć program Visual Studio z](#connecting-visual-studio-to-unity)aparatem Unity.  
  
 Jeśli nie chcesz wyświetlać błędów, ostrzeżeń i komunikatów z aparatu Unity w oknie **Lista błędów** programu Visual Studio, możesz je wyłączyć w menu Konfiguracja.  
  
### <a name="keyboard-shortcuts"></a>Skróty klawiaturowe  
 Można szybko uzyskać dostęp do funkcji Unity Tools for Visual Studio przy użyciu skrótów klawiaturowych. Poniżej znajduje się podsumowanie dostępnych skrótów.  
  
|Polecenie|Skrót|Nazwa polecenia skrótu|  
|-------------|--------------|---------------------------|  
|Otwórz kreatora z zachowaniem zachowań|**Ctrl+Shift+M**|**EditorContextMenus. CodeWindow. ImplementMonoBehaviours**|  
|Otwórz Kreatora szybkiego działania|**Ctrl+Shift+Q**|**EditorContextMenus. CodeWindow. QuickMonoBehaviours**|  
|Otwórz Eksplorator projektów środowiska Unity|**Alt + Shift + E**|**Widok. UnityProjectExplorer**|  
|Dokumentacja programu Access Unity|**Ctrl + Alt + M, CTRL + H**|**Help. UnityAPIReference**|  
|Dołącz do debugera aparatu Unity (odtwarzacz lub Edytor)|**_Brak domyślnego_**|**Debuguj. AttachUnityDebugger**|  
  
 Kombinacje klawiszy skrótów można zmienić, jeśli nie jest to ustawienie domyślne. Aby uzyskać informacje na temat sposobu jego zmiany, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych w programie Visual Studio](https://msdn.microsoft.com/library/5zwses53.aspx).  
  
## <a name="unity-debugging"></a>Debugowanie aparatu Unity  
 Visual Studio Tools for Unity umożliwia debugowanie skryptów edytora i gier dla projektu Unity przy użyciu zaawansowanego debugera programu Visual Studio.  
  
### <a name="connecting-visual-studio-to-unity"></a><a name="connecting-visual-studio-to-unity"></a> Łączenie programu Visual Studio z aparatem Unity  
 Visual Studio Tools for Unity komunikuje się z usługą Unity za pomocą połączenia UDP. Oznacza to, że można połączyć się z wystąpieniem aparatu Unity działającego lokalnie lub w dowolnym miejscu w sieci w taki sam sposób. Można nawiązać połączenie z dowolnym wystąpieniem aparatu Unity, które można zobaczyć w sieci przy użyciu okna dialogowego **Wybieranie wystąpienia aparatu Unity** .  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>Aby otworzyć okno dialogowe Wybieranie wystąpienia aparatu Unity  
  
- W programie Visual Studio w menu głównym wybierz polecenie **Debuguj**, **Dołącz debuger aparatu Unity**.  
  
     ![Dołącz debuger aparatu Unity.](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
- *Lub*w programie Visual Studio na pasku stanu wybierz ikonę wtyczki w prawym dolnym rogu programu Visual Studio.  
  
     ![Ta ikona pokazuje rozszerzenia VSTU jest podłączony do aparatu Unity.](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
> Jeśli ikona wtyczki pokazuje znacznik wyboru, nastąpiło już połączenie z wystąpieniem aparatu Unity.  
  
 W oknie dialogowym **Wybieranie wystąpienia aparatu Unity** są wyświetlane pewne informacje o każdym wystąpieniu aparatu Unity, z którym można nawiązać połączenie.  
  
 ![Wybierz wystąpienie aparatu Unity, z którym chcesz nawiązać połączenie.](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Project**  
 Nazwa projektu Unity, który jest uruchomiony w tym wystąpieniu aparatu Unity.  
  
 **Maszyna**  
 Nazwa komputera lub urządzenia, na którym działa to wystąpienie aparatu Unity.  
  
 **Typ**  
 **Edytor** , jeśli to wystąpienie aparatu Unity działa jako część edytora Unity; **Player** Jeśli to wystąpienie aparatu Unity jest odtwarzaczem autonomicznym.  
  
 **Port**  
 Numer portu gniazda UDP, dla którego jest nawiązywane połączenie z tym wystąpieniem aparatu Unity.  
  
> [!IMPORTANT]
> Ponieważ Visual Studio Tools for Unity i wystąpienie aparatu Unity komunikuje się za pośrednictwem gniazda sieciowego UDP, Zapora może zażądać tego programu. W takim przypadku konieczne będzie autoryzowanie połączenia, aby rozszerzenia VSTU i Unity mogły komunikować się.  
  
### <a name="debugging-your-project-in-a-unity-player"></a><a name="debugging-your-project-in-a-unity-player"></a> Debugowanie projektu w odtwarzaczu Unity  
 Możesz połączyć Visual Studio Tools for Unity bezpośrednio z aplikacją aparatu Unity działającą w autonomicznym odtwarzaczu, gdy nie korzystasz z edytora Unity lub aby debugować problemy, które są specyficzne dla platformy.  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>Aby włączyć debugowanie skryptów w odtwarzaczu Unity  
  
- Upewnij się, że tworzysz kompilację programistyczną z włączonym debugowaniem skryptów. W ustawieniach kompilacji projektu środowiska Unity zaznacz pola wyboru **kompilacja** i **debugowanie skryptu** .  
  
  ![Skonfiguruj ustawienia kompilacji aparatu Unity na potrzeby debugowania.](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  Ponadto, aby debugować aplikację aparatu Unity działającą w **odtwarzaczu internetowym Unity**, należy również skonfigurować ją do korzystania z **kanału wersji deweloperskiej**.  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>Aby skonfigurować kanał wydania programistycznego w odtwarzaczu internetowym Unity  
  
- W odtwarzaczu sieci Web Unity w menu kontekstowym wybierz pozycję **wersja kanału** i upewnij się, że opcja **programowanie** jest włączona.  
  
  > [!IMPORTANT]
  > W środowisku Unity 4,2 i nowszych element menu kontekstowego **kanału wydania** jest dostępny tylko w menu kontekstowym odtwarzacza sieci **Web, gdy** zostanie naciśnięte menu kontekstowe. Jeśli odtwarzacz internetowy działa na Mac OS X, naciśnij klawisz **Option** .  
  
  Na koniec upewnij się, że nawiązano połączenie z wystąpieniem aparatu Unity, które chcesz debugować. Aby uzyskać informacje o tym, jak to zrobić, zobacz sekcję [łączenie programu Visual Studio z](#connecting-visual-studio-to-unity) aparatem Unity.  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>Debugowanie biblioteki DLL w projekcie aparatu Unity  
 Wielu deweloperów aparatu Unity zapisuje składniki kodu jako zewnętrzne biblioteki DLL, dzięki czemu funkcje, które opracowują, mogą być łatwo współużytkowane z innymi projektami. Visual Studio Tools for Unity ułatwia debugowanie kodu w tych bibliotekach DLL bezproblemowo z innym kodem w projekcie środowiska Unity.  
  
> [!NOTE]
> W tej chwili Visual Studio Tools for Unity obsługuje tylko zarządzane biblioteki DLL. Nie obsługuje debugowania bibliotek DLL kodu natywnego, takich jak te, które są zapisywane w języku C++.  
  
 Należy zauważyć, że w opisany tutaj scenariuszu założono, że masz kod źródłowy — to znaczy, że tworzysz lub ponownie korzystasz z własnego kodu pierwszej firmy lub masz kod źródłowy dla biblioteki innej firmy, i planujesz wdrożyć ją w projekcie Unity jako plik DLL. W tym scenariuszu nie opisano debugowania biblioteki DLL, dla której nie masz kodu źródłowego.  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Aby debugować zarządzany projekt DLL używany w projekcie aparatu Unity  
  
1. Dodaj istniejący projekt DLL do rozwiązania programu Visual Studio wygenerowanego przez Visual Studio Tools for Unity. Rzadziej, możesz rozpocząć pracę z nowym zarządzanym projektem DLL, aby zawierał składniki kodu w projekcie Unity; w takim przypadku można zamiast tego dodać nowy zarządzany projekt do rozwiązania Visual Studio. Aby uzyskać więcej informacji na temat dodawania nowego lub istniejącego projektu do rozwiązania, zobacz [jak: Dodawanie projektów do rozwiązania](https://msdn.microsoft.com/library/vstudio/ff460187.aspx).  
  
    ![Dodaj istniejący projekt DLL do rozwiązania.](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    W obu przypadkach Visual Studio Tools for Unity utrzymuje odwołanie do projektu, nawet jeśli trzeba ponownie wygenerować pliki projektu i rozwiązania, więc wystarczy wykonać te kroki tylko raz.  
  
2. Odwołuje się do poprawnego profilu środowiska Unity Framework w projekcie DLL. W programie Visual Studio we właściwościach projektu DLL ustaw właściwość **platformy docelowej** na używaną wersję środowiska Unity. Jest to Biblioteka klas bazowych Unity zgodna ze zgodnością interfejsów API, które są obiektami docelowymi projektu, takimi jak interfejsy Unity pełnej, mikrolub sieci Web klas podstawowych. Zapobiega to wywoływaniu przez bibliotekę DLL metod platformy, które istnieją w innych strukturach lub poziomach zgodności, ale które mogą nie istnieć w używanej wersji środowiska Unity.  
  
    ![Ustaw platformę docelową bibliotek DLL na strukturę aparatu Unity.](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. Skopiuj bibliotekę DLL do folderu zasobów projektu aparatu Unity. W środowisku Unity zasoby to pliki spakowane i wdrożone razem z aplikacją aparatu Unity, aby mogły być ładowane w czasie wykonywania. Ponieważ biblioteki DLL są połączone w czasie wykonywania, biblioteki dll należy wdrożyć jako zasoby. Aby można było wdrożyć jako element zawartości, Edytor Unity wymaga umieszczenia bibliotek DLL wewnątrz folderu Assets w projekcie środowiska Unity. Można to zrobić na dwa sposoby:  
  
   - Zmodyfikuj ustawienia kompilacji projektu DLL, aby uwzględnić zadanie po utworzeniu skompilowane, które kopiuje wyjściowe pliki DLL i PDB z folderu wyjściowego do folderu **Assets** projektu środowiska Unity.  
  
   - Zmodyfikuj ustawienia kompilacji projektu DLL, aby ustawić folder wyjściowy jako folder **zasobów** projektu środowiska Unity. Pliki DLL i PDB zostaną umieszczone w folderze **Assets** .  
  
     Pliki PDB są konieczne do debugowania, ponieważ zawierają symbole debugowania biblioteki DLL i mapują kod DLL na jego formularz kodu źródłowego. Visual Studio Tools for Unity będzie używać informacji z bibliotek DLL i PDB do tworzenia biblioteki DLL. Plik MDB, który jest formatem symboli debugowania używanym przez aparat skryptów aparatu Unity.  
  
4. Debuguj swój kod. Można teraz debugować kod źródłowy biblioteki DLL wraz z kodem źródłowym projektu środowiska Unity i korzystać ze wszystkich funkcji debugowania, które są używane do, takich jak punkty przerwania i przechodzenie przez kod.
