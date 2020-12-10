---
title: Brakujące obiekty ze względu na nieprawidłowo skonfigurowany potok
description: Postępuj zgodnie z badaniem, w którym znajduje się niepoprawnie skonfigurowany potok. Pokazuje listę zdarzeń użycia grafiki, etapy potoku grafiki i stos wywołań zdarzeń grafiki.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ed8ac02d-b38f-4055-82fb-67757c2ccbb9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e099d94479183e795a2ad3c8fc8db03fa969111c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995021"
---
# <a name="walkthrough-missing-objects-due-to-misconfigured-pipeline"></a>Przewodnik: brak obiektów spowodowany błędnie skonfigurowanym potokiem
W tym instruktażu pokazano, jak za pomocą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] narzędzi Diagnostyka grafiki sprawdzać obiekt, który nie występuje ze względu na nieustawioną cieniowanie pikseli.

 Ten Instruktaż ilustruje następujące zadania:

- Korzystając z **listy zdarzeń grafiki** , można zlokalizować potencjalne źródła problemu.

- Korzystając z okna **etapy potoku grafiki** , można przeanalizować efekt `DrawIndexed` wywołania interfejsu API Direct3D.

- Sprawdzanie kontekstu urządzenia, aby upewnić się, że nie ustawiono etapu programu do cieniowania.

- Za pomocą okna **etapy potoku grafiki** wraz ze **stosem wywołań zdarzeń grafiki** , aby znaleźć Źródło cieniowania pikseli, które nie zostały wycofane.

## <a name="scenario"></a>Scenariusz
 Gdy w aplikacji 3-D brakuje obiektu, to czasami, ponieważ jeden z etapów modułu cieniującego nie jest ustawiony przed renderowaniem obiektu. W aplikacjach, które mają proste potrzeby renderowania, źródło tego błędu zwykle znajduje się w dowolnym miejscu w stosie wywołań wywołania rysowania obiektu. Jednak w przypadku optymalizacji niektóre aplikacje wsadowe przetwarzają obiekty, które mają wspólne programy, tekstury lub inne dane, aby zminimalizować obciążenie zmiany stanu. W tych aplikacjach Źródło błędu może być przykryty w systemie wsadowym zamiast znajdować się w stosie wywołań wywołania rysowania. W scenariuszu w tym instruktażu przedstawiono aplikację, która ma proste potrzeby renderowania, a więc Źródło błędu można znaleźć w stosie wywołań.

 W tym scenariuszu, gdy aplikacja jest uruchamiana w celu przetestowania, tło jest renderowane zgodnie z oczekiwaniami, ale jeden z obiektów nie jest wyświetlany. Korzystając z Diagnostyka grafiki, można przechwytywać ten problem do dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda następująco w aplikacji:

 ![Nie można zobaczyć obiektu](media/gfx_diag_demo_misconfigured_pipeline_problem.png "gfx_diag_demo_misconfigured_pipeline_problem")

## <a name="investigation"></a>Badanie
 Za pomocą narzędzi Diagnostyka grafiki, można załadować dokument dziennika grafiki, aby sprawdzić ramki, które zostały przechwycone podczas testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby przeanalizować ramkę w dzienniku grafiki

1. W programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Załaduj dokument dziennika grafiki zawierający ramkę, która wykazuje brakujący obiekt. Zostanie wyświetlona nowa karta graficzny dziennik grafiki w temacie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . W górnej części tej karty są docelowe wyniki renderowania dla wybranej ramki. W dolnej części jest **listą ramek**, która wyświetla każdą przechwyconą ramkę jako obraz miniatury.

2. Na **liście ramka** Wybierz ramkę, która pokazuje, że obiekt nie jest wyświetlany. Obiekt docelowy renderowania zostanie zaktualizowany w celu odzwierciedlenia wybranej ramki. W tym scenariuszu karta Dziennik grafiki wygląda następująco:

    ![Dokument dziennika grafiki w programie Visual Studio](media/gfx_diag_demo_misconfigured_pipeline_step_1.png "gfx_diag_demo_misconfigured_pipeline_step_1")

   Po wybraniu ramki, która demonstruje ten problem, można rozpocząć diagnozowanie jej przy użyciu **listy zdarzeń grafiki**. **Lista zdarzeń grafiki** zawiera wszystkie wywołania interfejsu API Direct3D, które zostały wykonane w celu renderowania aktywnej ramki — na przykład w celu skonfigurowania stanu urządzenia, tworzenia i aktualizowania buforów oraz do rysowania obiektów, które pojawiają się w ramce. Wiele rodzajów wywołań — na przykład, rysowania, wysyłania, kopiowania lub czyszczenia połączeń — są interesujące, ponieważ często są (ale nie zawsze) odpowiednie zmiany w miejscu docelowym renderowania, gdy aplikacja działa zgodnie z oczekiwaniami. Wywołania rysowania są szczególnie interesujące, ponieważ każda z nich reprezentuje geometrię renderowaną przez aplikację.

   Ponieważ wiesz, że obiekt docelowy renderowania nie zawiera brakującego obiektu, ale również że nie występują inne błędy, możesz użyć **listy zdarzeń grafiki** wraz z narzędziem **etapy potoku grafiki** , aby określić, które wywołanie rysowania odnosi się do geometrii brakującego obiektu. Okno **etapy potoku grafiki** pokazuje geometrię, która została wysłana do każdego wywołania rysowania, niezależnie od jej wpływu na obiekt docelowy renderowania. Podczas poruszania się po wywołaniach rysowania etapy potoku są aktualizowane w celu wyświetlenia geometrii, która jest skojarzona z każdym wywołaniem, gdy jest ona przenoszona przez każdy włączony etap, a docelowe dane wyjściowe renderowania są aktualizowane w celu wyświetlenia stanu obiektu docelowego renderowania po zakończeniu wywołania.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć połączenie rysowania dla brakującej geometrii

1. Otwórz okno **Lista zdarzeń grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **Lista zdarzeń**.

2. Otwórz okno **etapy potoku grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **etapy potoku**.

3. Podczas przechodzenia przez poszczególne wywołania rysowania w oknie **Lista zdarzeń graficznych** Obejrzyj okno **etapy potoku grafiki** dla brakującego obiektu. Aby to ułatwić, wprowadź ciąg "Draw" w polu **wyszukiwania** w prawym górnym rogu okna **Lista zdarzeń grafiki** . Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Draw" w swoich tytułach.

    W oknie **etapy potoku grafiki** na etapie **asemblera wejściowego** jest wyświetlana geometria obiektu, zanim zostanie on przekształcony, a etap **cieniowania wierzchołka** wyświetli ten sam obiekt po jego przeprowadzeniu. W tym scenariuszu należy zauważyć, że okno **etapy potoku grafiki** pokazuje etapy **asemblera** i programu do cieniowania  **wierzchołków** , ale nie etap **cieniowania pikseli** dla jednego z wywołań rysowania.

   > [!NOTE]
   > W przypadku innych etapów potoku — na przykład w przypadku programów do cieniowania kadłuba, programu do cieniowania domen lub cieniowania geometrii — przetwarzanie obiektu może być przyczyną problemu. Zazwyczaj problem jest związany z najwcześniejszym etapem, w którym wynik nie jest wyświetlany lub jest wyświetlany w nieoczekiwany sposób.

4. Zatrzymaj, gdy docierasz do wywołania rysowania, które odnosi się do brakującego obiektu. W tym scenariuszu okno **etapy potoku grafiki** wskazuje, że geometria została wystawiona dla procesora GPU (wskazywanej przez obecność etapu **asemblera wejściowego** ) i przekształcone (wskazywane przez etap **cieniowania wierzchołka** ), ale nie jest wyświetlana w miejscu docelowym renderowania, ponieważ nie wydaje się, że jest aktywny program cieniowania pikseli (wskazywany przez brak etapu **cieniowania pikseli** ). W tym scenariuszu można nawet zobaczyć Silhouette brakującego obiektu na etapie **scalania danych wyjściowych** :

    ![Zdarzenie DrawIndexed i jego wpływ na potok](media/gfx_diag_demo_misconfigured_pipeline_step_2.png "gfx_diag_demo_misconfigured_pipeline_step_2")

   Po upewnieniu się, że aplikacja wygenerowała wywołanie rysowania dla brakującego obiektu i odkryj, że etap programu do cieniowania pikseli był nieaktywny, można sprawdzić stan urządzenia, aby potwierdzić swoje ustalenia. Możesz użyć **tabeli obiektów Graphics** do sprawdzenia kontekstu urządzenia i innych danych obiektów Direct3D.

#### <a name="to-examine-device-context"></a>Aby przejrzeć kontekst urządzenia

1. Otwórz **kontekst urządzenia d3d11**. W oknie **etapy potoku grafiki** wybierz łącze **ID3D11DeviceContext** , które jest częścią `DrawIndexed` wywołania, które jest wyświetlane w górnej części okna.

2. Sprawdź stan urządzenia, który jest wyświetlany na karcie **kontekst urządzenia d3d11** , aby upewnić się, że w trakcie wywołania rysowania nie było aktywnego programu do cieniowania pikseli. W tym scenariuszu **Ogólne informacje modułu cieniującego**— wyświetlane pod **stanem programu do cieniowania pikseli**— wskazuje, że cieniowanie ma **wartość null**:

    ![Kontekst urządzenia D3D 11 przedstawia stan programu do cieniowania pikseli](media/gfx_diag_demo_misconfigured_pipeline_step_4.png "gfx_diag_demo_misconfigured_pipeline_step_4")

   Po upewnieniu się, że program do cieniowania pikseli został ustawiony na wartość null przez aplikację, następnym krokiem jest znalezienie lokalizacji w kodzie źródłowym aplikacji, w której jest ustawiony moduł cieniujący. Możesz użyć **listy zdarzeń grafiki** wraz ze **stosem wywołań zdarzeń grafiki** , aby znaleźć tę lokalizację.

#### <a name="to-find-where-the-pixel-shader-is-set-in-your-apps-source-code"></a>Aby dowiedzieć się, gdzie jest ustawiony program cieniowanie pikseli w kodzie źródłowym aplikacji

1. Znajdź `PSSetShader` wywołanie odnoszące się do brakującego obiektu. W oknie **Lista zdarzeń grafiki** wprowadź "Draw; PSSetShader "w polu **wyszukiwania** w prawym górnym rogu okna **Lista zdarzeń grafiki** . Filtruje listę, tak aby zawierała tylko zdarzenia "PSSetShader" i zdarzenia, które mają "Draw" w swoich tytułach. Wybierz pierwsze `PSSetShader` wywołanie, które pojawia się przed wywołaniem rysowania brakującego obiektu.

   > [!NOTE]
   > `PSSetShader` nie będą wyświetlane w oknie **Lista zdarzeń grafiki** , jeśli nie zostało ustawione w tej ramce. Zwykle zdarza się to tylko wtedy, gdy tylko jeden program do cieniowania pikseli jest używany dla wszystkich obiektów lub jeśli `PSSetShader` Wywołanie zostało przypadkowo pominięte w tej ramce. W obu przypadkach zalecamy przeszukanie kodu źródłowego aplikacji dla `PSSetShader` wywołań i użycie tradycyjnych technik debugowania do sprawdzenia zachowania tych wywołań.

2. Otwórz okno **stos wywołań zdarzeń grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **grafika stos wywołań zdarzeń**.

3. Użyj stosu wywołań, aby zlokalizować `PSSetShader` wywołanie w kodzie źródłowym aplikacji. W oknie **stos wywołań zdarzeń grafiki** wybierz pierwsze wywołanie i przejrzyj wartość, do której jest ustawiany program do cieniowania pikseli. Program do cieniowania pikseli może być ustawiony bezpośrednio na wartość null lub wartość null może wystąpić z powodu argumentu, który został przekazano do funkcji lub innego stanu. Jeśli nie jest ona ustawiona bezpośrednio, można znaleźć źródło wartości null w ramach stosu wywołań. W tym scenariuszu wykryjesz, że program do cieniowania pikseli jest ustawiany bezpośrednio `nullptr` w funkcji najwyższego poziomu, która nosi nazwę `CubeRenderer::Render` :

    ![Kod, który nie inicjuje cieniowania pikseli](media/gfx_diag_demo_misconfigured_pipeline_step_5.png "gfx_diag_demo_misconfigured_pipeline_step_5")

   > [!NOTE]
   > Jeśli nie możesz znaleźć źródła wartości null tylko poprzez zbadanie stosu wywołań, zalecamy ustawienie warunkowego punktu przerwania dla `PSSetShader` wywołania, na przykład wykonanie przerwy w programie, gdy cieniowanie pikseli zostanie ustawione na wartość null. Następnie uruchom ponownie aplikację w trybie debugowania i użyj tradycyjnych technik debugowania, aby zlokalizować źródło wartości null.

   Aby rozwiązać ten problem, przypisz poprawny program do cieniowania pikseli przy użyciu pierwszego parametru `ID3D11DeviceContext::PSSetShader` wywołania interfejsu API.

   ![Poprawiony kod źródłowy C&#43;&#43; ](media/gfx_diag_demo_misconfigured_pipeline_step_6.png "gfx_diag_demo_misconfigured_pipeline_step_6")

   Po naprawieniu kodu możesz go ponownie skompilować i uruchomić aplikację, aby sprawdzić, czy problem z renderowaniem został rozwiązany:

   ![Obiekt jest teraz wyświetlany](media/gfx_diag_demo_misconfigured_pipeline_resolution.jpg "gfx_diag_demo_misconfigured_pipeline_resolution")