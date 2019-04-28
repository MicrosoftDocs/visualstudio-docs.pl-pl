---
title: Debugowanie XAML w programie Blend | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 535e7ea155200b06b0783e79d95f4eba96ce1eed
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399516"
---
# <a name="debug-xaml-in-blend"></a>Debugowanie XAML w Blend
Możesz użyć narzędzi dostępnych w [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)] debugowanie XAML w swojej aplikacji. Podczas kompilowania projektu wszystkie błędy są wyświetlane w **wyniki** panelu. Kliknij dwukrotnie błąd do zlokalizowania znaczników związane z błędem. Jeśli potrzebujesz więcej miejsca do pracy, można ukryć **wyniki** panelu, naciskając klawisz F12.

## <a name="syntax-errors"></a>Błędy składniowe
 Błędy składni występują, jeśli pliki związane z kodem lub XAML nie wykonuj reguły formatowania języka. Opis błędu może pomóc Ci zrozumieć, jak go naprawić. Listy określa także nazwę pliku i numer wiersza, w którym występuje błąd. Błędy XAML są wyświetlane na **znaczników** karcie **wyniki** panelu.

> [!TIP]
> XAML jest językiem znaczników oparty na składni XML i regułom składni XML.

 Niektóre typowe przyczyny są błędy składni XAML:

- Błędnie napisane słowa kluczowego lub wielkość liter jest nieprawidłowy.

- Znaki cudzysłowu są ujęta atrybutów lub ciągów tekstowych.

- Brak tagu zamykającego elementu XAML.

- XAML element istnieje w lokalizacji, w którym nie jest dozwolone.

  Aby uzyskać więcej informacji na temat typowej składni XAML, zobacz [Przewodnik po składni XAML podstawowe](http://go.microsoft.com/fwlink/?LinkId=329942).

  Można również zidentyfikować i rozwiązać błędy składniowe proste związanym z kodem, błędy kompilacji i błędów czasu wykonywania w [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Jednak błędy związane z kodem, może być łatwiejsze do zidentyfikowania i rozwiązania w programie Visual Studio.

### <a name="debugging-sample-xaml-code"></a>Debugowanie przykładowego kodu XAML
 Poniższy przykład umożliwia przeprowadzenie proste XAML, w sesji debugowania w [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].

##### <a name="to-create-a-project"></a>Aby utworzyć projekt

1. W [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)], otwórz **pliku** menu, a następnie kliknij przycisk **nowy projekt**.

    W **nowy projekt** okno dialogowe po lewej stronie zostanie wyświetlona lista typów projektów. Po kliknięciu typów projektów, szablony projektów, które są skojarzone z nim są wyświetlane po prawej stronie.

2. Na liście typów projektów, kliknij **Windows Universal**.

3. Na liście szablonów projektu kliknij **pusta aplikacja (Windows Universal)**.

4. W **nazwa** polu tekstowym `DebuggingSample`.

5. W **lokalizacji** tekstu upewnij się, lokalizację projektu.

6. W **języka** kliknij **Visual C#**, a następnie kliknij przycisk **OK** do tworzenia projektu.

7. Kliknij prawym przyciskiem myszy na powierzchni projektowej, a następnie kliknij przycisk **Wyświetl źródło** Aby przełączyć się do **podziału** widoku.

8. Skopiuj poniższy kod, klikając **kopiowania** linku w prawym górnym rogu kodu.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Znajdź wartość domyślna **siatki**i Wklej kod między otwierającym i zamykającym **siatki** tagów. Po zakończeniu, kod powinien wyglądać następująco:

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
         </Grid>
    </Grid>
    ```

10. Naciśnij klawisze Ctrl + Shift + B, aby skompilować projekt.

    Wyświetlony komunikat o błędzie informujący, że nie można utworzyć projektu, a **wyniki** panelu zawierającego listę błędów, pojawi się w dolnej części aplikacji.

    ![Debugowanie XAML w Blend for Visual Studio](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolving-xaml-errors"></a>Rozwiązywanie błędów XAML
 Po wykryciu błędów XAML na powierzchnię projektową wyświetla alert, że projekt zawiera nieprawidłowe znaczniki. Jako Rozwiąż, listę błędów w **wyniki** panel zostanie zaktualizowany. Po rozwiązaniu wszystkich błędów na powierzchnię projektową jest włączona, a Twoja aplikacja jest wyświetlana na powierzchni projektowej.

##### <a name="to-resolve-the-xaml-errors"></a>Aby naprawić błędy XAML

1. Kliknij dwukrotnie pierwszy błąd na liście. Długość opisu jest "wartość" < "jest nieprawidłowa w atrybucie." Gdy klikniesz dwukrotnie błąd, wskaźnik znajdzie odpowiedniej lokalizacji w kodzie. `<` Poprzedniego `Button` jest prawidłowy i nie jest atrybutem zgodnie z sugestią podaną w komunikacie o błędzie. Jeśli spojrzysz na poprzedni wiersz kodu, można zauważyć, że cudzysłowu zamykającego oznacza dla atrybutu `Top` brakuje. Wpisz znaki cudzysłowu zamykającego. Należy zauważyć, że listę błędów w **wyniki** panelu aktualizacji w celu odzwierciedlenia zmian.

2. Kliknij dwukrotnie opis "'0' jest nieprawidłowy na początku nazwy." `Margin="0,149,0,0"` wydaje się być poprawnie sformułowana. Jednak należy zauważyć, że kodowanie kolorami `Margin` jest niezgodny z innymi wystąpieniami `Margin` w kodzie. Ponieważ znaki cudzysłowu zamykającego są nieobecne poprzedniego pary nazwa/wartość (`VerticalAlignment="Top`), `Margin="` jest do odczytu jako część wartości atrybutu poprzedniego i 0 jest do odczytu jako początek pary nazwa/wartość. Wpisz znaki cudzysłowu zamykającego dla `Top`. Lista błędów w **wyniki** panelu aktualizacji w celu odzwierciedlenia zmian.

3. Kliknij dwukrotnie błąd, "zamykający tag XML"Button"jest niezgodny." Wskaźnik myszy znajduje się w zamykającym **siatki** tag (`</Grid>`), sugerujące, że błąd znajduje się wewnątrz `Grid` obiektu. Należy zauważyć, że drugi `Button` obiektu brakuje tagu zamykającego. Po dodaniu zamykającym `/`, **wyniki** panelu lista jest aktualizowana. Teraz, gdy zostały rozwiązane błędy te początkowej dwa dodatkowe błędy zostały zidentyfikowane.

4. Kliknij dwukrotnie ikonę "elementu członkowskiego"content"nie jest rozpoznawany lub jest niedostępny." `c` w `content` powinny być wielkie litery. Zamień małe "c" wielkie litery "c".

5. Kliknij dwukrotnie pozycję "właściwości"Mame"nie istnieje w"<http://schemas.microsoft.com/winfx/2006/xaml>"przestrzeni nazw." "M" w "Mame" powinien być "y". Zastąp "M" z "y". Teraz, można przeanalizować XAML, aplikacja jest wyświetlana na powierzchni projektowej.

    ![Debugowanie XAML w Blend for Visual Studio](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    Naciśnij klawisze Ctrl + Shift + B, aby skompilować projekt i upewnij się, że nie istnieją żadne pozostałe błędy.

## <a name="debugging-in-visual-studio"></a>Debugowanie w Visual Studio
 Możesz otworzyć [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] projektów w programie Visual Studio, aby łatwo debugować kodu w aplikacji. Aby otworzyć [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] projektu w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **projektów** panelu, a następnie kliknij przycisk **Edytuj w programie Visual Studio**. Po zakończeniu sesji debugowania w programie Visual Studio, naciśnij klawisze Ctrl + Shift + S, aby zapisać wszystkie zmiany i przejdź z powrotem do [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Zostanie wyświetlony monit ponownie Załaduj projekt. Kliknij przycisk **tak na wszystko** kontynuowanie pracy w [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)].

 Aby uzyskać więcej informacji o debugowaniu aplikacji, zobacz [debugowanie aplikacji platformy UWP w programie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).

## <a name="getting-help"></a>Uzyskiwanie pomocy
 Jeśli potrzebujesz więcej debugowania pomocy usługi [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] aplikacji, możesz wyszukać [forum użytkowników aplikacji platformy uniwersalnej systemu Windows](http://go.microsoft.com/fwlink/?LinkId=280308) dla wpisów z problemu związanego z lub zadać pytanie.
