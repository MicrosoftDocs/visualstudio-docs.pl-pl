---
title: 'Przewodnik: brak obiektów ze względu na cieniowanie wierzchołków | Microsoft Docs'
description: Postępuj zgodnie z badaniem, w którym znajduje się błąd cieniowania wierzchołka. Pokazuje listę zdarzeń użycia grafiki, etapy potoku grafiki, debuger HLSL oraz stos wywołań zdarzeń grafiki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7e4c01a990ce4d3fff6769ba016c168b190687f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995001"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>Przewodnik: brak obiektów spowodowany cieniowaniem wierzchołków
W tym instruktażu pokazano, jak za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędzi Diagnostyka grafiki sprawdzać nieobecny obiekt z powodu błędu występującego podczas etapu cieniowania wierzchołka.

 Ten Instruktaż ilustruje następujące zadania:

- Korzystając z **listy zdarzeń grafiki** , można zlokalizować potencjalne źródła problemu.

- Korzystając z okna **etapy potoku grafiki** , można sprawdzić efekt `DrawIndexed` wywołań interfejsu API Direct3D.

- Sprawdzanie cieniowania wierzchołków przy użyciu **debugera HLSL** .

- Użycie **stosu wywołań zdarzeń grafiki** , aby ułatwić znalezienie źródła nieprawidłowej stałej HLSL.

## <a name="scenario"></a>Scenariusz
 Jednym z typowych przyczyn braku obiektu w aplikacji 3-D występuje, gdy program do cieniowania wierzchołków przeniesie wierzchołki obiektu w nieprawidłowy lub nieoczekiwany sposób — na przykład obiekt może być skalowany do bardzo małego rozmiaru lub przekształcony w taki sposób, aby był wyświetlany za kamerą, a nie przed nim.

 W tym scenariuszu, gdy aplikacja jest uruchamiana w celu jej przetestowania, tło jest renderowane zgodnie z oczekiwaniami, ale jeden z obiektów nie jest wyświetlany. Korzystając z Diagnostyka grafiki, można przechwytywać ten problem do dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda następująco w aplikacji:

 ![Nie można zobaczyć obiektu.](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>Badanie
 Za pomocą narzędzi Diagnostyka grafiki, można załadować plik dziennika grafiki, aby sprawdzić ramki, które zostały przechwycone podczas testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby przeanalizować ramkę w dzienniku grafiki

1. W programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Załaduj dziennik grafiki zawierający ramkę, która wykazuje brakujący obiekt. Zostanie wyświetlona nowa karta graficzny dziennik grafiki w temacie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . W górnej części tej karty są docelowe wyniki renderowania dla wybranej ramki. W dolnej części jest **listą ramek**, która wyświetla każdą przechwyconą ramkę jako obraz miniatury.

2. Na **liście ramka** Wybierz ramkę, która pokazuje, że obiekt nie jest wyświetlany. Obiekt docelowy renderowania zostanie zaktualizowany w celu odzwierciedlenia wybranej ramki. W tym scenariuszu karta Dziennik grafiki wygląda następująco:

    ![Dokument dziennika grafiki w programie Visual Studio](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   Po wybraniu ramki, która demonstruje ten problem, można rozpocząć diagnozowanie jej przy użyciu **listy zdarzeń grafiki**. **Lista zdarzeń grafiki** zawiera wszystkie wywołania interfejsu API Direct3D, które zostały wykonane w celu renderowania aktywnej ramki, na przykład wywołania interfejsu API w celu skonfigurowania stanu urządzenia, tworzenia i aktualizowania buforów oraz do rysowania obiektów, które pojawiają się w ramce. Wiele rodzajów wywołań jest interesujących, ponieważ występuje często (ale nie zawsze) odpowiednia zmiana w miejscu docelowym renderowania, gdy aplikacja działa zgodnie z oczekiwaniami, na przykład rysowanie, wysyłanie, kopiowanie lub czyszczenie wywołań. Wywołania rysowania są szczególnie interesujące, ponieważ każda z nich reprezentuje geometrię renderowaną przez aplikację (wywołania wysyłania mogą również renderować geometrię).

   Ponieważ wiadomo, że brakujący obiekt nie jest rysowany do elementu docelowego renderowania (w tym przypadku), ale pozostała część sceny jest rysowana zgodnie z oczekiwaniami — można użyć **listy zdarzeń grafiki** wraz z narzędziem **etapy potoku grafiki** , aby określić, które wywołanie rysowania odnosi się do geometrii brakującego obiektu. Okno **etapy potoku grafiki** pokazuje geometrię, która została wysłana do każdego wywołania rysowania, niezależnie od jej wpływu na obiekt docelowy renderowania. Podczas poruszania się po wywołaniach rysowania etapy potoku są aktualizowane w celu wyświetlenia geometrii, która jest skojarzona z tym wywołaniem, a docelowe dane wyjściowe renderowania są aktualizowane w celu wyświetlenia stanu obiektu docelowego renderowania po zakończeniu wywołania.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć połączenie rysowania dla brakującej geometrii

1. Otwórz okno **Lista zdarzeń grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **Lista zdarzeń**.

2. Otwórz okno **etapy potoku grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **etapy potoku**.

3. Podczas przechodzenia przez poszczególne wywołania rysowania w oknie **Lista zdarzeń graficznych** Obejrzyj okno **etapy potoku grafiki** dla brakującego obiektu. Aby to ułatwić, wprowadź ciąg "Draw" w polu **wyszukiwania** w prawym górnym rogu okna **Lista zdarzeń grafiki** . Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Draw" w swoich tytułach.

    W oknie **etapy potoku grafiki** , etap **asemblera wejściowego** pokazuje geometrię obiektu przed jego przeprowadzeniem, a etap **cieniowania wierzchołków** pokazuje ten sam obiekt po jego przeprowadzeniu. W tym scenariuszu wiesz, że znaleziono brakujący obiekt, gdy zostanie on wyświetlony na etapie **asemblera wejściowego** i nic nie jest wyświetlane na etapie programu do **cieniowania wierzchołka** .

   > [!NOTE]
   > W przypadku innych etapów geometrii — na przykład do cieniowania kadłuba, programu do cieniowania domen lub etapów modułu cieniującego geometrii — przetwarzania obiektu, może to być przyczyną problemu. Zazwyczaj problem jest związany z najwcześniejszym etapem, w którym wynik nie jest wyświetlany lub jest wyświetlany w nieoczekiwany sposób.

4. Zatrzymaj, gdy docierasz do wywołania rysowania, które odnosi się do brakującego obiektu. W tym scenariuszu okno **etapy potoku grafiki** wskazuje, że geometria została wystawiona dla procesora GPU (wskazywanej przez miniaturę asemblera wejściowego), ale nie jest wyświetlana w miejscu docelowym renderowania, ponieważ coś poszło źle na etapie cieniowania wierzchołka (wskazywanym przez miniaturę programu do cieniowania wierzchołka):

    ![Zdarzenie DrawIndexed i jego wpływ na potok](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   Po upewnieniu się, że aplikacja wygenerowała wywołanie rysowania dla brakującego obiektu i odkryj, że problem występuje podczas etapu cieniowania wierzchołków, można użyć debugera HLSL do sprawdzenia cieniowania wierzchołków i dowiedzieć się, co się stało z geometrią obiektu. Debuger HLSL umożliwia badanie stanu zmiennych HLSL podczas wykonywania, przechodzenie przez kod HLSL i ustawianie punktów przerwania, aby ułatwić zdiagnozowanie problemu.

#### <a name="to-examine-the-vertex-shader"></a>Aby przejrzeć cieniowanie wierzchołków

1. Rozpocznij debugowanie etapu programu do cieniowania wierzchołków. W oknie **etapy potoku grafiki** w obszarze etapu **cieniowania wierzchołka** wybierz przycisk **Rozpocznij debugowanie** .

2. Ponieważ etap **asemblera wejściowego** wydaje się zapewnić dobre dane dla cieniowania wierzchołków, a etap **cieniowania wierzchołka** wydaje się nie generować danych wyjściowych, należy przejrzeć strukturę wyjściową programu do cieniowania wierzchołków `output` . Po przekroczeniu kodu HLSL należy przejść bliżej tego, kiedy `output` jest modyfikowany.

3. Podczas pierwszej `output` modyfikacji element członkowski `worldPos` jest zapisywana w.

    ![Wartość "Output. worldPos" jest wyświetlana w odpowiedniej postaci](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    Ponieważ jej wartość jest rozsądna, Kontynuuj przechodzenie przez kod do następnego wiersza, który modyfikuje `output` .

4. Przy następnym `output` modyfikowaniu element członkowski `pos` jest zapisywana w.

    ![Wartość "Output. pos" została wyliczona jako zero](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    Tym razem wartość `pos` elementu członkowskiego — wszystkie zera — wygląda podejrzanie. Następnie chcesz określić, jak ma `output.pos` mieć wartość wszystkich zer.

5. Należy zauważyć, że `output.pos` wartość jest pobierana z zmiennej o nazwie `temp` . W poprzednim wierszu zobaczysz, że wartość `temp` jest wynikiem mnożenia poprzedniej wartości przez stałą o nazwie `projection` . Podejrzewasz, że `temp` podejrzana wartość jest wynikiem tego mnożenia. Po umieszczeniu wskaźnika na `projection` , Zauważ, że jego wartość to również same zera.

    ![Macierz projekcji zawiera złą transformację](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    W tym scenariuszu badanie ujawnia `temp` podejrzane wartości najprawdopodobniej spowodowane przez mnożenie przez `projection` , a ponieważ `projection` jest stałą, która ma zawierać macierz projekcji, wiadomo, że nie powinna zawierać samych zer.

   Po ustaleniu, że stała HLSL `projection` — przeniesiona do programu do cieniowania przez aplikację — jest najprawdopodobniej źródłem problemu, następnym krokiem jest znalezienie lokalizacji w kodzie źródłowym aplikacji, w której został wypełniony stały bufor. Możesz użyć **stosu wywołań zdarzeń grafiki** , aby znaleźć tę lokalizację.

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>Aby dowiedzieć się, gdzie stała jest ustawiona w kodzie źródłowym aplikacji

1. Otwórz okno **stos wywołań zdarzeń grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **grafika stos wywołań zdarzeń**.

2. Przejdź w górę stosu wywołań do kodu źródłowego aplikacji. W oknie **stos wywołań zdarzeń grafiki** wybierz pierwsze wywołanie, aby sprawdzić, czy stały bufor jest wypełniany w tym miejscu. Jeśli tak nie jest, Kontynuuj stos wywołań do momentu, gdy okaże się, że jest wypełniony. W tym scenariuszu wykryjesz, że stały bufor jest wypełniany — za pomocą `UpdateSubresource` interfejsu API Direct3D — w pełni zastos wywołań w funkcji o nazwie `MarbleMaze::Render` i że jej wartość pochodzi z obiektu stałego buforu o nazwie `m_marbleConstantBufferData` :

    ![Kod, który ustawia stały bufor obiektu](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   > Jeśli jednocześnie debugujesz aplikację, możesz ustawić punkt przerwania w tej lokalizacji i zostanie on trafiony podczas renderowania następnej ramki. Następnie można przeprowadzić inspekcję elementów `m_marbleConstantBufferData` Członkowskich, aby upewnić się, że wartość `projection` elementu członkowskiego jest ustawiona na wszystkie zera po wypełnieniu stałego buforu.

   Po znalezieniu lokalizacji, w której jest wypełniany stały bufor i odkryj, że jej wartości pochodzą ze zmiennej `m_marbleConstantBufferData` , następnym krokiem jest dowiedzenie, gdzie `m_marbleConstantBufferData.projection` element członkowski jest ustawiony na wszystkie zera. Możesz użyć polecenia **Znajdź wszystkie odwołania** , aby szybko skanować kod, który zmienia wartość `m_marbleConstantBufferData.projection` .

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>Aby znaleźć miejsce, w którym element członkowski projekcji jest ustawiony w kodzie źródłowym aplikacji

1. Znajdź odwołania do `m_marbleConstantBufferData.projection` . Otwórz menu skrótów dla zmiennej `m_marbleConstantBufferData` , a następnie wybierz polecenie **Znajdź wszystkie odwołania**.

2. Aby przejść do lokalizacji wiersza w kodzie źródłowym aplikacji, w którym `projection` element członkowski został zmodyfikowany, wybierz ten wiersz w oknie **Znajdź wyniki symboli** . Ponieważ pierwszy wynik, który modyfikuje element członkowski projekcji, może nie być przyczyną problemu, może być konieczne przeanalizowanie kilku obszarów kodu źródłowego aplikacji.

   Po znalezieniu lokalizacji, w której `m_marbleConstantBufferData.projection` jest ustawiony, można sprawdzić otaczający kod źródłowy, aby określić pochodzenie nieprawidłowej wartości. W tym scenariuszu wykryjesz, że wartość `m_marbleConstantBufferData.projection` jest ustawiona na zmienną lokalną o nazwie `projection` przed zainicjowaniem jej do wartości podanej przez kod `m_camera->GetProjection(&projection);` w następnym wierszu.

   ![Projekcja marmurowa jest ustawiana przed inicjalizacją](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   Aby rozwiązać ten problem, należy przenieść wiersz kodu, który ustawia wartość `m_marbleConstantBufferData.projection` po wierszu, który inicjuje wartość zmiennej lokalnej `projection` .

   ![Poprawiony kod źródłowy C&#43;&#43; ](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   Po naprawieniu kodu możesz ponownie skompilować i uruchomić aplikację, aby poznać, że problem z renderowaniem został rozwiązany:

   ![Obiekt w teraz wyświetlany.](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")