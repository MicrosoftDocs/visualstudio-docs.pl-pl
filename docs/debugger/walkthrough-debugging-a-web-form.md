---
title: Debugowanie formularza internetowego | Microsoft Docs
description: Skorzystaj z przewodnika, aby dowiedzieć się, jak debugować aplikację internetową ASP.NET (formularz internetowy), w tym jak ustawiać punkty przerwania i badać zmienne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18347b7ba9ff52778b5acef685acd8f1ee400793
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385213"
---
# <a name="walkthrough-debugging-a-web-form"></a>Przewodnik: Debugowanie formularza internetowego
Kroki opisane w tym przewodniku pokazują, jak debugować aplikację [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] internetową, znaną również jako formularz internetowy. Pokazano w nim, jak rozpocząć i zatrzymać wykonywanie, ustawić punkty przerwania i zbadać zmienne w oknie **Czujka.**

> [!NOTE]
> Aby ukończyć ten przewodnik, musisz mieć uprawnienia administratora na komputerze serwera. Domyślnie proces, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aspnet_wp.exe lub w3wp.exe, jest uruchamiany jako [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces. Aby [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] debugować program , musisz mieć uprawnienia administratora na komputerze, na [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] którym jest on uruchamiany. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).

Wyświetlane okna dialogowe i polecenia menu mogą różnić się od tych opisanych w Pomocy, w zależności od aktywnych ustawień lub wersji. Aby zmienić ustawienia, wybierz **pozycję Importuj i eksportuj ustawienia** **w** menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="to-create-the-web-form"></a>Aby utworzyć formularz sieci Web

1. Jeśli masz już otwarte rozwiązanie, zamknij je.

2. W menu **File (Plik)** kliknij pozycję **New (Nowy),** a następnie kliknij pozycję **Web Site (Witryna sieci Web).**

    Zostanie **wyświetlone okno dialogowe Nowa** witryna sieci Web.

3. W **okienku Szablony** kliknij pozycję **ASP.NET sieci Web.**

4. W **wierszu** Lokalizacja kliknij pozycję **HTTP** na liście, a następnie w polu tekstowym wpisz **http://localhost/WebSite** .

5. Na liście **Język** kliknij pozycję **Visual C#** **lub Visual Basic**.

6. Kliknij przycisk **OK**.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tworzy nowy projekt i wyświetla domyślny kod źródłowy HTML. Tworzy również nowy katalog wirtualny o nazwie **WebSite** w obszarze **Domyślna witryna sieci Web w** usługach IIS.

7. Kliknij **kartę Projekt** na dolnym marginesie.

8. Kliknij **kartę Przybornik** na lewym marginesie lub wybierz ją w menu **Widok.**

    Zostanie **otwarty przybornik.**

9. W **przyborniku** kliknij **kontrolkę Przycisk** i dodaj ją do głównej powierzchni projektowej Default.aspx.

10. W **przyborniku** kliknij **kontrolkę Pole** tekstowe i przeciągnij ją na główną powierzchnię projektową Default.aspx.

11. Kliknij dwukrotnie kontrolkę przycisku, która jest porzucona.

     W ten sposób można uzyskać dostęp do strony kodowej: Default.aspx.cs dla języka C# lub Default.aspx.vb dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] . Kursor powinien być w funkcji `Button1_Click` .

12. W `Button1_Click` funkcji dodaj następujący kod:

    ```vb
    TextBox1.Text = "Button was clicked!"
    ```

    ```csharp
    TextBox1.Text = "Button was clicked!";
    ```

13. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Projekt powinien zostać skompilowany bez błędów.

     Teraz możesz rozpocząć debugowanie.

## <a name="to-debug-the-web-form"></a>Aby debugować formularz internetowy

1. W oknie Default.aspx.cs lub Default.aspx.vb kliknij lewy margines w tym samym wierszu co dodany tekst:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

    Pojawi się czerwona kropka i tekst w wierszu zostanie wyróżniony czerwonym kolorem. Czerwona kropka reprezentuje punkt przerwania. Po uruchomieniu aplikacji w trybie debugowania, debuger zlokalizuje miejsce trafienia kodu i przerwie tam wykonywanie. Można wówczas wyświetlić stan aplikacji i zdebugować ją. Aby uzyskać więcej informacji, zobacz [Punkty przerwania](/previous-versions/ktf38f66(v=vs.100)).

2. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.

3. Zostanie **wyświetlone okno dialogowe Debugowanie** nie jest włączone. Wybierz **pozycję Modyfikuj plik Web.config, aby włączyć opcję debugowania,** a następnie kliknij przycisk **OK.**

    Internet Explorer zostanie wyświetlona właśnie zaprojektowana strona.

4. W Internet Explorer kliknij przycisk .

    W programie następuje do wiersza, w którym ustawiono punkt przerwania na stronie kodowej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Default.aspx.cs lub Default.aspx.vb. Ten wiersz powinien być wyróżniony żółtym kolorem. Można teraz wyświetlić zmienne w aplikacji i kontrolować jej wykonanie. Aplikacja przestaje działać i czeka na polecenie od Ciebie.

5. W menu **Debugowanie** kliknij pozycję **Windows,** kliknij pozycję **Obejrzyj,** a następnie kliknij pozycję **Watch1.**

6. W **oknie Czujka** wpisz **TextBox1.Text.**

    W **oknie** Czujka jest przedstawiana wartość zmiennej `TextBox1.Text` :

   '""'

7. W menu **Debug (Debugowanie)** kliknij pozycję Step Over **(Przekłoń).**

    Wartość zmian `TextBox1.Text` w oknie **Czujka** do odczytania:

   `"Button was clicked!"`

8. W menu **Debugowanie** kliknij pozycję **Kontynuuj.**

9. W Internet Explorer kliknij przycisk ponownie.

     Wykonywanie zatrzymuje się ponownie w punkcie przerwania.

10. W oknie Default.aspx.cs lub Default.aspx.vb kliknij czerwoną kropkę na lewym marginesie.

     Spowoduje to usunięcie punktu przerwania.

11. W menu **Debugowanie** kliknij polecenie **Zatrzymaj debugowanie**.

## <a name="to-attach-to-the-web-form-for-debugging"></a>Aby dołączyć do formularza internetowego w celu debugowania

1. W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można dołączyć debuger do działającego procesu. Aby uzyskać najbardziej efektywne debugowanie, skompiluj plik wykonywalny jako wersję debugowania z plikami symboli (PDB).

2. W oknie Default.aspx.cs lub Default.aspx.vb kliknij lewym marginesie, aby ponownie ustawić punkt przerwania w dodanym wierszu:

   ```vb
   TextBox1.Text = "Button was clicked!"
   ```

   ```csharp
   textBox1.Text = "Button was clicked!";
   ```

3. W menu Debug (Debugowanie) kliknij pozycję **Start Without Debugging (Rozpocznij bez debugowania).** 

    Formularz internetowy zaczyna działać w obszarze Internet Explorer, ale debuger nie jest dołączony.

4. Dołącz do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu. Aby uzyskać więcej informacji, zobacz [Debugowanie wdrożonych aplikacji internetowych.](../debugger/debugging-deployed-web-applications.md)

5. W Internet Explorer kliknij przycisk w formularzu.

    W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] programie należy trafić punkt przerwania w plikach Default.aspx.cs, Default.aspx.vb lub Default.aspx.

6. Po zakończeniu debugowania w menu **Debugowanie** kliknij pozycję **Zatrzymaj debugowanie.**

## <a name="see-also"></a>Zobacz też

- [Debugowanie ASP.NET aplikacji](../debugger/how-to-enable-debugging-for-aspnet-applications.md)