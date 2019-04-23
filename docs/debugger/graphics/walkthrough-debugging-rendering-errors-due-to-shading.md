---
title: 'Przewodnik: Debugowanie błędów renderowania spowodowanych cieniowaniem | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44e542bcbb801ee4035ba501b50bad81b53e8bdf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091333"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Przewodnik: Debugowanie błędów renderowania spowodowanych cieniowaniem
W tym instruktażu przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do zbadania obiekt, który jest niepoprawnie kolorowe z powodu usterki programu do cieniowania.

 W tym instruktażu przedstawiono sposób:

- Sprawdź dokument dziennika grafiki, aby zidentyfikować pikseli, które pokazują problem.

- Użyj **Historia pikseli grafiki** okna, aby dokładniej zbadać stan pikseli.

- Użyj **Debuger języka HLSL** do zbadania cieniowania pikseli i wierzchołka.

## <a name="scenario"></a>Scenariusz
 Niepoprawne kolorowanie na obiektach często występuje po program do cieniowania wierzchołków przekazuje piksel niepoprawne lub niepełne informacje programu do cieniowania.

 W tym scenariuszu ostatnio dodane do Twojej aplikacji obiektu. Dodano także nowy wierzchołek i programów do cieniowania pikseli, Przekształć obiekt i nadaj mu unikatowego wyglądu. Po uruchomieniu aplikacji podczas testu, obiekt jest renderowany w stałych czarny. Przy użyciu programu Graphics Diagnostics można przechwytywać problemy do dziennika grafiki tak, aby można było debugować aplikację. Ten problem będzie wyglądać następująco w aplikacji:

 ![Obiekt jest renderowany przy użyciu nieprawidłowych kolorów. ](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Badanie
 Korzystając z narzędzi programu Graphics Diagnostics, należy załadować dokument dziennika grafiki, aby sprawdzić ramek, które zostały przechwycone podczas testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Aby sprawdzić ramkę w dzienniku grafiki

1. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], załaduj dziennik grafiki zawierający ramkę, która zawiera Brak modelu. Nowe okno dokumentu dziennika grafiki pojawia się w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W górnej części tego okna jest dane wyjściowe docelowy renderowania zaznaczonej klatki. W dolnej części jest **lista ramek**, powoduje wyświetlenie jako miniaturę każdej uchwyconej klatki.

2. W **lista ramek**, zaznacz klatkę, w której ten obiekt nie jest poprawną wygląd. Obiektu docelowego renderowania jest aktualizowana, aby odzwierciedlić wybraną ramkę. W tym scenariuszu dziennika grafiki w oknie dokumentu wygląda następująco:

    ![Dokument dziennika w grafiki w programie Visual Studio. ](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Po zaznaczeniu klatki, która demonstruje problem, można użyć **Historia pikseli grafiki** okna do zdiagnozowania go. **Historia pikseli grafiki** okno pokazuje podstawowych, które może wywrzeć wpływ na określonych pikseli, ich programów do cieniowania i co ich wpływu na obiektu docelowego renderowania były w porządku chronologicznym.

#### <a name="to-examine-a-pixel"></a>Aby zbadać piksel

1. Otwórz **Historia pikseli grafiki** okna. Na **Graphics Diagnostics** narzędzi, wybierz **historii pikseli**.

2. Wybierz piksel do sprawdzenia. W oknie dokumentu dziennika grafiki wybierz jedną z pikseli na obiekt, który jest niepoprawnie pokolorowane:

    ![Wybieranie piksel Wyświetla informacje na temat jego historię. ](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    **Historia pikseli grafiki** okno zostanie zaktualizowany w celu odzwierciedlenia wybrany piksel. W tym scenariuszu **Historia pikseli grafiki** okna wygląda następująco:

    ![Historia pikseli zawiera jedno zdarzenie DrawIndexed. ](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Zauważ, że wynik do cieniowania pikseli jest całkowicie nieprzezroczysty czarny (0, 0, 0, 1), a **scalanie danych wyjściowych** połączone ten program do cieniowania pikseli z **Wstecz** kolor piksela w taki sposób, który  **Wynik** jest również całkowicie nieprzezroczysty czarny.

   Po zbadać pikseli, który jest niepoprawnie kolorowe i odnajdywać dane wyjściowe programu do cieniowania pikseli nie jest oczekiwanym kolor, można użyć debugera HLSL do badania program do cieniowania pikseli i Dowiedz się, co się stało z kolor obiektu. Możesz za pomocą debugera HLSL przeanalizować stan zmiennych HLSL w czasie wykonywania, krokowe kodu języka HLSL i ustawić punkty przerwania, aby pomóc w diagnozowaniu problemu.

#### <a name="to-examine-the-pixel-shader"></a>Aby sprawdzić program do cieniowania pikseli

1. Rozpocznij debugowanie programu do cieniowania pikseli. W **Historia pikseli grafiki** obok okna w obiekcie użytkownika typy pierwotne **programu do cieniowania pikseli**, wybierz **Rozpocznij debugowanie** przycisku.

2. W tym scenariuszu ponieważ program do cieniowania pikseli po prostu przekazuje w kolor cieniowania wierzchołków to ułatwia zaobserwować, że program do cieniowania pikseli nie jest źródłem problemu.

3. Umieść wskaźnik myszy na `input.color`. Należy zauważyć, że jego wartość jest całkowicie nieprzezroczysty czarny (0, 0, 0, 1).

    !["Pole color" członek "input" jest czarny. ](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    W tym scenariuszu badania wykaże, że niepoprawny kolor jest prawdopodobnie wynik cieniowania wierzchołków, który nie zawiera informacji prawy kolor dla programu do cieniowania pikseli do wykonywania operacji.

   Po określeniu, czy program do cieniowania wierzchołków prawdopodobnie nie dostarcza właściwe informacje programu do cieniowania pikseli, następnym krokiem jest Sprawdź program do cieniowania wierzchołków.

#### <a name="to-examine-the-vertex-shader"></a>Aby sprawdzić program do cieniowania wierzchołków

1. Rozpocznij debugowanie programu do cieniowania wierzchołków. W **Historia pikseli grafiki** obok okna w obiekcie użytkownika typy pierwotne **program do cieniowania wierzchołków**, wybierz **Rozpocznij debugowanie** przycisku.

2. Znajdź moduł cieniujący wierzchołków strukturę wyjściową — jest to dane wejściowe programu do cieniowania pikseli. W tym scenariuszu jest nazwa tej struktury `output`. Poszukaj w kodzie programu do cieniowania wierzchołków i zwróć uwagę, że `color` członkiem `output` struktura została jawnie ustawiona na całkowicie nieprzezroczysty czarny, prawdopodobnie w wyniku osoby trwa debugowanie wysiłków.

3. Upewnij się, czy członek kolor nigdy nie jest kopiowany z strukturze wejściowej. Ponieważ wartość `output.color` jest ustawiony na całkowicie nieprzezroczysty czarny tuż przed `output` struktury jest zwracany, to dobry pomysł, aby upewnić się, że wartość `output` nie został prawidłowo zainicjowany w poprzednim wierszu. Przechodź przez kod programu do cieniowania wierzchołków aż do wiersza, który ustawia `output.color` czarny podczas oglądania wartość `output.color`. Należy zauważyć, że wartość `output.color` nie została zainicjowana, dopóki nie jest ustawiona na czarny. Będzie to potwierdzenie, że wiersza kodu, który ustawia `output.color` na czarny powinny być zmodyfikowane, a nie usunięte.

    ![Wartość "output.color" jest czarny. ](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   Po ustaleniu, czy przyczyny tego problemu renderowania jest, że program do cieniowania wierzchołków nie dostarcza wartość prawidłowy kolor programu do cieniowania pikseli, można użyć tych informacji, aby rozwiązać ten problem. W tym scenariuszu możesz ją naprawić, zmieniając następujący kod w program do cieniowania wierzchołków

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 na

```hlsl
output.color = input.color;
```

 Ten kod po prostu przekazuje kolor wierzchołka z obiektu wierzchołków w niezmienionej postaci — bardziej złożonych programów do cieniowania wierzchołków można zmodyfikować kolor przed przekazaniem go za pośrednictwem. Kod programu do cieniowania wierzchołków poprawiony powinien wyglądać następująco:

 ![Kod programu do cieniowania wierzchołków poprawiony. ](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Po rozwiązaniu kodu skompilować go ponownie, a następnie uruchom aplikację ponownie, aby wykryć, że rozwiązanie jest problem z renderowaniem.

 ![Obiekt jest renderowany poprawne kolorów. ](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
