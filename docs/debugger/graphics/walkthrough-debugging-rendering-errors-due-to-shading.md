---
title: 'Przewodnik: debugowanie błędów renderowania spowodowanych cieniowania | Microsoft Docs'
description: Postępuj zgodnie z badaniem, które znajdzie usterkę modułu cieniującego. Pokazuje on sposób użycia Visual Studio Diagnostyka grafiki, w tym historię pikseli grafiki i debuger HLSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 218b263d7e971a0d2bdaa72020bb7cb58c31e000
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387089"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Przewodnik: debugowanie błędów renderowania spowodowanych cieniowaniem
W tym przewodniku pokazano, jak używać Diagnostyka grafiki do badania obiektu, który ma niepoprawne kolorowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z powodu usterki modułu cieniującego.

 W tym przewodniku pokazano, jak:

- Sprawdź dokument dziennika grafiki, aby zidentyfikować piksele, które pokazują problem.

- Użyj okna **Historia pikseli grafiki,** aby dokładniej zbadać stan pikseli.

- Użyj **debugera HLSL,** aby zbadać cieniowanie pikseli i wierzchołków.

## <a name="scenario"></a>Scenariusz
 Nieprawidłowe kolorowanie obiektów często występuje, gdy moduł cieniowania wierzchołków przekazuje nieprawidłowe lub niekompletne informacje do modułu cieniowania pikseli.

 W tym scenariuszu niedawno dodano obiekt do aplikacji. Dodano również nowe cieniowanie wierzchołków i pikseli, aby przekształcić obiekt i nadać mu unikatowy wygląd. Po uruchomieniu aplikacji podczas testu obiekt jest renderowany w kolorze czarnym. Za pomocą Diagnostyka grafiki można przechwycić problem do dziennika grafiki, aby można było debugować aplikację. Problem wygląda następująco:

 ![Obiekt jest renderowany z nieprawidłowymi kolorami.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Badanie
 Za pomocą Diagnostyka grafiki można załadować dokument dziennika grafiki, aby sprawdzić ramki przechwycone podczas testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby zbadać ramkę w dzienniku grafiki

1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pliku załaduj dziennik grafiki z ramką, która pokazuje brakujący model. W oknie nowego dokumentu dziennika graficznego zostanie wyświetlone okno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . W górnej części tego okna są docelowe dane wyjściowe renderowania wybranej ramki. W dolnej części znajduje się **lista ramek**, która wyświetla każdą przechwyconą ramkę jako obraz miniatury.

2. Na liście **ramek** wybierz ramkę, w której obiekt nie ma poprawnego wyglądu. Element docelowy renderowania jest aktualizowany w celu odzwierciedlenia wybranej ramki. W tym scenariuszu okno dokumentu dziennika grafiki wygląda następująco:

    ![Dokument dziennika grafiki w Visual Studio.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Po wybraniu ramki, która demonstruje problem,  można go zdiagnozować za pomocą okna Historia pikseli grafiki. Okno **Historia pikseli** grafiki przedstawia elementy pierwotne, które mogły mieć wpływ na określony piksel, jego cieniowania i wpływ na cel renderowania, w kolejności chronologicznej.

#### <a name="to-examine-a-pixel"></a>Aby zbadać piksel

1. Otwórz okno **Historia pikseli grafiki.** Na pasku **Diagnostyka grafiki** wybierz pozycję **Historia pikseli.**

2. Wybierz piksel do zbadania. W oknie dokumentu dziennika grafiki wybierz jeden z pikseli obiektu, który ma niepoprawny kolor:

    ![Wybranie piksela powoduje wyświetlenie informacji o jego historii.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    Okno **Historia pikseli grafiki** zostanie zaktualizowane w celu odzwierciedlenia wybranego piksela. W tym scenariuszu okno **Historia pikseli grafiki** wygląda następująco:

    ![Historia pikseli pokazuje jedno zdarzenie DrawIndexed.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Zwróć uwagę, że wynik cieniowania pikseli jest w pełni nieprzezroczysty czarny (0, 0, 0, 1), a połączenie danych  wyjściowych łączy ten cieniowanie pikseli z poprzednim kolorem piksela w taki sposób, że wynik jest również w pełni nieprzezroczysty czarny.  

   Po zbadaniu piksela, który jest niepoprawnie kolorowy i odkrysz, że dane wyjściowe modułu cieniowania pikseli nie są oczekiwanym kolorem, możesz użyć debugera HLSL, aby zbadać moduł cieniowania pikseli i dowiedzieć się, co się stało z kolorem obiektu. Debuger HLSL umożliwia badanie stanu zmiennych HLSL podczas wykonywania, krok po kodzie HLSL i ustawianie punktów przerwania w celu zdiagnozowania problemu.

#### <a name="to-examine-the-pixel-shader"></a>Aby zbadać cieniowanie pikseli

1. Rozpocznij debugowanie cieniowania pikseli. W **oknie Historia pikseli** grafiki w obszarze prymitywu obiektu obok opcji **Cieniowanie pikseli** wybierz przycisk Rozpocznij **debugowanie.**

2. W tym scenariuszu, ponieważ moduł cieniowania pikseli po prostu przekazuje kolor z modułu cieniowania wierzchołków, łatwo zauważyć, że cieniowanie pikseli nie jest źródłem problemu.

3. Rest the pointer on `input.color` . Zwróć uwagę, że jego wartość to w pełni nieprzezroczysty czarny (0, 0, 0, 1).

    !["Kolor" członka "input" jest czarny.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    W tym scenariuszu badanie pokazuje, że nieprawidłowy kolor jest prawdopodobnie wynikiem cieniowania wierzchołków, który nie dostarcza odpowiednich informacji o kolorze dla modułu cieniującego piksele.

   Gdy ustalisz, że program do cieniowania wierzchołków prawdopodobnie nie dostarcza odpowiednich informacji do cieniowania pikseli, następnym krokiem jest zbadanie modułu cieniującego wierzchołki.

#### <a name="to-examine-the-vertex-shader"></a>Aby zbadać moduł cieniowania wierzchołków

1. Rozpocznij debugowanie cieniowania wierzchołków. W **oknie Historia pikseli** grafiki w obszarze prymitywu obiektu obok opcji **Cieniowanie** wierzchołków wybierz **przycisk Rozpocznij debugowanie.**

2. Znajdź strukturę danych wyjściowych modułu cieniowania wierzchołków — jest to dane wejściowe modułu cieniowania pikseli. W tym scenariuszu nazwa tej struktury to `output` . Sprawdź kod modułu cieniującego wierzchołek i zwróć uwagę, że składowa struktury została jawnie ustawiona na całkowicie nieprzezroczystą czarny, być może w wyniku działań `color` `output` debugowania przez kogoś.

3. Upewnij się, że składowa koloru nigdy nie jest kopiowana ze struktury wejściowej. Ponieważ wartość jest ustawiona na całkowicie nieprzezroczysty czarny tuż przed zwróceniem struktury, dobrym pomysłem jest upewnienie się, że wartość nie została poprawnie zainicjowana w poprzednim `output.color` `output` `output` wierszu. Przechodzij przez kod modułu cieniującego wierzchołek do momentu osiągnięcia linii, która jest ustawiana na czarny, podczas `output.color` obserwowania wartości `output.color` . Zwróć uwagę, że wartość `output.color` nie zostanie zainicjowana, dopóki nie zostanie ustawiona na czarny. To potwierdza, że wiersz kodu ustawiany na czarny powinien `output.color` zostać zmodyfikowany, a nie usunięty.

    ![Wartość "output.color" jest czarna.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   Po ustaleniu, że przyczyną problemu z renderowaniem jest to, że program do cieniowania wierzchołków nie dostarcza poprawnej wartości koloru do cieniowania pikseli, można użyć tych informacji do rozwiązania problemu. W tym scenariuszu można rozwiązać ten problem, zmieniając następujący kod w programie do cieniowania wierzchołków

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 na wartość

```hlsl
output.color = input.color;
```

 Ten kod po prostu przekazuje kolor wierzchołka z niezmodyfikowanych wierzchołków obiektu — bardziej złożone cieniowania wierzchołków mogą modyfikować kolor przed przekazaniem go. Poprawiony kod modułu cieniującego wierzchołki powinien wyglądać następująco:

 ![Poprawiony kod modułu cieniującego wierzchołki.](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Po naprawieniu kodu odbuduj go i ponownie uruchom aplikację, aby dowiedzieć się, że problem z renderowaniem został rozwiązany.

 ![Obiekt jest renderowany z prawidłowymi kolorami.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
