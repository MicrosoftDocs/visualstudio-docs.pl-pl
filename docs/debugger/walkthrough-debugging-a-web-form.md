---
title: Debugowanie formularza sieci Web | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web pages [.NET Framework], debugging
- Web sites [.NET Framework], debugging
- ASP.NET, debugging Web applications
- Web applications [.NET Framework], debugging
- ASP.NET Web sites, debugging
- ASP.NET Web pages, debugging
- debugging ASP.NET Web applications, Web Forms
- debugging [Visual Studio], Web Forms
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d28ebc797715614aefaf7206f170157d4f4485f2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055157"
---
# <a name="walkthrough-debugging-a-web-form"></a>Wskazówki: debugowanie formularzy sieci Web
Kroki opisane w tym instruktażu pokazano, jak można debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacja internetowa, znany także jako formularz sieci Web. Pokazuje jak uruchomić i zatrzymać wykonywanie, ustawiać punkty przerwania i sprawdzić zmienne w **Obejrzyj** okna.

> [!NOTE]
> Do przeprowadzenia tego instruktażu, musi mieć uprawnienia administratora na komputerze serwera. Domyślnie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu, aspnet_wp.exe lub w3wp.exe, działa jako [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Aby debugować [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], musi mieć uprawnienia administratora na komputerze, gdzie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , uruchomi go. Aby uzyskać więcej informacji, zobacz [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).

Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>Aby utworzyć formularz sieci Web

1. Jeśli masz już rozwiązania otwarte, zamknij go.

2. Na **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **witryny sieci Web**.

    **Nową witrynę sieci Web** pojawi się okno dialogowe.

3. W **szablony** okienku kliknij **witryny sieci Web platformy ASP.NET**.

4. Na **lokalizacji** wiersz, kliknij przycisk **HTTP** z listy, a następnie w polu tekstowym, wpisz **http://localhost/WebSite**.

5. W **języka** kliknij **Visual C#** lub **języka Visual Basic**.

6. Kliknij przycisk **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tworzy nowy projekt i wyświetla domyślny kod źródłowy HTML. Tworzy również nowy katalog wirtualny o nazwie **witryny sieci Web** w obszarze **domyślna witryna sieci Web** w usługach IIS.

7. Kliknij przycisk **projektowania** karty dolny margines.

8. Kliknij przycisk **przybornika** kartę na lewym marginesie, lub wybierz ją na **widoku** menu.

    **Przybornika** zostanie otwarty.

9. W **przybornika**, kliknij przycisk **przycisk** kontroli i dodać go do powierzchni projektowej głównego Default.aspx.

10. W **przybornika**, kliknij przycisk **Textbox** kontrolować i przeciągnij go do powierzchni projektu głównego, Default.aspx.

11. Kliknij dwukrotnie formant przycisku porzucony.

     Spowoduje to przejście do strony kodowej: Default.aspx.cs dla języka C# lub Default.aspx.vb dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Kursor powinien być w funkcji `Button1_Click`.

12. W `Button1_Click` funkcji, Dodaj następujący kod:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Projekt powinien być kompilowany bez błędów.

     Teraz można przystąpić do uruchomienia debugowania.

## <a name="to-debug-the-web-form"></a>Aby debugować formularz sieci Web

1. W oknie Default.aspx.cs lub Default.aspx.vb należy kliknąć lewy margines w tym samym wierszu jako tekst, który został dodany:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Pojawi się czerwona kropka i tekst w wierszu zostanie wyróżniony czerwonym kolorem. Czerwona kropka reprezentuje punkt przerwania. Po uruchomieniu aplikacji w trybie debugowania, debuger zlokalizuje miejsce trafienia kodu i przerwie tam wykonywanie. Można wówczas wyświetlić stan aplikacji i zdebugować ją. Aby uzyskać więcej informacji, zobacz [punktów przerwania](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

2. Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.

3. **Debugowanie nie włączone** pojawi się okno dialogowe. Wybierz **modyfikowanie pliku Web.config, aby włączyć debugowanie** opcji, a następnie kliknij przycisk **OK**.

    Internet Explorer rozpoczyna się i zostanie wyświetlona strona, która została zaprojektowana.

4. W programie Internet Explorer kliknij przycisk.

    W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], spowoduje to przejście do wiersza gdzie ustawić punkt przerwania na stronę kodową Default.aspx.cs lub Default.aspx.vb. Ten wiersz powinien być wyróżniony żółtym kolorem. Można teraz wyświetlić zmienne w aplikacji i kontrolować jej wykonanie. Zatrzymuje wykonywanie i czeka, aż polecenie od Ciebie aplikacji.

5. Na **debugowania** menu, kliknij przycisk **Windows**, następnie kliknij przycisk **Obejrzyj**, a następnie kliknij przycisk **Watch1**.

6. W **Obejrzyj** okna, typ **TextBox1.Text**.

    **Obejrzyj** okno pokazuje wartość zmiennej `TextBox1.Text`:

   '""'

7. Na **debugowania** menu, kliknij przycisk **Step Over**.

    Wartość `TextBox1.Text` zmian **Obejrzyj** okna do odczytu:

   `"Button was clicked!"`

8. Na **debugowania** menu, kliknij przycisk **Kontynuuj**.

9. W programie Internet Explorer kliknij ponownie przycisk.

     Wykonanie ponownie zatrzymuje się w punkcie przerwania.

10. W oknie Default.aspx.cs lub Default.aspx.vb kliknij czerwoną kropkę na lewym marginesie.

     Spowoduje to usunięcie punktu przerwania.

11. Na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Aby dołączyć do formularza sieci Web do debugowania

1. W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można dołączyć debuger do działającego procesu. Najbardziej efektywne, debugowanie, skompiluj plik wykonywalny jako wersja do debugowania przy użyciu plików symboli (PDB).

2. W oknie Default.aspx.cs lub Default.aspx.vb kliknij na lewym marginesie, aby ponownie ustawić punkt przerwania w dodanym wierszu:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. Na **debugowania** menu, kliknij przycisk **Rozpocznij bez debugowania**.

    Formularz sieci Web zaczyna być uruchamiana w ramach programu Internet Explorer, ale nie jest dołączony debuger.

4. Dołącz do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Aby uzyskać więcej informacji, zobacz [debugowania wdrożonych aplikacji sieci Web](../debugger/debugging-deployed-web-applications.md).

5. W programie Internet Explorer kliknij przycisk w formularzu.

    W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], powinien trafiony punkt przerwania w Default.aspx.cs, Default.aspx.vb lub Default.aspx.

6. Po zakończeniu debugowania na **debugowania** menu, kliknij przycisk **Zatrzymaj debugowanie**.

## <a name="see-also"></a>Zobacz także

- [Debugowanie aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)