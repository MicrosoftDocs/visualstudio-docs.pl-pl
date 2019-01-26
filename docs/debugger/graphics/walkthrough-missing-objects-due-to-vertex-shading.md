---
title: 'Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7986a05ed090141734948404cb8580633c50e74
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55004360"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Przewodnik: Brak obiektów spowodowany cieniowaniem wierzchołków
W tym instruktażu przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędziami diagnostyki grafiki do zbadania obiekt, który nie istnieje ze względu na błąd występujący podczas etapu programu do cieniowania wierzchołków.  
  
 Ten instruktaż ilustruje następujące zadania:  
  
-   Za pomocą **Lista zdarzeń graficznych** do lokalizowania potencjalnych źródeł problemu.  
  
-   Za pomocą **etapy potoku grafiki** okna, aby sprawdzić efekt skonfigurowania `DrawIndexed` wywołań interfejsu API Direct3D.  
  
-   Za pomocą **Debuger języka HLSL** do zbadania cieniowania wierzchołków.  
  
-   Za pomocą **stos wywołań zdarzenia grafiki** ułatwia znalezienie źródła Nieprawidłowa stała HLSL.  
  
## <a name="scenario"></a>Scenariusz  
 Jedną z najczęstszych przyczyn nieistniejącego obiektu w 3-w aplikacji występuje, gdy program do cieniowania wierzchołków przekształca wierzchołki obiektu w sposób niepoprawne lub nieoczekiwanego — obiekt może na przykład skalować do bardzo małym rozmiarze, lub przekształcane w taki sposób, że wydaje się za zaporą aparatu , a nie przed nim.  
  
 W tym scenariuszu po uruchomieniu aplikacji pod kątem testowania tej tło jest renderowana zgodnie z oczekiwaniami, ale nie ma jeden z obiektów. Przy użyciu programu Graphics Diagnostics można przechwytywać problemy do dziennika grafiki tak, aby można było debugować aplikację. Problem wygląda to w aplikacji:  
  
 ![Obiekt nie może być widoczny. ](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")  
  
## <a name="investigation"></a>Badanie  
 Korzystając z narzędzi programu Graphics Diagnostics, należy załadować plik dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki  
  
1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załaduj dziennik grafiki zawierający ramkę, która wykazuje Brak obiektu. Nowa karta dziennika grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części na tej karcie jest dane wyjściowe docelowy renderowania zaznaczonej klatki. W dolnej części jest **lista ramek**, powoduje wyświetlenie jako miniaturę każdej uchwyconej klatki.  
  
2. W **lista ramek**, zaznacz klatkę, która pokazuje, że obiekt nie jest wyświetlany. Obiektu docelowego renderowania jest aktualizowana, aby odzwierciedlić wybraną ramkę. W tym scenariuszu dziennika grafiki w karcie wygląda następująco:  
  
    ![Dokument dziennika grafiki w programie Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")  
  
   Po wybraniu ramkę, która demonstruje problem, można rozpocząć do zdiagnozowania go za pomocą **Lista zdarzeń graficznych**. **Lista zdarzeń graficznych** zawiera każdego interfejsu API Direct3D wywołania wykonanego do renderowania aktywną ramkę, na przykład wywołania interfejsu API, aby skonfigurować stan urządzenia, do tworzenia i aktualizowania buforów i aby rysować obiekty, które pojawiają się w ramce. Wiele rodzajów wywołania są interesujące, ponieważ często (ale nie zawsze) analogiczna zmiana obiektu docelowego renderowania, gdy aplikacja działa zgodnie z oczekiwaniami, na przykład rysowania, wysyłania, kopiowanie lub wyczyść połączenia. Wywołania rysowania są szczególnie interesujące, ponieważ każdy z nich reprezentuje geometrię, która aplikacja renderowania (wywołań wysyłania umożliwia również renderowanie geometrii).  
  
   Ponieważ wiadomo, że nieistniejącego obiektu jest nie jest wstawiany do elementu docelowego renderowania (w tym przypadku) — ale, że pozostała część sceny jest rysowana zgodnie z oczekiwaniami — możesz użyć **Lista zdarzeń graficznych** wraz z **potoku grafiki Etapy** narzędzia, aby sprawdzić, które wywołania rysowania odnosi się do nieistniejącego obiektu geometrycznego. **Etapy potoku grafiki** okno pokazuje geometrię, która została wysłana do każdego wywołania rysowania, niezależnie od jego wpływ na obiektu docelowego renderowania. Po przeniesieniu za pośrednictwem wywołania rysowania etapy potoku są aktualizowane, aby pokazać geometrię, która jest skojarzona z tym wywołaniem, a wyjście docelowego renderowania jest aktualizowany do wyświetlenia stanu obiektu docelowego renderowania po wywołaniu zostało ukończone.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć wywołanie rysowania Brak geometrii  
  
1. Otwórz **Lista zdarzeń graficznych** okna. Na **Graphics Diagnostics** narzędzi, wybierz **listy zdarzeń**.  
  
2. Otwórz **etapy potoku grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **etapy potoku**.  
  
3. Podczas przeglądania przez każdego wywołania rysowania **Lista zdarzeń graficznych** okna, obejrzyj **etapy potoku grafiki** okna dla nieistniejącego obiektu. Aby to ułatwić, wprowadź "Draw" w **wyszukiwania** polu w prawym górnym rogu **Lista zdarzeń graficznych** okna. Filtruje listę, tak aby zawiera tylko zdarzenia, które mają "Draw" w tytułach.  
  
    W **etapy potoku grafiki** oknie **asemblera dane wejściowe** etapu pokazuje geometrii obiektu przed jego przekształcone i **program do cieniowania wierzchołków** etap zawiera takie same obiekt po jest przekształcane. W tym scenariuszu, wiesz, że Ci się znaleźć nieistniejącego obiektu pojawi się w **asemblera dane wejściowe** etapu i nic nie jest wyświetlana w **program do cieniowania wierzchołków** etapu.  
  
   > [!NOTE]
   >  Jeśli inne etapy geometrii — na przykład, moduł cieniujący kadłuba, program do cieniowania domeny lub program do cieniowania geometrii etapy — przetworzyć obiektu, mogą one być przyczyną tego problemu. Zazwyczaj problem dotyczy najwcześniejszym etapie, w którym nie jest wyświetlany wynik, lub jest wyświetlany w nieoczekiwany sposób.  
  
4. Zatrzymaj po przejściu do wywołania rysowania, która odnosi się do nieistniejącego obiektu. W tym scenariuszu **etapy potoku grafiki** okno wskazuje, czy geometrii został wydany do procesora GPU (wskazywanym przez miniaturę asemblera dane wejściowe), ale nie ma obiektu docelowego renderowania, ponieważ wystąpił błąd podczas etapu programu do cieniowania wierzchołków (wskazywanym przez miniaturę program do cieniowania wierzchołków):  
  
    ![To zdarzenie DrawIndexed i jego wpływ na potok](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")  
  
   Po zakończeniu upewnij się, czy aplikacja wystawiony dla nieistniejącego obiektu geometrii wywołanie rysowania i wykryć, czy ten problem będzie się działo podczas etapu programu do cieniowania wierzchołków, Debuger języka HLSL można użyć do badania program do cieniowania wierzchołków i Dowiedz się, co się stało z obiektu, który. Możesz za pomocą debugera HLSL przeanalizować stan zmiennych HLSL w czasie wykonywania, krokowe kodu języka HLSL i ustawić punkty przerwania, aby pomóc w diagnozowaniu problemu.  
  
#### <a name="to-examine-the-vertex-shader"></a>Aby sprawdzić program do cieniowania wierzchołków  
  
1. Rozpocznij debugowanie etapu programu do cieniowania wierzchołków. W **etapy potoku grafiki** okna, w obszarze **program do cieniowania wierzchołków** przejściowe, wybierz **Rozpocznij debugowanie** przycisku.  
  
2. Ponieważ **asemblera dane wejściowe** etapu pojawia się zapewnienie dobrej dane programu do cieniowania wierzchołków i **program do cieniowania wierzchołków** etapu wydaje się generuje nie danych wyjściowych, chcesz zbadać dane wyjściowe programu do cieniowania wierzchołków struktury, `output`. Podczas wykonywania kroków za pomocą kodu języka HLSL zapoznasz się bliżej podczas wyszukiwania `output` zostanie zmodyfikowany.  
  
3. Przy pierwszej `output` zostanie zmodyfikowany element członkowski `worldPos` są zapisywane.  
  
    ![Wartość "output.worldPos" pojawia się uzasadnione](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")  
  
    Ponieważ wartość wydaje się być uzasadnione, w przypadku kontynuowania krokowe wykonywanie kodu aż do następnego wiersza, który modyfikuje `output`.  
  
4. Przy następnym `output` zostanie zmodyfikowany element członkowski `pos` są zapisywane.  
  
    ![Zerowany wartość "output.pos"](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")  
  
    Tym razem, wartość `pos` elementu członkowskiego — samych zer — jest podejrzana. Następnie chcesz określić sposób `output.pos` dostarczonych wartości samych zer.  
  
5. Można zauważyć, że `output.pos` przyjmuje wartość ze zmiennej o nazwie `temp`. W poprzednim wierszu, zobaczysz, że wartość `temp` jest wynik mnożenia wartości poprzedniej wartości przez stałą o nazwie `projection`. Podejrzewasz, że `temp`firmy podejrzane wartość jest wynikiem tej mnożenia. Po umieszczeniu wskaźnika myszy na `projection`, zwróć uwagę, czy jej wartość jest również samych zer.  
  
    ![Projekcja macierz nie zawiera nieprawidłowe przekształcenie](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")  
  
    W tym scenariuszu badanie wykazało, że `temp`firmy podejrzane wartość to najprawdopodobniej spowodowane przez jego mnożenia przez wartość `projection`, a ponieważ `projection` jest stałą, która ma zawierać macierz projekcji, wiesz, że nie powinien zawierać samych zer.  
  
   Po ustaleniu, że stała HLSL `projection`— przekazywane do programu do cieniowania przez Twoją aplikację — jest prawdopodobnie źródło problemu, następnym krokiem jest aby znaleźć lokalizację w kodzie źródłowym aplikacji, gdzie jest wypełniony stałego buforu. Możesz użyć **stos wywołań zdarzenia grafiki** można znaleźć w tej lokalizacji.  
  
#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Aby dowiedzieć się, gdy stała jest ustawiona w kodzie źródłowym aplikacji  
  
1. Otwórz **stos wywołań zdarzenia grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **stos wywołań zdarzenia grafiki**.  
  
2. Przenieś do wyższego stos wywołań do kodu źródłowego aplikacji. W **stos wywołań zdarzenia grafiki** oknie Wybierz wywołanie najważniejsze, aby zobaczyć, jeśli stały bufor jest wypełniany istnieje. Jeśli nie jest dostępne, kontynuacja górę stosu wywołań okaże się, gdzie jest wypełniany. W tym scenariuszu użytkownik stwierdzi, że stały bufor jest wypełniony — za pomocą `UpdateSubresource` interfejsu API Direct3D — dalsze w górę stosu wywołań w funkcji, która nosi nazwę `MarbleMaze::Render`, i że jego wartość pochodzi z obiektu stałego buforu, który nosi nazwę `m_marbleConstantBufferData` :  
  
    ![Kod, który ustawia obiektu stałego buforu](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")  
  
   > [!TIP]
   >  Jeśli jednocześnie debugujesz aplikację, w tym miejscu można ustawić punktu przerwania i zostanie uruchomiona, podczas renderowania następnej ramki. Następnie można sprawdzić członkowie `m_marbleConstantBufferData` do upewnij się, że wartość `projection` elementu członkowskiego jest ustawiony na samych zer, jeśli stałego buforu.  
  
   Po znalezieniu lokalizacji, w którym zostanie wypełnione stały bufor i odnajdywanie, że jego wartości pochodzą ze zmiennych `m_marbleConstantBufferData`, następnym krokiem jest, aby dowiedzieć się, gdzie `m_marbleConstantBufferData.projection` element członkowski jest ustawiany na samych zer. Możesz użyć **Znajdź wszystkie odwołania** do szybkiego skanowania w poszukiwaniu kod, który zmienia wartość `m_marbleConstantBufferData.projection`.  
  
#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Aby znaleźć, gdzie element członkowski projekcji jest ustawiany w kodzie źródłowym aplikacji  
  
1. Znajdowanie odwołań do `m_marbleConstantBufferData.projection`. Otwórz menu skrótów dla zmiennej `m_marbleConstantBufferData`, a następnie wybierz **Znajdź wszystkie odwołania**.  
  
2. Aby przejść do lokalizacji linii w kodzie źródłowym aplikacji gdzie `projection` elementu członkowskiego jest modyfikowany, wybierz tę linię w **wyniki wyszukiwania symboli** okna. Ponieważ pierwszego wyniku, który modyfikuje element członkowski projekcji mogą nie być przyczyną tego problemu, trzeba sprawdzić kilka obszarów kodu źródłowego aplikacji.  
  
   Po znalezieniu lokalizację gdzie `m_marbleConstantBufferData.projection` jest ustawiona, można sprawdzić otaczającego kod źródłowy w celu ustalenia źródła pochodzenia niepoprawną wartość. W tym scenariuszu użytkownik stwierdza, że wartość `m_marbleConstantBufferData.projection` jest ustawiony na zmiennej lokalnej o nazwie `projection` zanim została zainicjowana z wartością, która została przez kod `m_camera->GetProjection(&projection);` w następnym wierszu.  
  
   ![Projekcja marble ustawiono przed zainicjowaniem](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")  
  
   Aby rozwiązać ten problem, Przenieś wiersz kodu, który ustawia wartość `m_marbleConstantBufferData.projection` po wierszu, który inicjuje wartość zmiennej lokalnej `projection`.  
  
   ![Poprawiony C&#43; &#43; kod źródłowy](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")  
  
   Po rozwiązaniu kod można skompilować go ponownie i uruchomić aplikację ponownie, aby odnaleźć rozwiązany problem renderowania:  
  
   ![Wyświetlany obiekt teraz. ](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")