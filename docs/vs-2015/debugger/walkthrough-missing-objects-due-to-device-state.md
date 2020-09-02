---
title: 'Przewodnik: brak obiektów ze względu na stan urządzenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b0d2bbd-0729-4aa5-8308-70c5bf1468c5
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a14c944cf38e0eaec7d1fbe4d7699bbd91c3e7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64822007"
---
# <a name="walkthrough-missing-objects-due-to-device-state"></a>Przewodnik: brak obiektów spowodowany stanem urządzenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Diagnostyka grafiki zbadać nieobecny obiekt z powodu nieprawidłowego skonfigurowania stanu urządzenia.  
  
 W tym instruktażu pokazano, jak:  
  
- Użyj **listy zdarzeń grafiki** , aby znaleźć potencjalne źródła problemu.  
  
- Użyj okna **etapy potoku grafiki** , aby sprawdzić efekt `DrawIndexed` wywołań interfejsu API Direct3D.  
  
- Użyj okna **Historia pikseli grafiki** , aby dokładniej zlokalizować problem.  
  
- Sprawdź stan urządzenia pod kątem potencjalnych problemów lub niepożądanych konfiguracji.  
  
## <a name="scenario"></a>Scenariusz  
 Jedną z przyczyn, w których obiekty mogą się nie pojawić, jeśli są one oczekiwane w aplikacji 3-D, jest błędna konfiguracja urządzenia graficznego, które powoduje, że obiekty są wykluczone z renderowania — na przykład, gdy porządek wiatru powoduje odrzucanie trójkątów, lub gdy funkcja testu głębokości powoduje odrzucenie wszystkich pikseli w obiekcie.  
  
 W scenariuszu opisanym w tym instruktażu właśnie został osiągnięty pierwszy punkt kontrolny podczas opracowywania aplikacji 3-D i jest gotowy do przetestowania go po raz pierwszy. Jednak po uruchomieniu aplikacji tylko interfejs użytkownika jest renderowany na ekranie. Korzystając z Diagnostyka grafiki, można przechwytywać problem do pliku dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda następująco w aplikacji:  
  
 ![Aplikacja przed usunięciem problemu](../debugger/media/vsg-walkthru1-firstview.png "vsg_walkthru1_firstview")  
  
 Aby uzyskać informacje o sposobach przechwytywania problemów graficznych w dzienniku grafiki, zobacz [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Badanie  
 Za pomocą narzędzi Diagnostyka grafiki, można załadować plik dziennika grafiki, aby sprawdzić ramki, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby przeanalizować ramkę w dzienniku grafiki  
  
1. W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Załaduj dziennik grafiki zawierający ramkę, która wykazuje brakujący model. Zostanie wyświetlona nowa karta Diagnostyka grafiki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . W górnej części tej karty są docelowe wyniki renderowania dla wybranej ramki. W dolnej części jest **listą ramek**, która wyświetla każdą przechwyconą ramkę jako obraz miniatury.  
  
2. Na **liście ramka**Wybierz ramkę, która pokazuje, że model nie jest wyświetlany. Obiekt docelowy renderowania zostanie zaktualizowany w celu odzwierciedlenia wybranej ramki. W tym scenariuszu karta Dziennik grafiki wygląda następująco:  
  
    ![Karta. vsglog w wersji zapoznawczej i lista ramek](../debugger/media/vsg-walkthru1-experiment.png "vsg_walkthru1_experiment")  
  
   Po wybraniu ramki, która demonstruje ten problem, można użyć **listy zdarzeń grafiki** do zdiagnozowania. **Lista zdarzeń grafiki** zawiera wszystkie wywołania interfejsu API Direct3D, które zostały wykonane w celu renderowania aktywnej ramki, na przykład wywołania interfejsu API w celu skonfigurowania stanu urządzenia, tworzenia i aktualizowania buforów oraz do rysowania obiektów, które pojawiają się w ramce. Wiele rodzajów wywołań jest interesujących, ponieważ występuje często (ale nie zawsze) odpowiednia zmiana w miejscu docelowym renderowania, gdy aplikacja działa zgodnie z oczekiwaniami, na przykład rysowanie, wysyłanie, kopiowanie lub czyszczenie wywołań. Wywołania rysowania są szczególnie interesujące, ponieważ każda z nich reprezentuje geometrię renderowaną przez aplikację (wywołania wysyłania mogą również renderować geometrię).  
  
#### <a name="to-ensure-that-draw-calls-are-being-made"></a>Aby upewnić się, że są wykonywane wywołania rysowania  
  
1. Otwórz okno **Lista zdarzeń grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **Lista zdarzeń**.  
  
2. Sprawdź **listę zdarzeń grafiki** dla wywołań rysowania. Aby to ułatwić, wprowadź ciąg "Draw" w polu **wyszukiwania** w prawym górnym rogu okna **Lista zdarzeń grafiki** . Filtruje listę, tak aby zawierała tylko zdarzenia, które mają "Draw" w swoich tytułach. W tym scenariuszu wykryjesz, że wykonano kilka wywołań rysowania:  
  
    ![Lista zdarzeń grafiki przedstawiająca przechwycone zdarzenia](../debugger/media/vsg-walkthru1.png "vsg_walkthru1_")  
  
   Po potwierdzeniu, że są wykonywane wywołania rysowania, można określić, która z nich odpowiada brakującej geometrii. Ponieważ wiesz, że brakująca geometria nie jest rysowana do elementu docelowego renderowania (w tym przypadku), możesz użyć okna **etapy potoku grafiki** , aby określić, które wywołanie rysowania odnosi się do brakującej geometrii. Okno **etapy potoku grafiki** pokazuje geometrię, która została wysłana do każdego wywołania rysowania, niezależnie od jej wpływu na obiekt docelowy renderowania. Podczas poruszania się po wywołaniach rysowania etapy potoku są aktualizowane w celu wyświetlenia geometrii, która jest skojarzona z tym wywołaniem, a docelowe dane wyjściowe renderowania są aktualizowane w celu wyświetlenia stanu obiektu docelowego renderowania po zakończeniu wywołania.  
  
#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>Aby znaleźć połączenie rysowania dla brakującej geometrii  
  
1. Otwórz okno **etapy potoku grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **etapy potoku**.  
  
2. Przechodź przez każde wywołanie rysowania podczas oglądania okna **etapy potoku grafiki** dla brakującego modelu. Etap **asemblera wejściowego** przedstawia dane surowego modelu. Etap **cieniowania wierzchołka** przedstawia przekształcone dane modelu. Etap **cieniowania pikseli** przedstawia dane wyjściowe programu do cieniowania pikseli. Etap **łączenia danych wyjściowych** pokazuje scalony obiekt docelowy renderowania tego wywołania rysowania i wszystkie poprzednie wywołania rysowania.  
  
3. Zatrzymaj po osiągnięciu wywołania rysowania odpowiadającego brakującemu modelowi. W tym scenariuszu okno **etapy potoku grafiki** wskazuje, że geometria została renderowana, ale nie została wyświetlona w miejscu docelowym renderowania:  
  
    ![Podgląd potoku pokazujący brakujący obiekt](../debugger/media/vsg-walkthru1-pipeline.png "vsg_walkthru1_pipeline")  
  
   Po upewnieniu się, że aplikacja wykazała brakującą geometrię i odszukasz odpowiednie wywołanie rysowania, możesz wybrać część docelowego danych wyjściowych renderowania, która powinna zawierać brakującą geometrię, a następnie użyć okna **Historia pikseli grafiki** , aby dowiedzieć się, dlaczego piksele zostały wykluczone. Historia pikseli zawiera listę wszystkich wywołań rysowania, które mogły mieć wpływ na określony piksel. Każde wywołanie rysowania w oknie **Historia pikseli grafiki** jest identyfikowane przez liczbę, która jest również wyświetlana w oknie **Lista zdarzeń grafiki** . Dzięki temu można potwierdzić, że piksel powinien wyświetlać brakującą geometrię i aby dowiedzieć się, dlaczego piksel został wykluczony  
  
#### <a name="to-determine-why-the-pixel-was-excluded"></a>Aby określić, dlaczego piksel został wykluczony  
  
1. Otwórz okno **Historia pikseli grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **Historia pikseli**.  
  
2. W oparciu o miniaturę programu do **cieniowania pikseli** wybierz piksel w danych wyjściowych bufor ramki, który powinien zawierać część brakującej geometrii. W tym scenariuszu dane wyjściowe programu do cieniowania pikseli powinny obejmować większość elementów docelowych renderowania; Po wybraniu piksela okno **Historia pikseli grafiki** będzie wyglądać następująco:  
  
    ![Okno historii pikseli przedstawiające powiązane wywołania rysowania](../debugger/media/vsg-walkthru1-hist1.png "vsg_walkthru1_hist1")  
  
3. Upewnij się, że wybrany piksel docelowy renderowania zawiera część geometrii, dopasowując liczbę sprawdzanych wywołań rysowania (z okna **Lista zdarzeń grafiki** ) do jednego z wywołań rysowania w oknie **Historia pikseli grafiki** . Jeśli żadne z wywołań w oknie **Historia pikseli graficznych** nie jest zgodne z wyszukiwanym wywołaniem rysowania, Powtórz te kroki (z wyjątkiem kroku 1) do momentu znalezienia dopasowania. W tym scenariuszu pasujące wywołanie rysowania wygląda następująco:  
  
    ![Okno historii pikseli przedstawiające informacje o fragmentacji](../debugger/media/vsg-walkthru1-hist2.png "vsg_walkthru1_hist2")  
  
4. Po znalezieniu dopasowania rozwiń pasujące wywołanie rysowania w oknie **Historia pikseli grafiki** i upewnij się, że piksel został wykluczony. Każde wywołanie rysowania w oknie **Historia pikseli grafiki** odpowiada jednemu lub więcej geometrycznym elementom podstawowym (punktom, wierszom lub trójkątom), które przecinają ten piksel w wyniku geometrii odpowiedniego obiektu. Każda taka przecięcie może współtworzyć końcowy kolor piksela. Element pierwotny, który jest wykluczony, ponieważ nie powiódł się, test głębokości jest reprezentowany przez ikonę pokazującą literę Z nad strzałką biegnącą w dół od lewej do prawej.  
  
5. Rozwiń wykluczony element podstawowy, aby kontynuować badanie stanu, który spowodował jego wykluczenie. W grupie **fuzja danych wyjściowych** przesuń wskaźnik myszy na **wynik**. Etykietka narzędzia wskazuje, dlaczego element pierwotny został wykluczony. W tym scenariuszu badanie wykaże, że element pierwotny został wykluczony, ponieważ test głębokości nie zakończył się powodzeniem, w związku z czym nie doprowadził do końcowego koloru piksela.  
  
   Po ustaleniu, że geometria nie jest wyświetlana, ponieważ jej pierwotne testy głębokości zakończyły się niepowodzeniem, może się zdarzyć, że ten problem jest związany ze stanem nieprawidłowym skonfigurowanym urządzeniem. Stan urządzenia i inne dane obiektów Direct3D można sprawdzić za pomocą **tabeli obiektów graficznych**.  
  
#### <a name="to-examine-device-state"></a>Aby przejrzeć stan urządzenia  
  
1. Otwórz okno **tabeli obiektów graficznych** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **tabela obiektów**.  
  
2. Zlokalizuj obiekt **urządzenia d3d10** w **tabeli obiektów graficznych**, a następnie otwórz obiekt **urządzenia d3d10** . Zostanie otwarta nowa karta **urządzenia d3d10** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby to ułatwić, można posortować **tabelę obiektów graficznych** według **typu**:  
  
    ![Tabela obiektów graficznych i stan pokrewnych urządzeń](../debugger/media/vsg-walkthru1-objtable.png "vsg_walkthru1_objtable")  
  
3. Sprawdź stan urządzenia, który jest wyświetlany na karcie **Urządzenie D3D10** , aby poznać potencjalne problemy. Ponieważ geometria nie zostanie wyświetlona, ponieważ jej elementy pierwotne nie powiodły się testu głębokości, można skupić się na stanie urządzenia, takim jak wzornik głębokości, który ma wpływ na test głębokości. W tym scenariuszu **Opis wzornika głębokości** (w obszarze **stan scalania danych wyjściowych**) zawiera nietypową wartość elementu członkowskiego **głębokości funkcji** `D3D10_COMPARISON_GREATER` :  
  
    ![Okno urządzenia D3D10 z informacjami o wzorniku głębokości](../debugger/media/vsg-walkthru1-devicestate.png "vsg_walkthru1_devicestate")  
  
   Po ustaleniu, że przyczyną problemu z renderowaniem może być błędnie skonfigurowana funkcja głębokości, można użyć tych informacji razem z wiedzą o kodzie, aby zlokalizować, gdzie funkcja głębokości została ustawiona nieprawidłowo, a następnie rozwiązać ten problem. Jeśli nie znasz kodu, możesz wyszukać problem, wykorzystując wskazówki zebrane podczas debugowania — na przykład na podstawie **opisu wzornika głębokości** w tym scenariuszu można wyszukać w kodzie słowa takie jak "głębokość" lub "większe". Po naprawieniu kodu ponownie skompiluj go i ponownie uruchom aplikację, aby poznać, że problem z renderowaniem został rozwiązany:  
  
   ![Aplikacja po rozwiązaniu problemu](../debugger/media/vsg-walkthru1-finalview.png "vsg_walkthru1_finalview")
