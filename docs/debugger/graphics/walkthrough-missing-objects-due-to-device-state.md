---
title: 'Przewodnik: Brak obiektów spowodowany stanem urządzenia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e42e1ce4cc1ccc0a01905046b33e4587964f8ce
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712076"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Przewodnik: Brak obiektów spowodowany stanem urządzenia
W tym instruktażu przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do zbadania obiekt, który nie istnieje ze względu na nieprawidłowo skonfigurowany stan urządzenia.

 W tym instruktażu przedstawiono sposób:

-   Użyj **Lista zdarzeń graficznych** do lokalizowania potencjalnych źródeł problemu.

-   Użyj **etapy potoku grafiki** okna, aby sprawdzić efekt skonfigurowania `DrawIndexed` wywołań interfejsu API Direct3D.

-   Użyj **Historia pikseli grafiki** okna, aby dokładniej zlokalizowania problemu.

-   Sprawdzanie stanu urządzenia dla potencjalnych problemów i błędów konfiguracji.

## <a name="scenario"></a>Scenariusz
 Jednym z powodów obiektów może nie być widoczna gdy dana osoba w 3-app to błędnej konfiguracji urządzenia grafiki, który powoduje, że obiekty, które mają być wykluczone z renderowaniem — na przykład, gdy kolejność zakręcania powoduje trójkąty uboju, w wyniku błędu , lub kiedy funkcja test głębi powoduje, że wszystkie piksele w obiekcie odrzucona.

 W scenariuszu, który jest opisany w tym przewodniku po prostu osiągnęły pierwszej odsłony w trakcie opracowywania aplikacji 3-w i gotowości do testowania go po raz pierwszy. Po uruchomieniu aplikacji, tylko interfejs użytkownika jest renderowany na ekranie. Za pomocą Graphics Diagnostics, możesz przechwytywać problemy do plik dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda to w aplikacji:

 ![Aplikację, zanim problem został rozwiązany](media/vsg_walkthru1_firstview.png "vsg_walkthru1_firstview")

 Aby uzyskać informacje o sposobie przechwytywania problemów z grafiką w dzienniku grafiki, zobacz [Capturing Graphics Information](capturing-graphics-information.md).

## <a name="investigation"></a>Badanie
 Korzystając z narzędzi programu Graphics Diagnostics, należy załadować plik dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki

1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załaduj dziennik grafiki zawierający ramkę, która wykazuje Brak modelu. Nowa karta Diagnostyka grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części na tej karcie jest dane wyjściowe docelowy renderowania zaznaczonej klatki. W dolnej części jest **lista ramek**, powoduje wyświetlenie jako miniaturę każdej uchwyconej klatki.

2. W **lista ramek**, zaznacz klatkę, która pokazuje, że model nie jest wyświetlany. Obiektu docelowego renderowania jest aktualizowana, aby odzwierciedlić wybraną ramkę. W tym scenariuszu dziennika grafiki w karcie wygląda następująco:

    ![.Vsglog kartę bufor ramki (wersja zapoznawcza) i ramki listy](media/vsg_walkthru1_experiment.png "vsg_walkthru1_experiment")

   Po zaznaczeniu klatki, która demonstruje problem, można użyć **Lista zdarzeń graficznych** do zdiagnozowania go. **Lista zdarzeń graficznych** zawiera każdego interfejsu API Direct3D wywołania wykonanego do renderowania aktywną ramkę, na przykład wywołania interfejsu API, aby skonfigurować stan urządzenia, do tworzenia i aktualizowania buforów i aby rysować obiekty, które pojawiają się w ramce. Wiele rodzajów wywołania są interesujące, ponieważ często (ale nie zawsze) analogiczna zmiana obiektu docelowego renderowania, gdy aplikacja działa zgodnie z oczekiwaniami, na przykład rysowania, wysyłania, kopiowanie lub wyczyść połączenia. Wywołania rysowania są szczególnie interesujące, ponieważ każdy z nich reprezentuje geometrię, która aplikacja renderowania (wywołań wysyłania umożliwia również renderowanie geometrii).

#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Aby upewnić się, że rysowania wywołania są wykonywane

1. Otwórz **Lista zdarzeń graficznych** okna. Na **Graphics Diagnostics** narzędzi, wybierz **listy zdarzeń**.

2. Sprawdzanie **Lista zdarzeń graficznych** narysuj wywołania. Aby to ułatwić, wprowadź "Draw" w **wyszukiwania** polu w prawym górnym rogu **Lista zdarzeń graficznych** okna. Filtruje listę, tak aby zawiera tylko zdarzenia, które mają "Draw" w tytułach. W tym scenariuszu można wykryć, czy nie wprowadzono kilka wywołań rysowania:

    ![Lista zdarzeń graficznych przedstawiający przechwycone zdarzenia](media/vsg_walkthru1_.png "vsg_walkthru1_")

   Po upewnieniu się, że rysowania, który trwa wywołań, można określić, która odnosi się do brakujących geometrii. Ponieważ wiadomo, że brakuje Geometria nie rysowania do elementu docelowego renderowania (w tym przypadku), można użyć **etapy potoku grafiki** okna, aby określić, które wywołania rysowania odnosi się do brakujących geometrii. **Etapy potoku grafiki** okno pokazuje geometrię, która została wysłana do każdego wywołania rysowania, niezależnie od jego wpływ na obiektu docelowego renderowania. Po przeniesieniu za pośrednictwem wywołania rysowania etapy potoku są aktualizowane, aby pokazać geometrię, która jest skojarzona z tym wywołaniem, a wyjście docelowego renderowania jest aktualizowany do wyświetlenia stanu obiektu docelowego renderowania po wywołaniu zostało ukończone.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć wywołanie rysowania Brak geometrii

1. Otwórz **etapy potoku grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **etapy potoku**.

2. Przechodzenie między każdym wywołaniem rysowania podczas oglądania **etapy potoku grafiki** okno Brak modelu. **Asemblera dane wejściowe** etap zawiera dane pierwotne modelu. **Program do cieniowania wierzchołków** etapu pokazuje dane po przekształceniu modelu. **Programu do cieniowania pikseli** etap zawiera dane wyjściowe programu do cieniowania pikseli. **Scalanie danych wyjściowych** etapu pokazuje scalony renderowania celem tego wywołania rysowania i poprzednich wywołań rysowania.

3. Zatrzymaj, gdy został osiągnięty wywołanie rysowania, które odnosi się do brakujących modelu. W tym scenariuszu **etapy potoku grafiki** okno wskazuje, czy geometrii była renderowana, ale nie znajdował się w celu renderowania:

    ![Przeglądarka potoku przedstawiający nieistniejącego obiektu](media/vsg_walkthru1_pipeline.png "vsg_walkthru1_pipeline")

   Po upewnieniu się, że aplikacja renderowane Brak geometrii i możesz znaleźć odpowiedniego wywołania rysowania, możesz wybrać fragment danych wyjściowych docelowego renderowania, powinien wyświetlić brakujące geometrii, a następnie za pomocą **Historia pikseli grafiki** okno, aby dowiedzieć się, dlaczego piksele zostały wykluczone. Historia pikseli zawiera listę każde wywołanie rysowania może wywrzeć wpływ na piksela. Wywołania rysowania każdego **Historia pikseli grafiki** okna jest identyfikowany przez numer, który jest wyświetlany na **Lista zdarzeń graficznych** okna. Dzięki temu można potwierdzić, że piksel powinien wyświetlić brakujące geometrii i aby dowiedzieć się, dlaczego piksel został wykluczony

#### <a name="to-determine-why-the-pixel-was-excluded"></a>Aby ustalić, dlaczego piksel został wykluczony

1. Otwórz **Historia pikseli grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **historii pikseli**.

2. Na podstawie **programu do cieniowania pikseli** miniaturę, wybierz piksel w bufor ramki danych wyjściowych może zawierać części Brak geometrii. W tym scenariuszu dane wyjściowe programu do cieniowania pikseli powinna obejmować większość obiektu docelowego renderowania; Po wybraniu piksel **Historia pikseli grafiki** okna wygląda następująco:

    ![Okno Historia pikseli pokazujący pokrewne Rysowanie wywołania](media/vsg_walkthru1_hist1.png "vsg_walkthru1_hist1")

3. Upewnij się, czy pikseli docelowego renderowania wybranego zawiera część geometrię, dopasowując liczba wywołania rysowania są sprawdzania (z **Lista zdarzeń graficznych** okna) do jednego wywołania rysowania w **grafiki Historia pikseli** okna. Jeśli żadna z wywołań w **Historia pikseli grafiki** okna dopasowania wywołania rysowania, w przypadku sprawdzania, powtórz te kroki (z wyjątkiem kroku 1) do momentu znalezienia dopasowania. W tym scenariuszu dopasowania wywołania rysowania wygląda następująco:

    ![Okno Historia pikseli, przedstawiający informacje o fragmentu](media/vsg_walkthru1_hist2.png "vsg_walkthru1_hist2")

4. Po znalezieniu dopasowania, rozwiń dopasowania wywołanie rysowania w **Historia pikseli grafiki** okna i upewnij się, że piksel został wykluczony. Wywołania rysowania każdego **Historia pikseli grafiki** okna odnosi się do co najmniej jeden geometrycznych podstawowych (punkty, linie lub trójkąty), które mieszają piksela wyniku geometrii odpowiedni obiekt. Takie przecięciu może przyczynić się do końcowy kolor piksela. Elementu podstawowego, który jest wykluczony, ponieważ nie powiodło się test głębi jest reprezentowany przez ikonę która zawiera literę Z nad strzałką, który odchyla dół od lewej do prawej.

5. Rozwiń prymityw wykluczonych dalszego zbadania stanu, który spowodował jego mają być wykluczone. W **scalanie danych wyjściowych** grupy, przesuń wskaźnik nad **wynik**. Etykietka narzędzia wskazuje, dlaczego element pierwotny został wykluczony. W tym scenariuszu badanie ujawnia, że element pierwotny został wykluczony, ponieważ test głębi nie powiódł się i dlatego nie miało wpływu na ostateczny koloru piksela.

   Po ustaleniu, że geometrii niewidoczny, ponieważ jego podstawowych nie powiodło się test głębi, może być podejrzewać, czy ten problem jest związany ze stanu nieprawidłowo skonfigurowane urządzenia. Stan urządzenia i inne Direct3D obiektu danych można sprawdzić za pomocą **Graphics Object Table**.

#### <a name="to-examine-device-state"></a>Aby sprawdzić stan urządzenia

1. Otwórz **Graphics Object Table** okna. Na **Graphics Diagnostics** narzędzi, wybierz **tabeli obiektów**.

2. Znajdź **urządzeniem D3D10** obiektu **Graphics Object Table**, a następnie otwórz **urządzeniem D3D10** obiektu. Nowy **urządzeniem d3d10** Otwiera zakładkę w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby to ułatwić, można sortować **Graphics Object Table** przez **typu**:

    ![Tabela obiektów graficznych i stan urządzenia powiązanych](media/vsg_walkthru1_objtable.png "vsg_walkthru1_objtable")

3. Sprawdź stan urządzenia, która jest wyświetlana w **urządzeniem d3d10** kartę potencjalnych problemach. Ponieważ Geometria nie pojawia się, ponieważ jego podstawowych nie powiodło się test głębi, można skoncentrować się na stanie urządzenia, takie jak wzornika głębi, który ma wpływ na test głębi. W tym scenariuszu **opis wzornika głębi** (w obszarze **dane wyjściowe stanu połączenia**) zawiera wartość nietypowe **głębokość funkcji** elementu członkowskiego, `D3D10_COMPARISON_GREATER`:

    ![Okno urządzenia D3D10 przedstawiający informacje o wzornika głębi](media/vsg_walkthru1_devicestate.png "vsg_walkthru1_devicestate")

   Po ustaleniu, czy funkcja nieprawidłowo głębokość może to być spowodowane problemem renderowania, dzięki tym informacjom wraz ze swojej znajomości kodu do zlokalizowania, gdzie funkcja głębi został ustawiony niepoprawnie, a następnie Rozwiąż ten problem. Jeśli nie jesteś zaznajomiony z kodem, wyszukaj frazę problemu przy użyciu wskazówek, które są zbierane podczas Gdybyś debugował — na przykład na podstawie **opis wzornika głębi** w tym scenariuszu możesz wyszukać kod słów np. "Głębokość" lub "Wyższa". Po rozwiązaniu kodu skompilować go ponownie i uruchomić aplikację ponownie, aby odnaleźć rozwiązany problem renderowania:

   ![Aplikacja po problem został rozwiązany](media/vsg_walkthru1_finalview.png "vsg_walkthru1_finalview")