---
title: Samouczek projektanta formularzy systemu Windows
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 07526637f2d8083f37f55aa3da36bb01479db087
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589841"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>Przewodnik: Wprowadzenie do programu Windows Forms Designer

Projektant formularzy systemu Windows udostępnia wiele narzędzi do tworzenia aplikacji Windows Forms. W tym artykule pokazano, jak utworzyć aplikację przy użyciu różnych narzędzi dostarczonych przez projektanta, w tym następujących zadań:

- Rozmieść formanty za pomocą linii przyciągania.
- Wykonywanie zadań projektanta przy użyciu tagów inteligentnych.
- Ustaw marginesy i dopełnienie dla formantów.
- Rozmieść <xref:System.Windows.Forms.TableLayoutPanel> formanty za pomocą formantu.
- Partycjonowanie układu formantu <xref:System.Windows.Forms.SplitContainer> przy użyciu formantu.
- Nawigowanie po układzie za pomocą okna Konspekt dokumentu.
- Elementy sterujące położeniem z wyświetlaniem informacji o rozmiarze i lokalizacji.
- Ustaw wartości właściwości za pomocą okna Właściwości.

Po zakończeniu będziesz mieć formant niestandardowy, który został złożony przy użyciu wielu funkcji układu dostępnych w Projektancie formularzy systemu Windows. Ten formant implementuje interfejs użytkownika (UI) dla prostego kalkulatora. Na poniższej ilustracji przedstawiono ogólny układ formantu kalkulatora:

![Interfejs użytkownika kalkulatora przewodnika z przewodnikiem](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Tworzenie niestandardowego projektu sterowania

Pierwszym krokiem jest utworzenie projektu kontroli DemoCalculator.

1. Otwórz program Visual Studio i utwórz nowy projekt **biblioteki kontroli formularzy systemu Windows.** Nazwij projekt **DemoCalculatorLib**.

   ::: moniker range=">=vs-2019"

   ![Szablon biblioteki formantu formularzy systemu Windows w programie Visual Studio 2019](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Aby zmienić nazwę pliku, w **Eksploratorze rozwiązań**wybierz prawym przyciskiem wyboru **UserControl1.vb** lub **UserControl1.cs**, wybierz **pozycję Zmień nazwę**i zmień nazwę pliku na DemoCalculator.vb lub DemoCalculator.cs. Wybierz **tak,** gdy pojawi się pytanie, czy chcesz zmienić nazwę wszystkich odwołań do elementu kodu "UserControl1".

Projektant formularzy systemu Windows pokazuje powierzchnię projektanta dla kontrolki DemoCalculator. W tym widoku można graficznie zaprojektować wygląd formantu, wybierając formanty i komponenty z przybornika i umieszczając je na powierzchni projektanta. Aby uzyskać więcej informacji na temat formantów niestandardowych, zobacz [Odmiany formantów niestandardowych](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Projektowanie układu sterowania

Kontrolka DemoCalculator zawiera kilka formantów formularzy systemu Windows. W tej procedurze rozmieść formanty za pomocą projektanta formularzy systemu Windows.

1. W Projektancie formularzy systemu Windows zmień kontrolkę DemoCalculator na większy, wybierając uchwyt zmiany rozmiaru w prawym dolnym rogu i przeciągając go w dół i w prawo. W prawym dolnym rogu programu Visual Studio znajdź informacje o rozmiarze i lokalizacji dla formantów. Ustaw rozmiar formantu na szerokość 500 i wysokość 400, obserwując informacje o rozmiarze podczas ponownego rozmiaru formantu.

2. W **przyborniku**wybierz węzeł **Kontenery,** aby go otworzyć. Wybierz kontrolkę **SplitContainer** i przeciągnij ją na powierzchnię projektanta.

   Jest `SplitContainer` umieszczony na powierzchni projektanta kontrolki DemoCalculator.

    > [!TIP]
    > Rozmiary `SplitContainer` formantu do rozmiaru DemoCalculator kontroli. Spójrz na **właściwości** okna, aby wyświetlić `SplitContainer` ustawienia właściwości formantu. Znajdź <xref:System.Windows.Forms.SplitContainer.Dock%2A> nieruchomość. Jego wartość jest [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill) `SplitContainer` , co oznacza, że formant zawsze rozmiar się do granic DemoCalculator kontroli. Ponownie rozmiar DemoCalculator kontroli, aby sprawdzić to zachowanie.

3. W oknie **Właściwości** zmień wartość właściwości <xref:System.Windows.Forms.SplitContainer.Dock%2A> na `None`.

    Formant `SplitContainer` zmniejsza się do jego domyślnego rozmiaru i nie jest już zgodny z rozmiarem DemoCalculator kontroli.

4. Wybierz glif tagu![inteligentnego (Smart Tag Glyph)](media/smart-tag-glyph.gif) `SplitContainer` w prawym górnym rogu formantu. Wybierz **dock w kontenerze nadrzędnym,** `Dock` aby ustawić właściwość na `Fill`.

    Formant `SplitContainer` dokuje do granic formantu DemoCalculator.

    > [!NOTE]
    > Kilka elementów sterujących oferuje tagi inteligentne ułatwiające projektowanie. Aby uzyskać więcej informacji, zobacz [Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w formantach formularzy systemu Windows](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Zaznacz pionowe obramowanie między panelami i przeciągnij je w prawo, tak aby większość miejsca zajęta przez lewy panel.

    Kontrolka `SplitContainer` DemoCalculator dzieli się na dwa panele z ruchomą krawędzią oddzielającą je. Panel po lewej stronie będzie trzymał przyciski kalkulatora i wyświetlacz, a panel po prawej stronie wyświetli zapis operacji arytmetycznych wykonywanych przez użytkownika.

6. W oknie **Właściwości** zmień wartość właściwości `BorderStyle` na `Fixed3D`.

7. W **przyborniku**wybierz węzeł **Typowe formanty,** aby go otworzyć. Wybierz `ListView` formant i przeciągnij go `SplitContainer` do prawego panelu formantu.

8. Wybierz `ListView` glif tagu inteligentnego formantu. W panelu tagów inteligentnych `Details`zmień ustawienie na `View` .

9. W panelu tagów inteligentnych wybierz pozycję **Edytuj kolumny**.

   Zostanie otwarte okno dialogowe **Edytor kolekcji ColumnHeader.**

10. W oknie dialogowym **Edytor kolekcji ColumnHeader** wybierz `ListView` pozycję **Dodaj,** aby dodać kolumnę do formantu. Zmień wartość `Text` właściwości kolumny na **Historia**. Wybierz **przycisk OK,** aby utworzyć kolumnę.

11. W panelu tagów inteligentnych wybierz pozycję **Dock w kontenerze nadrzędnym,** a następnie wybierz glif tagu inteligentnego, aby zamknąć panel tagów inteligentnych.

12. Z **przybornika węzła** `TableLayoutPanel` `SplitContainer` **Kontenery** przeciągnij formant do lewego panelu formantu.

    Formant pojawia się na powierzchni projektanta `TableLayoutPanel` z otwartym panelem tagów inteligentnych. Formant `TableLayoutPanel` rozmieszcza jego podrzędnych formantów w siatce. Formant `TableLayoutPanel` będzie zawierać democalculator formantu wyświetlacz i przyciski. Aby uzyskać więcej informacji, zobacz [Instruktaż: Rozmieszczanie formantów przy użyciu panelu TableLayoutPanel](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Wybierz **pozycję Edytuj wiersze i kolumny** na panelu tagów inteligentnych.

    Zostanie otwarte okno dialogowe **Style kolumn i wierszy.**

14. Wybierz przycisk **Dodaj,** aż pojawi się pięć kolumn. Zaznacz wszystkie pięć kolumn, a następnie wybierz **pozycję Procent** w polu **Typ rozmiaru.** Ustaw wartość **Procent** na **20**. Spowoduje to ustawienie każdej kolumny na taką samą szerokość.

15. W obszarze **Pokaż**wybierz pozycję **Wiersze**.

16. Wybierz **pozycję Dodaj,** aż zostanie wyświetlonych pięć wierszy. Zaznacz wszystkie pięć wierszy i wybierz **procent** w polu **Typ rozmiaru.** Ustaw wartość **Procent** na **20**. Spowoduje to ustawienie każdego wiersza na tej samej wysokości.

17. Wybierz **przycisk OK,** aby zaakceptować zmiany, a następnie wybierz glif tagu inteligentnego, aby zamknąć panel tagów inteligentnych.

18. W oknie **Właściwości** zmień wartość właściwości `Dock` na `Fill`.

## <a name="populate-the-control"></a>Wypełnij kontrolka

Teraz, gdy układ formantu jest skonfigurowany, można wypełnić DemoCalculator kontrolki za pomocą przycisków i wyświetlacza.

1. W **przyborniku**kliknij `TextBox` dwukrotnie ikonę formantu.

   Formant `TextBox` jest umieszczany w `TableLayoutPanel` pierwszej komórce formantu.

2. W oknie **Właściwości** zmień wartość właściwości `TextBox` ColumnSpan formantu na **5**.

   Formant `TextBox` przesuwa się do pozycji, która jest wyśrodkowany w jego wierszu.

3. Zmień `TextBox` wartość `Anchor` właściwości formantu `Left`na `Right`, .

   Formant `TextBox` rozwija się poziomo, aby objąć wszystkie pięć kolumn.

4. Zmień wartość `TextBox` `TextAlign` właściwości formantu `Right`na .

5. W oknie **Właściwości** rozwiń `Font` węzeł właściwości. Ustaw `Size` **na 14** `Bold` i ustawiono `TextBox` wartość **true** dla formantu.

6. Wybierz `TableLayoutPanel` formant.

7. W **przyborniku**kliknij `Button` dwukrotnie ikonę.

   Formant `Button` jest umieszczany w następnej otwartej komórce formantu. `TableLayoutPanel`

8. W **przyborniku**kliknij `Button` dwukrotnie ikonę jeszcze cztery razy, `TableLayoutPanel` aby wypełnić drugi wiersz formantu.

9. Zaznacz wszystkie `Button` pięć kontrolek, zaznaczając je przy jednoczesnym przytrzymywanie klawisza **Shift.** Naciśnij klawisz **Ctrl**+ `Button` **C,** aby skopiować kontrolki do schowka.

10. Naciśnij klawisz **Ctrl**+**V** trzy razy, `Button` aby wkleić `TableLayoutPanel` kopie formantów do pozostałych wierszy formantu.

11. Zaznacz wszystkie 20 `Button` formantów, zaznaczając je przy jednoczesnym przytrzymywanie klawisza **Shift.**

12. W oknie **Właściwości** zmień wartość właściwości `Dock` na `Fill`.

    Wszystkie `Button` formanty dokują, aby wypełnić komórki zawierające.

13. W oknie **Właściwości** rozwiń `Margin` węzeł właściwości. Ustaw wartość `All` **5**.

    Wszystkie `Button` formanty są o mniejszej wielkości, aby utworzyć większy margines między nimi.

14. Wybierz **przycisk10** i **button20**, a następnie naciśnij klawisz **Delete,** aby usunąć je z układu.

15. Wybierz **button5** i **button15**, a `RowSpan` następnie zmień wartość ich właściwości na **2**. Będą to **wyczyść** i **=** przyciski dla kontroli DemoCalculator.

## <a name="use-the-document-outline-window"></a>Używanie okna Konspekt dokumentu

Gdy formant lub formularz jest wypełniony kilkoma formantami, może być łatwiej poruszać się po układzie za pomocą okna Konspekt dokumentu.

1. Na pasku menu wybierz pozycję **Wyświetl** > inny**konspekt dokumentu****systemu Windows** > .

   Okno Konspekt dokumentu pokazuje widok drzewa DemoCalculator kontroli i jego formantów składnika. Formanty `SplitContainer` kontenera, takie jak pokaż ich formantów podrzędnych jako subnodes w drzewie. Można również zmienić nazwy formantów w miejscu za pomocą okna Konspekt dokumentu.

2. W oknie **Konspekt dokumentu** wybierz **prawym przyciskiem1**, a następnie wybierz pozycję **Zmień nazwę**. Zmień jego nazwę na sevenButton.

3. Za pomocą okna **Konspekt dokumentu** zmień nazwę `Button` formantów z nazwy wygenerowanej przez projektanta na nazwę produkcji zgodnie z następującą listą:

   - button1 do **sevenButton**

   - button2 do **eightButton**

   - button3 do **nineButton**

   - button4 do **podziałuButton**

   - button5, aby **wyczyścićbutton**

   - button6 do **fourButton**

   - button7 do **fiveButton**

   - button8 do **sześciuButton**

   - button9 do **mnożeniaButton**

   - button11 do **jednegoButton**

   - button12 do **twoButton**

   - button13 do **threeButton**

   - button14 do **odejmowaniaButton**

   - button15 do **równegoButton**

   - button16 do **zeraButton**

   - button17, aby **zmienić przycisksignbutton**

   - button18 do **przecinka.**

   - button19 do **dodatkuButton**

4. Za pomocą okien **Konspekt** `Text` dokumentu i `Button` **Właściwości** zmień wartość właściwości dla każdej nazwy formantu zgodnie z następującą listą:

   - Zmienianie właściwości tekstu formantu sevenButton na **7**

   - Zmienianie właściwości tekstu formantu eightButton na **8**

   - Zmienianie właściwości tekstu formantu nineButton na **9**

   - Zmienianie właściwości tekstu formantu formantu divisionButton na **/** (ukośnik do przodu)

   - Zmienianie właściwości tekstu formantu clearButton na **Wyczyść**

   - Zmienianie właściwości tekstu formantu fourButton na **4**

   - Zmienianie właściwości tekstu formantu fiveButton na **5**

   - Zmienianie właściwości tekstu formantu sixButton na **6**

   - Zmienianie właściwości tekstu sterującego mnożeniabutton na **\*** (gwiazdka)

   - Zmienianie właściwości tekstu formantu oneButton na **1**

   - Zmienianie właściwości tekstu formantu twoButton na **2**

   - Zmienianie właściwości tekstu formantu threeButton na **3**

   - Zmienianie właściwości tekstu sterującego przycisku odejmowania na **-** (łącznik)

   - Zmień właściwość tekstu formantu **=** equalsButton na (znak równości)

   - Zmienianie właściwości tekstu formantu zeroButton na **0**

   - Zmienianie właściwości tekstu formantu changeSignButton na**+/-**

   - Zmień właściwość tekstu sterującego z przecinka na **.** (kropka)

   - Zmień właściwość tekstu formantu additionButton na **+** (plus znak)

5. Na powierzchni projektanta zaznacz `Button` wszystkie formanty, zaznaczając je przy jednoczesnym przytrzymywanie klawisza **Shift.**

6. W oknie **Właściwości** rozwiń `Font` węzeł właściwości. Ustaw `Size` **wartość 14** `Bold` i ustawioną `Button` na wartość **true** dla wszystkich formantów.

To kończy projekt DemoCalculator kontroli. Pozostaje tylko podać logikę kalkulatora.

## <a name="implement-event-handlers"></a>Implementowanie programów obsługi zdarzeń

Przyciski w democalculator kontroli mają programy obsługi zdarzeń, które mogą służyć do implementacji wiele logiki kalkulatora. Projektant formularzy systemu Windows umożliwia zaimplementowanie wycinków wszystkich programów obsługi zdarzeń dla wszystkich przycisków za pomocą jednego dwukrotnego kliknięcia.

1. Na powierzchni projektanta zaznacz `Button` wszystkie formanty, zaznaczając je przy jednoczesnym przytrzymywanie klawisza **Shift.**

2. Kliknij dwukrotnie jeden `Button` z formantów.

   Edytor kodu otwiera programy obsługi zdarzeń generowane przez projektanta.

## <a name="test-the-control"></a>Przetestuj formant

Ponieważ DemoCalculator kontroli dziedziczy <xref:System.Windows.Forms.UserControl> z klasy, można przetestować jego zachowanie za pomocą **UserControl Test Container**. Aby uzyskać więcej informacji, zobacz [Jak: Testowanie zachowania w czasie wykonywania UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. Naciśnij **klawisz F5,** aby utworzyć i uruchomić kontrolę DemoCalculator w **kontenerze testowym UserControl**.

2. Zaznacz obramowanie `SplitContainer` między panelami i przeciągnij je w lewo i w prawo. I `TableLayoutPanel` wszystkie jego elementy sterujące podrzędne zmieścić się, aby zmieścić się w dostępnej przestrzeni.

3. Po zakończeniu testowania formantu wybierz przycisk **Zamknij**.

## <a name="use-the-control-on-a-form"></a>Używanie formantu w formularzu

Formant DemoCalculator może być używany w innych formantów złożonych lub w formularzu. W poniższej procedurze opisano sposób korzystania z niego.

### <a name="create-the-project"></a>Tworzenie projektu

Pierwszym krokiem jest utworzenie projektu aplikacji. Użyjesz tego projektu do utworzenia aplikacji, która pokazuje formant niestandardowy.

1. Utwórz nowy projekt **aplikacji formularzy systemu Windows** i nadaj mu nazwę **DemoCalculatorTest**.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **DemoCalculatorTest,** a następnie wybierz polecenie **Dodaj odwołanie,** aby otworzyć okno dialogowe **Dodawanie odwołania.**

3. Wybierz **projekt** kartę, a następnie kliknij dwukrotnie projekt DemoCalculatorLib, aby dodać odwołanie do projektu testowego.

4. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **DemoCalculatorTest**, a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. W projektancie formularzy systemu Windows zwiększ rozmiar formularza do około **700 x 500**.

### <a name="use-the-control-in-the-forms-layout"></a>Używanie formantu w układzie formularza

Aby użyć democalculator kontroli w aplikacji, należy umieścić go w formularzu.

1. W **przyborniku**rozwiń węzeł **Składniki DemoCalculatorLib.**

2. Przeciągnij kontrolkę **DemoCalculator** z **przybornika** na formularz. Przenieś formant do lewego górnego rogu formularza. Gdy formant znajduje się blisko obramowań formularza, *pojawią* się linie przyciągania. Snaplines wskazują odległość `Padding` właściwości formularza i `Margin` właściwości formantu. Ustawić formant w miejscu wskazanym przez linie zatrzaskowe.

   Aby uzyskać więcej informacji, zobacz [Przewodnik: Rozmieszczanie formantów przy użyciu linii przyciągania](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. Przeciągnij `Button` formant z **przybornika** i upuść go na formularz.

4. Przesuń `Button` kontrolkę wokół kontrolki DemoCalculator i obserwuj, gdzie pojawiają się snapline. Za pomocą tej funkcji można precyzyjnie i łatwo wyrównać formanty. Usuń `Button` formant po zakończeniu.

5. Wybierz prawym przyciskiem wyboru kontrolka DemoCalculator, a następnie wybierz polecenie **Właściwości**.

6. Zmień wartość właściwości `Dock` na `Fill`.

7. Wybierz formularz, a następnie `Padding` rozwiń węzeł właściwości. Zmień wartość **All** na **20**.

   Rozmiar DemoCalculator kontroli jest zmniejszona, aby `Padding` pomieścić nową wartość formularza.

8. Zmienić rozmiar formularza, przeciągając różne uchwyty zmiany rozmiaru do różnych pozycji. Należy obserwować, jak formant DemoCalculator jest zmieniany, aby pasował.

## <a name="next-steps"></a>Następne kroki

W tym artykule pokazano, jak skonstruować interfejs użytkownika dla prostego kalkulatora. Aby kontynuować, można rozszerzyć jego funkcjonalność, implementując logikę kalkulatora, a następnie [opublikować aplikację za pomocą ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Lub przejdź do innego samouczka, w którym [tworzysz przeglądarkę obrazów przy użyciu formularzy systemu Windows](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Zobacz też

- [formanty Formularzy systemu Windows](/dotnet/framework/winforms/controls/)
- [Kontrolki ułatwień dostępu dla formularzy systemu Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [Publikowanie przy użyciu funkcji ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
