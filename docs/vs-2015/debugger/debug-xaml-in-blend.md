---
title: Debuguj kod XAML w programie Blend | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e032f9f99087df26c82b4984c2267a35236bf6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444625"
---
# <a name="debug-xaml-in-blend"></a>Debugowanie XAML w Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć narzędzi w programie, [!INCLUDE[blend_first](../includes/blend-first-md.md)] Aby debugować kod XAML w aplikacji. Podczas kompilowania projektu wszystkie błędy są wyświetlane w panelu **wyników** . Kliknij dwukrotnie błąd, aby zlokalizować znacznik związany z błędem. Jeśli potrzebujesz więcej miejsca do pracy, możesz ukryć panel **wyników** , naciskając klawisz F12.  
  
## <a name="syntax-errors"></a>Błędy składniowe  
 Występują błędy składniowe, jeśli kod XAML lub plik związany z kodem nie są zgodne z regułami formatowania języka. Opis błędu może pomóc zrozumieć, jak go naprawić. Lista określa również nazwę pliku i numer wiersza, w którym występuje błąd. Błędy XAML są wyświetlane na karcie **znaczniki** w panelu **wyniki** .  
  
> [!TIP]
> XAML jest językiem znaczników opartym na języku XML i jest zgodna z regułami składni XML.  
  
 Niektóre typowe przyczyny błędów składni XAML to:  
  
- Słowo kluczowe zostało źle napisane lub kapitalizacja jest nieprawidłowe.  
  
- Brak znaków cudzysłowu wokół atrybutów lub ciągów tekstowych.  
  
- Element XAML nie zawiera taga zamykającego.  
  
- Element XAML istnieje w lokalizacji, w której jest niedozwolony.  
  
  Aby uzyskać więcej informacji na temat typowej składni języka XAML, zobacz [podstawowy przewodnik po SKŁADNI XAML](https://msdn.microsoft.com/library/windows/apps/hh700351.aspx).  
  
  Można również identyfikować i rozwiązywać proste błędy składni związane z kodem, błędy kompilacji i błędy czasu wykonywania w programie [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] . Błędy związane z kodem mogą jednak ułatwić identyfikowanie i rozwiązywanie problemów w programie Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Debugowanie przykładowego kodu XAML  
 Poniższy przykład przeprowadzi Cię przez prostą sesję debugowania XAML w [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] .  
  
##### <a name="to-create-a-project"></a>Aby utworzyć projekt  
  
1. W programie [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] Otwórz menu **plik** , a następnie kliknij pozycję **Nowy projekt**.  
  
    W oknie dialogowym **Nowy projekt** lista typów projektów pojawia się po lewej stronie. Po kliknięciu typu projektu skojarzone z nim szablony projektu pojawiają się po prawej stronie.  
  
2. Na liście typów projektów kliknij pozycję **XAML (Sklep Windows)**.  
  
3. Na liście szablonów projektu kliknij pozycję **pusta aplikacja**.  
  
4. W polu tekstowym **Nazwa** wpisz `DebuggingSample` .  
  
5. W polu tekstowym **Lokalizacja** Sprawdź lokalizację projektu.  
  
6. Na liście **Język** kliknij **Visual C#**, a następnie kliknij przycisk **OK** , aby utworzyć projekt.  
  
7. Kliknij prawym przyciskiem myszy powierzchnię projektową, a następnie kliknij pozycję **Wyświetl źródło** , aby przełączyć się do widoku **podzielonego** .  
  
8. Skopiuj następujący kod, klikając link **Kopiuj** w prawym górnym rogu kodu.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Znajdź domyślną **siatkę**i wklej kod między otwierającym i zamykającym tagiem **siatki** . Po zakończeniu kod powinien wyglądać następująco:  
  
    ```  
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
  
10. Naciśnij klawisze Ctrl+Shift+B, aby skompilować projekt.  
  
    Zostanie wyświetlony komunikat o błędzie informujący o tym, że nie można skompilować projektu, a panel **wyników** wyświetla błędy w dolnej części aplikacji.  
  
    ![Debugowanie kodu XAML w narzędziu Blend for Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Rozwiązywanie błędów XAML  
 Po wykryciu błędów XAML na powierzchni projektowej zostanie wyświetlony alert informujący, że projekt zawiera nieprawidłowe oznaczenie. Po rozwiązaniu błędów Lista błędów w panelu **wyników** zostanie zaktualizowana. Po rozwiązaniu wszystkich błędów powierzchnia projektowa jest włączona, a aplikacja zostanie wyświetlona na powierzchni projektowej.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Aby rozwiązać Błędy XAML  
  
1. Kliknij dwukrotnie pierwszy błąd na liście. Opis to "wartość <" jest nieprawidłowa w atrybucie "". Po dwukrotnym kliknięciu błędu wskaźnik znajdzie odpowiednią lokalizację w kodzie. `<`Poprzednia wartość `Button` jest prawidłowa, a nie atrybut zgodnie z sugestią w komunikacie o błędzie. Jeśli zobaczysz poprzedni wiersz kodu, Zauważ, że brakuje cudzysłowu zamykającego dla atrybutu `Top` . Wpisz cudzysłów zamykający. Zwróć uwagę, że lista błędów w panelu **wyników** jest aktualizowana w celu odzwierciedlenia zmian.  
  
2. Kliknij dwukrotnie opis "0" jest nieprawidłowy na początku nazwy "". `Margin="0,149,0,0"` wydaje się być poprawnie sformułowane. Należy jednak zauważyć, że Kodowanie koloru `Margin` nie jest zgodne z innymi wystąpieniami `Margin` w kodzie. Ponieważ brakuje cudzysłowu zamykającego w poprzedniej parze nazwa/wartość ( `VerticalAlignment="Top` ), `Margin="` jest on odczytywany jako część wartości poprzedzającego atrybutu, a 0 jest odczytywany jako początek pary nazwa/wartość. Wpisz znaki cudzysłowu zamykającego `Top` . Lista błędów w panelu **wyników** jest aktualizowana w celu odzwierciedlenia zmian.  
  
3. Kliknij dwukrotnie pozostały błąd, "przycisk zamykający tag XML" jest niezgodny. " Wskaźnik znajduje się w tagu **siatki** zamykającej ( `</Grid>` ), sugerując, że błąd znajduje się wewnątrz `Grid` obiektu. Zwróć uwagę, że w drugim `Button` obiekcie brakuje taga zamykającego. Po dodaniu zamknięcia `/` lista paneli **wyników** zostanie zaktualizowana. Teraz, gdy te początkowe błędy zostały rozwiązane, zidentyfikowano dwa dodatkowe błędy.  
  
4. Kliknij dwukrotnie "zawartość elementu członkowskiego nie została rozpoznana lub jest niedostępna". `c`W `content` przypadku powinny być wielkie litery. Zamień małe litery "c" na wielkie litery "c".  
  
5. Kliknij dwukrotnie "Właściwość Mame" nie istnieje w `https://schemas.microsoft.com/winfx/2006/xaml` przestrzeni nazw ". "M" w "Mame" musi być "N". Zamień literę "M" na "N". Teraz, gdy można analizować kod XAML, aplikacja zostanie wyświetlona na powierzchni projektowej.  
  
    ![Debugowanie kodu XAML w Blend for Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Naciśnij kombinację klawiszy Ctrl + Shift + B, aby skompilować projekt i potwierdzić, że nie występują żadne pozostałe błędy.  
  
## <a name="debugging-in-visual-studio"></a>Debugowanie w Visual Studio  
 Możesz otworzyć [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekty w programie Visual Studio, aby łatwiej debugować kod w aplikacji. Aby otworzyć [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekt w programie Visual Studio, kliknij prawym przyciskiem myszy projekt w panelu **projekty** , a następnie kliknij polecenie **Edytuj w programie Visual Studio**. Po zakończeniu sesji debugowania w programie Visual Studio naciśnij kombinację klawiszy Ctrl + Shift + S, aby zapisać wszystkie zmiany, a następnie przełącz się z powrotem do [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] . Zostanie wyświetlony monit o ponowne załadowanie projektu. Kliknij przycisk **tak, aby** kontynuować pracę [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] .  
  
 Aby uzyskać więcej informacji na temat debugowania aplikacji, zobacz [debugowanie aplikacji ze sklepu Windows w programie Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441472.aspx).  
  
## <a name="getting-help"></a>Uzyskiwanie pomocy  
 Jeśli potrzebujesz więcej pomocy w debugowaniu [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] aplikacji, możesz wyszukać na [forach społeczności aplikacji ze sklepu Windows](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) pod kątem ogłoszeń związanych z Twoim problemem lub ogłosić pytanie.
