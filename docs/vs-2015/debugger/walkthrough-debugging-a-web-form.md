---
title: 'Przewodnik: debugowanie formularza sieci Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e46169728c10d696f8dd99eb6459b9fcf081cb45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704930"
---
# <a name="walkthrough-debugging-a-web-form"></a>Przewodnik: Debugowanie formularza internetowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kroki opisane w tym instruktażu pokazują, jak debugować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikację sieci Web, znaną również jako formularz sieci Web. Pokazuje, jak uruchomić i zatrzymać wykonywanie, ustawić punkty przerwania i przeanalizować zmienne w oknie **czujki** .  
  
> [!NOTE]
> Aby ukończyć ten przewodnik, musisz mieć uprawnienia administratora na komputerze serwera. Domyślnie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces, aspnet_wp.exe lub w3wp.exe, działa jako [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces. Aby debugować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , musisz mieć uprawnienia administratora na komputerze, na którym [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] jest on uruchamiany. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
 Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-web-form"></a>Aby utworzyć formularz sieci Web  
  
1. Jeśli masz już otwarte rozwiązanie, zamknij je.  
  
2. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **Witryna sieci Web**.  
  
     Zostanie wyświetlone okno dialogowe **Nowa witryna sieci Web** .  
  
3. W okienku **Szablony** kliknij pozycję **witryna sieci Web ASP.NET**.  
  
4. W wierszu **lokalizacji** kliknij pozycję **http** z listy, a następnie w polu tekstowym wpisz **http://localhost/WebSite** .  
  
5. Na liście **Język** kliknij **Visual C#** lub **Visual Basic**.  
  
6. Kliknij przycisk **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tworzy nowy projekt i wyświetla domyślny kod źródłowy HTML. Powoduje także utworzenie nowego katalogu wirtualnego o nazwie **Witryna** sieci **Web w obszarze Domyślna witryna internetowa** w usługach IIS.  
  
7. Kliknij kartę **projekt** na dolnym marginesie.  
  
8. Kliknij kartę **Przybornik** na lewym marginesie lub wybierz ją w menu **Widok** .  
  
     Zostanie otwarty **Przybornik** .  
  
9. W **przyborniku**kliknij kontrolkę **przycisk** i Dodaj ją do głównej powierzchni projektowej, default. aspx.  
  
10. W **przyborniku**kliknij formant **TextBox** i przeciągnij formant do głównej powierzchni projektowej, default. aspx.  
  
11. Kliknij dwukrotnie formant przycisku, który został usunięty.  
  
     Spowoduje to przejście do strony kodowej: Default.aspx.cs for C# lub default. aspx. vb dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] . Kursor powinien znajdować się w funkcji `Button1_Click` .  
  
12. W `Button1_Click` funkcji Dodaj następujący kod:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.  
  
     Projekt powinien zostać skompilowany bez błędów.  
  
     Teraz wszystko jest gotowe do rozpoczęcia debugowania.  
  
### <a name="to-debug-the-web-form"></a>Aby debugować formularz sieci Web  
  
1. W oknie Default.aspx.cs lub default. aspx. vb kliknij lewy margines w tym samym wierszu co dodany tekst:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     Pojawi się czerwona kropka i tekst w wierszu zostanie wyróżniony czerwonym kolorem. Czerwona kropka reprezentuje punkt przerwania. Po uruchomieniu aplikacji w trybie debugowania, debuger zlokalizuje miejsce trafienia kodu i przerwie tam wykonywanie. Można wówczas wyświetlić stan aplikacji i zdebugować ją. Aby uzyskać więcej informacji, zobacz [punkty przerwania](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. W menu **Debugowanie** kliknij polecenie **Rozpocznij debugowanie**.  
  
3. Zostanie wyświetlone okno dialogowe **debugowanie nie jest włączone** . Wybierz opcję **Modyfikuj plik Web.config, aby włączyć opcję debugowania** , a następnie kliknij przycisk **OK**.  
  
     Zostanie uruchomiony program Internet Explorer i zostanie wyświetlona zaprojektowana strona.  
  
4. W programie Internet Explorer kliknij przycisk.  
  
     W programie spowoduje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] to przejście do wiersza, w którym ustawiany jest punkt przerwania na stronie kodowej default.aspx.cs lub default. aspx. vb. Ten wiersz powinien być wyróżniony żółtym kolorem. Można teraz wyświetlić zmienne w aplikacji i kontrolować jej wykonanie. Aplikacja przerywa wykonywanie i czeka na polecenie.  
  
5. W menu **debugowanie** kliknij pozycję **Windows**, a następnie kliknij pozycję **czujka**, a następnie kliknij pozycję **Watch1**.  
  
6. W oknie **czujka** wpisz **TextBox1. Text**.  
  
     Okno **czujki** pokazuje wartość zmiennej `TextBox1.Text` :  
  
    ```  
    ""  
    ```  
  
7. W menu **debugowanie** kliknij pozycję **krok powyżej**.  
  
     Wartość `TextBox1.Text` zmian w oknie **czujki** do odczytania:  
  
    ```  
    "Button was clicked!"  
    ```  
  
8. W menu **debugowanie** kliknij przycisk **Kontynuuj**.  
  
9. W programie Internet Explorer kliknij przycisk ponownie.  
  
     Wykonywanie zostało zatrzymane ponownie w punkcie przerwania.  
  
10. W oknie Default.aspx.cs lub default. aspx. vb kliknij czerwoną kropkę na lewym marginesie.  
  
     Spowoduje to usunięcie punktu przerwania.  
  
11. W menu **Debugowanie** kliknij polecenie **Zatrzymaj debugowanie**.  
  
### <a name="to-attach-to-the-web-form-for-debugging"></a>Aby dołączyć do formularza sieci Web na potrzeby debugowania  
  
1. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można dołączyć debuger do działającego procesu. W przypadku najbardziej efektywnego debugowania Skompiluj plik wykonywalny jako wersję do debugowania z plikami symboli (PDB).  
  
2. W oknie Default.aspx.cs lub default. aspx. vb kliknij przycisk na lewym marginesie, aby ponownie ustawić punkt przerwania w wierszu, który został dodany:  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3. W menu **debugowanie** kliknij polecenie **Uruchom bez debugowania**.  
  
     Formularz sieci Web zaczyna działać w programie Internet Explorer, ale debuger nie jest dołączony.  
  
4. Dołącz do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu. Aby uzyskać więcej informacji, zobacz [debugowanie wdrożonych aplikacji sieci Web](../debugger/debugging-deployed-web-applications.md).  
  
5. W programie Internet Explorer kliknij przycisk w formularzu.  
  
     W programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] należy nacisnąć punkt przerwania w default.aspx.cs, default. aspx. vb lub default. aspx.  
  
6. Po zakończeniu debugowania w menu **debugowanie** kliknij polecenie **Zatrzymaj debugowanie**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)
