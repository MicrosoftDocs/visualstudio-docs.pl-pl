---
title: 'Przewodnik: używanie Diagnostyka grafiki do debugowania cieniowania obliczeń | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db33a55c5ced7c1bbbf4b238185beac43ac290f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186934"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Przewodnik: używanie diagnostyki grafiki do debugowania cieniowania obliczenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak za pomocą narzędzi Diagnostyka grafiki programu Visual Studio zbadać cieniowanie obliczeniowe, które generuje nieprawidłowe wyniki.  
  
 Ten Instruktaż ilustruje następujące zadania:  
  
- Korzystając z **listy zdarzeń grafiki** , można zlokalizować potencjalne źródła problemu.  
  
- Korzystając ze **stosu wywołań zdarzeń grafiki** , można określić, które cieniowanie obliczeń jest wykonywane przez `Dispatch` zdarzenie DirectCompute.  
  
- Za pomocą okna **etapy potoku grafiki** i debugera HLSL, aby przejrzeć cieniowanie obliczeń, które jest źródłem problemu.  
  
## <a name="scenario"></a>Scenariusz  
 W tym scenariuszu nastąpiło zapisanie symulacji płynnej klasy, która używa DirectCompute do wykonywania większości operacji związanych z intensywnymi obliczeniami w ramach aktualizacji symulacji. Gdy aplikacja jest uruchamiana, renderowanie zestawu danych i interfejsu użytkownika wyglądają prawidłowo, ale symulacja nie zachowuje się zgodnie z oczekiwaniami. Za pomocą Diagnostyka grafiki można przechwytywać ten problem do dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda następująco w aplikacji:  
  
 ![Symulowany płyn zachowuje się nieprawidłowo.](../debugger/media/gfx-diag-demo-compute-shader-fluid-problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Aby uzyskać informacje o sposobach przechwytywania problemów graficznych w dzienniku grafiki, zobacz [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Badanie  
 Możesz użyć narzędzi Diagnostyka grafiki do załadowania pliku dziennika grafiki, aby można było sprawdzić przechwycone ramki.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby przeanalizować ramkę w dzienniku grafiki  
  
1. W programie Visual Studio załaduj dziennik grafiki zawierający ramkę, która wykazuje nieprawidłowe wyniki symulacji. Zostanie wyświetlona nowa karta Diagnostyka grafiki w programie Visual Studio. W górnej części tej karty są docelowe wyniki renderowania dla wybranej ramki. W dolnej części jest **listą ramek**, która wyświetla miniaturę każdej przechwyconej ramki.  
  
2. Na **liście ramka**Wybierz ramkę, która pokazuje nieprawidłowe zachowanie symulacji. Mimo że błąd pojawia się w kodzie symulacji, a nie w kodzie renderowania, nadal trzeba wybrać ramkę, ponieważ zdarzenia DirectCompute są przechwytywane w oparciu o ramy między ramkami oraz zdarzenia Direct3D. W tym scenariuszu karta Dziennik grafiki wygląda następująco:  
  
    ![Dokument dziennika grafiki w programie Visual Studio.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
   Po wybraniu ramki, która demonstruje ten problem, można użyć **listy zdarzeń grafiki** do zdiagnozowania. **Lista zdarzeń grafiki** zawiera zdarzenie dla każdego wywołania DirectCompute oraz wywołanie interfejsu API Direct3D, które zostało wykonane w aktywnej ramce — na przykład wywołania interfejsu API do uruchamiania obliczeń na procesorze GPU lub do renderowania zestawu danych lub interfejsu użytkownika. W tym przypadku interesuje `Dispatch` zdarzenia reprezentujące część symulacji, która jest uruchamiana na procesorze GPU.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Aby znaleźć zdarzenie wysyłania dla aktualizacji symulacji  
  
1. Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **Lista zdarzeń** , aby otworzyć okno **Lista zdarzeń grafiki** .  
  
2. Sprawdź **listę zdarzeń grafiki** dla zdarzenia rysowania, które renderuje zestaw danych. Aby to ułatwić, wprowadź `Draw` w polu **wyszukiwania** w prawym górnym rogu okna **Lista zdarzeń grafiki** . Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Draw" w swoich tytułach. W tym scenariuszu wykryjesz, że wystąpiły te zdarzenia rysowania:  
  
    ![Lista zdarzeń &#40;EL&#41; pokazuje zdarzenia rysowania.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3. Poruszaj się po każdym zdarzeniu rysowania podczas oglądania elementu docelowego renderowania na karcie dokument dziennika grafiki.  
  
4. Zatrzymaj, gdy obiekt docelowy renderowania najpierw wyświetla renderowany zestaw danych. W tym scenariuszu zestaw danych jest renderowany w pierwszym zdarzeniu rysowania. Zostanie wyświetlony błąd symulacji:  
  
    ![To zdarzenie rysowania renderuje zestaw danych symulacji.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5. Teraz sprawdź **listę zdarzeń grafiki** dla `Dispatch` zdarzenia, które aktualizuje symulację. Ponieważ jest to możliwe, że symulacja została zaktualizowana przed renderowaniem, można najpierw skoncentrować się na `Dispatch` zdarzeniach, które wystąpiły przed zdarzeniem rysowania, które renderuje wyniki. Aby to ułatwić, zmodyfikuj pole **wyszukiwania** , aby je odczytać `Draw;Dispatch;CSSetShader(` . Filtruje listę, tak aby zawierała `Dispatch` i `CSSetShader` zdarzenia oprócz zdarzeń rysowania. W tym scenariuszu wykryjesz, że kilka `Dispatch` zdarzeń wystąpiło przed zdarzeniem rysowania:  
  
    ![EL przedstawia zdarzenia rysowania, wysyłania i CSSetShader](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
   Teraz, gdy wiesz, które niektóre potencjalnie wiele `Dispatch` zdarzeń mogą odpowiadać temu problemowi, możesz sprawdzić je bardziej szczegółowo.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Aby określić, które cieniowanie obliczeń wykonuje wywołanie wysyłania  
  
1. Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **stos wywołań zdarzeń** , aby otworzyć okno **stos wywołań zdarzeń grafiki** .  
  
2. Rozpoczynając od zdarzenia rysowania, które renderuje wyniki symulacji, Przenieś do tyłu przez każde poprzednie `CSSetShader` zdarzenie. Następnie w oknie **stos wywołań zdarzeń grafiki** wybierz funkcję najwyższego poziomu, aby przejść do witryny wywołania. W miejscu wywołania można użyć pierwszego parametru wywołania funkcji [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) , aby określić, które cieniowanie obliczeń jest wykonywane przez następne `Dispatch` zdarzenie.  
  
   W tym scenariuszu istnieją trzy pary `CSSetShader` i `Dispatch` zdarzenia w każdej ramce. Trzecia para reprezentuje krok integracji (gdzie cząstki płynu są faktycznie przenoszone), druga para reprezentuje krok obliczania wymuszonego (w którym są obliczane siły, które mają wpływ na każdą cząstkę), a pierwsza para reprezentuje etap obliczania gęstości.  
  
#### <a name="to-debug-the-compute-shader"></a>Aby debugować cieniowanie obliczeń  
  
1. Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **etapy potoku** , aby otworzyć okno **etapy potoku grafiki** .  
  
2. Wybierz trzecie `Dispatch` zdarzenie (takie, które bezpośrednio poprzedza zdarzenie rysowania), a następnie w oknie **etapy potoku grafiki** w obszarze etap **cieniowania obliczeń** wybierz **Rozpocznij debugowanie**.  
  
    ![Wybór trzeciego zdarzenia wysyłania w EL.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
    Debuger HLSL jest uruchamiany w module cieniującego, który wykonuje krok integracji.  
  
3. Zapoznaj się z kodem źródłowym modułu cieniującego obliczeń dla kroku integracji, aby wyszukać Źródło błędu. Gdy używasz Diagnostyka grafiki do debugowania kodu programu do cieniowania HLSL obliczeń, możesz przejść przez kod i użyć innych znanych narzędzi do debugowania, takich jak okna czujki. W tym scenariuszu należy określić, że nie wydaje się, że jest to błąd w programie cieniowania obliczeń, który wykonuje krok integracji.  
  
    ![Debugowanie cieniowania obliczeń IntegrateCS.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4. Aby zatrzymać debugowanie cieniowania obliczeń, na pasku narzędzi **debugowania** wybierz polecenie **Zatrzymaj debugowanie** (klawiatura: Shift + F5).  
  
5. Następnie wybierz drugie `Dispatch` zdarzenie i Rozpocznij debugowanie cieniowania obliczeń tak samo jak w poprzednim kroku.  
  
    ![Wybór drugiego zdarzenia wysyłania w EL.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
    Debuger HLSL jest uruchamiany w module cieniującego, który oblicza siły, które działają na każdej cząstki płynów.  
  
6. Zapoznaj się z kodem źródłowym programu do cieniowania obliczeń dla kroku wymuszania obliczania. W tym scenariuszu należy określić, że Źródło błędu jest tutaj.  
  
    ![Debugowanie ForceCS&#95;proste cieniowanie obliczeń.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
   Po ustaleniu lokalizacji tego błędu można zatrzymać debugowanie i zmodyfikować kod źródłowy modułu cieniującego programu COMPUTE, aby poprawnie obliczyć odległość między tymi cząsteczkami. W tym scenariuszu wystarczy zmienić wiersz `float2 diff = N_position + P_position;` na `float2 diff = N_position - P_position;` :  
  
   ![Poprawiony kod programu do cieniowania&#45;obliczeń.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
   W tym scenariuszu, ponieważ cieniowanie obliczeniowe są kompilowane w czasie wykonywania, można po prostu ponownie uruchomić aplikację po wprowadzeniu zmian, aby obserwować ich wpływ na symulację. Nie trzeba ponownie kompilować aplikacji. Po uruchomieniu aplikacji można stwierdzić, że symulacja działa poprawnie.  
  
   ![Symulowany płyn zachowuje się prawidłowo.](../debugger/media/gfx-diag-demo-compute-shader-fluid-resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")
