---
title: Używanie narzędzi Visual Studio Tools for Unity | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443363"
---
# <a name="using-visual-studio-tools-for-unity"></a>Używanie rozszerzenia Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji dowiesz się, jak używać programu Visual Studio Tools dla integracji firmy Unity i funkcji zwiększających wydajność i jak za pomocą debugera programu Visual Studio do tworzenia gier Unity.  
  
## <a name="unity-integration-and-productivity"></a>Integracja aparatu Unity i produktywność  
 Visual Studio Tools for Unity integruje się za pomocą edytora środowiska Unity mogą pomóc zwiększyć wydajność pracy użytkownika. Tych funkcji zwiększających produktywność zautomatyzuj typowe zadania obsługi skryptów i Przenieś informacji z aparatu Unity w programie Visual Studio, dzięki czemu nie trzeba przejść do edytora środowiska Unity możesz jej znaleźć.  
  
### <a name="unity-documentation-access"></a>Dostęp do dokumentacji aparatu Unity  
 Możesz uzyskać dostęp Unity dokumentacji szybko z programu Visual Studio do skryptów. Visual Studio Tools for Unity nie znajduje się w dokumentacji interfejsu API lokalnie, spróbuje znaleźć go w trybie online.  
  
##### <a name="to-access-unity-documentation"></a>Aby uzyskać dostęp do dokumentacji aparatu Unity  
  
- W programie Visual Studio, zaznacz lub umieść kursor nad interfejsu API aparatu Unity, aby dowiedzieć się o, a następnie naciśnij klawisz **Ctrl + Alt + M, Ctrl + H**  
  
### <a name="unity-monobehavior-scripting-wizard"></a>Kreator skryptów MonoBehavior aparatu Unity  
 Na platformie Unity większość skryptów są implementowane przez pochodząca od klasy MonoBehavior i przesłanianie niektórych jego metod. Kreator MonoBehavior szybko utworzyć pusty definicje metod MonoBehavior, który ma przeciążenia. Za pomocą tego kreatora, można określić co najmniej jednej metody, które mają być przeciążenia z listy dostępnych metod, wybierz polecenie, gdzie zostanie wstawiona do kodu i zdecyduj, czy dołączać komentarzy na temat sposobu ich używania.  
  
 ![Okno dialogowe Kreator monobehavior. ](../cross-platform/media/vstu-monobehavior-wizard-full.png "vstu_monobehavior_wizard_full")  
  
##### <a name="to-create-empty-monobehavior-method-definitions-by-using-the-monobehavior-wizard"></a>Aby utworzyć pusty definicje metod MonoBehavior za pomocą Kreatora MonoBehavior  
  
1. W programie Visual Studio, umieść kursor w których możesz chcieć metody służące do wstawienia, a następnie naciśnij klawisz **Ctrl + Shift + M** Aby uruchomić Kreatora MonoBehavior. Lub, jeśli chcesz wstawić nowe metody po taki, który został już zaimplementowany, można określić, że później; Zamiast tego nacisnąć klawisze **Ctrl + Shift + M**.  
  
2. Wybierz metody, który ma przeciążenia. W **tworzyć metody skryptu** okna, w obszarze **Wybierz metody do utworzenia**, zaznacz pole wyboru obok nazwy każdej metody przeciążenia.  
  
3. Upewnij się, że wersja framework wyświetlane w **Framework w wersji** listy rozwijanej jest zgodna z wersją używasz. Jeśli nie jest zgodny, zmień wartość z listy rozwijanej, do wersji, którego chcesz użyć.  
  
4. Wybierz, gdzie zostanie wstawiony metody. Domyślnie metody są wstawiane w położeniu kursora; Jeśli chcesz wstawić je w innej lokalizacji, można wstawić je po dowolnej metody, która jest już zaimplementowana w klasie. Aby wybrać jedno z tych lokalizacji, zmień wartość **punkt wstawiania** rozwijanego lokalizacji.  
  
5. Jeśli chcesz, aby Kreator Generuj komentarze metod wybrano, Oznacz **Generuj komentarze metod** pola wyboru. Te komentarze są przeznaczone do pomagają zrozumieć, kiedy metoda jest wywoływana, i jakie są jej obowiązki ogólne.  
  
6. Wybierz **OK** przycisk, aby zakończyć działanie kreatora i wstawianie metody w kodzie.  
  
   Kreator MonoBehavior jest szczególnie przydatne, gdy nadal zapoznawania się z interfejsu API aparatu Unity lub gdy potrzebujesz przeciążenia metody, których nie jesteś zaznajomiony z. Stały się bardziej doświadczony przy użyciu interfejsu API aparatu Unity, możesz preferować Kreatora szybkiego MonoBehavior do szybkiego tworzenia metody, które już znasz z.  
  
#### <a name="quick-monobehavior-scripting-wizard"></a>Szybkie MonoBehavior skryptów kreatora.  
 Jeśli już znasz z interfejsu API aparatu Unity, przeciążonych metod można zaimplementować nawet szybciej za pomocą Kreatora szybkiego MonoBehavior. Za pomocą tego kreatora, można określić tylko jedną metodę, która jest wstawiany bez komentarzy metody w lokalizacji kursora.  
  
 ![Okno dialogowe Szybkie monobehavior kreatora. ](../cross-platform/media/vstu-monobehavior-wizard-quick.png "vstu_monobehavior_wizard_quick")  
  
###### <a name="to-create-an-empty-monobehavior-method-definition-by-using-the-quick-monobehavior-wizard"></a>Aby utworzyć pustą definicję metody MonoBehavior za pomocą Kreatora szybkiego MonoBehavior  
  
1. W programie Visual Studio, umieść kursor w miejscu metody do wstawienia, a następnie naciśnij klawisz **Ctrl + Shift + Q** Aby uruchomić Kreatora szybkiego MonoBehavior. W przeciwieństwie do innych MonoBehavior kreatora należy umieścić kursor celowo korzystając z tego kreatora, ponieważ nowa metoda jest zawsze wstawiany istnieje.  
  
2. Upewnij się, że wersja framework wyświetlany w prawym górnym rogu **tworzyć metody skryptu** okna jest zgodna z wersją używasz. Jeśli nie jest zgodny, zmień wartość z listy rozwijanej, do wersji, którego chcesz użyć.  
  
3. Znajdź metodę, która ma być przeciążenia. W oknie Utwórz skrypt metody begin wpisując nazwę metody, w polu tekstowym. Zostanie wyświetlona lista metod, których nazwy odpowiadają zostały wprowadzone.  
  
4. Wybierz metodę, którą chcesz przeciążenia. Gdy metoda ma jest wyświetlana na liście, wybierz ją przy użyciu myszy lub klawiszy strzałek, naciśnij klawisz **Enter**. Jeśli tak jest jedyną metodą na liście, możesz po prostu nacisnąć przycisk **Enter**. Metoda jest wstawiany do kodu.  
  
### <a name="unity-project-explorer"></a>Eksplorator projektu środowiska Unity  
 Eksplorator projektu środowiska Unity można użyć do nawigacji w swoim projekcie aparatu Unity w programie Visual Studio.  
  
 ![Okno Eksploratora projektów aparatu Unity. ](../cross-platform/media/vstu-unity-project-explorer.png "vstu_unity_project_explorer")  
  
##### <a name="to-view-the-unity-project-explorer"></a>Aby wyświetlić Eksplorator projektu środowiska Unity  
  
- W programie Visual Studio, w menu głównym wybierz **widoku**, **Eksploratora projektów aparatu Unity**. Klawiatury: **Alt+Shift+E**  
  
   ![Wyświetl okno Eksploratora projektów aparatu Unity. ](../cross-platform/media/vstu-view-unity-project-explorer.png "vstu_view_unity_project_explorer")  
  
  Eksplorator projektu środowiska Unity pokazuje wszystkie pliki projektu środowiska Unity i katalogów w taki sam sposób, który wykonuje przez Edytor platformy Unity — jest inny niż przechodząc skrypty unity za pomocą Eksploratora rozwiązań, który zawiera tylko skrypt pliki, a następnie wyświetli je jako projekty i rozwiązania, generowane przez program Visual Studio Tools for Unity organizuje ich. Szczególnie w przypadku dużych projektów często jest łatwiejszy do znalezienia skryptu, który chcesz zmodyfikować przy użyciu Eksploratora projektu środowiska Unity; zapewnia także jej łatwo modyfikować inne rodzaje plików — na przykład pliki konfiguracji na podstawie tekstu — w programie Visual studio bez dodawania ich do jednego z projektów w rozwiązaniu Visual Studio.  
  
### <a name="unity-error-list"></a>Listę błędów aparatu Unity  
 Można wyświetlić komunikaty z konsoli Unity w programie Visual Studio, gdy jest połączony z wystąpieniem Unity. Obejmuje to błędy i ostrzeżenia z poziomu aparatu Unity. Komunikaty są wyświetlane w programie Visual Studio **lista błędów** okna; błąd komunikaty z aparatu Unity są wyświetlane na **błędy** karcie, komunikaty ostrzegawcze **ostrzeżenia** karty i inne komunikaty — na przykład wiadomości wysyłane przy użyciu interfejsu API aparatu Unity czy — są wyświetlane na **wiadomości** kartę.  
  
 Aby można było wyświetlić komunikaty, muszą być swoim projekcie aparatu Unity [debugowania projektu w programie Unity Player](#debugging-your-project-in-a-unity-player) obsługuje debugowanie skryptów i importowanie Visual Studio Tools for Unity pakiet, który jest odpowiedni dla używanej wersji programu Visual Studio i Program Visual Studio musi być [łączenie programu Visual Studio Unity](#connecting-visual-studio-to-unity).  
  
 Jeśli nie chcesz wyświetlić błędy, ostrzeżenia i komunikaty z aparatu Unity w programie Visual Studio **lista błędów** okna, można je wyłączyć w menu konfiguracji.  
  
### <a name="keyboard-shortcuts"></a>Skróty klawiaturowe  
 Narzędzia Unity Tools do obsługi funkcji programu Visual Studio można szybko wyświetlić za pomocą ich skróty klawiaturowe. Poniżej przedstawiono podsumowanie skróty, które są dostępne.  
  
|Polecenie|Skrót|Nazwa polecenia skrótu|  
|-------------|--------------|---------------------------|  
|Otwórz kreatora MonoBehavior|**Ctrl+Shift+M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|  
|Otwórz Kreatora szybkiego MonoBehavior|**Ctrl+Shift+Q**|**EditorContextMenus.CodeWindow.QuickMonoBehaviours**|  
|Otwórz Eksploratora projektów aparatu Unity|**Alt+Shift+E**|**View.UnityProjectExplorer**|  
|Uzyskać dostęp do dokumentacji aparatu Unity|**Ctrl+Alt+M, Ctrl+H**|**Help.UnityAPIReference**|  
|Dołącz do debuger aparatu Unity (player lub Edytor)|**_Brak wartości domyślnej_**|**Debug.AttachUnityDebugger**|  
  
 Kombinacje klawiszy skrótów można zmienić, jeśli nie chcesz, aby domyślnie. Aby uzyskać informacji na temat sposobu zmiany, zobacz [określenie i dostosowywanie skrótów klawiaturowych w programie Visual Studio](https://msdn.microsoft.com/library/5zwses53.aspx).  
  
## <a name="unity-debugging"></a>Profilowanie aparatu Unity  
 Visual Studio Tools for Unity umożliwia debugowanie edytora i gier skrypty dla projektu środowiska Unity za pomocą zaawansowany debuger programu Visual Studio.  
  
### <a name="connecting-visual-studio-to-unity"></a> Łączenie programu Visual Studio do aparatu Unity  
 Visual Studio Tools for Unity komunikuje się za pomocą aparatu Unity za pośrednictwem połączenia protokołu UDP. Oznacza to, że połączenie z wystąpieniem Unity działa lokalnie, lub dowolnego miejsca w sieci w taki sam sposób. Można połączyć do dowolnego wystąpienia aparatu Unity widać w sieci za pomocą **Wybór wystąpienia aparatu Unity** okna dialogowego.  
  
##### <a name="to-open-the-select-unity-instance-dialog"></a>Aby otworzyć okno dialogowe Wybór wystąpienia aparatu Unity  
  
- W programie Visual Studio, w menu głównym wybierz **debugowania**, **Dołącz debuger aparatu Unity**.  
  
     ![Dołącz debuger aparatu Unity. ](../cross-platform/media/vstu-debugging-attach-unity-debugger.png "vstu_debugging_attach_unity_debugger")  
  
- *Lub*, w programie Visual Studio, na pasku stanu, wybierz ikonę wtyczki w prawym dolnym rogu programu Visual Studio.  
  
     ![Ta ikona wskazuje, że w narzędziach VSTU jest podłączony do aparatu Unity. ](../cross-platform/media/vstu-connection-connected.png "vstu_connection_connected")  
  
> [!TIP]
> Jeśli ikona wtyczki zawiera znacznik wyboru, którym już nawiązano połączenie z wystąpieniem Unity.  
  
 **Wybór wystąpienia aparatu Unity** Wyświetla okno dialogowe niektóre informacje na temat każdego wystąpienia aparatu Unity, w którym można nawiązać połączenie.  
  
 ![Wybierz wystąpienie aparatu Unity, aby nawiązać połączenie. ](../cross-platform/media/vstu-connection-to-unity.png "vstu_connection_to_unity")  
  
 **Project**  
 Nazwa projektu środowiska Unity, który działa w tym wystąpieniu aparatu Unity.  
  
 **Maszyny**  
 Nazwa komputera lub urządzenia z systemem tego wystąpienia aparatu Unity.  
  
 **Typ**  
 **Edytor** Jeśli to wystąpienie aparatu Unity jest uruchomiony jako część programu Unity Editor; **Player** przypadku autonomicznym odtwarzaczu tego wystąpienia aparatu Unity.  
  
 **Port**  
 Numer portu gniazda UDP, który tego wystąpienia aparatu Unity komunikuje się za pośrednictwem.  
  
> [!IMPORTANT]
> Ponieważ Visual Studio Tools for Unity i wystąpienia środowiska Unity komunikują się za pośrednictwem gniazd sieciowych UDP, Zapora może poprosić o nim. W takim przypadku musisz autoryzować połączenie, tak aby VSTU i Unity mogą komunikować się.  
  
### <a name="debugging-your-project-in-a-unity-player"></a> Debugowanie projektu w odtwarzaczu aparatu Unity  
 Visual Studio Tools for Unity można połączyć bezpośrednio do aplikacji platformy Unity w autonomicznym odtwarzaczu, gdy nie jest uruchomiony Edytor platformy Unity lub do debugowania problemów, które są specyficzne dla tej platformy.  
  
##### <a name="to-enable-script-debugging-in-a-unity-player"></a>Aby włączyć debugowanie skryptów w odtwarzaczu aparatu Unity  
  
- Upewnij się, że tworzysz kompilacji programowania z włączonym debugowaniem skryptów. W ustawieniach kompilacji w projekcie Unity oznaczyć **kompilacji rozwoju** i **debugowanie skryptu** pola wyboru.  
  
  ![Konfigurowanie ustawień kompilacji platformy Unity na potrzeby debugowania. ](../cross-platform/media/vstu-debugging-build-settings.png "vstu_debugging_build_settings")  
  
  Ponadto do debugowania aplikacji platformy Unity, działające w **odtwarzacz internetowy Unity**, należy również skonfigurować tak, aby użyć **kanału wersji rozwoju**.  
  
##### <a name="to-configure-the-development-release-channel-in-unity-web-player"></a>W celu skonfigurowania kanału wersji rozwoju w odtwarzaczu Web aparatu Unity  
  
- W programie Unity Player sieci Web w menu kontekstowym wybierz **kanału wersji** i upewnij się, że **rozwoju** opcja jest włączona.  
  
  > [!IMPORTANT]
  > W Unity 4.2 i nowsze **kanału wersji** element menu kontekstowego jest dostępna tylko w menu kontekstowym odtwarzacz internetowy podczas **Alt** zostanie naciśnięty klawisz, ponieważ jest otwierane menu kontekstowe. Odtwarzacz internetowy działa w systemie Mac OS X, naciśnij klawisz **opcji** zamiast tego klucza.  
  
  Na koniec upewnij się, że masz połączenie z wystąpieniem Unity, które chcesz debugować. Aby uzyskać informacje o tym, jak to zrobić, zobacz [łączenie programu Visual Studio Unity](#connecting-visual-studio-to-unity) sekcji.  
  
### <a name="debugging-a-dll-in-your-unity-project"></a>Debugowanie biblioteki DLL w swoim projekcie aparatu Unity  
 Wielu deweloperów Unity piszesz kod składników jako zewnętrzne biblioteki DLL tak, aby funkcje, które opracowują można łatwo udostępniać z innymi projektami. Visual Studio Tools for Unity ułatwia debugowanie kodu w tych bibliotek DLL, które bezproblemowo z innym kodem w swoim projekcie aparatu Unity.  
  
> [!NOTE]
> W tej chwili Visual Studio Tools for Unity obsługuje tylko zarządzane biblioteki dll. Nie obsługuje debugowania kodu natywnej biblioteki dll, takich jak napisanego w języku C++.  
  
 Należy pamiętać, że opisanym tutaj scenariuszu założono, że kod źródłowy — oznacza to, tworzysz lub ponowne wykorzystanie kodu firmy Microsoft lub masz źródło kodu do biblioteki innych firm i zamierzasz wdrożyć ją w swoim projekcie aparatu Unity jako biblioteki DLL. W tym scenariuszu nie opisano profilowanie DLL, dla której nie masz kodu źródłowego.  
  
##### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Debugowanie zarządzanego projektu biblioteki DLL używane w swoim projekcie aparatu Unity  
  
1. Dodaj istniejący projekt DLL do rozwiązania Visual Studio, generowane przez program Visual Studio Tools for Unity. Rzadziej może być rozpoczynaniu nowego zarządzanego projektu biblioteki DLL zawiera składniki kodu w swoim projekcie aparatu Unity; Jeśli tak jest rzeczywiście, możesz zamiast tego dodać nowego zarządzanego projektu biblioteki DLL do rozwiązania Visual Studio. Aby uzyskać więcej informacji na temat dodawania nowego lub istniejącego projektu do rozwiązania, zobacz [jak: Dodaj do rozwiązania, projekty](https://msdn.microsoft.com/library/vstudio/ff460187.aspx).  
  
    ![Dodaj istniejący projekt DLL do rozwiązania. ](../cross-platform/media/vstu-debugging-dll-add-existing.png "vstu_debugging_dll_add_existing")  
  
    W obu przypadkach program Visual Studio Tools for Unity przechowuje odwołanie do projektu, nawet wtedy, gdy jest ponownie wygenerować plików projektu i rozwiązania ponownie, wystarczy tylko jeden raz wykonać te kroki.  
  
2. Odwołanie do poprawnego profilu framework Unity w projekcie biblioteki DLL. W programie Visual Studio, we właściwościach projektu biblioteki DLL, ustaw **platformę docelową** właściwości do korzystania z wersji framework aparatu Unity. Jest to Unity podstawowej biblioteki klas zgodną zgodności interfejsu API, że docelowy system operacyjny projektu, takie jak pełne Unity, micro lub sieci web podstawowej biblioteki klas. Zapobiega to wywołanie metody framework znajdujące się w innych platform lub poziomy zgodności, ale który nie istnieje w wersji framework Unity, którą używasz biblioteki DLL.  
  
    ![Ustawić platformę docelową biblioteki DLL platformy Unity. ](../cross-platform/media/vstu-debugging-dll-target-framework.png "vstu_debugging_dll_target_framework")  
  
3. Skopiuj bibliotekę DLL do folderu zasobów w swoim projekcie aparatu Unity. Na platformie Unity zasoby są pliki, które są pakowane i wdrażany wraz z Twojej aplikacji platformy Unity, tak aby mogły być załadowane w czasie wykonywania. Ponieważ biblioteki DLL są połączone w czasie wykonywania, biblioteki DLL musi zostać wdrożony jako zasoby. Edytor platformy Unity można wdrożyć jako element zawartości, wymaga bibliotek DLL, które należy umieścić w folderze Zasoby w swoim projekcie aparatu Unity. Istnieją dwa sposoby, możesz to zrobić:  
  
   - Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, aby obejmować końcowe utworzone zadanie, które kopiuje pliki wyjściowe DLL i pliku PDB z jego folderu danych wyjściowych, aby **zasoby** folderu projektu środowiska Unity.  
  
   - Zmodyfikuj ustawienia kompilacji projektu biblioteki DLL, aby ustawić jej folderu danych wyjściowych **zasoby** folderu projektu środowiska Unity. Biblioteki DLL i pliku PDB, pliki zostaną umieszczone w **zasoby** folderu.  
  
     PDB, pliki są wymagane podczas debugowania, ponieważ zawiera symbole debugowania biblioteki DLL i utwórz mapę kodu, biblioteki DLL do postaci kodu źródłowego. Visual Studio Tools for Unity użyje informacji z biblioteki DLL i pliku PDB do tworzenia biblioteki DLL. Plik MDB debugowania symbol format jest używany przez aparat skryptów aparatu Unity.  
  
4. Debugowanie kodu. Można teraz debugować kod źródłowy biblioteki DLL wraz z kodu źródłowego w swoim projekcie aparatu Unity i wszystkie funkcje, które już znasz, takich jak punkty przerwania debugowania i krokowe wykonywanie kodu.
