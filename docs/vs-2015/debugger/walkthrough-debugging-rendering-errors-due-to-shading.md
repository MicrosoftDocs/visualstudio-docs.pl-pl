---
title: 'Przewodnik: Debugowanie błędów renderowania spowodowanych cieniowaniem | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4c158c4ce6762b69f73a55915cc459f84cd7fff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183634"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Diagnostyka grafiki zbadać obiekt, który jest niepoprawnie kolorowy spowodowany usterką programu do cieniowania.  
  
 W tym instruktażu pokazano, jak:  
  
- Przejrzyj dokument dziennika grafiki, aby zidentyfikować piksele pokazujące problem.  
  
- Użyj okna **Historia pikseli grafiki** , aby dokładniej przeanalizować stan pikseli.  
  
- Użyj **debugera HLSL** do sprawdzenia pikseli i programów do cieniowania wierzchołków.  
  
## <a name="scenario"></a>Scenariusz  
 Niewłaściwe kolorowanie obiektów często występuje, gdy program do cieniowania wierzchołków przeszedł nieprawidłowe lub niekompletne informacje.  
  
 W tym scenariuszu niedawno dodano obiekt do aplikacji wraz z nowymi wierzchołkami i cieniami pikseli w celu przekształcenia obiektu i nadania mu unikatowego wyglądu. Gdy aplikacja jest uruchamiana podczas testu, obiekt jest renderowany w postaci pełnej czerni. Korzystając z Diagnostyka grafiki, można przechwytywać ten problem do dziennika grafiki, dzięki czemu można debugować aplikację. Problem wygląda następująco w aplikacji:  
  
 ![Obiekt jest renderowany z nieprawidłowymi kolorami.](../debugger/media/gfx-diag-demo-render-error-shader-problem.png "gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Badanie  
 Za pomocą narzędzi Diagnostyka grafiki, można załadować dokument dziennika grafiki, aby sprawdzić ramki, które zostały przechwycone podczas testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby przeanalizować ramkę w dzienniku grafiki  
  
1. W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Załaduj dziennik grafiki zawierający ramkę, która wykazuje brakujący model. Zostanie wyświetlone nowe okno dokumentu dziennika grafiki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . W górnej części tego okna są dane wyjściowe docelowej renderowania zaznaczonej ramki. W dolnej części jest **listą ramek**, która wyświetla każdą przechwyconą ramkę jako obraz miniatury.  
  
2. Na **liście ramka**Wybierz ramkę, w której obiekt nie ma poprawnego wyglądu. Obiekt docelowy renderowania zostanie zaktualizowany w celu odzwierciedlenia wybranej ramki. W tym scenariuszu okno dokumentu dziennika grafiki wygląda następująco:  
  
    ![Dokument dziennika grafiki w programie Visual Studio.](../debugger/media/gfx-diag-demo-render-error-shader-step-1.png "gfx_diag_demo_render_error_shader_step_1")  
  
   Po wybraniu ramki, która demonstruje ten problem, można użyć okna **Historia pikseli grafiki** do zdiagnozowania. Okno **Historia pikseli grafiki pokazuje elementy** pierwotne, które mogły mieć wpływ na określony piksel, ich programy do cieniowania i jakie ich skutki dla elementu docelowego renderowania były w kolejności chronologicznej.  
  
#### <a name="to-examine-a-pixel"></a>Aby przejrzeć piksel  
  
1. Otwórz okno **Historia pikseli grafiki** . Na pasku narzędzi **Diagnostyka grafiki** wybierz pozycję **Historia pikseli**.  
  
2. Wybierz piksel do sprawdzenia. W oknie dokumentu dziennika grafiki wybierz jeden z pikseli w obiekcie, który jest niepoprawnie kolorowy:  
  
    ![Wybranie piksela wyświetla informacje o historii.](../debugger/media/gfx-diag-demo-render-error-shader-step-2.png "gfx_diag_demo_render_error_shader_step_2")  
  
    Okno **Historia pikseli grafiki** jest aktualizowane w celu odzwierciedlenia wybranego piksela. W tym scenariuszu okno **Historia pikseli grafiki** wygląda następująco:  
  
    ![Historia pikseli przedstawia jedno zdarzenie DrawIndexed.](../debugger/media/gfx-diag-demo-render-error-shader-step-3.png "gfx_diag_demo_render_error_shader_step_3")  
  
    Zwróć uwagę, że wynik cieniowania pikseli jest w pełni nieprzezroczysty czarny (0, 0, 0, 1) i że **scalanie danych wyjściowych** zostało połączone z **poprzednim** kolorem piksela w taki sposób, że **wynik** jest również całkowicie nieprzezroczysty czarny.  
  
   Po sprawdzeniu piksela, który jest niepoprawnie kolorowy i odkryj, że wyjście cieniowania pikseli nie jest oczekiwanym kolorem, można użyć debugera HLSL do sprawdzenia cieniowania pikseli i dowiedzieć się, co się stało z kolorem obiektu. Debuger HLSL umożliwia badanie stanu zmiennych HLSL podczas wykonywania, przechodzenie przez kod HLSL i ustawianie punktów przerwania, aby ułatwić zdiagnozowanie problemu.  
  
#### <a name="to-examine-the-pixel-shader"></a>Aby przejrzeć cieniowanie pikseli  
  
1. Rozpocznij debugowanie cieniowania pikseli. W oknie **Historia pikseli grafiki** , w obszarze pierwotny obiekt, obok **cieniowania pikseli**wybierz przycisk **Rozpocznij debugowanie** .  
  
2. W tym scenariuszu, ponieważ program do cieniowania pikseli przeszedł po prostu kolor za pośrednictwem programu do cieniowania wierzchołków, można łatwo obserwować, że program do cieniowania pikseli nie jest źródłem problemu.  
  
3. Umieść wskaźnik na `input.color` . Zwróć uwagę, że jej wartość jest całkowicie nieprzezroczysta czarny (0, 0, 0, 1).  
  
    ![Element członkowski "Color" elementu "Input" jest czarny.](../debugger/media/gfx-diag-demo-render-error-shader-step-5.png "gfx_diag_demo_render_error_shader_step_5")  
  
    W tym scenariuszu badanie wykaże, że niewłaściwy kolor jest prawdopodobnie wynikiem cieniowania wierzchołków, która nie zawiera właściwych informacji o kolorze dla cieniowania pikseli, na których będzie wykonywane działanie.  
  
   Po ustaleniu, że program do cieniowania wierzchołków prawdopodobnie nie dostarcza odpowiednich informacji do programu do cieniowania pikseli, następnym krokiem jest sprawdzenie cieniowania wierzchołków.  
  
#### <a name="to-examine-the-vertex-shader"></a>Aby przejrzeć cieniowanie wierzchołków  
  
1. Rozpocznij debugowanie cieniowania wierzchołków. W oknie **Historia pikseli grafiki** w obszarze pierwotnym obiektu obok opcji **cieniowania wierzchołka**wybierz przycisk **Rozpocznij debugowanie** .  
  
2. Znajdź strukturę wyjściową programu do cieniowania wierzchołków — jest to dane wejściowe cieniowania pikseli. W tym scenariuszu nazwa tej struktury jest `output` . Sprawdź kod programu do cieniowania wierzchołków i Zauważ, że `color` element członkowski `output` struktury został jawnie ustawiony jako całkowicie nieprzezroczysty, na przykład w wyniku wysiłków debugowania przez kogoś.  
  
3. Upewnij się, że element członkowski koloru nigdy nie jest kopiowany z struktury wejściowej. Ponieważ wartość `output.color` jest ustawiona na całkowicie nieprzezroczysty czarny tuż przed `output` zwróceniem struktury, dobrym pomysłem jest upewnienie się, że wartość `output` nie została prawidłowo zainicjowana w poprzednim wierszu. Przechodzenie przez kod programu do cieniowania wierzchołków do momentu, gdy zobaczysz `output.color` wartość `output.color` . Zwróć uwagę, że wartość `output.color` nie jest zainicjowana, dopóki nie zostanie ustawiona na czerń. Pozwala to upewnić się, że wiersz kodu, który jest ustawiany `output.color` na czarny, powinien być modyfikowany, a nie usunięty.  
  
    ![Wartość "Output. Color" jest czarna.](../debugger/media/gfx-diag-demo-render-error-shader-step-7.png "gfx_diag_demo_render_error_shader_step_7")  
  
   Po ustaleniu przyczyny problemu z renderowaniem polega na tym, że program do cieniowania wierzchołków nie zapewnia prawidłowej wartości koloru dla programu do cieniowania pikseli. można użyć tych informacji w celu rozwiązania problemu. W tym scenariuszu można rozwiązać ten problem, zmieniając Poniższy kod w programie do cieniowania wierzchołków  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 na wartość  
  
```hlsl  
output.color = input.color;  
```  
  
 Ten kod po prostu przekazuje kolor wierzchołka z wierzchołków obiektu niezmodyfikowanych — bardziej złożone cieniowanie wierzchołków mogą modyfikować kolor przed przekazaniem go przez. Skorygowany kod programu do cieniowania wierzchołków powinien wyglądać następująco:  
  
 ![Skorygowany kod programu do cieniowania wierzchołków.](../debugger/media/gfx-diag-demo-render-error-shader-step-8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Po naprawieniu kodu ponownie skompiluj go i ponownie uruchom aplikację, aby stwierdzić, że problem z renderowaniem został rozwiązany.  
  
 ![Obiekt jest renderowany z prawidłowymi kolorami.](../debugger/media/gfx-diag-demo-render-error-shader-resolution.png "gfx_diag_demo_render_error_shader_resolution")
