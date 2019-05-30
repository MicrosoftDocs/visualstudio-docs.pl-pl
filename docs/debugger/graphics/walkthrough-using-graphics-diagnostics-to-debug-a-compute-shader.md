---
title: Debugowanie cieniowania obliczenia, używanie graphics diagnostics
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19ae8472aaafbad1a04485ff2e3a2637f345bc00
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66262869"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Przewodnik: używanie diagnostyki grafiki do debugowania cieniowania obliczenia
W tym instruktażu przedstawiono sposób korzystania z narzędzi Visual Studio diagnostyki grafiki do zbadania cieniowania obliczenia, które generuje nieprawidłowe wyniki.

 Ten instruktaż ilustruje następujące zadania:

- Za pomocą **Lista zdarzeń graficznych** do lokalizowania potencjalnych źródeł problemu.

- Za pomocą **stos wywołań zdarzenia grafiki** do określenia, które cieniowanie obliczenia jest wykonywane przez DirectCompute `Dispatch` zdarzeń.

- Za pomocą **etapy potoku grafiki** okna i debugera HLSL można badać cieniowanie obliczenia będące źródłem problemu.

## <a name="scenario"></a>Scenariusz
 W tym scenariuszu zaprojektowałeś symulację dynamiki płynów, której używa DirectCompute do wykonywania najintensywniejszej obliczeniowo części aktualizacji symulacji. Po uruchomieniu aplikacji renderowanie zestawu danych i interfejs użytkownika jest poprawna, ale Symulacja nie zachowuje się zgodnie z oczekiwaniami. Przy użyciu programu Graphics Diagnostics można przechwytywać problemy do dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda to w aplikacji:

 ![Symulowane dynamiki zachowuje się nieprawidłowo. ](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")

 Aby uzyskać informacje o sposobie przechwytywania problemów z grafiką w dzienniku grafiki, zobacz [Capturing Graphics Information](capturing-graphics-information.md).

## <a name="investigation"></a>Badanie
 Narzędzia Graphics Diagnostics do załadowania pliku dziennika grafiki, aby skontrolować przechwycone ramki.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki

1. W programie Visual Studio Załaduj dziennik grafiki zawierający ramkę, która wykazuje niewłaściwe wyniki symulacji. Nowa karta Diagnostyka grafiki pojawia się w programie Visual Studio. W górnej części na tej karcie jest dane wyjściowe docelowy renderowania zaznaczonej klatki. W dolnej części jest **lista ramek**, która Wyświetla miniaturę każdej uchwyconej klatki.

2. W **lista ramek**, zaznacz klatkę, która pokazuje zachowanie nieprawidłowe. Mimo że ten błąd pojawia się w kodzie symulacji, a nie kod renderowania, nadal trzeba wybrać ramkę, ponieważ zdarzenia DirectCompute są przechwytywane na zasadzie klatka po klatce, wraz z zdarzeniami interfejsu Direct3D. W tym scenariuszu dziennika grafiki w karcie wygląda następująco:

    ![Dokument dziennika w grafiki w programie Visual Studio. ](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")

   Po zaznaczeniu klatki, która demonstruje problem, można użyć **Lista zdarzeń graficznych** do zdiagnozowania go. **Lista zdarzeń graficznych** zawiera zdarzenia dla każdego directcompute i wywołania interfejsu API Direct3D, która została wprowadzona podczas aktywnej ramki — na przykład wywołania interfejsu API w celu uruchomienia obliczeń w procesorze GPU albo wyrenderowania zestawu danych lub interfejsu użytkownika. W tym przypadku jesteśmy zainteresowani `Dispatch` zdarzenia, które reprezentuje części symulacji, korzystających z procesora GPU.

#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Aby znaleźć zdarzenia wysyłki dla aktualizacji symulacji

1. Na **Graphics Diagnostics** narzędzi, wybierz **listy zdarzeń** otworzyć **Lista zdarzeń graficznych** okna.

2. Sprawdzanie **Lista zdarzeń graficznych** dla zdarzenia remis, które renderuje zestaw danych. Aby to ułatwić, wprowadź `Draw` w **wyszukiwania** polu w prawym górnym rogu **Lista zdarzeń graficznych** okna. Filtruje listę, tak aby zawiera tylko zdarzenia, które mają "Draw" w tytułach. W tym scenariuszu użytkownik stwierdzi, że te zdarzenia remisu wystąpił:

    ![Lista zdarzeń &#40;EL&#41; przedstawia zdarzenia remisu. ](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")

3. Przenieś przez każde zdarzenie remisu podczas oglądania obiektu docelowego renderowania w karcie graficznej dziennika dokumentu.

4. Zatrzymaj, gdy obiekt docelowy renderowania po raz pierwszy wyświetli wyrenderowany zestaw danych. W tym scenariuszu zestaw danych jest renderowany w pierwszym zdarzeniu remisu. Jest wyświetlany błąd w symulacji:

    ![Rysuj to zdarzenie renderuje zestaw danych symulacji. ](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")

5. Teraz zbadaj **Lista zdarzeń graficznych** dla `Dispatch` zdarzenia, które aktualizuje symulację. Ponieważ istnieje duże prawdopodobieństwo, że Symulacja zostanie zaktualizowana, zanim zostanie renderowana, użytkownik może skupić się najpierw na `Dispatch` wydarzenia, występujących przed zdarzeniem rysowania, które renderuje wyniki. Aby to ułatwić, zmodyfikuj **wyszukiwania** pole, aby odczytać `Draw;Dispatch;CSSetShader(`. Filtruje listę, tak aby zawierała także `Dispatch` i `CSSetShader` zdarzeń oprócz zdarzeń rysowania. W tym scenariuszu użytkownik stwierdza, że kilka `Dispatch` zdarzeń wystąpiło przed zdarzeniem remisu:

    ![Pokazuje EL rysowania, wysyłania i CSSetShader zdarzenia](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")

   Teraz, gdy wiesz, które kilka z potencjalnie wielu `Dispatch` zdarzeń może odnieść się do problemu, można zbadać je bardziej szczegółowo.

#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Aby określić, które wywołanie wysyłki cieniowanie obliczenia wykonuje

1. Na **Graphics Diagnostics** narzędzi, wybierz **stos wywołań zdarzenia** otworzyć **stos wywołań zdarzenia grafiki** okna.

2. Począwszy od zdarzenia rysowania, które renderuje wyniki symulacji, przesunąć się do tyłu przez każde poprzednie `CSSetShader` zdarzeń. Następnie w **stos wywołań zdarzenia grafiki** oknie Wybierz pierwszą funkcję, aby przejść do witryny wywołania. W witrynie wywołania można użyć pierwszy parametr [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) wywołania funkcji do określenia, które cieniowanie obliczenia jest wykonywane przez następne `Dispatch` zdarzeń.

   W tym scenariuszu istnieją trzy pary `CSSetShader` i `Dispatch` zdarzenia w każdej ramce. Licząc od tyłu, trzeci reprezentuje parę integracji krok (gdzie cząstek płynu faktycznie się poruszyły), Druga para reprezentuje kroku obliczenia siły (gdzie siły, które wpływają na wszystkie cząstki są obliczane), a pierwsza Krok obliczania gęstości.

#### <a name="to-debug-the-compute-shader"></a>Aby debugować cieniowanie obliczenia

1. Na **Graphics Diagnostics** narzędzi, wybierz **etapy potoku** otworzyć **etapy potoku grafiki** okna.

2. Wybierz trzecie `Dispatch` zdarzeń (jedna bezpośrednio poprzedzające zdarzenie draw) a następnie w **etapy potoku grafiki** okna, w obszarze **obliczeniowy program do cieniowania** przejściowe, wybierz  **Rozpocznij debugowanie**.

    ![Wybierając trzecie Zdarzenie wysyłania EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")

    Debuger HLSL zostanie uruchomiony dla programu do cieniowania, który wykonuje krok integracji.

3. Sprawdź kodzie źródłowym cieniowania obliczenia kroku integracji do wyszukania źródła błędu. Korzystając z programu Graphics Diagnostics do debugowania kodu cieniowania obliczenia HLSL, można przejść przez kod i użyć innych znanych narzędzi debugowania, takich jak okna czujki. W tym scenariuszu należy określić, że prawdopodobnie w wyniku błędu w cieniowania obliczenia, które wykonuje krok integracji.

    ![Debugowanie cieniowania obliczenia IntegrateCS. ](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")

4. Aby zatrzymać debugowanie cieniowania obliczenia na **debugowania** narzędzi, wybierz **Zatrzymaj debugowanie** (klawiatury: Shift+F5).

5. Następnie wybierz drugą `Dispatch` zdarzeń i rozpoczęcia debugowania cieniowania obliczenia, podobnie jak w poprzednim kroku.

    ![Wybierając drugie zdarzenie wysyłania EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")

    Debuger HLSL zostanie uruchomiony dla programu do cieniowania, który oblicza siły działające na wszystkie cząstki płynu.

6. Poszukaj kroku obliczenia siły w kodzie źródłowym cieniowania obliczeń. W tym scenariuszu należy określić, czy źródło błędu jest tutaj.

    ![Debugowanie ForceCS&#95;prosty obliczeniowy program do cieniowania. ](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")

   Po określeniu lokalizacji błędu, można zatrzymać debugowanie i zmodyfikować kod źródłowy cieniowania obliczenia, aby poprawnie obliczyć odległość między wchodzącymi w interakcje cząstkami. W tym scenariuszu po prostu Zmień wiersz `float2 diff = N_position + P_position;` do `float2 diff = N_position - P_position;`:

   ![Poprawiony obliczeń&#45;kodu programu do cieniowania. ](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")

   W tym scenariuszu ponieważ cieniowania obliczenia są kompilowane w czasie wykonywania można tylko ponownie uruchomić aplikację po wprowadzeniu zmian, aby obejrzeć ich wpływ na symulację. Nie trzeba ponownie kompilować aplikacji. Po uruchomieniu aplikacji, można wykryć, że teraz Symulacja zachowuje się poprawnie.

   ![Symulowane dynamiki zachowuje się poprawnie. ](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")