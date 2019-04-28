---
title: 'Przewodnik: Brak obiektów spowodowany błędnie skonfigurowanym potokiem | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a00c52b9c167d1fbffc64135b0454110dc929286
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388581"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Przewodnik: brak obiektów spowodowany błędnie skonfigurowanym potokiem
W tym instruktażu przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędziami diagnostyki grafiki do zbadania obiekt, który nie istnieje ze względu na program do cieniowania pikseli nie ustawiono.

 Ten instruktaż ilustruje następujące zadania:

- Za pomocą **Lista zdarzeń graficznych** do lokalizowania potencjalnych źródeł problemu.

- Za pomocą **etapy potoku grafiki** okna, aby sprawdzić efekt `DrawIndexed` wywołania interfejsu API Direct3D.

- Sprawdzanie kontekstu urządzenia, aby upewnić się, że etapu programu do cieniowania nie została ustawiona.

- Za pomocą **etapy potoku grafiki** okna razem z **stos wywołań zdarzenia grafiki** ułatwia znalezienie źródła programu do cieniowania pikseli nie ustawiono.

## <a name="scenario"></a>Scenariusz
 Gdy obiekt jest brak w 3-w aplikacji, jest czasami ponieważ jeden z etapów modułu cieniującego nie została ustawiona przed wyświetleniem obiektu. W aplikacjach, które mają potrzeby renderowania prosty źródłem tego błędu jest zazwyczaj znajduje się gdzieś w stosie wywołań wywołania rysowania obiektu. Jednak optymalizacji, niektóre aplikacje usługi batch razem obiektów, które mają programów do cieniowania, tekstury lub inne dane w typowych w celu zminimalizowania — zmiana stanu obciążenie. W tych aplikacjach źródła błędu może być ukryty w systemu przetwarzania wsadowego, a nie znajduje się w stosie wywołań wywołania rysowania. Scenariusz, w tym przewodniku przedstawiono aplikację, która ma potrzeby renderowania proste, a źródła błędu można znaleźć w stosie wywołań.

 W tym scenariuszu po uruchomieniu aplikacji pod kątem testowania tej tło jest renderowana zgodnie z oczekiwaniami, ale nie pojawia się jeden z obiektów. Przy użyciu programu Graphics Diagnostics można przechwytywać problemy do dziennika grafiki tak, aby można było debugować aplikację. Problem wygląda to w aplikacji:

 ![Nie można zobaczyć obiekt](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Badanie
 Korzystając z narzędzi programu Graphics Diagnostics, należy załadować dokument dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki

1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ładowanie dokumentu dziennika grafiki zawierający ramkę, która wykazuje Brak obiektu. Nowa karta dziennika grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części na tej karcie jest dane wyjściowe docelowy renderowania zaznaczonej klatki. W dolnej części jest **lista ramek**, powoduje wyświetlenie jako miniaturę każdej uchwyconej klatki.

2. W **lista ramek**, zaznacz klatkę, która pokazuje, że obiekt nie jest wyświetlany. Obiektu docelowego renderowania jest aktualizowana, aby odzwierciedlić wybraną ramkę. W tym scenariuszu dziennika grafiki w karcie wygląda następująco:

    ![Dokument dziennika grafiki w programie Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Po zaznaczeniu klatki, która demonstruje problem, można rozpocząć do zdiagnozowania go za pomocą **Lista zdarzeń graficznych**. **Lista zdarzeń graficznych** zawiera każde wywołanie interfejsu API Direct3D do renderowania aktywnej ramki — na przykład, aby skonfigurować stan urządzenia, do tworzenia i aktualizowania buforów i aby rysować obiekty, które pojawiają się w ramce. Wiele rodzajów wywołania — na przykład rysowania, wysyłania, kopiowanie lub wyczyść wywołania — są interesujące, ponieważ często (ale nie zawsze) analogiczna zmiana obiektu docelowego renderowania, gdy aplikacja działa zgodnie z oczekiwaniami. Wywołania rysowania są szczególnie interesujące, ponieważ każdy z nich reprezentuje geometrię, która aplikacja renderowane.

   Ponieważ wiadomo, że nie zawiera obiektu docelowego renderowania brakujący obiektu, ale też że wydaje się być inne błędy, można użyć **Lista zdarzeń graficznych** wraz z **etapy potoku grafiki**narzędzia, aby sprawdzić, które wywołania rysowania odnosi się do nieistniejącego obiektu geometrycznego. **Etapy potoku grafiki** okno pokazuje geometrię, która została wysłana do każdego wywołania rysowania, niezależnie od jego wpływ na obiektu docelowego renderowania. Po przeniesieniu za pośrednictwem wywołania rysowania etapy potoku są aktualizowane, aby pokazać geometrię, która jest skojarzona z każdym wywołaniu, podczas ich przepływu w każdym etapie włączona, a wyjście docelowego renderowania aktualizowany w celu pokazania stanu obiektu docelowego renderowania, po zakończeniu wywołanie.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć wywołanie rysowania Brak geometrii

1. Otwórz **Lista zdarzeń graficznych** okna. Na **Graphics Diagnostics** narzędzi, wybierz **listy zdarzeń**.

2. Otwórz **etapy potoku grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **etapy potoku**.

3. Podczas przeglądania przez każdego wywołania rysowania **Lista zdarzeń graficznych** okna, obejrzyj **etapy potoku grafiki** okna dla nieistniejącego obiektu. Aby to ułatwić, wprowadź "Draw" w **wyszukiwania** polu w prawym górnym rogu **Lista zdarzeń graficznych** okna. Filtruje listę, tak aby zawiera tylko zdarzenia, które mają "Draw" w tytułach.

    W **etapy potoku grafiki** oknie **asemblera dane wejściowe** etapu obiektu, który pokazuje, zanim jest przekształcane i **program do cieniowania wierzchołków** etap zawiera takie same obiekt po jest przekształcane. W tym scenariuszu należy zauważyć, że **etapy potoku grafiki** Pokazuje okno **asemblera dane wejściowe** i **program do cieniowania wierzchołków** przygotowuje, ale nie **programu do cieniowania pikseli**  etapu dla jednego wywołania rysowania.

   > [!NOTE]
   > Jeśli inne etapy potoku — na przykład, moduł cieniujący kadłuba, program do cieniowania domeny lub etapów modułu cieniującego geometrii — przetworzyć obiektu, żadnego z nich mogą być przyczyną tego problemu. Zazwyczaj problem dotyczy najwcześniejszym etapie, w którym nie jest wyświetlany wynik, lub jest wyświetlany w nieoczekiwany sposób.

4. Zatrzymaj po przejściu do wywołania rysowania, która odnosi się do nieistniejącego obiektu. W tym scenariuszu **etapy potoku grafiki** okno wskazuje, czy geometrii został wydany do procesora GPU (wskazywane przez obecność **asemblera dane wejściowe** etapu) i po przekształceniu (wskazywanym przez  **Program do cieniowania wierzchołków** etapu), ale nie będzie wyświetlany w obiektu docelowego renderowania, ponieważ ma się nie podoba się program do cieniowania pikseli aktywne (wskazywanym przez brak **programu do cieniowania pikseli** etapu). W tym scenariuszu może nawet zobaczysz nakładające nieistniejącego obiektu w **scalanie danych wyjściowych** etapu:

    ![To zdarzenie DrawIndexed i jego wpływ na potok](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Po upewnij się, czy aplikacja wystawiony dla nieistniejącego obiektu geometrii wywołanie rysowania i wykryć, że etapu programu do cieniowania pikseli był nieaktywny, można zbadać stanu urządzenia, aby potwierdzić swoje znaleziska. Możesz użyć **Graphics Object Table** zbadać kontekst urządzenia i inne dane obiektu Direct3D.

#### <a name="to-examine-device-context"></a>Aby zbadać kontekst urządzenia

1. Otwórz **kontekstu urządzenia d3d11**. W **etapy potoku grafiki** oknie Wybierz **ID3D11DeviceContext** łącza, który jest częścią `DrawIndexed` wywołań, który jest wyświetlany w górnej części okna.

2. Sprawdź stan urządzenia, która jest wyświetlana w **kontekstu urządzenia d3d11** kartę, aby potwierdzić, że nie program do cieniowania pikseli aktywne podczas wywołania rysowania. W tym scenariuszu **ogólne informacje programu do cieniowania**— wyświetlany w obszarze **stan programu do cieniowania pikseli**— wskazuje, że programu do cieniowania jest **NULL**:

    ![Kontekst urządzenia D3D 11 pokazuje stan programu do cieniowania pikseli](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Po upewnieniu się, że program do cieniowania pikseli została ustawiona na wartość null przez aplikację, następnym krokiem jest aby znaleźć lokalizację w kodzie źródłowym aplikacji którego ustawiono programu do cieniowania. Możesz użyć **Lista zdarzeń graficznych** wraz z **stos wywołań zdarzenia grafiki** można znaleźć w tej lokalizacji.

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Aby dowiedzieć się, gdzie program do cieniowania pikseli jest ustawiony w kodzie źródłowym aplikacji

1. Znajdź `PSSetShader` wywołania, które odnosi się do nieistniejącego obiektu. W **Lista zdarzeń graficznych** oknie wprowadź "Draw; PSSetShader"w **wyszukiwania** polu w prawym górnym rogu **Lista zdarzeń graficznych** okna. Filtruje listę, tak aby zawierała tylko zdarzenia "PSSetShader" i zdarzenia, które mają "Draw" w tytułach. Wybierz pierwsze `PSSetShader` wywołania, które pojawia się przed wywołaniem rysowania brakuje obiektu.

   > [!NOTE]
   > `PSSetShader` nie będzie wyświetlane w **Lista zdarzeń graficznych** okna, jeśli nie została ustawiona podczas tej ramki. Zwykle dzieje się tak tylko wtedy, gdy program do cieniowania pikseli tylko jeden jest używany dla wszystkich obiektów lub jeśli `PSSetShader` wywołanie przypadkowo została pominięta podczas tej ramki. W obu przypadkach firma Microsoft zaleca, wyszukiwanie kod źródłowy aplikacji `PSSetShader` wywołania i użyciu tradycyjnych technik debugowania, aby sprawdzić zachowanie tych wywołań.

2. Otwórz **stos wywołań zdarzenia grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **stos wywołań zdarzenia grafiki**.

3. Użyj stos wywołań, aby zlokalizować `PSSetShader` wywołania w kodzie źródłowym aplikacji. W **stos wywołań zdarzenia grafiki** oknie Wybierz wywołanie najbardziej na wierzchu i sprawdź program do cieniowania pikseli jest ustawiana na wartość. Program do cieniowania pikseli, może być ustawione bezpośrednio na null lub wartość null, wartość mogą wystąpić z powodu argumentu, który został przekazany do funkcji lub inny stan. Jeśli go nie ustawiono bezpośrednio, może być Znajdź źródło wartość null, gdzieś w górę stosu wywołań. W tym scenariuszu użytkownik stwierdzi, że program do cieniowania pikseli jest bezpośrednio do ustawiania `nullptr` w pierwszą funkcję, która nosi nazwę `CubeRenderer::Render`:

    ![Kod, który nie zainicjowania programu do cieniowania pikseli](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   > Jeśli po prostu, sprawdzając stos wywołań, nie można zlokalizować źródła wartość null, zaleca się Ustaw warunkowego punktu przerwania na `PSSetShader` wywołań w taki sposób, że wykonywanie programu przerwanie wykonywania przy programu do cieniowania pikseli zostanie ustawiona na wartość null. Następnie ponownie uruchom aplikację w trybie debugowania i użyj tradycyjne techniki debugowania, aby zlokalizować źródła wartości null.

   Aby rozwiązać ten problem, należy przypisać program do cieniowania pikseli poprawne za pomocą pierwszego parametru `ID3D11DeviceContext::PSSetShader` wywołania interfejsu API.

   ![Poprawiony C&#43; &#43; kod źródłowy](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Po rozwiązaniu kod można skompilować go ponownie i uruchomić aplikację ponownie, aby sprawdzić, czy został rozwiązany problem renderowania:

   ![Obiekt jest teraz wyświetlany](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")