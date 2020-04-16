---
title: Debugowanie XAML w mieszance | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444625"
---
# <a name="debug-xaml-in-blend"></a>Debugowanie XAML w Blend
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą narzędzi [!INCLUDE[blend_first](../includes/blend-first-md.md)] można debugować kod XAML w aplikacji. Podczas tworzenia projektu wszelkie błędy są wyświetlane w panelu **Wyniki.** Kliknij dwukrotnie błąd, aby zlokalizować znaczniki związane z błędem. Jeśli potrzebujesz więcej miejsca do pracy, możesz ukryć panel **Wyniki,** naciskając klawisz F12.  
  
## <a name="syntax-errors"></a>Błędy składniowe  
 Błędy składni występują, jeśli kod XAML lub pliki dotyczące kodu nie są zgodne z regułami formatowania języka. Opis błędu może pomóc zrozumieć, jak go naprawić. Lista określa również nazwę pliku i numer wiersza, w którym występuje błąd. Błędy XAML są wyświetlane na karcie **Znaczniki** w panelu **Wyniki.**  
  
> [!TIP]
> XAML jest językiem znaczników opartym na XML i jest zgodny z regułami składni XML.  
  
 Oto niektóre typowe przyczyny błędów składni XAML:  
  
- Słowo kluczowe zostało błędnie napisane lub wielkość liter jest nieprawidłowa.  
  
- Brak cudzysłowów wokół atrybutów lub ciągów tekstowych.  
  
- W elemencie XAML brakuje znacznika zamykającego.  
  
- Element XAML istnieje w lokalizacji, w której nie jest dozwolone.  
  
  Aby uzyskać więcej informacji na temat typowej składni XAML, zobacz [Przewodnik po podstawowych składniach XAML](https://msdn.microsoft.com/library/windows/apps/hh700351.aspx).  
  
  Można również zidentyfikować i rozwiązać proste błędy składniowe, błędy kompilacji i błędy [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]w czasie wykonywania w pliku . Jednak błędy związane z kodem mogą być łatwiejsze do zidentyfikowania i rozwiązania w programie Visual Studio.  
  
### <a name="debugging-sample-xaml-code"></a>Przykładowy kod XAML debugowania  
 Poniższy przykład spowoduje przejście przez prostą sesję debugowania XAML w pliku [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
##### <a name="to-create-a-project"></a>Aby utworzyć projekt  
  
1. W [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]programie otwórz menu **Plik,** a następnie kliknij polecenie **Nowy projekt**.  
  
    W oknie dialogowym **Nowy projekt** po lewej stronie zostanie wyświetlona lista typów projektów. Po kliknięciu typu projektu szablony projektu, które są skojarzone z nim pojawiają się po prawej stronie.  
  
2. Na liście typów projektów kliknij pozycję **XAML (Sklep Windows)**.  
  
3. Na liście szablonów projektów kliknij pozycję **Pusta aplikacja**.  
  
4. W **Name** polu tekstowym `DebuggingSample`Nazwa wpisz .  
  
5. W polu tekstowym **Lokalizacja** sprawdź lokalizację projektu.  
  
6. Na liście **Język** kliknij pozycję **Visual C#,** a następnie kliknij przycisk **OK,** aby utworzyć projekt.  
  
7. Kliknij prawym przyciskiem myszy powierzchnię projektową, a następnie kliknij polecenie **Wyświetl źródło,** aby przełączyć się do widoku **podzielonego.**  
  
8. Skopiuj poniższy kod, klikając **łącze Kopiuj** w prawym górnym rogu kodu.  
  
   ```  
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>  
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>  
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>  
   </Grid>  
  
   ```  
  
9. Znajdź domyślną **siatkę**i wklej kod między otwierającymi i zamykającymi znacznikami **Siatki.** Po zakończeniu kod powinien wyglądać następująco:  
  
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
  
    Pojawi się komunikat o błędzie informujący, że nie można zbudować projektu, a w dolnej części aplikacji pojawi się panel **Wyniki** z listą błędów.  
  
    ![Debugowanie XAML w Blend dla Visual Studio](../debugger/media/blend-debugxaml-xaml.png "blend_debugXAML_XAML")  
  
### <a name="resolving-xaml-errors"></a>Rozwiązywanie błędów XAML  
 Po wykryciu błędów XAML powierzchnia projektowa wyświetla alert, że projekt zawiera nieprawidłowe znaczniki. Podczas rozwiązywania problemów lista błędów w panelu **Wyniki** jest aktualizowana. Po rozwiązaniu wszystkich błędów powierzchnia projektowa jest włączona, a aplikacja jest wyświetlana na powierzchni projektowej.  
  
##### <a name="to-resolve-the-xaml-errors"></a>Aby rozwiązać błędy XAML  
  
1. Kliknij dwukrotnie pierwszy błąd na liście. Opis jest "Wartość '<' nie jest prawidłowa w atrybucie." Po dwukrotnym kliknięciu błędu wskaźnik znajdzie odpowiednią lokalizację w kodzie. Poprzedni `<` `Button` jest prawidłowy, a nie atrybut, jak sugeruje się w komunikacie o błędzie. Jeśli spojrzysz na poprzedni wiersz kodu, zauważysz, że brakuje cudzysłowów zamykających dla atrybutu. `Top` Wpisz cudzysłowy zamknięcia. Należy zauważyć, że lista błędów w panelu **Wyniki** jest aktualizowana w celu odzwierciedlenia zmian.  
  
2. Kliknij dwukrotnie opis "'0' nie jest prawidłowy na początku nazwy." `Margin="0,149,0,0"`wydaje się być dobrze uformowany. Należy jednak zauważyć, że `Margin` kodowanie kolorami nie `Margin` pasuje do innych wystąpień w kodzie. Ponieważ w poprzednim parach nazw/wartości ( brakuje`VerticalAlignment="Top`końcowych `Margin="` cudzysłowów( ), odczytywany jest jako część wartości poprzedniego atrybutu, a 0 jest odczytywany jako początek pary nazwa/wartość. Wpisz cudzysłów `Top`zamykających dla . Lista błędów w panelu **Wyniki** zostanie zaktualizowana w celu odzwierciedlenia zmian.  
  
3. Kliknij dwukrotnie pozostały błąd, "Zamykający tag XML 'Button' jest niezgodny." Wskaźnik znajduje się przy **Grid** zamykaniu`</Grid>`tagu Siatki ( ), `Grid` co sugeruje, że błąd znajduje się wewnątrz obiektu. Należy zauważyć, `Button` że w drugim obiekcie brakuje tagu zamykającego. Po dodaniu `/`zamknięcia lista panelu **Wyniki** jest aktualizowana. Teraz, gdy te błędy początkowe zostały rozwiązane, zidentyfikowano dwa dodatkowe błędy.  
  
4. Kliknij dwukrotnie opcję "Zawartość elementu członkowskiego nie jest rozpoznawana lub niedostępna". In `c` `content` powinny być wielkie litery. Zastąp małe litery "c" na wielkie litery "c".  
  
5. Kliknij dwukrotnie opcję "Właściwość 'Mame' `https://schemas.microsoft.com/winfx/2006/xaml` nie istnieje w obszarze nazw." "M" w "Mame" powinien być "N". Wymień "M" na "N". Teraz, gdy kod XAML może być analizowany, aplikacja pojawia się na powierzchni projektowej.  
  
    ![Debugowanie XAML w programie Blend for Visual Studio](../debugger/media/blend-debugartboard-xaml.png "blend_debugArtboard_XAML")  
  
    Naciśnij klawisze Ctrl+Shift+B, aby utworzyć projekt i potwierdzić, że nie ma żadnych pozostałych błędów.  
  
## <a name="debugging-in-visual-studio"></a>Debugowanie w Visual Studio  
 Można otworzyć [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekty w programie Visual Studio, aby łatwiej debugować kod w aplikacji. Aby otworzyć [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] projekt w programie Visual Studio, kliknij go prawym przyciskiem myszy w panelu **Projekty,** a następnie kliknij polecenie **Edytuj w programie Visual Studio**. Po zakończeniu sesji debugowania w programie Visual Studio naciśnij klawisze Ctrl+Shift+S, [!INCLUDE[blend_subs](../includes/blend-subs-md.md)]aby zapisać wszystkie zmiany, a następnie przełącz się z powrotem do programu . Zostanie wyświetlony monit o ponowne załadowanie projektu. Kliknij **przycisk Tak, aby kontynuować** pracę w [!INCLUDE[blend_subs](../includes/blend-subs-md.md)].  
  
 Aby uzyskać więcej informacji na temat debugowania aplikacji, zobacz [Debugowanie aplikacji ze Sklepu Windows w programie Visual Studio](https://msdn.microsoft.com/library/windows/apps/hh441472.aspx).  
  
## <a name="getting-help"></a>Uzyskiwanie pomocy  
 Jeśli potrzebujesz więcej pomocy w [!INCLUDE[blend_subs](../includes/blend-subs-md.md)] debugowaniu aplikacji, możesz przeszukiwać [fora społeczności aplikacji ze Sklepu Windows](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) w poszukiwaniu postów związanych z problemem lub zadać pytanie.
