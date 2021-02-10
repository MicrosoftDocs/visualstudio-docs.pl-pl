---
title: Samouczek Projektant formularzy systemu Windows
description: Dowiedz się, jak utworzyć aplikację przy użyciu różnych narzędzi dostarczanych przez Projektant formularzy systemu Windows. Aplikacja jest kontrolką niestandardową, która używa wielu dostępnych funkcji układu.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 5803530290988affd6cfbb8342f3b1d545238985
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947853"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>Samouczek: wprowadzenie do Projektant formularzy systemu Windows

Projektant formularzy systemu Windows udostępnia wiele narzędzi do kompilowania aplikacji Windows Forms. W tym artykule przedstawiono sposób tworzenia aplikacji przy użyciu różnych narzędzi udostępnianych przez projektanta, w tym następujących zadań:

- Rozmieść kontrolki za pomocą linii wyrównania.
- Wykonywanie zadań projektanta przy użyciu tagów inteligentnych.
- Ustaw marginesy i dopełnienie dla kontrolek.
- Rozmieść formanty przy użyciu <xref:System.Windows.Forms.TableLayoutPanel> kontrolki.
- Podziel układ formantu przy użyciu <xref:System.Windows.Forms.SplitContainer> kontrolki.
- Przejdź do układu przy użyciu okna konspektu dokumentu.
- Kontrolki położenia z wyświetlanymi informacjami o rozmiarze i lokalizacji.
- Ustaw wartości właściwości przy użyciu okno Właściwości.

Po zakończeniu będziesz mieć kontrolkę niestandardową, która została przedstawiona przy użyciu wielu funkcji układu dostępnych w Projektant formularzy systemu Windows. Ta kontrolka implementuje interfejs użytkownika (UI) dla prostego kalkulatora. Na poniższej ilustracji przedstawiono ogólny układ kontrolki Kalkulator:

![Interfejs użytkownika kalkulatora przewodnika](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Tworzenie projektu kontrolki niestandardowej

Pierwszym krokiem jest utworzenie projektu kontrolki DemoCalculator.

1. Otwórz program Visual Studio i Utwórz nowy projekt **biblioteki formantów Windows Forms** . Nazwij projekt **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Szablon biblioteki formantów Windows Forms w programie Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Aby zmienić nazwę pliku, w **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **UserControl1. vb** lub **UserControl1.cs**, wybierz polecenie **Zmień** nazwę, a następnie zmień wartość w polu Nazwa pliku na DemoCalculator. vb lub DemoCalculator.cs. Wybierz opcję **tak** , gdy zostanie wyświetlony monit o zmianę nazwy wszystkich odwołań do elementu kodu "UserControl1".

Projektant formularzy systemu Windows pokazuje powierzchnię projektanta dla formantu DemoCalculator. W tym widoku można graficznie zaprojektować wygląd kontrolki, wybierając formanty i składniki z przybornika i umieszczając je na powierzchni projektanta. Aby uzyskać więcej informacji o kontrolkach niestandardowych, zobacz [odmian niestandardowych kontrolek](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Projektowanie układu formantu

Kontrolka DemoCalculator zawiera kilka kontrolek Windows Forms. Ta procedura polega na rozmieszczeniu formantów przy użyciu Projektant formularzy systemu Windows.

1. W Projektant formularzy systemu Windows Zmień formant DemoCalculator na większy rozmiar, wybierając uchwyt zmiany rozmiaru w prawym dolnym rogu i przeciągając go w dół i w prawo. W prawym dolnym rogu programu Visual Studio Znajdź informacje o rozmiarze i lokalizacji dla kontrolek. Ustaw rozmiar kontrolki na szerokość 500 i wysokość 400, oglądając informacje o rozmiarze podczas zmiany rozmiaru formantu.

2. W **przyborniku** wybierz węzeł **kontenery** , aby go otworzyć. Wybierz formant **SplitContainer** i przeciągnij go na powierzchnię projektanta.

   `SplitContainer`Znajduje się na powierzchni projektanta formantu DemoCalculator.

    > [!TIP]
    > Dopasowuje `SplitContainer` rozmiar formantu do rozmiaru formantu DemoCalculator. Sprawdź okno **Właściwości** , aby wyświetlić ustawienia właściwości `SplitContainer` formantu. Znajdź <xref:System.Windows.Forms.SplitContainer.Dock%2A> Właściwość. Jego wartość to [dockname. Fill](xref:System.Windows.Forms.DockStyle.Fill), co oznacza, że `SplitContainer` kontrolka będzie zawsze sama zmieniać rozmiar do granic formantu DemoCalculator. Zmień rozmiar kontrolki DemoCalculator, aby sprawdzić to zachowanie.

3. W oknie **Właściwości** Zmień wartość <xref:System.Windows.Forms.SplitContainer.Dock%2A> właściwości na `None` .

    `SplitContainer`Kontrolka zmniejszy się do rozmiaru domyślnego i nie jest już zgodna z rozmiarem formantu DemoCalculator.

4. Wybierz symbol tagu inteligentnego ( ![ symbol tagu inteligentnego ](media/smart-tag-glyph.gif) ) w prawym górnym rogu `SplitContainer` kontrolki. Wybierz pozycję **Zadokuj w kontenerze nadrzędnym** , aby ustawić `Dock` Właściwość na `Fill` .

    `SplitContainer`Kontrolka jest zadokowana do granic formantu DemoCalculator.

    > [!NOTE]
    > Kilka formantów oferuje inteligentne Tagi do ułatwienia projektowania. Aby uzyskać więcej informacji, zobacz [Przewodnik: wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Wybierz obramowanie pionowe między panelami i przeciągnij je w prawo, tak aby większość miejsca była wykonywana przez lewy panel.

    `SplitContainer`Dzieli formant DemoCalculator na dwa panele z rozdzielonym obramowaniem ruchomym. Panel po lewej stronie będzie zawierał przyciski kalkulatora i wyświetlacz, a panel po prawej stronie wyświetli rekord operacji arytmetycznych wykonywanych przez użytkownika.

6. W oknie **Właściwości** Zmień wartość `BorderStyle` właściwości na `Fixed3D` .

7. W **przyborniku** wybierz węzeł **Formanty standardowe** , aby go otworzyć. Zaznacz `ListView` kontrolkę i przeciągnij ją do prawego panelu `SplitContainer` formantu.

8. Wybierz `ListView` symbol tagu inteligentnego kontrolki. W panelu tagów inteligentnych Zmień `View` ustawienie na `Details` .

9. W panelu tagów inteligentnych wybierz pozycję **Edytuj kolumny**.

   Zostanie otwarte okno dialogowe **Edytor kolekcji ColumnHeader** .

10. W oknie dialogowym **Edytor kolekcji ColumnHeader** wybierz pozycję **Dodaj** , aby dodać kolumnę do `ListView` kontrolki. Zmień wartość `Text` Właściwości Column na **History**. Wybierz **przycisk OK** , aby utworzyć kolumnę.

11. W panelu tagów inteligentnych wybierz pozycję **Dock w kontenerze nadrzędnym**, a następnie wybierz symbol tagu inteligentnego, aby zamknąć Panel tagów inteligentnych.

12. Z **przybornika** węzłów **kontenerów** przeciągnij `TableLayoutPanel` formant do lewego panelu `SplitContainer` kontrolki.

    `TableLayoutPanel`Kontrolka pojawia się na powierzchni projektanta z otwartym panelem tagów inteligentnych. `TableLayoutPanel`Formant rozmieszcza swoje kontrolki podrzędne w siatce. `TableLayoutPanel`Kontrolka będzie zawierać DemoCalculator i przyciski kontrolki. Aby uzyskać więcej informacji, zobacz [Przewodnik: porządkowanie formantów przy użyciu TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Wybierz pozycję **Edytuj wiersze i kolumny** w panelu tagów inteligentnych.

    Zostanie otwarte okno dialogowe **Style kolumn i wierszy** .

14. Wybierz przycisk **Dodaj** , dopóki nie zostaną wyświetlone pięć kolumn. Zaznacz wszystkie pięć kolumn, a następnie w polu **Typ rozmiaru** wybierz pozycję **procent** . Ustaw wartość **procentową** na **20**. To ustawienie określa, że każda kolumna ma taką samą szerokość.

15. W obszarze **Pokaż** wybierz pozycję **wiersze**.

16. Wybierz pozycję **Dodaj** , dopóki nie zostaną wyświetlone pięć wierszy. Zaznacz wszystkie pięć wierszy i wybierz **procent** w polu **Typ rozmiaru** . Ustaw wartość **procentową** na **20**. To ustawia każdy wiersz na taką samą wysokość.

17. Wybierz **przycisk OK** , aby zaakceptować zmiany, a następnie wybierz symbol tagu inteligentnego, aby zamknąć Panel tagów inteligentnych.

18. W oknie **Właściwości** Zmień wartość `Dock` właściwości na `Fill` .

## <a name="populate-the-control"></a>Wypełnij kontrolkę

Teraz, gdy układ kontrolki jest skonfigurowany, można wypełnić formant DemoCalculator z przyciskami i ekranem.

1. W **przyborniku** wybierz `TextBox` ikonę kontrolki.

   `TextBox`Kontrolka jest umieszczana w pierwszej komórce `TableLayoutPanel` formantu.

2. W oknie **Właściwości** Zmień wartość `TextBox` Właściwości ColumnSpan kontrolki na **5**.

   `TextBox`Kontrolka przechodzi do położenia, które jest wyśrodkowane w jego wierszu.

3. Zmień wartość `TextBox` właściwości kontrolki `Anchor` na `Left` , `Right` .

   `TextBox`Kontrolka rozszerza się w poziomie, aby obejmowała wszystkie pięć kolumn.

4. Zmień wartość `TextBox` właściwości kontrolki `TextAlign` na `Right` .

5. W oknie **Właściwości** rozwiń `Font` węzeł właściwości. Ustaw wartość `Size` na **14**, a `Bold` dla  `TextBox` kontrolki wartość true.

6. Zaznacz `TableLayoutPanel` kontrolkę.

7. W **przyborniku** wybierz `Button` ikonę.

   `Button`Kontrolka jest umieszczana w następnej otwartej komórce `TableLayoutPanel` formantu.

8. W **przyborniku** wybierz `Button` ikonę cztery razy, aby wypełnić drugi wiersz `TableLayoutPanel` formantu.

9. Zaznacz wszystkie pięć `Button` kontrolek, zaznaczając je, przytrzymując klawisz **SHIFT** . Naciśnij klawisz **Ctrl** + **C** , aby skopiować `Button` kontrolki do Schowka.

10. Naciśnij **klawisze CTRL +** +  trzy razy, aby wkleić kopie `Button` formantów do pozostałych wierszy `TableLayoutPanel` formantu.

11. Zaznacz wszystkie 20 `Button` formantów, zaznaczając je, przytrzymując klawisz **SHIFT** .

12. W oknie **Właściwości** Zmień wartość `Dock` właściwości na `Fill` .

    Wszystkie `Button` kontrolki są zadokowane, aby wypełnić ich komórki.

13. W oknie **Właściwości** rozwiń `Margin` węzeł właściwości. Ustaw wartość `All` na **5**.

    Rozmiar wszystkich `Button` formantów jest mniejszy, aby utworzyć większy margines między nimi.

14. Wybierz pozycję **button10** i **button20**, a następnie naciśnij klawisz **delete** , aby usunąć je z układu.

15. Wybierz pozycję **Button5** i **button15**, a następnie zmień wartość `RowSpan` właściwości na **2**. Będą to **jasne** i **=** przyciski dla kontrolki DemoCalculator.

## <a name="use-the-document-outline-window"></a>Korzystanie z okna konspektu dokumentu

Gdy kontrolka lub formularz zostanie wypełniony kilkoma kontrolkami, łatwiej jest nawigować po stronie układu przy użyciu okna konspektu dokumentu.

1. Na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Konspekt dokumentu** systemu Windows.

   Okno Konspekt dokumentu zawiera widok drzewa formantu DemoCalculator i jego kontrolki składowe. Kontrolki kontenerów, takie jak `SplitContainer` Pokaż ich formanty podrzędne, jako podwęzły w drzewie. Możesz również zmienić nazwy kontrolek w miejscu przy użyciu okna Konspekt dokumentu.

2. W oknie **Konspekt dokumentu** kliknij prawym przyciskiem myszy pozycję **Button1**, a następnie wybierz polecenie **Zmień nazwę**. Zmień jej nazwę na sevenButton.

3. Korzystając z okna **Konspekt dokumentu** , Zmień nazwę `Button` kontrolek z nazwy wygenerowanej przez projektanta na nazwę produkcyjną zgodnie z następującą listą:

   - Button1 do **sevenButton**

   - Button2 do **eightButton**

   - button3 do **nineButton**

   - button4 do **divisionButton**

   - Button5 do **clearButton**

   - button6 do **fourButton**

   - button7 do **fiveButton**

   - button8 do **sixButton**

   - button9 do **multiplicationButton**

   - button11 do **oneButton**

   - button12 do **twoButton**

   - button13 do **threeButton**

   - button14 do **subtractionButton**

   - button15 do **equalsButton**

   - button16 do **zeroButton**

   - button17 do **changeSignButton**

   - button18 do **decimalButton**

   - button19 do **additionButton**

4. Korzystając z okna **Konspekt dokumentu** i **Właściwości** , Zmień `Text` wartość właściwości dla każdej `Button` nazwy kontrolki zgodnie z następującą listą:

   - Zmień właściwość Text formantu sevenButton na **7**

   - Zmień właściwość Text formantu eightButton na **8**

   - Zmień właściwość Text formantu nineButton na **9**

   - Zmień właściwość Text formantu divisionButton na **/** (ukośnik)

   - Zmień właściwość Text formantu clearButton na **Clear**

   - Zmień właściwość Text formantu fourButton na **4**

   - Zmień właściwość Text formantu fiveButton na **5**

   - Zmień właściwość Text formantu sixButton na **6**

   - Zmień właściwość Text formantu multiplicationButton na **\*** (gwiazdka)

   - Zmień właściwość Text formantu oneButton na **1**

   - Zmień właściwość Text formantu twoButton na **2**

   - Zmień właściwość Text formantu threeButton na **3**

   - Zmień właściwość Text formantu subtractionButton na **-** (łącznik)

   - Zmień właściwość tekstu formantu equalsButton na **=** (znak równości)

   - Zmień właściwość Text formantu zeroButton na **0**

   - Zmień właściwość Text formantu changeSignButton na **+/-**

   - Zmień właściwość Text formantu decimalButton na **.** (kropka)

   - Zmień właściwość Text formantu additionButton na **+** (znak plus)

5. Na powierzchni projektanta zaznacz wszystkie `Button` kontrolki, zaznaczając je, przytrzymując klawisz **SHIFT** .

6. W oknie **Właściwości** rozwiń `Font` węzeł właściwości. Ustaw wartość `Size` na **14** i ustaw dla `Bold` wszystkich kontrolek opcję **true** `Button` .

Spowoduje to zakończenie projektowania formantu DemoCalculator. To wszystko, co ma na celu dostarczenie logiki kalkulatora.

## <a name="implement-event-handlers"></a>Implementowanie obsługi zdarzeń

Przyciski w kontrolce DemoCalculator mają procedury obsługi zdarzeń, których można użyć do wdrożenia większości logiki kalkulatora. Projektant formularzy systemu Windows umożliwia zaimplementowanie wycinków wszystkich programów obsługi zdarzeń dla wszystkich przycisków z jednym zaznaczeniem.

1. Na powierzchni projektanta zaznacz wszystkie `Button` kontrolki, zaznaczając je, przytrzymując klawisz **SHIFT** .

2. Wybierz jedną z `Button` kontrolek.

   Edytor kodu zostanie otwarty dla programów obsługi zdarzeń generowanych przez projektanta.

## <a name="test-the-control"></a>Testowanie kontrolki

Ponieważ kontrolka DemoCalculator dziedziczy z <xref:System.Windows.Forms.UserControl> klasy, można testować jej zachowanie z **kontenerem test UserControl**. Aby uzyskać więcej informacji, zobacz [jak: testowanie zachowania elementu UserControl w czasie wykonywania](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić kontrolkę DemoCalculator w **kontenerze Test UserControl**.

2. Zaznacz obramowanie między `SplitContainer` panelami i przeciągnij je w lewo i w prawo. `TableLayoutPanel`I wszystkie jego kontrolki podrzędne zmienią rozmiar tak, aby mieściły się w dostępnym miejscu.

3. Po zakończeniu testowania kontrolki wybierz pozycję **Zamknij**.

## <a name="use-the-control-on-a-form"></a>Korzystanie z kontrolki w formularzu

Formant DemoCalculator może być używany w innych formantach złożonych lub w formularzu. Poniższa procedura zawiera opis sposobu korzystania z niego.

### <a name="create-the-project"></a>Tworzenie projektu

Pierwszym krokiem jest utworzenie projektu aplikacji. Ten projekt będzie używany do kompilowania aplikacji, która wyświetla kontrolkę niestandardową.

1. Utwórz nowy projekt **aplikacji Windows Forms** i nadaj mu nazwę **DemoCalculatorTest**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **DemoCalculatorTest** , a następnie wybierz pozycję **Dodaj odwołanie** , aby otworzyć okno dialogowe **Dodawanie odwołania** .

3. Przejdź do karty **projekty** , a następnie wybierz projekt DemoCalculatorLib, aby dodać odwołanie do projektu testowego.

4. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **DemoCalculatorTest**, a następnie wybierz pozycję **Ustaw jako projekt startowy**.

5. W Projektant formularzy systemu Windows Zwiększ rozmiar formularza do około **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Użyj kontrolki w układzie formularza

Aby użyć kontrolki DemoCalculator w aplikacji, należy ją umieścić w formularzu.

1. W **przyborniku** rozwiń węzeł **składniki DemoCalculatorLib** .

2. Przeciągnij formant **DemoCalculator** z **przybornika** do formularza. Przesuń formant do lewego górnego rogu formularza. Gdy kontrolka zbliża się do obramowania formularza, zostanie wyświetlona *linii wyrównania* . Linii wyrównania wskazują odległość `Padding` właściwości formularza i właściwości kontrolki `Margin` . Umieść formant w lokalizacji wskazanej przez linii wyrównania.

   Aby uzyskać więcej informacji, zobacz [Przewodnik: porządkowanie formantów przy użyciu linii wyrównania](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Przeciągnij `Button` kontrolkę z **przybornika** i upuść ją na formularzu.

4. Przenieś `Button` kontrolkę wokół kontrolki DemoCalculator i obserwuj, gdzie pojawia się linii wyrównania. Możesz precyzyjnie dostosować kontrolki za pomocą tej funkcji. Usuń `Button` kontrolkę po zakończeniu.

5. Kliknij prawym przyciskiem myszy formant DemoCalculator, a następnie wybierz polecenie **Właściwości**.

6. Zmień wartość `Dock` właściwości na `Fill` .

7. Wybierz formularz, a następnie rozwiń `Padding` węzeł właściwości. Zmień wartość **wszystkie** na **20**.

   Rozmiar formantu DemoCalculator jest zmniejszany w celu uwzględnienia nowej `Padding` wartości formularza.

8. Zmień rozmiar formularza, przeciągając różne uchwyty zmiany rozmiaru na różne pozycje. Obserwuj, jak zmieniany jest rozmiar kontrolki DemoCalculator.

## <a name="next-steps"></a>Następne kroki

W tym artykule przedstawiono sposób konstruowania interfejsu użytkownika dla prostego kalkulatora. Aby kontynuować, możesz przedłużyć jego funkcjonalność, implementując logikę kalkulatora, a następnie [publikując aplikację przy użyciu technologii ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Lub przejdź do innego samouczka, w którym [tworzysz Podgląd obrazów przy użyciu Windows Forms](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Zobacz też

- [formanty Formularzy systemu Windows](/dotnet/framework/winforms/controls/)
- [Ułatwienia dostępu dla formantów Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Publikowanie przy użyciu technologii ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
